---
description: JSONファイルの取り扱い
---

# データとシステム

`Datas`フォルダには、主にJSONファイルに関連付けられたすべての`System`リストが含まれています。 `System`フォルダには、Datasリスト内のクラスが含まれているため、常にパラメータとしてjsonを持つ`read`関数が含まれています。 `System.Animation`の例を以下に示します。

```javascript
/**
 * アニメーションに関連付けられたJSONを読み取る
 * @param {Record<string, any>} json アニメーションを記述するJSONオブジェクト
 */
read(json) {
    this.pictureID = Utils.defaultValue(json.pid, 1);
    this.positionKind = Utils.defaultValue(json.pk, AnimationPositionKind
        .Middle);
    this.frames = [];
    Utils.readJSONSystemList({ list: json.f, listIDs: this.frames, cons: AnimationFrame });
    this.rows = Utils.defaultValue(json.r, 5);
    this.cols = Utils.defaultValue(json.c, 5);
}
```

{% hint style="info" %}
**MVC（Model View Controller）**パターンでは、SystemクラスとDatasクラスをModelと見なすことができます。
{% endhint %}

JSONファイルから読み込まれたすべてのデータが含まれます。これらのファイルは、RPG Paper Makerエンジンによって生成されます。 `System`クラスと`Core`クラスの違いは、Systemクラスは常にJSONファイルに依存していることです。 
