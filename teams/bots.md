# Creating bots for Microsoft Teams

**TODO reviewers:** This topic is structured based on the [Getting Started with SKype Bots](https://docs.botframework.com/en-us/skype/getting-started/#navtitle) topic. Please review it carefully to make sure that the information correctly applies to Microsoft Team bots as well. Thanks!

Build and connect intelligent bots to interact with Microsoft Teams users naturally through 1:1 chat.

> **Note:** At this time, Microsoft Teams bots support 1:1 chat, but do not support channels or group chats.

## Creating a Microsoft Teams bot

All bots created using the Microsoft Bot Framework are automatically configured and ready to work in Microsoft Teams.

See the [Microsoft Bot Framework Overview](https://docs.botframework.com/en-us/) to learn how to:

1. Build a bot using the [C# SDK](https://docs.botframework.com/en-us/csharp/builder/sdkreference/), [Node.js SDK](https://docs.botframework.com/en-us/node/builder/chat-reference/modules/_botbuilder_d_.html) or [Skype REST API](https://docs.botframework.com/en-us/skype/chat).
	
	**TODO reviewers:** Do Team bots work with the Skype REST API?

2. Test it using the [Bot Framework Emulator](https://docs.botframework.com/en-us/tools/bot-framework-emulator/)
3. Deploy the bot to a cloud service, such as [Microsoft Azure](https://azure.microsoft.com/)
4. Register the bot with the Microsoft Bot Framework, and make sure you add Microsoft Teams as a channel. When you first register a bot it will be in Preview, which means it can be added by up to 100 users using [an add button or URL](#add-button-or-URL). To remove the limit you can easily publish it in Microsoft Teams using the Microsoft Bot Framework.
	
	**TODO reviewers:** Is the rest of this info about preview correct as well?

5. [Add the bot](#adding-a-bot) to a Microsoft Teams 1:1 chat, and test.

## Publishing

Publish your bot from the [Bot Dashboard](https://dev.botframework.com/bots) to remove user limits and request for it to be shown in the Microsoft bot directory. You can choose to automatically show in directories, or enable it later from the Bot Dashboard. Microsoft Teams will review your bot to remove the limit, and may select it for the Microsoft bot directory.

**TODO reviewers:** I removed references to a Microsoft(Skype) Teams Bot directory, since I'm assuming Teams doesn't have a bot directory yet, since search for bots isn't enabled yet. Is that correct?

> **Note:** Currently, People search is not enabled to find bots written in the Bot Framework.

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

## Finding and adding bots in Microsoft Teams

Users can find and add your Microsoft Teams bot in several ways.

### Add button or URL

**TODO reviewers:** This is from the Skype docs. Is this something Microsoft Teams is offering right now? 

You can create an add button here or copy and paste the add URL from the bot dashboard which will look like this 

`https://join.skype.com/bot/YourAppID`

For example:  `https://join.skype.com/bot/29415286-5a43-4a00-9dc5-bcbc2ce1f59e`

When a user taps or clicks the add button or add URL they will be prompted to sign into Microsoft Teams if necessary and redirected to a page with information about your bot and its capabilities. After they tap to add your bot they will be redirected straight into a chat with the bot in a Microsoft Teams app or the Microsoft Teams web app.

### Microsoft bot directory

Bots that are approved for Microsoft Teams may also appear in the Microsoft bot directory

### How a bot appears in Microsoft Teams

Once a bot has been added it will appear in your conversation history in the same way as a chat with another user, but with a hexagonal avatar.

Bots in Microsoft Teams always appear online and do not have a mood message

## Messages

Your bot can send rich text, emoticons, pictures and cards to a 1:1 chat. Users can send rich text and pictures to your bot. You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.

For more information on the format and attributes of these message types, see  the **[Messages](https://docs.botframework.com/en-us/skype/getting-started/#navtitle)** section of [Getting Started with Skype bots](https://docs.botframework.com/en-us/skype/getting-started/#messsages). Microsoft Teams supports the message types listed in this topic, with the following limitations:

* For messages, Microsoft Teams bots currently do not support Skype emoticons.
* For card types, Microsoft Teams bot currently does not support the receipt card type.
* For card actions, Microsoft Teams bots currently does not support the postBack action.

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





 
