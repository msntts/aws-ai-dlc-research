---
layout: default
title: セットアップガイド
nav_order: 3
---

# セットアップガイド
{: .no_toc }

AI-DLC を各 AI コーディングツールで使えるようにする手順
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>目次</summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## 共通手順

すべてのプラットフォームで共通の準備ステップです。

### 1. リリースのダウンロード

[GitHub Releases ページ](https://github.com/awslabs/aidlc-workflows/releases/latest) から `ai-dlc-rules-v<バージョン>.zip` をプロジェクトディレクトリの**外**にダウンロードします（例：`~/Downloads`）。

### 2. 展開

展開すると `aidlc-rules/` フォルダが作成されます。

```
aidlc-rules/
├── aws-aidlc-rules/           # コアワークフロールール
└── aws-aidlc-rule-details/    # フェーズ別詳細ルール
```

{: .warning }
> **Windowsユーザーへの注意**：エクスプローラーの「すべて展開」は、デフォルトで `ai-dlc-rules-v0.1.8\aidlc-rules\...` のようにバージョン番号のラッパーフォルダが作成されます。このフォルダを含めた正しいパスに置き換えて使用するか、直接 `aidlc-rules\` が展開先になるよう設定してください。

### 3. プラットフォーム別セットアップ

使用するツールのセクションに進んでください。

---

## 対応プラットフォーム

| プラットフォーム | 仕組み | インストールリンク |
|----------------|--------|-----------------|
| **Kiro** | Kiro Steering Files | [kiro.dev](https://kiro.dev/) |
| **Amazon Q Developer** | Amazon Q Rules | [インストール](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-in-IDE.html) |
| **Cursor IDE** | Cursor Rules | [cursor.com](https://cursor.com/) |
| **Cline** | Cline Rules | [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) |
| **Claude Code** | CLAUDE.md | [GitHub](https://github.com/anthropics/claude-code) |
| **GitHub Copilot** | copilot-instructions.md | [Marketplace](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) |
| **OpenAI Codex** | AGENTS.md | [developers.openai.com](https://developers.openai.com/) |

---

## Kiro（推奨：Kiro Steering Files）

**macOS/Linux：**

```bash
mkdir -p .kiro/steering
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rules .kiro/steering/
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details .kiro/
```

**Windows PowerShell：**

```powershell
New-Item -ItemType Directory -Force -Path ".kiro\steering"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules" ".kiro\steering\"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details" ".kiro\"
```

**ディレクトリ構造：**

```
<project-root>/
├── .kiro/
│   ├── steering/
│   │   └── aws-aidlc-rules/
│   └── aws-aidlc-rule-details/
```

**確認方法（Kiro IDE）：** Steering Files パネルで `core-workflow` が `Workspace` として表示されているか確認。

{: .note }
> Kiro IDE を Vibe モードで使用してください。Spec モードへの切り替えを促されたら `No` を選択して Vibe モードを維持します。

---

## Amazon Q Developer

**macOS/Linux：**

```bash
mkdir -p .amazonq/rules
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rules .amazonq/rules/
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details .amazonq/
```

**Windows PowerShell：**

```powershell
New-Item -ItemType Directory -Force -Path ".amazonq\rules"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules" ".amazonq\rules\"
Copy-Item -Recurse "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details" ".amazonq\"
```

**確認方法：** Amazon Q Chat ウィンドウの右下 `Rules` ボタンをクリックし、`.amazonq/rules/aws-aidlc-rules` が表示されているか確認。

---

## Cursor IDE

### オプション1：Project Rules（推奨）

**macOS/Linux：**

```bash
mkdir -p .cursor/rules

cat > .cursor/rules/ai-dlc-workflow.mdc << 'EOF'
---
description: "AI-DLC (AI-Driven Development Life Cycle) adaptive workflow for software development"
alwaysApply: true
---

EOF
cat ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md >> .cursor/rules/ai-dlc-workflow.mdc

mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Windows PowerShell：**

```powershell
New-Item -ItemType Directory -Force -Path ".cursor\rules"

$frontmatter = @"
---
description: "AI-DLC (AI-Driven Development Life Cycle) adaptive workflow for software development"
alwaysApply: true
---

"@
$frontmatter | Out-File -FilePath ".cursor\rules\ai-dlc-workflow.mdc" -Encoding utf8
Get-Content "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules\core-workflow.md" | Add-Content ".cursor\rules\ai-dlc-workflow.mdc"

New-Item -ItemType Directory -Force -Path ".aidlc-rule-details"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details\*" ".aidlc-rule-details\" -Recurse
```

**確認方法：** Cursor Settings → Rules, Commands → Project Rules に `ai-dlc-workflow` が表示されているか確認。

---

## Cline

**macOS/Linux：**

```bash
mkdir -p .clinerules
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md .clinerules/
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Windows PowerShell：**

```powershell
New-Item -ItemType Directory -Force -Path ".clinerules"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules\core-workflow.md" ".clinerules\"
New-Item -ItemType Directory -Force -Path ".aidlc-rule-details"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details\*" ".aidlc-rule-details\" -Recurse
```

**確認方法：** Cline のチャット入力フィールド下の Rules ポップオーバーで `core-workflow.md` が有効になっているか確認。

---

## Claude Code

### オプション1：プロジェクトルート配置（推奨）

**macOS/Linux：**

```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./CLAUDE.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Windows PowerShell：**

```powershell
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules\core-workflow.md" ".\CLAUDE.md"
New-Item -ItemType Directory -Force -Path ".aidlc-rule-details"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details\*" ".aidlc-rule-details\" -Recurse
```

**ディレクトリ構造：**

```
<project-root>/
├── CLAUDE.md
└── .aidlc-rule-details/
    ├── common/
    ├── inception/
    ├── construction/
    ├── extensions/
    └── operations/
```

**確認方法：** Claude Code で `/config` を実行し、現在のアクティブな指示を確認。

---

## GitHub Copilot

**macOS/Linux：**

```bash
mkdir -p .github
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md .github/copilot-instructions.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Windows PowerShell：**

```powershell
New-Item -ItemType Directory -Force -Path ".github"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules\core-workflow.md" ".github\copilot-instructions.md"
New-Item -ItemType Directory -Force -Path ".aidlc-rule-details"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details\*" ".aidlc-rule-details\" -Recurse
```

**確認方法：** VS Code の Copilot Chat パネル → Configure Chat（歯車アイコン）→ Chat Instructions で `copilot-instructions` が表示されているか確認。

---

## OpenAI Codex

**macOS/Linux：**

```bash
cp ~/Downloads/aidlc-rules/aws-aidlc-rules/core-workflow.md ./AGENTS.md
mkdir -p .aidlc-rule-details
cp -R ~/Downloads/aidlc-rules/aws-aidlc-rule-details/* .aidlc-rule-details/
```

**Windows PowerShell：**

```powershell
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rules\core-workflow.md" ".\AGENTS.md"
New-Item -ItemType Directory -Force -Path ".aidlc-rule-details"
Copy-Item "$env:USERPROFILE\Downloads\aidlc-rules\aws-aidlc-rule-details\*" ".aidlc-rule-details\" -Recurse
```

---

## AI支援セットアップ（実験的）

ファイルを手動でコピーする代わりに、AIエージェントにセットアップを任せることができます（Kiro、Claude Code、Cline などシェルアクセスがあるエージェント向け）。

チャットに以下のプロンプトを貼り付けてください：

```
Set up AI-DLC in this project by doing the following:

1. Download the latest AI-DLC release:
   - Use the GitHub API to find the latest release asset URL:
     curl -sL https://api.github.com/repos/awslabs/aidlc-workflows/releases/latest \
       | grep -o '"browser_download_url": *"[^"]*"' \
       | head -1 \
       | cut -d'"' -f4
   - Download the zip from that URL to /tmp/aidlc-rules.zip
   - Extract it: unzip -o /tmp/aidlc-rules.zip -d /tmp/aidlc-release
   - Copy the aidlc-rules/ folder from the extracted contents into .aidlc at the project root
   - Clean up: rm -rf /tmp/aidlc-rules.zip /tmp/aidlc-release

2. Create the appropriate rules/steering file for your IDE using the options below.
   [IDE名に応じてプラットフォームを選択: Kiro/Amazon Q/Cursor/Cline/Claude Code/GitHub Copilot]

3. The file content should be:
   When the user invokes AI-DLC, read and follow
   `.aidlc/aidlc-rules/aws-aidlc-rules/core-workflow.md` to start the workflow.

4. Add `.aidlc` to `.gitignore` unless I explicitly ask you not to.

5. Confirm what file you created and that `.aidlc` is gitignored.
```

---

## バージョン管理の推奨

**リポジトリにコミットすべきファイル：**

```gitignore
# バージョン管理対象
CLAUDE.md
AGENTS.md
.amazonq/rules/
.amazonq/aws-aidlc-rule-details/
.kiro/steering/
.kiro/aws-aidlc-rule-details/
.cursor/rules/
.clinerules/
.github/copilot-instructions.md
.aidlc-rule-details/
```

---

## トラブルシューティング

| 問題 | 解決方法 |
|------|---------|
| ルールが読み込まれない | ファイルがプラットフォームの正しい場所にあるか確認 |
| ファイルエンコーディングの問題 | ファイルが UTF-8 エンコードされているか確認 |
| セッション内でルールが適用されない | ファイル変更後に新しいチャットセッションを開始 |
| ルール詳細が読み込まれない | `.aidlc-rule-details/` とサブディレクトリが存在するか確認 |
| Windowsのパス問題 | Markdown ファイル内のパスにはバックスラッシュではなくスラッシュを使用 |
