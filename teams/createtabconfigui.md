# Create the configuration UI for your Microsoft Team tab app

The configuration UI is an HTML page that you host. Microsoft Teams displays it inside the 'Add Tab' dialog when a user chooses to add your tab.  This UI enables you to present options and gather information from the user, so they can specify and customize the content and experience you present in your tab app. For example, selecting existing app resources to display, such as files or task lists, or specifying the attributes of new app resources.

!["Screenshot of the configuration UI for an Excel spreadsheet tab"](images/tab_configui.png)

**TODO. ritaylor comment**  Excel not a great example (will explain why).  Let's use the basic Maps tab example we are working through here.  And maybe also a screenshot from VSTS or maybe ToDO list (more realistic).  Let's also highlight the iframed area within this dialog.

When the user chooses to add your tab to their team or chat, Microsoft Teams displays your configuration page, hosted within an IFrame in a dialog box. The configuration page communicates with Microsoft Teams through the [Microsoft Teams Tab library](https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js).

## Prerequisites for your configuration UI

For your configuration UI to display within Microsoft Teams, make sure it meets the [requirements for tab app UI](gettingstarted.md#prerequisites-for-your-tabs-app-ui).

## Collecting user information 

Your configuration UI needs to perform the following steps:

### User context and authentication

If your UI requires user context, see [Get user context, locale, or theme information](getusercontext.md). If it needs to authenticate the user, see [Authenticating your Microsoft Teams tab app](auth.md).

### Determine when the user has specified all required information
 
By default, the **Save** button on the configuration dialog box is disabled. When the user has selected or entered all the required information for your app, you can enable the **Save** button by calling `microsoftTeams.settings.registerOnSaveHandler(function(saveEvent){})` and setting `microsoftTeams.settings.setValidityState(true)`.   

### Determine the content to display in the tab

When the user selects **Save**, Microsoft Teams calls the save event handler you registered. At this point, you'll need to determine the URL of the content Microsoft Teams should host in the tab. You'll often by able to return the URL immediately if, for example, the user has selected a resource that already exists such as an existing file or task list. However, you can return the URL asynchronously if, for example, the user has requested a new resource which will take time for you to create. If you need to do so, store `saveEvent` for later. If you do not return the URL within 30 seconds, Microsoft Teams terminates the operation and displays an error.

Use `microsoftTeams.settings.setSettings({contentUrl, suggestedTabName, websiteUrl, removeUrl})` to specify the URL of the content Microsoft Teams should host in the tab. Things to keep in mind:

* If `contentUrl` resides in a different domain from the configuration UI, make sure you have added that domain to the `validDomains` element in the tab manifest file. For more information, see [Microsoft Teams tab schema](tab_schema.md) and [Redirecting across domains within a Microsoft Teams tab](crossdomain.md).
*  The other parameters  further customize how your content appears in Microsoft Teams:
	*  The mandatory `suggestedTabName` parameter sets the initial tab name. Users can rename the tab.
	*  The optional `websiteUrl` parameter sets where the user is taken if they select **Go to website**. Typically, this is a link to the same content as displayed on the tab, but within your main web app with its regular chrome and navigation.

**TODO. ritaylor comment**  Mention removeUrl, reference to later topic.  Mention 'customSettings' too (add it to above code snippet)

### Return success or failure result

Finally, call `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to notify Microsoft Teams on the outcome of the configuration.

## Configuration UI example

The excerpt below shows a simple example of code that might be included in a configuration page. In this case, the user is presented with two radio buttons, which represent a choice of two different resources. Selecting either radio button fires `onClick()`, which sets `microsoftTeams.settings.setValidityState(true)`, enabling the **Save** button.

On save, the code determines which radio button was checked, and sets the various parameters of `microsoftTeams.settings.setSettings` accordingly. Finally, it sets `saveEvent.notifySuccess()` to specify that the content URL has successfully been determined.

**TODO. ritaylor comment**  Let's just have the full Maps example HTML file here, and encourage reader to host and experiment with it themselves?  Also let's put it online somewhere (let's discuss) so easy to run.  Also, is it best for this example to come up front?  I.e. it is easier to walk through the topic if you are looking at this?

```

microsoftTeams.initialize();
microsoftTeams.settings.registerOnSaveHandler(function(saveEvent){
 	  
    var radios = document.getElementsByName('resourcetype');
  	if (radios[0].checked) {
       microsoftTeams.settings.setSettings(
		{contentUrl: "https://www.example.com/resource1/embed", 
		suggestedTabName: "Resource One", 
		websiteUrl: "https://www.example.com/resources", 
		removeUrl: "https://www.example.com/tabremove.htm"});
  	}
    else {
       microsoftTeams.settings.setSettings(
		{contentUrl: "https://www.example.com/resource2/embed", 
		suggestedTabName: "Resource Two", 
		websiteUrl: "https://www.example.com/resources", 
		removeUrl: "https://www.example.com/tabremove.htm"});
    }
    
    saveEvent.notifySuccess();
});
 
function onClick() {
    microsoftTeams.settings.setValidityState(true);
}

```

## Next Steps

* [Create the content UI for your Microsoft Teams tab](createtabcontent.md)

