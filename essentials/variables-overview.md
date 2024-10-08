# 変数と条件

## -- 概要

このセクションでは、ゲーム全体を通してデータの保存と利用に重要なコマンドについて説明します。これらのコマンドは、最もシンプルなゲームでも必要とされます。

## -- 変数

簡単に言うと、変数とは、ゲーム全体を通して編集および読み取りが可能なデータを格納する場所です。また、パラメータとプロパティも変数と非常によく似た機能を持ちますが、属性とスコープが異なります。これらについては、以下で説明します。

格納できるデータ型は3種類あり、それらを利用する方法はさらに多岐にわたります。

### データ型

Paper Makerでは、次のタイプのデータを扱うことができます。

* 数値 - 正と負の両方。
* スイッチ - ONまたはOFF。
* メッセージ - 英数字テキストの文字列。

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>各フィールドの左側にある円/点はラジオボタンと呼ばれます</p></figcaption></figure>

変数にデータを書き込むときは、上記の強調表示されたフィールドのいずれかを選択して、格納するデータのタイプを選択できます。その他のすべてのオプションは、データベース内の既存のデータを参照し、それを数値として変数に書き込みます。

### データの入力

変数にデータを書き込む理由はたくさんあります。一般的な用途の1つは、主人公のHPです。変数には、主人公に残っているHPの値が格納されます。攻撃を受けるたびに、その変数から値が引かれます。任意の時点で値を確認して、残りのHPを確認できます。

変数にデータを書き込む際に利用できる各オプションを見ていきましょう。

### - 選択

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

最初に、書き込み先の変数を選択します。...ボタンをクリックして単一の変数を選択するか、範囲オプションを使用して、変数のグループに同じデータを書き込みます。

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

左側には、変数の整理に使用できるページがあります。ページの名前は、「主人公のステータス」や「クエストの進捗状況」などに変更できます。

変数が必要になるたびに、単に次に利用可能なスペースを使用するのではなく、同様の変数をグループ化することをお勧めします。新しい作業をしている場合は、先に進んで新しいページを作成します。そうすることで、後で同様の変数を同じページに追加するスペースを確保できます。

他のデータベースリストと同様に、ドラッグアンドドロップでこれらのページの順序を変更できます。変数のID番号は変更されず、変数をさらに整理できます。

左側のページをクリックすると、右側で使用したい変数を1つ選択できます。

変数の名前は、用途に合わせて常に分かりやすくすることをお勧めします。主人公のHP、残り時間などです。コード内で簡単にすべてを読み取れるように、長すぎないように記述的にする必要があります。

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<img src="../.gitbook/assets/mm1.png" alt="" data-size="line"> ヒント：単語をすべて大文字で記述することで、変数の完全なリストの中で目立たせることができます。

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### - 操作

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

次に、どのような操作を行うかを選択します。

* 等しい - 古い値を新しい値で上書きします。
* 加算 - 変数に新しい値を追加します。
* 減算 - 変数から新しい値を引きます。
* 乗算 - 変数に新しい値を掛けます。
* 除算 - 変数を新しい値で割ります。
* 剰余 - 変数を新しい値で割り、余りを切り捨てます。\*

* 等しいは、すべてのデータ型で機能します。
* 加算\減算は、数値とメッセージで機能します。
* 残りは数値でのみ機能します。

\*この関数（別名Mod）は、ほとんどの人は馴染みがないかもしれませんが、便利です。入力された値で数値を除算し、余りのみを返します。

たとえば、10を3で割るとします。結果は3.333になります。

代わりに10 mod 3を使用すると、結果は1になります。3は10に3回収まり、合計で9になります。余りは1です。

この用途の1つは、小数点以下を削除することです。値が3.333の変数がある場合は、まずそのコピーを作成します。コピーに対してMod 1を実行すると、0.333になります。次に、元の値からコピーを引きます。3.333-0.333 = 3になります。javascriptを使用してこれを行う方法は他にもありますが、この方法はデフォルトのコマンドといくつかの計算で実行できます。

### - 値

このカテゴリには多くのオプションがあります。

