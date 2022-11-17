# Dune Docs
Dune Docsへようこそ!

Duneは、コミュニティによる、コミュニティのための暗号分析ツールです。

これらのドキュメントは、オープンソースであり、[Material for MkDocs](https://squidfunk.github.io/mkdocs-material)で構築されています。

誤字脱字からEVMのガイドまで、どんな投稿でも歓迎します。PRを送信してください。

## Install
ローカルでドキュメントを実行したい場合は、以下の手順に従ってください。

[Miniconda](https://docs.conda.io/en/latest/miniconda.html) などでローカルの python 3 環境をセットアップする。

Pythonのライブラリをインストールします。

```bash
pip install -r requirements.txt
```
ローカルでドキュメントを実行する。

```bash
mkdocs serve
```
## Notes
内部リンクにはマークダウンファイルへの相対パスを使用することを忘れないでください (例: `[link](../../relative/path/to/index.md)`)。そうしないと、mkdocsコンパイラは壊れた内部リンクを検出できません - [read more](/index.md)。


