# CSSコーディングスタイルガイド

## 基本方針

1. HTMLとCSSを極力書かない
2. 増やすより減らす
3. メンテナブルなコードを書く

## ガイド

* クラスの命名規則にBEMを使う。BEMの規則は[こちらの既約](https://github.com/juno/bem-methodology-ja)に準拠。
    * materializeのクラス名に限ってはこれに準拠しない
* CSSはクラスに記述する
    * タグなどにCSSを当てない => 「打ち消すためのCSS」が増えて肥大化するため
* 制限されたCSSを書かない => CSSの再利用性を高めるため

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

* CSSプロパティはアルファベット順に並べる。mixinは最初
* HTMLとCSSのインデントは半角スペース2文字
* CSSのプロパティをまとめれるときはできるだけまとめる (marginなど)
* Colorの16進数表記は3桁でも表せれる場合は3桁にする
* CSSのネストは孫まで
    * BEMできちんと命名していれば必要ない
    * ネストが増えるとレンダリングの速度も落ちる
* コメントは単行コメントのみ使う
    * コメントが入れ子になったりするのを防ぐ
* JSからアクセスする必要のあるクラスは、`js-hoge`と命名する。ただし、極力JSはIDを用いて指定する
* インラインスタイルは使わない
* `!important`は(極力)使わない
    * 特にmaterializeのスタイルが多重に継承されている場合などに打ち消したいときなどには使ってもよいが、`!important`を使う時点でスタイルシートが複雑になっている可能性が高い
* 使用する汎用クラス名はフレームワーク(materialize)で使われているのみ
    * 自作クラスはBEMで
    * そうすることでフレームワークのクラスとの判断もすぐにつけることができる

## 参考リンク

* [Japanese Translations of BEM-Methodology](https://github.com/juno/bem-methodology-ja)
* [こんなHTMLとCSSのコーディング規約で書きたい](http://qiita.com/pugiemonn/items/964203782e1fcb3d02c3)
* [Railsのプロジェクトリニューアルの機会にHTML/CSSのコーディング規約を作ってみた](http://qiita.com/soyanchu/items/dd99fe2b3d08eb7128c7)
