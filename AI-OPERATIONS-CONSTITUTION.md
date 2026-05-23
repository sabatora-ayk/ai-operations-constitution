# AI時代の個人開発・小規模ソフトウェア運用憲法

> Version 1.0  
> License: Personal Use / Single Developer License

---

## 0. この文書の目的

この文書は **AIを安全に運用するための実運用憲法** である。

目的は「AIで楽をすること」ではない。  
本当の目的は **「AIを使っても壊れない仕組みを作ること」**

---

## 1. 最重要思想

### AIを神格化しない

AIは「優秀だが暴走しうるインターン」であり、責任者ではない。

```
AI  = acceleration（提案・補助・加速）
Human = accountability（責任・承認・決裁）
```

### Browser = 敵地

ブラウザへ送った情報は **公開されうる** 前提で扱う。

### 復旧可能性を最優先

重要なのは「壊れないこと」ではなく、**「壊れても戻せること」**

### 最重要指標

- 安い
- 安全
- 速い
- 量産可能
- 復旧可能
- 維持可能

---

## 2. 基本構成

| ツール | 役割 |
|---|---|
| Claude | 設計・レビュー・PRD |
| ChatGPT | 壁打ち・改善・調査 |
| GPT-5/Codex | 実装・修正・テスト |
| Docker | 隔離環境 |
| GitHub Actions | CI/CD |
| Vercel | Deploy |
| Supabase/Cloudflare | 最小Backend |

---

## 3. AI役割分離

### Claude
**担当：** 要件整理 / 設計 / UI・UX / セキュリティ観点 / レビュー  
**禁止：** 本番変更 / auth変更 / billing変更

### GPT-5/Codex
**担当：** 実装 / test / lint / 型修正 / CI修正  
**禁止：** production変更 / secrets閲覧 / sudo / rm -rf

---

## 4. AI禁止領域

以下は **人間専用領域**：

- billing
- DNS
- IAM
- auth
- legal
- tax / accounting
- refund
- production DB

---

## 5. 権限分離

AIへは **最小権限のみ** 付与。

必須分離：
- dev
- staging
- production

---

## 6. 本番DB原則

**禁止：** AIが本番DBへ直接接続

**推奨：**
- staging DB
- anonymized dump
- mock data

---

## 7. 秘密情報管理

**使用：**
- 1Password
- GitHub Secrets
- Vercel Environment Variables

**禁止：**
- frontend secrets
- .env commit
- AIへの実キー共有

---

## 8. Browser分離

必須：「普段ブラウザ」と「AIブラウザ」を分離。

AIブラウザで禁止：
- AWS root
- Google Ads
- GitHub admin
- 銀行

---

## 9. 従量課金防御

必須：
- hard limit
- usage alert
- budget alert
- timeout
- rate limit
- concurrency limit

> **原則：無制限従量課金は事故前提**

---

## 10. AIコード運用

**禁止：** AIコードを直接mainへmerge

**必須フロー：**
```
AI → PR → CI → Human Review → merge
```

**必須CI：** lint / typecheck / test

> **原則：「動いた」ではなく「壊れてない」を確認する**

---

## 11. Dependency運用

AIは謎ライブラリを入れがち。

確認事項：
- maintainer
- license
- weekly downloads
- issue状況

> **原則：npm install は無料ガチャではない**

---

## 12. Prompt Injection対策

AIは README / Issue / Docs / PR から汚染される。

**禁止：** 書かれているから信用

---

## 13. Rollback / Backup

必須：
- DB backup
- deploy rollback
- config export
- version pinning

> **原則：壊れることより戻せないことが致命傷**

---

## 14. Feature Flags

推奨：
- 段階公開
- 一部ユーザーのみ
- 即OFF可能

---

## 15. Observability

最低限：
- error tracking
- request logging
- token usage
- latency monitor
- cost monitor

> **原則：LLMは静かに劣化する**

---

## 16. Context Window設計

AIは長文ほど壊れる。

必須：
- task分割
- scope限定
- context圧縮
- 要約

> **原則：巨大promptより責務分離**

---

## 17. モデル依存を薄くする

前提：値上げ / API終了 / rate limit は普通に起こる。

推奨構成：
```
AI Gateway
 ├ OpenAI
 ├ Anthropic
 └ Gemini
```

---

## 18. Eval基盤

最低限：
- regression test
- prompt eval
- hallucination test
- golden dataset

> **原則：AI品質は自然劣化する**

---

## 19. Data Governance

最低限：
- PII管理
- retention policy
- データ分類
- 学習利用可否

> **原則：データ流出はコードバグより重い**

---

## 20. Human Escalation

AIが判断不能時は **必ず人間へ戻す**。

対象：法務 / 医療 / 金融 / 高額決済 / account停止

---

## 21. AI Cost Architecture

> **重要：賢い設計より安く維持できる設計**

推奨：
- cache first
- small model first
- routing
- batching
- async

---

## 22. AIを同期前提にしない

LLMは遅い。

推奨：
- queue
- async jobs
- background processing
- webhook

> **原則：全部チャットUI化しない**

---

## 23. AI機能は optional にする

```
Core Product
 └ optional AI layer
```

> **原則：AI障害で全機能停止しない**

---

## 24. AI出力を信用しない

AI出力は「下書き・仮説・叩き台」として扱う。

特に危険：
- SQL
- migration
- regex
- pricing
- security
- legal

---

## 25. ADR（Architecture Decision Record）

必須推奨：`docs/adr/`

保存するもの：
- なぜ採用したか
- なぜ却下したか
- tradeoff
- コスト
- リスク

> **原則：AI時代は「決定理由」が資産**

---

## 26. Prompt Versioning

Promptは **コード** として扱う。

必須：
- Git管理
- versioning
- rollback
- eval

---

## 27. Vendor Lock-in対策

危険：OpenAI依存100% / Anthropic依存100%

推奨：Provider abstraction

---

## 28. MVP原則

最優先：**小さい成功体験**

禁止：最初から巨大AI基盤

---

## 29. 個人開発の現実

重要なのは：
- 継続性
- 保守性
- コスト管理
- 小さいリリース

> **最強なのは半年後も直せる構成**

---

## 30. ライセンス確認

AI生成コードでも license確認 は必要。

最低限：
- dependency license
- generated code review
- copy source確認

---

## 31. 自動化

推奨：GitHub Actions

用途：
- test
- lint
- build
- deploy
- AI review

---

## 32. 推奨repo構成

```
/AI-OPERATIONS-CONSTITUTION
README.md
CLAUDE.md
AGENTS.md
SECURITY.md
OPERATIONS.md
/docs
/docs/adr
/prompts
```

---

## 最終原則

> 便利さより安全。  
> 自動化より可視化。  
> 速度より復旧可能性。

**AIを信用しすぎない人が最後に残る**
