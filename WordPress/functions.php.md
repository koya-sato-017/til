# functions.php

- 機能を拡張するためのファイル

## タイトルタグを自動的に生成する

`function init_func() {
    add_theme_support('title-tag');
}`

- `init_func()`を実行する

`add_action('init', 'init_func');`

`add_action('after_setup_theme', 'init_func');`

- `after_setup_theme`
の方が早い

- これにより、index.phpの中のheadタグに自動的にtitleタグが生成される
