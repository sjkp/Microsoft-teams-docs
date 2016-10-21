# Create the package for your Microsoft Teams tab app

For your tab app to available within Microsoft Teams, you need to create a tab package and upload it to Microsoft Teams. The tab package is a zip file containing:

- A manifest file, which specifies attributes of your app, and points to required resources, such as app icons and the location of your app configuration page.
- Image files, to be used as icons for your app within Microsoft Teams :
	- A small icon file, 44 by 44 pixels.
	- A larger icon file, 88 by 88 pixels.
		
	Each icon image file must be a transparent PNG, with a white or light-colored background.

## Creating a manifest for your tab app 

The manifest you create for your app must adhere to the manifest schema. For more information, see [Microsoft Teams tab manifest schema](tab_schema.md).

> **Tip** Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:
> 
> `"$schema": "https://statics.teams.microsoft.com/sdk/v0.2/manifest/MicrosoftTeams.schema.json",`


## Uploading your tab package to Microsoft Teams

Once you've created your app manifest and image files, compressed them into a zip file, and upload the zip file to Microsoft Teams to make your app available as a tab.

1. In Microsoft Teams, select the team from the left-hand panel, select **... (more options)** and then select **View Team**.
2. Select the **Developer** tab, and then select **Upload**.
3. Navigate to your zip file and select it.

Now, users will see your app listed among the tabs they can add to teams or 1:1 chats.

## Next steps

* [Create tab configuration UI](createtabconfigui.md)
* [Create the tab content UI](createtabcontent.md)

