
```js
	$.makeArray(类数组) //最好用1版本
	$.inArray(数组)  //类似indexOf
	$obj.toArray()  //把前面的集合返回成数组
	type()  //返回对象
	.broswer.version()  //返回浏览器版本 用于检查IE版本号
	if($.broswer.msie)
		alert($.broswer.version);
	//返回IE版本号
    $.trim()  //去空格
    $.extend()  // 静态方法  用于添加静态方法 不能被实例调用
    			//用于合并对象 obj1 obj2 obj3 把obj2和obj3放进obj1里  后面覆盖前面的同名属性
    $.fn.extend()//$.fn是jQ原型  动态方法  给实例调用的 $("box").fn
	

```
