# Prerequisites for Microsoft Teams (preview) tabs app pages

For the UI of your tab app - its configuration, content, and (optionally) tab removal pages - to be displayed within Microsoft Teams, they need to meet the following requirements. 

* Host the page on a secure https:// endpoint.  Microsoft Teams will not display insecure http:// content.

* Make sure that the page can be hosted in an iframe:
	
	* Set header `Content-Security-Policy: child-src *.teams.microsoft.com *.skype.com`. Most modern browsers support this.

		* For Internet Explorer 11 compatability, Set X-Content-Security-Policy as well.

	* Alternately, set header `X-Frame-Options: ALLOW-FROM *.teams.microsoft.com`. This header is deprecated but still respected by most browsers.

* Include the [Microsoft Teams Tab library](jslibrary.md) in your page as a script source.

	`<script src="https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js" />`

* Once your page has successfully loaded, call `microsoftTeams.initialize()` to display your page. Microsoft Teams will not display your page unless you do so.

>**Tip:** For developers using TypeScript, Microsoft Teams provides a [definition file](https://statics.teams.microsoft.com/sdk/v0.2/types/MicrosoftTeams.d.ts) to enable IntelliSense or similar support from your code editor as well as compile-type type checking as part of your build.

## Next steps

* [Create the tab package](createpackage.md)
* [Create the configuration page](createconfigpage.md)
* [Create the tab content](createcontentpage.md)
* [Update or remove a tab](updateremove.md)