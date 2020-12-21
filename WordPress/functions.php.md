# functions.php

- 機能を拡張するためのファイル  
- テンプレート内で利用する独自のテンプレートタグや関数を定義するためのファイル  

## タイトルタグを自動的に生成する

`function init_func() {`

`    add_theme_support('title-tag');`

`}`

- `init_func()`を実行する

`add_action('init', 'init_func');`

`add_action('after_setup_theme', 'init_func');`

- `after_setup_theme`
の方が早い

- これにより、index.phpの中のheadタグに自動的にtitleタグが生成される

## アイキャッチ画像を表示させる

- function.php ファイルに以下のように書く
```function.php
add_theme_support('post-thumbnails');
```

- 投稿一覧のアイキャッチ画像に画像を指定

- single.phpの`header`の上に`<?php the_post_thumbnail(); ?>`を記述すると、imgタグをそのまま使ってしまうので、下記のようにする

```single.php
<?php
  $id = get_post_thumbnail_id();
  $img = wp_get_attachment_image_src($id);
?>
```

```single.php
style="background-image: url('<?php echo $img[0]; ?>')">
```
