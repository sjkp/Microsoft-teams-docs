# Update or remove a Microsoft Teams (preview) tab

You can enable users to update a tab after it's been added and to choose what happens to tab content if a tab is removed.

## Updating an existing tab instance

You can enable users to update, or reconfigure, a tab by setting the `canUpdateConfig` attribute in your tab manifest to `true`. For more information, see [Microsoft Teams tab package schema reference](schema.md). When you do so, Microsoft Teams adds a **Settings** option to the right-click menu for your tab.  When the user selects this option, Microsoft Teams will load the configuration page within an iframe inside an **Update Tab** dialog - similarly to the **Add Tab** dialog.

!["Screenshot of a tab with the right-click menu open to show the Settings menu option."](images/tab_settings.png)

In your configuration page code, call `microsoftTeams.settings.getSettings(function(settings) { /* ... */ })` after initialization. Once your callback is invoked, you can inspect to see if there are existing settings or if this is a new tab. You can then enable your configuration page and continue loading your content in the tab. 

>**Tip** When the user adds a tab, you can provide 'customSettings' inside Settings, which may be useful to you at this point.

## Removing a tab

You can enable users to select what happens to content when a tab is removed, by using a removal options page. For example, you might want to give them the option to download, archive, or delete the tab content.

>**Note:** Supporting removal options can significantly improve the user experience, especially if you expect users to frequently add and remove your tabs.  However, there is no guarantee that your page will always be loaded when a tab is removed.  For example, it won't happen if the user deletes the entire team or channel in which your tab sits.

The removal options page is an HTML page that you host. When a user chooses to remove your tab, Microsoft Teams will load the `removeUrl` (that you provided when [configuring a tab](createconfigpage.md)) within an iframe inside the **Remove tab** dialog.

You must include the [Microsoft Teams Tab library](jslibrary.md) in your removal options page so that it can communicate with Microsoft Teams.

>**Note:** the example here is solely to illustrate the concept.  Your removal options page should have a clean UI that fits with the look and feel of the Microsoft Teams dialog in which it sits.

!["Screenshot of the removal page for a simple example app, giving the user the option of whether to delete the map when the tab is removed."](images/tab_removal.png)

## Removal page example

The excerpt below shows an example tab removal page.

In this case, the user is presented with two radio buttons, which represent whether or not to delete the map and its data upon tab removal. Selecting either radio button fires `onClick()`, which sets `microsoftTeams.settings.setValidityState(true)`.

On remove, the code determines if the first radio button was checked, and if so, runs code (not shown) to remove the map and all its data from the underlying service. Finally, it calls `removeEvent.notifySuccess()` to specify that the removal process has successfully completed.

With this as a simple example, let's walk through the steps your removal page needs to perform to present the user with options, and process the content upon tab removal.

```HTML
<html>
<head>
<title>Map Tab remove UI</title>
</head>
<body>
<div id="container">
<form>
  <input type="radio" name="removetype" value="delete" onclick="onClick()">
	Delete this map and all data the team added to it? <br>
  <input type="radio" name="removetype" value="keep" onclick="onClick()">
	Keep this map available for use at 
	<a href='https://maps.bing.com' target='_blank'>https://maps.bing.com</a>
</form> 
</div>

<script src="https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js">
</script>
 
<script type="text/javascript">  

microsoftTeams.initialize();
microsoftTeams.settings.registerOnRemoveHandler(function(removeEvent){
 	  
    var radios = document.getElementsByName('removetype');
  	if (radios[0].checked) {
      // Delete the map and all its data from the underlying service.
	  }
    
    removeEvent.notifySuccess();
});
 
function onClick() {
    microsoftTeams.settings.setValidityState(true);
}

</script>```


### Prerequisites for your tab removal page 
 
For your tab removal page to display within Microsoft Teams, it must meet the [requirements for a tab page](prerequisites.md).

### Presenting the user with content options upon tab removal

Your code should call `microsoftTeams.settings.getSettings(function(settings) { /* ... */ })`. Once your callback is invoked, you can use these settings to determine the tab content that is being removed.

>**Tip** When the user adds a tab, you can provide 'customSettings' inside Settings, which may be useful to you at this point.

Upon page load, enable the **Remove** button immediately by calling `microsoftTeams.settings.setValidityState(true)`. So that you can do so, make sure that all the options in your tab removal page have a default selection.  Microsoft Teams will enable the **Remove** button after five seconds, even if your tab hasn't called `setValidityState`. 

If your tab removal page requires user context, see [Get user context, locale, or theme information](getusercontext.md). If your app needs to authenticate the user, see [Authenticating in your Microsoft Teams tab pages](auth.md).

### Processing the content prior to tab removal

Similar to the save handler, you can register a remove handler by calling `microsoftTeams.settings.registerOnRemoveHandler(function(removeEvent){})` for when the user selects **Remove**. At this point, your app should take whatever action(s) the user selected; for example, deleting or archiving content. If you need to perform these actions asynchronously, store `removeEvent`. Microsoft Teams removes the tab after 30 seconds, regardless of your actions.

Finally, call `removeEvent.notifySuccess()` or `removeEvent.notifyFailure()` to notify Microsoft Teams on the outcome of the removal.
