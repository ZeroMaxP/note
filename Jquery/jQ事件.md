```js
	//效果均接受speed参数
	obj.trigger("type",[arg1,argu2])  //用数组传参 type时已经绑定的函数
	show(speed,[fn])  //显示
	hide(speed,[fn])	//隐藏
	toggle  // 显示变隐藏  隐藏变显示
	slideUp（speed,[easing],[fn]）  //高度递减，递减到0 就display :none;		speed--> slow normal fast 或ms值 [fn]回调
	slideDown()  // 掉下来
	slideToggle() //Up Down转换
	$box.show(1000,function(){
        $box.hide()
	})  //显示后隐藏
	fadeOut()  //淡出
	fadeIn()  //淡入
	fadeToggle()  //切换
	fadeTo(sp,opacity,[easing],[fn])  //设定目标透明度 
	animate({
        width:value1,
        height:value2,
        opacity:value3
	},speed,[fn])  //传对象
	hover(fn1,fn2)  //fn1移入事件 fn2移出事件
	stop(arg1,arg2)  //清空当前对象的动画队列
		arg1 //true 和false没效果 agr2 //true 清除动画队列时，瞬间到达目标值， false  清除动画队列时，停在当前位置
	delay(timer)  //动画延迟时间 延迟delay后面的动画
	finish()  //相当于stop(true ,true)只对前面的函数生效
	
    
	
    
    
```
