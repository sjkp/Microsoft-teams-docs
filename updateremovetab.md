# Update or remove a Microsoft Teams tab

TODO: intro

## Updating an existing tab instance

!["Screenshot of a tab with the right-click menu open to show the Settings menu option."](../images/tab_settings.png)
TODO: redo screenshot prior to publication (contains 'Skype Teams' branding)

You can allow users to update or re-configure an existing tab, by setting 'canUpdateConfig' in your manifest to true.  If so, your tab will show a Settings option, available on the right-click menu on tab selector in the tab bar.   When the user clicks Settings, an Update Tab dialog will be shown that is very similar to the Add a Tab dialog.  In particular, it includes your config UI in an iframe.

If you support this option, you should call microsoftTeams.settings.getSettings(<callback>) after initialization.  Once you receive the callback, you can inspect to see if there are existing settings or if this is a new tab.  You can then enable your config UI and continue the steps described in Quick Start.

Note that when a tab is added, you can set 'customSettings' inside Settings and use this to help you re-hydrate your context if the tab is updated.  This is a string, but you can of course store multiple settings here by serializing or 'stringifying' an object.
