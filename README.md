# UiPath.Telegram
Telegram Bot activities are used to connect to Telegram application from UiPath application.
In order to use these activities they must be placed or enclosed within "Telegram Connector Scope".

Pre-requisites - Telegram Bot must be created using BotFather and the user must have the Token in order to communicate with other groups or users.

## Activities
1. Telegram Connector scope
2. Send Message
3. Send Image
4. Receive Message
 
## Telegram Connector scope
This is the parent activity within which all the below child activities **Send Message**, **Send Image** and **Receive message** can be executed.


## Send Message
In this activity Telegram Bot sends messages instantly to users or public group where Telegram Bot is also one of the users(of type admin).

### Input fields
- Chat ID - To accept the Chat ID of user or group. It's type is **Int64**.
  - *Example: Chat ID = 123456789 (private user) or Chat ID = -987654321*

- Text message - To accept the message or string to deliver to user or group. It's type is String.
  - *Example: Text message = "Welcome to the world of Bots!!!"*

## Send Photo
In this activity Telegram Bot sends Images or pictures instantly to users or public group.

### Input fields
- Chat ID - To accept the Chat ID of user or group. It's type is **Int64**.
  - *Example: Chat ID = 123456789 (private user) or Chat ID = -987654321*

- Image Path - To accept the physical location in computer where there the image exists. It's type is **String**.
  - *Example: Image Path = "D:\Images_Folder\test_image.png"*

- Image Text - To accept a description for the attached image. When no value is given, by default value "Image sent from Bot" is given. It's type is **String**.
  - *Example: Image Text = "Nice picture!"*

## Get Updates
In this activity Telegram Bot receives the text messages sent by the private user and users in group.

### Output fields
- Message List - Gives output of text messages in a list of strings. It's type is **List**<**String**>.
  - *Example: Message List = Msg_array (Variable Of type List of String)*
  

### Note:
Process to Get your Telegram chat ID

1. Paste the following link in your browser. Replace <API-access-token> with the API access token that you identified or created in the previous section:
  
https://api.telegram.org/bot<API-access-token>/getUpdates?offset=0

2. Send a message to your bot in the Telegram application. The message text can be anything. Your chat history must include at least one message to get your chat ID.

3. Refresh your browser.

4. Identify the numerical chat ID by finding the id inside the chat JSON object. In the example below, the chat ID is **123456789**.

{  
   "ok":true,
   "result":[  
      {  
         "update_id":XXXXXXXXX,
         "message":{  
            "message_id":2,
            "from":{  
               "id":**123456789**,
               "first_name":"Mushroom",
               "last_name":"Kap"
            },
            "chat":{  
               "id":**123456789**,
               "first_name":"Mushroom",
               "last_name":"Kap",
               "type":"private"
            },
            "date":1487183963,
            "text":"hi"
         }
      }
   }
}
