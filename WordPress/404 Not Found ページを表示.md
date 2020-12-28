- 404.phpを作成  

- 404.phpを修正  
```404.php
<form class="search-form" role="search" method="get" action="<?php echo esc_url(home_url()); ?>">
```

- formタグのinputタグ内のname属性には「s」を指定する必要あり  
`<input type="text" name="s" class="search-input" placeholder="キーワードを入力してください" value="">`  

- メイン画像のタイトルを表示させる  
🔻function.php  
```function.php
elseif (is_404()):
        return 'ページが見つかりません';
```

- メイン画像を表示させる  
🔻function.php
```function.php
elseif (is_search() || is_404()):
```

