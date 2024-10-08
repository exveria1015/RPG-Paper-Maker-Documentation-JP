---
description: イベントコマンドの概要
---

# イベントコマンド

オブジェクトとイベントのプロになったところで、使用可能なすべてのイベントコマンドを見ていきましょう。

## テキストを表示 <a id="show-text"></a>

![テキスト表示コマンドエディタ](https://rpg-paper-maker.github.io/basics/img/command-show-text.png)

現在のダイアログボックスオプションを使用して、ダイアログボックスにテキストを表示します。

* `話者`: テキストボックスの上部に小さなボックスが表示され、話者の名前が表示されます。空の場合、このボックスは表示されません。
* `顔グラフィック`: ダイアログボックスの左側に表示する顔グラフィック。
* `メッセージ`:
  * ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/bold.png) : 選択したテキストに太字効果を適用します。
  * ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/italic.png) : 選択したテキストに斜体効果を適用します。
  * ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/text-left.png) : 選択したテキストに左揃え効果を適用します。
  * ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/text-center.png) : 選択したテキストに中央揃え効果を適用します。
  * ![スクリーンショット](https://rpg-paper-maker.github.io/basics/img/text-right.png) : 選択したテキストに右揃え効果を適用します。
  * `フォントサイズ`: 選択したテキストに選択したフォントサイズを適用します。
  * `フォント名`: 選択したテキストに選択したフォント名を適用します。
  * `テキストの色`: 選択したテキストに選択したテキストの色を適用します。
  * `背景色`: 選択したテキストに選択した背景色を適用します。
  * `アウトラインの色`: 選択したテキストに選択したアウトラインの色を適用します。
  * `変数`: 現在選択されている変数の値を表示します。
  * `パラメータ`: 現在選択されているパラメータの値を表示します。
  * `プロパティ`: 現在選択されているプロパティの値を表示します。
  * `ヒーロー名`: 選択したヒーローインスタンスIDの名前を表示します。
  * `アイコン`: 選択したアイコンを表示します。

ゲームでのレンダリング:

![テキスト表示コマンドのサンプル](https://rpg-paper-maker.github.io/basics/img/render-hello-world.png)

## 選択肢を表示 <a id="display-a-choice"></a>

![選択肢表示コマンド](https://rpg-paper-maker.github.io/basics/img/command-display-choice.png)

* `選択肢`: 選択肢のテキストのリスト。
* `オプション`:
  * `自動インデックスのキャンセル`: キャンセルボタンを押したときに選択する選択肢のインデックス。

テキスト表示コマンドを適用して使用:

![選択肢表示コマンドの設定](https://rpg-paper-maker.github.io/basics/img/commands-display-choice.png)

![選択肢表示コマンド](https://rpg-paper-maker.github.io/basics/img/render-command-display-choice.png)

テキスト表示コマンドを前に使用せずに使用:

![テキスト表示コマンドなし](https://rpg-paper-maker.github.io/basics/img/commands-display-choice-without-text.png)

![テキスト表示コマンドなしのサンプル](https://rpg-paper-maker.github.io/basics/img/render-command-display-choice-without-text.png)

## 数字を入力 <a id="input-number"></a>

_まだ利用できません。_

## ダイアログボックスのオプションを設定 <a id="set-dialog-box-options"></a>

![ダイアログボックスのオプション](https://rpg-paper-maker.github.io/basics/img/command-dialog-box-options.png)

すべてのダイアログボックスのオプションを設定します。

* `ウィンドウスキンID`: 表示するウィンドウスキンID。
* `変形`:
  * `X`: ウィンドウのX座標。
  * `Y`: ウィンドウのY座標。
  * `幅`: ウィンドウの幅。
  * `高さ`: ウィンドウの高さ。
* `パディング`:
  * `左`: ウィンドウの左側の余白。
  * `上`: ウィンドウの上部の余白。
  * `右`: ウィンドウの右側の余白。
  * `下`: ウィンドウの下部の余白。
* `顔グラフィック`:
  * `位置`: 顔グラフィックの位置。ウィンドウの後ろか上に配置するかを選択できます。
  * `X`: 顔グラフィックの追加のX座標。
  * `Y`: 顔グラフィックの追加のY座標。
* `テキスト`:
  * `アウトライン`: テキストにアウトラインを付けるかどうかを選択します。
  * `カラーID`:
    * `テキスト`: テキストに使用するカラーID。
    * `アウトライン`: アウトラインに使用するカラーID。
    * `背景`: 背景に使用するカラーID。
  * `サイズID`: テキストに使用するサイズID。
  * `フォントID`: テキストに使用するフォントID。

## 画面の色調を変更 <a id="change-screen-tone"></a>

![画面の色調を変更](https://rpg-paper-maker.github.io/basics/img/command-change-screen-tone.png)

画面の色調（支配的な色）を変更します。RGBカラー（0、0、0）は、画面の色調に何も変更を加えません。

* `赤`: 赤の支配的な色。
* `緑`: 緑の支配的な色。
* `青`: 青の支配的な色。
* `灰色`: 灰色の支配的な色（彩度）。灰色= 0の場合、変更はありません。灰色= 100の場合、画面は灰色の色のみになります。
* `カラーIDの追加`: 前述の色を既存の色と組み合わせることができます。
* `次のコマンドの前に変更が完了するまで待つ`: チェックを入れると、コマンドは`時間`番号の後のみ終了します。
* `時間`: 画面の色調の変更を待つ時間。

## 画面を揺らす <a id="shake-screen"></a>

![](.gitbook/assets/command-shake-screen.png)

これは、たとえば地震をシミュレートして、シネマティックスを演出するのに役立ちます。

* `オフセット`: 揺れごとにオフセットするピクセル数。
* `揺れの回数`: 1秒あたりの揺れの回数。
* `移動が完了するまで次のコマンドを待つ`: チェックを入れると、揺れが終了したときに次のコマンドが実行されます。
* `時間`: 全体の揺れの時間。

## 画面をフラッシュ <a id="flash-screen"></a>

![](.gitbook/assets/command-flash-screen.png)

これは、画面を色で塗りつぶし、線形に通常の画面の色に戻すだけです。

* `カラーID`: 画面に表示するカラーID。
* `移動が完了するまで次のコマンドを待つ`: チェックを入れると、フラッシュが終了したときに次のコマンドが実行されます。
* `時間`: フラッシュの時間。

## 天気を変更 <a id="change-meteo"></a>

_まだ利用できません。_

## マップのプロパティを変更 <a id="change-map-properties"></a>

_まだ利用できません。_

## 待機 <a id="wait"></a>

![待機コマンドの設定](https://rpg-paper-maker.github.io/basics/img/command-wait.png)

特定の時間待機します。

* `時間`: 待機する時間（秒単位）。

## クロノメーターを変更 <a id="change-chronometer"></a>

_まだ利用できません。_

## オブジェクトをテレポート <a id="teleport-object"></a>

![オブジェクトのテレポート](https://rpg-paper-maker.github.io/basics/img/command-teleport-object.png)

これにより、オブジェクトが新しい位置にある既存のマップにテレポートされます。

* `オブジェクトID`: テレポートするオブジェクトID。
* **位置**:
  * `選択...`: マッププレビューアを使用して、マップと位置を選択します。
  * `IDマップ`, `X`, `Y`, `Yプラス`, `Z`: 移動先のマップIDと位置を手動で選択します。
  * `オブジェクト（ID）`: テレポート先のオブジェクトを選択します。
* **オプション**: _まだ利用できません。_

## オブジェクトを移動 <a id="move-object"></a>

![](.gitbook/assets/command-move-object.png)

これにより、特定のルートを使用して、現在のマップ内のオブジェクトが移動されます。また、オブジェクトの状態にリンクされている一部のプロパティを一時的に変更することもできます。

* `オブジェクトID`: 移動するオブジェクトID。
* `不可能な場合は無視`: チェックを入れると、実行できない移動（例：ルートをブロックする壁）は無視されます。チェックを外すと、不可能な移動が可能になるまで（例：NPCの移動に使用）、その移動が試行されます。
* `移動の終了を待つ`: チェックを入れると、すべての移動が実行されたときにのみコマンドが終了します。チェックを外すと、コマンドはすぐに終了します（移動は並行して実行されます）。
* `カメラの向きに合わせて`: チェックを入れると、方向の移動（北、南、西、東）はカメラの向きを考慮します。チェックを外すと、方向の移動はカメラの向きを考慮しません。
* **ステップ/スクエア移動**:
  * `スクエア`: すべての方向の移動単位をスクエアに変更します。
  * `ステップ`: すべての方向の移動単位をステップに変更します。
  * `1を北/南/西/東/北西/北東/南西/南東に`: オブジェクトを選択した方向に1スクエア/ステップ移動します。
  * `1をランダムに`: オブジェクトをランダムな方向に1スクエア/ステップ移動します。
  * `1をヒーローに`: オブジェクトをヒーローの方向に1スクエア/ステップ移動します。
  * `1をヒーローの反対側に`: オブジェクトをヒーローの反対方向に1スクエア/ステップ移動します。
  * `1つ前`: オブジェクトを1スクエア/ステップ前に移動します。
  * `1つ後`: オブジェクトを1スクエア/ステップ後ろに移動します。
* **方向を変える**: _まだ利用できません。_
* **オブジェクトのオプションを変更**:
  * ON / OFF: 一部のオプションでは、オプションONまたはOFFを使用できます。
  * 永続的: チェックを入れると、オブジェクトのオプションは保存後も保持されます。
  * グラフィックを変更: オブジェクトのグラフィックを変更します。

## アニメーションを表示 <a id="display-an-animation"></a>

![](.gitbook/assets/command-display-an-animation.png)

現在のマップにアニメーションを表示します。

* `オブジェクトID`: アニメーションが再生されるオブジェクトID。
* `アニメーションID`: 再生するアニメーションID。
* `次のコマンドの前にアニメーションの終了を待つ`: チェックを入れると、アニメーションの終了後にのみ次のコマンドが実行されます。

## カメラを移動 <a id="move-camera"></a>

カメラガイドについては、[こちら](camera-control.md)をご覧ください。

## カメラをリセット <a id="reset-camera"></a>

_まだ利用できません。_

## マップにオブジェクトを作成 <a id="create-object-in-map"></a>

_まだ利用できません。_

## マップからオブジェクトを削除 <a id="remove-object-from-map"></a>

![マップからオブジェクトを削除](https://rpg-paper-maker.github.io/basics/img/command-remove-object-from-map.png)

マップからオブジェクトを削除します。この削除は、マップを変更したり、保存したゲームをロードしたりしない限り有効です。

* `オブジェクトID`: マップで削除するオブジェクトID。

## 画像を表示 <a id="display-a-picture"></a>

![画像を表示](https://rpg-paper-maker.github.io/basics/img/command-display-picture.png)

画面の上部に画像を表示します。

* `画像ID`: 表示する画像ID。
* `インデックス`: 表示する画像のインデックス。インデックスが異なれば、同時に複数の画像を表示できます。インデックスが高いほど、画像は上に表示されます。2つの画像のインデックスが同じ場合、古い画像は削除されます。
* `起点`:
  * `上/左`: 起点の位置は（0、0）（=画面の左上）になります。
  * `中央`: 起点の位置は画面の中央になります。
* `座標`:
  * `X`: 起点に応じたX座標。
  * `Y`: 起点に応じたY座標。
* `効果`:
  * `ズーム`: 画像のズーム率（％）。
  * `不透明度`: 画像の不透明度（％）。
  * `角度`: 画像の角度（°）。

## 画像を設定/移動/回転 <a id="set-move-turn-a-picture"></a>

![画像を管理](https://rpg-paper-maker.github.io/basics/img/command-set-move-turn-picture.png)

画面の上部にすでに表示されている画像を設定/移動/回転します。

* `画像インデックス`: 設定/移動/回転する画像のインデックスを選択します。
* `設定`:
  * `画像ID`: 表示する画像IDを変更します。
  * `ズーム`: 画像のズーム率（％）を変更します。
  * `不透明度`: 画像のズーム率（％）を変更します。
* `移動`:
  * `X`: 起点に応じたX座標を変更します。
  * `Y`: 起点に応じたY座標を変更します。
* `回転`:
  * `角度`: 画像の角度（°）を変更します。
* `次のコマンドの前にアクションが完了するまで待つ`: チェックを入れると、コマンドは`時間`番号の後のみ終了します。
* `時間`: 画像の更新を待つ時間。

## 画像を削除 <a id="remove-a-picture"></a>

![画像を削除](https://rpg-paper-maker.github.io/basics/img/command-remove-picture.png)

画面に表示されている画像を削除します。

* `画像インデックス`: 削除する画像のインデックスを選択します。

## 動画を再生 <a id="play-a-video"></a>

_まだ利用できません。_

## ショップを開始 <a id="start-shop"></a>

_まだ利用できません。_

## 名前を入力 <a id="enter-a-name"></a>

_まだ利用できません。_

## メインメニューを開く <a id="open-main-menu"></a>

これにより、メインメニューが開きます。

ゲームでのレンダリング:

![メインメニューを開くコマンド](https://rpg-paper-maker.github.io/basics/img/render-main-menu.png)

## セーブメニューを開く <a id="open-saves-menu"></a>

これにより、セーブメニューが開きます。

ゲームでのレンダリング:

![セーブメニューを開くコマンド](https://rpg-paper-maker.github.io/basics/img/render-saves-menu.png)

## タイトル画面 <a id="title-screen"></a>

タイトル画面に移動します。

## ゲームオーバー <a id="game-over"></a>

これにより、ゲームオーバー画面に移動します。

_**/！現在、ゲームオーバー画面はありません。ゲームウィンドウが閉じるだけです。**_

## 音楽を再生 <a id="play-a-music"></a>

![音楽再生コマンド](https://rpg-paper-maker.github.io/basics/img/command-play-music.png)

これにより、現在のマップで音楽が再生されます。

* `IDで曲を選択`: 左側のリストを使用する代わりに、ID値で選択できます。
* **オプション**:
  * `音量`: 音楽の音量（％）。
  * `開始`: 音楽の開始時間（秒単位）。
  * `終了`: 音楽の終了時間（秒単位）。

## 音楽を停止 <a id="stop-music"></a>

![音楽停止コマンド](https://rpg-paper-maker.github.io/basics/img/command-stop-music.png)

これにより、現在のマップで再生されている音楽が停止します。

* `時間とともに消える`: 再生された音楽が消えるまでの秒数。

## BGMを再生 <a id="play-a-background-sound"></a>

これにより、現在の音楽の上にBGMが再生されます。

同様の音楽再生コマンドについては、[こちら](event-commands.md#play-a-music)をご覧ください。

## BGMを停止 <a id="stop-background-sound"></a>

これにより、現在のマップで再生されているBGMが停止します。

同様の音楽停止コマンドについては、[こちら](event-commands.md#stop-music)をご覧ください。

## 効果音を再生 <a id="play-a-sound"></a>

これにより、すべての曲の上に効果音が再生されます。

同様の音楽再生コマンドについては、[こちら](event-commands.md#stop-music)をご覧ください。

## 音楽効果を再生 <a id="play-a-music-effect"></a>

これにより、現在再生されている音楽を一時停止して、音楽が再生されます。音楽効果が終了すると、一時停止されていた音楽が再開されます。

同様の音楽再生コマンドについては、[こちら](event-commands.md#play-a-music)をご覧ください。

## 戦闘音楽を変更 <a id="change-battle-music"></a>

_まだ利用できません。_

## 勝利音楽を変更 <a id="change-victory-music"></a>

_まだ利用できません。_

## イベントを送信 <a id="send-event"></a>

![イベント送信コマンド](https://rpg-paper-maker.github.io/basics/img/command-send-event.png)

これにより、選択したターゲットにイベントが送信されます。

* **ターゲット**:
  * `すべて`: _まだ利用できません。_
  * `検出`: 特定の検出にイベントを送信します。
    * `送信者は受信できません`: 検出は送信者には適用されません。
  * `オブジェクト`: 特定のオブジェクトにイベントを送信します。
* **イベント**:
  * `イベントシステム`: システムイベント（ゲームシステム自体によって送信されるイベント）を選択します。
  * `ユーザイベント`: ユーザイベント（マップオブジェクトによって送信されるカスタムイベント）を選択します。
  * `パラメータ値`: イベントパラメータ値を選択します。デフォルト値を保持できます。

## 状態を変更 <a id="change-state"></a>

![](.gitbook/assets/command-change-state.png)

これにより、現在のオブジェクトの状態が変更されます。オブジェクトは、同時に複数の状態を持つことができます。

* **オブジェクト**:
  * `マップID`: 状態を変更するマップID。
  * `オブジェクトID`: 状態を変更するオブジェクトID。
* **選択**:
  * `状態ID`: 新しい状態ID。
* **操作**:
  * `置換`: オブジェクトの現在の状態をすべて削除し、新しい状態を追加します。
  * `追加`: 新しい状態のみを追加します。
  * `削除`: このIDを持つオブジェクトの状態を削除します。

## プロパティを変更 <a id="change-property"></a>

![プロパティ変更コマンド](https://rpg-paper-maker.github.io/basics/img/command-change-property.png)

これにより、現在のオブジェクトのプロパティ値が変更されます。

* **選択**:
  * `プロパティID`: 変更するプロパティID。
* **操作**: 現在のプロパティ値に応じて使用する操作。
* **値**:
  * `新しい値`: 対応する操作でプロパティに適用する新しい値。

## 通貨を変更 <a id="change-money"></a>

![](.gitbook/assets/command-modify-currency.png)

通貨の値を変更します。

* **選択**:
  * `通貨ID`: 値を変更する通貨ID。
* **操作**: 通貨の値に適用する操作。
* **番号**: 通貨に適用する数値。

## インベントリを変更 <a id="modify-inventory"></a>

![](.gitbook/assets/command-modify-inventory.png)

これにより、インベントリの内容が更新されます。たとえば、アイテムを追加できます。

* **選択**:
  * `アイテムID`: 選択するアイテム。
  * `武器ID`: 選択する武器。
  * `防具ID`: 選択する防具。
* **操作**: インベントリ内の選択の現在の数に応じて使用する操作。
* **番号**: 選択の数を更新するために使用する値。

## チームを変更 <a id="modify-team"></a>

![チーム変更コマンド](https://rpg-paper-maker.github.io/basics/img/command-modify-team.png)

これにより、チーム編成が更新されます。

* `レベル...の新しいインスタンスをチーム/控え/非表示に作成`: チーム、控え、または非表示にヒーローまたはモンスターの新しいインスタンスを作成します。
  * `インスタンスIDを...に保存`: インスタンスIDを保存する変数を​​選択します。これは、チーム内のキャラクターを移動または削除する場合に役立ちます。
* `ID...のキャラクターをチーム/控え/非表示に移動/削除`: _まだ利用できません。_

## セーブを許可/禁止 <a id="allow-forbid-saves"></a>

![セーブを許可/禁止するコマンド](https://rpg-paper-maker.github.io/basics/img/command-allow-forbid-saves.png)

* `許可`: チェックを入れると、セーブメニューが許可されます。

## メインメニューを許可/禁止 <a id="allow-forbid-main-menu"></a>

![メインメニューを許可/禁止するコマンド](https://rpg-paper-maker.github.io/basics/img/command-allow-forbid-main-menu.png)

* `許可`: チェックを入れると、メインメニューが許可されます。

## 全般オプションを変更 <a id="change-general-options"></a>

_まだ利用できません。_

## 戦闘を開始 <a id="start-a-battle"></a>

![戦闘開始コマンド](https://rpg-paper-maker.github.io/basics/img/command-start-battle.png)

これにより、あなたのチームと軍隊（モンスターのグループ）との戦いが始まります。

* **軍隊のID**:
  * `ID`: 軍隊IDを修正します。
  * `ランダム（マッププロパティ内）`: マッププロパティウィンドウに示されているランダムID。
* **戦闘マップ**:
  * `ID`: 戦闘マップIDを修正します。
  * `選択...`: マッププレビューアを使用して、戦闘マップと位置を選択します。
  * `IDマップ`, `X`, `Y`, `Yプラス`, `Z`: 移動先の戦闘マップIDと位置を手動で選択します。
* **オプション**:
  * `逃走を許可`: チェックを入れると、この戦闘で戦闘コマンド`逃げる`を使用できます。
  * `敗北でゲームオーバー`: チェックを入れると、この戦闘で負けると自動的にゲームオーバーになります。チェックを外すと、2つのコマンドコンテナが表示されます。1つは勝利状態用、もう1つは敗北状態用です。
* **トランジション**:
  * `開始/終了`: トランジションの開始/終了タイプ：
    * `なし`: すぐにトランジションします。
    * `フェードイン/アウト`: 色でトランジションします。
    * `ズームイン/アウト`: ズームイン/アウトでトランジションします。

## 敵を表示/非表示 <a id="display-hide-enemy"></a>

_まだ利用できません。_

## 行動を強制 <a id="force-an-action"></a>

_まだ利用できません。_

## 戦闘を終了 <a id="end-battle"></a>

_まだ利用できません。_

## 戦闘音楽を変更 <a id="change-battle-music_1"></a>

_まだ利用できません。_

## 勝利音楽を変更 <a id="change-victory-music_1"></a>

_まだ利用できません。_

## 統計を変更 <a id="change-a-statistic"></a>

![](.gitbook/assets/command-change-a-statistic.png)

ここでは、1人または複数のキャラクター（ヒーローまたは敵）の統計値を変更できます。

* `統計ID`: 値を変更する統計ID。
* **選択**:
  * `ヒーロー/敵インスタンスID`: キャラクターのインスタンスIDを選択します。これらは主に変数に格納されます。
  * `全体`: グループを選択します。これは、`チーム`、`控え`、または`非表示`の場合があります。
* **操作**: 現在の統計値に適用する操作を選択します。
* **値**:
  * `番号`: 動的な数値を選択します。
  * `計算式`: 値として計算式を入力します。
  * `最大統計値`: 統計の最大値を取得します（たとえば、HPを最大まで回復するために使用されます）
  * `最大値を超えることができます`: チェックを入れると、指定された値が統計の最大値を超える可能性があります。

## 経験値曲線を変更 <a id="change-experience-curve"></a>

_まだ利用できません。_

## ステータスを変更 <a id="change-status"></a>

_まだ利用できません。_

## スキルを変更 <a id="change-a-skill"></a>

![](.gitbook/assets/command-change-a-skill.png)

キャラクターに特定のスキルを習得させるか、忘れさせるかを選択します。

* `スキルID`: 習得または忘却するスキルID。
* **選択**:
  * `ヒーロー/敵インスタンスID`: キャラクターのインスタンスIDを選択します。これらは主に変数に格納されます。
  * `全体`: グループを選択します。これは、`チーム`、`控え`、または`非表示`の場合があります。
* **操作**: 選択したスキルを習得させるか、忘れさせるかを選択します。

## 名前を変更 <a id="change-name"></a>

![](.gitbook/assets/command-change-name.png)

名前を変更するキャラクターを選択します。これは、ヒーロー名を入力するコマンドとは異なり、HUDが開かないため、プレイヤーは名前を入力できません。

* `名前`: 新しいキャラクター名。
* **選択**:
  * `ヒーロー/敵インスタンスID`: キャラクターのインスタンスIDを選択します。これらは主に変数に格納されます。
  * `全体`: グループを選択します。これは、`チーム`、`控え`、または`非表示`の場合があります。

## クラスを変更 <a id="change-class"></a>

_まだ利用できません。_

## 装備を変更 <a id="change-equipment"></a>

![](.gitbook/assets/command-change-equipment.png)

キャラクターに武器または防具を強制的に装備させることができます。

* `装備ID`: 強制的に装備させる装備スロットID。
* `武器ID/防具IDを使用`: 強制的に装備させる武器または防具ID（装備IDによる）。
* **選択**:
  * `ヒーロー/敵インスタンスID`: キャラクターのインスタンスIDを選択します。これらは主に変数に格納されます。
  * `全体`: グループを選択します。これは、`チーム`、`控え`、または`非表示`の場合があります。
* `インベントリにある場合にのみ適用`: チェックを入れると、インベントリにない場合は装備は装備されません。チェックを外すと、アイテムはインベントリに追加されてから装備されます。

## 条件 <a id="condition"></a>

指定された条件が真の場合にのみ実行されるコマンドのコンテナを作成します。

* `条件が適用されない場合は「else」を追加`: 指定された条件が偽の場合にのみ実行されるコマンドの別のコンテナを作成します。
* **変数/パラメータ/プロパティ**:

![条件エディタ](https://rpg-paper-maker.github.io/basics/img/command-condition-variables-param-prop.png)

* `これ`: 変数、パラメータ、またはプロパティを他のタイプの値と比較します。
* **ヒーロー**:

![条件エディタ](https://rpg-paper-maker.github.io/basics/img/command-condition-heroes.png)

* `ヒーロー`: `チーム`、`控え`、または`非表示`の`すべてのヒーロー`、`ヒーローなし`、`少なくとも1人のヒーロー`、または`インスタンスIDを持つヒーロー`を選択します。
  * `名前が付けられています`: 選択範囲にこの名前があるかどうかを確認します。
  * `所属しています`: 選択範囲が`チーム`、`控え`、または`非表示`のいずれにあるかを確認します。
  * `スキルIDを使用できます`: 選択範囲が選択したスキルIDを使用できるかどうかを確認します。
  * `装備しています`:
    * `武器ID`: 選択範囲が選択した武器IDを装備しているかどうかを確認します。
    * `防具ID`: 選択範囲が選択した防具IDを装備しているかどうかを確認します。
  * `ステータスIDの影響を受けています`: _まだ利用できません。_
  * `統計IDを持っています`: 選択範囲の選択した統計を他のタイプの値と比較します。
* **所持品**:

![条件エディタ](https://rpg-paper-maker.github.io/basics/img/command-condition-possessions.png)

* `通貨ID`: 選択した通貨の数を他のタイプの値と比較します。
* `アイテムID`: インベントリ内の選択したアイテムの数を他のタイプの値と比較します。
* `武器ID`: インベントリ内の選択した武器の数を他のタイプの値と比較します。
  * `装備している武器もチェック`: チェックを入れると、装備している武器が武器の数に含まれます。
* `防具ID`: インベントリ内の選択した防具の数を他のタイプの値と比較します。
  * `装備している防具もチェック`: チェックを入れると、装備している防具が防具の数に含まれます。
* **その他**:

![](.gitbook/assets/command-condition-others.png)

* `キーID`: 選択したキーがオンかオフかを確認します。
* `最後の戦いで逃げた`: プレイヤーが最後の戦いで逃げたかどうかを確認します（戦闘コマンドのエスケープを使用）。
* `スクリプト`: スクリプトの戻り値に応じて確認します（プログラマー向け）。

## ループ <a id="loop"></a>

ループで実行されるコマンドのコンテナを作成します。

## ループを中断 <a id="break-loop"></a>

ループコンテナ内にある場合、ループを抜け出して、ループの後の次のコマンドに進みます。

## ラベル <a id="label"></a>

![](.gitbook/assets/command-label.png)

反応にラベルを追加します。これは、ラベルにジャンプコマンドと組み合わせて使用​​します。任意の名前を選択できます。

## ラベルにジャンプ <a id="jump-to-label"></a>

![](.gitbook/assets/command-jump-label.png)

ラベルコマンドと組み合わせることで、指定したラベルに移動することを選択できます。ループを作成する例を次に示します。

![](.gitbook/assets/example-label.png)

コマンドは次のように実行されます。

条件？>いいえ> ifの終わり>ラベルループにジャンプ>ラベルループ> ifの終わり>ラベルループにジャンプ>ラベルループ> ...

## 反応を停止 <a id="stop-the-reaction"></a>

現在の反応を停止します。

## コメント <a id="comment"></a>

![](.gitbook/assets/command-comment.png)

コメントはゲーム内で解釈されません。これはあなたのためだけのものです。特定の場所でコメントを残して、特定のコマンドを使用した理由を覚えておくことができます。

![](.gitbook/assets/example-command-comment.png)

## 共通反応を呼び出す <a id="call-a-common-reaction"></a>

![](https://rpg-paper-maker.github.io/basics/img/command-call-common-reaction.png)

これにより、対応するパラメータを使用して共通反応が呼び出されます。

* `共通反応`: 呼び出す共通反応。
* **パラメータ値**: 共通反応に適用するパラメータ。

## 変数を変更 <a id="change-variables"></a>

![](https://rpg-paper-maker.github.io/basics/img/command-change-variables.png)

これにより、1つまたは複数の変数の値が変更されます。

* **選択**:
  * `1つの変数`: 変更する一意の変数。
  * `範囲`: 変更する変数IDの範囲。
* **操作**: 現在の変数の値に応じて使用する操作。
* **値**:
  * `番号`: 単純な数値。
  * `ランダム`: 選択した2つの値の間の乱数。
  * `メッセージ`: 単純なメッセージ。
  * `スイッチ`: 単純なスイッチ。
  * `インベントリ内の...の数`: _まだ利用できません。_
  * `ID...の合計通貨`: _まだ利用できません。_
  * `インスタンスID...統計IDを持つ...`: _まだ利用できません。_
  * `マップ内のオブジェクト...特性`: 選択したオブジェクトの特性：
    * `Xスクエア位置`: 選択したオブジェクトのXスクエア位置。
    * `Yスクエア位置`: 選択したオブジェクトのYスクエア位置。
    * `Zスクエア位置`: 選択したオブジェクトのZスクエア位置。
    * `Xピクセル位置`: 選択したオブジェクトのXピクセル位置。
    * `Yピクセル位置`: 選択したオブジェクトのYピクセル位置。
    * `Zピクセル位置`: 選択したオブジェクトのZピクセル位置。
    * `向き`: 選択したオブジェクトの向き。
  * `その他の特性`: _まだ利用できません。_

## スクリプト <a id="script"></a>

![](https://rpg-paper-maker.github.io/basics/img/command-script.png)

スクリプトコードを実行します（上級プログラマー向け）。

* `動的を使用`: 静的でないコード（変数、パラメータ、またはプロパティ内）。