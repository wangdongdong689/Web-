<h2>1：Sublime介绍</h2>
Sublime是一个代码编辑器，可以编写HTML，php,js,css等。


<h2>2：Sublime优点</h2>
(1)跨平台<br>
(2)扩展性强<br>
(3)提交小，运行速度快<br>
(4)支持编辑功能，可以在控制台查看输出<br>
(5)支持大量的插件<br>


<h2>3：Sublime安装</h2>

下载：http://www.sublimetext.com/  
怎样查看版本：conmand/windows+e---》右键属性点击---》系统，系统类型<br>
注意：安装时对应系统的版本
      安装路径不能出现中文字符
      必须安装在计算机硬盘中，不是移动硬盘或者U盘


<h2>4：使用Sublime创建一个HTML文件：</h2>

```
control+N 新建文件
control+S 保存
```
<h6>快速生成html结构快捷键</h6>
1.html:5 然后按tab键
2.! 然后按tab键


<h2>5：新建项目：</h2>
菜单栏单击项目---》下拉框中选择[文件夹添加到项目]---》选择文件夹



<h2>6：Sublime3快速创建html模板</h2>

```
01 安装 Package Control
01.1 ctrl + ` 呼出控制台
01.2 复制(不要带最外层的双引号，该代码仅适用于sublime text 3)“
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'Package Control' + pf.replace(' ','%20')).read())
”
01.3 粘贴到控制台
01.4 回车
02 利用Package Control安装Sublime Tmpl
02.1 ctrl + shift + p 呼出Package Control界面
02.2 输入install
02.3 回车
02.4 输入SublimeTmpl
02.5 回车
03 使用Sublime Tmpl快捷键快速创建html5
03.1 ctrl + alt + h 新建一个html5文件
04.自定义模板
04.1 打开工具(Tools)--插件开发(Developer)--新建代码片段(New Snippet)
04.2 在<![CDATA[和]]>内写下你要的代码片段,注意的是代码片段要靠最左边。
04.3 设置快捷键，把下面tabTrigger标签的注释打开，中间的h就是你的快捷键。
04.4 Ctrl+s保存。名字随便起，但是后缀名必须是.sublime-snippet
04.5 新建一个页面index.html，在index中输入一个h，然后按Tab键，就出现你设置的代码片段了。
05.control+!tab键
如果不行的解决方法https://jingyan.baidu.com/article/ce43664935b90c3772afd377.html
```

<h2>7：破解Sublime</h2>

http://blog.sina.com.cn/s/blog_68e267e10102v76h.html


<h2>8：Sublime插件安装和使用</h2>

```
<h5>插件安装方式一：</h5>
(1)直接安装
(2)下载插件安装包，然后把安装包解压到packages目录中，完成安装（菜单--》首选项---》浏览插件）

<h5>插件安装方式二：</h5>
(1)使用package control组件安装
```


<h2>9：Package control的介绍</h2>
package contro是Sublime软件的插件包管理器，通过该组件，我们可以很方便的管理我们的插件(浏览，安装，卸载)


<h2>10：安装Package control(插件安装包管理器)</h2>

```
(1)检测Sublime是否安装了该组件 ctrl+shift+p 在命令版中输入PC，如果搜索时没有Package control，就证明没有安装<br>
(2)调出控制台窗口control+~
   取消控制台命令：control+~/按esc<br>
(3)找到安装package control命令，在控制台中运行：
如果官网打不开，可以在这个博客里看看：https://www.cnblogs.com/zhangyanbo/p/subltext3.html
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
提示链接失败，表示安装失败，重新输入命令：
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
control shift +p---》install选择Install Package Control---》等一会儿，当弹框提出Package Control was successfully installed...点击确定，控制台出现reloading Settings Package Control/Package Control.sublime-settings表示安装成功
检测组件是否安装成功：按control shift+p---》输入PC下面会出现Package Control:Create Package File...
```

<h2>11:使用package control 安装插件</h2>
<h5>(1)汉化插件ChineseLocalization
步骤：</h5>

```
--control+shift+p
--在命令框中选中Package Control:install Package选中它，按回车
--在命令中输入插件名称，选中插件，按回车
详细步骤：
control shift+P---》instal---》Package Control:Install Package---》左下角有个Loading repositories[= ],LineI,ColumnI---》安装完成会弹出一个插件列表，直接搜索ChineseLocalization点击选择中(如果不行直接关闭重启后再输入一下就可以了)
```
<h5>(2)ConverToUTF8自动把文件编码方式转换为UTF-8</h5>

```
步骤：
control shift+P---》instal---》Package Control:Install Package---》在插件列表里输入ConverToUTF8选中该插件---》左下角会有类似在加载的晃动，加载完成后关闭刚窗口就行
```

<h5>(3)Emmet 能够快速编写HTML、CSS标记的插件</h5>

```
步骤：
control shift+P---》instal---》Package Control:Install Package---》在插件李彪输入emmet----》右下角会有个=号在加载，加载完成后关闭该窗口就行
演示：
<!--后代:>-->
div>ul>li*3 按tab键
<!-- !兄弟：+ -->
div+p+ul
<!-- 分组 -->
div(header>ul>li*4)+footer>p  把光标放在语法的最后面，按tab键
问题：有弹窗是因为没有注册，注册下就行了
<h5>(4)IMESupport是用来支持输入框跟随光标显示的插件(win7、win8、win10)</h5>
步骤：同上
<h5>(5)SublimeCodeintel代码提示插件</h5>
步骤：同上
<h5>(6)SidebarEnhancements侧边栏插件，让侧边栏功能更丰富</h5>
步骤：同上
```

<h2>12：删除插件</h2>
步骤：control shift+P---》remove---》Package Control:Remove Package---》选中想要删除的即可


<h2>13：Markdown语法</h2>
步骤：
先新建一个为.md后缀名的文件
control+shift+p----》install---》Package Control:Remove Package----》markdown---》四个插件全部各安装一遍
检查是否安装成功：首先项---》package Settings,右边既可以看到有没有安装成功<br><br>
<h5>标题</h5>

```
#一级标题##二级标题###二级标题----》按住control+b生成html文件----》.md后缀名文件，#号成灰色状态，选择html文件又击在浏览器中打开
注意：
#标题的时候一定要有空格，这样好看些，如：
# 我是大标题
```
<h5>列表</h5>

- 我是列表
<h5>图片</h5>

![图片名](图片链接地址，如：C：\Users\apple\Desktop\00-前端工具\02-Sublime的使用.md\XX.jpg)
<h5>粗体和斜体</h5>

**粗体** <br>
 *斜体*
<h5>代码引用</h5>

`这里是一个代码段`<br>
```这里是整段代码```
<h5>表格</h5>
|姓名 | 表头1 | 表头1|<br>
|--- |-----| -----|<br>
|年龄 | 内容1 | 内容2|<br>
|性别 | 内容1 | 内容2|<br>

<h2>typora的使用</h2>

官网：https://www.typora.io/<br>
这是Markdown的一款编辑器，还有很多看你自己喜欢哪款你可以在网上搜索自己喜欢的Markdown的编辑器<br>
使用typora可以生成pdf和html文件...pcf、、、
