# Cloudflare Pages デプロイメントガイド

このガイドでは、Linqwell LLCのウェブサイトをCloudflare Pagesにデプロイする手順を詳しく説明します。

## 前提条件

- Cloudflareアカウント（無料で作成可能）
- GitHubアカウント（GitHub連携の場合）

## ステップバイステップガイド

### ステップ1: Cloudflareアカウントにログイン

1. [Cloudflare Dashboard](https://dash.cloudflare.com/)にアクセス
2. メールアドレスとパスワードでログイン

### ステップ2: Pagesプロジェクトを作成

1. 左側メニューから **Pages** を選択
2. **Create a project** をクリック

### ステップ3: デプロイ方法を選択

#### オプションA: GitHub連携（推奨・自動更新対応）

1. **Connect to Git** を選択
2. GitHubアカウントを認証
3. Linqwellのリポジトリを選択
4. **Begin setup** をクリック

**ビルド設定:**
- **Framework preset**: None
- **Build command**: （空のままで可）
- **Build output directory**: `linqwell-standalone`

5. **Save and Deploy** をクリック
6. デプロイ完了を待つ（通常1-2分）

#### オプションB: 直接アップロード（最も簡単）

1. **Direct upload** を選択
2. `linqwell-standalone` フォルダ内の全ファイルをドラッグ&ドロップ
3. アップロード完了を待つ

#### オプションC: Wrangler CLI（開発者向け）

```bash
# 1. Wranglerをインストール
npm install -g @cloudflare/wrangler

# 2. Cloudflareにログイン
wrangler login

# 3. デプロイ
wrangler pages deploy linqwell-standalone/
```

### ステップ4: カスタムドメイン設定

1. Cloudflare Dashboard → Pages → プロジェクト
2. **Settings** → **Custom domains**
3. **Add custom domain** をクリック
4. ドメイン名を入力（例：linqwell.com）
5. DNSレコードを設定

**DNS設定例:**
```
Type: CNAME
Name: www
Content: {your-project}.pages.dev
```

### ステップ5: SSL/TLS設定（自動）

Cloudflare Pagesは自動的にSSL/TLSを設定します。
- すべてのトラフィックはHTTPSにリダイレクト
- 証明書は自動更新

## トラブルシューティング

### デプロイが失敗する場合

1. **ファイル構成を確認**
   - `index.html`がルートにあるか
   - `assets/`フォルダが存在するか

2. **ビルド出力ディレクトリを確認**
   - GitHub連携の場合、`linqwell-standalone`に設定

3. **ファイルサイズを確認**
   - Cloudflare Pagesの制限：1ファイルあたり25MB以下

### ページが表示されない場合

1. ブラウザのキャッシュをクリア（Ctrl+Shift+Delete）
2. 別のブラウザで試す
3. Cloudflare Dashboard → Pages → プロジェクト → **Deployments** でログを確認

### パフォーマンス最適化

1. **キャッシュ設定**
   - Cloudflare → Caching → Cache Rules
   - 静的ファイル（CSS、JS）は長期キャッシュ

2. **圧縮設定**
   - Cloudflare → Speed → Optimization
   - Brotli圧縮を有効化

## 更新手順

### GitHub連携の場合

1. ローカルで変更を加える
2. GitHubにプッシュ
3. Cloudflareが自動的にデプロイ

### 直接アップロードの場合

1. ファイルを更新
2. Cloudflare Dashboard → Pages → **Re-deploy**
3. 最新版をアップロード

## セキュリティ設定

### 推奨設定

1. **DDoS保護**: 自動有効
2. **WAF（Web Application Firewall）**: 無料プランで利用可能
3. **レート制限**: 必要に応じて設定

### 設定方法

1. Cloudflare Dashboard → Security
2. 各設定を確認・調整

## 監視とログ

### アクセスログの確認

1. Pages → プロジェクト → **Deployments**
2. 各デプロイのステータスを確認

### パフォーマンス分析

1. Pages → プロジェクト → **Analytics**
2. アクセス数、キャッシュヒット率などを確認

## よくある質問

**Q: 無料プランでも使用できますか？**
A: はい。Cloudflare Pagesは無料で使用できます。

**Q: 独自ドメインは必須ですか？**
A: いいえ。`{project-name}.pages.dev`で自動的にアクセス可能です。

**Q: デプロイ後、すぐに反映されますか？**
A: 通常1-2分で反映されます。キャッシュの場合は最大24時間かかる場合があります。

**Q: HTTPSは対応していますか？**
A: はい。すべてのサイトが自動的にHTTPSで保護されます。

## サポート

問題が発生した場合：

1. [Cloudflare Community](https://community.cloudflare.com/)で質問
2. [Cloudflare Status](https://www.cloudflarestatus.com/)でシステムステータスを確認
3. Cloudflare Support（有料プランの場合）

---

**最終更新**: 2026年3月11日
