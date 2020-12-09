---
title:  カンバセーションイベントを取得する
description:  このステップでは、このカンバセーションの一部として送信済みのメッセージを表示します

---

カンバセーションイベントを取得する
=================

`getConversation()`メソッドの下に、イベントを取得するメソッドを追加してみましょう：

```java
private void getConversationEvents(NexmoConversation conversation) {
    conversation.getEvents(100, NexmoPageOrder.NexmoMPageOrderAsc, null,
            new NexmoRequestListener<NexmoEventsPage>() {
                @Override
                public void onSuccess(@Nullable NexmoEventsPage nexmoEventsPage) {
                    _conversationEvents.postValue(new ArrayList<>(nexmoEventsPage.getPageResponse().getData()));
                }

                @Override
                public void onError(@NonNull NexmoApiError apiError) {
                    _errorMessage.postValue("Error: Unable to load conversation events " + apiError.getMessage());
                }
            });
}
```

イベントが取得されたら（またはエラーが返されたら）、ビュー（`ChatFragment`）を更新して新しいデータを反映します。

> **注：** 私たちは2つの`LiveData`ストリームを使用しています。`_conversationMessages`で成功したAPIレスポンスを投稿し、`_errorMessage`で返されたエラーを投稿します。

私たちのビューが新しいデータに反応するようにしましょう。`ChatFragment`内で`private var conversationMessages = Observer<List<NexmoEvent>?>`プロパティを見つけ、会話の履歴を処理するために、このコードを追加します：

```java
private var conversationMessages = Observer<List<NexmoEvent>?> { events ->
    val messages = events?.mapNotNull {
        when (it) {
            is NexmoMemberEvent -> getConversationLine(it)
            is NexmoTextEvent -> getConversationLine(it)
            else -> null
        }
    }

    conversationMessagesTextView.text = if (messages.isNullOrEmpty()) {
        "Conversation has No messages"
    } else {
        messages.joinToString(separator = "\n")
    }

    progressBar.isVisible = false
    chatContainer.isVisible = true
}
```

メンバー関連のイベント（メンバーの招待、参加または参加解除）を処理するには、`fun getConversationLine(memberEvent: NexmoMemberEvent)`メソッドの本文を埋める必要があります：

```java
private fun getConversationLine(memberEvent: NexmoMemberEvent): String {
    val user = memberEvent.member.user.name

    return when (memberEvent.state) {
        NexmoMemberState.JOINED -> "$user joined"
        NexmoMemberState.INVITED -> "$user invited"
        NexmoMemberState.LEFT -> "$user left"
        else -> "Error: Unknown member event state"
    }
}
```

上記のメソッドは`NexmoMemberEvent`を`String`に変換し、チャットの会話で1行として表示されます。同様の変換は、`NexmoTextEvent`のために行う必要があります。`getConversationLine(textEvent: NexmoTextEvent)`メソッドの本文を埋めてみましょう：

```java
private String getConversationLine(NexmoTextEvent textEvent) {
    String user = textEvent.getFromMember().getUser().getName();
    return "$user said: " + textEvent.getText();
}
```

> **注：** このチュートリアルでは、メンバー関連のイベント`NexmoMemberEvent`と`NexmoTextEvent`のみを処理しています。上記の`when`式（`else -> null`）では、他の種類のイベントは無視されます。

これで最初のメッセージを送信する準備ができました。
