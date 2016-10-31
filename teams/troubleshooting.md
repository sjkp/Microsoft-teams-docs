# Troubleshooting the Microsoft Teams (Preview) SDK

## Error while reading manifest.json
Most manifest errors will provide a hint at what specific field is missing or invalid. However, if the json file cannot be read as json at all, this generic error message is used.

Common reasons for manifest read errors:

* Invalid json. Use an IDE such as [Visual Studio Code](https://code.visualstudio.com) or [Visual Studio](https://www.visualstudio.com/vs/) that automatically validates the json syntax.
* Encoding issues. Use UTF-8 for the manifest.json file. Other encodings, specifically with the BOM, may not be readable.

## Another extension with same id "&lt;id&gt;" exists
If you're attempting to re-upload an updated package with the same id, use the 'Replace' icon at the end of the tab's table row rather than the 'Upload' button again.

If you're not re-uploading an updated package, ensure the id is unique.

## The save button isn't enabled on the settings dialog
Be sure to call `microsoftTeams.setValidityState(true)` once the user has input or selected all required data on your settings page to enable the save button.

## After selecting the save button, the tab settings cannot be saved.
When adding a tab, if you click the save buttons but are presented with an error message indicating the settings cannot be saved, the problem could be one of two classes of issues.

### The save success message was never recieved
If a save handler was registered using `microsoftTeams.settings.registerOnSaveHandler(handler)`, the callback must call `saveEvent.notifySuccess()`. If the callback doesn't call this within 30 seconds or calls `saveEvent.notifyFailure(reason)` instead, this error will be shown.

If no save handler was registered, the `saveEvent.notifySuccess()` call is automatically made immediately upon the user selecting the save button.

### The provided settings were invalid
The other reason the settings may not be saved is if the call to `microsoftTeams.setSettings(settings)` provided an invalid settings object, or the call wasn't made at all.

Common problems with the settings object:

* `settings.contentUrl` is missing. This field is required.
* `settings.contentUrl` or the optional `settings.removeUrl`, or `settings.websiteUrl` are provided but not valid. The urls must be https urls and also must either be the same domain as the settings page or specified in the manifest's `validDomains` list.
* `settings.customSettings` is provided but over the 1kb limit.