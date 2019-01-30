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


## 1.8 Material Design

### 1.8.1 Bottom Navigation 底部导航栏

**一、介绍**

这里我就不介绍Material Design了,想了解更多就去看看官网，来看看他们自己的Introduction：(温馨提示：由于本人英语水平有限，以下引用均用有道翻译来翻译)
> We challenged ourselves to create a visual language for our users that synthesizes the classic principles of good design with the innovation and possibility of technology and science. This is material design. This spec is a living document that will be updated as we continue to develop the tenets and specifics of material design. 我们挑战自己，为我们的用户创造一种视觉语言，它综合了优秀设计的经典原则和技术和科学的可能性。这是材料设计。这个规范是一个活的文件，将会更新，因为我们继续发展的原则和材料设计的细节。

Bottom Navigation，想要使用Bottom Navigation，个人建议先看一下Bottom Navigation的设计，再来学习怎么用它。
> Bottom navigation bars make it easy to explore and switch between top-level views in a single tap. 底部导航条使得在单个点击中探索和切换顶级视图变得很容易。

> Tapping on a bottom navigation icon takes you directly to the associated view or refreshes the currently active view. 点击底部导航图标将直接带您到相关视图或刷新当前活动视图。

> Bottom navigation is primarily for use on mobile. To achieve a similar effect for desktop, use side navigation. 底部导航主要用于移动设备。为了达到类似的效果，桌面，使用边导航。

> Usage Three to five top-level destinations Destinations requiring direct access 3到5个顶级目的地 目的地需要直接访问

> Color Tint the active icon with the app’s primary color. Use black or white if the bottom navigation bar is already colored. 用app的主色来着色活动图标。如果底部导航栏已经着色，请使用黑色或白色。

> Specs Width of each action: The width of the view divided by the number of actions (with a max of 168dp and a minimum of 80dp) Height: 56dp Icon: 24 x 24dp 每个动作的宽度:视图的宽度除以操作数(最大值为168dp，最小为80dp) 高度:56 dp 图标:24×24 dp

**二、使用**

- 最快的方法就是在android studio中直接新建一个Bottom Navigation Activity。当然也可以新建一个Empty Activity。
- 首先添加以下依赖：

`implementation 'com.android.support.constraint:constraint-layout:1.0.2'`

1、MainActivity.java
```
package com.example.lcf.myapplication;

import android.os.Bundle;
import android.support.annotation.NonNull;
import android.support.design.widget.BottomNavigationView;
import android.support.v7.app.AppCompatActivity;
import android.view.MenuItem;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    private TextView mTextMessage;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mTextMessage = (TextView) findViewById(R.id.message);

        BottomNavigationView navigation = (BottomNavigationView) findViewById(R.id.navigation);
        navigation.setOnNavigationItemSelectedListener(new BottomNavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {
                switch (item.getItemId()) {
                    case R.id.navigation_home:
                        mTextMessage.setText(R.string.title_home);
                        return true;
                    case R.id.navigation_edit:
                        mTextMessage.setText(R.string.title_edit);
                        return true;
                    case R.id.navigation_dashboard:
                        mTextMessage.setText(R.string.title_dashboard);
                        return true;
                    case R.id.navigation_notifications:
                        mTextMessage.setText(R.string.title_notifications);
                        return true;
                }
                return false;
            }
        });
    }
}
```

2、activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.example.lcf.myapplication.MainActivity">

    <TextView
        android:id="@+id/message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="@dimen/activity_horizontal_margin"
        android:layout_marginStart="@dimen/activity_horizontal_margin"
        android:layout_marginTop="@dimen/activity_vertical_margin"
        android:text="@string/title_home"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <android.support.design.widget.BottomNavigationView
        android:id="@+id/navigation"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="0dp"
        android:layout_marginStart="0dp"
        android:background="?android:attr/windowBackground"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:menu="@menu/navigation" />

</android.support.constraint.ConstraintLayout>
```

3、navigation.xml，右击menu文件夹新建一个Menu resource file，name为navigation，由于我在这里使用了vector drawable，所以还要添加以下依赖implementation 'com.android.support:support-vector-drawable:26.1.0'。navigation.xml的代码如下：

```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/navigation_home"
        android:icon="@drawable/ic_home_black_24dp"
        android:title="@string/title_home" />
    <item
        android:id="@+id/navigation_edit"
        android:icon="@drawable/ic_edit_black_24dp"
        android:title="@string/title_edit" />
    <item
        android:id="@+id/navigation_dashboard"
        android:icon="@drawable/ic_dashboard_black_24dp"
        android:title="@string/title_dashboard" />

    <item
        android:id="@+id/navigation_notifications"
        android:icon="@drawable/ic_notifications_black_24dp"
        android:title="@string/title_notifications" />

</menu>
```

4、效果如下：

![20190129_bottom_navigation_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_bottom_navigation_1.PNG)

![20190129_bottom_navigation_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_bottom_navigation_2.PNG)

如果只有三个动作，则始终显示图标和文本标签 如果有四个或五个操作，则仅将非活动视图显示为图标。

### 1.8.2 DrawerLayout+NavigationView 实现滑动菜单效果

一、新建一个项目

- 可以New一个Project，选择Navigation Drawer Activity Mobile。这样新建的项目就有滑动菜单了。可以看个人情况再进行修改。
Gradle中会自动添加以下依赖:

`implementation 'com.android.support:design:26.1.0'`

- 如果不是选择Navigation Drawer Activity Mobile，且你项目中没有以上依赖，就需要自己添加上，File–>Project Structure–>app–>Dependencies–>Library Dependency。

![20190129_drawerLayout_navigationView_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_drawerLayout_navigationView_1.PNG)

二、java文件

1、MainActivity.java

```
package com.example.lcf.myapplication;

