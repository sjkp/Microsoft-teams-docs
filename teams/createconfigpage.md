# Create the configuration page for your Microsoft Teams (Preview) tab app

The configuration page is an HTML page that you host. When a user chooses to add your tab, Microsoft Teams will load the 'configUrl' that you [provided in your manifest](createpackage.md) within an iframe inside the **Add Tab** dialog.

In this page, you present options and gather information from the user about what they want in your tab. For example, you may let the user select existing app resources (such as files or task lists) or even create new such resources just for this tab.

You must include the [Microsoft Teams Tab library](jslibrary.md) in your configuration page so that it can communicate with Microsoft Teams.

>**Note:** the example here is solely to illustrate the concept.  Your configuration page should have a clean UI that fits with the look and feel of the Microsoft Teams dialog in which it sits.

!["Screenshot of the configuration page for a simple example app, giving the user the option of which map type to select."](images/tab_configui.png)

## Configuration page example

The excerpt below shows an example configuration page.

In this case, the user is presented with two radio buttons, which represent a choice of two different resources. Selecting either radio button fires `onClick()`, which sets `microsoftTeams.settings.setValidityState(true)`, enabling the **Save** button.

On save, the code determines which radio button was checked, and sets the various parameters of `microsoftTeams.settings.setSettings` accordingly. Finally, it calls `saveEvent.notifySuccess()` to specify that the content URL has successfully been determined.

With this as a simple example, let's walk through the steps your configuration page needs to perform to load your tab app content.

```HTML
<html>
<body>
<form>
  <input type="radio" name="maptype" value="bing" onclick="onClick()"> Bing Maps<br>
  <input type="radio" name="maptype" value="google" onclick="onClick()"> Google Maps
</form> 

<script src="https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js"></script>
 
<script type="text/javascript">  

microsoftTeams.initialize();
microsoftTeams.settings.registerOnSaveHandler(function(saveEvent){

    var radios = document.getElementsByName("maptype");
    if (radios[0].checked) {
       microsoftTeams.settings.setSettings({
         contentUrl: "https://www.bing.com/maps/embed",
         suggestedTabName: "Bing Map",
         websiteUrl: "https://www.bing.com/maps",
         removeUrl: "https://teams-get-started-sample.azurewebsites.net/tabremove.html"
      });
    } else {
       microsoftTeams.settings.setSettings({
         contentUrl: "https://www.google.com/maps/embed",
         suggestedTabName: "Google Map",
         websiteUrl: "https://www.google.com/maps",
         removeUrl: "https://teams-get-started-sample.azurewebsites.net/tabremove.html"
      });
    }
    
    saveEvent.notifySuccess();
});

function onClick() {
    microsoftTeams.settings.setValidityState(true);
}

</script>
</body>
</html>
```

## Prerequisites for your configuration page

For your configuration page to display within Microsoft Teams, make sure it meets the [requirements for tab app pages](prerequisites.md).

>In summary: you must host your page on a secure https:// endpoint, ensure your page permits itself to be iframed, include the Microsoft Teams tab library, and call microsoftTeams.initialize();

## Collecting user information 

Your configuration page needs to perform the following steps:

### Obtain user context and authenticate

If your page requires user context, see [Get user context, locale, or theme information](getusercontext.md). If it needs to authenticate the user, see [Authenticating your Microsoft Teams tab app](auth.md).

### Determine when the user has specified all required information
 
By default, the **Save** button on the configuration dialog box is disabled. When the user has selected or entered all the required information for your app, you can enable the **Save** button by calling `microsoftTeams.settings.setValidityState(true)`.

### Determine the content to display in the tab

Use `microsoftTeams.settings.setSettings({contentUrl, suggestedTabName, websiteUrl, removeUrl, customSettings})` to specify the URL of the [content page](createcontentpage.md) Microsoft Teams should host in the tab. Things to keep in mind:

* This call may be made at any time the configuration page is displayed, including before or after the user selects the **Save** button (see below).
* The `contentUrl` is a required field which specifies the URL of the content Microsoft Teams should host in the tab.
* If `contentUrl` resides in a different domain from the configuration page, make sure you have added that domain to the `validDomains` element in the tab manifest file. For more information, see [Microsoft Teams tab schema](schema.md) and [Redirecting across domains within a Microsoft Teams tab](crossdomain.md).
*  The other parameters further customize how your tab works in Microsoft Teams:
	* The optional `suggestedTabName` parameter sets the initial tab name. Users can rename the tab. The default value is the display name for the tab app as specified in the manifest.
	* The optional `websiteUrl` parameter sets where the user is taken if they click the **Go to website** button. Typically, this is a link to the same content as displayed on the tab, but within your main web app with its regular chrome and navigation.
	* The optional `removeUrl` parameter sets the URL for your [removal options page](updateremove.md#removing-a-tab).
	* The optional `customSettings` parameter can be used to store additional information that helps your tab app regain context when [updating or removing a tab](updateremove.md).

### React when the user clicks the Save button

Often you may not be able to determine the `contentUrl` immediately.  For example, you may first need create a new resource (a document or a task), and you only want to do this once the user selects **Save**. To be notified when the user selects **Save**, you must call
`microsoftTeams.settings.registerOnSaveHandler(function(saveEvent) { /* ... */ })`. Once this is done, when the user selects **Save**, Microsoft Teams calls the save event handler you registered.

You can return the settings asynchronously if, for example, the user has requested a new resource which will take time for you to create. To do this, store `saveEvent` for later. If you do not notify the outcome within 30 seconds, Microsoft Teams terminates the operation and displays an error.

### Return success or failure result

Finally, in your save handler registered previously, call `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to notify Microsoft Teams on the outcome of the configuration. If you have no save handler registered, the outcome will immediately and implicitly be success.

## Next Step

* [Create the content page for your Microsoft Teams tab](createcontentpage.md)
