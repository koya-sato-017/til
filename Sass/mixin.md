# @mixin

## @mixin を定義


`@mixin mixin名 { コード }`

## mixin の呼び出し

`@include mixin名`

## 引数を使って mixin にデータを渡す

`@mixin mixin名($hoge){}`

`@include mixin名($hoge);`

## 引数の初期値を指定する

`@mixin mixin名($hoge: 123){}`

`@include mixin名();`

* 引数を指定しないと、初期値が入る