import android.os.Bundle;
import android.support.design.widget.FloatingActionButton;
import android.support.design.widget.Snackbar;
import android.support.v7.app.ActionBar;
import android.view.View;
import android.support.design.widget.NavigationView;
import android.support.v4.view.GravityCompat;
import android.support.v4.widget.DrawerLayout;
import android.support.v7.app.ActionBarDrawerToggle;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;
import android.view.Menu;
import android.view.MenuItem;

public class MainActivity extends AppCompatActivity
        implements NavigationView.OnNavigationItemSelectedListener {
    DrawerLayout drawer;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        FloatingActionButton fab = (FloatingActionButton) findViewById(R.id.fab);
        fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Snackbar.make(view, "Replace with your own action", Snackbar.LENGTH_LONG)
                        .setAction("Action", null).show();
            }
        });

        drawer = (DrawerLayout) findViewById(R.id.drawer_layout);

        //这里加入了导航按钮图标
        ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(
                this, drawer, toolbar, R.string.navigation_drawer_open, R.string.navigation_drawer_close);
        drawer.addDrawerListener(toggle);
        toggle.syncState();
        
//        //也可以通过以下方法来设置 导航按钮图标       
//        ActionBar actionBar=getSupportActionBar();
//        if(actionBar!=null){
//            actionBar.setDisplayHomeAsUpEnabled(true);
//            //这里设置一张图片来当导航按钮图标（HomeAsUp按钮，id为android.R.id.home），需要在onOptionsItemSelected中设置点击处理。
//            actionBar.setHomeAsUpIndicator(R.mipmap.ic_launcher);
//        }

        NavigationView navigationView = (NavigationView) findViewById(R.id.nav_view);
        navigationView.setNavigationItemSelectedListener(this);
    }

    @Override
    public void onBackPressed() {
        drawer = (DrawerLayout) findViewById(R.id.drawer_layout);
        if (drawer.isDrawerOpen(GravityCompat.START)) {
            drawer.closeDrawer(GravityCompat.START);
        } else {
            super.onBackPressed();
        }
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
//        }else if(id ==android.R.id.home){
//            drawer.openDrawer(GravityCompat.START);
        }

            return super.onOptionsItemSelected(item);
    }

    @SuppressWarnings("StatementWithEmptyBody")
    @Override
    public boolean onNavigationItemSelected(MenuItem item) {
        // Handle navigation view item clicks here.
        int id = item.getItemId();

        if (id == R.id.nav_camera) {
            // Handle the camera action
        } else if (id == R.id.nav_gallery) {

        } else if (id == R.id.nav_slideshow) {

        } else if (id == R.id.nav_manage) {

        } else if (id == R.id.nav_share) {

        } else if (id == R.id.nav_send) {

        }

        DrawerLayout drawer = (DrawerLayout) findViewById(R.id.drawer_layout);
        drawer.closeDrawer(GravityCompat.START);
        return true;
    }
}
```

三、layout文件

1、activity_main.xml

NavigationView中设置了android:fitsSystemWindows=”true”，view会自动添加一个值等于状态栏高度(注意：它的所有父类都要设置这个属性才行，不然没用，另外，还要指定状态栏为透明的，如@android:color/transparent)，不过android:statusBarColor属性从API21才有的，创建一个values-v21目录，添加一个styles.xml。如下：

```
<resources>
    <style name="AppTheme.NoActionBar">
        <item name="windowActionBar">false</item>
        <item name="windowNoTitle">true</item>
        <item name="android:statusBarColor">@android:color/transparent</item>
    </style>
</resources>
```

上面的是values-v21目录中的styles.xml，而values目录中的如下：

```
<style name="AppTheme.NoActionBar">
    <item name="windowActionBar">false</item>
    <item name="windowNoTitle">true</item>
</style>
```

需要注意的是AndroidManifest.xml中MainActivity主题设置为android:theme=”@style/AppTheme.NoActionBar”。

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.v4.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/drawer_layout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true"
    tools:openDrawer="start">

    <include
        layout="@layout/app_bar_main"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <android.support.design.widget.NavigationView
        android:id="@+id/nav_view"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"
        app:headerLayout="@layout/nav_header_main"
        app:menu="@menu/activity_main_drawer" />

</android.support.v4.widget.DrawerLayout>
```

!> app:headerLayout=”@layout/nav_header_main”指定头布局
app:menu=”@menu/activity_main_drawer”指定NavigationView中的菜单布局。DrawerLayout 中允许放入两个直接子控件。

2、app_bar_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.lcfu1.myapplication.MainActivity">

    <android.support.design.widget.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:theme="@style/AppTheme.AppBarOverlay">

        <android.support.v7.widget.Toolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:popupTheme="@style/AppTheme.PopupOverlay" />

    </android.support.design.widget.AppBarLayout>

    <include layout="@layout/content_main" />

    <android.support.design.widget.FloatingActionButton
        android:id="@+id/fab"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom|end"
        android:layout_margin="@dimen/fab_margin"
        app:srcCompat="@android:drawable/ic_dialog_email" />

