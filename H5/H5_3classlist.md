### 通过classList对class类名 增删改查

```js
//添加
obj.onclick=function(){
  obj.classList.add(value)  //"abe","fsa" 可以  "fsaf fsa" 不行
 }

//删除
obj.onclick=function(){
  obj.classList.remove(value)  //"abe","fsa" 可以  "fsaf fsa" 不行
 }

//删除
obj.onclick=function(){
  this.classList.length// length
  obj.classList(value)  //"abe","fsa" 可以  "fsaf fsa" 不行
 }

//有删除，没有添加
obj.onclick=function(){
  obj.classList.toggle(value)  //"abe","fsa" 可以  "fsaf fsa" 不行
 }

//判断是否存在
obj.onclick=function(){
  let c=obj.classList.contains(value);
  c?obj.classList.remove(value):obj.classList.add(value)
  obj.classList.remove(value)  //"abe","fsa" 可以  "fsaf fsa" 不行
 }
```

### Dataset

```js
<div data-a="af" data-a-bf-cf></div>
console.log($("div")[0].dataset.a)
console.log($("div")[0].dataset["aBfCf"])
 //从第一个名字之后 ，都要驼峰命名发
let box=$("div")[0];
box.dataset[a]="new value";
box.setAttribute("data-a","new value");
console.log(box.getAttribue("data-a"));
box.removeAttribute("data-a");
delete box.dataset["data-a"];
```

### Parse-stringfy

```js
1.//解析后端传来的字符串
let arrStr="["hhh",18]";
let newArr=JSON.parse(arrStr);
console.log(newArr);

let json1="{"name":"faf","age":"54"}";
let json2=`{
"name":"afa",
"age":"54"
}`
console.log(let newjson1=JSON.parse(json1));

2.前端发起请求，携带数据，格式为字符串
let json3={
name:"afa",
age:54
}
console.log(JSON.srtingify(json3))  //默认补上双引号

let arr3=["afa","ff"];
console.log(JSON.stringify(arr3));

//不太安全.jpg
eval();
```

### decodeurl

```js
decodeURI(str) //解码 decodeURIComponent
encodeURI(str) //编码 encodeURIComponent
```

### btoa-atob

```js
把数据编译成base64编码 可以减少http请求 但是不要大面积使用
let str="faf";
let str1=window.btoa(str); //编码
let str2=window.atob(str); //解码
let str3="十大lff"; //有中文先转uicode编码
let uri=encodeURIComponent(str3);
var str4=window.btoa(uri);
str4=window.atob(str4);
decodeURIComponent(str4);

```



