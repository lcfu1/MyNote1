# 目录

# 一、Android

## 1.1 控件

### 1.1.1 TextView 文本框

**常用属性**：

- android:id：指控件id，在其他地方可通过id找到这个控件，注意书写格式@+id/自己取个id名称。

- android:layout_width：指控件的宽度。

- android:android_height：指控件的高度。

- android:text：指文本内容，可使用 **@string/名** 引用string资源。

- android:textSize：指文本大小，单位推荐用sp。

- android:textColor：指字体颜色。

- android:background：指控件背景，可以是颜色也可以是图片。

**简单使用**：

```
<TextView
        android:id="@+id/textView"
        android:layout_width="200dp"
        android:layout_height="200dp"/>
```

!> @+id就是在R.java文件里新增一个id名称，如果之前已经存在相同的id名称，那么会覆盖之前的名称。而@id则是直接引用R.java文件的存在的id资源，如果不存在，会编译报错。 

### 1.1.2 EditText 可输入文本框

**常用属性**：

- android:hint：指输入提示文本内容。
- android:inputType：指输入文本的类型。
- android:maxLines：指定最大行数。

**简单使用**：

```
<EditText
        android:id="@+id/editText"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
		android:hint="请输入"/>
```

### 1.1.3 Button 按钮

**常用属性**：

- android:text：指按钮中显示的文本内容。
- android:textAllCaps：禁用所有英文字母自动进行大写转换。
- 

**简单使用**：

```
<Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
		android:text="按钮"/>
```

先声明一个Button对象并绑定->用setOnClickListener方法给它安上监听器

```
Button button=(Button)findViewById(R.id.button);

//匿名内部类
button.setOnClickListener(new View.OnClickListener(){
	@Override
	public void onClick(View v){
		//...
	}
});

//独立类
View.OnClickListener OnClickListener=new View.OnClickListener(){
	@Override
	public void onClick(View v){
		//...
	}
});

//接口方式
acivity先实现View.OnClickListener接口，如：
implements View.OnClickListener

button.setOnClickListener(this);

@Override
public void onClick(View v){
	//...
}
```

### 1.1.4 ImageView 显示图片

**常用属性**：

- android:src：指定一张图片。
- android:background：指控件背景，可以是颜色或图片，如果是图片，大小会受控件大小影响，可能会变形。

**简单使用**：

```
<ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
		android:src="@drawable/img"/>
```

### 1.1.5 ImageButton 图片按钮

**常用属性**：

- android:src：指定一张图片。
- android:background：指控件背景，可以是颜色或图片，如果是图片，大小会受控件大小影响，可能会变形。
- 没有android:text属性。

**简单使用**：

```
<ImageButton
        android:id="@+id/imageButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
		android:src="@drawable/img"/>
```

## 1.2 布局



## 1.3 组件



## 1.4 数据存储



## 1.5 碎片



## 1.6 多媒体



## 1.7 网络



## 1.8 面试题

### 1、说一下Activity的生命周期

- 关键点：Activity的生命周期。
- 思路：解释Activity从创建到销毁整个生命周期中涉及到的方法及作用。
- 参考回答：
  - onCreate()表示Activity **正在创建**，常做**初始化**工作，如setContentView界面资源、初始化数据。
  - onStart()表示Activity **正在启动**，这时Activity **可见但不在前台**，无法和用户交互。
  - onResume()表示Activity **获得焦点**，此时Activity **可见且在前台**并开始活动。
  - onPause()表示Activity **正在停止**，可做 **数据存储、停止动画**等操作。
  - onStop()表示activity **即将停止**，可做**稍微重量级回收工作**，如取消网络连接、注销广播接收器等。
  - onDestroy()表示Activity **即将销毁**，常做**回收工作、资源释放**。
  - 另外，当Activity由后台切换到前台，由不可见到可见时会调用onRestart()，表示Activity **重新启动**。

# 二、Java



# 三、JavaWeb



# 四、算法



# 五、Git

## 5.1 命令总结

$ git config –global user.name “Your Name”
设置全局用户名。

$ git config –global user.name
查询用户名。

$ git config –global user.email “Your Email”
设置全局邮箱。

$ git config –global user.email
查询邮箱。

