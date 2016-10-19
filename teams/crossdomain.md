# Redirecting across domains within a Microsoft Teams tab

There are cases where your app might need to redirect the configuration or content page to a location on a different domain or subdomain. For example, suppose your configuration page begins on www.example.com. However, once your user, who works for Contoso, signs in, your app needs to redirect to www.contoso.example.com (or perhaps even www.anotherexample.com).  If your app performs the redirects itself, it will no longer be able to use the [Microsoft Teams Tab library](https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js) to receive or send information to Microsoft Teams. 

To redirect across domains within a Microsoft Teams tab:

* Make sure the URL falls within the domain(s) you've included in the ```validDomains``` list in the tab app manifest. For more information, see [Microsoft Teams tab package schema reference](tab-schema.md).
* Call ```microsoftTeams.navigateCrossDomain(yourNewUrl)``` to have Microsoft Teams redirect to the specified URL.
