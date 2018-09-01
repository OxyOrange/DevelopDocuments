
# 关于WKWebView高度的问题的解决

### IOS端嵌入网页的方式有两种UIWebView和WKWebView。其中WKWebView的性能要高些<\br>WKWebView的使用也相对简单

### WKWebView在加载完成后，在相应的代理里面获取其内容高度，大多数网上的方法在获取高度是会出现一定的问题，就是高度不准确；其解决方案如下：

![](https://github.com/zhanghouqi/DevelopDocuments/blob/master/Images/B6149FFE-1FFA-4FCB-99E1-893B47BBDEBB.png)

该方法获取的高度较为准备，无需其他处理就好