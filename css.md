# CSSコーディングスタイルガイド

## 基本方針

1. HTMLとCSSを極力書かない
2. 増やすより減らす
3. メンテナブルなコードを書く

## ガイド

### クラスの命名規則

* クラスの命名規則はBEMを用いる
* materializeのクラス名に限ってはこれに準拠しない
* できるだけCSSフレームワークで用意されているクラスを用いる
* BEMの概要についてこちらを[参照](https://github.com/juno/bem-methodology-ja)

#### Block

Blockはデザインを構築する親の要素となるような要素。

```css
.item
.item-list
.form
.form-search
.form-search-item
```

#### Element

Elementはデザインを構成する基本要素で、Blockに内包されます。
Elementが集まったものがBlockになります。

```css
.item__text
.item-list__btn
.form__input
.form-search__title
.form-search-item__user
```

#### Modifier

状態を表すときに使います。

```css
.item--red
.item-list__btn--type_success
.form__input--active
.form-search__title--hover
.form-search-result__user--following
```

### そのほか

* CSSはクラスに記述する
  * タグなどにCSSを当てない => 「打ち消すためのCSS」が増えて肥大化するため
* 制限されたCSSを書かない => CSSの再利用性を高めるため
* 使用する汎用クラス名はフレームワーク([materialize](http://materializecss.com/))で使われているのみ
  * 自作クラスはBEMで
  * そうすることでフレームワークのクラスとの判断もすぐにつけることができる

```css
// NG
div.modal
  text-align: left
p.content
  padding: 10px
```

```css
// OK
.modal
  text-align: left
.content
  padding: 10px
```

* CSSのネストは孫まで
  * BEMできちんと命名していればそもそもネストは必要ない
  * ネストが増えるとレンダリングの速度も落ちる
* CSSプロパティはアルファベット順に並べる。mixinは最初
* HTMLとCSSのインデントは半角スペース2文字
* CSSのプロパティはできるだけまとめる (marginなど)
* colorの16進数はしない、しなくて済むように設計
  * => よりメンテナブルで柔軟性のあるスタイルシートになる
  * materializeのカラーをHTMLのクラス名で指定
  * それができなければSASSの変数で指定
* Colorの16進数表記は3桁でも表せれる場合は3桁にする
* Colorはuppercaseで書く

```css
// NG
.hoge
  color: #ffffff

// OK
.hoge
  color: #FFF
```

* コメントは単行コメントのみ使う
  * コメントが入れ子になったりするのを防ぐ
* JSからアクセスする必要のあるクラスは、`js-hoge`と命名する。ただし、極力JSはIDを用いて指定する
* HTML中のクラス名は、CSSフレームワークのクラスを先に書き、自分で定義したクラスは後に書く
  * CSSフレームワークのデザインをベースに考えながらコーディングできる
* インラインスタイルは使わない
* `!important`は(極力)使わない
  * 特にmaterializeのスタイルが多重に継承されている場合などに打ち消したいときなどには使ってもよいが、`!important`を使う時点でスタイルシートが複雑になっている可能性が高い

## 参考リンク

* [Japanese Translations of BEM-Methodology](https://github.com/juno/bem-methodology-ja)
* [こんなHTMLとCSSのコーディング規約で書きたい](http://qiita.com/pugiemonn/items/964203782e1fcb3d02c3)
* [Railsのプロジェクトリニューアルの機会にHTML/CSSのコーディング規約を作ってみた](http://qiita.com/soyanchu/items/dd99fe2b3d08eb7128c7)
