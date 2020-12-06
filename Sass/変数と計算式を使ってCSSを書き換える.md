## 複数箇所の色の指定を同時に行う

```style.scss
$primary-color: rgb(6, 58, 155);

a {
    color: $primary-color;
}

btn {
    color: #fff;
    background-color: $primary-color;
}
```

style.css では以下のようになる

```style.css
a {
  color: #063a9b;
}

.btn {
  color: #fff;
  background-color: #063a9b;
}
```

## 変数と計算式を使って複数箇所の値を同時に変更する

```index.html
  <p><a href="#" class="btn">申し込む</a></p>
  <p><a href="#" class="btn btn-large">申し込む</a></p>
  <p><a href="#" class="btn btn-small">申し込む</a></p>
```

```style.scss
$btn-width: 80px;

.btn {
    color: #fff;
    background-color: $primary-color;
    padding: 5px 10px;
    text-decoration: none;
    width: $btn-width;
    display: inline-block;
    text-align: center;

    &.btn-large {
        width: $btn-width * 2;
    }
    
    &.btn-small {
        width: $btn-width / 2;
    }
}
```

```style.css
.btn {
  color: #fff;
  background-color: #063a9b;
  padding: 5px 10px;
  text-decoration: none;
  width: 80px;
  display: inline-block;
  text-align: center;
}

.btn.btn-large {
  width: 160px;
}

.btn.btn-small {
  width: 40px;
}
```
