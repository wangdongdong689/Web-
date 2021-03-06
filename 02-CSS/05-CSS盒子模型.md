<h1>CSS盒子模型概述</h1>
所谓盒子模型，即是将网页布局中的元素（能设置宽高的元素）进行拟物化的比喻，一个盒子是由“内容--<span style="font-size:24px;color:#0b933b;">content</span>”（盒子内的物件）、“内间距--<span style="font-size:24px;color:#0b933b;">padding</span>”（物件和盒子的距离）、“边框--<span style="font-size:24px;color:#0b933b;">border</span>”（盒子壁）、“外间距--<span style="font-size:24px;color:#0b933b;">margin</span>”（盒子和其它物体的距离）组成，如下示例图：
<img src="./images/code-css-055.jpg">
由于一些“客观”的原因，IE浏览器和标准（W3C，其它主流浏览器）的盒子模型有一定的差异，即IE浏览器的尺寸（“width”和“height”）包含了conent、padding和border；标准的盒子模型只包含content。一方面为为了兼容IE浏览器，另一方面是IE的盒子模型在实际的布局中的确更容易控制。所以我们在实际的开发工作中，都是将标准的盒子模型转换为IE的盒子模型。转换方式是将CSS的样式属性<span style="font-size:24px;color:#0b933b;">“box-sizing”<img src="./images/css3_support.gif"></span>的值设为<span style="font-size:24px;color:#0b933b;">“border-box”</span>。当然，如果我们要将IE的盒子模型转化为标准的盒子模型也是可行的，即将“box-sizing”的值设置为“cotent-box”，不过业界并不推崇这样做。我们可以自己动手制作一个简单的页面实例进行对比。
<h1>元素宽度“width”</h1>
该属性用于设置元素的宽度，但通过该属性设置的宽度有的时候未必就是元素真实的宽度。通过设置“width”的宽度，在<span style="font-size:24px;color:#0b933b;">IE标准的盒子模型</span>中，宽度是由“<span style="font-size:24px;color:#0b933b;">content+padding+border</span>”组成的，也就是说在IE标准的盒子模型中，设置“width”的时候是无需考虑“padding”和“border”的（这需在这两个属性的值都不大的时候）。而在标准的盒子模型中，宽度只包含“conent”，元素自带的，和人为设置的“padding”和“border”都会额外的增加元素的宽度。<br><br>
在HTML中具有盒子模型属性的显示类型有“块元素（block）”和“行内块(inline-block)”。<br><br>
“width”属性最常用的两种设置方式为“<span style="font-size:24px;color:#0b933b;">像素（px）</span>"设置和"<span style="font-size:24px;color:#0b933b;">百分比（%）</span>"设置。他们的特点如下：<br><br>

- <h3 style="font-sze:16px;color:#2a90d1;">像素设置</h3>
  优点：该方式去设置宽度更为的稳定，也就是说当一个元素是通过像素去设置元素宽度的时候，该元素的内容，特别是用像素去设置的文本内容也相对稳定，不会因为设备分辨率的不同而在排版显示上有所不同。<br><br>
  缺点：在不同设备上，需要对元素宽度进行修改才能得到最佳的布局效果。如一个在PC端宽度为“960像素”的元素，在手机端就会出现右半部分，甚至右大半部分的显示都会被裁切的情况（如“iphone 4”的浏览器显示分辨率为“320*480”）。
- <h3 style="font-sze:16px;color:#2a90d1;">百分比设置</h3>
  优点：能对不同显示分辨率做出更好的适应。最外层的标签元素（<body>的子节点）若宽度设为“100%”，那无论是在具有“<span style="font-size:24px;color:#0b933b;">4K</span>”显示分辨率的高清投影大屏幕上，还是在分辨率在几百像素的移动设备上，都能横向占满整个屏幕。现在有人将“百分比布局”称作“流式布局”，是一种应对“移动浪潮”布局的新趋势。<br><br>
  缺点：若采用百分比布局的方式，很多因素难以控制，如采用默认大小的表单元素，HTML5的功能标签，都会给这种布局方式带来麻烦,若是采用多列布局的页面，这种布局方式在移动端上的效果绝对是“灾难性”的。特别是对于缺乏前端开发经验的开发人员而言，这种布局方式经常会出现一些布局效果在意料之外的情况。<br><br>
  百分比设置的布局有一个“相对性”的特点，也就是它的百分比是对于父级元素而言的，“width”利用百分比宽度来布局的原理，如下例：<br><br>
