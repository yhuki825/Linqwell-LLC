# Linqwell LLC - Corporate Website

合同会社Linqwellの企業ウェブサイトです。医療機器のグローバルな流通と、バングラデシュ・ネパールの方々の日本での生活・ビジネスをトータルにサポートするサービスを紹介しています。

## 📋 ファイル構成

```
linqwell-standalone/
├── index.html              # メインHTMLファイル（すべてのコンテンツを含む）
├── assets/
│   ├── index-{hash}.css   # スタイルシート
│   └── index-{hash}.js    # JavaScriptバンドル
├── __manus__/             # デバッグ用ファイル（削除可能）
└── README.md              # このファイル
```

## 🚀 Cloudflare Pagesへのデプロイ方法

### 方法1: GitHub連携（推奨）

1. このファイルをGitHubリポジトリにプッシュ
2. Cloudflare Dashboardにアクセス
3. **Pages** → **Create a project** → **Connect to Git**
4. リポジトリを選択
5. ビルド設定：
   - **Framework preset**: None
   - **Build command**: （空のままで可）
   - **Build output directory**: `linqwell-standalone`
6. **Save and Deploy**をクリック

### 方法2: ドラッグ&ドロップ

1. Cloudflare Dashboardの **Pages** セクションにアクセス
2. **Create a project** → **Direct upload**
3. `linqwell-standalone` フォルダ内のすべてのファイルをアップロード
4. デプロイ完了

### 方法3: Wrangler CLI

```bash
# Wranglerのインストール
npm install -g @cloudflare/wrangler

# ログイン
wrangler login

# デプロイ
wrangler pages deploy linqwell-standalone/
```

## 📝 カスタマイズ方法

HTMLファイルを直接編集することで、以下の内容をカスタマイズできます：

- **会社情報**: 住所、電話番号、メールアドレスなど
- **テキスト内容**: 事業説明、メッセージなど
- **色やスタイル**: `assets/index-{hash}.css`を編集

## 🔧 技術仕様

- **フレームワーク**: React 19 + Tailwind CSS 4
- **バンドラー**: Vite
- **対応ブラウザ**: 最新のモダンブラウザ（Chrome, Firefox, Safari, Edge）
- **レスポンシブ**: モバイル・タブレット・デスクトップ対応

## 📱 機能

- ✅ レスポンシブデザイン
- ✅ スムーズスクロール
- ✅ モバイルメニュー
- ✅ SEO最適化（メタタグ、構造化データ）
- ✅ アクセシビリティ対応

## 🌐 ドメイン設定

Cloudflare Pagesでのデプロイ後、カスタムドメインを設定できます：

1. Cloudflare Dashboard → Pages → プロジェクト
2. **Custom domains** → **Set up a custom domain**
3. ドメインを入力して設定完了

## 📞 サポート

問題が発生した場合は、以下を確認してください：

1. すべてのファイルが正しくアップロードされているか
2. `index.html`が正しく配置されているか
3. ブラウザのコンソールでエラーがないか

## 📄 ライセンス

© 2025-2026 Linqwell LLC. All rights reserved.