### -- 数値

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>一部のフィールドでは小数点を使用できます</p></figcaption></figure>

最も一般的に使用されるオプションです。ドロップダウンメニューには、次の選択肢があります。

* 数値 - 操作で使用する数値を選択します。
* 変数 - 操作で選択した変数の値を使用します。

### -- ランダム

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

範囲を設定すると、エンジンは2つの値の間の乱数を取得します。

### -- メッセージ

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

変数に書き込むテキストを入力します。加算操作を使用すると、既存のメッセージの右側に新しいテキストが追加されます。必要に応じてスペースと句読点を追加してください。

### -- スイッチ

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

スイッチの新しい状態（ONまたはOFF）を選択します。

### -- インベントリ

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

プレイヤーが特定のアイテムをいくつ持っているかを確認し、その数値を変数に書き込みます。

ここには、次のオプションを提供するドロップダウンメニューがあります。

* 選択 - ドロップダウンメニューから直接アイテムを選択できます。
* 数値 - 数値を選択できます。これは、データベース内のアイテムのIDに対応しています。HPポーションのIDは1であることがわかります。
* 変数 - 変数の値を使用して、チェックされるアイテムのIDを選択できます。

### -- 通貨

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

最初のドロップダウンメニューでは、次の数値を取得できます。

* 所有 - 現在所有している通貨の量。
* 獲得 - ゲーム開始から獲得した金額。所有+使用。
* 使用 - 店で使った金額、またはコマンドで奪われた金額。

最後のドロップダウンメニューでは、ゲームで複数の通貨を使用している場合に、どの通貨を確認するかを選択します。

### -- 統計

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

主人公または敵の統計値を取得します。IDを知ることは難しい場合があります。IDは、主人公または敵に遭遇した順に割り当てられます。ゲームが非常に線形でない限り、変数で手動で追跡しない限り、これを知る直接的な方法はありません。

主人公の場合、簡単な方法は、新しいゲームの開始時にすべての主人公をパーティに追加することです。これにより、IDは0から順番に確保されます。その後、「パーティの変更」コマンドを使用して、一部の主人公を「非表示」に変更して、プレイヤーが利用できないようにすることができます。プレイヤーに主人公を戻したい場合は、「非表示」から「チーム/控え」に移動します。これは、ポケモンのクローンなど、無制限の数の主人公を追加できる場合は機能しません。もう1つの選択肢は、主人公が追加されたときに変数で追跡することです。

敵の場合、IDを提供できるオプションが以下にありますが、これは部隊のリアクション内でのみ機能します。変数で追跡することもできます。

### -- マップの特性

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

オブジェクトに関するさまざまなマップ関連情報を見つけることができます。

ドロップダウンリストでは、「このオブジェクト」を選択できます。これは、このコマンドを実行するオブジェクトになります。主人公も選択可能なオプションです。その後に、現在のマップ上のすべてのオブジェクトのリストが表示されます。別のマップ内のオブジェクトをターゲットにすることはできません。

最初のドロップダウンメニューで「数値」を使用すると、各マップで特定のオブジェクトに常に同じオブジェクトIDが割り当てられるようにすることができます。そうすれば、コード内で番号で参照でき、正しいオブジェクトがターゲットになることがわかります。

最後のドロップダウンメニューには、次の選択肢があります。

* X、Y、およびZの正方形の位置 - これは、エディターに表示される値に対応しています。0、0、0は、マップの北西の角の地上レベルにあります。オブジェクトの移動やテレポートなどのコマンドは正方形単位で測定されるため、正方形の方が便利な場合が多いです。

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption><p>正方形=タイル</p></figcaption></figure>

* X、Y、およびZのピクセル位置 - これは、正方形のサイズによって異なります。正方形のサイズが16ピクセルの場合、4の正方形の位置は、4 x 16 = 64ピクセルのピクセル位置になります。
* 向き - オブジェクトがどの方向を向いているかがわかります。これは、キャラクターシートのリソースに対応しています。

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

* 地形 - オブジェクトの下にあるタイルの地形IDがわかります。

### -- 敵

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

