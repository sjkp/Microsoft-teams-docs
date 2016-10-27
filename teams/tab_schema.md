# Microsoft Teams (Preview) tab package schema reference

The tab package manifest file specifies attributes of your app, and points to required resources, such as the app icons to use in the Microsoft Teams UI and the location of your app configuration page. The manifest must adhere to the tab package schema, detailed below. 

For more information on including the manifest in your app package, and an example manifest, see [Create the package for your Microsoft Team tab app](createtabpackage.md).

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

A short description of the extension used when space is limited. Maximum length is 80 characters.

### `full` (string, required)

The full description of the extension. Maximum length is 256 characters.

## `icons` (object, required)

Each icon image file must be a transparent PNG, with a white or light-colored background.

Properties of the `icons` object:

### `44` (string, required)

An icon for the extension sized to 44x44.

### `88` (string, required)

An icon for the extension sized to 88x88.

## `accentColor` (string, required)

A color to use in conjunction with the extension's icons. The value must be a valid HTML color code starting with '#', for example `#4464ee`.

## `configUrl` (string, required)

The url to use when configuring the extension.

## `canUpdateConfig` (boolean)

A value indicating whether an instance of the extension's config can be updated by the user after creation.

Default: `true`

## `needsIdentity` (boolean)

A value indicating whether the extension is requesting access to identity information

## `validDomains` (array)

A list of valid domains from which the extension expects to load any content. Domain listings can include wildcards, for example `*.example.com`. If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.

The object is an array with all elements of the type `string`.