</android.support.design.widget.CoordinatorLayout>
```

3、content_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layout_behavior="@string/appbar_scrolling_view_behavior"
    tools:context="com.lcfu1.myapplication.MainActivity"
    tools:showIn="@layout/app_bar_main">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</android.support.constraint.ConstraintLayout>
```

4、nav_header_main.xml头布局，ImageView中app:srcCompat=”@mipmap/ic_launcher_round”是个圆形的图片，如果你的图片不是圆形的，可以添加以下依赖implementation 'de.hdodenhof:circleimageview:2.1.0'，CircleImageView是个可以使图片圆形化的控件。使用方法如下面注释部分。

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="@dimen/nav_header_height"
    android:background="@drawable/side_nav_bar"
    android:gravity="bottom"
    android:orientation="vertical"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:theme="@style/ThemeOverlay.AppCompat.Dark">

    <!--<de.hdodenhof.circleimageview.CircleImageView-->
        <!--android:id="@+id/imageView"-->
        <!--android:layout_width="70dp"-->
        <!--android:layout_height="70dp"-->
        <!--android:paddingTop="@dimen/nav_header_vertical_spacing"-->
        <!--android:src="@drawable/a" />-->
    <ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:paddingTop="@dimen/nav_header_vertical_spacing"
        app:srcCompat="@mipmap/ic_launcher_round" />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:paddingTop="@dimen/nav_header_vertical_spacing"
        android:text="Android Studio"
        android:textAppearance="@style/TextAppearance.AppCompat.Body1" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="android.studio@android.com" />

</LinearLayout>
```

四、menu文件

1、activity_main_drawer.xml这个是NavigationView中的菜单布局，android:checkableBehavior=”single”表示只能单选。

```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    tools:showIn="navigation_view">

    <group android:checkableBehavior="single">
        <item
            android:id="@+id/nav_camera"
            android:icon="@drawable/ic_menu_camera"
            android:title="Import" />
        <item
            android:id="@+id/nav_gallery"
            android:icon="@drawable/ic_menu_gallery"
            android:title="Gallery" />
        <item
            android:id="@+id/nav_slideshow"
            android:icon="@drawable/ic_menu_slideshow"
            android:title="Slideshow" />
        <item
            android:id="@+id/nav_manage"
            android:icon="@drawable/ic_menu_manage"
            android:title="Tools" />
    </group>

    <item android:title="Communicate">
        <menu>
            <item
                android:id="@+id/nav_share"
                android:icon="@drawable/ic_menu_share"
                android:title="Share" />
            <item
                android:id="@+id/nav_send"
                android:icon="@drawable/ic_menu_send"
                android:title="Send" />
        </menu>
    </item>

</menu>
```

2、main.xml菜单布局

```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/action_settings"
        android:orderInCategory="100"
        android:title="@string/action_settings"
        app:showAsAction="never" />
</menu>
```

五、截图

我是在android5.0上测试的,这是设置了android:fitsSystemWindows=”true”的。可以观察一下手机状态栏，状态栏是透明的，而头布局在它伸展到状态栏下。

![20190129_drawerLayout_navigationView_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_drawerLayout_navigationView_2.PNG)

如果没有设置fitsSystemWindows，就会出现如下效果。

![20190129_drawerLayout_navigationView_3](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_drawerLayout_navigationView_3.PNG)

### 1.8.3 android可折叠式标题栏

一、代码

1、MainActivity.java

```
package com.example.lcf.myapplication;

import android.os.Bundle;
import android.support.design.widget.CollapsingToolbarLayout;
import android.support.v7.app.ActionBar;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;


public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        CollapsingToolbarLayout collapsingToolbarLayout = (CollapsingToolbarLayout) findViewById(R.id.coll);
        //设置展示的文字
        collapsingToolbarLayout.setTitle("学习");
        //设置展示文字的颜色
        collapsingToolbarLayout.setExpandedTitleColor(getResources().getColor(R.color.colorAccent));
    }
}
```

2、activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true">

    <android.support.design.widget.AppBarLayout
        android:id="@+id/appbar"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:fitsSystemWindows="true">

        <android.support.design.widget.CollapsingToolbarLayout
            android:id="@+id/coll"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:fitsSystemWindows="true"
            app:contentScrim="@color/colorPrimary"
            app:layout_scrollFlags="scroll|exitUntilCollapsed">

            <ImageView
                android:id="@+id/bg"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:fitsSystemWindows="true"
                android:scaleType="centerCrop"
                app:layout_collapseMode="parallax"
                app:srcCompat="@drawable/ic_launcher_background" />

            <android.support.v7.widget.Toolbar
                android:id="@+id/toolbar"
                android:layout_width="match_parent"
                android:layout_height="50dp"
                app:layout_collapseMode="pin">

                <ImageView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginRight="10dp"
                    app:srcCompat="@drawable/ic_arrow_back_black_24dp" />
            </android.support.v7.widget.Toolbar>
        </android.support.design.widget.CollapsingToolbarLayout>
    </android.support.design.widget.AppBarLayout>

    <android.support.v4.widget.NestedScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="hello" />
        </LinearLayout>
    </android.support.v4.widget.NestedScrollView>

    <android.support.design.widget.FloatingActionButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="16dp"
        app:layout_anchor="@id/appbar"
        app:layout_anchorGravity="bottom|end"
        app:srcCompat="@drawable/ic_edit_black_24dp" />
</android.support.design.widget.CoordinatorLayout>
```

