# Getting started developing a Microsoft Teams (Preview) tab app

You can build a Microsoft Teams tab app from scratch or by adapting your existing web app.

<<<<<<< 45f87e44568756c9e2f6d0bdafd21d90dfdd02f2
<<<<<<< 037abd7b01789e8b38042c55d04fdb770835179d
> **Don't have Microsoft Teams? Get a one-year trial subscription of Office 365 Developer at no charge** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Teams for your organization. [Here's how](setup.md).
=======
> **Don't have Microsoft Teams? Get a one-year trial at no charge** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Microsoft Teams for your organization. [Here's how](setup.md).
>>>>>>> More review

>**Note:** Currently, developing new Microsoft Teams tabs is supported for channels in Microsoft Teams desktop and web applications. It is not yet supported in Microsoft Teams mobile apps or for private chats.
=======
> **Don't have Microsoft Teams? Get a free one-year Office 365 developer subscription.** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Microsoft Teams for your organization. [Here's how](setup.md).
>>>>>>> Saturday lunch checkpoint

## Overview of building a Microsoft Teams tab app

Folow these steps to build a tab app:

*  [Design a great tab](design.md) While it's easy to adapt a web app to become a Microsoft Teams tab app, it's worth considering which of your experiences and functionality will work most effectively. 
*  [Create the package:](createpackage.md) This package contains the manifest, which specifies attributes of your tab app, as well as its icons within Microsoft Teams.
*  [Create the configuration page:](createconfigpage.md) Microsoft Teams displays this configuration page inside the **Add a Tab** dialog, when the user chooses to add your tab. The configuration page enables your tab app to present options and gather information from the user so they can customize the content and experience you present in your tab. This is an HTML page which you host and Microsoft Teams displays within an iframe.
	*  You can also [enable users to update a tab](updateremove.md#updating-an-existing-tab-instance) after they add it. 
*  [Create the content page:](createcontentpage.md) Microsoft Teams displays this content page when the user visits your tab. This is also an HTML page which you host and Microsoft Teams display within an iframe.
	* You can also provide a page for users to specify [what happens to content when they remove a tab](updateremove.md#removing-a-tab).

>**Note:** Currently, developing tab apps is supported for channels in the Microsoft Teams desktop and web applications. It is not yet supported in the Microsoft Teams mobile apps or for private chats.

## Next step

[Design a great Microsoft Teams tab app](design.md)