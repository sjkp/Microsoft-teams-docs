# Microsoft Teams tab package schema reference

The tab package manifest file specifies attributes of your app, and points to required resources, such as the app icons to use in the Microsoft Teams UI and the location of your app configuration page. The manifest must adhere to the tab package schema, detailed below. 

For more information on including the manifest in your app package, see [Create the package for your Microsoft Team tab app](createtabpackage.md).

The schema defines the following properties:

## `manifestVersion` (string, required)

The version of the manifest schema this manifest is using.

## `id` (string, required)

A unique identifier for this extension. The id must use reverse domain name notation.

## `version` (string, required)

The extension version. Changes to the extension should cause a version change. This version string must follow the semver standard.

## `name` (string, required)

The display name of the extension.

## `developer` (object, required)

Properties of the `developer` object:

### `name` (string, required)

The display name for the developer

### `websiteUrl` (string, required)

The url to the developer's website.

### `privacyUrl` (string, required)

The url to the developer's privacy policy.

### `termsOfUseUrl` (string, required)

The url to the developer's terms of use.

## `description` (object, required)

Properties of the `description` object:

### `short` (string, required)

A short description of the extension used when space is limited.

### `full` (string, required)

The full description of the extension.

## `icons` (object, required)

Properties of the `icons` object:

### `44` (string, required)

An icon for the extension sized to 44x44.

### `88` (string, required)

An icon for the extension sized to 88x88.

## `accentColor` (string, required)

A color to use in conjunction with the extension's icons.

## `configUrl` (string, required)

The url to use when configuring the extension.

## `canUpdateConfig` (boolean)

A value indicating whether an instance of the extension's config can be updated by the user after creation.

Default: `true`

## `needsIdentity` (boolean)

A value indicating whether the extension is requesting access to identity information

## `validDomains` (array)

A list of valid domains from which the extension expects to load any content.

The object is an array with all elements of the type `string`.

## Example manifest

```JSON

{
    "$schema": "https://statics.teams.microsoft.com/sdk/v0.2/manifest/MicrosoftTeams.schema.json",
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
            "full": "Host a map as a tab.  Give your tab a name, 
					select Bing Maps or Google Maps, and click save."
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