# Microsoft Teams Tab Package Schema


manifestVersion
	
	Required. The version of the manifest schema this manifest is using.
	
id
	Required. A unique identifier for this tab extension. The id must use [reverse domain name notation](https://en.wikipedia.org/wiki/Reverse_domain_name_notation).
	**TODO: reviewers**, is there a better link to explain 'reverse domain name notation' than this Wikipedia article above?

version

	Required. The tab extension version. Changes to the tab extension should cause a version change. This version string must follow the [semver standard](http://semver.org/).
	**TODO: reviewers**, is this the correct standard to link to?

name

	Required. The display name of the tab extension.
developer
	Required. 
	name
		Required. The display name of the developer who created this app.
	websiteUrl
		Required. The url to the developer's website for this app.
	privacyUrl
		Required. The url to the privacy policy for this app.
	termsOfUseUrl
		Required. The url to the terms of use for this app.
description
	Required. 
	short
		Required. A short description of the tab extension, used when space in the UI is limited. Maximum length is 80 characters.
	full
		Required. The full description of the tab extension, used when space allows. Maximum length is 256 characters.
icons
	Required. 
	44
		Required. Name of the small icon for the tab extension, sized to 44 x 44 pixels. 
	88
		Required. Name of the larger icon for the tab extension, sized to 88 x 88 pixels.
	For additional information on format requirements for icon images, and including them in your tab package, see [Create the package for your Microsoft Team tab app](../createtabpackage.md).
accentColor
	Required. 
	A color to use in conjunction with the tab extension's icons.
	**TODO: reviewers**, any particular formats you need to specify the color in? hex? rgb? named colors?
configUrl
	Required. 
	The url of the configuration page for this tab app. For more information, see [Create the configuration UI for your Microsoft Team tab app](../createtabconfigui.md).
canUpdateConfig
	```true``` if a tab instance configuration can be updated by the user after creation. For more information, see [Update or remove a Microsoft Teams tab](../updateremovetab.md).	
	**TODO: reviewers** This is optional, right? Default is false?
needsIdentity
	```true``` if the tab requests access to user context information. For more information, see [Get user context, locale, or theme information for use in your Microsoft Team tab](../getusercontext.md). 
	**TODO: reviewers** This is optional, right? Default is false?
validDomains
	A list of valid domains from which the tab expects to communicate with Microsoft Teams.

## Example schema
TODO: Go through and clean this up

```
{
    "$schema": "https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/tab-manifest-schema.json",
    "manifestVersion": "0.2",
    "id": "com.example.microsoftteamstabs.maps",
    "version": "0.2",
    "name": "Maps",
    "developer": {
        "name": "Example company",   
        "websiteUrl": "http://www.example.com",
        "privacyUrl": "http://www.example.com/privacy",
        "termsOfUseUrl": "http://www.example.com/termsofuse"
    },
    "description" : {
            "short": "Host a map as a tab.",
            "full": "Host a map as a tab.  Give your tab a name, select Bing Maps or Google Maps, and click save."
    },
    "icons": {
            "44": "maps44.png",
            "88": "maps88.png"
    },
    "accentColor" : "#223344",
    "configUrl": "https://exampletabs.azurewebsites.net/maps/tabconfig.htm",
    "canUpdateConfig": true,
    "needsIdentity": false,
    "validDomains": [
        "*.bing.com",
        "*.google.com"
    ]
}
```