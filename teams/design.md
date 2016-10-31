# Design a great Microsoft Teams (preview) tab app

While it's relatively easy to adapt a web app to become a Microsoft Teams tab app, you should consider which experiences and functionality in your app will work most effectively.

## Select relevant app functionality

Teams add tabs to channels. A channel is a specific topic or purpose that the team has. Find the concept(s) in your app that best fit this context.  Users will be more likely want to add these as a tab. For example, the Planner tab for a channel contains a single plan.  The Power BI tab maps to a specific report.

>**Note:** Currently, developing tab apps is supported for channels in the Microsoft Teams desktop and web applications. It is not yet supported in the Microsoft Teams mobile apps or for private chats.

## Scope and focus the user experience

Once configured, your tab should drill down to the relevant context and not let the user navigate outside of it within the tab. For example, the Power BI tab doesn't enable the user navigate to other Power BI reports in situ.  However, like many tabs based on an existing web app, it does enable the 'Go To Website' button that launches the report in the main Power BI website.

## Integrate with the Microsoft Teams user experience

Your tab experience should feel integrated into Microsoft Teams. If you are adapting an existing web app, do not include your usual web app chrome, or display navigational dead ends. 

## Streamline access 

Consider how to enable access permissions for your tab. Microsoft Teams is based on [Office Modern Groups](https://support.office.com/en-us/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2), so consider supporting permissions for them. At a minimum, you should make it easy for each new user to request access when they visit the tab. Or consider if you can make the content generally available without requesting additional permissions.

## Next step

[Create the package for your Microsoft Team tab app](createpackage.md)


