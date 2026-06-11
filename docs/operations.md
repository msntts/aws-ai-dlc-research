---
layout: default
title: Operations フェーズ
parent: AI-DLC 概要
nav_order: 3
---

# 🟡 Operations フェーズ
{: .no_toc }

**デプロイと運用**（将来拡張予定）
{: .fs-6 .fw-300 }

---

## 現在の状態

Operations フェーズは **現在プレースホルダー** です。Construction フェーズのビルド・テスト活動がすべて完了した状態を引き継ぎ、将来的にデプロイ・運用ワークフローへ拡張される予定です。

{: .note }
> 現時点では、ビルドとテストに関するすべての活動は Construction フェーズの **Build and Test ステージ** で処理されます。

---

## 将来予定されている機能

Operations フェーズが拡張された際に含まれる予定の機能：

| 機能 | 説明 |
|------|------|
| **デプロイ計画・実行** | IaC（Infrastructure as Code）を用いた自動デプロイ |
| **監視・オブザーバビリティ設定** | メトリクス・ログ・アラートの設定 |
| **インシデント対応手順** | 障害発生時のランブック生成 |
| **メンテナンス・サポートワークフロー** | 継続的な運用タスクの管理 |
| **本番リリース前チェックリスト** | Production Readiness Review の自動化 |

---

## 現在の代替手段

Operations フェーズが正式実装されるまでは、Construction フェーズの Build and Test で生成された以下の成果物を活用してください：

- `build-instructions.md` — ビルド手順
- `integration-test-instructions.md` — 統合テスト
- `performance-test-instructions.md` — パフォーマンステスト

インフラのデプロイについては、Infrastructure Design ステージで生成された IaC 仕様を参照してください。
