jq 版本区别  1版本  //兼容所有broswer

3  version  不兼容IE8

jQuery  $//命名空间

jq对象只能调用jq的API  //

```js
	//jQ对象转成原生对象
1	$(document).get(0)  -- $(document)[0]  
	
	//原生对象转jQ对象
    $(document)
    
    //获取子类
    get(index)
    
    //h5 新CSS自定义属性 前面加data-attr 前缀
    $(document).data("attr");   //带data前缀的
    $(document).data("attr");   //获取CSS属性
    $(document).prop("attr");	//获取合法属性，boolean只能用这个
```





