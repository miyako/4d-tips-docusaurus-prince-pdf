# 4d-tips-docusaurus-prince-pdf
docusaurus-prince-pdfを使用してPDFを作成するには

### [Prince](https://www.princexml.com/download/)をインストールする

**参考**: https://github.com/signcl/docusaurus-prince-pdf

#### 気を付けること

* `./pdf/`以降のフォルダーをあらかじめ作成しておく必要がある。

**例**:

```sh
cd ~/Desktop/
mkdir -p pdf/developer.4d.com-docs-ja/Concepts
npx docusaurus-prince-pdf --url https://developer.4d.com/docs/ja/Concepts/error-handling.html --selector 'div.docs-prevnext > a.docs-next' --output doc.pdf
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

* HTMLが崩れているために途中でドキュメントが終わってしまう（Princeは「次ページ」ボタンを検索する仕組み）

[https://developer.4d.com/docs/ja/Tags/tags.html](https://developer.4d.com/docs/ja/Tags/tags.html)

回避するためには[ページリスト](/dev.openbayes.com.txt)を用意しておき`--pdf-only`モードで出力する
