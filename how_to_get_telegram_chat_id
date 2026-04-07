# 如何获取 Telegram 机器人聊天 ID（Chat ID）

**内容目录：**
1. #创建-telegram-机器人并获取-bot-token
1. #获取私聊private-chat的-chat-id
1. #获取频道channel的-chat-id
1. #获取群组group-chat的-chat-id
1. #获取群组中话题topic的-chat-id

---

## 创建 Telegram 机器人并获取 Bot Token

1. 打开 Telegram 应用，搜索 `@BotFather`。
2. 点击 **Start**（开始）。
3. 点击菜单 -> `/newbot` 或者直接输入 `/newbot` 并发送。
4. 按照提示操作，直到收到类似如下的消息：
   ```
   Done! Congratulations on your new bot. You will find it at t.me/new_bot.
   You can now add a description.....

   Use this token to access the HTTP API:
   63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c
   Keep your token secure and store it safely, it can be used by anyone to control your bot.

   For a description of the Bot API, see this page: https://core.telegram.org/bots/api
   ```
5. 这里的 `63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c` 就是我们的 **Bot Token**（请勿分享给任何人）。

#如何获取-telegram-机器人聊天-idchat-id

---

## 获取私聊（Private Chat）的 Chat ID

1. 搜索并打开我们刚创建的 Telegram 机器人。
2. 点击 **Start** 或发送任意消息。
3. 在浏览器中打开此 URL：`https://api.telegram.org/bot{我们的_bot_token}/getUpdates`
   - 注意：需要在 Token 前加上 `bot` 前缀。
   - 示例：`https://api.telegram.org/bot63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c/getUpdates`
4. 我们将看到类似这样的 JSON 响应：
   ```json
   {
     "ok": true,
     "result": [
       {
         "update_id": 83xxxxx35,
         "message": {
           "message_id": 2643,
           "from": {...},
           "chat": {
             "id": 21xxxxx38,
             "first_name": "...",
             "last_name": "...",
             "username": "@username",
             "type": "private"
           },
           "date": 1703062972,
           "text": "/start"
         }
       }
     ]
   }
   ```
5. 查看 `result.0.message.chat.id` 的值，这就是我们的 **Chat ID**：`21xxxxx38`。
6. 测试发送消息：`https://api.telegram.org/bot63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c/sendMessage?chat_id=21xxxxx38&text=test123`
7. 如果 Bot Token 和 Chat ID 正确，我们应该能在 Telegram 机器人的对话框中收到 `test123` 消息。

#如何获取-telegram-机器人聊天-idchat-id

---

## 获取频道（Channel）的 Chat ID

1. 将我们的 Telegram 机器人添加到某个频道（Channel）中。
2. 向该频道发送一条消息。
3. 打开此 URL：`https://api.telegram.org/bot{我们的_bot_token}/getUpdates`
4. 我们将看到类似这样的 JSON 响应：
   ```json
   {
     "ok": true,
     "result": [
       {
         "update_id": 838xxxx36,
         "channel_post": {...},
           "chat": {
             "id": -1001xxxxxx062,
             "title": "....",
             "type": "channel"
           },
           "date": 1703065989,
           "text": "test"
         }
       }
     ]
   }
   ```
5. 查看 `result.0.channel_post.chat.id` 的值，这就是我们的 **Chat ID**：`-1001xxxxxx062`。
6. 测试发送消息：`https://api.telegram.org/bot63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c/sendMessage?chat_id=-1001xxxxxx062&text=test123`
7. 如果配置正确，消息 `test123` 应该会发送到我们的 Telegram 频道中。

#如何获取-telegram-机器人聊天-idchat-id

---

## 获取群组（Group Chat）的 Chat ID

获取群组 Chat ID 最简单的方法是使用 Telegram 桌面客户端。

1. 打开 Telegram 桌面应用程序。
2. 将我们的 Telegram 机器人添加到群组中。
3. 向群组发送一条消息。
4. 右键点击该消息，选择 **Copy Message Link（复制消息链接）**。
   - 我们会得到一个类似这样的链接：`https://t.me/c/194xxxx987/11/13`
   - 链接结构为：`https://t.me/c/{group_chat_id}/{group_topic_id}/{message_id}`
   - 因此，这里的群组 Chat ID 是：`194xxxx987`
5. 要在 API 中使用该 ID，需要在前面加上 `-100` 前缀，变为：`-100194xxxx987`。
6. 现在测试发送消息：`https://api.telegram.org/bot63xxxxxx71:AAFoxxxxn0hwA-2TVSxxxNf4c/sendMessage?chat_id=-100194xxxx987&text=test123`
7. 如果设置正确，消息 `test123` 应该会出现在我们的群组中。

#如何获取-telegram-机器人聊天-idchat-id

---

## 获取群组中话题（Topic）的 Chat ID

如果想向 Telegram 群组中的特定话题（Topic）发送消息，我们需要获取话题 ID。

1. 与上面的步骤类似，点击 **Copy Message Link** 后，我们会得到类似链接：`https://t.me/c/194xxxx987/11/13`，其中的 `11` 就是 **Topic ID（话题 ID）**。
2. 调用 API 时使用 `message_thread_id` 参数，示例如下：
   `https://api.telegram.org/bot783114779:AAEuRWDTFD2UQ7agBtFSuhJf2-NmvHN3OPc/sendMessage?chat_id=-100194xxxx987&message_thread_id=11&text=test123`
3. 如果 Bot Token、Chat ID 和 Topic ID 都正确，消息 `test123` 将会发送到指定的群组话题中。
