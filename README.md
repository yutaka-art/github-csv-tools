<div align="center"><img src="https://github.com/gavinr/github-csv-tools/blob/master/banner.jpg?raw=true" alt="GitHub CSV Tools banner" title="GitHub CSV Tools" />
<h3 align="center">CSV形式でGitHubイシューのインポート・エクスポートツール</h3>
</div>

<p align="center">
  
  <a href="https://github.com/gavinr/github-csv-tools/actions?query=workflow%3ATest+branch%3Amaster">
    <img alt="Build" src="https://github.com/gavinr/github-csv-tools/workflows/Test/badge.svg">
  </a>
  <a href="https://github.com/gavinr/github-csv-tools/actions?query=workflow%3ARelease+branch%3Amaster">
    <img alt="Release" src="https://github.com/gavinr/github-csv-tools/workflows/Release/badge.svg">
  </a>
  <a href="https://www.npmjs.com/package/github-csv-tools">
    <img alt="npm latest version" src="https://img.shields.io/npm/v/github-csv-tools/latest.svg">
  </a>
  <a href="https://repoio.com">
    <img alt="npm latest version" src="https://img.shields.io/badge/hosted-repoio.com-orange">
  </a>
</p>

## 使用方法

前提条件: [Node.jsをインストール](https://nodejs.org/en/)して、以下のコマンドでインストールしてください：

```bash
npm install -g github-csv-tools
```

インストール後、`githubCsvTools --help` で使用方法を確認するか、以下を参照してください。

エクスポート・インポートの手順：

### イシューのインポート

現在、タイトル、本文、ラベル、ステータス（クローズ済み・オープン）、マイルストーンをインポートできます。入力形式の例については[test](/test)フォルダを参照してください。

```bash
githubCsvTools myFile.csv
```

### イシューのエクスポート

```bash
githubCsvTools
```

| オプション             | デフォルト値                                                                   | 備考                                                                                                                                                                                                          |
| ---------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -f, --exportFileName   | YYYY-MM-DD-hh-mm-ss-issues.csv                                                | エクスポートするCSVファイル名                                                                                                                                                                                 |
| -a, --exportAttributes | number, title, labels, state, assignees, milestone, comments, created_at, updated_at, closed_at, body | エクスポートする属性（列）のカンマ区切りリスト**                                                                                                                                                                 |
| -c, --exportComments   | なし                                                                           | エクスポートにコメントを含める。`--exportAttributes`と組み合わせて使用する場合、`id`を含める必要があります                                                                                                     |
| -e, --exportAll        | なし                                                                           | GitHub APIから取得可能なすべての値をエクスポート。含めない場合、GitHubの*インポート*と互換性があることが確認済みの属性のサブセット（上記の`--exportAttributes`を参照）がエクスポートに含まれます |

** `exportAttributes`の利用可能なオプションのリストには、[GitHub API Export](https://developer.github.com/v3/issues/#response-4)のすべてのオプションが含まれます。子オブジェクトの値は「ドット」を使用して参照できます - たとえば、ユーザーの`avatar_url`は`user.avatar_url`でアクセスできます。

### トークン

すべての操作において、ツールはGitHubトークンの入力を求めます。このトークンを取得するには：

1. <https://github.com/settings/tokens> にアクセス
2. 「Generate New Token」をクリック
3. `repo`にチェックを入れる
4. ツールがトークンを求めた際に、提供されたトークンをコピー&ペーストする

## その他のオプション

| オプション              | 備考                                                                          |
| ----------------------- | -----------------------------------------------------------------------------|
| -V, --version           | バージョン番号を出力                                                         |
| -g, --github_enterprise | GitHub EnterpriseのURL。<https://your-internal-githubenterprise.com/api/v3>  <br />（注意：末尾の`/api/v3`を忘れないでください）|
| -t, --token             | GitHubトークン。<https://github.com/settings/tokens>                          |
| -o, --organization      | リポジトリが存在するユーザーまたは組織のスラッグ。<br />例：`/myOrg/my-repo`の場合、この値は**myOrg**になります                    |
| -r, --repository        | リポジトリ名（スラッグ）<br />例：`/myOrg/my-repo`の場合、この値は**my-repo**になります                                                 |
| --csvDelimiter          | CSV区切り文字（デフォルトは','）                                             |
| -v, --verbose           | 追加のログ情報を含める                                                       |
| -h, --help              | すべてのオプションとヘルプを表示                                             |

## 開発

1. リポジトリをクローンする
2. リポジトリディレクトリに移動し、`npm install -g`を実行する

## 更新履歴

[CHANGELOG.md](https://github.com/gavinr/github-csv-tools/blob/master/CHANGELOG.md)を参照

## ホスト版 [![hosted shield](https://img.shields.io/badge/hosted-repoio.com-orange)](https://repoio.com)

このソフトウェアは[repoio.com](https://repoio.com)でダウンロード・インストール不要で使用できます。

## 謝辞

- [octokit/rest.js](https://octokit.github.io/rest.js/)
- [nodeCSV](https://www.npmjs.com/package/csv)
- [commander](https://www.npmjs.com/package/commander)
- [co](https://www.npmjs.com/package/co)
- [Tim Patterson's Post on Atlassian.com](https://developer.atlassian.com/blog/2015/11/scripting-with-node/)
