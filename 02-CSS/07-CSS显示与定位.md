<h1>CSS显示与定位概述</h1>
在HTML中，元素会按照标准的“文档流”布局方式进行布局，即“从左到右，从上到下”的方式进行布局，而通过CSS里面的部分定位和显示方式的设置可以使元素脱离“文档流”，采用特殊的布局方式进行布局，或者在页面中进行“隐藏”，而“隐藏”在CSS中又有两种定义方式，一种可以脱离“文档流”，一种仍然存在于“文档流”的布局中。
<h1>元素的显示方式“display”</h1>
规定元素的“<span style="font-size:24px;color:#0b933b;">显示类型</span>”，以目前的HTML标准来讲，HTML文档中自带的标签元素的“显示类型”已经被定义，如（只列出了部分“显示类型”的分类）：

- block：< div>、< p>、< header>、< main>、< footer>、< nav>、< section>、< article>、< ul>、< ol>等。
- inline-block：< input>、< textarea>、< button>、< meter>、< progress>”等。
- inline：< span>、< a>、< label>、< em>、< mark>、< img>、< audio>、< video>等。
- table：< table>。
- table-row：< tr>。
- table-cell：< th>和< td>。
- list-item：< li>。
如果考虑到布局需要，有的时候我们会强制的将“显示类型”进行转换，在进行转换后，该元素的功能和特性（如将< div>标签转换为“inline-block”之后，也不能嵌套在< p>里和转换为“block”的< span>里）也不会产生变化。<br><br>
显示类型“display”属性主要有以下类型的值：

- <h3 style="font-sze:16px;color:#2a90d1;">none（主要）</h3> 
  将元素设定为不显示，使元素完全地脱离“文档流”。
- <h3 style="font-sze:16px;color:#2a90d1;">inline（主要）</h3> 
  将元素设定为“行内元素”。
- <h3 style="font-sze:16px;color:#2a90d1;">inline-block（主要）</h3> 
  将元素设定为“行内块元素”。
- <h3 style="font-sze:16px;color:#2a90d1;">block（主要）</h3> 
  将元素设定为“块元素”。
- <h3 style="font-sze:16px;color:#2a90d1;">  list-item</h3>
  将元素设置为列表项。
- <h3 style="font-sze:16px;color:#2a90d1;">run-in</h3>
  根据上下文作为“行内块元素”或“块元素”显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table</h3>
  将元素作为table显示。
- <h3 style="font-sze:16px;color:#2a90d1;">inline-table</h3>
  将元素作为行内的table显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-row-group</h3>
  将元素作为一个tbody元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-header-group</h3>
  将元素作为一个thead元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1; ">table-footer-group</h3>
  将元素作为一个tfoot元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-row</h3>
  将元素作为一个tr元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-column-group</h3>
  将元素作为一个colgroup元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-column</h3>
  将元素作为一个col元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-cell</h3>
  将元素作为一个table单元格元素来显示。
- <h3 style="font-sze:16px;color:#2a90d1;">table-caption</h3>
  将元素作为一个table标题显示。
  <h1>元素可见性“Visibility”</h1>
  该属性用于设置元素“是否可见”，也就是即使元素是不可见的，那它所占据的空间也不会消失。“visibility”属性有以下值：
- <h3 style="font-sze:16px;color:#2a90d1;">Visible（默认）</h3>
  设置元素为可见的
- <h3 style="font-sze:16px;color:#2a90d1;">hidden</h3>
  设置元素为不可见的
- <h3 style="font-sze:16px;color:#2a90d1;">collapse</h3>
在表格元素中使用时，此值可删除一行或一列，但是它不会影响表格的布局。被行或列占据的空间会留给其他内容使用。如果此值被用在其他的元素上，会呈现为“hidden”<br><br>
我们通过一段代码的运行效果来对比“display”属性和“visibility”在元素显示、隐藏后的布局对比。<br><br>
HTML代码示例：

