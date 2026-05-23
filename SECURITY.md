# SECURITY.md
# セキュリティルール（サンプル版）

---

## 最重要ルール

```
AIに渡した情報は公開されうる前提で扱う。
secretsは絶対にAIに渡さない。
```

## secrets管理

```
✅ 使う：1Password / GitHub Secrets / Vercel Env Vars
❌ 禁止：.envをcommit / frontendにAPIキーを書く / AIチャットにキーを貼る
```

## .gitignore 必須項目

```gitignore
.env
.env.local
.env.*.local
*.key
*.pem
secrets/
```

## ブラウザ分離

```
普段ブラウザ  → 一般用途
AIブラウザ   → AIツール専用

AIブラウザで禁止：AWS root / GitHub admin / 銀行
```

## 従量課金防御

```
✅ 必ずhard limitを設定する
✅ budget alertを設定する
原則：無制限従量課金は事故前提
```

---

> ⚡ 完全版（Prompt Injection対策・インシデント対応手順・依存関係レビュー）  
> 👉 [AI Operations Starter Kit](https://sbtrlabs.gumroad.com)
