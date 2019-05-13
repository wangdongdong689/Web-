<h1>CSS高级选择器概述</h1>
CSS高级选择器区别于CSS普通选择器，它并非是通过HTML页面标签中一些可见的因素进行选择（如标签名，属性名、值，同级关系，嵌套结构等），也不是对一些简单的操作条件进行选择（如鼠标悬浮，鼠标点击，输入框获得焦点等），而是对标签元素的结构、标签元素的索引、标签元素的状态等一些更为复杂的条件下进行的选择，甚至能改变现有标签的状态结构。<br><br>
很多CSS高级选择器都是在CSS3标准后诞生的，它们出现一方面让标签的选择更加的简便精准，一方面又让HTML的DOM结构更加清晰，顺应了标签结构语义化，可读性更强的趋势，同时也使得搜索引擎能更好的检索到我们所开发的网站（SEO）。能正确灵活地运用CSS的高级选择器，不仅能让我们开发的网站功能更加地强大，表现更加地“绚丽”，还能更大程度地增加用户的体验度，让我们开发的网站在用户心目中留下一个深刻的好印象。
<h2 style="color:#11278a;">伪元素选择器<img src="./images/css3_support.gif"></h2>
该类选择器主要用于向指定的<span style="color:#0b933b;font-size:24px;">选择器</span>添加指定的效果，该类选择器会<span style="color:#0b933b;font-size:24px;">增加“1”的权重</span>，主要有四个伪元素：
<h3 style="color:#2a90d1;">:first-letter</h3>
选择“块级元素”文本段落中的首个字符，只能对“块级元素”生效。<br><br>
该选择器可以设置的值有：<br><br>

- font属性
- color属性
- background属性
- margin属性
- padding属性
- border属性
- text-decoration属性
- vertical-align属性
- text-transform属性
- line-height属性
- float属性
- clear属性

HTML代码示例：

```
<article>
   <p class="firstLetter">天将降大任于是人也，必先苦其心志，劳其筋骨，饿其体肤，空伐其身行，行弗乱其所为，所以动心忍性，曾益其所不能。</p>
</article>
```
CSS代码如下：

```
<!-- 伪元素选择器--首字选择 -->
.firstLetter:first-letter{
    padding:4px;
    border:2px solid #all;
    color:#all;
    font:24px "微软雅黑";
    margin:2px 4px 0 2px;
}
```
运行效果：

<img src="./images/first-letter.png">
<h3 style="color:#2a90d1;">:first-line</h3>
选择“块级元素”文本段落中的首行文本，只能对“块级元素”生效。<br><br>
该选择器可以设置的值有：<br><br>

- font属性
- color属性
- background属性
- word-spacing属性
- letter-spacing属性
- text-decoration属性
- vertical-align属性
- text-transform属性
- line-height属性
- clear属性

HTML代码示例：

```
<article>
   <p class="firstLine">天将降大任于是人也，必先苦其心志，劳其筋骨，饿其体肤，空伐其身行，行弗乱其所为，所以动心忍性，曾益其所不能。</p>
</article>
```
CSS代码如下：

```
<!-- 伪元素选择器--首行选择 -->
.firstLine:first-line{
    font:28px/42px "微软雅黑";
    color:#4e5221;
    letter-spacing:8px;
}
```
运行效果：

<img src="./images/first-line.png">
<h3 style="color:#2a90d1;">:before</h3>
在指定的选择器之前插入一段内容。插入的内容默认为“行内元素”，可以通过“display”强制装换显示类型。<br><br>
HTML代码示例：

```
<article>
    <p class="addBefore-1">这是正文文本</p>
    <p class="addBefore-2">这是正文文本</p>
    <p class="addBefore-3">这是正文文本</p>
</article>
```
CSS代码如下：

```
<!-- 伪元素选择器--元素之前添加 -->
.addBefore-1:before{
    content:url("./images/onepiece-1.png");
     width: 24px; height: 24px;
}
.addBefore-2:before {
            content: url("./images/onepiece-1.png");
            width: 0px;
            display: inline-block;
        }
.addBefore-3:before {
            content: "好像";
            border: 1px solid #f80;
            font: 24px "微软雅黑";
            color: #f80;
            display: inline-block;
            position: relative;
            top: -4px;
            margin-right: 5px;
        }
```
运行效果：

<img src="./images/before.png">
<h3 style="color:#2a90d1;">:after</h3>
在指定的选择器之后插入一段内容，使用方式和“:before”一样。插入的内容默认也是为“行内元素”，同样可以通过“display”强制装换显示类型。<br><br>
HTML代码示例：

```
<article>
    <p class="addAfter-1">这是正文文本</p>
    <p class="addAfter-2">这是正文文本</p>
    <p class="addAfter-3">这是正文文本</p>
</article>
```
CSS代码如下：

```
 /* 伪元素选择器--元素之后添加 */
        .addAfter-1:after {
            content: url("./images/onepiece-2.png");
            display: inline-block;
            position: relative;
            top: 15px;
        }
        .addAfter-2:after {
            content: "";
            display: inline-block;
            border-width: 5px 5px 5px 18px;
            border-style: solid;
            border-color: transparent transparent transparent #f80;
            -webkit-animation: afterSelector 0.6s infinite linear alternate;
        }
        .addAfter-3:after {
            content: "我就问炫不炫？";
            border: 2px solid #0058ff;
            font: 20px "微软雅黑"; color: #0058ff;
            box-shadow: inset 0 0 10px rgba(13, 68, 172, 0.81),0 0 10px rgba(13, 68, 172, 0.81);
        }
        @-webkit-keyframes afterSelector {
            0% { margin-left: 0px }
            100% { margin-left: 15px; border-width: 8px 6px 8px 18px;}
        }
```
运行效果：

<img src="./images/CSS3-after.png">
使用“:before”和“:after”伪元素选择器不仅能为指定的元素添加文字、图片和各种利用“width”、“height”、“border”制作出来的形状，甚至还能添加音频、视频这些多媒体文件，而且具有高度自定义性。

<!-- 章节练习（一） -->