HTML代码如下：

  ```
  <section>
        <div>
            <p></p>
            <p></p>
        </div>
  </section>
  ```
CSS代码如下：

```
    section, div, p {
            box-sizing: border-box;
        }
        section {
            width: 90%; height: 480px;
            background-color: #d38888;
            margin: 0 auto;
            padding-top: 50px;
        }
        div {
            width: 90%; height: 380px;
            background-color: #c2d388;
            margin: 0 auto;
            padding-top: 50px;
        }
        p:first-child {
            width: 90%; height: 130px;
            background-color: #8b88d3;
            margin: 10px auto;
        }
        p:last-child {
            width: 10%; height: 130px;
            background-color: #4dbc5e;
            margin: 10px auto;
        }
```
运行效果：

<img src="./images/width.png">
<h1>元素高度“height”</h1>
该属性的作用是用于设置“块级元素”和“行内块元素”的<span style="font-size:24px;color:#0b933b;">高度</span>，它绝大部分特征、度量单位和盒子模型的计算方式基本上和“width”属性一样。但在CSS的领域里，垂直方向的一些属性总是会出现一些让人“费解”的问题，如垂直居中的属性"<a href="javascript:;">vertical-align</a>","<a href="javascript:;" >margin-top和margin-bottom</a>"的重叠，<a href="javascript:;">页面内“块级元素”的首个子元素</a>（如：div > p:first-child）在执行“margin-top”时会让父元素去执行该属性，而对于它的最后一个子元素则不会产生这种情况，等等一系列的问题。<br><br>
“width”属性的表现和“height”属性的差异在于，在同样不设置<html>或<body>宽高的条件下，任意“块级元素”和“行内块级元素”在不考虑盒子模型的前提下使用“widht”属性设置百分比（%）单位都能达到预期的效果，而<a href="javascript:;">“height”则不然</a>除非对设置了“height”属性的父级元素设置“height”属性，否则无论用多少的百分比去设置元素的高度，该元素的高度都始终为“0”。
<h1>外间距“margin”</h1>
“margin”我们称他为外间距，是一个<span style="font-size:24px;color:#0b933b;">具有宽高</span>样式属性的元素（即通常的“行内块元素”和“块元素”）相对于<span style="font-size:24px;color:#0b933b;">同级元素</span>和<span style="font-size:24px;color:#0b933b;">父级元素</span>的一个距离值，常用单位像素“px”。该属性对文本类元素（即“行内元素”）标签是无效的。<br><br>
“margin”属性有四个分支属性，如下：

- <h3 style="font-sze:16px;color:#2a90d1;">margin-top</h3>
   距离上方同级元素在垂直方向的距离，若上方元素含有“margin-bottom”，则会<span style="font-size:24px;color:#0b933b;">重叠该值</span>，并且<span style="font-size:24px;color:#0b933b;">取较大值</span>作为间距值。<br><br>
   若该元素为父元素内的首个子元素，则是设置父元素距离上方元素的距离，若上方元素含有“margin-bottom”，则同样会重叠该值，取较大值作为间距值。
- <h3 style="font-sze:16px;color:#2a90d1;">margin-right</h3>
    距离父级元素右边框的距离，若父元素有内间距“padding-right”,则还需要加上该值。<br><br>
    距离右方同级元素在水平方向的距离，若右方元素含有“margin-left”，则会和该值相加，取两个元素之间间距值的<span style="font-size:24px;color:#0b933b;">和</span>作为间距值。
- <h3 style="font-sze:16px;color:#2a90d1;">margin-bottom</h3>
  距离下方同级元素在垂直方向的距离，若下方元素含有“margin-top”，则会<span style="font-size:24px;color:#0b933b;">重叠该值</span>，并且<span style="font-size:24px;color:#0b933b;">取较大值</span>作为间距值。若该元素是DOM内最后一个元素，则相当于是给父元素设置了一个下间距（padding-bottom），若父元素已经设置了“padding-bottom”，则与父元素的该值相加取<span style="font-size:24px;color:#0b933b;">和</span>作为与页面底部的间距。
- <h3 style="font-sze:16px;color:#2a90d1;">margin-left</h3>
   距离父级元素左边框的距离，若父元素有内间距“padding-left”,则还需要加上该值。<br><br>
   距离左方同级元素在水平方向的距离，若左方元素含有“margin-right”，则会和该值相加，取两个元素之间间距值的<span style="font-size:24px;color:#0b933b;">和</span>作为间距值。<br><br>
   如果我们在一个元素需要在多个方向进行设置外间距的时候，如果将“margin”多个方向的属性都设置一遍，难免会让代码看起来比较繁杂，增加了不少代码量，也增加了维护的难度。这个时候我们可以将“margin”四个方向的值“合四为一”，写法如下：

