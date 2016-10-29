﻿# Redirecting across domains within a Microsoft Teams (Preview) tab

There are cases where your tab app might need to redirect the configuration or content page to a location on a different domain or subdomain. For example, suppose your configuration page begins on www.example.com. However, once a user who works for the Contoso Company signs in, your app needs to redirect to www.contoso.example.com (or perhaps even a different domain altogether, like www.anotherexample.com).  If your app performs the redirects itself, it will no longer be able to use the Microsoft Teams Tab library to receive or send information to Microsoft Teams. 

Instead, you should request that Microsoft Teams perform cross-domain redirects:

* Make sure the URL falls within the domain(s) you've included in the `validDomains` list in the tab app manifest. For more information, see [Microsoft Teams tab package schema reference](tab_schema.md).
* Call `microsoftTeams.navigateCrossDomain(yourNewUrl)` to request that Microsoft Teams redirect the iframe containing your page to the specified URL.
