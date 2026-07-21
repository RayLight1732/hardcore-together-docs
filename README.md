# Hardcore Together Docs

「Hardcore Together」プロジェクトの仕様書・アーキテクチャ設計ドキュメントを管理するリポジトリです。

Paper+Velocity製の既存実装を、NeoForge + Gate（Gate/Managerの2プロセス構成）へ移行するための設計をまとめています。実装本体（Gate、Manager、hardcore MOD、lobby MOD）はそれぞれ別リポジトリで管理され、本リポジトリはリポジトリ横断で共有する仕様・プロトコル定義のドキュメントのみを扱います。

## コンポーネント構成

| コンポーネント | 役割 |
|---|---|
| Hardcore Together Gate | 接続ルーティング、コマンド受付・権限チェック、プレイヤー退避・自動転送を行うプロキシ（Go） |
| Hardcore Together Manager | hardcoreサーバーのプロセスライフサイクル管理、ワールドのバックアップ/アーカイブ、挑戦記録の参照（Go、常駐プロセス） |
| Parkour Lobby | チェックポイント機能を持つ待機用lobbyサーバー（NeoForge） |
| Hardcore Together | 死亡/討伐判定・タイマー・記録管理を行うhardcoreサーバー本体（NeoForge） |

## ドキュメント一覧

- [`docs/specification.md`](docs/specification.md) — 全体仕様書。プロジェクト名・アーキテクチャ・各コンポーネントの仕様・プロトコル概要
- [`docs/architecture-gate.md`](docs/architecture-gate.md) — Gateリポジトリの実装設計
- [`docs/architecture-manager.md`](docs/architecture-manager.md) — Managerリポジトリの実装設計（レイヤードアーキテクチャ）
- [`docs/architecture-neoforge.md`](docs/architecture-neoforge.md) — hardcore MOD（NeoForge）の内部アーキテクチャ設計
- [`docs/protocol-gate-manager.md`](docs/protocol-gate-manager.md) — Gate ⇔ Manager間シグナルプロトコル定義
- [`docs/protocol-mod-manager.md`](docs/protocol-mod-manager.md) — hardcore MOD ⇔ Manager間シグナルプロトコル定義

`specification.md`が全体仕様の正であり、各`architecture-*.md`はそれを個別リポジトリの実装へどう落とし込むかの設計、各`protocol-*.md`はプロセス間通信の詳細な取り決めです。
