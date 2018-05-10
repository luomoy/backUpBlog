---
title: 移动端软键盘调出时挤压布局
date: 2018-05-08 17:09:55
tags:
	- 移动端
	- 软键盘
---
input聚焦时会调出手机自带的软键盘，安卓移动端上软键盘会挤压布局，但人iphone确实好着的。
对于这个问题也百度了好多，试了很多方法，***各种定位、定时器、计算窗口高度和页面高度什么的***，都没有效果，最后在一个前端群里问了这个问题，就有个大佬让我试试，然后就解决了？对！就这样解决了!
解决办法：
* 给页面绝对定位
* body上有自适应背景图，防止背景图压缩可以执行以下：

``` java
//获取设备高度（软键盘调出来时高度也会变小，所以在点击事件前获取）
var deviceH=document.documentElement.clientHeight+"px";

//表单获得焦点后动态改变body和背景图片的大小
$('select,input').on("click",function(){
   $("body").attr("style","background:url('./img/bg2.jpg') no-repeat;
		width:100%;
		height:"+deviceH+";
		background-size: 100%"+deviceH);
});
```