- <h3 style="font-sze:16px;color:#2a90d1;">margin：10px;</h3>
  即将“margin”四个方向的值“margin-top”、“margin-right”、“margin-bottom”和“margin-left”都设置为10像素。
- <h3 style="font-sze:16px;color:#2a90d1;">margin: 10px 15px;</h3>
  即将“margin”垂直方向的值“margin-top”和“margin-bottom”设置为10像素，水平方向的值“margin-left”和“margin-right”都设置为15像素。
 - <h3 style="font-sze:16px;color:#2a90d1;">margin: 10px 15px 20px;</h3> 
   即将“margin”距离上方“margin-top”的值设为10像素，水平方向的值“margin-left”和“margin-right”都设置为15像素，距离下方的“margin-bottom”的值设为20像素
 - <h3 style="font-sze:16px;color:#2a90d1;">margin: 10px 15px 20px 25px;</h3> 
   即将“margin”分别对应的“margin-top”，“margin-right”，“margin-bottom”，“margin-left”的值设为10像素，15像素，20像素和25像素。<br><br>
   通过对上面“margin”值的设置我们可以发现，在该属性设置三个值的时候是没有同时设置垂直方向，又分别设置左右方向的写法的，这点在以后使用中要注意。<br><br>
   利用“margin”多值设置的方法，我们还产生了一种<span style="font-size:24px;color:#0b933b;">设计模式</span>，即将“margin”的值设为“<span style="font-size:24px;color:#0b933b;">0 auto</span>”，可以让一个“块元素”在页面中水平居中。这里也需要注意的是，虽然“margin”四个方向的属性对“行内块元素”是有效的，但这水平居中的设计模式对于它来说是无效的。要让“行内块元素”执行水平居中就要涉及到我们另外一种设计模式了，即“绝对定位+负外边距”的用法。在CSS显示与定位中会讲到。
   <h1>内间距"padding"</h1>
   “padding”我们称他为内间距，是一个具有宽高样式属性的元素相对于<span style="font-size:24px;color:#0b933b;">自身元素的内容</span>的一个距离值，常用单位像素“px”。该属性对文本类元素（即"行内元素"）标签是无效的。在“标准（W3C）的盒子模型”中，“padding”的值会占据除“width”和“height”所设置值的额外宽高空间，而在“IE盒子模型”中，“padding”所设置的值不会增加元素的宽和高，但会<span style="font-size:24px;color:#0b933b;">向内</span>占据空间。<br><br>
   HTML代码示例：

   ```
   <div>这个是标准的盒子模型，这个是标准的盒子模型，这个是标准的盒子模型，这个是标准的格子模型，这个是标准的盒子模型，这个是标准的盒子模型，这个是标准的盒子模型，这个是标准的盒子模型...</div>
   <div>这个是IE的盒子模型，这个是IE的盒子模型，这个是IE的盒子模型，这个是IE的盒子模型，这个是IE的盒子模型，这个是IE的盒子模型...</div>
   ```
   对应的CSS代码如下：
   ```
   div{
       width:320px;
       height:200px;
       font:22px "微软雅黑";
       color:#fff;
       margin-left:100px;
       float:left;
   }
   div:first-child{
       background-color:#095eb4;
       padding:20px;
       box-sizing:contnet-box;
   }
   div:last-of-type{
       background-color:#0db427;
       padding:20px;
       box-sizing:border-box;
   }
   ```
   运行效果：

   <img src="./images/padding.png">
   “padding”属性的值设置相对于“margin”来说需要考虑的额外因素更少（除了对设置了“background-origin”属性为“conent-box”的元素来说，后面会讲到），它的设置的值在垂直方向也不会出现任何“预料外”的情况，它有四种分支属性，如下：

 - <h3 style="font-sze:16px;color:#2a90d1;">padding-top</h3>
   设置该元素的边界与<span style="font-size:24px;color:#0b933b;">自身的内容在上方的间距</span>。
- <h3 style="font-sze:16px;color:#2a90d1;">padding-right</h3>
  设置该元素的边界与<span style="font-size:24px;color:#0b933b;">自身的内容在右方的间距</span>。
