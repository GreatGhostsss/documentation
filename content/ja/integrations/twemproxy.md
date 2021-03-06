---
assets:
  dashboards: {}
  logs: {}
  monitors: {}
  service_checks: assets/service_checks.json
categories:
  - web
  - autodiscovery
creates_events: false
ddtype: check
dependencies:
  - 'https://github.com/DataDog/integrations-core/blob/master/twemproxy/README.md'
display_name: Twemproxy
git_integration_title: twemproxy
guid: a5cca58a-9984-4226-ad1c-8dff73c9d6ac
integration_id: twemproxy
integration_title: Twemproxy
is_public: true
kind: インテグレーション
maintainer: help@datadoghq.com
manifest_version: 1.0.0
metric_prefix: twemproxy.
metric_to_check: twemproxy.total_connections
name: twemproxy
public_title: Datadog-Twemproxy インテグレーション
short_description: twemproxy のパフォーマンスを視覚化し、他のアプリケーションと関連付け
support: コア
supported_os:
  - linux
  - mac_os
  - windows
---
## 概要

各 Twemproxy サーバーで、全体の統計とプールごとの統計を追跡します。この Agent チェックは、クライアントとサーバーの接続とエラー、リクエスト率と応答率、プロキシの受送信バイト数などのメトリクスを収集します。

## セットアップ

### インストール

Agent の Twemproxy チェックは [Datadog Agent][1] パッケージに含まれています。Twemproxy サーバーに追加でインストールする必要はありません。

### 構成

#### ホスト

ホストで実行中の Agent でこのチェックを構成する場合は、以下の手順に従ってください。コンテナ環境の場合は、[コンテナ化](#コンテナ化)セクションを参照してください。

1. [Agent のコンフィギュレーションディレクトリ][2]のルートにある `conf.d/` フォルダーの `twemproxy.d/conf.yaml` ファイルを編集します。使用可能なすべてのコンフィギュレーションオプションの詳細については、[サンプル twemproxy.d/conf.yaml][3] を参照してください。

   ```yaml
   init_config:

   instances:
     - host: localhost
       port: 22222
   ```

2. [Agent を再起動][4]すると、Datadog へ Twemproxy メトリクスの送信が開始します。

#### コンテナ化

コンテナ環境の場合は、[オートディスカバリーのインテグレーションテンプレート][5]のガイドを参照して、次のパラメーターを適用してください。

| パラメーター            | 値                                  |
| -------------------- | -------------------------------------- |
| `<インテグレーション名>` | `twemproxy`                            |
| `<初期コンフィギュレーション>`      | 空白または `{}`                          |
| `<インスタンスコンフィギュレーション>`  | `{"host": "%%host%%", "port":"22222"}` |

### 検証

[Agent の `status` サブコマンドを実行][6]し、Checks セクションで `twemproxy` を探します。

## 収集データ

### メトリクス
{{< get-metrics-from-git "twemproxy" >}}


### イベント

Twemproxy チェックには、イベントは含まれません。

### サービスのチェック

`twemproxy.can_connect`:

Agent が Twemproxy 統計エンドポイントに接続してメトリクスを収集できない場合は、CRITICAL を返します。それ以外の場合は、OK を返します。

## トラブルシューティング

ご不明な点は、[Datadog のサポートチーム][8]までお問合せください。

[1]: https://app.datadoghq.com/account/settings#agent
[2]: https://docs.datadoghq.com/ja/agent/guide/agent-configuration-files/#agent-configuration-directory
[3]: https://github.com/DataDog/integrations-core/blob/master/twemproxy/datadog_checks/twemproxy/data/conf.yaml.example
[4]: https://docs.datadoghq.com/ja/agent/guide/agent-commands/#start-stop-and-restart-the-agent
[5]: https://docs.datadoghq.com/ja/agent/kubernetes/integrations/
[6]: https://docs.datadoghq.com/ja/agent/guide/agent-commands/#agent-status-and-information
[7]: https://github.com/DataDog/integrations-core/blob/master/twemproxy/metadata.csv
[8]: https://docs.datadoghq.com/ja/help/