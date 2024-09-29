# メインメニュー

`システムマネージャ > メインメニュー` で、ゲーム内のメインメニューをカスタマイズできます。

![](../.gitbook/assets/main-menu.png)

## アイテムタイプ

アイテムタイプは、アイテムを編集する際に選択できるすべてのタイプのリストです。

![](<../.gitbook/assets/main-menu-item-type (1).png>)

## インベントリフィルター

![](../.gitbook/assets/render-main-menu-inventory-filters.png)

インベントリを開いているときに、タブのコンテンツフィルターを編集できます。

![](../.gitbook/assets/main-menu-inventory-filter.png)

* `名前`: ゲーム内で表示する名前を選択します
* `種類`: フィルターの種類
  * `すべて`: フィルターを適用しません
  * `消耗品`: すべての消耗品
  * `カスタム`: 関連付けられたアイテムタイプIDを選択します
  * `武器`: すべての武器
  * `防具`: すべての防具
  * `武器と防具`: すべての武器と防具
  * `スクリプト`: `Core.Item` タイプの変数 `item` に応じて `true` または `false` を返すカスタムスクリプトフィルターを使用します。 例：

```javascript
return item.system.id === 1;
```

## メインメニューコマンド

![](../.gitbook/assets/render-main-menu-commands.png)

メインメニューコマンドは、メインメニューを開いたときに左上に表示されるコマンド選択ボックスです。

![](../.gitbook/assets/main-menu-command.png)

* `名前`: ゲーム内で表示する名前
* `種類`: クリックしたときに行うアクションの種類:
  * `インベントリ`: インベントリメニューを開きます
  * `スキル`: スキルメニューを開きます
  * `装備`: 装備メニューを開きます
  * `ステート`: ステートメニューを開きます
  * `順序`: 並べ替えたいヒーローリストを選択します
  * `セーブ`: セーブメニューを開きます
  * `終了`: タイトル画面に戻ります
  * `スクリプト`: 特殊なスクリプトを呼び出します。 成功の場合は `true`、不可能な場合は `false` を返します。 `Scene.Menu` タイプの変数 `menu` を使用できます。 例：

```javascript
menu.windowChoicesTeam.select(0);
return true;
```

## 表示するヒーロー統計

![](../.gitbook/assets/render-main-menu-statistic.png)

ヒーローの説明の右側に表示する統計をカスタマイズできます。

![](../.gitbook/assets/main-menu-statistic.png)

* `統計ID`: 表示する統計ID
