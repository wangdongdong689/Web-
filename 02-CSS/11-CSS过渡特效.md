<h1>CSS过渡特效概述</h1>
在CSS中用于设置过渡特效的属性叫做“<span style="font-size: 24px;color: #0b933b;">transtion”<img src="./images/css3_support.gif"></span>,该属性允许CSS的属性值在一定的时间区间内平滑地过渡，这就拜托了我们在CSS3版本标准之前对“JavaScript”和“Flash”的依赖，使页面的性能得以提升。这种效果可以在鼠标悬浮（:hover）、鼠标单击（:active）、表单元素获得焦点（:focus）或对元素任何改变以及在JavaScript中某些事件执行后触发，并圆滑（若不对时间曲线进行特殊设置）地以动画效果改变CSS的属性值。<br><br>

该属性能够对CSS中绝大部分属性的变化生效，但不能对CSS属性值<span style="font-size: 24px;color: #0b933b;">不为“数值”</span>的属性生效，即只有当属性的值为一个数值的时候，该属性才能生效。数值包含“纯数字”、“像素数值”、“百分比数值”、“十六进制数值”等CSS属性的值为数值的元素生效。如：当元素的宽度为“width:100px”变化为“width:200px”的时候过渡效果能够生效<br><br>
注意：但当元素的宽度为“width:100px”变化为“width:auto”的时候，就不会产生过渡效果了。当一个元素的字体颜色为“<span style="color: rgb(243, 30, 29);">#f31e1d</span>”,变化为“<span style="color: rgb(35, 150, 253);">#2396fd</span>”的时候过渡有效，但当它的字体颜色由“<span style="color: rgb(243, 30, 29);">#f31e1d</span>”变为“transparent”的时候过渡就不会产生效果了。这一点在使用中需要留意。<br><br>
该属性包含多个分支属性，主要有：“过渡CSS属性名称”、“过渡执行时间”、“过渡时间速率曲线”和“过渡的延时执行”四个主要内容。
<h1>执行变换的属性“transition-property”</h1>
该属性是用来指定当元素其中一个属性改变时执行的过渡动画效果，该属性有三种类型的值：
<h3 style="color: #2a90d1;font-size: 24px;">none</h3>
将过渡效果设置为“<span style="font-size: 24px;color: #0b933b;">无过渡效果</span>”,或<span style="font-size: 24px;color: #0b933b;">停止</span>当前过渡效果。
<h3 style="color: #2a90d1;font-size: 24px;">all（默认）</h3>
为所支持的所有CSS属性在<span style="font-size: 24px;color: #0b933b;">值变化时</span>执行动画过渡效果。
<h3 style="color: #2a90d1;font-size: 24px;">[property name]</h3>
指定一个或多个属性名称列表，以逗号“，”进行分割，当指定的属性产生变化时，为其执行指定属性的动画过渡效果。<br><br>
HTML部分为4个< section>标签，CSS代码如下：

```
html,body {
            margin: 0; padding: 0;
        }
        section {
            width: 200px; height: 200px;
            transition: 0.9s;
            background-color: #e80000;
            border: 5px solid #131313;
            margin-right: 20px; float: left;
        }
        section:nth-child(1) {
            transition-property: background-color;}
        section:nth-child(1):hover {
            background-color: #240808;}
        section:nth-child(2) {
            transition-property: border-color;}
        section:nth-child(2):hover {
            border-color: #7ce9f7;}
        section:nth-child(3) {
            transition-property: border-radius,border-color;}
        section:nth-child(3):hover {
            border-radius: 50%;
            border-color: #e800df;}
        section:nth-child(4) {
            transition-property: all;}
        section:nth-child(4):hover {
            background-color: #e800df;
            border-color: #fc0303;
            border-radius: 50%;
        }
```
<h1>过渡执行的时间“transition-duration”</h1>
该属性是用于设定一个属性的值过渡被触发开始时到结束时所需要经历的时间，单位为秒（s），如：“0.3s”或“.3s”,它的默认值为“0”，单位不能省略，否则过渡动画无法执行。<br><br>
HTML部分为4个< section>标签，CSS代码如下：

```
section {
            width: 200px; height: 200px;
            transition: all;
            background-color: #e80000;
            border: 5px solid #131313;
            margin-right: 20px; float: left;
        }
        section:nth-child(1) {
            transition-duration: 0.16s;
        }
        section:nth-child(2) {
            transition-duration: 0.5s;
        }
        section:nth-child(3) {
            transition-duration: 1s;
        }
        section:nth-child(4) {
            transition-duration: 3s;
        }
        section:hover {
            background-color: #131313;
            border-color: #e80000;
            border-radius: 50%;
        }
```
<h1>过渡时间曲线"transition-timing-function"</h1>
该属性允许你根据时间的推进去改变属性值的变换速率，目前它可能够设置6个类型的值：
<h3 style="color: #2a90d1;font-size: 24px;">ease</h3>
默认值，逐渐变慢。
<h3 style="color: #2a90d1;font-size: 24px;">linear</h3>
匀速。
<h3 style="color: #2a90d1;font-size: 24px;">ease-in</h3>
加速。
<h3 style="color: #2a90d1;font-size: 24px;">ease-out</h3>
减速。
<h3 style="color: #2a90d1;font-size: 24px;">ease-in-out</h3>
先加速，后减速。
<h3 style="color: #2a90d1;font-size: 24px;">cubic-bezier([参数])</h3>
可以定义一个时间曲线，可以为其配置四个参数，前两个参数为“x1”和“x2”，定义“<span style="font-size: 24px;color: #0b933b;">开始控制点</span>”，后两个参数为“y1”和“y2”，定义“<span style="font-size: 24px;color: #0b933b;">结束控制点</span>”。而“开始点”和“结束点”是通过这两条“转换点控制轴”分别去调整两个点来实现曲线的变化的，如果对Photoshop里面的“钢笔工具”的“路径”比较熟悉的话，稍加联想应该能理解到这个时间曲线轴的改变原理，这种曲线叫做“<span style="font-size: 24px;color: #0b933b;">贝塞尔曲线</span>”。<br><br>

