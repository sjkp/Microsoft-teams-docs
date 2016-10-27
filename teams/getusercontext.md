# Get user context, locale, or theme information for use in your Microsoft Team (Preview) tab

There may be cases where your app needs basic information about the user, team, or company. This can be especially useful when:

* You need to create or associate resources in your app with the specified user or team.
* You want to initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again. (For more information on authenticating within your Microsoft Teams tab, see [Authenticating your Microsoft Teams tab](auth.md).)

> **Important:** While this user information provided by Microsoft Teams is useful for a smooth user experience, it is not guaranteed secure and therefore should **not** be used as proof of identity. 

In addition, you can retrieve locale and theme information.

There are two ways to access user context information:

* Inserting URL placeholder values
* Using the Microsoft Teams Tab library

## Getting user information through inserting URL placeholder values

First, set the `needsIdentity` element in your tab manifest to `true`. Doing so will prompt the user for their consent when they select your tab.

Next, use placeholders in your configuration or content URLs. Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to. The available placeholders include:

* {upn}: The user name
* {groupId}: The ID of an Office 365 group
* {tid}: The company ID, i.e., tenant ID
* {theme}: Display theme, such as 'default' or 'dark'
* {locale}: The user locale, such as 'en-us'

For example, suppose in your tab app manifest you set the `configURL` attribute to:

`"https://tasks.office.com/config?auth_upn={upn}&auth_tenant={tid}&group={groupId}"`

And the signed-in user has the following attributes:

* Their username is 'user@example.com'
* Their company tenancy ID is 'e2653c-etc'
* They are a member of the Office 365 group named 'test' 

When they select your tab, they will be navigated to:

`https://tasks.office.com/config?auth_upn=user@example.com&auth_tenant=e2653c-etc&group=test`


## Getting user information through using the Microsoft Teams Tab library

You can also retrieve the information listed above using the [Microsoft Teams Tab library](https://statics.teams.microsoft.com/sdk/v0.2/js/MicrosoftTeams.js), by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.

In addition, you can also register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.










