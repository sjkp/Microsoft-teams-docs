# Authenticating a user in your Microsoft Teams (Preview) tab app

Tab apps run in iframes.  Azure Azure Active Directory (Azure AD), and other identity providers that you may use, do not usually allow their sign in and consent pages to be hosted within an iframe.

>**Note:** you can [obtain user context information](getusercontext.md) to simplify the sign in experience and to help build authentication requests and URLs.

## Silent authentication using Azure AD

If your app uses Azure AD as its identity provider, you may be able to authenticate the user silently within the iframe.  To do this, you must be sure that the existing Azure AD session cookies (from the user having already signed in to Microsoft Teams) will be sufficient.  For example, if you are using a redirect flow, you must be sure that when you redirect to Azure AD, it will redirect straight back with the tokens you need, and will not attempt to display anything to the user.

This will likely only be true if your tenant admin has configured your app in Azure AD so that it does **not** require:
* any additional authentication beyond that needed for Microsoft Teams: for example, does need additional two-factor authentication
* any consent by the user.

## Authentication using a pop-up window

If your app cannot silently authenticate the user against Azure AD, or if your app uses a identity provider other than Azure AD, it will need to explicitly authenticate the user in a pop up window.  You must use the [Microsoft Teams Tab Library](jslibrary.md) to do this, so that it works successfully in both the web and desktop apps for Microsoft Teams.  

1. Add UI to your configuration or content page to enable the user to sign in when necessary.
2. When the user selects to sign in, call `microsoftTeams.authentication.authenticate({url: <auth URL>, width: <width>, height: <height>, successCallback: <successCallback>, failureCallback: <failureCallback>})`.
	
	This launches the pop-up window for the specified identity provider, so the user can sign in. Once the user has completed their authentication, the pop-up window will be redirected to the callback page you specified for your app. 
3. In your app's callback page, call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()`.
	
	This will result in a callback to the successCallback or failureCallback function that you registered in step two, inside the original configuration or content page.  
4. If successful, you can now refresh or reload the page and show the configuration or content relevant to the now-authenticated user. If authentication fails, display an error message.