$ git config –list
检查已有的配置信息。

$ git config –global alias.st status
用st表示status。

$ mkdir gitReporitory
mkdir命令是用来创建文件夹的，这里创建一个叫gitreporitory的文件夹。

$ cd gitReporitory
进入gitReporitory文件夹。

$ pwd
显示当前目录。

$ ls
查看当前项目的所有文件。

$ git init
把这个目录变为Git可以管理的仓库。

$ git add hello.txt
添加文件到git仓库上，其中hello.txt就是要添加的文件。

$ cat hello.txt
查看文件的内容，这里查看hello.txt的内容。

$ cat .git/config
查看Git配置文件。

$ git add .
添加所有文件到git仓库上。

$ git commit -m “first commit”
添加完文件还需要提交到git仓库上，-m后面输入的是本次提交的说明。

$ git status
用于检查本地项目的状态，遇到问题就试试它，会有提示。

$ git diff
可以查看哪里有改动过。

$ git rm hello.txt
删除版本库中的hello.txt文件。

$ rm hello.txt
把工作区中的hello.txt文件删除掉，但版本库中的并没有删除掉。

$ git checkout – hello.txt
假设我们修改了hello.txt文件，但还没git add到暂存区，现在想返回到修改前，可以使用$ git checkout – hello.txt返回到没修改的时候。

$ git reset HEAD hello.txt
假设我们修改了hello.txt文件，并git add到了暂存区，但现在我们发现有错误，需要修改，我们可以使用该命令把添加到暂存区的修改撤销回工作区。

$ git reset HEAD hello.txt加$ git checkout – hello.txt
删除版本库中的hello.txt文件后，没提交前我们还可以通过$ git reset HEAD hello.txt加$ git checkout – hello.txt撤消删除。

$ git log
查看修改记录。

$ git log -1
显示最后一次提交信息。

$ git reflog
查看你的每一次命令。

$ git reset –hard
查看当前版本。

$ git reset –hard HEAD^
回退到上一版本。HEAD表示当前版本，HEAD^表示上一版本，HEAD^^表示上上一个版本，HEAD~100则为上100个版本。

$ git reset –hard b6db134
其中b6db134是我刚刚回退前版本的commit id的前七位，Git使用SHA-1算法计算数据的校验和，通过对文件的内容或目录的结构计算出一个SHA-1哈希值，作为指纹字符串，由40个十六进制字符组成，但这里我们用前7位就好了，Git会自动寻找出来的。

$ git help
查看帮助文档。

$ git help add
查看add命令的使用。

$ git branch
查看当前项目所有分支。

$ git branch one
创建一个one分支。

$ git checkout one
切换到one分支。

$ git checkout -b two
创建并切换到two分支。

$ git checkout -b one origin/one
创建远程origin的one分支到本地。

$ git branch –set-upstream-to=origin/branch-name branch-name
创建本地分支和远程分支的链接关系。

$ git checkout master
切换回master分支。

$ git branch -d one
删除one分支。

$ git merge one
合并one分支到master分支上。

$ git merge –no-ff -m “merge with no-ff” one
合并one分支，–no-ff参数用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

$ git log –graph –pretty=oneline –abbrev-commit
用带参数的git log查看分支的合并情况。

$ git stash
保存当前仓库已改变的状态。

$ git stash list
查看保存到哪。

$ git stash apply或$ git stash apply stash@{0}
恢复已保存的状态。

$ git stash drop
删除stash内容。

$ git stash pop
恢复的同时把stash内容也删除。

$ git tag
查看当前所有版本。

$ git tag -a v1.0 -m “这里填相关信息”
为项目版本打个标签。

$ git show v1.0
查看对应版本的相关信息。

$ git clone https://github.com/lcfu1/lcfu1.git
这里是以https的形式下载的，也可以以SSH的格式，如$ git clone git@github.com:lcfu1/lcfu1.git。

$ ssh-keygen -t rsa -b 4096 -C “your_email@example.com”
SSH key的配置，your_email@example.com是你注册github的邮箱。

$ ssh -T git@github.com
查看是否添加成功。

