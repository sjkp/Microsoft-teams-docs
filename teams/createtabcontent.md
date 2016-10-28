# Create the content for your Microsoft Teams (Preview) tab

When the user visits your tab, Microsoft Teams will load the `contentUrl` that you [provided earlier](createtabconfigui.md) inside an iframe.

!["Tab with iframed content highlighted."](images/tab_content.png)

## Prerequisites for content displayed in your tab

For your content to display within a Microsoft Teams tab, make sure it meets the [requirements for tab app pages](tabprerequisites.md).

>In summary: you must host your page on a secure https:// endpoint, ensure your page permits itself to be iframed, include the Microsoft Teams tab library, and call microsoftTeams.initialize();

In addition, make sure your content conforms to the [design recommendations](design.md) for Microsoft Teams tabs.

## Samples

Check out our [code samples](samples.md) on GitHub.

## Next steps

* [Update or remove a Microsoft Teams tab](updateremovetab.md)

