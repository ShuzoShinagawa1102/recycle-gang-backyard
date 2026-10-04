# 基幹APIの利用契約

基幹リポジトリの`contracts/openapi/backyard.yaml`と`admin.yaml`を利用する。版付きbundleと生成器設定からそれぞれDart Dio SDKを生成し、取得版・ハッシュを固定する。

| 項目 | 業者 | 管理者 |
|---|---|---|
| APIパス | `/api/backyard/v1/...` | `/api/admin/v1/...` |
| SDK | `flutter/packages/backyard_api/` | `flutter/packages/admin_api/` |
| 認可 | 所属業者・担当作業 | 操作権限・対象範囲 |
| 経路 | 採用済み経路の取得 | 計算要求・候補照会・採用 |

環境別の安定URLをCloudFrontへ向ける。サーバー実装版専用のURLに固定しない。ログイン資格情報とAPI権限は基幹が検証する。API契約を分けるだけでアクセス制御が成立するとは扱わない。

管理者の計算要求・採用要求には`Idempotency-Key`を送る。同じ操作の再送では同じキーと入力を使い、新しい操作には新しいキーを割り当てる。競合時はデータを再取得する。二重回収実績・二重採用を画面の連打防止だけに依存させない。

SDK更新時は契約差分、権限境界、旧版互換性を確認する。使用契約版、必要機能、試験したBE版、公開中アプリ版を別々に記録する。

[契約の正](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/develop/v1/doc/architecture/backend/api-contract-policy.md)、[計算と採用のAPI](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/develop/v1/doc/architecture/backend/optimizer-contract.md)
