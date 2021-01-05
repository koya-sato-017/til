`$('#...').html('...');`  
セレクター.メソッド（'パラメーター'）  


```jquery.html
$.getJSON('https://h2o-space.com/htmlbook/images.php', function(data) {
            for (var i=0; i<data.length; i++) {
                $('<div class="photo"></div>')
                .append('<img src="' + data[i].path + '">')
                .append('<div class="inner"><p>' + data[i].caption + '<span>' + data[i].name + '</span></p></div>')
                .appendTo('#img_unit');
            }
        });
```

上記で以下のような記述が作成された  
```jquery
<div class="photo">
    <img src="img/img01.jpg">
    <div class="inner"><p>caption<span>name</span></p></div>
</div>
```
`appendTo` で `#img_unit` の中に上記が入った  

```jquery
<div id="img_unit">
    <div class="photo">
        <img src="img/img01.jpg">
        <div class="inner"><p>caption<span>name</span></p></div>
    </div>
</div>
```

