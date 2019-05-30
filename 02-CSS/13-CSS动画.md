<h1>CSS动画概述</h1>
在CSS中执行动画的属性是CSS3属性中的“animation<img src="./images/css3_support.gif">”，该属性可以让元素随着时间的推移，产生“位置”、“形状”、“颜色”、“大小”、“透明度”等属性变化。<br><br>

它和“transition”的不同之处在于，它可以不需要任何事件的激活（当然也可以通过事件激活），让元素本身就“<span style="font-size: 24px;color: #0b933b;">挂载</span>”一系列的CSS属性变化。他和“transform”的不同之处在于，它并不需要“transition”的过渡特效，让元素可以通过“<span style="font-size: 24px;color: #0b933b;">关键帧</span>”的设置达到想要的动画运行的“速度曲线（贝塞尔曲线）”。“animation”属性和前两者还有一个比较显著的区别，就是它可以单独地存在，即可以不依赖任何选择器，但可以提供给任何与它动画<span style="font-size: 24px;color: #0b933b;">内容匹配</span>并且“显示类型”支持的选择器<span style="font-size: 24px;color: #0b933b;">调用</span>，它和前两者还有一个很显著的区别，就是它能够“无限次”地执行动画效果。<br><br>

该属性可以和过渡属性“transition”搭配使用，但通常来讲是没有共存的意义的，因为“animation”也可以通过设置“animation-timing-function（动画时间曲线，区别于‘过渡时间曲线’）”来达到动画平滑或无规律的“过渡”效果。但该属性和变形转换属性“transform”配合起来使用，往往都会出现一些让人感到“惊艳”的效果。<br><br>

该属性的执行需要通过关键帧“<span style="font-size: 24px;color: #0b933b;">@keyframes+[animation name]</span>”进行定义，该定义从CSS3技术发展的现状来看，还都需要在前面加上浏览器厂商的“前缀”，如：“@-webkit-keyframes”、“@-moz-keyframes”或“@-ms-keyframes”等，当然，和其它需要加前缀的属性一样，该定义也需要保留一份未加任何前缀的“初始定义”，以供现在或未来的一些支持该属性定义的其它浏览器厂商使用，如：“腾讯浏览器（采用‘X5’内核排版渲染）”。

<h1>动画名称“animation-name”</h1>
该属性用于定义动画的名称，以供需要使用该动画的“animation”属性调用，该名称完全是由用户自定义的，但也应该要“<span style="font-size: 24px;color: #0b933b;">语义化</span>”一些，方便调用者能更直观地了解此处定义动画的实际作用，而且切忌出现特殊符号（浏览器解析会存在差异），如一个改变元素大小动画的名称定义应该是：

```
@keyframes resizeWidth{
    <!-- 各关键帧执行的CSS属性 -->
    、、、
}
```
CSS选择器中的调用应该是：
```
section{
    animation-name:resizeWidth;
}
```
<h1>动画关键帧的两种定义方式</h1>
定义动画的“关键帧”有两种方式，一种为“英文单词”定义模式，一种为“百分数”定义模式。
<h3 style="color: #2a90d1;font-size:24px;">英文单词模式</h3>
该模式只包含两个关键帧，即开始帧“from”，表示动画开始时执行的CSS属性，和结束帧“to”，表示动画结束时执行的CSS属性。

<h3 style="color: #2a90d1;font-size:24px;">百分数模式</h3>
该模式相对“英文单词”定义关键帧的模式更为详细，能够支持理论上从“0%”到“100%”之间的所有帧的定义，“0%”相当于“from”，表示动画开始帧，“100%”相当于“to”，表示动画结束帧。该模式由于控制的精细度高，书写修改容易，甚至可以通过“定义百分比的跳跃”或“CSS属性值的跳跃”来实现动画的“匀速”、“加速”、“减速”，“变速”等动画速率的变化，非常地灵活，所以这种写法也是现今最主流的定义动画关键帧的方式。<br><br>

以下就是两种模式的书写对比：

```
<!-- 英文单词模式 -->
@keyframes resizeWidth{
    from{width:100px;}
    to{wdith:800px;}
}
<!-- 百分比模式 -->
@keyframes resizeWidth{
    0%{width:100px;}
    20%{width:100px;}
    40%{width:100px;}
    60%{width:100px;}
    80%{width:100px;}
    100%{width:100px;}
}
```
<h1>动画执行时间“animation-duration”</h1>
该属性用于定义动画执行的时间，即一段动画从开始到动画结束所经历的时间，单位为秒“s”或毫秒“ms”，默认值为“0”，即看不执行任何动画，所以在定义设置一个动画的时候始终都要设置该属性，并给定一个大于“0”的时间。<br><br>

HTML部分有一个< section>标签，对应的CSS部分代码为：