部隊のリアクション以外でこのオプションを使用しようとすると、ドロップダウンリストは空になります。利用可能な敵は戦闘ごとに変わるためです。部隊のリアクション内で使用すると、部隊のモンスターのリストが表示されます。

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

IDがわかったら、統計の変更や戦闘員の変身など、IDでオブジェクトをターゲットとする他のコマンドを使用できます。

唯一の制限は、プレイヤーが現在どの敵をターゲットにしているかを知るコマンドがないことです。

### -- その他の特性

ここでは、さまざまなゲーム情報を見つけることができます。

* 現在のマップID - 主人公が現在いるマップ。マップのプロパティでIDを確認できます。

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

* チームの人数 - 現在パーティにいる主人公の人数を返します。
* 非表示の人数 - 現在パーティから非表示になっている主人公の人数を返します。
* 控えの人数 - 現在控えに配置されている主人公の人数を返します。
* 合計歩数 - ゲーム全体でプレイヤーが歩いた歩数を追跡します。1タイルは約3〜4歩です。
* 合計秒数 - 合計プレイ時間を追跡します。
* 合計セーブ回数 - ゲームをセーブした回数を追跡します。
* 合計戦闘回数 - プレイヤーが参加した戦闘の回数を追跡します。
* カメラの位置X、Y、およびZ - 現在のカメラの位置をピクセル単位で表す数値を返します。
* 音楽の合計秒数 - 現在の「音楽」曲が再生されている時間を示します。
* BGMの合計秒数 - 現在の「BGM」曲が再生されている時間を示します。

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption><p>表現は一貫していませんが、背景音とBGMは同じものです</p></figcaption></figure>

これらのすべてのオプションの具体的な使用方法については、後のセクションで詳しく説明します。

## パラメータとプロパティ

変数とともに、パラメータとプロパティもあります。これらはすべてデータを保持しますが、データの使用方法が異なります。

### - 変数

変数は使い方が簡単でグローバルであり、コードの配置場所に関係なく、すべてのオブジェクトとリアクションからアクセスできます。

変数を作成するには、変数アイコンをクリックするか、「変数の変更」コマンドを開きます。

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption><p>残りは上記で説明されています</p></figcaption></figure>

### - パラメータ

パラメータは変数のように機能しますが、作成されたエリア（イベントまたはコモンリアクション）でのみ使用できます。あるエリアで作成されたパラメータを別のエリアで使用することはできません。

パラメータを持つエリアは2つあります。

1. システムマネージャー>イベント/ステータスタブ：

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

「<>」をダブルクリックまたは右クリックして、新しいエントリを作成します。

その後、イベントの設定に表示されます。

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

パラメータを変更するには、値を「デフォルト」から別の値に変更する必要があります。

このイベント中にアクティブ化されるコマンドは、そのパラメータに新しい値を使用します。

2. システムマネージャー>コモンリアクションタブ。

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

そのリストは分離されており、コモンリアクションの呼び出し時にのみ表示されます。

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

コモンリアクションは、コマンド内で新しいパラメータ値を参照します。

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

ゲーム中にパラメータを変更するコマンドはありません。変数/プロパティを値として使用する必要があります。その後、変数を変更してパラメータを変更できます。

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

用途によっては、変数を作成する手間が省け、変数のリストが肥大化するのを防ぐことができます。その他、Anything、None、Keyboardなどのデータ型も役立ちますが、非常に特殊であり、上級ユーザー向けです。

### - プロパティ

プロパティはローカルであるため、作成されたオブジェクトからのみアクセスできます。つまり、値を読み取る条件は、同じオブジェクト上にある必要があります。

プロパティを作成するには、オブジェクトを開き、「プロパティ」ボックスに新しいエントリを作成します。

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption><p>ダブルクリックまたは右クリックして、新しいエントリを作成します。</p></figcaption></figure>

これらは、複数のオブジェクトに同じプロパティを設定でき、それぞれが独自の値を格納できるため便利です。プロパティを使用するコマンドは、オブジェクト自体に配置する必要があります。これにより、完成したオブジェクトをコピーアンドペーストでき、すべてが独立して機能します。

