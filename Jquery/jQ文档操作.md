```js
$(obj).after$(obj2) <--> $(obj).insertBefore$(obj2)  //obj2当弟弟
$(obj).Before$(obj2) <--> $(obj).insertAfter$(obj2)  //obj2当哥哥
$(p).warp  //p找父亲
$(p).unwarp() //通过儿子杀父级
 obj.warpall(obj2) //集体认爹 如果有儿子放在第一个儿子的里面
 obj.wrapInner(obj2) //为所有对象下子节点添加一个父亲
 obj.replaceWith(obj2)  //把obj整个替换为obj2
 	empty()  //清空内容
 	remove()  //自杀不会保留事件
 	detach  //自杀 会保留事件
 	clone  //true 深复制 false 浅复制
 	
```
