# Window, Document オブジェクト

* Window や Document はあらかじめブラウザ側が用意してくれているので定義する必要はない

```index.js
window = {
    console: {
        log() { },
    },
    alert() { },
    document: {
        getElementById() { },
        
    }
 }
 ```
 `window.console.log()`  
 * window は省略可能なので   
 `console.log()`  
 と書ける
 
 ```
 document: {
        getElementById() { },
        
    }
```  
* DOM（≒HTMLへのアクセス）

`window.screen.width`  
`window.screen.height`  
`window.document.getElementById("Masthead");`  
→ `<div id ="Masthead" class="… ">…</div>`  
`window.location.reload();`  
