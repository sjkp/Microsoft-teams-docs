# Getting started developing a Microsoft Teams tab app

This section shows how to get started building a Microsoft Teams tab app, either from scratch or adapting an existing web app.

>**Note:** Currently, developing new Microsoft Teams tabs is supported for channels in Microsoft Teams desktop and web applications. It is not yet supported in Microsoft Teams mobile apps or for private chats.

## Overview of building a Microsoft Teams tab app

Building a new tab app or adapting an existing web app to be a tab consists of the following general steps:

*  [Creating an tab app package:](createtabpackage.md) This package contains the tab app manifest, which specifies attributes of the tab app, as well as the icons for your app within Microsoft Teams.
*  [Creating the configuration page:](createtabconfigui.md) Microsoft Teams displays this when the user selects to add your tab. The configuration page enables your app to present options and gather information from the user so they can specify and customize the content and experience you present in your tab app. This is an HTML page which you host and Microsoft Teams displays within an iframe.
	*  You can also [enable users to update a tab](updateremovetab.md#updating-an-existing-tab-instance) after they add it. 
*  [Creating the content page:](createtabcontent.md) Once the user has configured the tab, Microsoft Teams displays the content for your tab app based on their configuration choices. This is also an HTML page iframe.
	* You can also provide a page for users to specify [what happens to content when they remove a tab](updateremovetab.md#removing-a-tab).


## Next step

[Create the package for your Microsoft Team tab app](createtabpackage.md)
