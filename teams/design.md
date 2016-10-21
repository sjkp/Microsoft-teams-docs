# Design a great Microsoft Teams tab app

While it's relatively easy to adapt a web app to become a Microsoft Teams tab, it's worth taking some time before you start to consider which experiences and functionality in your app will work most effectively as a tab app. Paying attention to these design considerations up front, whether you're creating a new app or adapting an existing web app, will help ensure you build a tab app that users want to incorporate in their Microsoft Teams collaboration.

First, understand that users work with Microsoft Team tabs in specific contexts> Either:

* A channel; that is, a conversation around a specific topic or purpose within the larger Team, or
* A 1:1 chat

In each case, tabs allow teams to collect together all the tools they need for a particular purpose. They can instantly access the tool in the correct context, and have collaborative experiences, such as conversations, around it.

With that in mind, consider the following when designing your tab app.

## Select relevant app functionality

Find the concept(s) in your app that best fit the contexts listed above.  Users will be more likely want to pin these as a tab. For example, the OneNote tab for a channel contains a section of the team's notebook. The Power BI tab maps to a specific report.

## Scope and focus the user experience

Once configured, your tab should drill down to the relevant context and not let the user navigate outside of it within the tab. Again using OneNote as an example, the OneNote tab places the user in a specific section of the team notebook, and doesn't anable them navigate to other sections.

## Integrate with the Microsoft Teams user experience

Your tab experience should feel integrated into Microsoft Teams. If you are adapting an existing web app, do not include your usual web app chrome, or display navigational dead ends. 

## Provide access to your web app's full functionality

If you are adapting an existing web app, your tab should provide a way for users to launch the full web app experience *outside* Microsoft Teams. For example, the OneNote tab includes an **Open in OneNote** option that launches the OneNote web app in a separate window.

## Streamline access 

Consider how to enable access permissions for your tab. Microsoft Teams is based on [Office Modern Groups](https://support.office.com/en-us/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2), so consider supporting permissions for them. At a minimum, you should make it easy to request access, so that each new user seeing the tab can do so. Or consider making the content generally available without requesting additional permissions.

## Generate parent objects

If your tab creates a new object for a channel, consider how to automatically create its parent object (mapping to the team) if it doesn't already exist. 





