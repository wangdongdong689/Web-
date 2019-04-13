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
