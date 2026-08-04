# culu hair 公式ランディングページ

三重県伊勢市のシェアサロン「culu hair（culu share salon）」の入り口ページです。
Googleビジネスプロフィールからの訪問者が、

- 担当スタイリスト（yusaku / mayu）への予約
- シェアサロン利用希望の美容師の方への案内

のどちらかを迷わず選べることを目的にした、シンプルな1枚のページです。
将来的に店舗紹介・アクセス・メニュー・ギャラリー・ブログなどを追加できるよう、
セクション単位で拡張しやすい構造にしています。

---

## 1. ページ概要

| ファイル | 役割 |
|---|---|
| `index.html` | ページ本体（構成・文言・リンク） |
| `css/style.css` | デザイン（配色・フォント・レイアウト） |
| `images/` | 写真・ロゴなどの画像置き場 |

JavaScriptは使用していません（画像が無い場合に非表示にする1行の処理のみHTML内にあります）。

---

## 2. ローカルで確認する方法

ビルド不要です。`index.html` をブラウザにドラッグ＆ドロップするか、
Finderでダブルクリックするだけで表示できます。

VS Codeを使っている場合は「Live Server」拡張機能で開くと、
ファイル保存時に自動リロードされて便利です。

---

## 3. Instagramリンクの変更方法

`index.html` 内を「instagram」で検索すると、以下のような箇所が2つ見つかります（yusaku用・mayu用）。

```html
<a class="btn btn--primary" href="https://www.instagram.com/" target="_blank" rel="noopener">
  Instagram・ご予約はこちら
</a>
```

`href="https://www.instagram.com/"` の部分を、それぞれの実際のInstagramプロフィールURLに書き換えてください。

---

## 4. 美容師募集LPリンクの変更方法

`index.html` 内の「シェアサロンについて詳しく見る」ボタン付近にある以下の箇所を編集します。

```html
<a class="btn btn--outline" href="#" target="_blank" rel="noopener">
  シェアサロンについて詳しく見る
</a>
```

`href="#"` を、既存の美容師募集LPのURLに書き換えてください。

---

## 5. 画像の追加方法

以下のファイル名で `images/` フォルダに配置すると、そのまま反映されます。
ファイルが無い場合は、上品なイニシャル入りの丸型プレースホルダーが自動的に表示されるため、
写真が揃っていない状態でもデザインが崩れません。

| 用途 | 保存場所・ファイル名 | 推奨サイズ / 比率 |
|---|---|---|
| yusaku プロフィール写真 | `images/stylists/yusaku.jpg` | 正方形推奨（例: 600×600px） |
| mayu プロフィール写真 | `images/stylists/mayu.jpg` | 正方形推奨（例: 600×600px） |
| ヒーロー画像（店内写真） | `images/salon-interior.jpg` | 横長（例: 1600×900px以上、16:9〜1.9:1程度） |
| OGP画像（SNSシェア時のサムネイル） | `images/ogp.jpg` | 1200×630px |
| ロゴ | `images/logo.png` または `.svg` | 現状は文字ロゴのため任意。差し替えたい場合は下記「発展させる場合」を参照 |

写真は容量を軽くしてから配置してください（1枚あたり目安300KB以下）。
表示速度を保つため、スマホでの撮影サイズをそのままアップロードしないようご注意ください。

`salon-interior.jpg` はヘッダー直下のヒーロー画像です。**「culu hair」のロゴや説明文はHTMLの文字ではなく、
この画像ファイル自体に焼き込まれています**（デザインツールで作成した完成画像をそのまま横幅いっぱいに
表示する仕様）。トリミングは行わず、画像の縦横比のまま表示されます。

そのため、ヒーロー内の文言やレイアウトを変更したい場合は、`index.html` を編集するのではなく、
**画像を作成したデザインツール側で文字を編集し、書き出し直したものを `salon-interior.jpg` として
上書き保存してください。** ファイル名を変えずに同じ場所へ上書きすれば、そのまま反映されます。

---

## 6. スタイリストの追加方法

`index.html` 内の `<!-- STYLIST CARD: mayu ここから -->` 〜 `<!-- STYLIST CARD: mayu ここまで -->` の
1ブロックをまるごとコピーし、以下を書き換えて `</section>`（`<!-- 新しいスタイリストを追加する場合は...-->` のコメントの上）に貼り付けてください。

1. `stylist-card__photo--mayu` のクラス名を新しい名前に変更（任意の英字、例: `stylist-card__photo--kaho`）
2. `<span class="stylist-card__initial">M</span>` のイニシャルを変更
3. `src="images/stylists/mayu.jpg"` の画像パスを新しいファイル名に変更
4. `浜口まゆ` を本名に変更
5. `mayu` をローマ字表示名に変更
6. `href="https://www.instagram.com/"` を本人のURLに変更

`css/style.css` は変更不要です（丸型・レイアウトは自動で揃います）。

---

## 7. GitHubへのアップロード方法

1. GitHubで新しいリポジトリを作成する（例: `culu-hair`）
2. ターミナルでこのフォルダに移動し、以下を実行

```bash
git init
git add .
git commit -m "Initial commit: culu hair LP"
git branch -M main
git remote add origin https://github.com/【あなたのユーザー名】/culu-hair.git
git push -u origin main
```

---

## 8. GitHub Pagesで公開する方法

1. GitHubのリポジトリページで「Settings」を開く
2. 左メニューの「Pages」を選択
3. 「Build and deployment」の「Source」を `Deploy from a branch` に設定
4. 「Branch」を `main` / `/(root)` にして「Save」
5. 数分後、`https://【あなたのユーザー名】.github.io/culu-hair/` で公開される

公開後は、`index.html` 内の `og:url` を実際のURLに書き換えてください。

```html
<meta property="og:url" content="https://example.com/">
```

---

## 9. 発展させる場合（将来の拡張について）

現状は「お客様の予約導線」と「美容師募集の入口」に絞ったシンプルな1ページですが、
`index.html` の `<main>` 内、末尾のコメント

```html
<!-- 今後追加予定のセクション（今回は未実装）
     店舗紹介 / アクセス / メニュー / スタイルギャラリー / ブログ / Google口コミ / 会社紹介
     追加する際は、このコメントの位置に <section> を新設してください -->
```

の位置に、新しい `<section>` を追加していくことで自然に拡張できます。
配色・余白・フォントはすべて `css/style.css` の `:root` 内のCSS変数（`--color-*` / `--space-*`）に
まとまっているため、新しいセクションもこの変数を使えばデザインが統一されます。

文字ロゴ（`culu hair`）を画像ロゴに差し替える場合は、`.site-header__logo` を
`<img src="images/logo.svg" alt="culu hair">` に置き換えてください。
