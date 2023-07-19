# 4d-tips-docusaurus-prince-pdf
docusaurus-prince-pdfを使用してPDFを作成するには

### [Prince](https://www.princexml.com/download/)をインストールする

**参考**: https://github.com/signcl/docusaurus-prince-pdf

#### 気を付けること

* `./pdf/`以降のフォルダーをあらかじめ作成しておく必要がある。

**例**:

* v20 LTS

```sh
cd ~/Desktop/
mkdir -p pdf/developer.4d.com-docs-20/ja/GettingStarted
npx docusaurus-prince-pdf --url https://developer.4d.com/docs/ja/20/GettingStarted/installation --selector '.pagination-nav__link--next' --output doc.pdf
```

* v19 LTS

```sh
cd ~/Desktop/
mkdir -p pdf/developer.4d.com-docs-19/ja/GettingStarted
npx docusaurus-prince-pdf --url https://developer.4d.com/docs/19/ja/GettingStarted/installation.html --selector 'div.docs-prevnext > a.docs-next' --output doc.pdf
```
* Rx

```sh
cd ~/Desktop/
mkdir -p pdf/developer.4d.com-docs-Rx/ja/GettingStarted
npx docusaurus-prince-pdf --url https://developer.4d.com/docs/Rx/ja/GettingStarted/installation.html --selector 'div.docs-prevnext > a.docs-next' --output doc.pdf
```

* Go Mobile

```sh
cd ~/Desktop/
mkdir -p pdf/developer.4d.com-go-mobile-ja/docs/getting-started
npx docusaurus-prince-pdf --url https://developer.4d.com/go-mobile/ja/docs/getting-started/introduction --selector ".pagination-nav__link--next" --output doc.pdf
```

**裏技**

```
./pdf/dev.openbayes.com.txt
```

にURLを列挙したテキストファイルを置いて

```sh
npx docusaurus-prince-pdf --pdf-only 
```

とすればそのままPDFが作成できる（開発者のハードコーディング）

* 非商用ライセンス
* 出力したPDFの表紙にはPrinceの透かしロゴマークが挿入される
* サイトやメールに[www.princexml.com](https://www.princexml.com/)のクレジットを掲載する

**参考**: https://www.princexml.com/purchase/license_faq/

* HTMLが崩れているために途中でドキュメントが終わってしまう場合，[ページリスト](/dev.openbayes.com.txt)を用意しておき`--pdf-only`モードで出力する

* デフォルトの設定では余計な要素が出力されるので

```
~/.npm/_npx/{identifier}/node_modules/docusaurus-prince-pdf/print.css
```

のスタイルシートを編集する

```css

  .navPusher {
    padding-top: 0px !important;
  }

  .mainContainer{
    padding: 50px 0 0 0 !important;
  }
  
  .fixedHeaderContainer {
    /* 上部の青いバナーも消すには display: none; */
  }    


  .slidingNav,
  .button,
  .nav-footer,
  .navBreadcrumb {
    display: none !important;
  }

  input {
    display: none !important;
  }

  ul.nav-site > li {
    display: none !important;
  }

  p, li, th, tr, td, h1, h2, h3, h4, h5, h6 {
    font-family: "Meiryo UI" !important;
  }
```