```
 <form>
        <section>
            <h3>“visibility”属性：</h3>
            <input name="visibility" type="checkbox" checked>
            <input name="visibility" type="text" value="visibility">
            <input name="visibility" type="checkbox">
            <input name="visibility" type="text" value="显示与否">
            <input name="visibility" type="checkbox" checked>
            <input name="visibility" type="text" value="都会占据">
            <input name="visibility" type="checkbox">
            <input name="visibility" type="text" value="本来的空间">
        </section>
        <section>
            <h3>“display”属性：</h3>
            <input name="display" type="checkbox" checked>
            <input name="display" type="text" value="display">
            <input name="display" type="checkbox">
            <input name="display" type="text" value="隐藏后">
            <input name="display" type="checkbox" checked>
            <input name="display" type="text" value="不会在">
            <input name="display" type="checkbox">
            <input name="display" type="text" value="占据空间">
        </section>
    </form>
```
CSS代码如下：

```
       body {
            margin: 0; padding: 0;
        }
        section:first-child, section:first-child h3:first-child {
            margin-top: 0;
        }
        section{ margin: 20px 0;}
        <!-- CSS主要代码 -->
        input { vertical-align: middle;}//属性设置元素的垂直对齐方式
        input[type="text"][name="visibility"],
        input[type="text"][name="display"] {
            width: 120px;
            margin-right: 30px;
        }
        input[type="checkbox"] {
            width: 20px; height: 20px;
        }
        /* “visibility”属性 */
        input[type="text"][name="visibility"] { visibility: hidden }
        input:checked + input[name="visibility"] {
            visibility: visible;
        }
        /* “display”属性 */
        input[type="text"][name="display"] { display: none }
        input:checked + input[name="display"] {
            display: inline-block;
        }
```
运行效果：

<img src="./images/visibility.png">
<img src="./images/visibility（2）.png">
上述案例可以发现，通过将“visibility”的属性值设置为“hidden”，元素虽然不可见了，但仍未脱离“文档流”，在页面显示中占据着原本的位置。而通过将“display”的属性值设置为“none”，元素不可见了，而且在页面中占据的位置也让与“文档流”内布局的其它元素了。
<h1>元素的不透明度“opacity”</h1>
该元素用户设置元素的不透明度，取值范围是“0”到“1”之间的浮点数，可以保留两位小数，如“0.3”、“0.55”，可以支持省略掉前面的“0”也就是“.3”、“.55”的写法。“0”（相当于“visibility:hidden”）表示完全透明，“1”（默认）表示完全不透明。<br><br>
HTML部分为6个< section>标签，CSS代码如下：

```
       html,body {
            margin: 0; padding: 0;
            height: 100%;
        }
        body {
            background: url("./images/bgi-07.jpg") no-repeat;
            background-size: 100% 100%;
            background-position: 50% 50%;
        }
        section {
            width: 160px; height: 160px;
            background: url("./images/bgi-01.jpg") no-repeat;
            background-size: 100% 100%;
            background-position: 50% 50%;
            margin-right: 20px; margin-top: 20px; margin-bottom: 20px;
            float: left;
        }
        section:nth-child(1) { opacity: 0 }
        section:nth-child(2) { opacity: 0.2 }
        section:nth-child(3) { opacity: 0.4 }
        section:nth-child(4) { opacity: 0.6 }
        section:nth-child(5) { opacity: 0.8 }
        section:nth-child(6) { opacity: 1 }
```
运行效果：