二、详解

- CollapsingToolbarLayout只能作为AppBarLayout的子布局使用
- app:contentScrim=”@color/colorPrimary”折叠后的背景色
- app:layout_scrollFlags="scroll|exitUntilCollapsed"滚动并保留toolbar在界面上，如果想全部滚出，就只设置scroll。
- ImageView中设置app:layout_collapseMode=”parallax”，就是折叠过程中会产生偏移。而Toolbar中设置app:layout_collapseMode=”pin”，折叠过程中位置不变。
- 为了ImageView能够与状态栏融合，需要设置android:fitsSystemWindows=”true”属性，不过只在ImageView中设置android:fitsSystemWindows=”true”属性是没用的，它的所有父布局如CollapsingToolbarLayout、AppBarLayout、CoordinatorLayout都要设置，并且还要在styles.xml中设置android:statusBarColor属性，styles.xml如下：

```
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimary</item>
        <item name="colorAccent">@color/colorAccent</item>
        <item name="android:statusBarColor">@android:color/transparent</item>
    </style>

</resources>
```

- NestedScrollView实现内部文字滚动

- FloatingActionButton悬浮按钮，app:layout_anchor=”@id/appbar”指定一个锚点，设置app:layout_anchorGravity让悬浮按钮显示在AppBarLayout右下角。

三、效果

![20190129_collapsingtoolbarlayout](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_collapsingtoolbarlayout.gif)

## 1.9 自定义View

### 1、屏幕坐标系

手机屏幕左上角为坐标原点，向右为x轴增大方向，向下为y轴增大方向

如下图：

![20190129_view_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_1.PNG)

### 2、view的坐标

view的坐标是相对父容器而言的，包括：getTop()、getBottom()、getLeft()、getRight()。

如下图：

![20190129_view_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_2.PNG)

从android3.0开始，View增加了几个参数：x、y、translationX和traslationY，x和y是View左上角的坐标，而translationX和traslationY是View左上角相对于父容器的偏移量。这几个参数是相对于父容器的坐标，并且translationX和traslationY的默认值是0，和View的四个基本的位置参数一样，View也提供了get和set方法。这几个参数的换算关系如下： x=left+translationX y=top+translationY View在平移的过程中， top和left表示原始左上角的位置信息，它们的值并不会发生改变，此时发生改变的是x、y、translationX和traslationY这四个参数。

### 3、MotionEvent和TouchSlop

MotionEvent中的getRaw和get：

- event.getRowX()、event.getRowY()：触摸点相对于屏幕原点的x坐标
- event.getX()、event.getY()： 触摸点相对于其所在组件原点的x坐标

![20190129_view_3](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_3.PNG)

TouchSlop：

- TouchSlop是系统所能识别出的被认为是滑动的最小距离，就是两次滑动之间的距离小于这个常量，系统就不认为你在进行滑动操作，这是一个常量，和设备有关。获取方法：ViewConfiguration.get(getContext()).getScaledTouchSlop()。

### 4、角度与弧度

注：默认的屏幕坐标系中角度增大方向为顺时针

角度：角度是60进制，两条射线从圆心向圆周射出，形成一个夹角和夹角正对的一段弧。当这段弧长正好等于圆周长的360分之一时，两条射线的夹角的大小为1度。

如下图：

![20190129_view_4](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_4.PNG)

弧度：弧度是10进制，两条射线从圆心向圆周射出，形成一个夹角和夹角正对的一段弧。当这段弧长正好等于圆的半径时，两条射线的夹角大小为1弧度。

如下图：

![20190129_view_5](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_5.PNG)

角度和弧度的换算：rad = deg x π / 180，deg = rad x 180 / π，其中rad是弧度，deg是角度。圆的周长为2πr，由上面弧度概念可知圆360度对应2π弧度。

### 5、简介颜色

屏幕上默认的模式是RGB565，而我们常用的都是ARGB8888（四通道高精度(32位)）和ARGB4444（四通道低精度(16位)），还有一种不常用的Alpha8（仅有透明通道(8位)）。

ARGB通道，其中RGB是红绿蓝，A是Alpha（通常用来作为此颜色的透明度），取值范围均为0~255，RGB 从0x00到0xff表示颜色从深到浅，A 从ox00到oxff表示从透明到不透明。

在Android Studio中打开一张图片，在左上角可以看到一个绿色吸管（颜色选择器）。

如下图：

![20190129_view_6](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_6.PNG)

点击打开，在中间的圆圈色板中选择任意颜色可得到它的RGB值，不过它还有个功能，点击下图红色圈出的绿色吸管，你就可以查看电脑当前屏幕中任意颜色的RGB值。

![20190129_view_7](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_7.PNG)

注：Android Studio界面不要最大化，然后把你想要查的图片或其它画面和它放在电脑的同一屏幕下。别小看这个小功能，很实用的。

如下gif图（有点模糊，将就看）：

![20190129_view_8](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_8.gif)

### 6、颜色混合模式

安卓着色器(tint)可以为图标着色，既可以在xml中，也可以在代码中设置，一共有16种颜色混合模式。

