### WebAPI を叩くとは
* プログラミング上から外部とデータのやりとりをすること
* 「非同期」という概念

### 

```index.js
function callApi() {
    const res = window.fetch("https://jsonplaceholder.typicode.com/users");
    console.log(res);
}

callApi();
```
`window`は省略可


```DevTools
Promise {<pending>}
```

`function callApi() {`  
を  
`async function callApi() {`  
と書く

`async function`
* 非同期関数と呼ばれる

`const res =　fetch("https://jsonplaceholder.typicode.com/users");`  
を  
`const res =　await fetch("https://jsonplaceholder.typicode.com/users");`  
と書く

```DevTools
Response
```

* async await で fetch を使うと Response オブジェクトが返ってくる

`const users = await res.json();`  
json メソッドで実際にプログラミング上から使いやすい形に変換

```index.js
async function callApi() {
    const res =　await fetch("https://jsonplaceholder.typicode.com/users");
    const users = await res.json();
    console.log(users);
}

callApi();
```

```DevTools
(10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```
展開すると  
```DevTools
(10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
0: {id: 1, name: "Leanne Graham", username: "Bret", email: "Sincere@april.biz", address: {…}, …}
1: {id: 2, name: "Ervin Howell", userna
```

* `fetch``then`を使って書き換え
```index.js
function callApi() {
    fetch("https://jsonplaceholder.typicode.com/users")
        .then(function(res) {
            return res.json();
        })
        .then(function(users) {
            console.log(users);
        })
}

callApi();
```

* `XMLHttpRequest`を使って書き換え
```index.js
function callApi() {
    const xhr = new XMLHttpRequest();
    xhr.open("GET", "https://jsonplaceholder.typicode.com/users");
    xhr.responseText = "json";
    xhr.send();
    xhr.onload = function() {
        console.log(xhr.response);
    };
}

callApi();
```
