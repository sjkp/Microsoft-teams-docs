# Create the content for your Microsoft Teams (Preview) tab

When the user visits your tab, Microsoft Teams will load the `contentUrl` that you [provided earlier](createconfigpage.md) inside an iframe.

You must include the Microsoft Teams Tab library (https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js) in your content page so that it can communicate with Microsoft Teams.

>**Note:** The very simple 'maps' example in this documentation uses existing Bing and Google maps as content pages for illustration, which of course do not include this library.  See the [samples](samples.md) for a full example tab app that does so.  

!["Tab with iframed content highlighted."](images/tab_contentui.png)

**TODO: make this a Bing Map, to fit with the example we've been following**

## Prerequisites for content displayed in your tab

For your content to display within a Microsoft Teams tab, make sure it meets the [requirements for tab app pages](prerequisites.md).

>In summary: you must host your page on a secure https:// endpoint, ensure your page permits itself to be iframed, include the Microsoft Teams tab library, and call microsoftTeams.initialize();

In addition, make sure your content conforms to the [design recommendations](design.md) for Microsoft Teams tabs.

## Samples

Check out our [code samples](samples.md) on GitHub.

## Next steps

* [Update or remove a Microsoft Teams tab](updateremove.md)

