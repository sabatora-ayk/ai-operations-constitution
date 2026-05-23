# OPERATIONS.md
# 開発フロー（サンプル版）

---

## 基本フロー

```
AI（コード生成）
    ↓
PR作成（feature branch）
    ↓
CI自動チェック（lint / typecheck / test）
    ↓
Human Review（必須）
    ↓
merge → staging → 本番
```

> 原則：「動いた」ではなく「壊れてない」を確認する

## ブランチルール

```
main      → 本番（直接pushは禁止）
feature/* → AIはここで作業
```

## CI必須チェック

```yaml
- lint
- typecheck  
- test
- build
```

## Rollback

```
問題発生時：
1. Vercelダッシュボードから即ロールバック
2. git revert → PR → 通常フローでmerge
```

> 原則：壊れることより戻せないことが致命傷

---

> ⚡ 完全版（GitHub Actions設定・バックアップ方針・監視設定・Feature Flags）  
> 👉 [AI Operations Starter Kit](https://sbtrlabs.gumroad.com)
