# @extend

```index.html
<a href="#" class="btn-default">ボタン</a>
<a href="#" class="btn-alert">ボタン</a>
```

```style.scss
%btn {
    padding: 5px 10px;
    border-radius: 5px;
    color: #333;
    text-decoration: none;
}

.btn-default {
    @extend %btn;
    background-color: #ccc;
}

.btn-alert {
    @extend %btn;
    background-color: #fcc;
}
```

scss を上記のように書くと、 css は下記のようにコンパイルされる

```style.css
.btn-default, .btn-alert {
  padding: 5px 10px;
  border-radius: 5px;
  color: #333;
  text-decoration: none;
}

.btn-default {
  background-color: #ccc;
}

.btn-alert {
  background-color: #fcc;
}
```

* `%btn`で形状を指定して、`.btn-default`と`.btn-alert`それぞれで色を指定するという考え方

