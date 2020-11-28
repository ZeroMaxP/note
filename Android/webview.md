## 设置APP的联网权限

```xml
<uses-permission android:name="android.permission.INTERNET"></uses-permission>
```



## JAVA实现

```java
WebView webView; //初始化

webView=(WebView)findViewById(R.id.webview);//获取webview的实例,并转化为对象 

webView.getSettings().setJavaScriptEnabled(true);//获取WebSeting对象并设置支持JS

webView.setWebViewClient(new WebViewClient()); //设置在当前界面打开不转到系统browser

webView.loadUrl("http://www.zeromaxp.com/")//加载url
    
webView.setWebViewClient(new WebViewClient() {
    public boolean shouldOverrideUrlLoading(WebView View,String url){
        	View.loadUrl(url);
        	return true;
        	}
        });
//和上面一样的是每次访问都在当前界面true是当前界面,flase是系统网页
```

