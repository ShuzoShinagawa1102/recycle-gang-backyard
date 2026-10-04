# バックヤードの構成

## 利用者と責務

| 領域 | 対象 | 操作 | 契約 |
|---|---|---|---|
| provider | 業者、Web/iOS/Android | オファー、担当回収、採用済み経路、実績、SOS | backyard.yaml |
| admin | Recycle Gang管理者、Web | 運行・募集・割当、経路計算と採用、状況照会、監査 | admin.yaml |

同じFlutterプロジェクト内でfeature・Webルート・SDKを分離する。Webルートは`/provider`と`/admin`。画面幅と入力方法に応じ、現場のモバイル操作とPCの一覧・比較操作を構成する。

画面は入力補助・API呼出し・状態表示を担う。業務判定、所属/所有権、管理者の操作権限は基幹が検証する。optimizerと業務DBへ直接接続しない。

## フォルダ構成

```text
recycle-gang-backyard/
├── flutter/
│   ├── lib/
│   │   ├── app/                    # 起動・認証・ルート・環境
│   │   └── features/
│   │       ├── provider/
│   │       │   ├── offers/
│   │       │   ├── collections/
│   │       │   └── sos/
│   │       └── admin/
│   │           ├── service_runs/
│   │           ├── dispatch/
│   │           ├── route_planning/
│   │           └── audit/
│   ├── packages/
│   │   ├── backyard_api/
│   │   └── admin_api/
│   ├── test/
│   └── integration_test/
├── ci/
└── doc/
```

各featureをpresentation / application / dataへ分ける。Riverpod、go_router、Dioを利用し、SDKのDTOを画面の表示モデルへ変換する。

## 管理者の経路計画操作

計算要求でjobIdを受け取り、基幹から状態と候補を取得する。未割当・警告を確認してから候補採用を要求する。`409 STALE_SNAPSHOT`では入力の変更を表示し、再計算へ進める。古い候補を強制上書きする画面は作らない。

## 配布

`backyard-vX.Y.Z`で版を管理する。管理者Webもこの版に含める。Web/iOS/Androidの成果物・ビルド番号・公開状態は個別に記録する。モバイルに管理者ナビゲーションを表示しない。

開発は`develop/v1`を基準にする。[共通CI/CD](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/develop/v1/doc/process/ci-cd-policy.md)と[モバイル配布](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/develop/v1/doc/architecture/infrastructure/mobile-delivery.md)に従う。
