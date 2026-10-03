# Recycle Gang Backyard

業者・運営向けFlutterアプリを管理するリポジトリです。Webとモバイルを対象とし、業務BEは[recycle-gang](https://github.com/ShuzoShinagawa1102/recycle-gang)のSpring Bootを共有します。

更新日：2026-10-03。現在は設計文書のみ。Flutterプロジェクト、SDK、CI/CD、AWS/ストア公開は未実装です。

## 担当する機能

オファーの通知・確認・応答、担当回収と採用済み経路の表示、回収成果の記録、SOS、運営向けの管理画面。募集の成立条件・報酬・完了条件の正は基幹リポジトリの[業務ルール](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/business/business-rules.md)です。

## ドキュメント

- [構成・責務](doc/architecture.md)
- [API契約の利用](doc/api-contract.md)
- [全体の開発・運用方針](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/architecture/development-baseline.md)
- [共通のリリース方針](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/process/release-policy.md)
- [共通のCI/CD方針](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/process/ci-cd-policy.md)
- [モバイルビルド・配布案](https://github.com/ShuzoShinagawa1102/recycle-gang/blob/main/doc/architecture/infrastructure/mobile-delivery.md)

全体方針の正は基幹リポジトリに置き、本リポジトリに全文を複製しません。
