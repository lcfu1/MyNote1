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