- <h3 style="font-sze:16px;color:#2a90d1;">padding-bottom</h3>
  设置该元素的边界与<span style="font-size:24px;color:#0b933b;">自身的内容在下方的间距</span>。
- <h3 style="font-sze:16px;color:#2a90d1;">padding-left</h3>
  设置该元素的边界与<span style="font-size:24px;color:#0b933b;">自身的内容在左方的间距</span>。<br>
和"margin"一样"padding"属性的值也有组合起来写的用法，如下：
- <h3 style="font-sze:16px;color:#2a90d1;">padding：10px;</h3>
  即将元素边界与内容四个方向“padding-top”、“padding-right”、“padding-bottom”和“padding-left”的间距都设置为10像素。
- <h3 style="font-sze:16px;color:#2a90d1;">padding：10px 12px;</h3>
  将元素边界与内容上下两个方向“padding-top”、“padding-bottom”的间距都设置为10像素,与内容左右两个方向“padding-left”和“padding-right”的间距都设置为12像素。
- <h3 style="font-sze:16px;color:#2a90d1;">padding：10px 12px 15px;</h3>
  即将元素边界与内容上方“padding-top”的间距设置为10像素，与内容左右两个方向“padding-left”和“padding-right”的间距都设置为12像素，与内容下方“padding-top”的间距设置为15像素。<br><br>
  与“margin”一样，“padding”属性在设置三个值的时候是没有同时设置垂直方向，又分别设置左右方向的写法的。若要进行这样的设置，请使用四个值的设置方式去进行设置，即将垂直方向（第一个和第三个）的值设为一样，再分别去设置水平方向（第二个和第四个）的值。<br><br>
  在“IE盒子模型”下运用“padding”需要特别注意的是，“padding”的值会占据内容的空间。如在一个高度为“50像素”，“padding-top”和“padding-bottom”均为“10像素”的“行内块”或“块级”元素内，给文本内容设置行高“line-height:50px”并不会达到垂直居中的效果，而要将文本元素的行高设置为“height-(padding-top+padding-bottom)=<span style="font-size:24px;color:#0b933b;">innerHeight</span>在JavaScript中“innerHeight”表示内容的高度，“outerHeight”表示元素实际占据的高度）”，即“50-(10+10)=30”才能达到文本在该元素内垂直居中的效果。

<!-- <章节练习（一）将以下带标注的图形在代码编辑器内进行编写，并在浏览器呈现：

1、“#fdffc1”色的部分为<body>的背景色，“#eb9bee”色部分为一个<section>标签，宽为“960像素”，高为“560像素”，内部<p>标签的宽高根据已提供数值进行计算得出；

2、“#5e98ee”色是两个<p>标签的“内间距”（该标签的背景色），里面的“#4adf2d”色不用表示出来，它表示该标签的“内容”，第一个<p>标签的内容用任意一段大于一行的文本填充即可（方便查看“内间距”值是否生效），第二个<p>标签的文本内容和第一个<span>标签内的一致，但不换行，超出的部分用“省略号”代替（必须要使用“text-overflow”进行裁切），并在该元素内垂直居中。 <img src="./images/width+height+margin+padding.jpg">-->
<h1>元素边框“border”</h1>
该属性的作用是为设定该属性的元素添加边框。在“标准盒子模型”中，该属性的分支属性“border-width”所设置的值会增加元素的实际宽度和高度，而在“IE盒子模型中”该属性的分支属性“border-width”所设置的值会和“padding”（若设置或标签自带该属性）共同占据内容的空间。该属性能对任何显示类型的元素设置，包括“行级元素（inline）”。<br><br>
“border”属性有三个分支属性：

- <h3 style="font-sze:16px;color:#2a90d1;">border-width</h3>
设定边框的宽度。可以为Web技术中常用的度量单位，通常为像素“px”。<br><br>
HTML代码部分为3个“< div>”标签，对应的CSS代码如下：

```
div{
    width:200px;height:100px;
    border-style:solid;
    border-color:#333;
    margin-right:50px;
    float:left;
}
div:nth-child(1){
    border-width:1px;
}
div:nth-child(2){
    border-width:5px;
}
div:nth-child(3){
    border-width:10px;
}
```
运行效果：

<img src="./images/border.png">

- <h3 style="font-sze:16px;color:#2a90d1;">border-style</h3>
设置边框的类型，主要有以下可以设定的值：

