---
title: Create the users
description: In this step you learn how to create the Users that will participate in the Conversation.
---

# Create the Users

Each participant in a [Conversation](/conversation/concepts/conversation) is represented by a [User](/conversation/concepts/user) object and must be authenticated by the Client SDK. In a production application, you would typically store this user information in a database.

Execute the following commands to create two users, `Alice` and `Bob` who will log in to the Vonage Client and participate in the chat (Conversation).

```bash
vonage apps:users:create Alice
vonage apps:users:create Bob
```

This will return user IDs similar to the following:

```sh
Creating User... done
User ID: USR-8b888723-dd31-49f7-9a1f-39fda5e4a73f
```

Make a note of these as you'll need them later.