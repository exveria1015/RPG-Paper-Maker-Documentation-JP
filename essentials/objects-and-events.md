# オブジェクトとイベント

あなたは美しいマップの作成方法を知っていますが、NPC、宝物などを追加してマップを生き生きとしたものにしたいと思うでしょう。これらの要素は`オブジェクト`と呼ばれます。これらのオブジェクトは、`イベント`（主人公の行動、クロノメーター、攻撃など）にも反応します。オブジェクトとイベントは、マップを活性化し、ゲームのストーリーを作成するためのものです！

## イベント <a href="#events" id="events"></a>

**/! RPG Paper Maker のイベントは、RM クラシックシリーズのイベントとは異なる概念です。**

`システムマネージャー > イベント/ステート`でイベントにアクセスできます。

![](../.gitbook/assets/systems-manager-events-states.png)

イベントは、重要なことが起こったことを表し、マップ内のオブジェクトはそれに反応したり、しなかったりします。イベントとは、たとえば、主人公がアクションボタンを押したことや、雨が降り始めたことなどです。これらのイベントは、他のオブジェクトによってオブジェクトに送信されます。イベントには2つのタイプがあります。

* **システムイベント**（時間、キーボードの押下など）。マップ内のオブジェクトではなく、ゲームシステム自体によって送信されます。
* **ユーザーイベント**（クエストの完了、剣のヒットなど）。自分で作成し、ローカルオブジェクトを介して送信できます。

イベントには`パラメータ`も含まれます。たとえば、バックグラウンドで3秒ごとにサウンドを再生する場合は、パラメータtime = 3000（ミリ秒）、repeat = ONを使用して時間イベントを使用できます。パラメータを使用してできるすばらしいことを想像してみてください（たとえば、パワーパラメータを取る剣のヒットイベント）。イベントのパラメータを編集するときは、パラメータのデフォルト値を選択できます。

**/! 物理現象とイベントを混同しないでください。風のアニメーションや重力などにイベントを使用しないでください。**

## リアクション <a href="#reactions" id="reactions"></a>

リアクションは、順番に実行されるコマンドのツリーです。たとえば、コマンドは、画面にテキストを表示したり、マップ内の特定のオブジェクトを移動したりすることができます。リアクションの例を次に示します。

![](../.gitbook/assets/example-reaction.png)

このリアクションは、変数 myValue が2と等しいかどうかをチェックします。OKの場合、「OKです！」というメッセージが表示されます。そうでない場合は、「後でもう一度やり直してください。」というメッセージが表示されます。

リアクションに新しいコマンドを編集/追加するには、対応するノードを`ダブルクリック`します。これにより、コマンドの大きなリストを含むこのウィンドウが開きます。

![](../.gitbook/assets/event-commands.png)

これらのコマンドの詳細については、後で1つずつ説明します。

キーボード検索を使用してコマンドをすばやく検索する方法もあります。

![](../.gitbook/assets/commands-keyboard.png)

対応するコマンドノードを`右クリック`して、コピー/貼り付け/削除することもできます。

## 共通リアクション <a href="#common-reactions" id="common-reactions"></a>

同じコマンドセットを何度もコピーしていることに気付いた場合は、共通リアクションの作成を検討する必要があります。 `システムマネージャー > 共通リアクション`でこれらにアクセスできます。

![](../.gitbook/assets/common-reactions.png)

この方法では、常にコピーする代わりに、この共通リアクションを呼び出すことができます。リアクションにバリエーションがある場合は、パラメータも取ります。

* `リアクション時に主人公をブロックする`: チェックを入れると、リアクションが終了するまで主人公は移動できなくなります。

## オブジェクト <a href="#objects" id="objects"></a>

オブジェクトとは、マップ内で移動したり、イベントに反応したりできるものです。したがって、基本的に木はオブジェクトではありません（切ることができ、斧のヒットに反応する場合を除く）。静的な要素にすぎません。 NPC、モンスターなど、何でもかまいません。主人公はオブジェクト自体であるため、リアクションを完全にプログラムできます。

