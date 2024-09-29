---
description: タイルセットと衝突の使用方法
---

# タイルセットと衝突

以前、マップのプロパティに `Tileset` 選択オプションがあることを確認しました。今回は、それが何であるかを見ていきます。

## タイルセット <a id="tilesets"></a>

タイルセットは、マップのテクスチャと衝突にリンクされた情報セットに対応します。メインツールバーのここをクリックしてデータマネージャーを開き、`Tilesets` タブを選択します。

![Tilesets タブ](https://rpg-paper-maker.github.io/basics/img/tileset-manager.png)

タイルセットを追加/削除する場合は、`Set max...` ボタンまたは `+` または `-` を使用します。 `Picture` を変更するには、次のウィジェットをクリックします。これにより、（1種類の画像のみを含む）縮小された画像マネージャーが開きます。その画像は、このタイルセットを持つマップに使用する静的テクスチャに対応します。

タイルセットにリンクされた特別なテクスチャ（オートタイル、壁など）を変更することもできます。

## 衝突 <a id="collisions"></a>

衝突はビデオゲームにおいて重要です。移動するオブジェクトが他のオブジェクトやマップ要素と衝突するかどうかを管理する必要があります。

## バウンディングボックス <a id="bounding-boxes"></a>

バウンディングボックスは、交差をチェックするために使用される単純なジオメトリです。各オブジェクトには対応するバウンディングボックスがあり、移動するたびにエンジンはオブジェクトのバウンディングボックスがマップ内の別のバウンディングボックスと交差するかどうかをチェックします。

デバッグのために（奇妙な動作が発生した場合に）バウンディングボックスを表示する方法があります。次のオプションを確認してください。

![衝突バウンディングボックスの表示](https://rpg-paper-maker.github.io/basics/img/collision-debug.png)

## 単純なボックスと方向付けられたボックス <a id="simple-boxes-and-oriented-boxes"></a>

使用しているスプライトによっては、バウンディングボックスを次のように方向付けることができます。

![衝突バウンディングボックスのサンプル](https://rpg-paper-maker.github.io/basics/img/collision-boxes.png)

固定スプライトは平面であるため、方向付ける必要はありません。ただし、顔、ダブル、クワッドラスプライトは立体であるため、バウンディングボックスは円柱になる可能性があります。円柱の衝突は処理が重いため、優れたパフォーマンスで衝突を管理するために妥当な方向付けられたボックスを使用しています。

## 衝突を変更するにはどうすればよいですか？ <a id="how-can-i-change-collisions"></a>

タイルセットの場合は、データマネージャーの `Tilesets` タブの画像プレビューで直接編集できます。もう1つの方法は、考えられるすべての衝突をマージした衝突マネージャーを開くことです。メインツールバーのここをクリックして、衝突マネージャーを開きます。

![衝突マネージャー](https://rpg-paper-maker.github.io/basics/img/collision-manager.png)

## 通行可能 <a id="praticable"></a>

たとえば、各正方形のサイズを変更することで、タイルセットの衝突を変更できます。これは、バウンディングボックスのサイズに影響します。`マウス` または `右クリック` でサイズを変更するか、`Edit` をクリックして、四角形の値を選択するためのウィンドウを開くことができます。

![衝突のサイズ変更](https://rpg-paper-maker.github.io/basics/img/collision-praticable.png)

## 方向（床のみ） <a id="directions-only-for-floors"></a>

衝突が発生する方向を指定できます。

![方向](https://rpg-paper-maker.github.io/basics/img/collision-direction.png)

## キャラクター <a id="characters"></a>

キャラクターはアニメーション化されており、フレームごとに異なる衝突を処理できます。ただし、すべてのフレームで同じ衝突を使用する場合は、`Repeat` オプションをオンにします。

![キャラクターの衝突](https://rpg-paper-maker.github.io/basics/img/collision-character.png)

## オートタイル <a id="autotiles"></a>

メインツールバーのここをクリックして、オートタイルリストを管理できます。

![オートタイルマネージャー](https://rpg-paper-maker.github.io/basics/img/autotiles-list.png)

ここでは、各オートタイルの画像と衝突を管理できます。オートタイルは動的な床です。これには、隣接する正方形に応じて自動的に変化する境界線があります。オートタイル画像の例を次に示します。

![オートタイルのサンプル](https://rpg-paper-maker.github.io/basics/img/autotile-general.png)

マップでのレンダリング：

![オートタイルのサンプル](https://rpg-paper-maker.github.io/basics/img/autotiles-preview.png)

タイルセットにオートタイルを追加することを忘れないでください。

![タイルセットへのオートタイルの追加](https://rpg-paper-maker.github.io/basics/img/autotiles-tileset.png)

これは、テクスチャセレクター **（2）** でも実行できます。

![テクスチャセレクターでも](https://rpg-paper-maker.github.io/basics/img/autotiles-update-list.png)

## アニメーションオートタイル <a id="animated-autotiles"></a>

_まだ利用できません。_

## スプライトの壁 <a id="sprites-walls"></a>

オートタイルと同じ方法で壁を管理できます。

* 衝突マネージャー
* テクスチャセレクター
* データマネージャーの `Tilesets` タブ：

![壁マネージャー](https://rpg-paper-maker.github.io/basics/img/walls-tileset.png)

## 山 <a id="mountains"></a>

オートタイルと同じ方法で山を管理できます。

* テクスチャセレクター
* データマネージャーの `Tilesets` タブ：
* `Collisions`：
  * `Default (according to height and angle)`：山との衝突を管理するには、`Systems manager > System` に移動し、`Mountain collisions height limit (in px)` と `Mountain collisions angle limit (in degree)` を設定します。
  * `Force always collides`：常に衝突を強制します。
  * `Force never collides`：常に衝突しないようにします。

![山岳マネージャー](https://rpg-paper-maker.github.io/basics/img/mountains-tileset.png)

## 3Dオブジェクト <a id="3d-objects"></a>

メインツールバーのここをクリックして、3Dオブジェクトリストを管理できます。

![3Dオブジェクトマネージャー](https://rpg-paper-maker.github.io/basics/img/objects-3d-list.png)

3Dオブジェクトのオプションは、選択した `shape` によって異なります。

* `Box`：単純なボックス。

  * `Texture`：ボックスのテクスチャ。ボックステクスチャには特定のテンプレートがあります。基本リソースでいつでも確認できます。

  ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/box-template.png)

  * `Collisions`：そのボックスに適用する衝突の種類を選択します。
    * `None`：衝突なし。
    * `Perfect`：ボックスの面との完全な衝突。
  * `Size`：ボックスのサイズ。正方形の数と追加のピクセル数で選択できます。
    * `Width`：ボックスの幅。
    * `Height`：ボックスの高さ。
    * `Depth`：ボックスの奥行き。
    * `Texture`：テクスチャの適用方法を選択します。
      * `Stretch`：テクスチャをストレッチします。サイズの比率を考慮しない異なるサイズでテンプレートに従う場合に使用できます。
      * `Perfect size`：常にピクセルの比率を尊重したい場合に使用します。サイズは2x2x1の食器棚の例をご覧ください。

![3Dオブジェクトのサンプル](https://rpg-paper-maker.github.io/basics/img/box-cupboard.png)

* `Sphere` **（まだ利用できません）**
* `Cylinder` **（まだ利用できません）**
* `Cone` **（まだ利用できません）**
* `Capsule` **（まだ利用できません）**
* `Custom`：独自の3Dオブジェクトモデル（`.obj`）をインポートします。
  * `Object`：関連付けられた `.obj` を選択します。
  * `MTL` **（まだ利用できません）**
  * `Texture`：オブジェクトのUVマッピングに対応するテクスチャを選択します。
  * `Collisions`：そのカスタムオブジェクトに適用する衝突の種類を選択します。
    * `None`：衝突なし。
    * `Simplified`：オブジェクトの簡略化されたバウンディングボックスの衝突。衝突は、すべての3Dオブジェクトの頂点を含むことができる最小の単一のボックスを表します。
  * `Scale`：乗算するスケールサイズ。デフォルトでは、値は `1.0` なので、乗算は3Dオブジェクトのサイズに影響を与えません。

タイルセットにオブジェクトを追加することを忘れないでください。

![タイルセットへの3Dオブジェクトの追加](https://rpg-paper-maker.github.io/basics/img/objects-3d-tileset.png)

（またはテクスチャセレクターを使用します）