HTML部分为6个< section>标签，CSS代码如下：

```
section {
            font: 20px/130px arial;
            box-sizing: border-box;
        }
        section {
            width: 160px; height: 160px;
            transition: all 1.2s;
            background-color: #e80000;
            border: 5px solid #131313;
            margin-right: 20px; float: left;
            text-align: center; color: #fff;
        }
        section:nth-child(1) {
            transition-timing-function: ease; /*(0.25, 0.1, 0.25, 1.0)*/
        }
        section:nth-child(2) {
            transition-timing-function: linear; /* (0.0, 0.0, 1.0, 1.0) */
        }
        section:nth-child(3) {
            transition-timing-function: ease-in; /* (0.42, 0, 1.0, 1.0) */
        }
        section:nth-child(4) {
            transition-timing-function: ease-out; /* (0, 0, 0.58, 1.0) */
        }
        section:nth-child(5) {
            transition-timing-function: ease-in-out; /* (0.42, 0, 0.58, 1.0) */
        }
        section:nth-child(6) {
            transition-timing-function: cubic-bezier(0, 0.79, 0.95, 0.1);
        }
        section:hover {
            background-color: #131313;
            border-color: #e80000;
            border-radius: 50%;
        }
```
<h1>过渡延迟“transition-delay”</h1>
该属性规定在用户进行操作后多久开始执行动画，也就是延迟执行过渡动画的时间，单位同样是秒“s”，写法与“transition-duration”一致，默认值同样为“0”。<br><br>

HTML部分为6个< section>标签，CSS代码如下：

```
 section {
            font: 20px/200px arial;
            box-sizing: border-box;
        }
        section {
            width: 200px; height: 200px;
            transition: all 0.6s linear;
            background-color: #e80000;
            border: 5px solid #131313;
            margin-right: 20px; float: left;
            text-align: center; color: #fff;
        }
        section:nth-child(1) {
            transition-delay: 0s;
        }
        section:nth-child(2) {
            transition-delay: 0.4s;
        }
        section:nth-child(3) {
            transition-delay: 0.8s;
        }
        section:nth-child(4) {
            transition-delay: 1.2s;
        }
        section:hover {
            background-color: #131313;
            border-color: #e80000;
            border-radius: 50%;
        }
```
<h1>综合的“transition”</h1>
和其它大多数CSS样式设置属性一样“transition”属性也支持多值组合的写法，而且也是实际开发中最为常用的写法，能大大地节约代码量，但在编写该属性的时候一定要注意值的编写顺序，否则过渡动画执行会异常，甚至完全不能执行。<br><br>

HTML部分为6个< section>标签，CSS代码如下：

```
section {
            font: 46px/240px "jokerman";
            box-sizing: border-box;
        }
        section {
            width: 240px; height: 240px;
            background-repeat: no-repeat;
            background-size: cover;
            margin-right: 20px; float: left;
            text-align: center; color: transparent;
            box-shadow: inset 0 0 0 16px rgba(255, 255, 255, 0.5);
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0);
            transform: rotate(-360deg);
            border-radius: 50%;
            opacity: 0.3;
        }
        section:nth-child(1) {
            background-image: url("../../../img/bgi/example-bgi-01.jpg");
            transition: .4s linear;
        }
        section:nth-child(2) {
            background-image: url("../../../img/bgi/example-bgi-02.jpg");
            transition: all .9s 0.1s;
        }
        section:nth-child(3) {
            background-image: url("../../../img/bgi/example-bgi-03.jpg");
            transition: all 1.85s ease-in-out 0.2s;
        }
        section:nth-child(4) {
            background-image: url("../../../img/bgi/example-bgi-04.jpg");
            transition: 1.2s cubic-bezier(0, 0.79, 0.95, 0.1);
        }
        section:hover {
            transform: rotate(0deg);
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.8);
            color: #fff;
            opacity: 1;
        }
```

<!-- 
<章节练习>
尝试用CSS3的过渡属性制作出一个“创意特效”，具体要求如下：

1、不能是简单的色彩、大小、字体等变化，要有一定创意；

2、制作效果扩展性强，能为以后的作业或项目中所使用。 -->