# Create the package for your Microsoft Team tab app

In order for your app to be listed as a tab that can be added within Microsoft Teams, you need to create a tab package and upload it to Microsoft Teams. The tab package is a zip file containing:

- A manifest file that specifies attributes of your app, and points to required resources, such as the app icons to use in the Microsoft Teams UI and the location of your app configuration page.
- Image files to be used as icons for your app within the Microsoft Teams UI:
	- A small icon file, 44 by 44 pixels.
	- A larger icon file, 88 by 88 pixels.
		
	Each icon image file must be a transparent PNG, with a white or light-colored background.

## Creating a manifest for your app 

The manifest you create for your app must adhere to the manifest schema. For more information, see [Microsoft Teams tab manifest schema](tab_schema.md).

> **Tip** Specify the schema in your manifest to enable IntelliSense or similar support from your code editor:
> 
> {
    "$schema": "https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/tab-manifest-schema.json",
	...}

## Uploading your tab package to Microsoft Teams

Once you've created your app manifest and image files, and compressed them into a zip file, upload the zip file to Microsoft Teams to make your app available as a tab.

1. In Microsoft Teams, select the team from the left-hand panel, select **...** and then select **View Team**.
2. Select the **Developer** tab, and then select **Upload**.
3. Navigate to your zip file and select it.
	
	Your app displays under **Tabs in development**.

From here, users can select your app to add it as a tab to the selected Team or chat.

## Next steps

* [Create tab configuration UI](createtabconfigui.md)
* [Create the tab content UI](createtabcontent.md)

