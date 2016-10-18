# Get user context, locale, or theme information for use in your Microsoft Team tab

There may be cases where your app needs basic information about the user, team, or company

> **Important**: While this user information is useful for a smooth user experience, it is not secure and therefore should **not** be used as proof of identity. 

There are two way:

* Through inserting URL placeholder values
* Through using the Microsoft Teams Tab library

## Through inserting URL placeholder values

First, set the ```needsIdentity``` element in your tab manifest to ```true```. Doing so will prompt the user for their consent when they select your tab.

TODO: get consent screenshot?

Next, use placeholders in your configuration or content URLs. Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to. The available placeholders include:

* {upn}: The user name
* {groupId}: The ID of an Office 365 group
* {tid}: The company ID, i.e., tenant ID
* {mkt}: TODO--is this theme? or a mistake?
* {locale}: The user locale

For example, suppose in your tab manifest you set the ```configURL``` attribute to:
```"https://tasks.office.com/config?auth_upn={upn}&auth_tenant={tid}&group={groupId}"```

And the signed-in user has the following attributes:

* Their username is  'user@example.com'
* Their company tenancy ID is 'e2653c-etc'
* They are a member of the Office 365 group named 'test' 

When they select your tab, they will be navigated to:
```https://tasks.office.com/config?auth_upn=user@example.com&auth_tenant=e2653c-etc&group=test```


## Through using the Microsoft Teams Tab library





You may need basic information or context about the user, team, or company (tenant) to provide a seamless experience.  In particular.  This information can help you:
	• Create or associate resources in your system with the user or team
	• Start an OAuth or similar redirect flow against AAD or other identity provider, without the user being unnecessarily prompted again for their username.  

Note: this information is described as a 'hint' because it is suitable for improving the user experience, but it must not be used as proof of identity.  An attacker could load your page in a bad browser, replace our library, and provide you with any user name they like.

To request this information, you must set 'needsIdentity' in your manifest.  In turn, this will cause the following to be displayed when the user consents to your tab:

	<Tab name> needs access to:
	Team member’s email addresses and information that can identify your team and organization name. Data may be sent to a third-party service

You can have the username (i.e. UPN), Office 365 group ID, and AAD tenant ID of the currently signed in user injected into your configuration or content URLs by inserting a {upn}, {groupId} and {tid} placeholder into the URLs you provide. For example, if your tab specifies the configuration URL:
	'https://tasks.office.com/config?auth_upn={upn}&auth_tenant={tid}&group={groupId} '
 and the user signed into Microsoft Teams is:
	 'yudogan@microsoft.com' in tenant 'e2653c-0351-42e6-b0bf-75c28889e017', and a member of group 'abcde'
 then your tab's configuration iframe will actually be navigated to:
	https://tasks.office.com/config?auth_upn=yudogan@microsoft.com&auth_tenant=e2653c-0351-42e6-b0bf-75c28889e017&group=abcde

Or you can ask for this same information via the JavaScript library: microsoftTeams.getContext() .

This information can be used as a hint to AAD when kicking off an authentication flow within your iframe.  If the UPN, tenant ID and existing AAD session cookies are sufficient for you to silently authenticate the user against your service then you can stop here and merrily go about building your experience; otherwise, see User authentication - pop-up flow


Obtaining the locale and UI theme

You may need to know the current locale (e.g. en-us) or the UI theme (default or dark).  This works similarly to the process described in User context:

	• You can have this injected into your configuration or content URLs by inserting a {mkt} and {locale} placeholder into the URLs you provide.
	
	• You can obtain this same information via the JavaScript library: microsoftTeams.getContext() .

You can also register to be told if the theme changes by calling microsoftTeams.registerOnThemeChangeHandler(…);


