# CSS Lint
＊ Web 業界2年目の端くれで、 HTML や CSS の根っこ、仕様書から理解していきたいと考えている人です。CSSリントってなんぞやと思って調べていたら、気になってきたのでちょっと翻訳してみる。英語の勉強も兼ねて。気が向いたら更新と言うことで。後結構タイプミスがあるけど、手に障害があってキーボード入力が遅いので、 Google ドキュメントに音声入力で入力した後、コピペしているからである。とりあえずざっくりと訳していく方が大事だと思うんで細かいところは未来の自分に任せることにする。


https://github.com/CSSLint/csslint
# Parsing errors should be fixed
The most important rule, as far as CSS Lint is concerned, is to ensure there are no parsing errors in the CSS. Parsing errors usually mean you mistyped a character and caused the code to become invalid CSS. These errors may cause the browser to drop a property or an entire rule. Parsing errors are always presented as errors by CSSLint, the most important issues to fix.

## Possible Errors
The following rules point out potential errors in your CSS.

* box-model: Beware of box model size

* display-property-grouping: Require properties appropriate for display

* duplicate-properties: Disallow duplicate properties

* empty-rules: Disallow empty rules

* known-properties: Require use of known properties
## Compatibility
The following rules flag for compatibility problems across browsers and browser settings.

adjoining-classes: Disallow adjoining classes
box-sizing: Disallow box-sizing
compatible-vendor-prefixes: Require compatible vendor prefixes
gradients: Require all gradient definitions
text-indent: Disallow negative text-indent
vendor-prefix: Require standard property with vendor prefix
fallback-colors: Require fallback colors
star-property-hack: Disallow star hack
underscore-property-hack: Disallow underscore hack
bulletproof-font-face: Bulletproof font-face (new in v0.9.10)
## Performance
The following rules are aimed at improving CSS performance, including runtime performance and overall code size.

* font-faces: Don't use too many web fonts
Web フォントを使うとそれに伴うファイルが大きいのと、それらをダウンロードするあいだ Web ページをレンダリングするの止めてしまうから。5個以上は使わないでね 。

* import: Disallow @import
インポートを使うとウェブブラウザがコードを読み込むとき、インポートで設定されている CSS ファイルをダウンロードするまで泊まるから。
なるべく使わないでね。なるべく一緒にまとめるか、 Head タグのリンクで設定してね。

* regex-selectors: Disallow selectors that look like regular expressions
読み込みが遅くなるからセレクターに正規表現を混ぜないで。
※使うセレクタによってブラウザの読み込みが違う。^[[パフォーマンス観点でのCSSセレクタ指定方法](https://qiita.com/rnakayama/items/168bcbc05e6b1fc989f5)]

* universal-selector: Disallow universal selector
ユニバーサルセレクタをキーセレクタにしないで。全部読み込みに入っちゃうから。[^1][^2]

* unqualified-attributes: Disallow unqualified attribute selectors
属性セレクタをキーセレクタに設定しないで、全部読み込みに入っちゃうから。[^1]

* zero-units: Disallow units for zero values
0に特に退院をつけなくていいよ。 長さやパーセントの数字を設定する全てのシチュエーションにおいて特定の単位を指定することなしに0は機能する。 
* overqualified-elements: Disallow overqualified elements
過剰にセレクターにエレメントつけていないかどうか。 

* shorthand: Require shorthand properties
マージンやパディングなど、上下左右個別で設定している時は短縮して書いてください。

* duplicate-background-images: Disallow duplicate background images
CSS からバックグラウンドを読み込む時、 一つのセレクターから読み込むようにして。
同じ background を使って別の設定をしたいのなら、クラスを作って上書きしてね。


[^1]:[ブラウザのCSS解釈方法についての衝撃事実](https://qiita.com/rnakayama/items/e4f3b54e266f7e1867f9)
[^2]:[CSSの適用について、予想外の事実を知った](http://d.hatena.ne.jp/oknknic/20110716/1310835176)


## Maintainability & Duplication
These rules help to ensure your code is readable and maintainable by others.

* floats: Disallow too many floats
たくさんのフロートを使いすぎない。 たくさんフロートを使っている場合はグリッドシステムを使うといいよ。

* font-sizes: Don't use too many font-size declarations
いたるところにフォントサイズプロパティを設定しないでね
十箇所見つけたら警告を出します 

* ids: Disallow IDs in selectors 
IDタグはセレクターで使わないように。
ページに１つの決まりがあり、メンテナンス性が悪い。セレクタで使うと、効率悪いよ^[[Don’t use IDs in CSS selectors?。](http://oli.jp/2011/ids/)]

* important: Disallow !important
Important 室蘭において与えられたプロパティーの合体の得意地形を人為的にやったのに使われる.
Important を使えば使うほどデベロッパーはページの一部分を直す時に効率的に 問題を抱えるようになる
スタイルシート内に important を一つでも使っていると警告する 

* order-alphabetical: Disallow non alphabetical
## Accessibility
These rules are designed to pick out possible accessibility issues.

* outline-none: Disallow outline:none
## OOCSS
These rules are based on the principles of OOCSS.

* qualified-headings: Disallow qualified headings
* unique-headings: Headings should only be defined once
Translation
