# Getting started developing a Microsoft Teams tab app

This section shows how to get started building a Microsoft Teams tab app, either from scratch or adapting an existing web app to be hosted on a Microsoft Teams tab.

## Overview of building a Microsoft Teams tab app

Building a new tab app, or adapting an existing web app so that it can be hosted on a Microsoft Teams tab, consists of the following general steps:

*  [Creating an tab app package:]() This package contains the tab app manifest, which specifies attributes of the tab app, as well as the icon files used to represent your app within the Microsoft Teams UI.
*  [Creating the configuration UI:]() This HTML page, hosted by Microsoft Teams within an IFrame, enables you to present options and gather information from the user, so they can specify and customize the content and experience you present in the tab app.
*  [Creating the content UI:]() This HTML page, hosted by Microsoft Teams within an IFrame, presents the user with the content for your tab app, based on their configuration choices.

Optionally, you can also [enable users to update a tab](updateremovetab.md#updating-an-existing-tab-instance) after they add it, or provide UI for users to specify [what happens to content when they remove a tab](updateremovetab.md#removing-a-tab).


## Prerequisites for your tabs app UI

For your HTML pages to be hosted within a Microsoft Teams tab, they need to meet the following requirements. This applies to configuration, content, and removal pages for your tab app.

* Make sure that the page can be hosted in an IFrame:
	
	* Set the Content-security-policy header. This is supported in most modern browsers.
		
		Include child-src policy

		Return *.teams.microsoft.com  and *.skype.com in list of safe domains
	* Set X-Frame-Options = ALLOW-FROM *.teams.microsoft.com.

* Include the [Microsoft Teams Tab library](https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js) in your page as a script source.
* In your page code, call ```microsoftTeams.initialize()``` to display your UI.


## Next step

[Create the package for your Microsoft Team tab app](createtabpackage.md)


