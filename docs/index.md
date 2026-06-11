---
layout: default
title: ホーム
nav_order: 1
description: AWS AI-Driven Development Life Cycle (AI-DLC) の包括的な解説ドキュメント
permalink: /
---

# AWS AI-DLC（AI駆動開発ライフサイクル）解説ドキュメント
{: .fs-9 }

AIがコードを書き、人間が意図を守る。開発の新しいパラダイム。
{: .fs-6 .fw-300 }

[AI-DLCとは →]({{ site.baseurl }}/overview){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[セットアップガイド →]({{ site.baseurl }}/setup){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## このドキュメントについて

本サイトは、AWSが提唱する **AI-Driven Development Life Cycle（AI-DLC）** を調査・解説したものです。以下の公式情報源を集約しています。

| 情報源 | 種別 |
|--------|------|
| [AWS Blog: AI-Driven Development Life Cycle](https://aws.amazon.com/jp/blogs/news/ai-driven-development-life-cycle/) | 方法論ブログ |
| [AI-DLC Method Definition Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) | 方法論定義書 |
| [awslabs/aidlc-workflows (GitHub)](https://github.com/awslabs/aidlc-workflows) | オープンソース実装 |

---

## AI-DLCを一言で言うと

> **「AIが実行し、人間が監視する」動的チームコラボレーションによるソフトウェア開発方法論**

従来の「AIがコードを提案する」ツール活用とも、「AIが完全自律で動く」全自動化とも異なる第三の道です。AIがルーティンタスクを担いながら、すべての重要な意思決定で人間の承認を得ます。

---

## サイト構成

```
AI-DLC 概要          → 方法論の背景・哲学・メリット
  └ Inception フェーズ  → 要件定義・設計フェーズ詳細
  └ Construction フェーズ → 実装・テストフェーズ詳細
  └ Operations フェーズ  → 運用フェーズ（今後拡張予定）
セットアップガイド    → ツール別インストール手順
拡張システム         → セキュリティ・テスト等のルール拡張
実践 Tips            → 効果的な使い方・よくある落とし穴
サポートツール       → Evaluator・Design Reviewer
リソース             → 関連ブログ・公式ドキュメント
```

---

## クイックスタート

AI-DLC を効果的に使うには、起動前に以下の2つのドキュメントを準備することを強く推奨します。

| ドキュメント | 内容 |
|------------|------|
| **Vision Document** | 何を・誰のために作るか、MVPスコープ、対象外機能、未決事項 |
| **Technical Environment Document** | 言語・フレームワーク・クラウド構成・禁止ライブラリ・サンプルコード |

これらを準備してからチャットで起動します：

```
I want to start a new project. Please read [ビジョンドキュメントのパス] and
[技術環境ドキュメントのパス], then begin the AIDLC workflow.
```

{: .note }
> ドキュメントなしで起動した場合、AI-DLC が Requirements Analysis で多くの質問を生成します。ドキュメントを先に準備するほど質問が減り、スムーズに進みます。

詳細なセットアップ手順は[セットアップガイド]({{ site.baseurl }}/setup)を、ドキュメントの書き方は[公式テンプレート](https://github.com/awslabs/aidlc-workflows/tree/main/docs/writing-inputs)を参照してください。

---

{: .note }
> 本サイトの情報は調査時点（2026年6月）のものです。最新情報は[公式GitHubリポジトリ](https://github.com/awslabs/aidlc-workflows)を参照してください。
