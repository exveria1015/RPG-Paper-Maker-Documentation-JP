---
description: 新しいプラグインを作成する手順を紹介します。
---

# プラグインの作成方法

独自のプラグインを作成するための準備が整いましたので、早速始めましょう！

スクリプトマネージャーを開きます。

![](../.gitbook/assets/script-manager.png)

{% hint style="info" %}
別のタブで、System、Libs、Shadersフォルダー内のファイルを確認することもできます。
{% endhint %}

それでは、最初のプラグインを作成してみましょう。空のプラグインをダブルクリックして、空のプラグインを作成します。

![](../.gitbook/assets/create-plugin.png)

`Edit`タブでは、いくつかのオプションにアクセスできます。

![](../.gitbook/assets/plugin-edit.png)

* `Name`：プラグイン名。プロジェクト内で一意である必要があります。
* `Author`：ここに自分の名前を入力できます。
* `Description`：プラグインの機能を記述します。
* `Version`：プラグインのバージョン。`X.X.X` の形式である必要があります。
* `Website`：プラグインに関連するウェブサイトのURL。
* `Tutorial`：この特定のプラグインに関連するチュートリアルのURL。
* `Category`：プラグインのカテゴリ。次のいずれかになります。
  * `Battle`
  * `Menus`
  * `Map`
  * `Others`
* `Parameters`：プラグインのパラメータ。これについては、以下で詳しく説明します。
* `Commands`：プラグインのコマンド。これについては、以下で詳しく説明します。

Visual Studio Codeの代わりにエンジン内で直接プラグインコードを編集したい場合は、`Code`タブにアクセスすることもできます。

![](../.gitbook/assets/plugin-code.png)

Visual Studio Codeで確認すると、`Plugins`フォルダー内に新しいフォルダーが作成されていることがわかります。

![](../.gitbook/assets/plugins-folder.png)

新しいプラグインを作成するたびに、プラグイン名と同じ名前のフォルダーが作成されます。このフォルダーには、次のものが含まれます。

* `code.js`：プラグインコードを含むJSファイル。
* `details.json`：プラグインのすべての詳細（作成者、説明、パラメータなど）。

それでは、コンソールに「Hello world」と表示するだけのプラグインを作成してみましょう。

```javascript
import { RPM } from "../path.js"

const pluginName = "MyFirstPlugin";
const inject = RPM.Manager.Plugins.inject;

console.log("Hello world!");
```

これでプレイテストができます。コンソールを表示するには、`CTRL + ALT + I`キーを押します。

![](../.gitbook/assets/console-hello-world.png)

`RPM`モジュールをインポートすることで、RPG Paper Makerのデータにアクセスすることもできます。

```javascript
import { RPM } from "../path.js"
```

そのため、他の`System`モジュールの前に`RPM`モジュールを使用する必要があります。例：

```javascript
import { RPM } from "../path.js"

const pluginName = "MyFirstPlugin";
const inject = RPM.Manager.Plugins.inject;

console.log("Hello world: " + RPM.Core.MapObject.SPEED_NORMAL);
```

![](../.gitbook/assets/console-rpm.png)

素晴らしい！うまくいきました！

## アプリへのコードの挿入

Systemアプリを拡張する方法を見ていきましょう。新しいプラグインを作成する際にデフォルトでインポートされる`inject`関数を使用できます（4行目）。

```javascript
const inject = RPM.Manager.Plugins.inject;
```

### Inject関数の構文

Inject関数は、既存のクラスを変更するために通常必要となるプロトタイピングを置き換えるように設計されています。injectはより合理化されており、エイリアスを作成する必要がありません。

`inject`関数を使用せずに既存のメソッドを挿入する方法の例を以下に示します。

```javascript
let alias_load = RPM.Scene.TitleScreen.prototype.load;
RPM.Scene.TitleScreen.prototype.load = async function() {
    await alias_load.apply(this);
    console.log("Title screen loaded!")
}
```

これにより、`alias_load`というエイリアスが作成され、`RPM.Scene.TitleScreen`から`load`メソッドのプロトタイプを書き換えます。`apply`を使用してエイリアスを呼び出します。これは、タイトル画面の読み込み時にデフォルトで実行されるRPMの動作です。その後ろに独自のコードを追加することで、タイトル画面の読み込みが完了したときに`"Title screen loaded!"`と表示されます。

次に、inject関数を使用する場合の例を以下に示します。

```javascript
inject(RPM.Scene.TitleScreen, "load", async function() {
    console.log("Title screen loaded!");
}, false, false, true);
```

よりシンプルでわかりやすくなりました！

各引数の詳細をコメントで説明します。

```javascript
inject(
    RPM.Scene.TitleScreen, // コードを挿入/上書きするクラス。
    "load", // コードを挿入/上書きする変数/関数名。
    async function() { console.log("Title screen loaded!");}, // 挿入/上書きする新しい変数/関数。
    false, // 変数/関数が静的かどうかをここで指定します（注：静的変数/関数と非静的変数/関数は、同じ名前で同時に存在できます）。（デフォルト：false）
    false, // （関数のみ）trueの場合、コードを上書きします（元のコードは呼び出されません）。falseの場合、コードを挿入します。（デフォルト：false）
    true); // （関数のみ）trueの場合、独自のコードの前に元の関数のコードを実行します。（デフォルト：true）
```

{% hint style="info" %}
**アロー関数構文（() => {}）を使用しないでください。アロー関数には「this」がないため、挿入時に機能しません。例のように、代わりにfunction（function（）{}）を使用してください。**&#x20;
{% endhint %}

### thisの拡張

