# Scratch Pages

個人用の一時ページ置き場。思いつきで公開したいビジュアル・調べもの・旅行プランなどを、Vercel 上でさくっとホストするためのプロジェクト。

## 特徴

- **超軽量**: 純粋な HTML ファイルのみ。フレームワーク不要。
- **即デプロイ**: GitHub に push すれば Vercel が数十秒で自動公開。
- **クリーンURL**: `/msc-bellissima` のように `.html` なしでアクセス可能。
- **新ページ追加が簡単**: HTML ファイル 1 個と `index.html` への追記のみ。

## ディレクトリ構成

```
scratch-pages/
├── index.html              # ポータルページ（公開中ページ一覧）
├── msc-bellissima.html     # 公開ページ（例）
├── vercel.json             # Vercel 設定（cleanUrls など）
├── .gitignore
└── README.md
```

## はじめてのデプロイ手順

### 1. GitHub リポジトリを作成

```
Repository name: scratch-pages
Public / Private: お好みで
Initialize with: Add a README file（あとで上書き）
```

### 2. ローカルから push

```bash
cd scratch-pages
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/scratch-pages.git
git push -u origin main
```

### 3. Vercel に連携

1. https://vercel.com にログイン
2. **Add New Project** → GitHub の `scratch-pages` を選択
3. **Framework Preset**: `Other` を選択
4. **Build & Output Settings** はそのままで OK
5. **Deploy** をクリック

数十秒で `https://scratch-pages.vercel.app` が公開されます。

### 4. （任意）カスタムドメイン

Vercel の **Settings → Domains** から独自ドメインを設定可能。

## 新しいページを追加する

```bash
# 1. HTML ファイルを作成
echo '<h1>新しいページ</h1>' > newpage.html

# 2. index.html の #pagesGrid 内にカードを追加
# 例：
# <a class="page-card" href="/newpage">
#   <span class="emoji">✨</span>
#   <h3>新しいページ</h3>
#   <p class="desc">説明</p>
#   <div class="meta"><span>日付</span><span class="arrow">→</span></div>
# </a>

# 3. push
git add . && git commit -m "Add newpage" && git push
```

Vercel が自動デプロイし、`https://scratch-pages.vercel.app/newpage` で公開されます。

## Vercel CLI を使う場合

```bash
npm i -g vercel
cd scratch-pages
vercel              # プレビューデプロイ
vercel --prod       # 本番デプロイ
```

## 公開ページ

| URL | ページ | 公開日 |
|---|---|---|
| `/` | ポータル（このページ一覧） | 2026.06.22 |
| `/msc-bellissima` | MSCベリッシマ 沖縄クルーズ徹底比較（11名・3部屋グループ特化） | 2026.06.22 |

## 更新履歴

- 2026.06.22 - msc-bellissima ページ公開＆リサーチ結果反映（旅行代理店ランキング・予算シミュレーション追加）

## カスタマイズ

- **配色変更**: `index.html` の `:root` セクション（`--coral`, `--ink` など）を編集
- **ロゴ変更**: `index.html` の `.nav-brand-logo` 内の SVG を差し替え
- **統計の自動カウント**: `index.html` の JavaScript が `.page-card` 要素を自動カウント

## 注意事項

- 個人情報・機密情報は載せない（Public で公開される前提）
- 商用利用はしない（個人用サンドボックス）
- 大きなファイル（画像・動画など）はVercelのデプロイサイズ制限に注意
