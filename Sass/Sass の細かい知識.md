## コメント

* １行コメントは、 scss にのみ表示される

```style.scss
h1 {
    /* 色を赤にする */
    // １行コメント
    /* color: red; */
    background-color: #ccc;
}
```  
以下のようにコンパイルされる  
```style.css
h1 {
  /* 色を赤にする */
  /* color: red; */
  background-color: #ccc;
}
```

## Live Sass Compile の設定

* コンパイル先の css を軽くする
* liveSassCompile.settings.formats を開く

`"format": "expanded"`  
を  
`"format": "compressed"`  
に変更

* コメントアウトを以下のように「!」をつけると、複数行コメントは css にも反映される  
`/*! color: red; */`

## 変数のスコープ

* 変数をセレクターの中で宣言すると、セレクターの中でしか使えない  
```style.scss
h1 {
    $primary-color: red;
    color: $primary-color;
    background-color: #ccc;
}

p {
    color: $primary-color;
}
```

以下のエラー  
`Error: Undefined variable: "$primary-color".`
