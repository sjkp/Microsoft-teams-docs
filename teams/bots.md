# Creating bots for Microsoft Teams (Preview)

Build and connect intelligent bots to interact with Microsoft Teams users naturally through 1:1 chat.

> **Don't have Microsoft Teams? Get a one-year trial at no charge** To get started developing for Microsoft Teams, you'll need an Office 365 account, and to turn on Teams and bots for your organization. [Here's how](setup.md).

> **Note:** At this time, Microsoft Teams bots support 1:1 chat. They do not yet support channels or group chats.

## Creating a Microsoft Teams bot

All bots created using the Microsoft Bot Framework are automatically configured and ready to work in Microsoft Teams.

See the [Microsoft Bot Framework Overview](https://docs.botframework.com/en-us/) to learn how to:

1. Register the bot with the Microsoft Bot Framework, and make sure you add Microsoft Teams as a channel. When you first register a bot it will be in Preview, which means that it is only available to users in Microsoft Teams via side loading of the bot ID or via add button.
2. Build a bot using the [C# SDK](https://docs.botframework.com/en-us/csharp/builder/sdkreference/), [Node.js SDK](https://docs.botframework.com/en-us/node/builder/chat-reference/modules/_botbuilder_d_.html) or [Microsoft Bot Connector API](https://docs.botframework.com/en-us/restapi/connector/#navtitle).

3. Test it using the [Bot Framework Emulator](https://docs.botframework.com/en-us/tools/bot-framework-emulator/)
4. Deploy the bot to a cloud service, such as [Microsoft Azure](https://azure.microsoft.com/)
5. [Add the bot](#testing-your-bot-in-microsoft-teams) to a Microsoft Teams 1:1 chat, and test.

## Publishing

Publish your bot from the [Bot Dashboard](https://dev.botframework.com/bots) to request for it to be shown in the Microsoft bot directory. You can choose to automatically show in directories, or enable it later from the Bot Dashboard. Microsoft Teams will also review your bot for potential inclusion in the Teams app gallery.

> **Note:** Currently, People search is not enabled to find bots written in the Bot Framework. Users may interact with your bot by side loading the bot app ID.

Please make sure to read the [Best Practices](http://docs.botframework.com/directory/best-practices/), [Review Guidelines](http://docs.botframework.com/directory/review-guidelines/), [Terms of use](https://aka.ms/bf-terms), and [Code of Conduct](http://aka.ms/bf-conduct) before publishing your bot.

The [Terms of use](https://aka.ms/bf-terms) contains Sample Terms you can use to help create your own Terms of Service and the  [Code of Conduct](http://aka.ms/bf-conduct) contains links to third party Privacy Statement resources.

## Testing your bot in Microsoft Teams

There are two ways to test your bot in Microsoft Teams:

*	On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Channels**, select **Add to Microsoft Teams**.

	Microsoft Teams will launch with a 1:1 chat with your bot.

*	Side-load your bot from within Microsoft Teams:
	* On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Details**, copy the **Microsoft App ID** for your bot.
	
	!["Getting the AppID for the bot"](images/Bots_AppID_BotFramework.png)
	
	* From within Microsoft Teams, on the **Chat** pane, select the **Add chat** icon. For **To:**, paste your bot's Microsoft app ID.
	
	!["Getting the AppID for the bot"](images/Bots_Sideloading.png)
		
		The app ID should resolve to your bot name.
	* Select your bot and send a message to initiate a conversation.
	* Alternatively, you can paste your bot's app ID in the search box in the top left in Microsoft Teams. In the search results page, navigate to the People tab to see your bot and to start chatting with it. 

### Microsoft bot directory

Bots that are approved for Microsoft Teams may also appear in the Microsoft bot directory.

### How a bot appears in Microsoft Teams

Once a bot has been added it will appear in your conversation history in the same way as a chat with another user, but with a hexagonal avatar.

Bots in Microsoft Teams always appear online and do not have a mood message.

## Messages

Your bot can send rich text, pictures and cards to a 1:1 chat. Users can send rich text and pictures to your bot. You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.

| Format | From user to bot  | From bot to user |  Notes |                                                           
|:-------|:-------|:------------|:-------|
| Rich text | ✔ | ✔ | No emoticons |  
| Pictures | ✔ | ✔ | PNG, JPEG or GIF up to 20Mb |
| Cards | ✘ | ✔ |  |

### Welcome messages

To send a welcome message to a user listen for the [conversationUpdate](https://docs.botframework.com/en-us/csharp/builder/sdkreference/activities.html) activity.

### Pictures

Pictures are sent by adding attachments to a message.

Pictures can be PNG, JPEG or GIF up to 20Mb.

## Cards and buttons

Microsoft Teams supports the following cards which may have several properties and attachments. You can find information on how to use cards in the [.NET SDK](https://docs.botframework.com/en-us/csharp/builder/sdkreference/activities.html#richcards) and [Node.js SDK](https://docs.botframework.com/en-us/node/builder/guides/examples/#demo-skype-calling) docs.

* Hero card
* Thumbnail card
* Carousel card (with hero or thumbnail cards)
* List card

> **Note:** Microsoft Teams cards currently only support openUrl and imBack actions.

### Images

Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the image aspect ratio for the card.

Images should be HTTPS, up to 1024x1024, up to 1MB in size, and PNG or JPEG.

| Property | Type  | Description |                                                           
|:-------|:-------|:------------|
| url | URL | HTTPS URL to the image |
| alt | String | Accessible description of the image |

### Buttons

Buttons are shown stacked at the bottom of the card. Button text is always on a single line and will be trimmed if too long. If more buttons than can be supported by the card are included they will not be shown.

### Actions

| Property | Type  | Description |                                                           
|:-------|:-------|:------------|
| type | String | Required field. One of openURL (opens the given URL) or imBack (posts a message in the chat to the bot that sent the card) |
| title | String | Text description that appears on the button |
| value | String |  For openURL is a URL, and for imBack is a user defined string |

### Hero card

The [hero card](https://docs.botframework.com/en-us/csharp/builder/sdkreference/activities.html#herocard) renders a title, subtitle, text, large image and buttons.

!["Example of a hero-card"](images/Bots_HeroCarExample.PNG)

| Property | Type  | Description |                                                           
|:-------|:-------|:------------|
| title | Rich text | Title of the card. Maximum 2 lines |
| subtitle | Rich text | Subtitle of the card. Maximum 2 lines |
| text | Rich text | Text appears just below the subtitle |
| images: [] | Array of images | Image displayed at top of card. Aspect ratio 16:9 |
| buttons: [] | Array of action objects | Set of actions applicable to the current card. Maximum 6. |
| tap | Action object | This action will be activated when the user taps on the card itself |

### Thumbnail card

The [thumbnail card](https://docs.botframework.com/en-us/csharp/builder/sdkreference/activities.html#thumbnailcard) renders a title, subtitle, text, small thumbmail image and buttons.

!["Example of a thumbnail-card"](images/Bots_ThumbnailExample.png)

| Property | Type  | Description |                                                           
|:-------|:-------|:------------|
| title | Rich text | Title of the card. Maximum 2 lines |
| subtitle | Rich text | Subtitle of the card. Maximum 2 lines |
| text | Rich text | Text appears just below the subtitle |
| images: [] | Array of images | Image displayed at top of card. Aspect ratio 1:1 (square) |
| buttons: [] | Array of action objects | Set of actions applicable to the current card. Maximum 6. |
| tap | Action object | This action will be activated when the user taps on the card itself |


### Carousel card

The [carousel card](https://docs.botframework.com/en-us/csharp/builder/sdkreference/activities.html) can be used to show a carousel of images and text, with associated action buttons.

!["Example of a list-card"](images/Bots_CarouselExample.png)

Properties are the same as for the hero or thumbnail card.

### List card

The list card can be used to show a vertically stacked list of cards.

!["Example of a list-card"](images/Bots_ListExample.PNG)

Properties are the same as for the hero or thumbnail card.

## Bot settings

### Disabling a bot

To stop your bot receiving messages and remove it from directories go to your Bot Dashboard and edit the Microsoft Teams channel. Disable the bot in settings.

### Deleting a bot

To delete your bot completely go to your Bot Dashboard and edit the Microsoft Teams channel. Select the **Delete** button at the bottom.





 
