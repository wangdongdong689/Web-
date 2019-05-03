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