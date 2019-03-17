<h2>1：Git安装</h2>


https://www.git-scm.com/download/win

<h2>2：初始化Git </h2>

`命令：git init`

<h2>3:配置用户名和邮箱</h2>

```
命令：git config --global user.name "xiaoming"`
命令：git config --global user.email "xiaoming@123456789.com"
```

<h2>4：把代码添加到仓储门口</h2>

```
命令：git add ./00-前端工具 （这里指的的是指定文件里）
简写：git add ./ （把修改过的代码统一的放到仓储门口）
```

<h2>5：把仓储门口的代码放到仓储里去存起来</h2>

`
命令：git commit -m "这是对本次添加东西的说明"<br>
`

问题：如果不写-m 会进入到vim编辑器的模式中去，按i底部会出现--INSERT--，在顶部这里也可以写说明<br>

解决方法：按下esc:q<br>
         如果出现一段红色英文代码退出不了，需要强制提出<br>
         按下esc:q!

<h2>6：把所有修改后的代码一次性放到版本库，4/5可以省略</h2>

`命令：git commit --all -m "这是一次性放到的仓储中的操作" `

<h2>7：在GitHub上创建一个仓库</h2>

`在Git上创建一个仓库，把HTTPS链接复制下来
命令`

<h2>8：提交代码到Github上</h2>

`命令：git push [地址] master`<br>
问题：如果第一次提交要输入Github上账户名和密码


<h2>ssh方式上传代码(以苹果笔记本电脑为例)</h2>

```
1：任意目录右键点击打开Git Bash Here
2：输入命令ssh-keygen -t rsa -C "xiaoming@123456789.com"
3:回车 (指定存储目录的位置，直接按默认)
4：y(已经存在是否覆盖，因之前有有过)
5：回车 (相当于生成一个种子一样的东西)
6：回车
7：验证是否成功：
此电脑---》C盘----》用户---》apple---》.ssh---》公钥id_rsa.pub右击用VSCode打开复制代码----》在GitHub上头像那点击Settings----》SSH and GPG keys--->New SSH key---》把代码黏贴在Key里，在Title那起个名字，按Add SSH Key----》就可以看到我命的my_window了
问题：如果不知道自己用户名，command+r----》cmd回车/确定
8：在GitHub上创建一个仓储New repository----》Ropository name命名---》Creatr repository确定----》点击SSH把地址复制下来
9：在我们写的项目那右键点击打开Git Bash Here---》git init----》git add ./-----》git commit -m "要上传到git上了"----》git push[把Github上刚刚复制的地址黏贴在这]master
```


<h2>补充命令</h2>

```查看当前的状态，可以用来查到当前代码有没有存放到仓储中去
命令：git status (显示工作目录和暂存区的状态)

查看日志
命令：git log             (查看历史提交的日志)
命令：git log --oneline   (查看简洁版的日志)

版本回退
命令：git reset --hart Head~0 (回退到上一次代码提交的状态)
      git reset --hart Head~1 (回退到上上一次代码提交的状态)

回退到某一个版本
命令：git reset --hart [版本号]

查看所有提交的版本号
命令：git reflog

创建分支
命令：git branch [分支名] (创建分支)

切换分支
命令：git checkout [分支名] (切换到这个分支)

查看分支
命令：git branch

合并分支
命令：git merge dev

删除分支
命令：git branch -d dev 
(注意：在自己分支里是删除不了自己的，如：dev分支里有个master分支，想删除dev这个分支,先切换到master分支，在master分支里去删除dev分支)

拉取Github上的代码
注意：*本地要初始化一个仓储*
命令：git init
命令：git pull [地址] master
问题：如果想看日志，输入的是git log提交的次数比较多，命令行里退不出来，直接按q就退出了

通过clone拉取Github上的代码
命令：git clone [地址]
注意：*如果多次执行会覆盖本地的内容*

pull和clone的区别：开发一般都是pull，多次执行它会合并这个项目，不会覆盖，需要在本地初始化一个文件；
                  clone一般第一次拿取数据会使用它，它会在文件夹自动生成一个新的文件，多次执行会覆盖本地的内容；

pull解决冲突;先pull，再push;如果pull代码时，进了vim编辑器的模式,wq保存退出
命令：esc :wq 


push 和pull的简写
命令：git remote add origin [地址]
命令：git push origin  有了上一步操作后，在本目录情况下，push和pull都可以简写


简写master,本地和GitHub关联
命令：git push origin -u master
下一次往GitHub上push时，可以直接
命令：git push  (以下在此目录就可以简写了)

pull不能直接-u相关联时
命令：git pull origin master
命令：git push origin -u master
命令：git push/pull  (以下在此目录就可以简写了)
```
<h2>9.GitHub上面格子为什么没有变绿</h2>
近期我的GitHub上面的绿格子只有我在new repository才会变绿，而我之前创建的new repository上做修改和上传就不会有人颜色变化，于是在网上查了下，解决方法如下：

- 先查看自己git的账户名和邮箱

```
git config user.name
git config user.email
```
然后修改成和GitHub上面一直的账户名和邮箱

```
git config --global user.name "Your_username"
git config --global user.email "Your_email"
```
注意：

- user.name后面有个空格，user.email后面也有空格，必须空格，不然不提示错误也不对
- 最后运行完没有任何提示后，你可以上传一个稍微改动的文件，刷新看看驴哥，此时就有变化了。
<h2>10.git无法pull仓库refusing to merge unrelated histories</h2>

https://lindexi.oschina.io/lindexi/post/git%E6%97%A0%E6%B3%95pull%E4%BB%93%E5%BA%93refusing-to-merge-unrelated-histories.html