- none，无边框
- solid，实现边框
- dotted，点线边框
- dashed,虚线边框
- double，双线边框
- groove，3D凹槽边框
- ridge，3D吐槽边框
- indet，内浮雕边框
- outset，外浮雕边框

HTML代码部分为9个带文本的“< div>”标签，对应的CSS代码如下：

```
div{
    width:200px;height:100px;
    background-color:#ff0;
    border-width:10px;
    border-color:#888;
    margin-right:50px;margin-bottom:20px;
    box-sizing:border-box;
    text-align:center;
    float:left;
}
div:nth-child(1){
    border-style:none;
    line-height:100px;
}
```
div:nth-child(2){border-style:solid;}
div:nth-child(3){border-style:dotted;}
div:nth-child(4){border-style:dashed;}
div:nth-child(5){border-style:double;}
div:nth-child(6){border-style:groove;}
div:nth-child(7){border-style:ridge;}
div:nth-child(8){border-style:inset;}
div:nth-child(9){border-style:outset;}

运行效果：

<img src="./images/border-style.png">

- <h3 style="font-sze:16px;color:#2a90d1;">border-color</h3>
设置边框的颜色，可以是Web技术中常规的四种颜色值“英文单词”、“HEX”、“RGBa”和“HSLa”。<br><br>
HTML代码部分为4个带文本的“< div>”标签，对应的CSS代码如下：

```
div{
    width:200px;height:100px;
    border-width:10px;
    border-style:solid;
    margin-right:30px;
    box-sizing:border-box;
    font:22px/80px "微软雅黑";
    text-align:center;
    float:left;
}
div:nth-child(1){border-color:red;}
div:nth-child(2){border-color:#ff0;}
div:nth-child(3){border-color:rgb(0,0,255);}
div:nth-child(4){border-color:hsl(120,100%,50%);}
```

运行效果：

<img src="./images/border-color.png">
当然“border”属性的各个分支属性也能单独地对某个方向上的值进行设置。HTML代码部分为3个“< div>”标签，对应的CSS代码如下：

```
div{
    width:220px;height:140px;
    margin-right:30px;
    box-sizing:border-box;
    float-left;
}
div:nth-child(1){
    border-top-width:5px;
    border-right-width:10px;
    border-bottom-width:15px;
    border-left:20px;
    border-style:solid;
    border-color:#3559bc;
}
div:nth-child(2){
    border-width:10px;
    border-top-style:solid;
    border-right-style:dotted;
    border-bottom-style:dashed;    
    border-left-style:none;
    border-color:#59a70c;
}
div:nth-child(3){
    border-width:10px;
    border-style:solid;
    border-top-color:#418ce3;
    border-right-color:#a70c83;
    border-bottom-color:#ebbb19;
    border-left-color:#95704c;
}
```

运行效果：

<img src="./images/boder-color1.png"><br><br>
“border”属性也有组合值的写法，该写法也是最常使用的方式。HTML代码部分为4个“< div>”标签，对应的CSS代码如下：

```
div{
    width:180px;height:120px;
    margin-right:30px;
    box-sizing:border-box;
    float-left;
}
div:nth-child(1){
    border:10px solid #a03838;
}
div:nth-child(2){
    border-width:20px 15px 10px 5px;
    border-style:solid;
    border-color:#248924;
}
div:nth-child(3){
    border-width:10px;
    border-style:solid none dashed ridge;
    border-color:#243f89;
}
div:nth-child(4){
    border-wdith:10px;
    border-style:solid;
    border-color:#892466 #ffa700 #56e30b #25bfbf;
}
```
运行效果：

<img src="./images/border-color（1）.png"><br><br>
除此之外，“border”还有一个很有趣的“玩”法，就是通过将元素的宽高都设为“0”，然后设置“border”的各分支属性的值将它作为一个“形状”来使用。我们来看这样一个例子：

```
div{
    width:0;height:0;
    margin-right:30px;
    box-sizing:border-box;
    float:left;
}
div:nth-child(1){
    border-width:20px 45px 20px 45px;
    border-style:solid;
    border-color:transparent #d6530d transparent #d6530d;
}
div:nth-child(2){
    border-width:30px 45px 30px 45px;
    border-style:ridge;
    border-color:#0dd690 transparent #0dd690 transparent;
}
div:nth-child(3){
    border-width:90px 45px 45px;
    border-style:double;
    border-color:#543fc7 transparent transparent transparent; 
}
div:nth-child(4){
    border-width:30px 60px 30px 60px;
    border-style:ridge;
    border-color:transparent transpraent #e2187d #e2187d;
}
```
运行效果：

