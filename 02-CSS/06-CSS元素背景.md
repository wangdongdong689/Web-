<h1>CSS背景概述</h1>
在当今HTML页面中，页面的背景色默认为“白色”，除了少许的表单元素及HTML5规范后才出现的一些新的“功能性”元素标签，其它元素是不具有背景色的（也可以理解为透明的）。要为页面内的元素添加漂亮的“装饰”，让页面表现得更加丰富，区别于人，除了“border”、“outline”、“box-shadow”外，“background”在里面也扮演着相当重要的角色，本章围绕“background”这个属性进行的。
<h1>背景色“background-color”</h1>
该属性可以称得上是该属性使用率最高的属性，是用于设置<span style="font-size:24px;color:#0b933b;">任何显示类型</span>（display）元素的背景颜色，可以使用的颜色为Web技术中的常用颜色模式：“颜色英文单词”、“HEX”、“RGBa”、“HSLa”。<br><br>
HTML代码部分为4个<section>标签，对应的CSS代码如下:

```
section{
    width:220px;height:140px;
    margin-right:30px;
    float:left;
    box-sizing:border-box;
}
section:nth-child(1){
    background-color:#f2e005;
    border:10px solid #5f9ade;
}
section:nth-child(3){
    background-color:#05f245;
    border:10px dotted #5f9ade;
}
section:nth-child(4){
    background-color:#0e05f2;
    border:10px double #5f9ade;
}
```
运行效果:

<img src="./images/background-color.png">
通过上例我们可以发现，“background-color”默认的颜色范围会覆盖到“border”的边界，但是这个覆盖是可以通过后面会讲到的“background-clip”分支属性进行设置的。
<h1>背景图像“background-image”</h1>
在CSS3版本发布之前“background-image”这一属性在页面的美化中可以说有着非常核心的地位，但在CSS3版本发布之后，该属性在页面美化中的比重开始下降，页面的加载速度也得到了不少的提升。但要使用CSS3或者HTML的“canvas”技术去实现复杂的图像终究比较困难，所以在很多Web应用场景中“background-image”仍然扮演着非常重要的角色。<br><br>

在实际运用的过程中需要注意的是背景图片“background-image”是可以和背景色“background-color”共存的，也就是采用一张“非矩形”的“Png图片”作为背景图片时要小心背景色带来的以外影响。<br><br>

HTML代码部分为4个< section>标签,对应的CSS代码如下：

```
section{
    width:240px;height:160px;
    margin-rigth:30px;
    float:left;
    box-sizing:border-box;
}
section:nth-child(1){
    background-iamge:url("./images/bgi-01.jpg");
    background-size:72px 72px;
}
section:nth-child(2){
    background-image:url("./images/bgi-01.jpg");
    background-size:cover;
    background-position:center center;
}
section:nth-child(3){
    background-image:url("./images/bgi-01.jpg");
    background-size:contain;
}
section:nth-child(4){
    background:url("./images/bgi-01.jpg")0 0 no-repeat,
               url("./images/bgi-02.jpg")120px 0 no-repeat,
               url("./images/bgi-03.jpg")0 80px no-repeat,
               url("./images/bgi-04.jpg")120px 80px no-repeat,
    background-szie:50% 50%;
}
```
运行效果：

<img src="./images/background-image.png">
<h1>背景图像重复“background-repeat”</h1>
当一张背景图像宽或高小于其元素容器，或用“background-size”（后面会讲到）设置宽高大小元素容器的宽高时，背景图片默认会以“平铺”的方式排满整个元素的背景，而该属性正是用于控制图像重复排列方式的，它有以下值：

- <h3 style="font-sze:16px;color:#2a90d1;">repeat</h3>
  默认。以“平铺”的方式排列图片
- <h3 style="font-sze:16px;color:#2a90d1;">repeat-x</h3>
  只在水平方向（X轴方向）进行重复
- <h3 style="font-sze:16px;color:#2a90d1;">repeat-y</h3>  
  只在垂直方向（Y轴方向）进行重复
- <h3 style="font-sze:16px;color:#2a90d1;">no-repeat</h3>   
  使背景图片不重复<br><br>
  HTML代码部分为4个< section>标签,对应的CSS代码如下：
```
section{
    width:240px;heigth:160px;
    background-image:url("./images/bgi-01.jpg");
    background-size:20% 25%;
    border:1px solid #999;
    margin-right:30px;
    float:left;
    box-sizing:border-box;
}
section:nth-child(1){
    background-repeat:repeat;
}
section:nth-child(2){
    background-repeat:repeat-x;
}
section:nth-child(3){
    background-repeat:repeat-y;
}
section:nth-child(4){
    background-repeat:no-repeat;
}
```
运行效果：

<img src="./images/background-repeat.png"> 
<h1>背景图定位“background-position”</h1>
该属性用于设置背景图片在元素内出现的位置。使用这个属性主要分为两类实际情况：第一类情况就是元素的宽高大于背景图片时，这个时候是通过“0”或“<span style="font-size:24px;color:#0b933b;">正数值</span>”去进行定位；第二类情况就是元素的宽高小于背景图片的宽高时，这个时候是通过“0”或“<span style="font-size:24px;color:#0b933b;">负数值</span>”去进行定位（这是采用 “CSS图片精灵（CSS Sprites）”技术来开发项目的时候比用的属性）。<br><br>
该属性的值有三种形式：

- <h3 style="font-sze:16px;color:#2a90d1;">方位英文单词</h3> 
   可以有“left”、“right”、“top”、“bottom”和“center”。用法如：“left top”（默认），设置背景图在元素内的“左上方”；“right bottom”，设置背景图在元素内的“右下方”；“center center”，设置背景图在元素的“中心”。  