たとえば、オブジェクトにHPプロパティを付与し、プレイヤーが攻撃するたびにHPから1が引かれるようにすることができます。他のオブジェクトのHPプロパティには影響しません。外部オブジェクトを使用してプロパティを確認することはできません。プロパティ自体で確認する必要があります。

<img src="../.gitbook/assets/mm (1).jpg" alt="" data-size="line"> プロパティを変数にする、プロパティを変数に書き込んでその値を使用/編集する、または既存の変数をプロパティに書き込むことができます。

別の例として、最初にアクティブ化されたときだけ実行できるコマンドのスペースを作成します。たとえば、NPCに話しかけたときを追跡し、最初に話しかけたときに特別なことを言わせるなどです。

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

このNPCをコピーアンドペーストして、テキストを更新するだけです。それぞれが独自のプロパティを追跡し、NPCごとに1回だけ条件を実行できるようにします。

ほとんどのコマンドは、変数、パラメータ、またはプロパティを参照できます。作成されるまで、このリストには表示されません。

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

## デフォルト値

さまざまなタイプのデータには、それぞれ異なるデフォルト値があります。

* 変数は自動的に0から始まります。
* パラメータは、デフォルト値を選択するように求めます。
* プロパティは、デフォルト値を選択するように求めます。

特定のタイプのデータをデフォルトとして選択した場合、どのタイプのデータも受け入れることができ、それ以降は、そのデータ型になります。

## -- 条件

変数だけではあまり意味がありません。変数をコマンドに組み込む以外に、条件は変数をチェックし、内部の値に基づいてコードを実行します。これらをIF文と呼び、論理的に考えることができます。

変数が0と等しい場合は、Xを実行します。\
変数が1と等しい場合は、Yを実行します。\
変数が2と等しい場合は、Zを実行します。

ELSEステートメントを追加して、IF部分が真でない場合にどうなるかを決定することもできます。

変数が0より大きい場合は、Xを実行します。そうでない場合は、Yを実行します。

値が1以上の場合は1つのアクションを実行し、それ以下の場合は別のことを実行します。ELSEをいつ使用するかは、何を達成しようとしているかによって異なります。通常、ELSEは結果が2つしかない場合にのみ使用します。結果が3つ以上ある場合は、ELSE部分を無効にした複数の条件を使用することをお勧めします。

条件ウィンドウの下部にあるチェックボックスをオンにして、ELSEを有効にします。

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

IFステートメントのみが必要になる場合も多々あります。ELSEステートメントを空のままにするのではなく、無効にすることをお勧めします。

条件を使用する場合、最初に参照するデータのタイプを選択します。ほとんどのデータ型には、異なる基準があります。

### 変数/パラメータ/プロパティ

このセクションは、おそらく最も一般的に使用されます。ゲーム内のさまざまなことを追跡するために、多くの変数を使用します。剣を振るたびに1つずつ増やすことで、主人公のアクションを追跡します。次のNPCに話しかけたり、アクションを完了するたびに1つずつ増やすことで、クエストの進捗状況を追跡します。すべてのスイッチ/メッセージは、本質的に変数です。

パラメータまたはプロパティを設定していない場合は、変数を選択することしかできません。

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

追加すると、ドロップダウンメニューから選択できるようになります。

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

これらを使用する場合、次の標準的な数学的オプションを使用できます。

* 等しい
* 等しくない
* 以上
* 以下
* より大きい
* より小さい

最後のフィールドは、比較対象です。一般に、var/param/prop内のデータ型と一致する必要があります。変数にSwitch:ONを書き込んだ場合は、別のSwitchデータ型と比較することをお勧めします。タイプのすべてのクロスコンビネーションが機能するわけではありません。

単純なIFステートメントの場合、ほとんどの場合、4などの静的な数値を使用します。ただし、複雑で動的なシステムの場合、別のvar/param/propとの比較を開始します。これについては、後で詳しく説明します。

### 主人公

このセクションには、主人公に関連する多くのタイプのデータが含まれており、それぞれに異なる基準があります。より大きいなどの数学的オプションだけではありません。

最初にターゲットを選択します。

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

