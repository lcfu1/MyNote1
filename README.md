# 目录

# 一、Android



## 1.1 控件



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