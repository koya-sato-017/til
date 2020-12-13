# jsonplaceholder が持っている WebAPI のいろんな情報を DOM に反映する

## データのやりとり

* JavaScript 側から HTML の ID を取得したいので、`getElementById`メソッドを使い、 ID がついているタグを変数に格納

* ボタンにクリックイベントを追加  
`addEventListener`は第二引数にコールバック関数を受け取る

* `function`の中で、ユーザーを取得する WebAPI を叩く  
`async function`と`fetch`を使い、`await`をつける

```index.js
const button = document.getElementById("addBtn");
const lists = document.getElementById("lists");

button.addEventListener("click", async function() {
    // データのやりとり
    const res = await fetch("https://jsonplaceholder.typicode.com/users");
    const users = await res.json();
```

## DOM操作

* ボタンを押して`li`要素が追加されるようにする

* `document.createElement`で HTML 要素を生成

* `li`タグに list を追加
`list.innerText = "foo";`  
`lists.appendChild(list);`

* API で取得したユーザーを li 要素として追加

* `forEach`メソッドで、引数にコールバック関数をとる
`users.forEach(function(user) {`  
`forEach`を使うことで、10回分（10個分）のユーザー情報を取得

* 名前`user.name`以外にも li 要素として追加可能  
`user.name`を`user.address.zipcode`とすると、郵便番号を取得

```index.js
const button = document.getElementById("addBtn");
const lists = document.getElementById("lists");

button.addEventListener("click", async function() {
    // DOM操作
    users.forEach(function(user) {
        const list = document.createElement("li");
        list.innerText = user.name;
        lists.appendChild(list);
    });
});
```

#### `for`文でも記述可
```index.js
for (let index = 0; index < users.length; index++) {
        const user = users[index];
        const list = document.createElement("li");
        list.innerText = user.name;
        lists.appendChild(list);
    }
```

### ページを読み込んだ時にユーザーを li 要素に追加する

`window.addEventListener`を使う

```index.js
window.addEventListener("load", async function() {
    // データのやりとり
    const res = await fetch("https://jsonplaceholder.typicode.com/users")
    const users = await res.json();

    // DOM操作
    users.forEach(function(user) {
        const list = document.createElement("li");
        list.innerText = user.name;
        lists.appendChild(list);        
    });
});
```

### リファクタリング

* 共通部分切り取り、`function`に`listUsers`と名前をつける
```index.js
async function listUsers() {
    // データのやりとり
    const res = await fetch("https://jsonplaceholder.typicode.com/users")
    const users = await res.json();

    // DOM操作
    users.forEach(function(user) {
        const list = document.createElement("li");
        list.innerText = user.name;
        lists.appendChild(list);        
    });
}
```

* 共通部分にそれぞれ`listUsers`を貼り付ける  
```button.addEventListener("click", listUsers);```  
```window.addEventListener("load", listUsers);```

* 処理を分解する  
`function`に`getUsers`と名前をつける

```index.js
async function getUsers() {
    const res = await fetch("https://jsonplaceholder.typicode.com/users")
    const users = await res.json();
    return users;
}
```
```index.js
async function listUsers() {
    const users = await getUsers();
```


* `function`に`addList`と名前をつける
```index.js
function addList(user) {
    const list = document.createElement("li");
    list.innerText = user.name;
    lists.appendChild(list);        
}
```

* `addList`を`forEach`の中に入れる  
`users.forEach(addList);`

* 順序を整理する

* コメントを追加する

## 完成したコード
```index.js
// DOM
const button = document.getElementById("addBtn");
const lists = document.getElementById("lists");

// 関数（メソッド）
function addList(user) {
    const list = document.createElement("li");
    list.innerText = user.name;
    lists.appendChild(list);        
}

async function getUsers() {
    const res = await fetch("https://jsonplaceholder.typicode.com/users")
    const users = await res.json();
    return users;
}

async function listUsers() {
    const users = await getUsers();
    users.forEach(addList);
}

// イベント
window.addEventListener("load", listUsers);
button.addEventListener("click", listUsers);
```