これは、すべての主人公に適用されます。ただし、下のオプションのチェックボックスをオンにすると、どの主人公のグループを参照するかを選択できます。アクティブなパーティだけに影響を与えたい場合があります。

残りのコマンドは自明です。

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

### 所有物

このセクションでは、主人公が所持しているアイテム（インベントリ内または主人公に装備されているアイテムの両方）を確認します。これらは、より大きいなどの数学的オプションのみを使用し、すべて自明です。

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

### その他

このセクションには、前のカテゴリに分類されないその他すべてのタイプのデータが含まれています。

* キー押下 - キーが押されているかどうかを確認します。キーが押されていることを知るには、これをSwitch:ONに設定します。エンジンは常にこれらの値を自動的に追跡しています。

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

* オブジェクトの視線 - オブジェクトがどの方向を向いているかを確認します。これは、南から時計回りに0から始まる数値で表されます。エンジンは常にこの値を自動的に生成しています。

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

* オブジェクトが登っている - オブジェクトが現在登るアニメーション中かどうかを確認します。データ>タイルセットで登ることを有効にしたタイルでのみ機能します。

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

* クロノメーター - 既存のクロノメーター（タイマー）の値を確認します。最初に「クロノメーター」コマンドを使用して開始する必要があります。ここで、一致するIDを選択して監視し、特定の時間に達したときにコードを実行します。

<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

* 前回の戦闘から逃げる - 直前の戦闘から逃げると、内部スイッチがオンになり、これが現在オンになっているかどうかを確認します。前回の戦闘から逃げた場合、新しい戦闘のボーナスを無効にすることがあります。

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

* スクリプト - javacsriptを使用して何かを確認します。

<figure><img src="../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

## 変数の置換

ほとんどのコマンドでは、数値を選択するか、変数を使用するかを選択できます。変数を使用することにより、他の場所で変数を編集して、その使用結果を変更できます。

いくつかの例を以下に示します。

### 選択を行う

プレイヤーにどの主人公を回復するかを選択させることができます。

チームには、IDが1、2、3、4の4人の主人公がいます。選択肢ごとに異なる値に設定された変数を指定して、「選択肢の表示」コマンドを使用できます。

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

その変数を使用して、プレイヤーが選択した主人公を参照できます。

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

### どれをチェックするか？

1人の主人公を確認するには、変数を静的な数値に設定し、条件内でその変数を参照します。

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

4人すべての主人公がバトルソードを持っているかどうかを確認したい場合があります。主人公ごとに1つずつ、合計4つの条件を作成できます。または、変数をインクリメントして、コードをループすることもできます。主人公のIDが順番になっている限り、これは可能です。

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

> 変数をシーケンスの最初の主人公に設定します。
>
> 条件は、最初の主人公が剣を持っているかどうかを確認します。
>
> 見つかった場合は、誰が持っていたかを示すメッセージが表示され、空に置き換えられます（装備解除と同じ）。
>
> 変数をインクリメントするため、今度は2番目の主人公を指します。
>
> 別の変数をインクリメントして、ループの実行回数を追跡できるようにします。
>
> 4人の主人公をチェックする必要があるため、カウントが4未満の場合はループを続ける必要があります。そのため、先頭に戻ります。
>
> 2番目の主人公に対して、今回は変数が2に設定された状態で、同じ条件が2回目に実行されます。
>
> これは主人公ごとに繰り返され、カウントが4に達するとループが停止し、終了します。

可能性は無限大です。変数を置き換えるフィールドによって、その使用方法が決まることに注意してください。フィールドによっては、新しい数値、どの主人公を選択するか、どのスキルを忘れるかなどを求めるものがあります。変数の使用は、多くの場合、静的な数値/選択肢の入力と同じです。デフォルトの使用方法はさまざまです。

## -- 結論

これらをどれだけ複雑に使用するかはあなた次第です。学習を始めたばかりの人は、シンプルに始めて、徐々に複雑なものに進めていきましょう。適切な外部メモを取っておくことで、特に長い時間が経過した後にコードを確認する必要があるときに、すべてを追跡するのに役立ちます。

KevinOfNine著