<img src="./images/border-style(1).png">

<!-- 设法用“border”属性将下面的图像在代码编辑器内实现，并在浏览器呈现：

1、图形的颜色按照图示设定；

2、图形的大小、倾斜角度均不限，只要图形相似即可；

3、禁止使用CSS3的“transform”属性。

<提示>

每个图形可以由多个元素组合，并妥善利用“float”属性及它的值“left”。
<img src="./images/layout-02.jpg"> -->

<h1>圆角的盒子“border-radius”<img src="./images/css3_support.gif"></h1>
该属性虽然带了一个“border”字样，同样也是用来设置元素的边界，但它和“border”并无太大的关系，它是对元素的“左上”、“右上”、“右下”和“左下”四个角的“圆度”进行设置。该属性能对任何显示类型的元素设置，包括“行级元素（inline）”。<br><br>
HTML部分为为4个等宽高的< div>标签，对应的CSS代码如下：

```
div{
    width:200px;height:100px;
    margin-right:50px;
    float:left;
}
div:nth-child(1){
    background-color:#89051e;
    border-radius:30px;
}
div:nth-child(2){
    background-color:#248905;
    border-radius:50px;
}
div:nth-child(3){
    background-color:#053889;
    border-radius:200px/100px;
}
div:nth-child(4){
    background-color:#b20cc7;
    border-radius:50%;
}
```
运行效果：

<img src="./images/border-radius.png">

“border-radius”实现的原理是根据该属性所设置的值，在元素内建立一个以该值为半径的“<span style="font-size:24px;color:#0b933b;">看不见的圆</span>”，并以该圆的边缘形状来设置边角的圆度。<br><br>
上例中“第三个< div>”中有两个值，并用“/”符号进行分割，第一个值表示<span style="font-size:24px;color:#0b933b;">水平方向</span>圆的半径，第二个表示<span style="font-size:24px;color:#0b933b;">垂直方向</span>圆的半径。<br><br>
上例中“第四< div>”中采用的是百分比，它表示在“水平方向”设置为“width”属性50%的值，在“垂直方向”也设置为“height”属性50%的值来绘制一个“看不见的圆”来表示四个角的圆度，若对“border-radius”的值用“百分比单位”进行统一设置（即不对四个角分别进行设置的情况，这在后面会讲到），那它的上限值就是“50%”，会呈现出一个“正圆（元素的宽高相等）”或“椭圆（元素的宽高不相等）”，在此基础上再增加这个值不会看到任何变化。<br><br>
“border-radius”属性除了能统一对元素的边角进行设置，还能分别对一个矩形元素的四个角分别进行设置，如：

```
div{
    width:200px;height:100px;
    margin-right:50px;
    float:left;
}
div:nth-child(1){
    background-color:#ffba00;
    border-top-left-radius:100px;
    border-bottom-right-radius:50px;
    border-bottom-left-radius:30px;
}
div:nth-child(2){
    background-color:#1bc2ff;
    border-bottom-left-radius:150%;
    border-top-right-radius:150%;
}
div:nth-child(3){
    background-color:#ed64b3;
    border-top-right-radius:50%;
    border-bottom-right-radius:50%;
}
```
运行结果：

<img src="./images/border-radius（1）.png"><br><br>
但在进行“border-radius”四个角分别设置的时候需要注意一个要点，就是设置方向一定要先是“top”或“bottom”方向，再是“left”或“right”方向，否则不能达到预期的效果。可以使用百分比单位（包括超过“50%”的百分比单位，超过150%后会将不再对选择的边角进行影响，而是对选择边角的“对角”进行影响了，这个值没有最大值，也就是一个无穷大的值，会让“对角”无限趋向一个“直角”，即让“对角”趋向一个没有设置过“border-radius”的边角的样式），但不能使用如“180px/90px”值的形式，否则该段CSS属性无效。<br><br>
关于“border”和“border-radius”属性配合“CSS3”中新属性的更多“有趣”的玩法可以参照<a href="https://jingyan.baidu.com/article/e52e36154226ef40c70c5148.html">这个例子</a>。
<h1>元素的轮廓“outline”</h1>
该属性用于设置一个元素的轮廓线，和“border”不一样，“outline”无论在什么“盒子模型”下，都不会占据页面的空间，并且它不能分别去设置各个方向的值，即不能对“top”、“right”、“bottom”和“left”方向的“outline”进行分别设置，只能进行<span style="font-size:24px;color:#0b933b;">统一设置</span>。在使用“<span style="font-size:24px;color:#0b933b;">webkit</span>（老版本Chrome浏览器、Safari浏览器以及iOS和Android系统自带浏览器）”内核或“<span style="font-size:24px;color:#0b933b;">blink</span>（以新版的Chrome浏览器和Opera浏览器为代表）”内核的浏览器中，该属性会在表单元素在获得焦点后自动出现，本意是让用户获得更好的交互体验，但该设定很多时候反而会影响我们对“Web”页面的风格设置，这个时候我们都是将它的值设置为“none”。另外，“outline”属性并不受圆角属性“border-radius”的影响。<br><br>
和“border”属性大体一致，“outline”有以下分支属性：

