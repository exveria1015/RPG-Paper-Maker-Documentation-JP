---
description: すごい！ ゲームアクションを次のレベルに引き上げる方法を学びましょう。
---

# アクションバトルシステム

**/！ このチュートリアルは、エンジンの可能性を最大限に表現するために、今後のアップデートに合わせて常に更新されます。現時点では基本的な機能しか搭載されていないため、最初はあまり魅力的ではないかもしれません（アニメーションなどはありません）。**

また、これを読む前に、[オブジェクトとイベントのチュートリアル](objects-and-events.md) を参照する必要があることに注意してください。

## アクションバトルシステムとは？ <a id="what-is-an-action-battle-system"></a>

アクションバトルシステムとは、アクションRPGやシンプルなアクションゲームで使用されるバトルの種類です。一例としては、プラットフォームゲームであるゼルダ2を除く**ゼルダの伝説**シリーズがあり、剣攻撃、爆弾、矢などを駆使したバトルシステムを採用しています。

![例：ゼルダの伝説 ふしぎのぼうし](https://rpg-paper-maker.github.io/advanced/img/zelda.png)

## 主人公と敵の特性を作成する方法 <a id="how-to-create-my-hero-and-enemies-characteristics"></a>

まずは基本的な特性であるHP（ヒットポイント）から始めます。実際には統計値を設定するためのコマンドはありませんが、別の方法があります。プロパティを使用します。 `システムマネージャー > モデル` に移動し、`主人公` モデルを選択します。次のように、プロパティ `HP` を追加できます。

![システムマネージャー > モデル > プロパティの設定](https://rpg-paper-maker.github.io/advanced/img/abs-prop.png)

マップ内の敵にも同じことができます。

![](https://rpg-paper-maker.github.io/advanced/img/abs-enemies.png)

注意：ここではモデルを使用することを強くお勧めします！

## 剣攻撃を作成する方法 <a id="how-to-create-sword-attacks"></a>

ここでは、アクションキーで剣を使うとしましょう。必要なものは3つです。

* 近くの敵に送信されるイベントソードアタックを作成します。 `システムマネージャー > イベント/ステート` に移動し、デフォルト値として任意の値を設定できるパラメーター `威力` を持つ `剣攻撃` という名前の新しいイベントを追加します。このパラメーターは、攻撃剣の威力を変更するのに役立ちます。

![システムマネージャー > イベント/ステート](https://rpg-paper-maker.github.io/advanced/img/abs-event-sword.png)

* 敵がHP0になると表示されなくなるように、死亡ステートを作成します。 `システムマネージャー > イベント/ステート` に移動し、`死亡` という名前の新しいステートを追加します。

![ステート](https://rpg-paper-maker.github.io/advanced/img/abs-state-dead.png)

* 剣攻撃が有効な範囲を示す剣の検出を作成します。 `システムマネージャー > システム` に移動し、次のような `剣` という名前の新しい検出を追加します。

![検出の設定](https://rpg-paper-maker.github.io/advanced/img/abs-detection-sword.png)

それでは、`主人公` モデルに戻りましょう。イベントアクションキー押下はすでに主人公のアクションイベントの送信に使用されていますが、剣イベントの送信にも使用できます。主人公が検出剣エリア内にいる敵に威力5の剣攻撃イベントを送信するように、これに対するリアクションを設定しましょう。

![コマンド > イベント送信コマンド](https://rpg-paper-maker.github.io/advanced/img/abs-sword-command.png)

完了です。これで、何かが起こるようにしたい場合は、敵が剣攻撃に反応できるはずです。任意の威力値の剣攻撃イベントに対して、HPを失い、HPが0以下になったら死亡するように設定しましょう。

![コマンド > プロパティ変更コマンド](https://rpg-paper-maker.github.io/advanced/img/abs-sword-enemy.png)

![](https://rpg-paper-maker.github.io/advanced/img/abs-enemy-text-command.png)

死亡ステートは、グラフィックのない単なる空のオブジェクトですが、死亡アセットにすることもできます。これで剣攻撃が完成しました！

## マップ内の敵が残した戦利品を作成する方法 <a id="how-to-create-loots-left-by-enemies-in-map"></a>

敵が即座に死亡するのではなく、ドロップした可能性のある戦利品に置き換えることができます！主人公のタッチに反応し、死亡ステートを戦利品ステートに置き換える戦利品ステートを追加するだけです。

![戦利品の定義](https://rpg-paper-maker.github.io/advanced/img/abs-loot.png)

例えば、80%の確率で戦利品が出現するランダム効果を追加することもできます。

![戦利品の定義](https://rpg-paper-maker.github.io/advanced/img/abs-loot-rand.png)

結果：

![サンプル](https://rpg-paper-maker.github.io/advanced/img/abs-sword-loot.gif)

## 投射物（弾丸、矢）を作成する方法 <a id="how-to-create-projectiles-bullets-arrows"></a>

_現在利用できません（マップコマンドでオブジェクトの作成/削除が必要です）_

## 爆弾を作成する方法 <a id="how-to-create-bombs"></a>

_現在利用できません（マップコマンドでオブジェクトの作成/削除が必要です）_

## AIを作成する方法 <a id="how-to-create-an-ai"></a>

_現在利用できません（より多くの移動コマンド（パスファインディング）が必要です）_

## 侵入システムを作成する方法 <a id="how-to-create-an-intrusion-system"></a>

_現在利用できません（より効果的に使用するには、特定のオブジェクトコマンドに検出を送信する必要があります）_
