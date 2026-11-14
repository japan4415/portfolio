# Portfolio

加藤慶彦（Yoshihiko Kato）のポートフォリオサイトです。Astro + Tailwind CSS v4 の静的サイトを Cloudflare Workers で配信しています。

## 開発

- Node.js 20 以上
- `npm ci`
- `npm run dev` — 開発サーバー（既定は http://localhost:4321）
- `npm run build` — `dist/` に静的ファイルを生成
- `npm run preview` — ビルド結果をローカルで確認

## 画像

- 元画像は `src/assets/images/` に置きます。
- `astro:assets` の `<Picture>` が AVIF / WebP / JPEG（透過画像は PNG）と複数幅を生成し、`srcset` / `sizes` / `width` / `height` を出力します。
- `public/` に置いた画像は最適化されず、そのまま配信されます。

## デプロイ

- `wrangler.jsonc` の `portfolio` Worker が `dist/` を配信します。
- `npx wrangler deploy`、または GitHub と連携した Cloudflare Workers Builds でデプロイします。
- `public/_headers` でキャッシュとセキュリティヘッダーを設定しています。
- `public/robots.txt` と `public/sitemap.xml` は静的ファイルです。

## ブラウザ対応

Popover API、`:popover-open`、`fetchpriority`、AVIF / WebP を利用しています。Popover API 非対応のブラウザでは、JavaScript の簡易フォールバックでメニューを開閉します。