```
section{
    width:240px;height:180px;
    background-color:#ba0a0a;
}
section:hover{
    animation-name:resizeWidth;
    animation-duration:2s;
}
@keyframes resizeWidth{
    from{width:240px;}
    to{width:600px;}
}
```
当然，上例中的“animation”各属性都不一定要写在“:hover”的伪类选择器里，也可以直接写在“section”的选择器里，不过这样页面在加载时就会直接执行该动画，除非设置了动画执行次数“animation-iteration-count”属性（后面会讲到该属性），否则页面将无法再次执行该动画，这点和设置了“<span style="font-size: 24px;color: #0b933b;">CSS位移属性</span>”并设置了“transition”过渡属性的元素一样。

<h1>动画时间曲线“animation-timing-function”</h1>
该属性和“transition”的分支属性“transition-timing-function”十分相似，同样是用于定义元素随着时间的推进执行动画的速率变化。它同样有这样6个值：

<h3 style="color: #2a90d1;font-size:24px;">ease</h3>
默认值，逐渐变慢。
<h3 style="color: #2a90d1;font-size:24px;">linear</h3>
匀速。
<h3 style="color: #2a90d1;font-size:24px;">ease-in</h3>
加速。
<h3 style="color: #2a90d1;font-size:24px;">ease-out</h3>
减速。
<h3 style="color: #2a90d1;font-size:24px;">ease-in-out</h3>
先加速，后减速。
<h3 style="color: #2a90d1;font-size:24px;">cubic-bezier([参数])</h3>
可以定义一个时间曲线，可以为其配置四个参数，前两个参数为“x1”和“x2”，定义“<span style="font-size: 24px;color: #0b933b;">开始控制点</span>”，后两个参数为“y1”和“y2”，定义“<span style="font-size: 24px;color: #0b933b;">结束控制点</span>”。而“开始点”和“结束点”是通过这两条“转换点控制轴”分别去调整两个点来实现曲线的变化的。<br><br>

HTML部分代码为4个< section>标签，对应的CSS部分代码为：

```
        /*body {
            padding: 50px;
        }*/
        section {
            width: 180px; height: 180px;
            border-radius: 50%;
            text-align: center;
            color: #fff;
            font: 42px/180px "snap itc";
            box-sizing: border-box;
            float: left;
            margin-right: 50px;
        }
        section:nth-child(3){
            padding-top: 40px;
            font: 36px/50px "snap itc";
        }
        section:nth-child(4){
            padding-top: 30px;
            font: 36px/50px "snap itc";
        }
        section:nth-child(1) { background-color: #ba0a0a; }
        section:nth-child(2) { background-color: #15b108; }
        section:nth-child(3) { background-color: #0a47ba; }
        section:nth-child(4) { background-color: #ba0a98; }
        section:nth-child(1):hover,section:nth-child(2):hover,
        section:nth-child(3):hover,section:nth-child(4):hover {
             animation: rotateSection 3s;
        }
        section:nth-child(1):hover {
            animation-timing-function: ease;
        }
        section:nth-child(2):hover {
            animation-timing-function: linear;
        }
        section:nth-child(3):hover {
            animation-timing-function: ease-in-out;
        }
        section:nth-child(4):hover {
            animation-timing-function: cubic-bezier(1, -0.3, 0.99, 0.62);
        }
        @keyframes rotateSection {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

```
<h1>动画时间的延迟“animation-delay”</h1>
该属性和“transition”属性的“transition-delay”属性也十分相似，它规定在动画是在延迟多少秒“s”或毫秒“ms”后开始执行动画，默认值同样为“0”，即立即开始动画。<br><br>

HTML部分代码为4个< section>标签，对应的CSS部分代码为：

```
 /*body {
            padding: 50px;
        }*/
        section {
            width: 180px; height: 180px;
            border-radius: 50%;
            text-align: center;
            color: #fff;
            font: 32px/180px "snap itc","华文琥珀";
            box-sizing: border-box;
            float: left;
            margin-right: 50px;
            cursor: default;
        }
        section:nth-child(1) { background-color: #ba0a0a; }
        section:nth-child(2) { background-color: #15b108; }
        section:nth-child(3) { background-color: #0a47ba; }
        section:nth-child(4) { background-color: #ba0a98; }
        section:nth-child(1):hover,section:nth-child(2):hover,
        section:nth-child(3):hover,section:nth-child(4):hover {
             animation: rotateSection 0.6s linear;
        }
        section:nth-child(1):hover {
            animation-delay: 0s;
        }
        section:nth-child(2):hover {
            animation-delay: 0.4s;
        }
        section:nth-child(3):hover {
            animation-delay: 0.8s;
        }
        section:nth-child(4):hover {
            animation-delay: 1.2s;
        }
        @keyframes rotateSection {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
```
该属性在制作大规模“动画集”时十分常用，可以让元素在执行指定事件（包括加载事件）后有次序地前后对“挂载”的动画进行播放，从而组成一幅“生动”而“有故事性”的动画。

