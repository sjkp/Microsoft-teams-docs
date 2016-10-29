# Getting started developing a Microsoft Teams (Preview) tab app

This section shows how to get started building a Microsoft Teams tab app, either from scratch or by adapting an existing web app.

<<<<<<< 037abd7b01789e8b38042c55d04fdb770835179d
> **Don't have Microsoft Teams? Get a one-year trial subscription of Office 365 Developer at no charge** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Teams for your organization. [Here's how](setup.md).
=======
> **Don't have Microsoft Teams? Get a one-year trial at no charge** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Microsoft Teams for your organization. [Here's how](setup.md).
>>>>>>> More review

>**Note:** Currently, developing new Microsoft Teams tabs is supported for channels in Microsoft Teams desktop and web applications. It is not yet supported in Microsoft Teams mobile apps or for private chats.

## Overview of building a Microsoft Teams tab app

Building a new tab app, or adapting an existing web app to be a tab, consists of the following general steps:

*  [Design a great Microsoft Teams tab app](design.md) While it's easy to adapt a web app to become a Microsoft Teams tab, it's worth taking some time before you start to consider which of your experiences and functionality  will work most effectively. 
*  [Create an tab app package:](createtabpackage.md) This package contains the manifest, which specifies attributes of the tab app, as well as the icons for your app within Microsoft Teams.
*  [Create the configuration page:](createtabconfigui.md) Microsoft Teams displays this page, inside the **Add a Tab** dialog, when the user chooses to add your tab. The configuration page enables your app to present options and gather information from the user so they can customize the content and experience you present in your tab app. This is an HTML page which you host and Microsoft Teams displays within an iframe.
	*  You can also [enable users to update a tab](updateremovetab.md#updating-an-existing-tab-instance) after they add it. 
*  [Create the content page:](createtabcontent.md) Once the user has configured the tab, Microsoft Teams displays the content for your tab app based on their configuration choices. This is also an HTML page which you host and Microsoft Teams display within an iframe.
	* You can also provide a page for users to specify [what happens to content when they remove a tab](updateremovetab.md#removing-a-tab).

## Next step

[Design a great Microsoft Teams tab app](design.md)