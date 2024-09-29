
---
description: イベントコマンドの処理
---

# イベントコマンド

`EventCommand` フォルダには、すべてのイベントコマンドクラスが含まれています。これらのクラスは `Core.ReactionInterpreter` によって解釈されます。 Manager.Events はオブジェクトにイベントを送信します。そして、イベントを受信すると、オブジェクトは新しい `Core.ReactionInterpreter` をインスタンス化します。

`EventCommand` クラスには、以下のメソッドが含まれます。

```javascript
initialize() {
    return null;
}

update(currentState, object, state) {
    return 1;
}

onKeyPressed(currentState, key) {
}

onKeyReleased(currentState, key) {
}

onKeyPressedRepeat(currentState, key) {
    return true;
}

onKeyPressedAndRepeat(currentState, key) {
    return true;
}

drawHUD(currentState) {
}
```

`initialize` メソッドは、他のメソッドのパラメータで `currentState` という名前で参照されるオブジェクトです。 `update` メソッドでは、リアクションにおいて現在のノード位置に追加されるノードの数を返す必要があります。0 を返すと、移動せず、このコマンドの更新を続けます。1 を返すと、現在のコマンドの次のコマンドに進みます。