<img src="./images/opacity.png">
将“opacity”的值设置为“0”，和将“visibility”的值设置为“hidden”在布局表现上几乎一致，但在对待用户<span style="font-size:24px;color:#0b933b;">行为</span>上却有着很大的差别。因为，通过将“opacity”的值设置为“0”的方式，只是让元素透明了，但仍然是可以让如鼠标悬浮等事件生效的，而将“visibility”的值设置为“hidden”的方式，是不能触发鼠标悬浮这一类的事件的，这点要注意区分。
<h1>元素的浮动“float”</h1>
该属性可以使元素脱离文档流，在父容器中进行浮动，停靠到父元素的“<span style="font-size:24px;color:#0b933b;">内容边界</span>”或其它浮动元素的“<span style="font-size:24px;color:#0b933b;">边框</span>”，浮动的元素会忽略元素间的“空格”，让同样具有该属性的元素“紧密”地排列在一起。该属性通常用于处理一些需要紧密排列在一起的“块级元素”，如“导航条”、“相册”，或用于处理“图文混排”等。<br><br>
该属性有三个允许的值：

- <h3 style="font-sze:16px;color:#2a90d1;">none</h3>
   默认，元素不进行浮动。
- <h3 style="font-sze:16px;color:#2a90d1;">left</h3>
   元素从左到右进行浮动。
- <h3 style="font-sze:16px;color:#2a90d1;">right</h3>
  元素从右到左进行浮动。<br><br>
“无序列表”的浮动示例，HTML代码如下：

```
<section>
        <ul class="fl">
            <li>列表项1</li>
            <li>列表项2</li>
            <li>列表项3</li>
            <li>列表项4</li>
            <li>列表项5</li>
        </ul>
    </section>
    <section>
        <ul class="fr">
            <li>列表项1</li>
            <li>列表项2</li>
            <li>列表项3</li>
            <li>列表项4</li>
            <li>列表项5</li>
        </ul>
    </section>
```
CSS代码如下:

```
        ul {
            list-style: none;
            margin: 0; padding: 0;
        }
        ul.fl li,ul.fr li {
            width: 100px;
            line-height: 30px;
            text-align: center;
            color: #fff;
        }
        ul.fl li {
            background-color: #ac0a0a;
            float: left;
        }
        ul.fr li {
            background-color: #0a36ac;
            float: right;
        }
        ul.fl:after, ul.fr:after {
            content: ".";
            height: 0;
            display: block;
            visibility: hidden;
            clear: both;
        }
```
运行效果：

<img src="./images/float.png">
再来看一个“图文混排”的示例（做了部分其它样式美化），HTML代码如下：

```
        <section class="flImg">
            <img src="./images/bgi-01.jpg">
            <p>壬戌之秋，七月既望，苏子与客泛舟游于赤壁之下。清风徐来，水波不兴。举酒属客，诵明月之诗，歌窈窕之章。少焉，月出于东山之上，徘徊于斗牛之间。白露横江，水光接天。纵一苇之所如，凌万顷之茫然。浩浩乎如冯虚御风，而不知其所止；飘飘乎如遗世独立,羽化而登仙。</p>
            <p>于是饮酒乐甚，扣舷而歌之。歌曰：“桂棹兮兰桨，击空明兮溯流光。渺渺兮予怀，望美人兮天一方。”客有吹洞箫者，倚歌而和之。其声呜呜然，如怨如慕，如泣如诉；余音袅袅，不绝如缕。舞幽壑之潜蛟，泣孤舟之嫠妇。</p>
        </section>
        <section class="frImg">
            <img src="./images/bgi-03.jpg">
            <p>壬戌之秋，七月既望，苏子与客泛舟游于赤壁之下。清风徐来，水波不兴。举酒属客，诵明月之诗，歌窈窕之章。少焉，月出于东山之上，徘徊于斗牛之间。白露横江，水光接天。纵一苇之所如，凌万顷之茫然。浩浩乎如冯虚御风，而不知其所止；飘飘乎如遗世独立,羽化而登仙。</p>
            <p>于是饮酒乐甚，扣舷而歌之。歌曰：“桂棹兮兰桨，击空明兮溯流光。渺渺兮予怀，望美人兮天一方。”客有吹洞箫者，倚歌而和之。其声呜呜然，如怨如慕，如泣如诉；余音袅袅，不绝如缕。舞幽壑之潜蛟，泣孤舟之嫠妇。</p>
        </section>
```
CSS代码如下:

