```js
 //type 方式 url 接口 data 请求数据 success()成功时候执行的函数
 data:{
     user:"value1",
     pwa:"value2"
 }
 
 cache:boolean  //true就缓存  false不缓存
 context  //修改上下文环境 即this指向
 error:function(){
     
 }
 dowm //完成执行
 
 timeout //请求超时
 passward  //用人输入密码  如果接口需要密码
 
 async  //ture 异步 false 同步
 
$.ajax({
   type: "POST",  
   url: "some.php",
   data: "name=John&location=Boston",
   success: function(msg){  //msg 默认给你json parse
     alert( "Data Saved: " + msg );
   }
});

$.get("url",data,callback,type)  //如果后台需要你发送的数据类型可以传type

$.post("url",{data},callback,type)  //

$.getJSON("test.php",{},function(msg){
    //msg 是json类型
}}

//在页面上有ajax = new XMLHttpRequest 时执行
ajaxStart()
ajaxSend() send前回调
ajaxSuccess()

$(dom).load("url") //请求把返回的内容放进dom中



```