injectの性質上、`this`には2つの新しい値が追加されます。

* `callResult`：`loadBefore`がtrueに設定されており、関数が戻り値を返す関数の場合、最初の関数の結果が返されます。これにより、値を変更/通過させることができます。
* `super`：エイリアスコールを条件付きにする場合、またはコードの途中で発生させる場合は、overwriteがtrueに設定されている場合にのみsuperを呼び出すことをお勧めします。そうしないと、エイリアスが2回呼び出されます。

使用例：

```javascript
inject(MyClass, "myFunction", function() {
    if (this.isOk()) {
        console.log("this is my class :)");
    } else {
        this.super(); // 一部の条件では上書きされません
    }    
}, false, true, false); // 上書きを使用

inject(MyClass, "myFunction2", function() {
    if(this.callResult === 2) {
        return 4;
    } else {
        return this.callResult; // 元のコードの戻り値を返します
    }
}, false, false, true); // 上書きなし、loadBefore
```

### 使用例を試してみましょう！

それでは、RPMコード内の既存の関数プロトタイプを編集してみましょう。例として、タイトル画面にアイコンを表示してみましょう。これを行うには、次の2つの関数を拡張する必要があります。

* `load`：表示するアイコンを読み込む
* `drawHUD`：読み込んだアイコンを描画する

```javascript
import { Datas } from "../../System/index.js";
import { RPM } from "../path.js"

const pluginName = "MyFirstPlugin"; // ここでプラグイン名を変更します
const inject = RPM.Manager.Plugins.inject;

// アイコンを読み込む
inject(RPM.Scene.TitleScreen, "load", async function() {
    this.pictureIcon = RPM.Datas.Pictures.getPictureCopy(RPM.Common.Enum.PictureKind.Icons, 1);
}, false, false, true);

// アイコンを描画する
inject(RPM.Scene.TitleScreen,"drawHUD", function() {
    this.pictureIcon.draw(200, 200);
}, false, false, true);

```

これでうまくいきました！

![](../.gitbook/assets/plugin-icon.png)

## 静的関数/変数

すべての変数/関数がクラスインスタンスの一部であるわけではありません。一部はクラスに静的に割り当てられており、そのため、そのクラスのインスタンスなしでアクセスできます。

```javascript
const inject = RPM.Manager.Plugins.inject;

class myClass {
    static myStaticFunction() {
        return 2;
    }
}

inject(myClass,"myStaticFunctions", function() {
    return 4
}, true, true, false);
```

## パラメータ

タイトル画面にアイコンを表示する前の例に戻りましょう。ユーザー（このプラグインを使用する人）が表示するアイコンIDを選択できるようにしたいとします。ここでパラメータを使用できます！

![](../.gitbook/assets/plugin-parameter.png)

コード側では、iconIDパラメータを取得するようにload関数を編集する必要があります。パラメータ値を取得するには、`getParameter(pluginName, parameterName)`を使用します。

```javascript
inject(RPM.Scene.TitleScreen, "load", async function() {
       this.pictureIcon = RPM.Datas.Pictures.getPictureCopy(RPM.Common.Enum.PictureKind.Icons, RPM.Manager.Plugins.getParameter(pluginName, "iconID"));
}, false, false, true);
```

これで、プラグインユーザーは次のようにパラメータ値を変更できます。

![](../.gitbook/assets/plugin-parameter-user.png)

## コマンド

プラグインをカスタムイベントコマンドに関連付けることもできます！素晴らしい！非常に簡単な例を作成してみましょう。`print`という名前のコマンドを作成し、コンソールに必要なテキストを出力します。ここでは、エディター側で作成します。

![](../.gitbook/assets/plugin-create-command.png)

作成したので、コマンドアクションを登録するためにプラグインコードを再度編集しましょう。`registerCommand(pluginName, commandName, commandFunction)`を使用して定義する必要があります。

```javascript
RPM.Manager.Plugins.registerCommand(pluginName, "console", (text) => {
    console.log(text);
});
```

このコマンドを使用するには、イベントコマンド`Plugin...`を作成し、プラグインとコマンドを選択します。

![](../.gitbook/assets/plugin-command.png)

トリガーすると、コンソールにテキストが出力されます！

![](../.gitbook/assets/plugin-command-render.png)

## 複雑なパラメータ

パラメータに、より複雑な値を指定することもできます。1つ目は`Custom structure`で、JavaScriptの`Object`に似ています。

![](../.gitbook/assets/plugin-parameter-custom-structure.png)

{% hint style="warning" %}
返されるパラメータは、深いパラメータ検索の後、`System.DynamicValue`になることに注意してください。そのため、`x`の値を取得する場合は、`RPM.Manager.Plugins.getParameter(pluginName, "Size").x.getValue()`を実行する必要があります。
{% endhint %}

もう1つは`Custom list`です。JavaScriptの`Array`に似ています。

![](../.gitbook/assets/plugin-parameter-custom-list.png)

{% hint style="warning" %}
カスタムリストについても、動的な値を取得することを忘れないでください！この例では、`RPM.Manager.Plugins.getParameter(pluginName, "Size")[0].getValue()`を使用して、最初のリスト値を取得できます。
{% endhint %}

`Hero`、`Monster`、`Weapon`などの他のすべての値は、ID値を返します。

## プラグインのエクスポート（オンライン提出）

オンラインプラグインを提出するには、GitHub wikiの次のガイドに従ってください。[https://github.com/RPG-Paper-Maker/RPG-Paper-Maker/wiki/Online-plugins-submission](https://github.com/RPG-Paper-Maker/RPG-Paper-Maker/wiki/Online-plugins-submission).