$ git remote add origin git@github.com:lcfu1/Git.git
向本地仓库添加一个名为origin，地址为git@github.com:lcfu1/Git.git的远程仓库。

$ git remote -v
查看该项目的远程仓库。

$ git remote rm origin
删除已有的远程仓库。

$ git remote add github git@github.com:lcfu1/Git.git
关联GitHub的远程库。

$ git push origin master:master
推送到远程仓库，origin是上面我们在本地仓库添加的一个名为origin，地址为git@github.com:lcfu1/Git.git的远程仓库。第一个master是本地的master分支，第二是远程的master分支，如果两个一个则可以简化为$ git push origin master。

$ git push origin master
推送到远程仓库的master分支。

$ git push origin one
推送到远程仓库的one分支。

$ git push github master
推送到GitHub。

$ git pull
更新本地仓库。

$ git push one:master
将本地的one分支推送到远程仓库。

$ git push master:one
删除远程仓库的one分支。

## 5.2 简单使用


# 六、前端



# 七、Oracle



# 八、Gradle



# 九、网络通信



# 十、物联网安全



# 十一、大数据



# 十二、Kotlin



# 十三、Python



# 十四、UML



# 十五、C



# 十六、推荐神器



## 16.1 LICEcap(录屏工具)

下载地址：https://licecap.en.softonic.com/ ，下载并安装。
使用步骤：
1.打开，点击Record…，填写文件名，保存。
2.然后LICEcap就会倒计时3秒后开始录制，点击Stop后保存。

效果图：
![20190117_LICEcap](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190117_LICEcap.gif)



## 16.2 Pointofix(桌面画板工具)

下载地址：http://www.pointofix.de/download.php ，下载并安装。
不过安装好的Pointofix不是中文的，需要在官网下载语言翻译包。

![20190117_PointofixLanguagePack](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190117_PointofixLanguagePack.PNG)

语言翻译包的使用可以看上面图片最后的说明，解压并找到`pointofix_translation_zh-cn.ini`，重命名为`pointofix_translation.ini`，然后放到pointofix的安装目录下即可，重启就变成中文了。



## 16.3 Typora（Markdown编辑器）

描述：Markdown编辑器，支持边输入边预览。
官网：https://www.typora.io/ 。

效果图：

![20190118_Typora](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190118_Typora.gif)



## 16.4 HEditor（HTML/CSS/JavaScript在线编辑器）

效果图：

![20190120_HEditor](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190120_HEditor.PNG)



## 16.5 Kotlin在线编辑器

描述：JetBrains官方的kotlin在线编辑器。

使用：<https://try.kotlinlang.org/>

效果图：

![20190120_Kotlin](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190120_Kotlin.PNG)



## 16.6 shields

描述：Concise, consistent, and legible badges in SVG and raster format。

项目的github地址：<https://github.com/badges/shields>

使用：<https://shields.io/>

效果：

[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/lcfu1/MyNote)  [![Packagist](https://img.shields.io/packagist/l/doctrine/orm.svg)](https://github.com/lcfu1/MyNote/blob/master/LICENSE)



# 十七、推荐网站

- Android Developers: https://developer.android.google.cn/index.html
- Codelabs: http://clmirror.storage.googleapis.com/index.html
- wanandroid: http://www.wanandroid.com/
- 廖雪峰的官方网站: https://www.liaoxuefeng.com/
- GitHub: https://github.com/
- 开源中国: http://www.oschina.net/
- InfoQ: http://www.infoq.com/cn
- CSDN: https://www.csdn.net/
- 极客学院: http://www.jikexueyuan.com/
- V2EX: https://www.v2ex.com/
- 知乎: https://www.zhihu.com/
- stackoverflow: https://stackoverflow.com/
- 简书：https://www.jianshu.com/

# 十八、推荐好书

## 18.1 Android

- 第一行代码 - 郭霖
- Android开发艺术探索 - 任玉刚
- Android编程权威指南（3）
- Android开发进阶从小工到专家 - 何红辉
- 巧用Gradle构建Android应用 - Ken Kousen

## 18.2 Java

- java 2 实用教程(第四版)
- java编程思想

# 十九、推荐资源

- https://github.com/open-android/Android
- https://www.jianshu.com/p/9618c038135f
