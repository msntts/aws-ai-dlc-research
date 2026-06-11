---
layout: default
title: サポートツール
nav_order: 6
---

# サポートツール
{: .no_toc }

AI-DLC ワークフローを補完する評価・レビューフレームワーク
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>目次</summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## AIDLC Evaluator

**場所：** [`scripts/aidlc-evaluator/`](https://github.com/awslabs/aidlc-workflows/tree/main/scripts/aidlc-evaluator)

AI-DLC ワークフローへの変更を検証するための自動テスト・レポートフレームワークです。

### 機能

| 機能 | 説明 |
|------|------|
| **ゴールデンテストケース** | 検証用のベースラインテストケース集 |
| **実行フレームワーク** | 評価パイプラインを通じたテストケースのオーケストレーション |
| **セマンティック評価** | AIベースの出力の正確性・完全性評価 |
| **コード評価** | 静的解析（リンティング・セキュリティスキャン・重複検出） |
| **NFR評価** | 非機能要件テスト（トークン使用量・実行時間・クロスモデル一貫性） |
| **CI/CD統合** | PR検証の自動化パイプライン |

### クイックスタート

```bash
cd scripts/aidlc-evaluator
uv sync
uv run python run.py test
```

---

## AIDLC Design Reviewer

**場所：** [`scripts/aidlc-designreview/`](https://github.com/awslabs/aidlc-workflows/tree/main/scripts/aidlc-designreview)

{: .warning }
> **実験的機能（EXPERIMENTAL）** — AWS Bedrock 経由の Claude モデルを使用して AIDLC 設計成果物を分析する AIパワードデザインレビューツールです。

### 機能

| 機能 | 説明 |
|------|------|
| **マルチエージェントレビュー** | 3つの専門AIエージェント（批評・代替案・ギャップ分析） |
| **品質スコアリング** | 重み付けされた重大度分析と実行可能な推奨事項 |
| **CLIツール** | CI/CDパイプライン向けのオンデマンドレビュー |
| **Claude Code Hook** | 開発中のリアルタイムレビュー（実験的） |

### インストール（CLI ツール）

```bash
cd scripts/aidlc-designreview
uv sync --extra test
source .venv/bin/activate  # Linux/Mac
design-reviewer --aidlc-docs /path/to/aidlc-docs
```

### インストール（Claude Code Hook）

```bash
# ワークスペースルートから
./scripts/aidlc-designreview/tool-install/install-linux.sh      # Linux
./scripts/aidlc-designreview/tool-install/install-mac.sh        # macOS
.\scripts\aidlc-designreview\tool-install\install-windows.ps1   # Windows PowerShell
```

インストーラーがワークスペースルートを自動検出し、`.claude/` にフックをインストールします。

---

## セキュリティスキャナー（CI/CD）

リポジトリ自体は6つのセキュリティスキャナーを `main` へのプッシュ・PR・毎日のスケジュールで実行しています。AI-DLC ルールの開発に貢献する場合に参考にしてください。

| スキャナー | 検出対象 | 失敗条件 | 設定ファイル |
|-----------|---------|---------|------------|
| **Bandit** | Python SAST問題 | 高信頼度の発見 | `.bandit` |
| **Semgrep** | 多言語SAST | 任意の発見（PR:新規のみ） | `.semgrepignore` |
| **Grype** | 依存関係の CVE | High/Critical CVE | `.grype.yaml` |
| **Gitleaks** | git履歴内のシークレット | ベースライン外のシークレット | `.gitleaks.toml` |
| **Checkov** | IaC 設定ミス | 任意のチェック失敗 | `.checkov.yaml` |
| **ClamAV** | マルウェア | 任意の検出 | なし |

すべての HIGH・CRITICAL 発見はマージ前に修正またはリスク受容の文書化が必要です。
