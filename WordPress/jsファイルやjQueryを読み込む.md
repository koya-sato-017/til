# WordPressにjsファイルやjQueryを読み込みたい  
- 前提として、WordPressにはあらかじめjQueryが読み込まれている  

## functions.php での記述  

### パラメータ  
```functions.php
<?php wp_enqueue_script( $handle, $src, $deps, $ver, $in_footer ); ?>
```  
- `$handle`  
ハンドル名　好きな名前でOK  
- `$src`  
`get_template_directory_uri`  
を使って取得する  
- `$deps`  
依存するスクリプトのハンドル名を指定  
初期値： array()  
例： `array( 'jquery' )`  
- `$ver`  
スクリプトのバージョン番号を指定する文字列  
初期値： false  
- `$in_footer`  
初期値： false  
`true`にすると、</body> 終了タグの前に配置(`wp_footer()`テンプレートタグが含まれていることが必須)  

### フック  
アクションフックでスクリプトとスタイルをエンキューする  
```functions.php
<?php
function theme_name_scripts() {
	wp_enqueue_style( 'style-name', get_stylesheet_uri() );
	wp_enqueue_script( 'script-name', get_template_directory_uri() . '/js/example.js', array(), '1.0.0', true );
}

add_action( 'wp_enqueue_scripts', 'theme_name_scripts' );
?>
```  
- jQuery に依存するテーマのスクリプトをリンクする場合  
`array( 'jquery' )`  

### 自作のjQueryを読み込む場合  
- いったんWordPress既存のjQueryを解除する必要あり  
```functions.php
function add_my_scripts() {	
  //WordPress 本体の jQuery を登録解除
  wp_deregister_script( 'jquery');  
  //jQuery を CDN から読み込む
  wp_enqueue_script( 'jquery', 
    '//ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js', 
    array(), 
    '3.3.1', 
    true //</body> 終了タグの前で読み込み
  );
```  

## jQuery における noConflict モード  
WordPress に含まれる他の JavaScript ライブラリとの互換性の問題を防ぐため、デフォルトで noConflict モードになっている  

下記のように書くとエラー  
```
$(document).ready(function(){
     $(#somefunction) ...
});
```  
下記のように書かなければならない  
```
jQuery(document).ready(function(){
    jQuery(#somefunction) ...
});
```  
または  
`jQuery(function($){});`で囲む  