- <h3 style="font-sze:16px;color:#2a90d1;">百分比单位</h3> 
  用法如：“0% 50%”，设置背景图在元素内“水平方向”的“左方”，垂直方向的“中心”；“50% 50%”,，设置背景图在元素内的“中心”；“100% 100%”，设置背景图在元素内的“右下方”。
- <h3 style="font-sze:16px;color:#2a90d1;">像素单位</h3> 
  背景图的“左上角”相对于元素“左上角”偏移的距离，如“10px 20px”,设置背景图“水平向右”偏移10像素，“垂直向下”偏移20像素。<br><br>
  这三种形式去设置背景图片的位置是可以“<span style="font-size:24px;color:#0b933b;">混搭</span>”的，如：“left 100%”、“50% 70px”、“top 30px”等。不过从代码规范性的角度出发，并不推荐这种“混搭”的方式。<br><br>
  这是一个定位图片位置的例子，HTML代码部分为4个< section>标签,对应的CSS代码如下：

  ```
  section{
      width:220px;height:140px;
      background-iamge:url("./images/bgi-01.jpg");
      background-repeat:no-repeat;
      background-size:50% 50%;
      border:1px solid #aaa;
      margin-right:30px;
      float:left;
  }
  section:nth-child(1){
      background-position:center bottom;
  }
  section:nth-child(2){
      background-position:100% 50%;
  }
  section:nth-child(3){
      background-position:30px 45px;
  }
  section:nth-child(4){
      background-position:50% center;
  }
  ```
  运行效果：

  <img src="./images/background-position.png"><br><br>
  这是用“CSS Sprites”进行定位的例子，HTML代码部分为:

  ```
  <form name="background-position">
       <button type="button">全部</button>
       <button type="button">普通</button>
       <button type="button">悬浮</button>
       <button type="button">点击</button>
       <button type="button" disabled>禁用</button>
       <button type="button">全效</button>
  </form>
 CSS代码如下：
 ```
 button{
     width:72px;height:32px;
     background-color:transparent;
     background-image:url("./images/bgi-05.png");
     background-repeat:no-repeat;
     border:none;outline:none;
     font:18px "微软雅黑";color:#fff;
     padding:0;
     box-sizing:content-box;
     cursor:pointer;
 }
 button:nth-child(1){
     width:144px;height:64px;
     background-posiiton:0 0;
 }
 button:nth-child(2){
     background-posiiton:0 0;
 }
 button:nth-child(3):hover{
     background-posiiton:-72px 0;
 }
 button:nth-child(4):active{
     background-posiiton:0 -32px;
 }
 button:nth-child(5):disabled{
     background-posiiton:-72px -32px;
     color:#ddd;
     cursor:not-allowed;
 }
 button:nth-child(6):hover{
     background-posiiton:-72px 0;
 }
 button:nth-child(6):active{
     background-posiiton:0 -32px;
 }
 ```
 运行结果：

 <img src="./images/background-position(1).png">
 <h1>背景图固定“background-attachment”</h1>
 通过将该属性的值设置为“<span style="font-size:24px;color:#0b933b;">fixed</span>”后，页面出现滚动条后就算页面滚动，背景图也会固定在原来的位置不会跟随页面滚动。它的默认值是“<span style="font-size:24px;color:#0b933b;">scroll</span>”，是当页面滚动的时候，背景图也跟随页面同步滚动。<br><br>
 CSS主要代码如下:

 ```
 body{
     background-image:url("./images/bgi-06.jpg");
     background-repeat:no-repeat;
     background-size:cover;
     background-position:center center;
     background-attachment:fixed;
     padding:60px 0 120px;
 }
 article{
     width:960px;height:auto;
     background-color:rgba(144,129,114,0.6);
     border-radius:15px;
     margin:0 auto;
     paddint:20px;
     text-shadow:0 1px 2px rgba(83,72,62,0.9);
     color:#fff;
 }
 article p{
     text-indent:2em;
     font:24px "楷体";
 }
 ```
 <a href="https://www.aulence.com/html-pages/css/codeEffect/code-78.html">查看本例演示效果</a>
 <h1>背景裁切范围“background-clip<img src="./images/css3_support.gif"></h1>
 该属性是规定背景显示的范围，是从“border”开始，是从“padding”开始，还是从“content”开始，它有以下值：
 
 - <h3 style="font-sze:16px;color:#2a90d1;">border-box</h3> 
   默认，背景的覆盖范围从“border”开始
- <h3 style="font-sze:16px;color:#2a90d1;">padding-box</h3> 
   背景的覆盖范围从“padding”开始
- <h3 style="font-sze:16px;color:#2a90d1;">content-box</h3> 
   背景的覆盖范围从“content”开始<br><br>
HTML代码部分为3个< section>标签,对应的CSS代码如下：

```
section{
    width:240px;height:160px;
    background-image：url("./images/bgi-01.jpg");
    background-repeat:no-repeat;
    border:15px dotted #f830ca;
    padding:15px;
    margin-right:30px;
    float:left;
    box-sizing:content-box;
}
section:nth-child(1){
    background-clip:border-box;
}
section:nth-child(2){
    background-clip:padding-box;
}
section:nth-child(3){
    background-clip:content-box;
}
```
运行效果：

<img src="./images/background-clip.png">
示例中使用了背景图片“background-image”作为演示，当背景为背景色“background-color”时该属性进行的范围裁切效果也是一样的，可以自行进行效果实践。
<h1>背景图大小“background-size<img src="./images/css3_support.gif"></h1>
该属性用于设置背景图片的大小，主要可以通过四种类型的单位设置：