---
title: Welcome
description: Welcome to Dune Docs
hide:
  - navigation
---
<style>
.md-typeset h1,
.md-content__button {
display: none;
}
.md-header__topic{
font-weight: bold;
}
</style>

![Dune Docs cover](images/dune-docs-cover.jpg)

Duneは、膨大なブロックチェーンデータを発見、探索、可視化するために必要なすべてのツールを備えた、ブロックチェーン研究のための強力なツールです。

デューンは、こんな疑問を解決する鍵になります。

- [How much volume flows through Uniswap each day?](https://dune.com/queries/3)

- [Which Dex has the highest volume?](https://dune.com/queries/1847)

- [How are important Stablecoins behaving today?](https://dune.com/hagaetc/stablecoins)

## Dune in 5-minutes ⚡
![type:video](https://www.youtube.com/embed/S-cctFmR828)

## How the data flows
<img alt="how the data flows" class="hoz-cent" src="images/how-the-data-flows.jpg">

パブリックブロックチェーンは[open and free](https://dune.com/blog/revolution-not-quarterly)なので、そこからデータを取得するのはそんなに難しくないはずですよね？

イエスでもあり、ノーでもある。

例えば、国際輸送のスピードがパリの最新クチュールの消費者需要にどのように影響するかを分析するために、従来のビジネスから孤立したデータを取得することに比べれば...。

そうブロックチェーンのデータを閲覧、分析することは "簡単 "です。

しかし、Duneのことわざのフードの下には多くのことが起こっています。イーサリアムのようなパブリックブロックチェーン上の状態の変化が、どのようにしてチャートやグラフを作成するためにクエリするデータに変わるのかをよりよく理解するために、フードを開けて見てみましょう。

### <img alt="chain adds a block" src="images/chain-adds-a-block.png" class="vrt-cent"> <span class="vrt-cent"> 1. A chain adds a block</span>
技術的な詳細はさまざまですが、すべてのブロックチェーンの中核には、一連の取引が提案され、合意された後、以前に合意された取引を含むブロックのチェーンの末尾に追加されるようになっています。

どのブロックを次のブロックとするかは、様々な[consensus mechanisms](https://crypto.com/university/consensus-mechanisms-in-blockchain)、方法がありますが、コンセンサスが得られると、最新のブロックに関する情報がブロックチェーンのネットワークにブロードキャストされ、参加者（「ノード」）にこの新しいブロックを知らせ、自分の記録に追加することができます。

ブロックチェーンの仕組みについて詳しく知りたい方は[Check out this awesome Blockchain 101 demo](https://andersbrownworth.com/blockchain/)!

### <img alt="nodes transmit to dune" src="images/nodes-transmit-to-dune.png" class="vrt-cent"><span class="vrt-cent"> 2. Node providers transmit data to Dune</span>
この「新しいブロックが作成された」というメッセージを受け取るには、誰かが[blockchain node](https://www.alchemy.com/overviews/what-is-an-ethereum-node)を実行する必要があります。[blockchain node](https://www.alchemy.com/overviews/what-is-an-ethereum-node)は、ブロックチェーンのネットワークに接続し、他のノード間で情報を送ったり、場合によっては取引の検証やデータの保存を可能にする「クライアント」ソフトウェアを実行するコンピュータです。

ちょっとした技術的なノウハウがあれば、誰でもノードを動かすことができる。それがブロックチェーン*public*の大きな特徴です

ほぼ全員がノードを運営できるため、参加者の誠実さを保つために、システムには多くの透明性があります。

この透明性により、データアナリストが「何が起こっているか」の全体像にアクセスし、あらゆる種類の分析を行うことができるようになり、ハイブマインドを活用することも可能になります。

生データにアクセスするための苦労は必要ない。

Duneのようなプロジェクトが大規模に運用できるように、[node providers](https://www.alchemy.com/overviews/blockchain-node-providers)はブロックチェーンのデータを取得するノードインフラを構築・運用し、アプリケーションプログラミングインターフェース（API）を通じて私たちがアクセスできるようにします。

こうすることで、私たちは可能な限り最高のデータアクセス体験を提供することに集中でき、ノードプロバイダーは可能な限り効率的にノードを稼働させることに集中できるのです。

### <img alt="dune adds to sql tables" src="images/dune-adds-to-sql-tables.png" class="vrt-cent"><span class="vrt-cent"> 3. Dune adds raw data to SQL tables</span>
ノードプロバイダーはブロックチェーンの取引データをハッシュ化されたバイトコードとして送ってきます（例えば、イーサリアムのデータは[the keccak256 algorithm](https://medium.com/0xcode/hashing-functions-in-solidity-using-keccak256-70779ea55bb0)でハッシュ化されています）。

Dune Data Engineはこのバイトコードを取り出し、"[Raw Data](https://dune.com/docs/tables/v2/raw/) "と呼ぶテーブル群に抽出します。

これらはチェーンによって多少異なりますが、一例として、ほとんどの[Ethereum Virtual Machine (EVM)](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/creation-traces/)ベースのチェーンでは、以下のようなものがあります。

* [[chain].blocks](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/blocks/) - チェーンに追加されたトランザクションのグループ。

* [[chain].creation_traces](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/creation-traces/) - [`create` traces](https://medium.com/coinmonks/ethereum-data-evm-traces-simplified-5e297e4f40a4)を含むトランザクション（内部トランザクションに含まれることもある）

* スマートコントラクトで作成された[[chain].logs](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/event-logs/)～[event logs](https://medium.com/mycrypto/understanding-event-logs-on-the-ethereum-blockchain-f4ae7ba50378)

* ブロック内のトランザクションで発生する[[chain].traces](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/traces/)～[trace data](https://medium.com/coinmonks/ethereum-data-evm-traces-simplified-5e297e4f40a4)

* [[chain].transactions](https://dune.com/docs/tables/v2/raw/ethereum-mainnet/transactions/) - あるアドレスから別のアドレスに送信される暗号化された署名付き命令。

これらのテーブルのデータは人間が読むことができますが（バイトコードはそうではありません）、理解し解釈するにはブロックチェーンに関する幅広い知識が必要です。

このRaw Dataは、興味深いインサイトに操作するのに多くの手間がかかることもあり、Dune [decodes](https://dune.com/docs/tables/decoded/)はこのデータを使用しています。

### <img alt="dune decodes data" src="images/dune-decodes-data.png" class="vrt-cent"><span class="vrt-cent"> 4. Dune decodes raw data</span>
生の`.log`テーブルは、次のようなデータを返します。

この形式のデータは、かなり限定的なデータ分析のユースケースがある。

このデータをより使いやすいものに変換するために、[Wizards submit smart contracts for decoding here](https://dune.com/contracts/new).

その際、スマートコントラクトの[Application Binary Interface (ABI)](https://www.alchemy.com/overviews/what-is-an-abi-of-a-smart-contract-examples-and-usage)というWeb2.0のAPIに似たものを使って、コントラクトとやり取りするトランザクションの中で何が起こっているかを理解します。

そして、分析がしやすい[Decoded Tables](https://dune.com/docs/tables/decoded/)を作るのです。

例えば、上記のトランザクションをデコードすると、次のようになります。

### <img alt="community casts spells" src="images/community-casts-spells.png" class="vrt-cent"><span class="vrt-cent"> 5. The Dune community casts Spells</span>
Duneは、Wizardsという素晴らしいコミュニティの力を借りて、[Spells](https://dune.com/docs/tables/spells/)でデータをデコードするだけでなく、さらに一歩踏み込みました。

スペルは、Duneと我々のコミュニティによって構築・維持されているカスタムテーブルで、できるだけ摩擦を少なくして多くのデータを簡単に集計できるようにします。

例えば最も人気のあるスペルの1つである[nft.trades](https://dune.com/spellbook#!/model/model.spellbook.nft_trades)は、Solana上のMagic EdenやEthereum上のLooksRareなどの取引を自分でコンパイルしなくても、プロトコルやブロックチェーン間でNFT取引データの探索と変換を簡単に行えるようにします。

### <img alt="wizards make magic" src="images/wizards-make-magic.png" class="vrt-cent"><span class="vrt-cent"> 6. Dune Wizards make magic</span>
これらのデータから、ウィザードはデータベースへのデータの保存、操作、検索に広く使われている言語であるSQLを使って[Queries](https://dune.com/docs/features/queries/)を構築します。

このクエリから、私たちがよく知っている[Visualizations](https://dune.com/docs/features/visualizations/)と[Dashboards](https://dune.com/docs/features/dashboards/)が作られるのです。

Eg [@rchen8](https://dune.com/rchen8)のOpenSeaの日次ボリューム。

![type:video](https://dune.com/embeds/11385/22601/a9fc0859-cac6-4111-b21d-6104e71b16b5)

## Making 🪄 with dune.com
Dune.comは、Dune Data Platformの上に構築された最初のキラーアプリで、SQL、Ethereum Virtual Machine、ビジネスの知識が少しでもあれば、誰でもできるだけ簡単にブロックチェーンデータを興味深い方法で分析できるように設計されています。

Dune.comアプリの基本的な構成要素は以下のとおりです。

- **Dashboards:** ブロックチェーンデータの特定のグループについてのストーリーを伝えるビジュアライゼーションとテキストを含むウィジェットのセットです。

- **Visualizations:** 表形式でわかりにくいデータを、視覚的にわかりやすくするチャートとグラフ。

- **Queries:** Dune のデータベースからデータを抽出し、Dune のダッシュボードにテーブルとビジュアリゼーションで表示できるようにするコマンドです。

Dune.com の訪問者は、クエリから構築されたテキスト、テーブル、視覚化ウィジェットを含むダッシュボードを閲覧します。

Dune Wizard（ブロックチェーンアナリスト）は、データを取得するためのカスタムクエリを作成し、その結果を可視化し、ダッシュボードを使用してデータを使ったストーリーを語ることができます。

### Queries
Duneは、ブロックチェーンのデータをSQLデータベースに集約し、簡単に問い合わせができるようにします。

[Queries](getting-started/queries/index.md)は、ブロックチェーンからどのようなデータを我々のデータベースで見つけて返すかを指定するために使用されます。

もしかしたら、*all the Dex trades that happened today*や*total value of stablecoins minted this year*を知りたいかもしれません。どんな質問でも、答えの発見はデューンクエリから始まります!

クエリーは、従来のSQLクエリーと同様にデータの行と列を返し、それを使ってダッシュボードに表示するビジュアライゼーションを作成することができます。

![SQL Query - Uniswap USD volume](images/sql-query-uniswap-usd-volume.png)

ブロックチェーンアナリスト（ウィザードすなわちあなた！）がQueriesの実行を開始するには、いくつかの方法があります。

1. 最も簡単な方法は、Dune [*Spells*](reference/tables/spells/index.md)) を使って、よく使われるデータ・テーブルを問い合わせることです。よく使われるスペルには、`dex.trades`、`lending.borrow`、`stablecoin.transfer` があります。

2. ブロック、ログ、トランザクションのような生のEthereumデータを照会します。

3. また、中央集権的な取引所データを照会することも可能です。例えば、`prices.usd`を使用すると、ほとんどすべての暗号資産の価格を迅速に返すことができます。

### Visualizations
表形式（行と列）で表示されたデータは、読みにくいことがあります。[Visualizations](getting-started/visualizations/index.md) は、Query の結果を取り込み、情報を明確、正確、かつ *visual* な方法で提示します。

Dune Visualizationsを使えば、こんな風に変形させることで、簡単にデータのストーリーを語り始めることができるのです。

![Table chart](images/table-chart.png)

このようなものに。

![Bar chart](images/bar-chart.png)

バーチャートで可視化すると、4月19日の転送量が最も多かったことがわかり、時系列でトレンドを把握することができます。

Duneは、データを視覚的に表現するために、以下のような様々なVisualizationを提供しています。

- **Bar Charts**

- **Area Charts**

- **Scatter Charts**

- **Line Charts**

- **Pie Charts**

- **Counters**

- **Tables**

### Dashboards
綿密に計画されたビジュアルを使い、賢いブロックチェーンアナリスト（ウィザード！）は、[Dune Dashboards](getting-started/dashboards.md)を通じてさまざまなデータの集まりについて物語を語ることができます。

例えば、下のダッシュボード、[Dex Metrics](https://dune.com/hagaetc/dex-metrics) by [@hagaetc](https://dune.com/hagaetc)では、カテゴリーとしての「DEX」が成長していることが上部にはっきりと示されています。その下には、どのDEXが出来高で最も人気があるかが表示され、最後に時間的な変化を示す積み上げ棒グラフを見ることができます。

このダッシュボード一つを見るだけで、誰でもDEX市場全体を把握することができるのです。

![Dashboard](images/dashboard.png)

## How to navigate these docs
私たちは、「デューン」のすべてについて、誰が、何を、いつ、どこで、なぜ、どのように、という質問に答えるために、これらのドキュメントを作りました。

ここでは、各セクションの内容を簡単にご紹介します。

- [Getting Started](getting-started/index.md)は、Duneの使い方を学ぶための場所です。

- [Reference](reference/index.md)では、「誰が、何を、どこで」という質問に対する答えや、私たちがまとめたいくつかの補足資料をご覧いただけます。

- [Spellbook](spellbook/index.md)には、スペルの作成と使用に必要なものがすべて揃っています。

- [API](api/index.md) は、私たちの API をあなたのプロジェクトに統合するために必要なすべてのものを見つける場所です。

もし、あなたが杖を使いたくてうずうずしているなら、[Query Quick Start](getting-started/query-quick-start/index.md)に飛んで、最初のDune Queryを作るためのチュートリアルを見てください。

## Dune is a community effort
Dune.com では、すべてのクエリとデータセットがデフォルトで公開されています（クエリにプライバシーが必要な場合は、[Pro Plan](https://dune.com/pricing) で対応可能です）。

これにより、Wizardは他のクリエイターのQueryをフォーク、リミックスして、彼らの知識や洞察力の上に構築することが容易になります。

逆に、新しいQueryを作成するたびに、Duneを通じて他の人がブロックチェーンや暗号資産について新しいことを学ぶのに役立ちます。

このポジティブなフィードバックループによって、デューンコミュニティは、私たち全員がより多くを学ぶことができる、増え続けるクエリの範囲を通して、共に成功することができるのです。

私たちの[Community Discord](https://discord.gg/BJBHFR6sdy)に参加すれば、私たちのチームとコミュニティから世界レベルのサポートを受けることができます。

楽しいLIVEに参加するために、[events calendar](reference/events.md)をチェックしてみてください。

また、機能要望やバグレポートなど、フィードバックがあれば、[here](https://feedback.dune.com)に提出してください。

