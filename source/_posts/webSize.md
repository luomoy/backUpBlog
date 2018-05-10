---
title: 前端冷知识集锦
tag: 
	- 前端
	- hexo
---
分享一些浏览网页时get到的前端技能和冷知识


### 把浏览器当编辑器

#### 以下代码贴到地址栏运行后浏览器变成了一个原始而简单的编辑器，与Windows自带的notepad一样
``` java
data:text/html, <html contenteditable>
```

归根结底多亏了HTML5中新加的contenteditable属性，当元素指定了该属性后，元素的内容成为可编辑状态。

推而广之，将以下代码放到console执行后，整个页面将变得可编辑

``` java
document.body.contentEditable='true';
```
<!--more-->
### 关于CSS的恶作剧
相信你看完以下代码后能够预料到会出现什么效果。

``` java
*{
    cursor: none!important;
}
```


### 简单的文字模糊效果
以下两行简单的CSS3代码可达到将文字模糊化处理的目的，出来的效果有点像使用PS的滤镜，so cool!

``` bash
p {
    color: transparent;
    text-shadow: #111 0 0 5px;
}
```

### 垂直居中
前提是要给父集盒子加上相对定位，并给宽高为100%；

``` bash
div {
    position: absolute;
    top: 50%;
    left:50%;
    transform: translate(-50%,-50%); 
}
```

### 生成随机字符串
利用Math.random和toString生成随机字符串，来自前一阵子看到的一篇<a href="https://modernweb.com/45-useful-javascript-tips-tricks-and-best-practices/">博文</a>。这里的技巧是利用了toString方法可以接收一个基数作为参数的原理，这个基数从2到36封顶。如果不指定，默认基数是10进制。略屌！ 

``` bash
function generateRandomAlphaNum(len) {
    var rdmString = "";
    for (; rdmString.length < len; rdmString +=Math.random().toString(36).substr(2));
    return rdmString.substr(0, len);
}
generateRandomAlphaNum(10)//数字可根据自身需要更改
```

### 禁止别人以iframe加载你的页面
``` bash
if (window.location != window.parent.location) window.parent.location = window.location;
```
###console.table
``` bash
var data = [{'品名': '杜雷斯', '数量': 4}, {'品名': '冈本', '数量': 3}];
console.table(data);
```