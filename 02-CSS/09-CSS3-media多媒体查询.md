<h1>css3--media：多媒体查询</h1>
<h4>1. 概念--什么是多媒体查询？</h4>
<h4>2. 作用--多媒体解决的问题是什么？</h4>
<h4>3. 语法--多媒体查询的基本语法。</h4>
<h4>4. 实例--多媒体查询使用实例。</h4>
<h4>5. 主要媒体类型与关键字</h4>
<h4>6. 媒体类型特征写法及其特征列表</h4>
<h4>7. 媒体查询的其他写法</h4>
<h4>8. pc端/移动端断点尺寸</h4>
<h4>9. 使用bootstrap写法</h4>
<h4>10. 兼容移动端，viewport</h4>
<h4>11. css2中的media写法</h4>
<h1>多媒体查询？</h1>
<h2>1. 概念</h2>
媒体查询是指：通过查询出访问我们网页的设备的媒体类型，来决定使用何种样式。【所谓媒体就是指手机电脑等设备】
<h2>作用</h2>
媒体查询的作用为：为了解决在不同媒体类型上，网页的排版，显示，样式等问题。
<h2>基本语法</h2>
<span style="color:red;">@media</span>&nbsp;&nbsp;&nbsp;not|only mediatype&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:red;">and (expressions)</span><span style="color:green;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{  CSS 代码...;  }</span><br>
关键字&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;媒体类型&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;媒体特征&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;此媒体类型对应的代码</span>
<h1>多媒体查询--实例</h1>
<h2>1. 基本语法</h2>
<span style="color:red;">@media</span>&nbsp;&nbsp;&nbsp;not|only mediatype&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:red;">and (expressions)</span><span style="color:green;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{  CSS 代码...; }</span>
<h2>2.基本例子：</h2>

```
@media screen and(max-width:700px){
    body{
        color:red;
        font-size:30px;
    }
}
```
解释：<br><br>
这句代码表示，当媒体类型为电脑屏幕，平板，智能手机等类型，且最大宽度为700px时，让字体变为30px大小，颜色变为红色。<span style="color:red;">【也可以只给出媒体类型】</span>
<h1>主要媒体类型与关键字</h1>
<h2 style="color:red;">1.主要媒体类型</h2>
 
 - all    用于所有多媒体类型设置
 - print  用于打印机
 - screen 用于电脑屏幕，平板，智能手机等。
 - speech 用于屏幕阅读器
 <h2 style="color:red;">2.使用媒体查询时，媒体类型前面可以加上 not/only关键字，含义如下</h2>
 <b>not:</b><br><br>
  not是用来排除掉某些特定的设备的，比如 @media not print（非打印设备）。如果后面加了媒体特征的话，那么会更加具体的排除相应“包含此特征的媒体类型”<br><br>
<b>only:</b>
<b>用来定某种特别的媒体类型。</b>对于支持Media Queries的移动设备来说，如果存在only关键字，移动设备的Web浏览器会忽略only关键字并直接根据后面的表达式应用样式文件。<b>对于不支持Media Queries的设备但能够读取Media Type类型的Web浏览器，遇到only关键字时会忽略这个样式文件。</b>
<h1>多媒体特征写法与列表</h1>
<b style="color:red;">媒体类型特征</b><br><br>
<b>写法:</b>以<b>and</b>与类型相连，多个特征也以<b>and</b>相连】每个特征都写在括号中，类似于<b>css</b>属性的键值对写法】一个括号里面只写一个特征】<br><br>
<b>实例：</b><br><br>

```
@media screen and (max-width:700px) {

     body{
              color:red;
	 font-size:30px;
	}
    }

@media screen and (max-width:800px)  and (min-width:700px) {

     body{
              color:red;
	 font-size:30px;
	}
    }

```
<h2 style="color:red;">媒体类型特征---列表</h2>
height	定义输出设备中的页面可见区域高度。<br>
min-height	定义输出设备中的页面最小可见区域高度。<br>
max-height	定义输出设备中的页面最大可见区域高度。<br><br>
width	定义输出设备中的页面可见区域宽度。<br>
min-width	定义输出设备中的页面最小可见区域宽度。<br>
max-width	定义输出设备中的页面最大可见区域宽度。<br><br>
max-device-width	定义输出设备的屏幕最大可见宽度。<br>
min-device-width	定义输出设备的屏幕最小可见宽度。<br>
max-device-height	定义输出设备的屏幕可见的最大高度。<br>
min-device-height	定义输出设备的屏幕的最小可见高度。<br><br>
resolution	定义设备的分辨率。如：96dpi, 300dpi, 118dpcm<br>
max-resolution	定义设备的最大分辨率。<br>
min-resolution	定义设备的最小分辨率。<br><br>
aspect-ratio	定义输出设备中的页面可见区域宽度与高度的比率<br>
device-aspect-ratio	定义输出设备的屏幕可见宽度与高度的比率。<br><br>
device-height	定义输出设备的屏幕可见高度。<br>
device-width	定义输出设备的屏幕可见宽度。<br><br>
max-aspect-ratio	定义输出设备的屏幕可见宽度与高度的最大比率。<br>
min-aspect-ratio	定义输出设备中的页面可见区域宽度与高度的最小比率。<br><br>
max-device-aspect-ratio	定义输出设备的屏幕可见宽度与高度的最大比率。<br>
min-device-aspect-ratio	定义输出设备的屏幕可见宽度与高度的最小比率。
<h1>多媒体查询的其他写法</h1>
<b>1.可以不写媒体类型（默认为all），如下：</b>

