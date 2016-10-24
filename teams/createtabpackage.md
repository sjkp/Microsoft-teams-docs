# Create the package for your Microsoft Teams tab app

For your tab app to be available within Microsoft Teams, you need to create a tab package and upload it to a team. The tab package is a zip file containing:

- A manifest file, which specifies attributes of your app, and points to required resources, such as app icons and the location of your app configuration page.
- Image files, to be used as icons for your app within Microsoft Teams :
	- A small icon file, 44 by 44 pixels.
	- A larger icon file, 88 by 88 pixels.
		
	Each icon image file must be a transparent PNG, with a white or light-colored foreground.

**TODO. ritaylor comment** Let's have the actual manifest example on this page. Also have a variant that points to the config UI online somewhere (let's discuss)

## Creating a manifest for your tab app 

The manifest you create for your app must adhere to the manifest schema. For more information, see [Microsoft Teams tab manifest schema](tab_schema.md).

> **Tip** Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:
> 
> `"$schema": "https://statics.teams.microsoft.com/sdk/v0.2/manifest/MicrosoftTeams.schema.json",`


## Uploading your tab package to Microsoft Teams

Once you've created your app manifest and image files, compres them into a zip file.  Upload this zip file to a team to make your app available as a tab.

1. Create a new team for testing, if necessary. 
2. Select the team from the left-hand panel, select **... (more options)** and then select **View Team**.
3. Select the **Developer** tab, and then select **Upload**.
4. Navigate to your zip file and select it.

Now, when team members add a new tab to a channel in this team, they will see your app in the gallery of available tabs.

## Next steps

* [Create tab configuration UI](createtabconfigui.md)
* [Create the tab content UI](createtabcontent.md)

