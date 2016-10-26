# Creating bots for Microsoft Teams

Build and connect intelligent bots to interact with Microsoft Teams users naturally through 1:1 chat.

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
	* From within Microsoft Teams, on the **Chat** pane, select the **Add chat** icon. For **To:**, paste your bot's Microsoft app ID.
		
		The app ID should resolve to your bot name.
	* Select your bot and send a message to initiate a conversation.
	* Alternatively, you can paste your bot's app ID in the search box in the top left in Microsoft Teams. In the search results page, navigate to the People tab to see your bot and to start chatting with it. 

### Microsoft bot directory

Bots that are approved for Microsoft Teams may also appear in the Microsoft bot directory.

### How a bot appears in Microsoft Teams

Once a bot has been added it will appear in your conversation history in the same way as a chat with another user, but with a hexagonal avatar.

Bots in Microsoft Teams always appear online and do not have a mood message.

## Messages

Your bot can send rich text, emoticons, pictures and cards to a 1:1 chat. Users can send rich text and pictures to your bot. You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.

For more information on the format and attributes of these message types, see  the **[Messages](https://docs.botframework.com/en-us/skype/getting-started/#messsages)** section of [Getting Started with Skype bots](https://docs.botframework.com/en-us/skype/getting-started/). Microsoft Teams supports all the message types listed in this topic, with the following limitations and exceptions:

* For messages, Microsoft Teams bots currently do not support Skype emoticons.
* For messages, the channel ID value will be "msteams".
* For card types, Microsoft Teams bots currently do not support the receipt card type.
* Microsoft Teams bots currently do not support calling or group chats.

<!--
| Format | From user to bot  | From bot to user |  Notes |                                                           
|:-------|:-------|:------------|:-------|
| Rich text | ✔ | ✔ | Including emoticons |  
| Pictures | ✔ | ✔ | PNG, JPEG or GIF up to 20Mb |
| Video | Coming soon | ✔ | MP4, AAC+h264 up to 15Mb (approx. 1 minute), plus JPEG thumbnail |
| Cards | ✔ | ✔ |  |
-->

## Bot settings

### Disabling a bot

To stop your bot receiving messages and remove it from directories go to your Bot Dashboard and edit the Microsoft Teams channel. Disable the bot in settings.

### Deleting a bot

To delete your bot completely go to your Bot Dashboard and edit the Microsoft Teams channel. Select the **Delete** button at the bottom.





 