```
<link rel="stylesheet" href="media.css" media="screen and (min-width:700px)" >
或
@media (min-width:700px){
 .body{
      color:blue;
	 font-size:80px;
      }
}
```
<b>2.可以使用逗号（，）被用来表示并列，如下</b>

```
<link rel="stylesheet" href="media.css" media="screen and (min-width:700px) and (max-width:800px),screen and (min-width:900px)" >

或

@media screen and (min-width:700px) and (max-width:800px),screen and (min-width:900px){

       //css样式文件
	
}

```
<h1>CSS媒体查询--PC端尺寸大全</h1>
分辨率   比例 | 设备尺寸<br>
1024*500 （8.9寸）<br>
<span style="color:red;">1024*768 </span>（比例4：3  | 10.4寸、12.1寸、14.1寸、15寸; ）<br>
<span style="color:red;">1280*800</span>（16：10  |15.4寸）<br>
<span style="color:red;">1280*1024</span>(比例：5：4  | 14.1寸、15.0寸)<br>
1280*854(比例：15：10 | 15.2）<br>
1366*768 (比例：16：9 | 不常见）<br>
<span style="color:red;">1440*900</span>（16：10  17寸 仅苹果用）<br>
1440*1050（比例：5：4  | 14.1寸、15.0寸）<br>
1600*1024（14：9  不常见）<br>
1600*1200 （4：3 | 15、16.1）<br>
1680*1050（16：10 | 15.4寸、20.0寸）<br>
1920*1200 (23寸）<br>
通过上面的电脑屏蔽及尺寸的例表上我们得到了几个宽度<br>
1024  1280  1366  1440  1680  1920  
<h1>CSS媒体查询--移动端尺寸断点</h1>

- @media screen and ( min-width: 212px){/*213px显示屏样式 LG Optimus One*/}
- @media screen and ( min-width: 319px){/*320px显示屏样式 苹果4/4S/5C/5S黑莓Z30 */}
- @media screen and ( min-width: 359px){/*360px显示屏样式 索尼Z1*/}
- @media screen and ( min-width: 383px){/*384px显示屏样式 黑莓Z10 谷歌 Nexus 6 LG Optimus G*/}
- @media screen and ( min-width: 399px){/*399px显示屏样式 三星galaxyNote*/}
- @media screen and ( min-width: 414px){/*414px显示屏样式 苹果6plus*/}
- @media screen and ( min-width: 423px){/*424px显示屏样式 LG 4X */}
- @media screen and ( min-width: 479px){/*480px显示屏样式 索尼MT27i Xperia sola*/}
- @media screen and ( min-width: 539px){/*640px显示屏样式 摩托罗拉Droid3/4/Razr Atrix 4g*/}
- @media screen and ( min-width: 639px){/*640px显示屏样式*/}
- @media screen and ( min-width: 640px){/*640px以上显示屏样式*/}
<h1>CSS媒体查询--开发中如何确定宽度bootstrap
</h1>
<b>最简单的方法：</b><br>
直接使用响应式做的比较的的ui框架，或者，一个大公司的标准。如<b style="color:red;">bootstrap</b>的标准<br><br>
<b style="color:red;">bootstrap</b>

- /* 超小屏幕（手机，小于 768px） */
- /* 没有任何媒体查询相关的代码，因为这在 Bootstrap 中是默认的（新版的Bootstrap 是移动设备优先） */<br><br><br>

- /* 小屏幕（平板，大于等于 768px） */
@media (min-width: @screen-sm-min) { ... }
- /* 中等屏幕（桌面显示器，大于等于 992px） */
@media (min-width: @screen-md-min) { ... }
- /* 大屏幕（大桌面显示器，大于等于 1200px） */
@media (min-width: @screen-lg-min) { ... }

<span style="color:red;">用min-width时，小的放上面大的在下面，同理如果是用max-width那么就是大的在上面，小的在下面
</span>
<h1>CSS媒体查询--开发中如何确定宽度</h1>
网易：<br>
/* media */<br>
/* 横屏 */<br>
@media screen and (orientation:landscape){

}<br><br>
/* 竖屏 */<br>
@media screen and (orientation:portrait){

}<br><br>
/* 窗口宽度<960,设计宽度=768 */<br>
@media screen and (max-width:959px){

}<br><br>
/* 窗口宽度<768,设计宽度=640 */<br>
@media screen and (max-width:767px){

}


