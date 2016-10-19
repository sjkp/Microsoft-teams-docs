# Create the content for your Microsoft Teams tab

Once you have determined the URL of the content the user wants, based on user configuration choices, you send that URL to Microsoft Teams  to display that content in the new tab.

## Prerequisites for content displayed in your tab

For your content to display within a Microsoft Teams tab, be sure to do the following:

* Make sure that the UI can be hosted in an IFrame
	
	* Set the Content-security-policy header. This is supported in most modern browsers.
		
		Include child-src policy

		Return *.teams.microsoft.com  and *.skype.com in list of safe domains
	* Set X-Frame-Options = ALLOW-FROM *.teams.microsoft.com.

* Include the [Microsoft Teams Tab library](https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js) as a script source.
* Call ```microsoftTeams.initialize()``` to display your UI.

In addition, make sure your content conforms to the [TODO: design guidelines]() for Microsoft Teams tabs.

## Next steps

* [TODO: check out our code samples on GitHub]()