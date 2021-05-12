---
title: Create conversational tabs
author: laujan
description: Create conversational sub-entity chat for your channel tabs
keywords: teams tabs channel configurable 
ms.topic: conceptual
ms.author: lomeybur
---
# Create conversational tabs

Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity. A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user may want a more focused conversation. The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or the content changed over time, making the conversation irrelevant to the content being shown. Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.

Conversational sub-entities are only supported in channels. However, they can be used from a personal or static tab to create or continue conversations in tabs that are *already* pinned to a channel. The static tab is useful if you wish to provide one location for a user to view and access conversations happening across multiple channels.

## Requirements

In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database. We will provide you with the `conversationId`, but it will be your responsibility to store that `conversationId` and return it to Teams in order for users to continue the conversation.

## Starting a new channel tab conversation

To start a new conversation, you use the `openConversation()` function. Starting and continuing a conversation are all handled by this method, however, the inputs to the function change depending on which action you want to take. From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** takes the following inputs to start a conversation in a channel:

* **subEntityId**: This is the ID of your specific sub-entity. For example, task-123.
* **entityId**: This is the ID of the tab instance when it was created. The ID is important to refer back to the same tab instance.
* **channelId**: This is the channel in which the tab instance resides.
   > [!NOTE]
   > The **channelId** is optional for channel tabs. However, it is recommended if you wish to keep your implementation across channel and static tabs the same.
* **title**: This is the title that is shown to the user in the chat panel.

Most of these values can also be retrieved from the `getContext` API.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: ”Task Title”});
```

This will open the conversation panel.

![Conversationl Sub Entities - Start Conversation](~/assets/images/tabs/conversational-subentities/start-conversation.png)

If the user starts a conversation, it’s important to listen for the callback of that event in order  to retrieve and save the conversationId:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

The conversationReponse object contains information related to the conversation that was just started. We recommend you save all the properties of this response object for reuse later.

## Continuing a channel tab conversation

Now that a conversation has started, subsequent calls to `openConversation()` will require that you also provide the same inputs as above, but also include the conversationId. This will open the conversation panel for the user with the appropriate conversation in view. Users will be able to see new/incoming messages in real-time.

![Conversationl Sub Entities - Continue Conversation](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## Polishing your conversational tab

Finally, it’s important that your tab consumes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md) (e.g. user clicking the tab chiclet deeplink from the channel conversation). The expected behavior would be for you to receive the deeplink, open that sub-entity and then open the conversation panel for that specific sub-entity.

To support conversational sub-entities from your personal/static tab, you don’t have to change anything about your implementation. Keep in mind that we only support starting or continuing conversations from channel tabs that are already pinned. Supporting static tabs will allow you to provide a single location for your users to interact with all your sub-entities. It is however important that you save the `subEntityId`, `entityId` and `channelId` when your tab is originally created in a channel in order for you to have the right properties when opening the conversation view in a static tab.

## Additional functions

In addition to the above functions, you can also manually close the conversation view

```javascript
microsoftTeams.conversations.closeConversation();
```

Or listen for an event when the conversation view is closed by a user

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
