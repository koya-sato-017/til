# @for と @while

## @for

```style.scss
@for $i from 1 to 5 {
    .level_#{$i} {
        font-size: 2px * $i;
    }
}
```

```style.css
.level_1 {
  font-size: 2px;
}

.level_2 {
  font-size: 4px;
}

.level_3 {
  font-size: 6px;
}

.level_4 {
  font-size: 8px;
}
```

## @while

```style.scss
$i: 1;
@while $i < 10 {
    .level_#{$i} {
        font-size: 2px * $i;
    }
    $i: $i + 2;
}
```

```style.css
.level_1 {
  font-size: 2px;
}

.level_3 {
  font-size: 6px;
}

.level_5 {
  font-size: 10px;
}

.level_7 {
  font-size: 14px;
}

.level_9 {
  font-size: 18px;
}
```

* @for と比べて @while の方が書き方が複雑だが、その分自由に繰り返しが作れる
