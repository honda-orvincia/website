# orvincia.com 運用規約(honda-orvincia/website)

株式会社ORVINCIAコーポレートサイト。GitHub Pagesで https://orvincia.com/ に公開(mainへのpushで自動デプロイ、反映まで1〜2分)。

## 構成

```
index.html            トップ(会社概要・代表・問い合わせフォーム)
fc-package/           FC本部構築パッケージLP
fc-support/           FC本部運営支援LP
guide/                SEO記事セクション(一覧+記事)
guide/guide.css       ガイド共通CSS(本体のデザイントークンに準拠)
_templates/article.html  記事テンプレート
sitemap.xml           サイトマップ(手動管理)
google0d6eb41e0796d6d4.html  Search Console確認ファイル — 絶対に削除しない
CNAME                 orvincia.com — 削除しない
```

- SEO戦略の全体像: `~/Desktop/orvincia-fc-service/docs/seo-organic-strategy_20260805.md`
- 事業前提・表現制約の詳細: `~/Desktop/orvincia-fc-service/CLAUDE.md`

## 記事公開の手順(この順番で必ず全部やる)

1. `_templates/article.html` をコピーして `guide/<slug>/index.html` を作成し、プレースホルダを置換
2. 本文を書く。**必ず `.field-note`(現場からのメモ=本多さんの一次情報)を1つ以上入れる**。一次情報ブロックは本多さんの実体験の提供を受けてから書く — 創作は禁止
3. FAQを含む記事はFAQPage構造化データを追加
4. `guide/index.html` の `ARTICLE_LIST:START〜END` に記事カードを追加(新しい記事が上)。**初回記事の公開時のみ**: 同ファイルの `<meta name="robots" content="noindex">` を削除し、guide一覧をsitemap.xmlに追加し、トップ(index.html)のnav-linksに `<a href="/guide/">FC本部構築ガイド</a>` を追加する
5. 公開済み記事の `RELATED:START〜END` に相互リンクを設定(関連2〜3本)
6. `sitemap.xml` に記事URLを追加(`<lastmod>` は公開日)
7. commit(日本語1行でOK)→ push → 1〜2分待って本番URLをcurlで200確認
8. Search ConsoleのURL検査でインデックス登録をリクエスト(ブラウザ操作)

## 表現の制約(違反したら公開前に直す)

- ❌「現役で自分のFC本部を運営」「直営店を自分で回している」— 事実でない。本人が運営するのは**店舗**(店舗オーナーとして)。FC本部の現場は**支援先**での実働
- 支援先の名称は出さない。業種表現のみ(例: リラクゼーション業態の多店舗チェーン)
- 景表法: No.1表記・「必ず儲かる」等の断定・根拠のない実績数字は禁止。数字は事実のみ
- 記事はですます調。煽りタイトル(「〜はやめろ」等)は使わない。誠実さがブランド

## デザイン

- 色: ネイビー #023a91 / ゴールド #cb9a08 / アイボリー #fcfaf2。見出しはNoto Serif JP
- ガイド配下は `/guide/guide.css` を使う。記事ごとのインラインCSSは書かない
