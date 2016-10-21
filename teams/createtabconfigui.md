# Create the configuration UI for your Microsoft Team tab app

The configuration UI enables you to present options and gather information from the user, so they can specify and customize the content and experience you present in the tab for your app. For example, selecting existing app resources to display, such as files, or specifying the attributes of new app resources.

!["Screenshot of the configuration UI for an Excel spreadsheet tab"](images/tab_configui.png)

The configuration UI is hosted within an IFrame in the dialog box Microsoft Teams displays when the user chooses to add your tab to their team or chat. It communicates to the main Microsoft Teams UI through the [Microsoft Teams Tab library](https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js).

## Prerequisites for your configuration UI

For your configuration UI to display within  Microsoft Teams, make sure it meets the [requirements for tab app UI](gettingstarted.md#prerequisites-for-your-tabs-app-ui).

## Collecting user information 

Your configuration UI needs to perform the following steps:  

### Determine when the user has specified all required information
 
By default, the **Save** button on the configuration dialog box is disabled. When the user has selected or entered all the required information for your app, you can enable the **Save** button by calling `microsoftTeams.settings.registerOnSaveHandler(function(saveEvent){})` and setting `microsoftTeams.settings.setValidityState(true)`.   

### Determine the content to display in the tab

Microsoft Teams calls the save event handler you registered when the user selects **Save**. At this point, you'll need to determine the URL of the content Microsoft Teams should host in the tab. If the user has selected a resource that already exists, such as an existing file, you can return the URL immediately. However, if the user has requested a new resource, you can can return the URL asynchronously, after you've created the resource.  If so, store `saveEvent` for later.  You have 30 seconds to return the URL, before the operation is terminated and an error displayed.

Use `microsoftTeams.settings.setSettings({contentUrl, suggestedTabName, websiteUrl, removeUrl})` to specify the URL of the content Microsoft Teams should host in the tab. Things to keep in mind:

* If `contentUrl` resides in a different domain from the configuration UI, make sure you have added that domain to the `validDomains` element in the tab manifest file. For more information, see [Microsoft Teams tab schema](tab_schema.md) and [Redirecting across domains within a Microsoft Teams tab](crossdomain.md).
*  You can use the other parameters to further customize how your content appears in Microsoft Teams:
	*  The `suggestedTabName` parameter sets the initial tab name. Users can rename the tab.
	*  The `websiteUrl` parameter sets where the user is taken if they select **Go to website**. Typically, this is a link to the same content as displayed on the tab, but within your app with its regular chrome and navigation.

### Return success or failure result

Finally, call `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to notify Microsoft Teams on the outcome of the configuration.

## Configuration UI example

The excerpt below shows a simple example of code that might be included in a configuration page. In this case, the user is presented with two radio buttons, which represent a choice of two different resources. Selecting either radio button fires `onClick()`, which sets `microsoftTeams.settings.setValidityState(true)`, enabling the **Save** button.

On save, the code determines which radio button was checked, and sets the various parameters of `microsoftTeams.settings.setSettings` accordingly. Finally, it sets `saveEvent.notifySuccess()` to specify that the content URL has successfully been determined.

```

microsoftTeams.initialize();
microsoftTeams.settings.registerOnSaveHandler(function(saveEvent){
 	  
    var radios = document.getElementsByName('resourcetype');
  	if (radios[0].checked) {
       microsoftTeams.settings.setSettings({contentUrl: "https://www.example.com/resource1/embed", suggestedTabName: "Resource One", websiteUrl: "https://www.example.com/resources", removeUrl: "https://localhost/maps/tabremove.htm"});
  	}
    else {
       microsoftTeams.settings.setSettings({contentUrl: "https://www.example.com/resource2/embed", suggestedTabName: "Resource Two", websiteUrl: "https://www.example.com/resources", removeUrl: "https://localhost/maps/tabremove.htm"});
    }
    
    saveEvent.notifySuccess();
});
 
function onClick() {
    microsoftTeams.settings.setValidityState(true);
}

```

## Next Steps

* [Create the content UI for your Microsoft Teams tab](createtabcontent.md)