```
          section {
                width: 1024px;
                background-color: #edebe4;
                padding: 20px;
                box-sizing: border-box;
                border: 2px solid #2e2a1b;
                border-radius: 15px;
            }
            section > p {
                text-indent: 2em;
                font: 26px "华文行楷";
                color: #5f5a47;
                margin: 0;
            }
            section:after {
                content: ".";
                height: 0;
                visibility: hidden;
                display: block;
                clear: both;
            }
            <!-- CSS主要代码 -->
            section:not(:first-child) {
                margin-top: 20px;
            }
            section > img {
                width: 160px; height: 160px;
                margin-bottom: 6px;
            }
            section.flImg > img {
                margin-right: 8px;
                float: left;
            }
            section.frImg > img {
                margin-left: 8px;
                float: right;
            }
```
运行效果：

<img src="./images/float（2）.png">
在使用浮动“float”属性的时候有一个需要特别注意的地方，就是若一个<span style="font-size:24px;color:#0b933b;">普通</span>的“块级元素”内的子元素全部都具有浮动属性（值必须为“left”或“right”），那它自身的<span style="font-size:24px;color:#0b933b;">高度会为“0”像素</span>，这是因为它的子元素已经全部脱离了“文档流”，再加上HTML中的普通“块级元素”若不设定“height”为大于“0”的像素值，那它在页面中将不能显示，所以这个元素在页面中的高度固然为“0”。<br><br>
若其子元素全部浮动的元素是独立存在于一个已经参与“定位（本章接下来的内容会讲到）”的元素内的话似乎也没有什么影响，但若它已经参与了“文档流”内的布局了的话，因为其高度为“0”的原因会给后续的元素布局带来些麻烦，我们看看这样一个例子：<br><br>
HTML代码如下:

```
<main>
        <section>
            <img src="./images/bgi-02.jpg" title="这是左浮动图片">
            <p>壬戌之秋，七月既望，苏子与客泛舟游于赤壁之下。清风徐来，水波不兴。举酒属客，诵明月之诗，歌窈窕之章。少焉，月出于东山之上，徘徊于斗牛之间。白露横江，水光接天。纵一苇之所如，凌万顷之茫然。浩浩乎如冯虚御风，而不知其所止；飘飘乎如遗世独立,羽化而登仙...</p>
        </section>
        <section>
            <img src="./images/bgi-04.jpg" title="这是右浮动图片">
            <p>壬戌之秋，七月既望，苏子与客泛舟游于赤壁之下。清风徐来，水波不兴。举酒属客，诵明月之诗，歌窈窕之章。少焉，月出于东山之上，徘徊于斗牛之间。白露横江，水光接天。纵一苇之所如，凌万顷之茫然。浩浩乎如冯虚御风，而不知其所止；飘飘乎如遗世独立,羽化而登仙...</p>
        </section>
    </main>
```
CSS代码如下：

```
       main {
            width: 960px;
        }
        section {
            background-color: #edebe4;
            border: 2px solid #2e2a1b;
            border-radius: 15px;
            padding: 20px;
        }
        section > img{
            width: 240px; height: auto;
            border: 2px solid #af219f;
        }
        section:first-child > img {
            float: left;
        }
        section:last-child {
            margin-top: 20px;
        }
        section:last-child > img {
            float: right;
        }
```
运行效果：

<img src="./images/float（3）.png">
通过上面的示例，我们可以清楚地看到，每个区块元素< section>都没有设置“height”属性，而是想通过该元素内部的子元素自动地“撑起”它的高度，内部的文本的确是撑起了这个< section>元素的高度，但是意外的是，里面的< img>元素的却超出了其父元素< section>的下边界。这是因为代码中的两个< img>元素都设置了“float”属性，第一个值的为“left”，第二个的值为“right”，都脱离了“文档流”，也就是不再占据页面内的高度了，所以出现了以上示例中的情况。要防止元素设置“float”产生的副作用，请学习下一节的内容“清除浮动副作用”。