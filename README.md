# 4d-tips-docusaurus-prince-pdf
docusaurus-prince-pdfを使用してPDFを作成するには

### [Prince](https://www.princexml.com/download/)をインストールする

**参考**: https://github.com/signcl/docusaurus-prince-pdf

#### 気を付けること

* `./pdf/`以降のフォルダーをあらかじめ作成しておく必要がある。

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