マップにオブジェクトを追加するには、`オブジェクト`マップエディターセクションを選択します。マップの正方形をポイントし、`ダブルクリック`するか、正方形をクリックした後`Enter`キーを押します。これにより、新しいウィンドウが開きます。

![](<../.gitbook/assets/object-map (1).png>)

* `名前`: オブジェクトの名前を選択します。これは、後でこのオブジェクトに対して外部からアクションを実行する場合に役立ちます。
* `フレームごとに1つのイベントのみ`: イベントについては後ほど説明しますが、チェックを入れると、オブジェクトはフレームごとに1つのリアクションしか持たず、同時に複数持つことはありません。
* `モデル`: このオブジェクトのモデルを選択します。モデルの構成方法については、後で説明します。

### イベント <a href="#events_1" id="events_1"></a>

`イベント`セクションで、オブジェクトが反応できるイベントを構成できます。ノードを`ダブルクリック`します。

![](../.gitbook/assets/event.png)

ユーザーイベントとシステムイベントのどちらにするかを選択し、パラメータ値を変更できます。

![](../.gitbook/assets/event-parameters.png)

システムイベントは次のとおりです。

* `時間`: 時間間隔がクリアされると送信されるイベント。
  * **間隔**（デフォルト：0）：待機時間（ミリ秒）。
  * **繰り返し**（デフォルト：オン）：各間隔の後または1回イベントを送信します。
* `クロノメーター`: _まだ利用できません。_
* `キー押下`: キーボードのキーを押すと送信されるイベント。
  * **ID**（デフォルト：任意）：キーのID。
  * **繰り返し**（デフォルト：オフ）：オンの場合、このイベントは、最初に押したときにわずかにオフセットしてキーを押している限り送信されます。
  * **即時繰り返し**（デフォルト：オフ）：オンの場合、このイベントは、オフセットなしでキーを押している限り送信されます。
* `キー解放`: キーボードのキーを離すと送信されるイベント。
  * **ID**（デフォルト：任意）：キーのID。
* `マウスダウン`: マウスボタンを押すと送信されるイベント。
  * **X**（デフォルト：0）：イベントがトリガーされたときのマウスのX位置。
  * **Y**（デフォルト：0）：イベントがトリガーされたときのマウスのY位置。
  * **左**（デフォルト：オン）：オンの場合、このイベントはマウスの左クリックからのみ送信されます。
* `マウスアップ`: マウスボタンを離すと送信されるイベント。
  * **X**（デフォルト：0）：イベントがトリガーされたときのマウスのX位置。
  * **Y**（デフォルト：0）：イベントがトリガーされたときのマウスのY位置。
  * **左**（デフォルト：オン）：オンの場合、このイベントはマウスの左クリックからのみ送信されます。
* `マウス移動`: マウスを動かすと送信されるイベント。
  * **X**（デフォルト：0）：イベントがトリガーされたときのマウスのX位置。
  * **Y**（デフォルト：0）：イベントがトリガーされたときのマウスのY位置。

### ステート <a href="#states" id="states"></a>

オブジェクトには、一連の`ステート`があります。たとえば、主人公は、通常のステート、または毒/脆弱なステートにすることができます。オブジェクトは同時に複数のステートになる可能性があることに注意してください。

このリストに新しいステートを追加できます。新しい共通ステートを作成する場合は、`完全なリストを更新...`ボタンもあります。

![](../.gitbook/assets/object-state-second.png)

ステートごとに、特定のイベントに対するさまざまなリアクションを選択する必要があります。 `リアクションのコピー`ボタンと`リアクションの貼り付け`ボタンを使用して、ステート間でリアクションをコピー/貼り付けできます。これらのさまざまなオプションは、各ステートでも使用できます。

![](<../.gitbook/assets/state-options (1).png>)

