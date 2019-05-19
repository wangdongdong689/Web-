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
使用“:before”和“:after”伪元素选择器不仅能为指定的元素添加文字、图片和各种利用“width”、“height”、“border”制作出来的形状，甚至还能添加音频、视频这些多媒体文件，而且具有高度自定义性。<br><br>

<!-- 章节练习（一） 
制作任意四个文本，具体要求如下：
1、第一个文本段落需大于两行，为首字添加一个效果：字体设为22像素的“微软雅黑”字体，具有一个2像素的边框，字体颜色和边框均为红色，背景色为“#f3d5df”,字体与表框之间的内间距为2像素；

2、第二个文本段落需大于两行，将首行文字的字间距设为“0.8em”24像素的“微软雅黑”字体，字体颜色为“#e910d4”，并且具有下划线；

3、第三个段落文本，字数控制在4~10字内，文本水平居中。为该段落前添加一个宽高均为“32像素”背景色为“#6d2a03”圆角（border-radius）为“16像素”的形状，形状内含有一个水平垂直均居中的“炫”字。设法使该形状和段落文本水平对齐。

4、第四个段落文本，字数控制在4~10字内，文本水平居中。为该段落后添加一张接近圆形的“PNG图片”，图片大小为“32*32”。设法使该图片和和段落文本水平对齐。

<扩展功能>
1、使段落三前面的“炫”字形状显示出动态的“外发光效果”（最小发光距离“5像素”，最大发光距离“20像素”，发光颜色“rgba(48, 77, 235, 0.88)”）；

2、使段落四后方的图片以中心为原点进行无限的顺逆时针旋转（旋转速度自定）。
-->
<h1>结构性伪类选择器<img src="./images/css3_support.gif"></h1>
<a href="http://www.w3school.com.cn/cssref/css_selectors.asp">W3C选择器</a><br><br>

该类选择器主要用于当前选择器精确地通过元素“<span style="color:#0b933b;font-size:24px;">索引值”</span>或<span style="color:#0b933b;font-size:24px;">"匹配类型"</span>的索引值定位到该选择器的<span style="color:#0b933b;font-size:24px;">同级</span>指定元素。该类型选择器的格式是<span style="color:#0b933b;font-size:24px;">“基本选择器”</span>（包括“后代选择器”、“自主选择器”、“同级选择器”等）或<span style="color:#0b933b;font-size:24px;">"属性选择器"</span>（包括各种带条件的属性选择器）”+“结构性伪类选择器”的形式。“结构性伪类选择器”会增加“1”的权重，该类选择器主要有以下形式：
<h3 style="color:#2a90d1;">:first-child</h3>
对该类所有父元素中的首个子元素进行选择。<br><br>
HTML代码如下：

```
<section>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </section>
    <article>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </article>
    <div>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </div>
```
CSS代码如下：
```
 section,article {
            border-bottom: 1px dashed #bbb;
        }
        div {
            border: none;
        }
        p:first-child {
            color: #800;
            font: x-large "华文行楷";
        }
```
运行效果：

<img src="./images/first-child.png">
<h3 style="color:#2a90d1;">:last-child</h3>
对该类所有父元素中的最后一个子元素进行选择。<br><br>
HTML代码如下：

```
<section>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </section>
    <article>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </article>
    <div>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </div>
```
CSS代码如下：
```
section,article {
            border-bottom: 1px dashed #bbb;
        }
        div {
            border: none;
        }
        p:last-child {
            color: #060;
            font: x-large "华文彩云";
        }
```
运行效果：

<img src="./images/last-child.png">
<h3 style="color:#2a90d1;">:first-of-type</h3>
对该类所有父元素中的首个匹配到类型的子元素进行选择。<br><br>
HTML代码如下：

```
    <section>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </section>
    <article>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </article>
    <div>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
    </div>
```
CSS代码如下：

```
section,article {
            border-bottom: 1px dashed #bbb;
        }
        div {
            border: none;
        }
        h3:first-of-type {
            color: #046;
            font: x-large "华文琥珀";
        }
        p:first-child {
            color: #f46;
            font: x-large "微软雅黑";
        }
```
运行效果：

