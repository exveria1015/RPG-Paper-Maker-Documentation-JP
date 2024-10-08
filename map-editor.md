---
description: マップエディターについて知っておくべきことすべて。
---

# マップエディター

プロジェクトを開くと、次のビューが表示されます。

![RPG Paper Maker の画面](https://rpg-paper-maker.github.io/basics/img/map-editor.png)

## マップの管理

マップセレクター **\(1\)** を見てみましょう。ここでは、フォルダーまたはマップの追加、編集、削除、コピー、貼り付けを行うことができます。ゲームの各ゾーンのマップを整理するために、フォルダーを使用することをお勧めします。デフォルトでは、「戦闘マップ」フォルダーもあり、戦闘の背景に使用するすべてのマップを配置するために使用できます。これらのマップをこの特定のフォルダーに配置する必要はありません。マップをクリックすると、マップエディター **\(5\)** にロードされます。 `右クリック` すると、このコンテキストメニューが開きます。

![マップのコンテキストメニュー](https://rpg-paper-maker.github.io/basics/img/new-map.png)

マップを作成/編集する場合は、次のウィンドウが表示されます。

![](.gitbook/assets/map-properties.png)

* `名前`: マップ名。
* `タイルセット`: タイルセットは、特定のテクスチャセットに適用される多くの情報（衝突、動的テクスチャなど）を表します。設定方法については、次の章で説明します。
* **サイズ**:
  * `長さ`: マップの長さ（正方形の数）（X軸）。
  * `幅`: マップの幅（正方形の数）（Z軸）。
  * `高さ`: マップの高さ（正方形の数）（Y軸> 0）。
  * `奥行き`: マップの奥行き（正方形の数）（Y軸<0）。
* `音楽`: マップに入るときにバックグラウンドで再生される音楽。
* `環境音`: 音楽とともにバックグラウンドで再生される環境音。風、雨などがあります。
* `カメラプロパティID`: マップに入るときに使用されるカメラプロパティID。
* **空**:
  * `カラーID`: 空に使用される一意のカラーID。
  * `画像`: 空の背景として使用される画像。
  * `スカイボックスID`: 空に使用されるスカイボックスID。
* **マップ開始時のリアクション**: マップに入るときに発生する特定のイベントをここで設定できます。オブジェクトのおかげでこれを行う方法については、後で説明します。
* **戦闘**: **（まだ実装されていません）**

## カーソル/グリッド/カメラの移動 <a id="move-cursor-grid-camera"></a>

カメラは常に次のカーソルを見ています。

![マップカーソル](https://rpg-paper-maker.github.io/basics/img/cursor.png)

カーソルで可能な操作を次に示します。

* キーボードの `QWSD` を使用して、`X` 軸と `Z` 軸上を移動します。
* `Y` 軸上を移動する：
  * マス単位で移動する： `CTRL + 上矢印/下矢印` または `CTRL + マウスホイール` を使用します
  * ピクセル単位で移動する： `CTRL + SHIFT + 上矢印/下矢印` または `CTRL + SHIFT + マウスホイール` を使用します

![マス単位で移動](https://rpg-paper-maker.github.io/basics/img/y-axis.png)

* `CTRL + 左クリック` を使用して、カーソルをポイントされた要素のマスにテレポートします。

カメラの位置を移動するには、`マウスホイール` を押したまま、目的の方向にマウスを動かします。

![カメラの移動](https://rpg-paper-maker.github.io/basics/img/camera-turn.gif)

## 要素の配置/削除 <a id="place-remove-elements"></a>

マップ要素選択部分 **\(3\)** では、マップに配置する要素の種類（地面、スプライト、オブジェクト、レリーフなど）を選択できます。左クリックまたは右クリックすることで、特定のマスに何かを追加または削除できます。

たとえば、床の場合：

![](https://rpg-paper-maker.github.io/basics/img/map-editor-add-remove.png)

## 元に戻す/やり直し <a id="undo-redo"></a>

各マップで変更を加える前に戻ったり、変更後に進んだりできます。元に戻すには `CTRL+Z` を、やり直しには `CTRL+Y` を押します。

## 変更の保存 <a id="save-changes"></a>

マップエディターの変更を保存するには、ツールバーの次のショートカットを使用できます。

![保存とすべて保存](https://rpg-paper-maker.github.io/basics/img/save.png)

* `保存`: 現在開いているマップへの変更を保存します。
* `すべて`: 変更されたすべてのマップへの変更を保存します。マップが変更されると、名前の後に `*` が表示されます。

![保存されていない変更](https://rpg-paper-maker.github.io/basics/img/map-save.png)

## UIの詳細の表示/非表示 <a id="show-hide-some-ui-details"></a>

* `G`: グリッドの表示/非表示を切り替えます
* `I`: ポイントされたマスに関する情報の表示/非表示を切り替えます。

![UIの詳細](https://rpg-paper-maker.github.io/basics/img/square-infos.png)

## ペイントモードの変更 <a id="change-paint-mode"></a>

マップに要素を描画するためのさまざまなペイントモード **\(4\)** を次に示します。

![ペイントモード](https://rpg-paper-maker.github.io/basics/img/paint.png)

* `鉛筆`: マスを1つずつ描画します。
* `長方形`: 長方形をトレースした後、マスを描画します **（まだ使用できません）**。
* `ペイントピン`: ポイントされたマスと同じテクスチャでマスを塗りつぶします。

## 地面 <a id="lands"></a>

配置できる地面を次に示します。

![地面の種類](https://rpg-paper-maker.github.io/basics/img/lands.png)

## 床 <a id="floors"></a>

テクスチャセレクター **\(2\)** を使用すると、テクスチャの長方形を選択できます。長方形を選択した後、マウスをマップのマスに置いて床を配置します。

![床](https://rpg-paper-maker.github.io/basics/img/add-floor.png)

## オートタイル <a id="autotiles"></a>

オートタイルは動的な床です。隣接するマスに応じて自動的に変化する境界線があります。

![オートタイル](https://rpg-paper-maker.github.io/basics/img/autotiles-preview.png)

テクスチャセレクター **\(2\)** では、マスを選択するだけです。

![テクスチャセレクター](https://rpg-paper-maker.github.io/basics/img/autotile-texture.png)

## アニメーションオートタイル <a id="animated-autotiles"></a>

_まだ使用できません。_

## スプライト <a id="sprites"></a>

![スプライトメニュー](https://rpg-paper-maker.github.io/basics/img/sprites.png)

スプライトは、"紙"の世界をシミュレートするために使用できる垂直面です。スプライトには次の種類があります。

![スプライトの種類](https://rpg-paper-maker.github.io/basics/img/sprites-preview.png)

* `フェイススプライト`: X/Y軸上で常にカメラの方を向いているスプライト。
* `固定スプライト`: フラットなスプライト。
* `ダブルスプライト`: 2つの交差するフラットスプライト。
* `クアッドラスプライト`: 4つの交差するフラットスプライト。

別の種類の