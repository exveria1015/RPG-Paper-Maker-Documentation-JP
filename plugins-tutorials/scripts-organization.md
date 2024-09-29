---
description: スクリプトの構成方法について理解する
---

# スクリプト構成

## システム

システムコードはECMAScriptモジュールを使用しているため、すべてのモジュールはモジュール名と同じフォルダにまとめられています。 `System` フォルダを確認してください：

![System Modules](../.gitbook/assets/system-modules.png)

以下はモジュールの説明です：

* `Common`：主に静的プロパティとメソッドを取得するために使用されるすべての静的クラス (Mathf, Paths...)
* `Core`：ゲームの実行で直接使用されるすべてのコアクラス (Autotiles, WindowBox...)
* `Datas`：JSONゲームファイルを読み取るすべてのシステムクラスをグループ化するすべてのデータクラス

    &#x20;(Heroes, Systems...)
* `EventCommand`：リアクションで解釈できるすべてのイベントコマンド (ShowText, Wait...)
* `Graphic`：WindowBoxクラス内に描画するために使用されるすべてのグラフィッククラス (Text, Player...)
* `Manager`：特定のゲームイベントを管理するために使用されるすべてのマネージャークラス (Collisions, Plugins...)
* `Scene`：すべてが描画されるすべてのシーンクラス (Map, Menu...)
* `System`：データからJSONを読み取るすべてのシステムクラス (Color, Monster...)

これらのモジュールがどのように使用されるかは、このチュートリアルで徐々に見ていきます。

各 `*.js` ファイルには、 `*.d.ts` も付属しています。

![System Example](../.gitbook/assets/system-example.png)

`*.d.ts` については気にする必要はありません。これらのファイルは、Visual Studio Codeがオートコンプリートを正しく入力できるようにするために用意されています。

{% hint style="info" %}
実際、RPG Paper Makerの元のコードはTypeScriptで書かれています。TypeScriptはJavaScriptですが、型指定の制限があります。TypeScriptコードはJavaScript Standardコードにコンパイルされ、これらの `*.d.ts` も提供されます。
{% endhint %}

## シェーダー

`Shaders` フォルダには、3Dで使用されるすべてのシェーダーが含まれています。簡単に言うと、シェーダーはCPUではなくグラフィックカードで実行される小さなプログラムです。後ほど、どのように使用されるかを見ていきます。

![Shader Expample](../.gitbook/assets/shaders-example.png)

## ライブラリ

`Libs` フォルダには、RPG Paper Makerで使用されるすべての外部ライブラリが含まれています。

![Libs Example](../.gitbook/assets/libs-example.png)

以下を使用しています。

* `howler.js`：すべての曲を非常に簡単に再生管理するライブラリです。
* `three.js`：最も重要なライブラリです。WebGL（3D）を非常に簡単に扱うための多くの関数とクラスを提供しています。私たちのコードでは、これらをたくさん目にすることになります。ドキュメントはこちらで確認できます：[https://threejs.org/docs/](https://threejs.org/docs/) RPG Paper Makerでの使用方法を簡単に理解することができます。

## プラグイン

将来作成するすべてのプラグインは、この `Plugins` フォルダに入ります。

![Plugin Example](../.gitbook/assets/plugins-example.png)

後ほど、どのように管理されるかを見ていきます。

## コードはどこから始まるのか？

さて、ここで疑問が出てきます。すべてのコードはどこから始まるのでしょうか？それは `System/main.js` にあります。中身で何が起こっているのか、簡単に見てみましょう。

```javascript
let loaded = false;
/**
 *  ゲームスタックとデータを初期化する。
 */
async function initialize() {
    await Manager.Plugins.load();
    Manager.Stack.loadingDelay = 0;
    Manager.Songs.initialize();
    Manager.Stack.clearHUD();
    await load();
}
```

まず、 `initialize` 関数を定義しています。最初にプラグインを読み込み、次にいくつかのマネージャー (`Manager.Stack` と `Manager.Songs`) を初期化し、 `load` 関数を使用してデータ（ゲームJSON内のデータ）を読み込みます。

```javascript
/**
 *  ゲームスタックとデータを読み込む。
 */
async function load() {
    await Datas.Settings.read();
    await Datas.Systems.read();
    await Datas.Variables.read();
    await Datas.Pictures.read();
    await Datas.Songs.read();
    await Datas.Videos.read();
    await Datas.Shapes.read();
    Manager.GL.load();
    Manager.GL.initialize();
    Manager.GL.resize();
    await Datas.SpecialElements.read();
    await Datas.Tilesets.read();
    await Datas.Items.read();
    await Datas.Skills.read();
    await Datas.Weapons.read();
    await Datas.Armors.read();
    await Datas.Classes.read();
    await Datas.Heroes.read();
    await Datas.Monsters.read();
    await Datas.Troops.read();
    await Datas.BattleSystems.read();
    await Datas.TitlescreenGameover.read();
    await Datas.Keyboards.read();
    await Datas.Animations.read();
    await Datas.CommonEvents.read();
    await Datas.Systems.getModelHero();
    await Datas.Systems.loadWindowSkins();
    Manager.Stack.pushTitleScreen();
    loaded = true;
    Manager.Stack.requestPaintHUD = true;
}
```

すべてが読み込まれると、タイトル画面のシーンが初期化され、読み込みが完了したことが通知されます。ゲームのメインループは `loop` 関数です。

```javascript
/**
 *  ゲームのメインループ。
 */
function loop() {
    requestAnimationFrame(loop);
    // すべてが読み込まれている場合に更新
    if (loaded) {
        if (!Manager.Stack.isLoading()) {
            Manager.Stack.update();
        }
        if (!Manager.Stack.isLoading()) {
            Manager.Stack.draw3D();
        }
    }
    Manager.Stack.drawHUD();
    // 経過時間
    Manager.Stack.elapsedTime = new Date().getTime() - Manager.Stack
        .lastUpdateTime;
    Manager.Stack.averageElapsedTime = (Manager.Stack.averageElapsedTime +
        Manager.Stack.elapsedTime) / 2;
    Manager.Stack.lastUpdateTime = new Date().getTime();
}
```

これは、以下によって呼び出されます。

```javascript
// -------------------------------------------------------
//
// ループ開始
//
// -------------------------------------------------------
requestAnimationFrame(loop);
```

これは基本的に、現在のシーン（開始時は `Scene.TitleScreen`）を更新して描画しています。

最後に、入力は以下によって管理されます。

```javascript
Inputs.initialize();
```

次のチュートリアルでは、 `Manager.Stack` がどのように処理されるかを見ていきます。
