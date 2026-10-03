# バックヤードの構成案

更新日：2026-10-03。業務BE共有とFlutter Web/モバイル対応は合意済み。フォルダ/ライブラリはレビュー案。

## 責務

画面、入力補助、認証状態、API通信、操作中/失敗時の表示を担当する。業務ルールの最終判断はSpring Boot側。業者所属・担当範囲・運営権限はBEで検証し、表示上の権限分岐だけで制御しない。

スマートフォンは担当訪問・回収結果・SOS等の現場操作、PCは一覧・募集・割当・状況把握に合わせた配置とする。同一Flutter資産を利用しつつ画面幅/入力方法に適応する。

## 目標配置

| パス | 内容 |
|---|---|
| `flutter/lib/app/` | 起動、ルート、テーマ、認証、環境設定 |
| `flutter/lib/features/offers/` | オファー一覧/応答 |
| `flutter/lib/features/collections/` | 担当回収/成果記録 |
| `flutter/lib/features/sos/` | SOS発信/状況 |
| `flutter/lib/features/operations/` | 運営向け操作 |
| `flutter/packages/backyard_api/` | 版付き契約から生成するDart SDK |
| `flutter/test/`、`flutter/integration_test/` | widget/機能/端末試験 |
| `ci/` | build/検証/配布。実装時に追加 |
| `doc/` | 本アプリ固有の設計 |

Riverpod/go_routerは利用者アプリと揃える案。BE/Flyway/業務DBはこのリポジトリへ追加しない。UIの都合で業務モデルをコピーして独自確定しない。

## リリース

タグは`backyard-vX.Y.Z`。Web/iOS/Androidは初期共通アプリ版とし、成果物・ビルド番号・公開状態は別に管理する。Webの出力はbuild/web、iOSはmacOS/Xcode、Androidは対応SDKのあるビルド環境を使う。ECSをCI用に追加する前提はない。

GitFlowとdevelop/v1、CI起動表、05:00 JST日次、手動CDは[共通方針](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/process/ci-cd-policy.md)に従う。業務E2Eでは基幹・optimizerの具体版を固定する。
