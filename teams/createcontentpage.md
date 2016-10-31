# Create the content for your Microsoft Teams (preview) tab

The content page is an HTML page that you host.  When the user visits your tab, Microsoft Teams will load the `contentUrl` (that you [provided earlier](createconfigpage.md)) within an iframe inside the main tab canvas area.

In this page, you present the main function of your tab app, following the [design recommendations](design.md).

You must include the [Microsoft Teams Tab library](jslibrary.md) in your configuration page so that it can communicate with Microsoft Teams.

>**Note:** The very simple 'maps' example in this documentation uses existing Bing and Google maps as content pages for illustration, which of course do not include this library.  See the [samples](samples.md) for a full example tab app that does so.  

!["Tab with iframed content highlighted."](images/tab_content.png)

## Prerequisites for content displayed in your tab

For your content to display within a Microsoft Teams tab, make sure it meets the [requirements for tab app pages](prerequisites.md).

>In summary: you must host your page on a secure https:// endpoint, ensure your page permits itself to be iframed, include the Microsoft Teams tab library, and call microsoftTeams.initialize();

## Samples

Check out our [sample tab apps](samples.md) on GitHub.

## Next steps

* [Update or remove a Microsoft Teams tab](updateremove.md)

