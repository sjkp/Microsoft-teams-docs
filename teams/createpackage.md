# Create the package for your Microsoft Teams (preview) tab

For your tab to be available within Microsoft Teams, you need to create a tab package and upload it to a team. The tab package is a zip file containing:

- A manifest file named `manifest.json`, which specifies attributes of your tab and points to required resources such the location of its configuration page.
- Image files, to be used as icons for your tab.  These must be transparent PNG files, with white or light-colored foreground in both small (44 by 44 pixels) and large (88 by 88 pixels) sizes.  (The accompanying background or 'accent color' is specified in the manifest.)

## Creating a manifest for your tab 

Below is a sample manifest for a simple tab.

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
            "full": "Host a map as a tab.  Give your tab a name, select Bing Maps or Google Maps, and click save."
    },
    "icons": {
            "44": "maps44.png",
            "88": "maps88.png"
    },
    "accentColor" : "#223344",
    "configUrl": "https://teams-get-started-sample.azurewebsites.net/tabconfig.html",
    "canUpdateConfig": true,
    "needsIdentity": false,
    "validDomains": [
        "*.bing.com",
        "*.google.com"
    ]
}
```
The manifest you create for your tab must adhere to the schema. For more information, see the [Microsoft Teams manifest schema](schema.md).

> **Tip:** Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:
> 
> `"$schema": "https://statics.teams.microsoft.com/sdk/v0.2/manifest/MicrosoftTeams.schema.json",`

## Uploading your tab package to Microsoft Teams

Once you've created your manifest and image files, compress them into a zip file.

> **Tip:** [Download the example zip file](https://github.com/OfficeDev/microsoft-teams-sample-get-started/blob/master/package/MapsTab.zip) that contains the example manifest shown here, and use it with the following instructions. 

Upload your zip file to a team to make your app available as a tab.

1. Create a new team for testing, if necessary.  Click **Create team** at the bottom of the left-hand panel.
2. Select the team from the left-hand panel, select **... (more options)** and then select **View Team**.
	
	!["Screenshot of the more options menu, with the View Teams option selected.](images/tab_view_team.png)
3. Select the **Developer (Preview)** tab, and then select **Upload**.

	!["Screenshot of the Developer pane, with tabs in development listed."](images/tab_sideload.png)

4. Navigate to your zip file and select it.

> **Note:** To re-upload an updated package, click the **Replace** icon at the end of the tab's table row.  Don't click **Upload** again; Microsoft Teams will say the tab already exists.

> Encountering other problems?  See the [troubleshooting guide](troubleshooting.md).

Now, when team members add a new tab to a channel in this team, they will be able to add your tab via the tab gallery.

1. Go to any channel in the team.  Click **+** to the right of the existing tabs.
2. Select your tab from the gallery that appears.
3. Accept the consent prompt.
4. Configure your tab via its [configuration page](createconfigpage.md) and click **Save**. 

!["The Add a tab dialog box, featuring a gallery of available tabs."](images/tab_gallery.png)

> **Note:** By default, all team members can add tabs.  But team admins can restrict this privilege to themselves if they so wish, via an option in the team settings.

## Next step

* [Create the configuration page](createconfigpage.md)