如下图：

![20190129_view_9](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_9.PNG)

- Clear：在底部中清除内容所在的区域
- Dst：可以看做底部的背景
- Src：可以看做上面的内容
- Srcover：内容覆盖在背景之上
- DstOver：背景覆盖在内容之上
- SrcIn:显示Src和Dst相交的Src区域
- Dstin：显示相交的Dst区域
- SrcOut：显示不相交的Src区域
- DstOut：显示不相交的Dst区域
- SrcAtTop:显示Dst所在的区域，相交区域显示Src
- DstAtTop：显示Src所在区域，相交区域显示Dst
- Xor：异或，相交区域不显示，其他区域保留
- Sarken：Src覆盖在Dst之上，相交区域Src以最暗显示
- Lighten：Src覆盖在Dst之上，相交区域Src以最亮显示
- Multiply：显示相交区域的混合
- Screen：显示全部区域，相交区域以全色显示，即白色

Alpha通道主要在两个图像混合的时候生效。默认情况下，当一个颜色绘制到Canvas上时的混合模式是这样计算的：(RGB通道) 最终颜色 = 绘制的颜色 + (1 - 绘制颜色的透明度) × Canvas上的原有颜色。绘制颜色和原有颜色都是经过预乘了自己的Alpha通道的值的。

PorterDuff模式的混合计算公式：（D指原本在Canvas上的内容dst，S指绘制输入的内容src，a指alpha通道，c指RGB各个通道）。

- ADD：Saturate(S + D)
- CLEAR：[0, 0]
- DARKEN：[Sa + Da - SaDa, Sc(1 - Da) + Dc*(1 - Sa) + min(Sc, Dc)]
- DST：[Da, Dc]
- DST_ATOP：[Sa, Sa * Dc + Sc * (1 - Da)]
- DST_IN：[Sa * Da, Sa * Dc]
- DST_OUT：[Da * (1 - Sa), Dc * (1 - Sa)] 
- DST_OVER：[Sa + (1 - Sa)Da, Rc = Dc + (1 - Da)Sc]
- LIGHTEN：[Sa + Da - SaDa, Sc(1 - Da) + Dc*(1 - Sa) + max(Sc, Dc)]
- MULTIPLY：[Sa * Da, Sc * Dc]
- SCREEN：[Sa + Da - Sa * Da, Sc + Dc - Sc * Dc]
- SRC：[Sa, Sc]
- SRC_ATOP：[Da, Sc * Da + (1 - Sa) * Dc]
- SRC_IN：[Sa * Da, Sc * Da]
- SRC_OUT：[Sa * (1 - Da), Sc * (1 - Da)]
- SRC_OVER：[Sa + (1 - Sa)Da, Rc = Sc + (1 - Sa)Dc]
- XOR：[Sa + Da - 2 * Sa * Da, Sc * (1 - Da) + (1 - Sa) * Dc]

### 7、定义颜色

上面简单了解了一下颜色的相关内容，现在来介绍一下使用。

在java中定义使用：

```
int color= Color.BLUE;//蓝色
int color1= Color.rgb(0,0,255);//蓝色
int color2= Color.argb(127,0,0,255);//半透明度蓝色
int color3=0xff0000ff;//蓝色带透明度
int color4=getResources().getColor(R.color.blue);//引用xml中定义的颜色
```

在xml中定义：

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!--蓝色-->
    <color name="blue">#0000ff</color>
    <!--半透明度蓝色-->
    <color name="blue1">#7f0000ff</color>
</resources>
```

### 8、自定义View绘制流程

![20190129_view_10](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_10.PNG)

**构造函数**

四种重载：

```
//一般在直接New一个View的时候调用。
public void SimpleView(Context context) {}
//一般在layout文件中使用的时候会调用，关于它的所有属性(包括自定义属性)都会包含在attrs中传递进来。
public void SimpleView(Context context, AttributeSet attrs) {}
//调用了三个参数的构造函数，必须明确指定第三个参数，第三个参数是默认的Style（当前Application或Activity所用的Theme中的默认Style）。
public void SimpleView(Context context, AttributeSet attrs, int defStyleAttr) {}
public void SimpleView(Context context, AttributeSet attrs, int defStyleAttr, int defStyleRes) {}
```

使用：

在activity中：

`SimpleView view=new SimpleView(this);`

在layout中：

```
<com.lcfu1.view.SimpleView
  android:layout_width"wrap_content"
  android:layout_height"wrap_content"/>
