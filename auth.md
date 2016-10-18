# Authenticating your Microsoft Teams tab

Your tab app can use Azure Azure Active Directory (Azure AD) or any identity provider. Microsoft Teams provides a mechanism to enable secure user authentication when necessary.

## Silent authentication using Azure AD and user context

If your app uses Azure AD as its identity provider, you can retrieve user context information and use it to determine if you can authenticate the user silently. Retrieve the username and tenant ID, as described in [Get user context, locale, or theme information for use in your Microsoft Team tab](../getusercontext.md). If these, along with any existing Azure AD session cookies, are sufficient for you to silently authenticate the user, you can log the user into your service without having to prompt them. 

If not--for example, if your app requires two-factor authentication, or user consent--you'll need to have the user explicitly authenticate using the flow described below.

> **Important:** While this user information is useful for a smooth user experience, it is not guaranteed secure and therefore should **not** be used as proof of identity. 

## Authentication using a pop-up window

If your app cannot silently authenticate the user against Azure AD, or if your app uses a identity provider other than Azure AD, the user will need to explicitly authenticate using their credentials. 

Hosting an authentication flow within an IFrame is not considered secure, and most identity providers do not allow it. Instead, initiate an authentication flow for your tab by calling into [Microsoft Teams Tab library](https://teamspacewusprodms.blob.core.windows.net/tabframework/0.2/MicrosoftTeams.js). Microsoft Teams then generates a pop-up window in which the user can sign in.

To launch the pop-up window and authenticate the user, follow these steps:

1. Add UI to your configuration or content page to enable the user to sign in when necessary.
2. When the user selects to sign in, call ```microsoftTeams.authentication.authenticate({url: <auth URL>, width: <width>, height: <height>, successCallback: <successCallback>, failureCallback: <failureCallback>})```
	This launches the pop-up window for the specified identity provider, so the user can sign in. Once the user has completed their authentication, the pop-up window will be redirected to the callback page you specified for your app. 
3. In your app's callback page, call ```microsoftTeams.authentication.notifySuccess()``` or ```microsoftTeams.authentication.notifyFailure()```.
	This will result in a callback to the successCallback or failureCallback function that you registered in step two, inside the original configuration or content page.  
4. If successful, you can now refresh or reload the page and show the configuration or content relevant to the now-authenticated user. If authentication fails, display an error message.