- <h3 style="font-sze:16px;color:#2a90d1;">outline-width</h3>
   设置轮廓线的宽度，能为Web技术中常用的度量单位，最常用的为像素“px”。
- <h3 style="font-sze:16px;color:#2a90d1;">outline-style</h3>
   设置轮廓线的样式，和“border-style”一致。
- <h3 style="font-sze:16px;color:#2a90d1;">outline-color</h3>
  设置轮廓线的颜色，和“border-color”一样支持Web的四种“颜色模式”。
- <h3 style="font-sze:16px;color:#2a90d1;">outline-offset<img src="./images/css3_support.gif"></h3>
  设置轮廓线相对元素边界的距离，通常以像素“px”为单位。<br><br>
HTML代码内容为：

```
<section>
   <div></div>
   <div></div>
   <div></div>
   <div></div>
</section>
```
CSS代码如下：
```
section{
    margin-left:20px;
    margin-top:20px;
}
div{
    width:220px;height:140px;
    background-color:#f5ff00;
    float:left;
    border-radius:50%;
}
div:nth-child(1){
    outline:15px solid #af3535;
}
div:nth-child(2){
    outline:20px dotted #53br3a;
}
div:nth-child(3){
    outline:10px dashed #3c5aa8;
}
div:nth-child(4){
    margin-top:0px;
    margin-left:50px;
    outline:10px ridge #c339bd;
    outline-offset:10px;
}
```
运行效果：

<img src="./images/outline.png">
<h1>可调整元素大小的“resize”<img src="./images/css3_support.gif"></h1>

该属性是用于定义“块级元素”的大小是否可以调整、以何种方式（水平方向还是垂直方向）调整，该属性需要配合属性值为“auto”、“hidden ”或“scroll”的“<span style="font-size:24px;color:#0b933b;">overflow</span>”属性使用，但被调整大小的元素的宽和高不能小于它原始的宽和高。另外，“resize”属性有个特别案例，就是能够对表单元素< textarea>使用，并且无需显示的去设置“overflow”属性。<br><br>
讲到“resize”这个属性，不得不提到四个新的属性，“<span style="font-size:24px;color:#0b933b;">max-width</span>"和"<span style="font-size:24px;color:#0b933b;">max-height</span>",它们分别表示元素允许的“<span style="font-size:24px;color:#0b933b;">最大宽度</span>”和“<span style="font-size:24px;color:#0b933b;">最大高度</span>”，与之对应的是“<span style="font-size:24px;color:#0b933b;">min-width</span>”和“min-height”,它们分别表示元素允许的“<span style="font-size:24px;color:#0b933b;">最小宽度</span>”和“<span style="font-size:24px;color:#0b933b;">最小高度</span>”。这四个属性除了在"resize"中运用比较多，在限制< table>单元格的宽高也非常实用。<br><br>
HTML代码内容为：

```
<section>resize:both</section>
<section>resize:borizontal</section>
<section>resize:vertical</section>
<section>限制的resize:both</section>
<textarea placeholder="我是文本域"></textarea>
```
CSS代码如下：
```
section,textarea{
    width:180px;height:120px;
    border:1px solid #666;
    float:left;
    margin-left:50px;
    box-sizing:border-box;
}
section:nth-child(1){
    resize:both;
    overflow:auto;
}
section:nth-child(2){
    resize:horizontal;
    overflow:auto;
}
section:nth-child(3){
    resize:vertical;
    overflow:auto;
}
section:nth-child(4){
    max-width:220px;
    max-height:180px;
    resize:both;
    overflow:auto;
}
textarea{
    resize:none;
}
```
运行效果：

