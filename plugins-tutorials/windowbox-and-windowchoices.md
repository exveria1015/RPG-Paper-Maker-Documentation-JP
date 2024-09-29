---
description: シーンにウィンドウを表示する方法
---

# WindowBox と WindowChoices

## WindowBox

`Core` モジュールの `WindowBox` クラスを使用して、特定のコンテンツを持つウィンドウボックスを描画できます。以下のようなものを描画できます。

![](../.gitbook/assets/windowbox.png)

シーンでのウィンドウボックス宣言の例を次に示します。

```javascript
this.exampleWindow = new RPM.Core.WindowBox(x, y, w, h, {
    // 以下のオプションは任意です
    content: new Graphic.Text("myText"), // コンテンツは Graphic.Base です
    padding: [0, 0, 0, h], // ボックスのパディング [x, y, x, h]
    limitContent: true // チェックされている場合、コンテンツはパディングに合わせてカットされます
});
```

そして、シーンの `drawHUD` でこのウィンドウを描画できます。

```javascript
drawHUD() {
    this.exampleWindow.draw();
}
```

## WindowChoices

`Core` モジュールの `WindowChoices` クラスを使用して、複数の `WindowBox` を選択肢として表示することもできます。

![](../.gitbook/assets/windowchoices.png)

シーンでの選択肢ウィンドウの使用例を次に示します。

```javascript
this.exampleChoices = new RPM.Core.WindowChoices(x, y, w, h, [new Graphic.Text("A"), new Graphic.Text("B")], {
    // 以下のオプションは任意です
    listCallbacks: [myfunction1, myFunction2], // 押されたときに実行されるすべてのコールバック関数のリスト
    orientation: OrientationWindow.Vertical, // ウィンドウの向き（水平または垂直）
    nbItemsMax: 2, // 選択肢ボックスに表示する最大項目数
    padding: WindowBox.SMALL_SLOT_PADDING, // ボックスのパディング
    space: 0, // ボックス内の各選択肢間のスペース
    currentSelectedIndex: 0, // 選択肢ボックス内の現在選択されているインデックスの位置
    bordersInsideVisible: true // チェックされている場合、各選択肢に個別のウィンドウボックスが表示されます
});
```

入力を処理します。

```javascript
onKeyPressed(key) {
    this.windowChoicesCommands.onKeyPressed(key, this);
}

onKeyPressedAndRepeat(key) {
    return this.exampleChoices.onKeyPressedAndRepeat(key);
}
```

`onKeyPressed` は、選択肢でEnterキーを押したときのコールバック（関数）を処理するためのものです。ここでの2番目の引数は `this` ですが、コールバック内の `this` を置き換える任意のものに置き換えることができます。 `onKeyPressedAndRepeat` は、選択肢を切り替えるための移動キーを処理するためのものです。

そして、シーンの `drawHUD` で選択肢を描画できます。

```javascript
drawHUD() {
    this.exampleChoices.draw();
}
```

## グラフィックス

`WindowBox` と `WindowChoices` の例では、`Graphic.Text` クラスを使用しています。実際には、`Graphic` モジュールには多くのクラスがあります。最も興味深いものを以下に示します。

### Graphic.Text

単純なテキストを表示します。

```javascript
new Graphic.Text('mytext', {
    x: 0,
    y: 0,
    w: 0,
    h: 0,
    align: Align.Left,
    fontSize: Utils.defaultValue(Datas.Systems.dbOptions.v_tSize, Constants.DEFAULT_FONT_SIZE),
    fontName: Utils.defaultValue(Datas.Systems.dbOptions.v_tFont, Constants.DEFAULT_FONT_NAME),
    verticalAlign: AlignVertical.Center,
    color: Utils.defaultValue(Datas.Systems.dbOptions.v_tcText, System.Color.WHITE),
    bold: false,
    italic: false,
    backColor: Utils.defaultValue(Datas.Systems.dbOptions.v_tcBackground, null),
    strokeColor: Utils.defaultValue(Datas.Systems.dbOptions.tOutline, false) ? Utils.defaultValue(Datas.Systems.dbOptions.v_tcOutline, null) : null
});
```

### Graphic.TextIcon

アイコン付きの単純なテキストを表示します。

```javascript
new Graphic.TextIcon("myText", iconID, {
    side: Align.Left,
    align: Align.Left,
    space: Constants.MEDIUM_SPACE
});
```

### Graphic.Message

タグ付きの複雑なテキストを表示します。ShowTextコマンドで使用されます。

```javascript
new Graphic.Message("<b>myText</b>", facesetID);
```

### Graphic.Player

メインメニューのように選択肢ボックスにプレイヤーを描画したり、戦闘のようにプレイヤーの情報を描画したりします。

```javascript
new Graphic.Player(player, reverse);
```

### Graphic.PlayerDescription

選択肢ボックスにプレイヤーを描画したり、プレイヤーの説明を描画したりします。

```javascript
new Graphic.PlayerDescription(player);
```
