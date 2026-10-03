# 基幹APIの利用契約

更新日：2026-10-03。OpenAPI本体・SDKは未生成。

提供側の予定位置は`recycle-gang/contracts/openapi/backyard.yaml`。本アプリはその版付きbundleと生成器設定からSDKを生成する。提供側YAMLの独自コピーを編集して分岐させない。

| 項目 | 方針 |
|---|---|
| 接続先 | 環境別の安定API URL＋`/api/backyard/v1/...` |
| 対応の管理 | 使用契約版/ハッシュ、必要機能、試験済みBE版、公開中アプリ版を区別 |
| 認可 | 業者所属・担当作業・運営権限をBEで検証 |
| データ取得 | 採用済み経路と担当回収をBEから取得。optimizerへ直接接続しない |
| 更新 | 成果記録/SOS/オファー応答をBEへ要求。DBへ直接接続しない |
| 再送 | 通信失敗時の再試行は契約の冪等性仕様に従う。二重実績を作らない |
| 更新の競合 | 状態/版の競合を表示し再取得する。古い画面で無条件上書きしない |

サーバー実装版への固定URLを持たない。BEが互換更新されれば同じアプリが接続を継続できる。SDK更新時は契約差分と旧版互換を確認する。

仕様の正：[API契約・生成方針](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/architecture/backend/api-contract-policy.md)。
