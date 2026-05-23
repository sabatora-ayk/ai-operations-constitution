# AI Operations Constitution
### For Solo Developers & Small Teams

![Version](https://img.shields.io/badge/version-1.0-7c3aed)
![License](https://img.shields.io/badge/license-MIT-blue)

**AI時代の個人開発・小規模チーム向け 実運用憲法**

> AI = acceleration（提案・補助・加速）  
> Human = accountability（責任・承認・決裁）

---

## このリポジトリについて

AIツール（Claude、ChatGPT、Codexなど）を使う開発で  
「どこまで任せていいか」「本番を守るには」を整理した実運用テンプレートです。

---

## ファイル構成

```
/
├── AI-OPERATIONS-CONSTITUTION.md   ← 憲法本文（無料・全文公開）
├── CLAUDE.md                       ← Claudeの役割定義（サンプル）
├── AGENTS.md                       ← AI役割分離テンプレート（サンプル）
├── SECURITY.md                     ← セキュリティルール（サンプル）
├── OPERATIONS.md                   ← 開発フロー（サンプル）
└── prompts/
    └── implement-sample.md         ← 実装プロンプトサンプル
```

---

## クイックスタート

以下の4ファイルをプロジェクトのルートにコピーして使えます：

```bash
CLAUDE.md
AGENTS.md
SECURITY.md
OPERATIONS.md
```

`CLAUDE.md` は Claude Code が自動読み込みします。

---

## 最重要原則

```
1. AIを神格化しない
   → AIは「優秀だが暴走しうるインターン」

2. 復旧可能性を最優先
   → 壊れないことより、壊れても戻せること

3. AIに触らせない領域を決める
   → billing / auth / 本番DB / DNS / 法務
```

---

## 完全版（Starter Kit）

このリポジトリは憲法本文＋サンプルファイルの無料版です。

すぐに使えるフルセット（全9ファイル）はこちら：

🔗 **[AI Operations Starter Kit — Gumroad](https://sbtrlabs.gumroad.com)**

**含まれるもの（有料版）:**
- 全テンプレートファイル（編集済み・すぐ使える）
- 実装 / レビュー / バグ修正 プロンプトテンプレート3種
- PDF版（印刷・共有用）
- 日本語版・英語版セット
- 永久アップデート無料

---

## ライセンス

MIT License — 個人・商用利用可

---

## 作者

**SBTR AI Lab**  
X: [@sabatora_](https://x.com/sabatora_)  
Gumroad: [sbtrlabs.gumroad.com](https://sbtrlabs.gumroad.com)