```

**onMeasure()**

测量View大小，View的大小不仅由自身所决定，同时也会受到父控件的影响。

```
@Override
protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        super.onMeasure(widthMeasureSpec, heightMeasureSpec);

        int widthMode = MeasureSpec.getMode(widthMeasureSpec);
        int widthSize = MeasureSpec.getSize(widthMeasureSpec);
        int heightMode = MeasureSpec.getMode(heightMeasureSpec);
        int heightSize = MeasureSpec.getSize(heightMeasureSpec);
}
```

widthMeasureSpec 和 heightMeasureSpec两个 int 类型的参数，是由宽、高和各自方向上对应的测量模式来合成的一个值。getMode()：测量模式，getSize()：确切数值。

SpecMode类型：

- UNSPECIFIED：父视图没有给子视图任何限制，子视图可以设置为任意大小。
- EXACTLY：表示父视图已经确切的指定了子视图的大小，match_parent、具体的数值（如100dp）对应的都是这个模式。
- AT_MOST：表示子视图具体大小没有尺寸限制，但是存在上限，上限一般为父视图大小，一般来说wrap_content对应这种模式。

**onSizeChanged()**

```
@Override
protected void onSizeChanged(int w, int h, int oldw, int oldh) {
	super.onSizeChanged(w, h, oldw, oldh);
}
```

在视图大小发生改变时调用。w和h就是View最终的大小。

**onLayout()**

```
@Override
protected void onLayout(boolean changed, int left, int top, int right, int bottom) {
	super.onLayout(changed, left, top, right, bottom);
}
```

确定布局的函数，用于确定子View的位置，在自定义ViewGroup中会用到，他调用的是子View的layout函数。

在自定义ViewGroup中，onLayout一般是循环取出子View，然后经过计算得出各个子View位置的坐标值。

对于非ViewGroup类型来说，它需要做的工作只是测量尺寸与绘制自身内容。

**onDraw()**

```
@Override
public void onDraw(Canvas canvas)
{
	super.onDraw(canvas);
}
```

就是实际绘制内容。

### 9、绘制随手移动的小球

```
package com.lcfu1.view;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.util.AttributeSet;
import android.view.MotionEvent;
import android.view.View;

public class DrawView extends View
{
	//小球的初始位置
	public float currentX = 50;
	public float currentY = 50;

	// 定义、并创建画笔
	Paint p = new Paint();

	public DrawView(Context context)
	{
		super(context);
	}
	public DrawView(Context context , AttributeSet set)
	{
		super(context,set);
	}
	