<h1>动画播放的次数“animation-iteration-count”</h1>
该属性用于设置动画播放的次数。它可以设置3种类型的值：

<h3 style="color: #2a90d1;font-size:24px;">1（默认值）</h3>
表示在执行某事件后只执行1次动画。
<h3 style="color: #2a90d1;font-size:24px;">[number]</h3>
任意正整数，表示在执行某事件后只执行[numver]次动画。
<h3 style="color: #2a90d1;font-size:24px;">infinite</h3>
表示在执行某事件后“无限次”执行动画。<br><br>

HTML部分代码为3个< section>标签，对应的CSS部分代码为：

```
 body {
            height: 236px;
            padding-top: 50px;
        }
        section {
            width: 180px; height: 180px;
            border-radius: 50%;
            text-align: center;
            color: #fff;
            font: 42px/180px "snap itc","华文琥珀";
            box-sizing: border-box;
            float: left;
            cursor: default;
        }
        section:nth-child(1) { background-color: #ba0a0a; }
        section:nth-child(2) { background-color: #15b108; }
        section:nth-child(3) { background-color: #0a47ba; }
        section {
            animation: bounceSection 0.6s linear;
            position: absolute;
            top: 100px;
        }
        section:nth-child(1) {
            left: 10px;
            animation-iteration-count: 1;
        }
        section:nth-child(2) {
            left: calc(10px + 50px + 180px);
            animation-iteration-count: 3;
        }
        section:nth-child(3) {
            left: calc(10px + (50px + 180px) * 2);
            animation-iteration-count: infinite;
        }
        @keyframes bounceSection {
            0% { top: 118px; transform: scale(1.2,0.9)}
            80% { top: 0px; transform: scale(1)}
            100% { top: 118px; transform: scale(1.2,0.9)}
        }
```

<h1>动画周期逆向播放“animation-direction”</h1>
该属性用于设置元素动画是否能够周期性地逆向播放，逆向动画播放的进行时间和“正向播放”一致，时间速度曲线会按照“100%（to）”到“0%（from）”的方向进行。<br><br>

HTML部分代码为：

```
<section class="clock-bg">
    <section class="clock-pointer"></section>
</section>
```
CSS部分代码为：

```
 body {
        }
        .clock-bg {
            width: 240px; height: 240px;
            background: url("./img/content/clock-bg.png") no-repeat;
            position: relative;
            animation: translateClock 5s linear infinite;
            animation-direction: normal;
        }
        .clock-pointer {
            width: 5px; height: 116px;
            background-color: #3777d6;
            border-radius: 3px;
            border-top-left-radius: 50%;
            border-top-right-radius: 50%;
            position: absolute;
            left: calc(50% - 3px); top: 12px;
            transform-origin: 2px 106px;
            animation: swingPointer 1.2s ease-in infinite;
            animation-direction: alternate;
        }
        @keyframes translateClock {
            0% { transform: translateX(0)}
            100% { transform: translateX(600px)}
        }
        @keyframes swingPointer {
            0% { transform: rotate(0deg)}
            100% { transform: rotate(360deg)}
        }
```
<h1>动画的播放和暂停“animation-play-state”</h1>
该属性用于设置动画的播放和暂停状态，它有两个值：
<h3 style="color: #2a90d1;font-size:24px;">running</h3>
播放动画。
<h3 style="color: #2a90d1;font-size:24px;">paused</h3>
暂停动画。<br><br>

HTML部分代码为：

```
<input id="play" type="text" value="播放">
    <input id="stop" type="text" value="暂停">
    <section class="clock-bg">
        <section class="clock-pointer"></section>
    </section>
```
CSS部分代码为：
```
 input {
            width: 60px;
            font: 20px "微软雅黑";
        }
        .clock-bg {
            width: 240px; height: 240px;
            background: url("../../../img/content/clock-bg.png") no-repeat;
            position: relative;
            animation: translateClock 5s linear infinite;
            animation-direction: normal;
        }
        .clock-pointer {
            width: 5px; height: 116px;
            background-color: #3777d6;
            border-radius: 3px;
            border-top-left-radius: 50%;
            border-top-right-radius: 50%;
            position: absolute;
            left: calc(50% - 3px); top: 12px;
            transform-origin: 2px 106px;
            animation: swingPointer 1.2s ease-in infinite;
            animation-direction: alternate;
        }
        input#paly:focus ~ section {
            animation-play-state: running;
        }
        input#stop:focus ~ section {
            animation-play-state: paused;
        }
        @keyframes translateClock {
            0% { transform: translateX(60px)}
            100% { transform: translateX(600px)}
        }
        @keyframes swingPointer {
            0% { transform: rotate(0deg)}
            100% { transform: rotate(360deg)}
        }
```
<h1>设定元素动画形态“animation-fill-mode”</h1>
经过之前“animation”属性的学习应该会发现一个问题，就是若不将动画的“animation-iteration-count”属性设置为“infinite”值的话，动画在播放完成后会还原到元素没有“挂载”动画播放效果之前的状态，在有的应用场景里这样似乎没有问题，但在有些应用场景下，这样的设定会让人有一种“瞎忙活”或“功败垂成”的感觉。而“animation-fill-mode”属性的出现克服了这个问题，它可以预设值动画播放前的“第一帧”和保留动画播放完成后的“最后一帧”，可以通过以下值进行设置：

