<h1>CSS文本概述</h1>
字体CSS设置主要是围绕文字本身进行，如文字风格、字体粗细、字体大小、字体系列、字体颜色等，就是说无论进行什么样的设置都是围绕单个文字本身的样式进行设置的，并不会影响到文本的整体布局（“font”组合值写法中的“行高”除外），这一节中CSS文本设置是对文本布局方面的知识进行。
<h1>文本的居中方式"text-align"</h1>
该属性用于控制"行内块元素"或"块元素"内"行内元素"（文本元素）的居中方式，包含三个值：

- <h3 style="font-sze:16px;color:#2a90d1;">left（默认）</h3>
    文本左对齐
- <h3 style="font-sze:16px;color:#2a90d1;">center</h3>
    文本居中对齐
- <h3 style="font-sze:16px;color:#2a90d1;">right</h3>
    文本右对齐<br><br>
HTML代码示例：

```
<article>
   <p class="left">文本左对齐</p>
   <P class="center">文本居中对齐</P>
   <P class="right">文本右对齐</P>
</article>
<article>
   <p class="left">
       <span>文本标签左对齐</span>
   </p>
   <p class="center">
       <label>字段标签居中对齐</label>
   </p>
   <p class="right">
       <a href="javascript:;">超链接标签右对齐</a>
   </p>
</article>
```
CSS代码如下：

```
<!-- 文本对齐方式：left、center、right -->

.left{
    text-align:left;
    }
.center{
    text-align:center;
    }
.right{
    text-align:right;
    }
```