	//绘制内容
	@Override
	public void onDraw(Canvas canvas)
	{
		super.onDraw(canvas);
                // 设置画布的颜色
		canvas.drawColor(Color.GRAY);
		// 设置画笔的颜色
		p.setColor(Color.RED);
		// 绘制一个小圆（作为小球）
		canvas.drawCircle(currentX, currentY, 15, p);
	}
	// 为该组件的触碰事件重写事件处理方法
	@Override
	public boolean onTouchEvent(MotionEvent event)
	{
		// 修改currentX、currentY两个属性
		currentX = event.getX();
		currentY = event.getY();
		// 通知当前组件重绘自己
		invalidate();
		// 返回true表明该处理方法已经处理该事件
		return true;
	}
}
```

在现实中要画东西就需要画纸，而要在屏幕上面画东西，则需要Canvas，也就是画布。

### 10、Canvas

常用方法如下：

![20190129_view_11](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_11.PNG)

例：

drawColor(int color)：设置画布的颜色，如：

```
canvas.drawColor(Color.GRAY);
```

drawPaint([Paint paint)：画点，如:

```
canvas.drawPoint(10,10,paint); 
```

drawPoints(float[] pts,Paint paint)：画一组点，如：

```
canvas.drawPoints(new float[]{100,100,130,100},paint);
```

drawLine(float startX, float startY, float stopX, float stopY, Paint paint)：画线，如画一条横线：

```
canvas.drawLine(100,100,200,100,paint);
```

drawLines(float[] pts,Paint paint)：画一组线，如画两条横线：

```
canvas.drawLines(new float[]{100,100,200,100,100,200,200,200},paint);
```

drawCircle(float cx, float cy, float radius, Paint paint)：画圆，如：

```
canvas.drawCircle(100, 100, 15, paint);
```

drawRect(float left, float top, float right, float bottom, Paint paint)：画距形，如：

```
canvas.drawRect(100,100,200,200,paint);
```

drawRoundRect(float left, float top, float right, float bottom, float rx, float ry, Paint paint)：画圆角距形，如：

```
canvas.drawRoundRect(100,100,200,200,20,20,paint);
```

不过上面这种方法在API21及以上才能使用。如果是API21以下，我们可以使用如下方法:

```
RectF rectF=new RectF(100,100,200,200);
canvas.drawRoundRect(rectF,20,20,paint);
```

drawOval(float left, float top, float right, float bottom,Paint paint)：画椭圆，如：

```
canvas.drawOval(100,100,200,200,paint);
```

不过上面这种方法同画圆角距形一样，在API21及以上才能使用。如果是API21以下，我们可以使用如下方法:

```
RectF rectF = new RectF(100,100,200,200);
canvas.drawOval(rectF,paint);
```

drawArc(float left, float top, float right, float bottom, float startAngle, float sweepAngle, boolean useCenter, Paint paint)：画圆弧，在API21及以上才能使用，其中startAngle是开始角度、sweepAngle是扫过角度、useCenter是是否使用中心，使用中心绘制出来的图形类似于一个扇形，而设置为false则是圆弧起始点和结束点之间的连线加上圆弧围成的图形。如：

```
canvas.drawArc(100,100,200,200,0,90,false,paint);
```

drawArc(RectF oval, float startAngle, float sweepAngle, boolean useCenter, Paint paint)：也是画圆弧，如果是API21以下，我们可以使用以上这种方法，如：

```
RectF rectF = new RectF(100,100,200,200);
canvas.drawArc(rectF,0,90,true,paint);
```

translate(float dx, float dy)：位移，translate是坐标系的移动，如果有多个translate()，则是基于当前位置移动，而不是每次都基于屏幕左上角的(0,0)点移动。如下：

```
//设置画笔颜色
mPaint.setColor(Color.BLACK);
canvas.translate(100,100);
canvas.drawCircle(0,0,10,mPaint);
canvas.translate(100,100);
canvas.drawCircle(0,0,10,mPaint);
canvas.translate(100,-100);
canvas.drawCircle(0,0,10,mPaint);
```

![20190129_view_12](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_12.PNG)

scale(float sx, float sy)：缩放，缩放的中心默认为坐标原点，而缩放中心轴就是坐标轴，当缩放比例为负数的时候会根据缩放中心轴进行翻转。

```
mPaint.setColor(Color.BLACK);//设置画笔颜色
canvas.translate(100,100);//移动坐标系原点到（100，100）
canvas.drawCircle(0,0,100,mPaint);//画圆
canvas.scale(0.5f,0.5f);// 画布缩放
mPaint.setColor(Color.YELLOW);// 改变画笔颜色为黄色
canvas.drawCircle(0,0,100,mPaint);//画圆
```

![20190129_view_13](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_13.PNG)

scale(float sx, float sy, float px, float py)：这个方法可以控制缩放中心的位置，缩放中心就是对应坐标系的原点。如果使用了translate()，坐标系位置发生了改变，则缩放中心的位置是改变后对应的坐标原点，而不是屏幕左上角的(0,0)点。如：

```
mPaint.setColor(Color.BLACK);//设置画笔颜色
canvas.translate(100,100);//移动坐标系原点到（100，100）
canvas.drawCircle(0,0,100,mPaint);//画圆
canvas.scale(0.5f,0.5f,0,0);// 画布缩放
mPaint.setColor(Color.YELLOW);// 改变画笔颜色为黄色
canvas.drawCircle(0,0,100,mPaint);//画圆
```

![20190129_view_14](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_14.PNG)

scale是可以叠加的，如下：

```
mPaint.setColor(Color.BLACK);//设置画笔颜色
mPaint.setStyle(Paint.Style.STROKE);//描边
mPaint.setStrokeWidth(20f);//设置画笔宽度为10px
canvas.translate(100,100);//移动坐标系原点到（100，100）
canvas.drawCircle(0,0,100,mPaint);//画圆
canvas.scale(0.5f,0.5f);// 画布缩放
canvas.drawCircle(0,0,100,mPaint);//画圆
canvas.scale(0.5f,0.5f);// 画布缩放
canvas.drawCircle(0,0,100,mPaint);//画圆
```

![20190129_view_15](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_15.PNG)

rotate(float degrees)：以当前坐标原点旋转，跟scale一样有控制中心和可叠加。如：

```
mPaint.setColor(Color.BLACK);//设置画笔颜色
canvas.translate(100,100);//移动坐标系原点到（100，100）
canvas.drawRect(0,0,100,100,mPaint);//画距形
canvas.rotate(90);//旋转90度
mPaint.setColor(Color.YELLOW);//改变画笔颜色
canvas.drawRect(0,0,100,100,mPaint);//画距形
```

![20190129_view_16](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_16.PNG)

skew(float sx, float sy)：sx是将画布在x方向上倾斜相应的角度，sx倾斜角度的tan值， sy是将画布在y轴方向上倾斜相应的角度，sy为倾斜角度的tan值。也可以叠加。X = x + sx * y、Y = sy * x + y。如下：

```
mPaint.setColor(Color.BLACK);//设置画笔颜色
canvas.translate(100,100);//移动坐标系原点到（100，100）
canvas.drawRect(0,0,100,100,mPaint);//画距形
canvas.skew(1,0);//1=tan45度，在x轴方向上倾斜45度
mPaint.setColor(Color.YELLOW);//改变画笔颜色
canvas.drawRect(0,0,100,100,mPaint);//画距形
```

![20190129_view_17](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_17.PNG)

### 11、Paint

上面简述了Canvas的使用，要想在Canvas上画东西，肯定不能少了Paint，也就是画笔。

Paint部分函数：

![20190129_view_18](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_18.PNG)

例：

```
// 定义、并创建画笔
Paint paint = new Paint();
//设置画笔颜色
paint.setColor(Color.RED);
//设置画笔模式为填充，STROKE：描边、FILL：填充、FILL_AND_STROKE：描边加填充
paint.setStyle(Paint.Style.FILL); 
//设置画笔宽度为10px
paint.setStrokeWidth(20f);
//抗锯齿功能
paint.setAntiAlias(true);
//设置画笔的样式 Paint.Cap.Round：圆形、Paint.Cap.SQUARE：方形
paint.setStrokeCap(Paint.Cap.ROUND);
//结合处为圆弧
paint.setStrokeJoin(Paint.Join.ROUND);
```

## 2.0 面试题

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

```
$ git config –global user.name “Your Name”
设置全局用户名。
```

```
$ git config –global user.name
查询用户名。
```

```
$ git config –global user.email “Your Email”
设置全局邮箱。
```

```
$ git config –global user.email
查询邮箱。
```

```
$ git config –list
检查已有的配置信息。
```

```
$ git config –global alias.st status
用st表示status。
```

```
$ mkdir gitReporitory
mkdir命令是用来创建文件夹的，这里创建一个叫gitreporitory的文件夹。