<img src="./images/resize.png">
<h1>元素的阴影“box-shadow<img src="./images/css3_support.gif">”</h1>
该属性能够让元素获得一个“<span style="font-size:24px;color:#0b933b;">阴影</span>”效果，根据颜色的不同，有时候也可以叫做“<span style="font-size:24px;color:#0b933b;">发光</span>”效果。“box-shadow”属性没有分支属性，它的值是以“组合值”的形式设置的，它最多允许<span style="font-size:24px;color:#0b933b;">6个值</span>的组合，按值的顺序分别代表：

- <h3 style="font-sze:16px;color:#2a90d1;">h-skewing（必要）</h3>
  阴影在水平方向的偏移，负数是向左偏移，正数是向右偏移，单位为“px”。
- <h3 style="font-sze:16px;color:#2a90d1;">v-skewing（必要）</h3>
  阴影在垂直方向的偏移，负数是向上偏移，正数是向下偏移，单位为“px”。
- <h3 style="font-sze:16px;color:#2a90d1;">blur（可选）</h3>
  阴影的“模糊距离”或“模糊程度”，单位为“px”。
- <h3 style="font-sze:16px;color:#2a90d1;">spread（可选）</h3> 
  阴影的扩展范围，若将“blur”设为“0”，该值则相当于一个可以进行位置偏移但不具备“outline-offset”的“outline”，单位为“px”。
 - <h3 style="font-sze:16px;color:#2a90d1;">color（可选）</h3>  
   阴影的颜色，支持Web技术中的常用颜色模式：“颜色英文单词”、“HEX”、“RGBa”、“HSLa”。
  - <h3 style="font-sze:16px;color:#2a90d1;">inset（可选）</h3>   
   将默认向外的阴影方向改为<span style="font-size:24px;color:#0b933b;">向内</span>。<br><br>
HTML代码内容为4个左浮动的< section>标签，对应的CSS代码如下：

```
body{
    padding:20px;
}
section{
    width:220px;height:140px;
    border:1px solid #ddd;
    border-radius:30px;
    float:left;
    margin-right:30px;
}
section:nth-child(1){
    box-shadow:-10px -10px 15px #999;
}
section:nth-child(2){
    box-shadow:0 10px 8px rgba(111,137,208,0.9);
}
section:nth-child(3){
    box-shadow:5px 0 0 10px hsla(275,44%,48%,0.92);
}
section:nth-child(4){
    box-shadow:8px 6px 16px #3e3f55 inset;
}
```
运行效果：

<img src="./images/box-shadow.png">

“box-shadow”还能设置<span style="font-size:24px;color:#0b933b;">多组值</span>，每组值用英文","进行分割，可以让元素发出“多彩的光芒”。对应的CSS代码如下：

```
section{
    width:220px;height:140px;
    border:1px solid #ddd;
    text-align:center;
    font:24px/140px "微软雅黑";
    border-radius:30px;
    float:left;
    margin-right:30px;
    box-shadow:-15px -15px 10px rgba(234,22,22,0.8),
    0 -10px 10px rgba(237,164,25,0.8),
    15px -15px 10px rgba(147,237,25,0.8),
    10px 0 10px rgba(25,237,180,0.8),
    15px 15px 10px rgba(25,66,237,0.8),
    0 10px 10px rgba(25,49,237,0.8),
    -15px 15px 10px rgba(107,25,237,0.8),
    -10px 0 10px rgba(224,35,202,0.8);
}
```
运行效果：

<img src="./images/box-shadow（1）.png">

<!-- <章节练习（三）>
用CSS代码制作一个在四个方向发出不同“光芒”的元素，并在浏览器端呈现，要求如下：

1、元素的宽为“240像素”，高度为“180像素”；

2、四个方向分别是元素的“左上角”、“右上角”、“右下角”和“左下角”；

3、无论是水平方向还是在垂直方向偏移值都为30像素；

4、颜色分别是“rgba(235, 21, 21, 0.75)”、“rgba(202, 235, 21, 0.75)”、“rgba(21, 235, 103, 0.75)”和“rgba(21, 87, 235, 0.75)”；

5、元素内部有个不进行任何方向偏移，模糊距离20像素的“内发光”效果，颜色为“rgba(219, 21, 235, 0.75)”；

6、让该元素在浏览器中水平和垂直方向都居中。

<友情提示>

为了让“box-shadow”的多组值结构更加地清晰，建议在每组值设置完成并加上“,”号之后手动进行一次换行。 -->