<h3 style="color: #2a90d1;font-size:24px;">backwards</h3>
让元素保持动画第一帧定义里所设置的CSS属性，直到动画开始执行。
<h3 style="color: #2a90d1;font-size:24px;">forwards</h3>
让元素保持动画播放结束后最后一帧定义里所设置的CSS属性。
<h3 style="color: #2a90d1;font-size:24px;">both</h3>
让元素保持动画第一帧里定义的CSS属性，直到动画开始，动画播放完成后又保持动画最后一帧的属性。<br><br>

HTML部分代码为3个< section>标签，对应的CSS部分代码为：

```
body {
            padding: 44px;
        }
        section {
            float: left;
            margin-right: 50px;
            font: 42px/200px "snap itc";
            text-align: center;
            color: #fff;
        }
        section {
            width: 200px; height: 200px;
            animation: changeElement 1.2s 3s;
            background-color: #0ab7c6;
        }
        section:nth-child(1) {
            animation-fill-mode: backwards;
        }
        section:nth-child(2) {
            animation-fill-mode: forwards;
        }
        section:nth-child(3) {
            animation-fill-mode: both;
        }
        @keyframes changeElement {
            0% {
                width: 240px; height: 240px;
                background-color: #c63411;
            }
            100% {
                background-color: #e310ff;
                transform: rotate(30deg);
            }
        }
```
<h1>组合值的写法“animation”</h1>
作为CSS里的3大亮点“transition”属性、“transform”属性、“animation”属性，“animation”的值自然也支持组合形式的书写，如例：

```
<!-- 分别表示：动画名称、执行时间、速度曲线、延迟时间、播放次数、周期逆向播放、播放状态（开始/暂停）、首帧预设/末帧保留 -->

animation:animName 1s ease 0.3s infinite alternate running both;
```
当然，上例中是一种将“animation”中所有支持的值都罗列的形式，在实际操作中，是可以根据需要“选取”所需要的值进行组合的，如：

```
<!-- 执行动画"animName"，播放时间为2秒 -->
animation:animName 2s;

<!-- 执行动画“animName”,播放时间为2秒，匀速播放 -->
animation:animName 2s linear;

<!-- 执行动画“animName”,播放时间为2秒，延迟0.5秒播放 -->
animation:animName 2s 0.5s;

<!-- 执行动画“animName”播放时间为2秒，无限次播放 -->
animation:animName 2s infinite;

<!-- 执行动画“animName”,播放时间为2秒，延迟1秒，播放前显示首帧样式，播放完成保留最后一帧样式 -->
animation:animName 2s 1s both;

<!-- 等等 -->
```
通过上面组合值的写法，仔细一点的人应该能发现，就是无论用什么方式去组合“animation”的值，有两个值是必要的，就是“动画名称”和“动画执行时间”，原因很简单，没有动画名称，元素就无法去调用该动画，没有动画执行时间，就看不到动画效果。这点在以后的使用中要特别的留心，而且值组合的顺序也要尽量按照本章中分支属性介绍的顺序进行，否则很可能让你定义的动画出现“意料外”的情况。

<!-- <综合练习>
制作一个3D相册盒子，具体要求如下：

1、盒子需要6个宽高相等的面（正方体），宽度和高度均不得超出320像素，每个面的透明度为0.9（可以在0.7~0.95之间浮动）；

2、盒子的6个面为6张不同的图片，6张图片需要不失比例地完整填充盒子的每一个面，也可以用PS等工具将图片裁剪到合适的大小；

3、盒子需要在页面载入时就自动“永久”地旋转起来，需要保证在一个动画周期运行完成后6个面都能得到过显示；

4、页面需要一张背景图片，背景图片需要在不失比例的情况下，填充满分辨率范围从“1024*768”到“1920*1080”的屏幕（注意背景图片和盒子本体产生对比，否则会影响到显示效果）。

<扩展功能>

1、当鼠标移动到盒子上时，6个面会照各自的方向有过渡地展开100像素的距离；

2、当6个面展开后，会从一个正方形变成一个圆形，并且内外都发出一圈白光。 -->