```
$ cd gitReporitory
进入gitReporitory文件夹。
```

```
$ pwd
显示当前目录。
```

```
$ ls
查看当前项目的所有文件。
```

```
$ git init
把这个目录变为Git可以管理的仓库。
```

```
$ git add hello.txt
添加文件到git仓库上，其中hello.txt就是要添加的文件。
```

```
$ cat hello.txt
查看文件的内容，这里查看hello.txt的内容。
```

```
$ cat .git/config
查看Git配置文件。
```

```
$ git add .
添加所有文件到git仓库上。
```

```
$ git commit -m “first commit”
添加完文件还需要提交到git仓库上，-m后面输入的是本次提交的说明。
```

```
$ git status
用于检查本地项目的状态，遇到问题就试试它，会有提示。
```

```
$ git diff
可以查看哪里有改动过。
```

$ git rm hello.txt
删除版本库中的hello.txt文件。
```

```
$ rm hello.txt
把工作区中的hello.txt文件删除掉，但版本库中的并没有删除掉。
```

```
$ git checkout – hello.txt
假设我们修改了hello.txt文件，但还没git add到暂存区，现在想返回到修改前，可以使用$ git checkout – hello.txt返回到没修改的时候。
```

```
$ git reset HEAD hello.txt
假设我们修改了hello.txt文件，并git add到了暂存区，但现在我们发现有错误，需要修改，我们可以使用该命令把添加到暂存区的修改撤销回工作区。
```

```
$ git reset HEAD hello.txt加$ git checkout – hello.txt
删除版本库中的hello.txt文件后，没提交前我们还可以通过$ git reset HEAD hello.txt加$ git checkout – hello.txt撤消删除。
```

```
$ git log
查看修改记录。
```

```
$ git log -1
显示最后一次提交信息。
```

```
$ git reflog
查看你的每一次命令。
```

```
$ git reset –hard
查看当前版本。
```

```
$ git reset –hard HEAD^
回退到上一版本。HEAD表示当前版本，HEAD^表示上一版本，HEAD^^表示上上一个版本，HEAD~100则为上100个版本。
```

```
$ git reset –hard b6db134
其中b6db134是我刚刚回退前版本的commit id的前七位，Git使用SHA-1算法计算数据的校验和，通过对文件的内容或目录的结构计算出一个SHA-1哈希值，作为指纹字符串，由40个十六进制字符组成，但这里我们用前7位就好了，Git会自动寻找出来的。
```

```
$ git help
查看帮助文档。
```

```
$ git help add
查看add命令的使用。
```

```
$ git branch
查看当前项目所有分支。
```

```
$ git branch one
创建一个one分支。
```

```
$ git checkout one
切换到one分支。
```

```
$ git checkout -b two
创建并切换到two分支。
```

```
$ git checkout -b one origin/one
创建远程origin的one分支到本地。
```

```
$ git branch –set-upstream-to=origin/branch-name branch-name
创建本地分支和远程分支的链接关系。
```

```
$ git checkout master
切换回master分支。
```

```
$ git branch -d one
删除one分支。
```

```
$ git merge one
合并one分支到master分支上。
```

```
$ git merge –no-ff -m “merge with no-ff” one
合并one分支，–no-ff参数用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
```

```
$ git log –graph –pretty=oneline –abbrev-commit
用带参数的git log查看分支的合并情况。
```

```
$ git stash
保存当前仓库已改变的状态。
```

```
$ git stash list
查看保存到哪。
```

```
$ git stash apply或$ git stash apply stash@{0}
恢复已保存的状态。
```

```
$ git stash drop
删除stash内容。
```

```
$ git stash pop
恢复的同时把stash内容也删除。
```

```
$ git tag
查看当前所有版本。
```

```
$ git tag -a v1.0 -m “这里填相关信息”
为项目版本打个标签。
```

```
$ git show v1.0
查看对应版本的相关信息。
```

```
$ git clone https://github.com/lcfu1/lcfu1.git
这里是以https的形式下载的，也可以以SSH的格式，如$ git clone git@github.com:lcfu1/lcfu1.git。
```

```
$ ssh-keygen -t rsa -b 4096 -C “your_email@example.com”
SSH key的配置，your_email@example.com是你注册github的邮箱。
```

```
$ ssh -T git@github.com
查看是否添加成功。
```

```
$ git remote add origin git@github.com:lcfu1/Git.git
向本地仓库添加一个名为origin，地址为git@github.com:lcfu1/Git.git的远程仓库。
```

```
$ git remote -v
查看该项目的远程仓库。
```

```
$ git remote rm origin
删除已有的远程仓库。
```

```
$ git remote add github git@github.com:lcfu1/Git.git
关联GitHub的远程库。
```

```
$ git push origin master:master
推送到远程仓库，origin是上面我们在本地仓库添加的一个名为origin，地址为git@github.com:lcfu1/Git.git的远程仓库。第一个master是本地的master分支，第二是远程的master分支，如果两个一个则可以简化为$ git push origin master。
```

```
$ git push origin master
推送到远程仓库的master分支。
```

```
$ git push origin one
推送到远程仓库的one分支。
```

```
$ git push github master
推送到GitHub。
```

```
$ git pull
更新本地仓库。
```

```
$ git push one:master
将本地的one分支推送到远程仓库。
```

```
$ git push master:one
删除远程仓库的one分支。
```

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