* `グラフィック`: ここでオブジェクトグラフィック（キャラクター画像）を選択します。以下で要素の種類（スプライトなど）を選択します。
*   `移動`: リアクションがない場合のオブジェクトの移動にリンクされたオプション。

    * `タイプ`: 移動のタイプ。
      * `固定`: オブジェクトはまったく移動しません。
      * `ランダム`: オブジェクトはマップ内をランダムに移動します。
      * `ルート`: オブジェクトは、`ルートの編集...`ボタンで編集できるルートをループします。まったく同じオブジェクト移動コマンドのドキュメント[こちら](event-commands.md#move-object)をご覧ください。



    注意：`システムマネージャー > システム`で速度と頻度のリストを編集できます。
* `速度`: オブジェクトの移動時の速度値。この値には、同じ時間で移動した距離が乗算されます。これは、フレーム期間も乗算します。デフォルト値は1です。
* `頻度`: オブジェクトの移動時の頻度値。この値は、次の移動を実行する前に待機する時間を秒単位で変更します。デフォルト値は0（秒）です。

![](../.gitbook/assets/speeds.png)

![](../.gitbook/assets/frequencies.png)

* `名前`: 速度/頻度の名前。
* `値`: 速度/頻度の値（数値のみ）。



* `移動アニメーション`: チェックを入れると、移動アニメーションのすべてのフレームが描画されます。そうでない場合、キャラクターアニメーションの最初のフレームのみが描画されます。
* `停止アニメーション`: チェックを入れると、停止アニメーションのすべてのフレームが描画されます。そうでない場合、キャラクターアニメーションの最初のフレームのみが描画されます。
* `登るアニメーション`: _（まだ利用できません）_チェックを入れると、登るアニメーションのすべてのフレームが描画されます。そうでない場合、キャラクターアニメーションの最初のフレームのみが描画されます。
* `方向の修正`: チェックを入れると、主人公を見てもグラフィックの方向は変わりません。そうでない場合、主人公の方を向きます。
* `カメラと一緒に設定`: チェックを入れると、カメラの向きに応じてグラフィックの向きが更新されます。そうでない場合、カメラの向きは何も変更しません。
* `ピクセルオフセット`: チェックを入れると、移動アニメーションは2フレーム後に1ピクセル下に移動します。これは興味深い効果を追加します。
* `位置を維持する`: チェックを入れると、オブジェクトは、セーブのロード後やマップの変更後も、常にその位置を維持します。そうでない場合、オブジェクトの位置は、セーブのロード後またはマップの変更後に再初期化されます。
* `検出`: フレームごとにイベントを送信するために選択する検出。

### プロパティ <a href="#properties" id="properties"></a>

オブジェクトには、一連のプロパティもあります。HP、年齢、性別などです。それはすべて、あなたのニーズとゲームの種類によって異なります。

![](../.gitbook/assets/object-properties.png)

* `名前`: プロパティ名。
* `初期値`: オブジェクトが最初にロードされたときのプロパティの初期値。

## 例：宝箱を作成する <a href="#example-create-a-chest" id="example-create-a-chest"></a>

宝箱を作成する簡単な方法を次に示します。

* システムマネージャーで、宝箱が開かれたときのステートがあることを確認してください。

![](../.gitbook/assets/states-opened.png)

* 各ステートのリアクションを完了し、通常のステートの最後にステートを置き換えることを忘れないでください。

![](../.gitbook/assets/state-1.png)

![](../.gitbook/assets/state-2.png)

## 既存のオブジェクトの編集/コピー/貼り付け/削除 <a href="#edit-copy-paste-delete-an-existing-object" id="edit-copy-paste-delete-an-existing-object"></a>

オブジェクトを`右クリック`すると、コンテキストメニューを開くことができます。

![](../.gitbook/assets/object-context-menu.png)

## モデル <a href="#models" id="models"></a>

モデルは、一般的に使用できるオブジェクトです。 `システムマネージャー > モデル`でモデルリストを表示できます。

![](../.gitbook/assets/object-hero.png)

たとえば、マップで摘むことができる花を追加する場合は、モデル「花」を作成し、マップ内の空のオブジェクトにこのモデルを使用できます。

* モデルを作成する：

![](../.gitbook/assets/model-flower.png)

* マップオブジェクトにモデルフラワーを使用する：

![](../.gitbook/assets/object-model-flower.png)

### デフォルトモデル <a href="#default-model" id="default-model"></a>

ID 1のモデルは、新しいオブジェクトを作成するときのデフォルトモデルです。ここで、オブジェクトの作成時に含めるデフォルトの情報を変更できます。

### 主人公モデル <a href="#hero-model" id="hero-model"></a>

主人公もオブジェクトであり、多くのシステムイベントに反応します。

* `キー押下 > 上、下、左、右主人公`: オブジェクト移動コマンドを使用して、押された方向にオブジェクト主人公を移動します。
* `キー押下 > 左、右カメラ`: カメラ移動コマンドを使用して、カメラの向きを変更します。
* `キー押下 > アクション`: イベント送信コマンドを使用して、カスタムイベント`HeroAction`を向いている正方形のオブジェクトに送信します。
* `キー押下 > メインメニュー`: メインメニューを開くコマンドを使用して、メインメニューを開きます。

### 継承 <a href="#inheritance" id="inheritance"></a>

オブジェクトがモデルを使用しているが、コンテンツも含まれている場合、この新しいコンテンツはモデルコンテンツの一部を置き換えます。モデル自体がモデルを持つことができます。

* **ステート**: 同じIDのステートがある場合、このステートIDのモデルリアクションは現在のコンテンツに置き換えられます。
* **プロパティ**: 同じ名前のプロパティがある場合、このプロパティ名のモデルリアクションは現在のコンテンツに置き換えられます。
* **イベント**: これは影響しません。

## マップスタートアップリアクション <a href="#map-startup-reactions" id="map-startup-reactions"></a>

マッププロパティでは、次のセクションが表示されます。

![](../.gitbook/assets/map-startup-reactions.png)

これは単に、たとえば新しいマップに入るときのキネマティクスに役立つ見えないオブジェクトです。これは見えないため、ステートグラフィックはありません。デフォルトでは、間隔パラメータに0、繰り返しパラメータにOFFを指定して、イベント`時間`に反応します。つまり、これらのリアクションは、マップに入るときに高い優先度で実行されます。これは、キネマティクスやその他のことに使用できます。

## 検出 <a href="#detections" id="detections"></a>

オブジェクトで検出を使用することが重要です。実際、`主人公のアクション`イベントに反応するときには、すでに使用しています。 `主人公のアクション`イベントは、主人公自身から目の前のオブジェクトに送信されるイベントです。イベントの送信先を決定するために、`検出`と呼ばれるものを使用します。

`システムマネージャー > システム`の検出リストにアクセスできます。

![](<../.gitbook/assets/detections (1).png>)

そして、これが正面の検出です！ここでは、イベントを正面に送信できることがはっきりとわかります。イベントを送信するオブジェクトの正方形の位置と向きを示す矢印があります。 `左クリック`を使用して検出ボックスを追加し、`右クリック`を使用して既存の検出ボックスを削除できます。

* `名前`: 検出名。
* `フィールド`: 増減できる検出フィールド。
  * `左`: イベントを送信するオブジェクトの左側にある正方形の数。
  * `右`: イベントを送信するオブジェクトの右側にある正方形の数。
  * `上`: イベントを送信するオブジェクトの上側にある正方形の数。
  * `下`: イベントを送信するオブジェクトの下側にある正方形の数。
* `新しいボックスの長さ/幅/高さ`: 次のボックスに適用される高さ。
  * `正方形`: 検出ボックスの長さ/幅/高さの正方形の数。
  * `ピクセル`: 検出ボックスの長さ/幅/高さに追加されるピクセルの数。
* `自動`: 検出ボックスの追加を自動的に生成する方法。
  * `円`: 指定された`半径`の円を描画します。
  * `長方形`: 指定された`長さ`と`幅`の長方形を描画します。
  * `生成`: このボタンをクリックすると、選択したフォームとオプションが生成されます。

