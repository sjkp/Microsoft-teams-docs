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

## Prerequisites for tabs app pages

**TODO. ritaylor comment** Move this section to later topics on config and content UI

For the UI of your tab app--its configuration, content, and (optionally) tab removal pages--to be displayed within Microsoft Teams, they need to meet the following requirements. 

* Make sure that the page can be hosted in an iframe:
	
	* Set header `Content-Security-Policy: child-src *.teams.microsoft.com *.skype.com`. Most modern browsers support this.

		* For Internet Explorer 11 compatability, Set X-Content-Security-Policy as well.

	* Alternately, set header `X-Frame-Options: ALLOW-FROM *.teams.microsoft.com`. This header is deprecated but still respected by most browsers.

* Include the [Microsoft Teams Tab library](https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js) in your page as a script source.

	Eg: `<script src="https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js" />`

* Once your page has successfully loaded, call `microsoftTeams.initialize()` to display your UI. Microsoft Teams will not display your page unless you do so.

>**Tip:** For developers using TypeScript, Microsoft Teams provides a [definition file](https://statics.teams.microsoft.com/sdk/v0.2/types/MicrosoftTeams.d.ts) to enable IntelliSense or similar support from your code editor as well as compile-type type checking as part of your build.

## Next step

[Create the package for your Microsoft Team tab app](createtabpackage.md)
