---
description: スタックマネージャーの処理方法を見ていきましょう。
---

# スタックとシーン

## スタック

`main.js` で `Manager.Stack` というクラスが使われていたのを見ましたね。まず、スタックとは何でしょうか？それはシーンを含む単純な配列です。

![](../.gitbook/assets/stack.png)

スタックの一番上は、描画される現在のシーンです。`push` を使用してスタックの一番上に新しいシーンを追加し、`pop` を使用して一番上のシーンを削除できます。`Manager/Stack.js` を確認してください。

## ベースシーン

それでは `Scene/Base.js` を開いてみましょう。すべてのシーンクラスはこのベースを拡張します。これは、反応の解釈（マップ内のオブジェクトの反応、一般的な反応）を処理します。すべてのシーンには、次の関数が含まれます。

```javascript
update() {
    ...
}
```

`update` は、シーンを描画する前にすべてのデータ更新を行うためのものです。

```javascript
onKeyPressed(key) {
    ...
}

onKeyReleased(key) {
    ...
}

onKeyPressedRepeat(key) {
    ...
}

onKeyPressedAndRepeat(key) {
    ...
}
```

すべての入力処理。`onKeyPressed` はキーが押されたときに、`onKeyReleased` はキーが離されたときに、`onKeyPressedRepeat` はキーが繰り返し押されたときに、`onKeyPressedAndRepeat` は最初の押下後わずかな間隔を置いてキーが繰り返し押されたとき（一般的にはメニューに使用されます）に呼び出されます。

```javascript
draw3D() {
    ...
}

drawHUD() {
    ...
}
```

データの更新後、描画関数が呼び出されます。`draw3D` は 3D のものを描画するためのもので、`drawHUD` は 2D のものを描画するためのものです。

```javascript
close() {
    ...
}
```

そして最後に、`close` 関数には、シーンがスタックから削除されるときに実行するすべてのものが含まれています。