<img src="./images/first-of-type.png">
<h3 style="color:#2a90d1;">:last-of-type</h3>
对该类所有父元素中的最后一个匹配到类型的子元素进行选择。<br><br>
HTML代码如下：

```
<section>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
    </section>
    <article>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </article>
    <div>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
    </div>
```
CSS代码如下：

```
section,article {
            border-bottom: 1px dashed #bbb;
        }
        div {
            margin: 1em 0;
            border: none;
        }
        h3:last-of-type {
            color: #d45ed4;
            font: x-large "楷体";
        }
        p:last-child {
            color: #138d29;
            font: x-large "幼圆";
        }
```
运行效果：

<img src="./images/last-of-type.png">
<h3 style="color:#2a90d1;">:only-child</h3>
对该类所有父元素中只含有唯一所匹配（不包含同级元素）的子元素进行选择。<br><br>
HTML代码如下：

```
<section>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
    </section>
    <article>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </article>
    <div>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </div>
    <section>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </section>
```
CSS代码如下：
```
 section,article,div {
            border-bottom: 1px dashed #bbb;
        }
        section div {
            border: none;
            margin: 1em 0;
        }
        section:last-child {
            border: none;
        }
        p:only-child {
            color: #638d13;
            font: xx-large "黑体";
        }
```
运行效果：

<img src="./images/only-child.png">
<h3 style="color:#2a90d1;">:only-of-type</h3>
对该类所有父元素中只含有唯一所匹配类型的子元素进行选择。<br><br>
HTML代码如下：

```
<section>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
    </section>
    <article>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
    </article>
    <div>
        <h3>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</h3>
        <p>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</p>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
    </div>
```
CSS代码如下：
```
section,article {
            border-bottom: 1px dashed #bbb;
        }
        section div, article div {
            margin: 1em 0;
            border: none;
        }
        div:last-child {
            border: none;
        }
        p:only-of-type {
            color: #550fa7;
            font: x-large "微软雅黑";
        }
```
运行效果：

<img src="./images/only-of-type.png">
<h3 style="color:#2a90d1;">:nth-child(n)</h3>
对其父元素的第“n”个子元素进行选择，通过设置<span style="color:#0b933b;font-size:24px;">参数</span>“n”指定为第几个元素<br><br>
HTML代码如下：

```
    <section>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
        <div>夫君子之行,静以修身,俭以养德,非淡泊无以明志,非宁静无以致远。</div>
    </section>
```
CSS代码如下：
```
div { line-height: 1.4;}
        div:nth-child(2), div:nth-child(4) {
            font: 24px "微软雅黑";
        }
        div:nth-child(2) {
            color: #6d9b4b;
        }
        div:nth-child(4) {
            color: #9b4b86;
        }
```
运行效果：

<img src="./images/nth-child(n).png">
该选择器不仅能准确的匹配到第“几”个指定类型的元素，还能对匹配类型元素的“<span style="color:#0b933b;font-size:24px;">奇偶索</span>引”值进行选择，用“奇偶索引”选择器来制作隔行变色的表格及相关场景的元素时非常高效便捷：<br><br>
HTML代码如下：

```
<table>
        <tr>
            <th>编号</th><th>姓名</th><th>职位</th><th>外貌</th>
        </tr>
        <tr>
            <td>rimi-001</td><td>张三</td><td>学霸</td><td>长得还比较帅</td>
        </tr>
        <tr>
            <td>rimi-002</td><td>李四</td><td>学霸</td><td>长得还比较帅</td>
        </tr>
        <tr>
            <td>rimi-003</td><td>王五</td><td>学霸</td><td>长得还比较帅</td>
        </tr>
        <tr>
            <td>rimi-004</td><td>王麻子</td><td>学霸</td><td>长得还比较...</td>
        </tr>
    </table>
```
CSS代码如下：
```
table, th, td {
            border: 1px solid #aaa;
            line-height: 160%;
            border-collapse: collapse;
            text-align: center;
            color: #fff;
        }
        th { width: 140px }
        th:last-child { width: 240px }
        table tr:nth-child(odd),table tr:nth-child(even) {
            font: 22px "幼圆";
        }
        table tr:nth-child(odd) {
            background-color: #0a2841;
        }
        table tr:nth-child(even) {
            background-color: #4d1608;
        }
```
运行效果：