---
layout: default
title: リソース
nav_order: 7
---

# リソース
{: .no_toc }

AI-DLC に関する公式ドキュメント・ブログ記事・リポジトリへのリンク集
{: .fs-6 .fw-300 }

---

## 公式ドキュメント

| リソース | 説明 | リンク |
|--------|------|--------|
| **AI-DLC Method Definition Paper** | 方法論の正式定義書 | [amplifyapp.com](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) |
| **awslabs/aidlc-workflows** | オープンソース実装（GitHub） | [github.com/awslabs/aidlc-workflows](https://github.com/awslabs/aidlc-workflows) |
| **最新リリース** | ai-dlc-rules の最新版ダウンロード | [Releases ページ](https://github.com/awslabs/aidlc-workflows/releases/latest) |

---

## AWS ブログ記事

| タイトル | 概要 | リンク |
|--------|------|--------|
| **AI-Driven Development Life Cycle（日本語版）** | AI-DLC 方法論の概要・3フェーズ・メリットを解説 | [AWS Blog JP](https://aws.amazon.com/jp/blogs/news/ai-driven-development-life-cycle/) |
| **AI-Driven Development Life Cycle（英語版）** | 同上の英語原文 | [AWS Blog DevOps](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) |
| **Open-Sourcing Adaptive Workflows for AI-DLC** | AI-DLC ワークフローのオープンソース化発表 | [AWS Blog](https://aws.amazon.com/blogs/devops/open-sourcing-adaptive-workflows-for-ai-driven-development-life-cycle-ai-dlc/) |
| **Building with AI-DLC using Amazon Q Developer** | Amazon Q Developer を使った AI-DLC 実践ウォークスルー | [AWS Blog](https://aws.amazon.com/blogs/devops/building-with-ai-dlc-using-amazon-q-developer/) |

---

## プラットフォーム別ドキュメント

| プラットフォーム | ドキュメント |
|----------------|-------------|
| **Kiro** | [Kiro Steering Files](https://kiro.dev/docs/cli/steering/) |
| **Amazon Q Developer** | [Q Developer IDE Plugin](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html) |
| **Cursor** | [Cursor Rules](https://cursor.com/docs/context/rules) |
| **Claude Code** | [Claude Code GitHub](https://github.com/anthropics/claude-code) |
| **GitHub Copilot** | [Copilot Docs](https://docs.github.com/en/copilot) |

---

## リポジトリ内の主要ファイル

| ファイル | 説明 |
|--------|------|
| [`README.md`](https://github.com/awslabs/aidlc-workflows/blob/main/README.md) | セットアップガイド・プラットフォーム別手順 |
| [`aidlc-rules/aws-aidlc-rules/core-workflow.md`](https://github.com/awslabs/aidlc-workflows/blob/main/aidlc-rules/aws-aidlc-rules/core-workflow.md) | コアワークフロー定義（各AIエージェントに組み込む） |
| [`docs/WORKING-WITH-AIDLC.md`](https://github.com/awslabs/aidlc-workflows/blob/main/docs/WORKING-WITH-AIDLC.md) | AI-DLC の実践ガイド・インタラクションパターン |
| [`docs/GENERATED_DOCS_REFERENCE.md`](https://github.com/awslabs/aidlc-workflows/blob/main/docs/GENERATED_DOCS_REFERENCE.md) | 生成される `aidlc-docs/` の完全なリファレンス |
| [`docs/writing-inputs/`](https://github.com/awslabs/aidlc-workflows/tree/main/docs/writing-inputs) | Vision・Technical Environment ドキュメントの記述ガイド |
| [`CHANGELOG.md`](https://github.com/awslabs/aidlc-workflows/blob/main/CHANGELOG.md) | バージョン履歴（git-cliff 自動生成） |

---

## 関連技術

AI-DLC が対応する AI コーディングツール：

- [Kiro](https://kiro.dev/) — AWS の AI-IDE
- [Amazon Q Developer](https://aws.amazon.com/jp/q/developer/) — AWS の AI コーディングアシスタント
- [Cursor](https://cursor.com/) — AI-first エディタ
- [Cline](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) — VS Code の AI エージェント拡張
- [Claude Code](https://github.com/anthropics/claude-code) — Anthropic の CLI エージェント
- [GitHub Copilot](https://github.com/features/copilot) — GitHub の AI ペアプログラマー
- [OpenAI Codex](https://developers.openai.com/) — OpenAI のコーディングエージェント

---

## ライセンス

`awslabs/aidlc-workflows` は **MIT-0 ライセンス**（帰属表示不要の MIT）で公開されています。
自由に使用・変更・配布できます。
