# AGENTS.md
# AI役割分離テンプレート（サンプル版）

---

## 基本原則

```
AIには最小権限のみ付与する。
環境は必ず分離する：dev / staging / production
```

## エージェント別担当

| エージェント | 担当 | 禁止 |
|---|---|---|
| Claude | 設計・レビュー・PRD | 本番変更・auth・billing |
| ChatGPT | 壁打ち・調査・改善 | 本番変更・secrets受け取り |
| Codex / Copilot | 実装・テスト・修正 | production変更・sudo・rm -rf |

## 環境分離ルール

```
dev環境     → AIに開放可
staging環境  → 読み取りのみ
production   → AI完全禁止（人間のみ）
```

## AI禁止領域（人間専用）

```
❌ billing / DNS / IAM / auth
❌ legal / tax / refund
❌ production DB
```

---

> ⚡ 完全版（詳細な権限設計・エスカレーションルール・連携フロー）  
> 👉 [AI Operations Starter Kit](https://sbtrlabs.gumroad.com)
