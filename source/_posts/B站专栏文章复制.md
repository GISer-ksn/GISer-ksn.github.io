---
title: B站专栏文章复制
date: 2020-07-16 20:38:35
tags: 
  - JavaScript
categories: 
  - Bilibili
cover: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1595149378409&di=570b2f34ca1c53b60c3a5b4a61c346f9&imgtype=0&src=http%3A%2F%2Fn.sinaimg.cn%2Fsinacn%2Fw640h360%2F20180108%2F54c4-fyqincv3483815.jpg

top_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1595147812761&di=d005e78a1229ab381139f17c650482b1&imgtype=0&src=http%3A%2F%2Fp4.ssl.cdn.btime.com%2Ft013c4c6999528a21d4.jpg%3Fsize%3D1706x960

top: false
comments: true
copyright: false
#toc_number: false
---

## pc端b站专栏文章不可复制，在控制台执行一下代码即可

```javascript
document.querySelector('div.article-holder').classList.remove('unable-reprint');
document.querySelector('div.article-holder').addEventListener('copy',function(e){
    e.clipboardData.setData("text",window.getSelection().toString())
})
//移除'不可复制'属性，添加事件监听
```

<br/>

<br/>

<br/>

<br/>

<br/>

版权声明：本文为CSDN博主「Haip」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

原文链接：https://blog.csdn.net/u014324940/article/details/105101547/