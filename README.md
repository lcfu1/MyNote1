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

### 1.9.1 屏幕坐标系

手机屏幕左上角为坐标原点，向右为x轴增大方向，向下为y轴增大方向

如下图：

![20190129_view_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_1.PNG)

### 1.9.2 view的坐标

view的坐标是相对父容器而言的，包括：getTop()、getBottom()、getLeft()、getRight()。

如下图：

![20190129_view_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_2.PNG)

从android3.0开始，View增加了几个参数：x、y、translationX和translationY，x和y是View左上角的坐标，而translationX和translationY是View左上角相对于父容器的偏移量。这几个参数是相对于父容器的坐标，并且translationX和translationY的默认值是0，和View的四个基本的位置参数一样，View也提供了get和set方法。这几个参数的换算关系如下： x=left+translationX y=top+translationY View在平移的过程中， top和left表示原始左上角的位置信息，它们的值并不会发生改变，此时发生改变的是x、y、translationX和translationY这四个参数。

### 1.9.3 MotionEvent和TouchSlop

MotionEvent中的getRaw和get：

- event.getRowX()、event.getRowY()：触摸点相对于屏幕原点的x坐标
- event.getX()、event.getY()： 触摸点相对于其所在组件原点的x坐标

![20190129_view_3](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_3.PNG)

TouchSlop：

- TouchSlop是系统所能识别出的被认为是滑动的最小距离，就是两次滑动之间的距离小于这个常量，系统就不认为你在进行滑动操作，这是一个常量，和设备有关。获取方法：ViewConfiguration.get(getContext()).getScaledTouchSlop()。

### 1.9.4 角度与弧度

注：默认的屏幕坐标系中角度增大方向为顺时针

角度：角度是60进制，两条射线从圆心向圆周射出，形成一个夹角和夹角正对的一段弧。当这段弧长正好等于圆周长的360分之一时，两条射线的夹角的大小为1度。

如下图：

![20190129_view_4](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_4.PNG)

弧度：弧度是10进制，两条射线从圆心向圆周射出，形成一个夹角和夹角正对的一段弧。当这段弧长正好等于圆的半径时，两条射线的夹角大小为1弧度。

如下图：

![20190129_view_5](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190129_view_5.PNG)

角度和弧度的换算：rad = deg x π / 180，deg = rad x 180 / π，其中rad是弧度，deg是角度。圆的周长为2πr，由上面弧度概念可知圆360度对应2π弧度。

### 1.9.5 简介颜色

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

### 1.9.6 颜色混合模式

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

### 1.9.7 定义颜色

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

### 1.9.8 自定义View绘制流程

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

### 1.9.9 绘制随手移动的小球

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

### 1.9.10 Canvas

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

### 1.9.11 Paint

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

### 1.9.12 自定义View的分类

自定义View的分类标准不是唯一的，有些人分为两类：自定义View和自定义ViewGroup，而这里分为4类，如下：

1. 继承View重写onDraw方法：用于实现一些不规则的效果，需要自己支持wrap_content和处理padding。
2. 继承ViewGroup派生特殊的Layout：用于实现自定义布局，需要合适地处理ViewGroup的测量和布局这两个过程，并同时处理子元素的测量和布局过程。
3. 继承特定的View（如TextView）：扩展已有View的功能，不需要自己支持wrap_content和处理padding。 
4. 继承特定的ViewGroup（如LinearLayout）：不需要自己处理ViewGroup的测量和布局这两个过程。

### 1.9.13 自定义View需要注意的事项

1. 让View支持wrap_content：直接继承View或ViewGroup的控件如果不在onMeasure中对wrap_content做特殊处理，那么在布局中设置wrap_content并不会达到预期的效果。
2. 让View支持padding：直接继承View的控件如果不在draw方法中处理padding，那么在布局中设置padding属性是达不到预期效果的（margin属性是由父容器控制的，所以不需要做特殊的处理）。继承ViewGroup的控件则需要在onMeasure和onLayout中考虑padding和子元素的margin对其造成的影响。
3. 不要在View中使用Handler：View内部提供了post系列的方法来替代Handler的作用。
4. 及时停止View中的线程或动画：如果View中有线程或动画，当包含此View的Activity退出、此View被remove或此View变得不可见时（预防内存泄漏），就调用onDetachedFromWindow方法。当包含此View的Activity启动时，就调用onAttachedToWindow方法。
5. 处理好View中的滑动冲突：当View带有滑动嵌套时，就要合适地处理滑动冲突，否则会影响View的效果。

### 1.9.14 继承View重写onDraw方法

举个简单的例子，如下：

CircleView.java代码如下：

```
package com.lcfu1.view;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.view.View;

public class CircleView extends View{
    private Paint mPaint = new Paint();
    private int mColor= Color.BLUE;

    public CircleView(Context context) {
        super(context);
        init();
    }
    public CircleView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        init();
    }
    
    private void init() {
        mPaint.setColor(mColor);
        mPaint.setStyle(Paint.Style.FILL);
    }
    
    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        int paddingLeft=getPaddingLeft();
        int paddingRight=getPaddingRight();
        int paddingTop=getPaddingTop();
        int paddingBottom=getPaddingBottom();
        int width=getWidth()-paddingLeft-paddingRight;
        int height=getHeight()-paddingTop-paddingBottom;
        int radius=Math.min(width,height);
        canvas.drawCircle(width/2+paddingLeft,height/2+paddingTop,radius/2,mPaint);
    }
}
```

布局如下：

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.lcfu1.view.CircleView
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:background="#fc5355"
        android:layout_margin="30dp"
        android:padding="20dp"/>
</LinearLayout>
```

上面的代码是绘制一个中心点以宽高的最小值为直径的蓝色实心的圆形，因为margin属性是由父容器控制的，所以不需要在CircleView中做特殊的处理。但是直接继承View和ViewGroup的控件，padding属性是默认不生效的，需要在CircleView中自己处理。

没在代码中进行处理，设置padding属性是不生效的，如下：

![20190130_view_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_1.PNG)

在代码中处理后如下：

![20190130_view_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_2.PNG)

为CircleView添加自定义属性，在values目录下新建一个attr.xml（文件名没有特殊限制，可以根据需要来命名），attr.xml如下：

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <declare-styleable name="CircleView">
        <attr name="circle_color" format="color"/>
    </declare-styleable>
</resources>
```

CircleView.java代码修改如下：

```
package com.lcfu1.view;

import android.content.Context;
import android.content.res.TypedArray;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.view.View;

public class CircleView extends View{
    private Paint mPaint = new Paint();
    private int mColor= Color.BLUE;

    public CircleView(Context context) {
        super(context);
        init();
    }
    public CircleView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        TypedArray typedArray=context.obtainStyledAttributes(attrs,R.styleable.CircleView);
        //如果没有指定circle_color属性就选择Color.BLUE做为默认颜色
        mColor=typedArray.getColor(R.styleable.CircleView_circle_color,Color.BLUE);
        //实现资源
        typedArray.recycle();
        init();
    }
    
    private void init() {
        mPaint.setColor(mColor);
        mPaint.setStyle(Paint.Style.FILL);
    }
    
    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        int paddingLeft=getPaddingLeft();
        int paddingRight=getPaddingRight();
        int paddingTop=getPaddingTop();
        int paddingBottom=getPaddingBottom();
        int width=getWidth()-paddingLeft-paddingRight;
        int height=getHeight()-paddingTop-paddingBottom;
        int radius=Math.min(width,height);
        canvas.drawCircle(width/2+paddingLeft,height/2+paddingTop,radius/2,mPaint);
    }
}
```

布局如下：

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.lcfu1.view.CircleView
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:background="#fc5355"
        android:layout_margin="30dp"
        android:padding="20dp"
        app:circle_color="#ffea00"/>
</LinearLayout>
```

效果如下：

![20190130_view_3](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_3.PNG)

上面代码首先加载自定义属性集合CircleView，然后解析circle_color属性，如果没有指定circle_color属性就选择Color.BLUE做为默认颜色，解析完成后就使用recycle()方法实现资源。在布局中使用自定义属性必须在布局文件中添加schemas声明，如：xmlns:app=”http://schemas.android.com/apk/res-auto”，app是自定义属性的前缀，使用如：app:circle_color=”#ffea00”。还有另外一个声明方法，就是使用该工程的应用包名，如xmlns:app=”http://schemas.android.com/apk/res/com.lcfu1.view”，这种声明方式也是可以的，但是会有如下提示，所以建议使用第一种方式：

> In Gradle projects, always use http://schemas.android.com/apk/res-auto for custom attributes less… (Ctrl+F1) In Gradle projects, the actual package used in the final APK can vary; for example,you can add a .debug package suffix in one version and not the other. Therefore, you should not hardcode the application package in the resource; instead, use the special namespace http://schemas.android.com/apk/res-auto which will cause the tools to figure out the right namespace for the resource regardless of the actual package used during the build. 翻译：在Gradle项目中，总是使用http://schemas.android.com/apk/res-auto来获取定制属性。(Ctrl + F1) 在Gradle项目中，最终APK中使用的实际包会有所不同;例如，您可以在一个版本中添加.debug包后缀，而不是另一个版本。因此，您不应该在资源中硬编码应用程序包;相反，使用特殊的命名空间http://schemas.android.com/apk/res-auto，它将会导致工具为资源找到正确的名称空间，而不考虑构建期间使用的实际包。

在布局中，设置android:layout_width为match_parent或指定一个值（如200dp）都可以达到预期的效果，如指定为200dp，效果如下：

![20190130_view_4](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_4.PNG)

但如果设置为wrap_content并不会达到预期的效果，而是跟使用match_parent一样。可以通过在代码中指定一个wrap_content模式的默认宽或高来解决，如选择400px作为默认宽或高（注：这里是px而不是dp）。布局中layout_width设置为wrap_content（当然也可以把layout_height也设置为wrap_content，这里只是举个例子），CircleView.java代码修改如下：

```
package com.lcfu1.view;

import android.content.Context;
import android.content.res.TypedArray;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.view.View;

public class CircleView extends View{
    private Paint mPaint = new Paint();
    private int mColor= Color.BLUE;

    public CircleView(Context context) {
        super(context);
        init();
    }
    public CircleView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        TypedArray typedArray=context.obtainStyledAttributes(attrs,R.styleable.CircleView);
        //如果没有指定circle_color属性就选择Color.BLUE做为默认颜色
        mColor=typedArray.getColor(R.styleable.CircleView_circle_color,Color.BLUE);
        //实现资源
        typedArray.recycle();
        init();
    }
    
    private void init() {
        mPaint.setColor(mColor);
        mPaint.setStyle(Paint.Style.FILL);
    }
    
    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        super.onMeasure(widthMeasureSpec, heightMeasureSpec);
        int widthMode = MeasureSpec.getMode(widthMeasureSpec);
        int widthSize = MeasureSpec.getSize(widthMeasureSpec);
        int heightMode = MeasureSpec.getMode(heightMeasureSpec);
        int heightSize = MeasureSpec.getSize(heightMeasureSpec);
        if(widthMode==MeasureSpec.AT_MOST && heightMode==MeasureSpec.AT_MOST){
            setMeasuredDimension(400,400);
        }else if(widthMode==MeasureSpec.AT_MOST){
            setMeasuredDimension(400,heightSize);
        }else if(heightMode==MeasureSpec.AT_MOST){
            setMeasuredDimension(widthSize,400);
        }
    }
    
    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        int paddingLeft=getPaddingLeft();
        int paddingRight=getPaddingRight();
        int paddingTop=getPaddingTop();
        int paddingBottom=getPaddingBottom();
        int width=getWidth()-paddingLeft-paddingRight;
        int height=getHeight()-paddingTop-paddingBottom;
        int radius=Math.min(width,height);
        canvas.drawCircle(width/2+paddingLeft,height/2+paddingTop,radius/2,mPaint);
    }
}
```

效果如下：

![20190130_view_5](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_5.PNG)

如上面的代码 ，AT_MOST对应LayoutParams中的wrap_content，如布局中layout_width使用了wrap_content，就指定一个wrap_content模式的默认宽给它，如400px。这里是px而不是dp。dp（英文density-independent-pixel的缩写，意为密度无关像素），在不同的像素密度的设备上会自动适配。上面的效果截图是正方形的，可能设备刚好是1dp = 2px的，在其它手机上测试就不一定是正方形了，这点是需要注意的。

### 1.9.15 实现一个简单的ImageView

ImageView.java代码如下：

```
package com.lcfu1.view;

import android.content.Context;
import android.content.res.TypedArray;
import android.graphics.Bitmap;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.drawable.Drawable;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.view.View;

public class ImageView extends View{
    private Paint mBitmapPaint=new Paint();
    private Drawable mDrawable;
    Bitmap mBitmap;
    private int mWidth;
    private int mHeight;

    public ImageView(Context context) {
        super(context);
        init();
    }
    public ImageView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        if(attrs!=null){
            TypedArray typedArray=null;
            try{
                typedArray=context.obtainStyledAttributes(attrs,R.styleable.ImageView);
                mDrawable=typedArray.getDrawable(R.styleable.ImageView_src);
                measureDrawable();
            }finally {
                if(typedArray!=null){
                    typedArray.recycle();
                }
            }
        }
        init();
    }
    
    private void measureDrawable() {
        if(mDrawable==null){
            throw new RuntimeException("drawable不能为空");
        }
        mWidth=mDrawable.getIntrinsicWidth();
        mHeight=mDrawable.getIntrinsicHeight();
    }
    
    private void init() {
        //抗锯齿功能
        mBitmapPaint.setAntiAlias(true);
    }
    
    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        super.onMeasure(widthMeasureSpec, heightMeasureSpec);
        setMeasuredDimension(resolveSize(mWidth, widthMeasureSpec),
                resolveSize(mHeight, heightMeasureSpec));
    }
    
    @Override
    protected void onDraw(Canvas canvas) {
        if(mBitmap==null){
            mBitmap = Bitmap.createScaledBitmap(ImageUtils.drawableToBitamp(mDrawable),
                    getMeasuredWidth(), getMeasuredHeight(), true);
        }
        canvas.drawBitmap(mBitmap,getLeft(),getTop(),mBitmapPaint);
        //保存画布状态
        canvas.save();
        //画布顺时针旋转90度
        canvas.rotate(90);
        //设置画笔颜色为黑色
        mBitmapPaint.setColor(Color.BLACK);
        //设置绘制的文本大小
        mBitmapPaint.setTextSize(30);
        //绘制文本
        canvas.drawText("LCFU1", getLeft() + 50, getTop() - 50, mBitmapPaint);
        //画布恢复原来的状态
        canvas.restore();
    }
}
```

上面代码使用了一个drawable转bitmap的工具类ImageUtils.java，代码如下：

```
package com.lcfu1.view;

import android.graphics.Bitmap;
import android.graphics.Canvas;
import android.graphics.drawable.BitmapDrawable;
import android.graphics.drawable.Drawable;

//drawable转bitmap
public final class ImageUtils {
    private ImageUtils() {
    }
    public static Bitmap drawableToBitamp(Drawable drawable) {
        if (drawable instanceof BitmapDrawable) {
            BitmapDrawable bd = (BitmapDrawable) drawable;
            return bd.getBitmap();
        }
        int w = drawable.getIntrinsicWidth();
        int h = drawable.getIntrinsicHeight();
        Bitmap bitmap = Bitmap.createBitmap(w, h, Bitmap.Config.ARGB_4444);
        Canvas canvas = new Canvas(bitmap);
        drawable.setBounds(0, 0, w, h);
        drawable.draw(canvas);
        return bitmap;
    }
}
```

布局如下：

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.lcfu1.view.ImageView
        android:layout_width="300dp"
        android:layout_height="300dp"
        app:src="@drawable/image" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="LCFU1"
        android:textSize="15sp"
        android:textColor="#000000"/>
</LinearLayout>
```

attr.xml如下：

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <declare-styleable name="ImageView">
        <attr name="src" format="integer"/>
    </declare-styleable>
</resources>
```

效果如下：

![20190130_view_6](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_6.PNG)

如果布局文件中ImageView控件的layout_width和layout_height设置为wrap_content，则效果如下：

![20190130_view_7](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_7.PNG)

attr.xml中的ImageView属性集里面有一个src的整型属性，通过这个自定义属性，我们就可以在ImageView控件中使用该属性来设置图片的资源id。绘制文本，先保存画布状态，然后将画布顺时针旋转90度，再在画布上绘制文字，最后将画布恢复到原来的状态。对画布进行平移或旋转等其实都是对坐标系的平移或旋转，画布本身并没有变化。过程如下：

![20190130_view_8](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_8.PNG)

### 1.9.16 绘制图片

**drawPicture(矢量图)**

使用Picture前请关闭硬件加速，以免引起不必要的问题！请参考Android的硬件加速及可能导致的问题

关闭方法： 在AndroidManifest.xml的加上android:hardwareAccelerated="false"。

> 官方对Picture的描述： A Picture records drawing calls (via the canvas returned by beginRecording) and can then play them back into Canvas (via draw(Canvas) or drawPicture(Picture)).For most content (e.g. text, lines, rectangles), drawing a sequence from a picture can be faster than the equivalent API calls, since the picture performs its playback without incurring any method-call overhead. Note: Prior to API level 23 a picture cannot be replayed on a hardware accelerated canvas. 有道翻译：一个图片记录调用(通过画布返回的开始记录)，然后可以回放到画布(通过绘制(画布)或drawPicture(图片))。对于大多数内容(例如，文本、线条、矩形)，从图片中绘制序列比等效的API调用要快，因为图片执行它的播放而不产生任何方法调用开销。 注意:在API级别23之前，不能在硬件加速画布上重新播放图片。

Picture的公共方法和描述

- beginRecording(int width, int height)：开始录制 (返回一个Canvas，在Canvas中所有的绘制都会存储在Picture中)。
- createFromStream(InputStream stream)：通过输入流创建一个Picture，该方法在API级别18中被弃用。推荐的替代方法是不使用writeToStream，而是把图片画成一个位图，你可以把它作为原始的或压缩的像素来保存。
- draw(Canvas canvas)：将Picture中内容绘制到Canvas中。
- endRecording()：结束录制。
- getHeight()：获取高度。
- getWidth()：获取宽度。
- requiresHardwareAcceleration()：指示Picture是否包含只在绘制到硬件加速画布时才工作的记录命令。
- writeToStream(OutputStream stream)：将Picture中内容写出到输出流中，该方法在API级别18中被弃用。推荐的方法是将图片绘制到位图中，您可以将其作为原始的或压缩的像素保存。

录制的内容是不会直接显示在屏幕上的，需要使用下面几种方法把它显示出来：

- Picture提供的draw方法
  - 对Canvas有影响，可操作性较弱。
- Canvas提供的drawPicture方法
  - 对Canvas没有影响，可操作性较强。
- PictureDrawable的draw方法
  - 对Canvas没有影响，可操作性较强。

简单示例：

```
package com.lcfu1.view;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Picture;
import android.graphics.drawable.PictureDrawable;
import android.util.AttributeSet;
import android.view.View;

public class canvas extends View {
    // 1.创建一个画笔
    private Paint mPaint = new Paint();
    private Picture mPicture = new Picture();

    public canvas(Context context) {
        super(context);
    }
    
    public canvas(Context context, AttributeSet attrs) {
        super(context, attrs);
        init();
        //调用录制方法
        recording();
    }
    
    //初始化画笔
    private void init() {
        mPaint.setColor(Color.RED);
        mPaint.setStyle(Paint.Style.STROKE);
        mPaint.setStrokeWidth(2);
    }
    
    @Override
    public void onDraw(Canvas canvas) {
        super.onDraw(canvas);
    
        //使用Picture提供的draw方法绘制
        //mPicture.draw(canvas);
    
        //使用Canvas提供的drawPicture方法绘制
        //canvas.drawPicture(mPicture);
    
        //将Picture包装成为PictureDrawable，使用PictureDrawable的draw方法绘制
        PictureDrawable drawable=new PictureDrawable(mPicture);
        //这里要设置绘制区域，不然显示不出来
        drawable.setBounds(0,0,400,400);
        drawable.draw(canvas);
    }
    
    //录制方法
    private void recording() {
        Canvas canvas = mPicture.beginRecording(400, 400);// 开始录制 (接收返回值Canvas)
        canvas.drawColor(Color.GRAY);
        canvas.translate(200,200);//位移
        canvas.drawCircle(0,0,100,mPaint);//绘制圆
        mPicture.endRecording();
    }
}
```

layout中：

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.lcfu1.view.canvas
        android:layout_width="200dp"
        android:layout_height="200dp" />
</LinearLayout>
```

效果如下：

![20190130_view_9](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_9.PNG)

**drawBitmap(位图)**

drawBitmap的常用方法如下：

```
// 第一种，绘制图片内容，默认从坐标原点开始
public void drawBitmap(Bitmap bitmap, Matrix matrix, Paint paint)

// 第二种，指定与坐标原点的距离,这里要注意的是坐标原点，如果canvas有位移、旋转等操作，坐标原点会发生相应变化
public void drawBitmap(Bitmap bitmap, float left, float top, Paint paint)

// 第三种，Rect src指定绘制图片的区，Rect dst 或RectF dst指定图片在屏幕上显示(绘制)的区域
public void drawBitmap(Bitmap bitmap, Rect src, Rect dst, Paint paint)
public void drawBitmap(Bitmap bitmap, Rect src, RectF dst, Paint paint)
```

简单示例如下：

```
import android.content.Context;
import android.graphics.Bitmap;
import android.graphics.BitmapFactory;
import android.graphics.Canvas;
import android.graphics.Matrix;
import android.graphics.Paint;
import android.graphics.Rect;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.view.View;

/**
 * Created by lcf on 2018/4/21 0021.
 */

public class picture extends View {
    Bitmap mBitmap;

    public picture(Context context) {
        super(context);
    }
    
    public picture(final Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
    
        //从mipmap获取Bitmap
        mBitmap= BitmapFactory.decodeResource(context.getResources(),R.mipmap.ic_launcher);
    
        //从assets获取Bitmap
//        try {
//            InputStream inputStream =context.getAssets().open("lcfu1.jpg");
//            mBitmap = BitmapFactory.decodeStream(inputStream);
//            inputStream.close();
//        } catch (IOException e) {
//            e.printStackTrace();
//        }

    }
    
    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
    
        //绘制图片内容，默认从坐标原点开始
        //canvas.drawBitmap(mBitmap, new Matrix(),new Paint());
    
        //指定与坐标原点的距离,这里要注意的是坐标原点，如果canvas有位移、旋转等操作，坐标原点会发生相应变化
        //canvas.drawBitmap(mBitmap,100,100,new Paint());
    
        Rect src = new Rect(0,0,mBitmap.getWidth(),mBitmap.getHeight()/2);// 指定图片绘制区域
        Rect dst = new Rect(0,0,mBitmap.getWidth(),mBitmap.getHeight()/2);//指定图片在屏幕上显示的区域,也就是给个固定区域来填满显示
        canvas.drawBitmap(mBitmap,src,dst,new Paint());// 绘制图片
    }
}
```

效果如下：

![20190130_view_10](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_view_10.PNG)

上面例子是通过BitmapFactory从资源文件中获取Bitmap的，获取Bitmap的三种方式如下：

1. 通过Bitmap创建：复制一个已有的Bitmap(新Bitmap状态和原有的一致)或者创建一个空白的Bitmap(内容可改变)。

2. 通过BitmapDrawable获取：从资源文件、内存卡、网络等地方获取一张图片并转换为内容不可变的Bitmap。

3. 通过BitmapFactory获取：从资源文件、内存卡、网络等地方获取一张图片并转换为内容不可变的Bitmap。

BitmapFactory获取Bitmap的方法：

1. 从资源文件drawable、mipmap、raw、assets获取：

```
//从mipmap获取Bitmap
mBitmap= BitmapFactory.decodeResource(context.getResources(),R.mipmap.ic_launcher);

//从assets获取Bitmap
try{
	InputStream is =context.getAssets().open("lcfu1.jpg");
	mBitmap = BitmapFactory.decodeStream(is);
	is.close();
} catch (IOException e) {
	e.printStackTrace();
}
```

2. 内存卡文件：

```
mBitmap= BitmapFactory.decodeFile("sdcard/lcfu1.jpg");
```

3. 网络文件：

```
// 需要获取网络输入流的代码
Bitmap bitmap = BitmapFactory.decodeStream(inputStream);
inputStream.close();
```

## 2.0 AndroidStudio

### 2.0.1 优势

1. 由Google公司开发并大力完善和支持。
2. 稳定速度快：启动速度快，与其他IDE（集成开发环境Integrated Development Environment）相比，性能明显提升了。
3. 强大的UI编辑器：能实时展示界面布局效果。
4. 完善的插件管理：支持多种插件，可支持在插件管理中下载。
5. 支持多种代码管理工具：直接支持Git、SVN等主流的代码管理工具。
6. 整合了Gradle构建工具：Gradle继承了Ant的灵活性和Maven的生命周期管理，不使用XML作为配置文件格式，采用了DSL格式，使得脚本更加灵活简洁。
7. 内置终端：不需要自己打开一个终端来使用ADB等工具，当然也可以使用[Genymotion安卓模拟器](https://www.genymotion.com/)。
8. 智能化：智能保存、补齐等，提高开发效率。

### 2.0.2 下载安装

1. 可到[Android Studio中文社区](http://www.android-studio.org/)或[https://developer.android.google.cn/studio/](https://developer.android.google.cn/studio/)进行下载。
2. 最好下载的Android Studio包含构建 Android 应用所需的所有工具。
3. 如果电脑上已安装了JDK，则安装Android Studio时只需安装默认的选项。
4. 如果电脑上有SDK，可选择本地的SDK目录。

### 2.0.3 离线配置Gradle

1. Android Studio没有自带Gradle插件，但会自动下载Gradle。
2. [下载Gradle](http://gradle.android-studio.org/)。
3. 进入C:\Users\Administrator\.gradle\wrapper\dists\gradle-4.1-all\bzyivzo6n839fup2jbap0tjew，最后这个文件夹是随机生成的，直接进入，把下载好的gradle-3.0-all.zip放到这个文件夹内。
4. 重启Android Studio。

!> 注：Gradle是一种依赖管理工具，基于Groovy语言，抛弃了基于XML的各种繁琐配置，取而代之的是一种基于Groovy的内部领域特定语言（DSL），掌握Gradle脚本的编译和打包是应用开发非常必要的。

### 2.0.4 第一个Android程序

**项目的结构模式：**

![20190130_androidstudio_1](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_1.PNG)

**Android模式的项目结构：**

![20190130_androidstudio_2](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_2PNG)

**Project模式的项目结构：**

![20190130_androidstudio_3](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_3.PNG)

**app目录：**

![20190130_androidstudio_4](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_4.PNG)

**Project模式目录讲解：**

1. .gradle和.idea：Android Studio自动生成的，不需要手动编辑。
2. app：放置项目中的代码、资源等内容。
3. build：编译时自动生成的文件。
4. gradle：包含了gradle wrapper的配置文件，使用gradle wrapper的方式不需要提前将gradle下载好，而是会自动根据本地缓存情况决定是否联网下载。Android Studio默认没有启动gradle wrapper的方式，可自己设置：File->Settings->Build，Execution，Deployment->Gradle。
5. .gitignore：过虑不需要上传的文件或目录。
6. build.gradle：项目全局的gradle构建脚本。
7. gradle.properties：全局的gradle配置文件。
8. gradlew和gradlew.bat：用于在命令行界面中执行gradle命令，其中gradlew是在Linux或Mac系统中使用的，gradlew.bat是在Windows系统中使用的。
9. Hello.iml：用于标识这是一个IntelliJ IDEA项目，所有的IntelliJ IDEA项目都会自动生成的一个文件（Android Studio是基于IntelliJ IDEA开发的）。
10. local.properties：指定本机Android SDK路径，如果Android SDK路径改变了，就修改此文件中的路径为新的本机Android SDK路径。
11. Settings.gradle：用于指定项目中所有引入的模块，Hello项目中只有一个app模块，所以只引入app模块。

**app目录讲解：**

1. build：编译时自动生成的文件。
2. libs：放置第三方jar包，会自动添加到构建路径中。
3. androidTest：用来编写Android Test测试用例的，可以对项目进行一些自动化测试。
4. java：放置所有Java代码。
5. res：放置项目所需资源。
6. AndroidManifest.xml：Android项目的配置文件。
7. test：用来编写Unit Test测试用例的，是对项目进行自动化测试的另一种方式。
8. .gitignore：过虑app模块中不需要上传的文件或目录。
9. app.iml：IntelliJ IDEA项目自动生成的文件。
10. build.gradle：app模块的gradle构建脚本。
11. proguard-rules.pro：指定项目的混淆规则，将代码进行混淆以防别人破解。

### 2.0.5  实用技巧

#### 代码管理

1. 在电脑上安装Git，[windows下载地址](https://gitforwindows.org/)。

2. 配置File->Settings->Version Control->Git，配置Git目录。

![20190130_androidstudio_5](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_5.PNG)

3. 配置File->Settings->Version Control->GitHub，点击Create API Token登录GitHub。

![20190130_androidstudio_6](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_6.PNG)

4. 菜单栏->VCS->Enable Version Control Integration，选择Git，完成后工具栏会新增如下图所示的快捷工具：

![20190130_androidstudio_7](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_7.PNG)

5. 过虑不需要上传的文件或目录，File->Settings->Version Control->Ignored Files，选择不需要同步的文件或文件夹，也可以通过修改.gitignore文件来实现，建议使用第一种方式，如下图：

![20190130_androidstudio_8](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_8.PNG)

6. 同步代码到Github，菜单栏->VCS->Import into Version Control->Share Project On GitHub，如下图：

![20190130_androidstudio_9](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_9.PNG)
7. 单击Share按钮后，会弹出提交文件列表，不需要上传的文件或目录，可以不选择它，同步完成后就可以在Github上看到该目录了。

![20190130_androidstudio_10](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_10.PNG)

8. 后面修改的代码，就可以使用VCS快捷工具进行快速同步到Github上。

![20190130_androidstudio_11](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_11.PNG)
#### 代码编辑技巧

1. 可通过File->Settings->Keymap来设置快捷键，如下图：

![20190130_androidstudio_12](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_12.PNG)

2. 内容补全：在写完方法名或需要用{}前，使用Ctrl+Shift+Enter组合键进行快速补全。

3. 列选择：按住Alt键选择代码块，可进行多行编辑。

4. 代码补全：使用Enter键可从光标处插入提示补全的代码，对前面的不做修改。使用Tab键可进行选择，但会删除后面的代码，直到遇到点号、圆括号、分号、空格等为止。

5. 查看方法调用路径：Ctrl+Alt+H组合键。

6. 预览某个方法或类的实现：Ctrl+Shift+I组合键。

7. 快速使用命令：Ctrl+Shift+A组合键。对于没有设置快捷键或忘记快捷键的菜单功能或命令时，可以使用该命令进行模糊匹配以快速调用。

8. 自动导入包设置：File->Settings->Editor->General->Auto Import，选中Show import popup、Show import pupup、Optimize imports on the fly 和 Add unambiguous imports on the fly，设置完成后就可以自动导入包和自动去掉无用包了。如下图：

![20190130_androidstudio_13](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_13.PNG)
9. Tip of the day：每次打开Android Studio都会出现一个Tip of the day，我们也可以手动打开：Help->Tip of the day。如下图：

![20190130_androidstudio_14](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/android/20190130_androidstudio_14.PNG)

#### 快捷键

| 快捷键                | 作用                   |
| --------------------- | ---------------------- |
| Ctrl+鼠标左键点击     | 打开此关键字说明       |
| Alt+回车              | 导入包，自动修正       |
| Ctrl+N                | 查找类                 |
| Ctrl+Shift+N          | 查找文件               |
| Ctrl+Alt+L            | 格式化代码             |
| Ctrl+R                | 替换文本               |
| Ctrl+alt+空格         | 代码提示               |
| Ctrl+D                | 复制行                 |
| Ctrl+X                | 删除行                 |
| Ctrl+P                | 方法参数提示           |
| Ctrl+/                | 注释                   |
| Alt＋Up and Alt＋Down | 可在方法间快速移动     |
| Ctrl+Shift+Enter      | 内容补全               |
| 按住Alt键选择         | 列选择                 |
| Ctrl+Alt+H            | 查看方法调用路径       |
| Ctrl+Shift+I          | 预览某个方法或类的实现 |
| Ctrl+Shift+A          | 快速使用命令           |

#### 调试技巧

1. 调试程序：通过菜单->Build->Attach to Android Process，也可以通过工具栏快捷键工具Attach to Android Process进入调试模式。
2. 条件断点：通过右键断点对一个断点加入条件，即填写Condition中的条件，只有满足条件时，才会进入断点。
3. 日志断点：当想打印一些日志信息，但又不想添加log代码后重新部署时，则可以在断点上单击鼠标右键，取消选中Suspend，然后勾选Log evaluated Expression，并在输入框中输入要打印的日志信息。
4. 分析传入/传出数据流：Menu->Analyze->Analyze Data Flow to Here这个操作将会根据当前选中的变量、参数或字段，分析出其传递到此处的路径。传出数据流（Analyze Data Flow from Here）则会分析当前选中的变量往下传递的路径，直到结束。
5. 修改变量值：修改变量值可以快速调试各个Case，提高异常处理的调试效率。

## 2.1 面试题

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


# 六、SVG

## 6.1 SVG定义

可缩放矢量图形是基于可扩展标记语言(标准通用标记语言的子集)，用于描述二维矢量图形的一种图形格式。它由万维网联盟制定，是一个开放标准。

## 6.2 什么是SVG？

- SVG 指可伸缩矢量图形 (Scalable Vector Graphics)

- SVG 用来定义用于网络的基于矢量的图形

- SVG 使用 XML 格式定义图形

- SVG 图像在放大或改变尺寸的情况下其图形质量不会有所损失

- SVG 是万维网联盟的标准

- SVG 与诸如 DOM 和 XSL 之类的 W3C 标准是一个整体

## 6.3 优势

- SVG 可被非常多的工具读取和修改(比如记事本)

- SVG 与 JPEG 和 GIF 图像比起来，尺寸更小，且可压缩性更强。

- SVG 是可伸缩的

- SVG 图像可在任何的分辨率下被高质量地打印

- SVG 可在图像质量不下降的情况下被放大

- SVG 图像中的文本是可选的，同时也是可搜索的(很适合制作地图)

- SVG 可以与 Java 技术一起运行

- SVG 是开放的标准

- SVG 文件是纯粹的 XML

**矢量图像格式和位图图像格式的区别：**

矢量图像用点和线来描述物体，所以文件会比较小，同时也能提供高清晰的画面，适合于直接打印或输出。而位图图像的存储单位是图像上每一点的像素值，因此一般的图像文件都很大，会占用大量的网络带宽。SVG是一种矢量图形格式，GIF、JPEG是光栅文件格式。

**1.任意放缩：**

用户可以任意缩放图像显示，而不会破坏图像的清晰度、细节等。

**2.文本独立：**

SVG图像中的文字独立于图像，文字保留可编辑和可搜寻的状态。也不会再有字体的限制，用户系统即使没有安装某一字体，也会看到和他们制作时完全相同的画面。

**3.较小文件：**

总体来讲，SVG文件比那些GIF和JPEG格式的文件要小很多，因而下载也很快。

**4.超强显示效果：**

SVG图像在屏幕上总是边缘清晰，它的清晰度适合任何屏幕分辨率和打印分辨率。

**5.超级颜色控制：**

SVG图像提供一个1 600万种颜色的调色板，支持ICC颜色描述文件标准、RGB、线X填充、渐变和蒙版。

**6.交互X和智能化**

SVG面临的主要问题一个是如何和已经占有重要市场份额的矢量图形格式Flash竞争的问题，另一个问题就是SVG的本地运行环境下的厂家支持程度。

## 6.4 SVG编辑器

- 线上编辑器（下载地址：https://c.runoob.com/more/svgeditor）

- 本地编辑器inkscape（下载地址：http://baoku.360.cn/soft/show/appid/102866）

## 6.5 简单的画圆例子代码解析

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="black"
  stroke-width="2" fill="red" />
</svg>
```

**SVG 代码解析：**

- standalone属性：该属性规定此 SVG 文件是否是"独立的"，或含有对外部文件的引用。standalone="no"意味着 SVG 文档会引用一个外部文件 - 在这里，是 DTD 文件。

- http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd：外部的 SVG DTD，该 DTD 位于 W3C，含有所有允许的 SVG 元素。

- `<svg>`元素：包括开启标签`<svg>`和关闭标签`</svg>`，这是根元素。

- width和height属性：设置此SVG文档的宽度和高度，这里设置为100px。

- xmlns 属性：定义 SVG 命名空间。

- version 属性：定义所使用的 SVG 版本。

- `<circle> `：创建一个圆。

- cx和cy属性：定义圆中心的 x 和 y 坐标，如果忽略，那么圆点会被设置为 (0, 0)。

- r 属性：定义圆的半径。

- stroke和 stroke-width属性：控制如何显示形状的轮廓，这里把圆的轮廓设置为 2px 宽，黑边框。

- fill属性：设置形状内的颜色，这里设置为红色。

## 6.6 SVG的使用

**SVG在HTML页面的使用**

- SVG 文件可通过以下标签嵌入 HTML 文档：`<embed>`、`<object>`或者`<iframe>`。

- SVG的代码可以直接嵌入到HTML页面中，或链接到SVG文件。

- 谷歌Chrome，火狐，Internet Explorer9，和Safari都支持。

**`<embed>`标签：**

- 优势：所有主要浏览器都支持，并允许使用脚本

- 缺点：不推荐在HTML4和XHTML中使用（但在HTML5允许）

- 使用：`<embed src="circle.svg" type="image/svg+xml" />`

**`<object>`标签：**

- 优势：所有主要浏览器都支持，并支持HTML4，XHTML和HTML5标准

- 缺点：不允许使用脚本。

- 使用：`<object data="circle.svg" type="image/svg+xml"></object>`

**`<iframe>`标签：**

- 优势：所有主要浏览器都支持，并允许使用脚本

- 缺点：不推荐在HTML4和XHTML中使用（但在HTML5允许）

- 使用：`<iframe src="circle.svg"></iframe>`

**直接在HTML嵌入SVG代码：**

- *代码如下：*

```
<!DOCTYPE html>
<html>
<body>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="black"  stroke-width="2" fill="red" />
</svg>
</body>
</html>
```

**链接到SVG文件：**

- 通过`<a>`标签可以链接到一个SVG文件。

- 使用：`<a href="circle.svg">SVG</a>`

## 6.7 矩形

用 `<rect> `标签来创建矩形 。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <rect x="50" y="50" rx="20" ry="20" width="100" height="100" style="fill:blue;stroke:pink;stroke-width:2;fill-opacity:0.1;stroke-opacity:0.9" />
</svg>
```

**解析：** 

- x、y属性分别定义矩形的左侧和顶端位置。
- rx、ry属性可使矩形产生圆角。 
- width、height 属性分别定义矩形的高度和宽度。
- style 属性用来定义 CSS 属性。
- CSS 的 fill 属性定义矩形的填充颜色（rgb 值、颜色名或者十六进制值）。
- CSS 的 stroke-width 属性定义矩形边框的宽度。
- CSS 的 stroke 属性定义矩形边框的颜色。
- CSS 的 fill-opacity 属性定义填充颜色透明度（合法的范围是：0 - 1）。
- CSS 的 stroke-opacity 属性定义笔触颜色的透明度（合法的范围是：0 - 1）。

## 6.8 圆形

用`<circle>` 标签来创建一个圆。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
   <circle cx="100" cy="100" r="40" stroke="black" stroke-width="2" fill="red" />
</svg>
```

**解析：**

- cx和cy属性分别定义圆点的x和y坐标。 
- r属性定义圆的半径。
- 其它属性跟上面矩形style属性中的CSS属性一样。

## 6.9 椭圆

用`<ellipse>` 标签来创建一个椭圆 。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <ellipse cx="100" cy="100" rx="50" ry="20" style="fill:yellow;stroke:purple;stroke-width:2" />
</svg>
```

**解析：**

- cx、cy属性分别定义椭圆中心的x坐标、y坐标。
- rx、ry属性分别定义水平半径、垂直半径。

## 6.10 线

用`<line>` 标签来创建一条直线。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <line x1="0" y1="0" x2="200" y2="0" style="stroke:rgb(255,0,0);stroke-width:2" />
</svg>
```

**解析：**

- x1、y1属性分别在 x、y轴定义线条的开始。
- x2、y2属性分别在 x、y轴定义线条的结束。

## 6.11 折线

用`<polyline>` 标签来创建任何只有直线的形状。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <polyline points="0,0 100,0 100,100" style="fill:none;stroke:black;stroke-width:2" />
</svg>
```

**解析：**

- points属性定义多边形每个角的 x 和 y 坐标。

## 6.12 多边形

用`<polygon>` 标签来创建含有不少于三个边的图形。 

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <polygon points="100,10 40,180 190,60 10,60 160,180" style="fill:red;stroke:black;stroke-width:2;fill-rule:evenodd;" />
</svg>
```

**解析：**

- points属性定义多边形每个角的 x 和 y 坐标。
- fill-rule属性：
  - nonzero：按该规则，要判断一个点是否在图形内，从该点作任意方向的一条射线，然后检测射线与图形路径的交点情况。从0开始计数，路径从左向右穿过射线则计数加1，从右向左穿过射线则计数减1。得出计数结果后，如果结果是0，则认为点在图形外部，否则认为在内部。 
  - evenodd：按该规则，要判断一个点是否在图形内，从该点作任意方向的一条射线，然后检测射线与图形路径的交点的数量。如果结果是奇数则认为点在内部，是偶数则认为点在外部。 

## 6.13 路径

用`<path>` 标签来定义一个路径。 

可用以下命令控制路径数据，允许大小写字母，大写表示应用绝对位置，小写表示相对定位。

| 命令                                | 描述                           |
| :---------------------------------- | :----------------------------- |
| M = moveto                          | 移动到                         |
| L = lineto                          | 连线到                         |
| H = horizontal lineto               | 水平连线到                     |
| V = vertical lineto                 | 垂直连线到                     |
| C = curveto                         | 使用曲线连接到                 |
| S = smooth curveto                  | 使用平滑曲线连接到             |
| Q = quadratic Bézier curve          | 使用二次贝塞尔曲线连接到       |
| T = smooth quadratic Bézier curveto | 使用平滑的二次贝塞尔曲线连接到 |
| A = elliptical Arc                  | 使用椭圆曲线连接到             |
| Z = closepath                       | 将路径封闭到                   |

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <path d="M0 0 L100 0 L100 100 Z" />
</svg>
```

**解析：**

- d属性用来定义路径。
- M0 0：从位置(0,0)开始。
- L100 0：直线到位置(100,0)。
- L100 100：直线到位置(100,100)。
- Z：关闭路径。

## 6.14 文本

`<text>`元素用于定义文本。 

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <text x="0" y="0" fill="red" transform="rotate(30 -20,20)">SVG</text>
</svg>
```

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <path id="path1" d="M75,20 a1,1 0 0,0 100,0" />
  </defs>
  <text x="10" y="100" style="fill:red;">
    <textPath xlink:href="#path1">SVG</textPath>
  </text>
</svg>
```

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <text x="10" y="20" style="fill:red;">
	First
    <tspan x="10" y="40">Second</tspan> 
  </text>
</svg>
```

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1"
xmlns:xlink="http://www.w3.org/1999/xlink">
  <a xlink:href="https://lcfu1.github.io/Note/" target="_blank">
    <text x="10" y="10" fill="red">lcfu1</text>
  </a>
</svg>
```

**解析：**

- transform属性实现旋转 。
- 每个`<tspan>`元素可以包含不同的格式和位置。 
- 放在 `<a>`元素中作为链接文本。

## 6.15 stroke属性

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <g fill="none">
    <path stroke="red" stroke-linecap="butt" stroke-width="4" d="M10 10 L100 10" />
    <path stroke="black" stroke-linecap="round" stroke-width="5" d="M10 20 L100 20" />
    <path stroke="blue" stroke-linecap="square" stroke-width="6" stroke-dasharray="20,10,5,5,5,10" d="M10 30 L200 30" />
  </g>
</svg>
```

**解析：**

- stroke：定义一条线，文本或元素轮廓颜色。
- stroke-width：定义厚度。
- stroke-linecap：定义不同类型的开放路径的终结。
  - butt：默认。向线条的每个末端添加平直的边缘。 
  - round：向线条的每个末端添加圆形线帽。 
  - square： 向线条的每个末端添加正方形线帽。 
- stroke-dasharray：创建虚线。

## 6.16 过虑器

**SVG支持的过虑器表：**

| 过虑器              | 作用                                   |
| ------------------- | -------------------------------------- |
| feBlend             | 使用不同的混合模式把两个对象合成在一起 |
| feColorMatrix       | 用于彩色滤光片转换                     |
| feComponentTransfer | 执行数据的 component-wise 重映射       |
| feComposite         |                                        |
| feConvolveMatrix    |                                        |
| feDiffuseLighting   |                                        |
| feDisplacementMap   |                                        |
| feFlood             |                                        |
| feGaussianBlur      | 执行高斯模糊图像                       |
| feImage             |                                        |
| feMerge             | 建立在彼此顶部图像层                   |
| feMorphology        |                                        |
| feOffset            | 过滤阴影，  创建阴影效果               |
| feSpecularLighting  |                                        |
| feTile              |                                        |
| feTurbulence        |                                        |
| feDistantLight      | 定义一个光源，用于照明过滤             |
| fePointLight        | 用于照明过滤                           |
| feSpotLight         | 用于照明过滤                           |

过滤器在`<defs>`元素中定义，使用`<filter>`标记来定义SVG滤镜，`<filter>`标记使用id属性来定义向图形应用哪个滤镜，在图形中使用`<filter>`属性，通过将 url 值设置为用户分配给过滤器的 id 属性的值。

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <filter id="f1" x="0" y="0">
      <feGaussianBlur in="SourceGraphic" stdDeviation="10" />
    </filter>
  </defs>
  <rect width="100" height="100" stroke="black" stroke-width="2" fill="red" filter="url(#f1)" />
</svg>
```

**解析：**

- `<feGaussianBlur>`元素：定义模糊效果。
- `in="SourceGraphic"`：定义了由整个图像创建效果。
- `stdDeviation`属性：定义模糊量。
- `<rect>`元素的滤镜属性用来把元素链接到"f1"滤镜。

## 6.17 渐变

是一种从一种颜色到另一种颜色的平滑过渡，有两种基本形式：线性（Linear）和径向渐变（Radial）。

**1、线性渐变`<linearGradient>`**

线性渐变可以定义为水平，垂直或角渐变：

- 当y1和y2相等，而x1和x2不同时，可创建水平渐变
- 当x1和x2相等，而y1和y2不同时，可创建垂直渐变
- 当x1和x2不同，且y1和y2不同时，可创建角形渐变

**水平线性渐变例子：**

 ```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <circle cx="100" cy="100" r="50" fill="url(#grad1)" />
</svg>
 ```

**解析：**

- `<linearGradient>`标签的id属性可为渐变定义一个唯一的名称。
- `<linearGradient>`标签的x1，x2，y1，y2属性定义渐变开始和结束位置。
- 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个`<stop>`标签来规定。offset属性用来定义渐变的开始和结束位置。
- 填充属性把 circle 元素链接到此渐变。

**垂直线性渐变例子：**

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <circle cx="100" cy="100" r="50" fill="url(#grad1)" />
</svg>
```

**2、放射性渐变`<radialGradient>`**

```
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <radialGradient id="grad1" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:0" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </radialGradient>
  </defs>
  <circle cx="100" cy="100" r="50" fill="url(#grad1)" />
</svg>
```

**解析：**

- `<radialGradient>`标签的 id 属性可为渐变定义一个唯一的名称。
- cx，cy和r属性定义的最外层圆和fx和fy定义的最内层圆。
- `circle`标签中的cx，cy和r属性定义圆的起始坐标和半径。
- 渐变颜色范围可以由两个或两个以上的颜色组成。每种颜色用一个`<stop>`标签指定。offset属性用来定义渐变色开始和结束。
- 填充属性把circle元素链接到此渐变。

# 七、HTML


# 八、CSS


# 九、JavaScript


# 十、数据库

## 10.1 简介

### 10.1.1 数据

- 指所有能输入到计算机中并被计算机程序处理 的符号的总称。 

### 10.1.2 数据处理

- 指对各种形式的数据进行收集、储存、加 工和传播的一系列活动的综合。其目的是从大量的、原 始的数据中抽取、推导出对人们有价值的信息。 

### 10.1.3 数据库

数据库(database)

- 以一定方式存储在一起，能为多个用户共享， 具有尽可能小的数据冗余特点，与应用程序彼此独 立的数据集合。
- 长期存储在计算机内，有组织的管理，具有 较小冗余，可供多个用户共享的数据集合。

### 10.1.4 数据库管理系统

数据库管理系统(database management system,DBMS)，是位于用户和操作系统(OS)之间的一层数据管理软件，负责对数据库进行统一的管理和控制，并为用户和应用程序提供访问数据库的方法。

### 10.1.5 数据库系统

数据库系统(database system,DBS)，是计算机系统、DB、DBMS、应用软件、数据库管理员(database administrator，DBA)和用户的集合。

### 10.1.6 数据库技术的发展

- 第一代数据库技术，即层次数据库和网状数据库技术
- 第二代数据库技术，即关系数据库技术
- 第三代数据库技术，即新一代数据库技术

### 10.1.7 计算机数据管理技术

经历的三个阶段：

**人工管理阶段**

- 数据不保存
- 人工管理数据
- 数据不共享
- 数据不具有独立性

**文件系统阶段**

- 数据可以长期保存
- 文件的多样化和结构化
- 文件系统管理数据

**数据库系统阶段**

- 数据的整体结构化
- 数据独立性高
- 数据的共享性高，冗余度低，易扩充
- 提供了完整的控制功能

## 10.2 简单的查询语句

### 10.2.1 SQL

SQL(Structured Query Language)，结构化查询语言。

### 10.2.2 结构化查询语言分类

- 数据查询语言（DQL:Data Query Language）：语句主要包括 SELECT，用于从表中检索数据。
- 数据操作语言（DML：Data Manipulation Language）：语句主要包括INSERT，UPDATE和DELETE，用于添加，修改和删除表中的行数据。
- 事务处理语言（TPL:Transaction Process Language）：语句主要包括COMMIT和ROLLBACK，用于提交和回滚。
- 数据控制语言（DCL:Data Control Language）：语句主要包括GRANT和REVOKE，用于进行授权和收回权限。
- 数据定义语言（DDL:Data Definition Language）：语句主要包括CREATE、DROP、ALTER，用于定义、销毁、修改数据库对象。

### 10.2.3 SQL概念和规则

相关概念

- 关键字（Keyword）：SQL语言保留的字符串，例如，SELECT 和FROM都是关键字。
- 语句（statement）：一条完整的SQL命令，例如，SELECT * FROM dept 是一条语句。
- 子句（clause）：部分的SQL语句，通常是由关键字加上其它 语法元素构成，例如，SELECT * 是一个子句，FROM table也是一个子句。

书写规则

- 不区分大小写，也就是说SELECT，select，Select，执行时 效果是一样的，关键字建议大写，其它语法元素（如列名、表名等）小写。
- 可以单行来书写，也可以书写多行，建议分多行书写，增强代码可读性，通常以子句为单位进行分行。
- 关键字不可以缩写、分开以及跨行书写，如SELECT不可以写成SEL或SELE CT等形式。
- Tab和缩进的使用可以提高程序的可读性。

### 10.2.4 SQL所涉及的运算符和函数

| 名称     | 运算符                                                       | 说明                                                         |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 比较运算 | =、!=、>、<、>=、<=、<>、!>、!<、                            | 等于、不等于、大于...                                        |
|          | BETWEEN AND、NOT BETWEEN AND                                 | 介于两者之间、介于两者之外                                   |
| 谓       | IN、NOT IN                                                   | 在其中、不在其中                                             |
| 词       | LIKE、NOT LIKE                                               | 匹配、不匹配                                                 |
|          | IS NULL、IS NOT NULL                                         | 是空值、不是空值                                             |
| 逻辑运算 | NOT、AND、OR                                                 | 非、与、或                                                   |
| 集函数   | COUNT(*)、COUNT(列名)、SUM(列名)、AVG(列名)、MAX(列名)、MIN(列名) | 统计元组个数、统计列值个数、列值汇总、求列值平均、求列值最大、求列值最小 |

### 10.2.5 运算符的优先级

| 优先级 | 运算分类       | 运算符举例                     |
| ------ | -------------- | ------------------------------ |
| 1      | 算术运算符     | +，-，*，\                     |
| 2      | 连接运算符     | \|\|                           |
| 3      | 比较运算符     | =, <>, <, >, <=, >=            |
| 4      | 特殊比较运算符 | BETWEEN AND，IN，LIKE，IS NULL |
| 5      | 逻辑非         | NOT                            |
| 6      | 逻辑与         | AND                            |
| 7      | 逻辑或         | OR                             |

注：

- 括号()优先于其他操作符。

### 10.2.6 基本SELECT语句

File->New->SQL Window，新建一个SQL窗口，在这里写语句。

```
SELECT [DISTINCT]{*|column|expression [alias],...}
FROM table
[WHERE condition(s)]
```

注：

- SELECT子句：表示所需检索的数据列。
- FROM子句：表示检索的数据来自哪个表。
- condition(s)：表示条件表达式。

### 10.2.7 简单的选择与投影查询

- 无条件查询
  - 只有SELECT和FROM组成的简单查询。
- 条件查询
  - 就是使用WHERE子句为查询增加条件，WHERE子句的条件表达式是一个逻辑表达式，由常量、变量、函数、属性名和各种运算符组成。
  - WHERE子句可以返回限定的数据行。

### 10.2.8 查询所有列

```
SELECT *
FROM emp
```

注：

- *：等价于所有的列。

### 10.2.9 查询指定列

```
SELECT ename
FROM emp
```

注：

- ename：指的就是ENAME列。

### 10.2.10使用算术运算符

| 运算符 | 描述 |
| ------ | ---- |
| +      | 加   |
| -      | 减   |
| *      | 乘   |
| /      | 除   |

**优先级**

- 乘除优先于加减。
- 相同优先权的表达式按照从左至右的顺序依次计算。
- 括号可以提高优先权。

```
SELECT sal,sal+1000
FROM emp
```

注：

- sal+1000：查询的结果为sal+1000的值。

### 10.2.11 空值NULL

- 空值是指一种无效的、未赋值、未知的或不可用的值。
- 空值不同于零或者空格。
- 任何包含空值的算术表达式运算后的结果都为空值NULL。

```
SELECT comm,comm+1000
FROM emp
```

注：

- comm+1000：只有comm不为空值，相加才有结果，不然就为空值。

- 如果comm为空值，但想相加的值不为空值，可以使用nvl函数，如：

```
  SELECT comm,nvl(comm+1000,0)
  FROM emp
```

### 10.2.12 列别名

用来重新命名列的显示标题。

**使用方法**

- 列名 列别名。
- 列名 AS 列别名。

**以下情况要添加双引号**

- 列别名中包含有空格。
- 列别名中要求区分大小写。
- 列别名中包含有特殊字符。

```
SELECT ename 员工名,job AS 工作,sal "薪水"
FROM emp
```

### 10.2.13 连接操作符

- 用于连接列与列、列和字符。
- 形式上是以两个竖杠||。
- 用于创建字符表达式的结果列。

```
SELECT ename || job
FROM emp
```

### 10.2.14 原义字符串

- 原义字符串是包含在SELECT列表中的一个字符、一个数 字或一个日期。
- 日期和字符字面值必须用单引号引起来。
- 每个原义字符串都会在每个数据行输出中出现。

```
SELECT ename || '的工作是' || job AS "Employee Details"
FROM emp
```

### 10.2.15 消除重复行

```
SELECT DISTINCT job
FROM emp
```

注：

- 使用DISTINCT关键字。

### 10.2.16 显示表的结构

File->New->Command Window，新建一个Command窗口，可以在这个窗口显示表的结构，如：

```
Connected to Oracle Database 11g Enterprise Edition Release 11.2.0.1.0 
Connected as scott@ORCL

SQL> DESC emp
Name     Type         Nullable Default Comments 
-------- ------------ -------- ------- -------- 
EMPNO    NUMBER(4)                              
ENAME    VARCHAR2(10) Y                         
JOB      VARCHAR2(9)  Y                         
MGR      NUMBER(4)    Y                         
HIREDATE DATE         Y                         
SAL      NUMBER(7,2)  Y                         
COMM     NUMBER(7,2)  Y                         
DEPTNO   NUMBER(2)    Y                         

SQL> 
```

注：

- 使用DESC emp命令来查看表结构。



### 10.2.17 比较数值型数据

```
SELECT deptno
FROM emp
WHERE deptno=30
```

### 10.2.18 比较字符型数据

```
SELECT job
FROM emp
WHERE job='SALESMAN'
```

注：

- 字符型数据作为被比较的值时，必须用单引号引起来。
- 字符型数值区分大小写。

### 10.2.19 比较日期型数据

```
SELECT hiredate
FROM emp
WHERE hiredate>'01-1月-81'
```

注：

- 日期型数值作为被比较的值时，必须用单引号引起来。
- 日期型数值是区分日期表达形式的，默认的日期形式是DD-MON-RR。

### 10.2.20 BETWEEN AND

用来判断要比较的值是否在某个范围内。

```
SELECT deptno
FROM emp
WHERE deptno BETWEEN 20 AND 30
```

### 10.2.21 IN

用来判断要比较的值是否和集合列表中的任何一个值相等。

```
SELECT deptno
FROM emp
WHERE deptno IN(20,30)
```

### 10.2.22 LIKE

- 使用LIKE运算符判断要比较的值是否满足部分匹配，也叫模糊查询。
- 模糊查询中两个通配符：
  - %：代表零或任意更多的字符。
  - _：代表一个字符。
  - 如果要查询的字符串本身就含有%或_，可以使用ESCAPT进行转义。
  - ESCAPE '\'短语表示\为换码字符，紧跟在\后面的字符“%”不再具有通配符的含义，而转义为普通的“%”字符。

```
SELECT ename
FROM emp
WHERE ename LIKE 'M%'

SELECT ename
FROM emp
WHERE ename LIKE '_M%'

SELECT ename
FROM emp
WHERE ename LIKE 'S\%%' ESCAPE '\'
```

### 10.2.23 IS NULL

使用IS NULL运算符来判断要比较的值是否为空值NULL。

```
SELECT comm
FROM emp
WHERE comm IS NULL
```

### 10.2.24 AND

要求两个条件都为真，结果才为真。

```
SELECT ename,job
FROM emp
WHERE ename LIKE 'S%' AND job='CLERK'
```

### 10.2.25 OR

只需要两个条件中的一个为真，结果就返回真。

```
SELECT ename,job
FROM emp
WHERE ename LIKE 'S%' OR job='CLERK'
```

### 10.2.26 NOT

可以和IN、BETWEEN AND、LIKE、IS NULL一起使用。

```
SELECT job
FROM emp
WHERE job NOT IN('CLERK')
```

### 10.2.27 ORDER BY子句

ORDER BY子句能对查询结果集进行排序，语法结构如下：

```
SELECT  [DISTINCT] { * | 列名|表达式[别名][,...]}
FROM表名 [WHERE  条件]
[ORDER BY  {列名|表达式|列别名|列序号} [ASC|DESC],…]
```

注：

- 可以按照列名、表达式、列别名、结果集的列序号排序。
- ASC：升序，默认值。
- DESC：降序。
- ORDER BY 子句必须写在SELECT语句的后。

**排序规则**

- 数字升序排列小值在前，大值在后。即按照数字大小顺序由小到大排列。
- 日期升序排列相对较早的日期在前，较晚的日期在后。
- 字符升序排列按照字母由小到大的顺序排列，即由A-Z排列；中文升序按照字典顺序排列。
- 空值在升序排列中排在后，在降序排列中排在开始。

### 10.2.28 按列名升序排序

```
SELECT sal
FROM emp
ORDER BY sal
```

### 10.2.29 按列名降序排序

```
SELECT sal
FROM emp
ORDER BY sal DESC
```

### 10.2.30 按列别名排序

```
SELECT sal salary
FROM emp
ORDER BY salary
```

### 10.2.31 多列参与排序

```
SELECT sal,comm
FROM emp
ORDER BY sal,comm DESC
```

注：

- 参与排序的多列都可以指定升序或者降序。
- ORDERBY子句中可以写没在SELECT列表中出现的列。

### 10.2.32 按结果集列序号排序

```
SELECT sal,comm
FROM emp
ORDER BY 2
```

注：

- 列名可以用SELECT语句后列的顺序号来代替。

## 10.3 多表连接

### 10.3.1 连接

- 连接是在多个表之间通过一定的连接条件，使表之间发生关联，进而能从多个表之间获取数据。 

- 在WHERE子句中书写连接条件

- 如果在多个表中出现相同的列名，则需要使用表名作为来自该表的列名的前缀。
- N个表相连时，至少需要N－1个连接条件。

### 10.3.2 笛卡尔积

- 第一个表中的所有行和第二个表中的所有行都发生连接。 
- 为了避免笛卡尔积的产生，通常需要在WHERE子句中包含 一个有效的连接条件。
- 产生： 
  - 连接条件被省略。
  - 连接条件是无效的。

```
SELECT emp.ename,dept.deptno
FROM emp,dept
```

注：emp表14行，dept表4行，上面得到的结果有14*4=56行。

### 10.3.3 等值连接

```
SELECT emp.ename,dept.deptno
FROM emp,dept
WHERE emp.deptno=dept.deptno
```

### 10.3.4 表别名

```
SELECT e.ename,d.dname
FROM emp e,dept d
WHERE e.deptno=d.deptno
```

### 10.3.5 非等值连接

```
SELECT e.ename,e.sal,s.grade
FROM emp e,salgrade s
WHERE e.sal BETWEEN s.losal AND s.hisal
```

### 10.3.6 外部连接

在多表连接时，可以使用外部连接来查看哪些行，按照连接条件没有被匹配上。 

外部连接的符号是(+)。

```
SELECT e.ename,d.dname,d.deptno
FROM emp e,dept d
WHERE e.deptno(+)=d.deptno
```

### 10.3.7 自身连接

也叫自连接，是一个表通过某种条件和本身进行连接的一 种方式，就如同多个表连接一样。

```
SELECT e.ename,m.ename 经理
FROM emp e,emp m
WHERE e.mgr=m.empno
```

### 10.3.8 SQL:1999语法的连接

ANSI SQL:1999标准的连接语法

- Oracle除了上述自己的连接语法外，同时支持美国国家 标准协会（ANSI）的SQL:1999标准的连接语法。

### 10.3.9 交叉连接

交叉连接会产生两个表的交叉乘积，和两个表之间的笛卡尔积是一样的；

使用CROSS JOIN子句完成。

```
SELECT e.ename,d.dname
FROM emp e
CROSS JOIN dept d
```

### 10.3.10 自然连接

- 自然连接是对两个表之间相同名字和数据类型的列进行的等值连接；
- 如果两个表之间相同名称的列的数据类型不同，则会产生错误；
- 使用NATURAL JOIN子句来完成。

```
SELECT ename,dname
FROM emp
NATURAL JOIN dept
```

### 10.3.11 USING子句

自然连接是使用所有名称和数据类型相匹配的列作为连接条件，而USING子句可以指定用某个或某几个相同名字和数据类型的列作为连接条件。

```
SELECT deptno,e.ename,d.dname
FROM emp e 
JOIN dept d USING(deptno)
WHERE deptno=20
```

注： 

- 如果有若干个列名称相同但数据类型不同，自然连接子句可以用USING子句来替换，以指定产生等值连接的列。
- 如果有多于一个列都匹配的情况，使用USING子句只能指定其中的一列。
- USING子句中的用到的列不能使用表名和别名作为前缀。
- NATURAL JOIN子句和USING子句是相互排斥的，不能同时使用。

### 10.3.12 ON子句

- 自然连接条件基本上是具有相同列名的表之间的等值连接。
- 如果要指定任意连接条件,或指定要连接的列，则可以使用ON子句。
- 用ON将连接条件和其它检索条件分隔开，其它检索条件写在WHERE子句。
- ON子句可以提高代码的可读性。

```
SELECT e.deptno,e.ename,d.dname
FROM emp e
JOIN dept d
ON e.deptno=d.deptno
WHERE e.deptno=20
```

### 10.3.13 左外连接

左外连接以FROM子句中的左边表为基表，该表所有行数据按照连接条件无论是否与右边表能匹配上，都会被显示出来。

```
SELECT e.deptno,e.ename,d.dname
FROM emp e
LEFT OUTER JOIN dept d
ON e.deptno=d.deptno
```

### 10.3.14 右外连接

右外连接以FROM子句中的右边表为基表，该表所有行数据按照连接条件无论是否与左边表能匹配上，都会被显示出来。

```
SELECT e.deptno,e.ename,d.dname
FROM emp e
RIGHT OUTER JOIN dept d
ON e.deptno=d.deptno
```

### 10.3.15 全外连接

全外连接返回两个表等值连接结果，以及两个表中所有等值连接失败的记录。

```
SELECT e.deptno,e.ename,d.dname
FROM emp e
FULL OUTER JOIN dept d
ON e.deptno=d.deptno
```

## 10.4 分组函数

### 10.4.1 分组函数

分组函数是对表中一组记录进行操作，每组只返回一个结果，即首先要对表记录进行分组，然后再进行操作汇总，每组返 回一个结果，分组时可能是整个表分为一组，也可能根据条件分成多组。

分组函数常用到以下五个函数：

- MIN
- MAX
- SUM
- AVG
- COUNT

注：

- MIN和MAX函数主要是返回每组的最小值和最大值。 

```
SELECT hiredate
FROM emp
```

- MIN和MAX可以用于任何数据类型。

- SUM和AVG函数分别返回每组的总和及平均值。 

```
SELECT SUM(sal),AVG(sal)
FROM emp
```

- SUM和AVG函数都是只能够对数值类型的列或表达式操作。 

- COUNT函数返回满足条件的非空(NULL)行的数量 。 

- COUNT(*)：返回表中满足条件的行记录数。

- 组函数中的DISTINCT会消除重复记录后再使用组函数。

```
SELECT COUNT(DISTINCT deptno)
FROM emp
```

- 除了COUNT(*)之外，其它所有分组函数都会忽略列中的空值，然后再进行计算。

- 在分组函数中使用NVL函数可以使分组函数强制包含含有空值的记录。

```
SELECT COUNT(comm)
FROM emp
  
SELECT COUNT(NVL(comm,0))
FROM emp
  
结果分别为：
4
14
```

### 10.4.2 GROUP BY子句

- GROUP BY子句可将表中满足WHERE条件的记录按照指定的列划分成若干个小组。

```
SELECT deptno,SUM(sal)
FROM emp
GROUP BY deptno
```

- 在SELECT列表中除了分组函数那些项，所有列都必须包含在GROUP BY子句中。

```
SELECT ename,deptno,SUM(sal)
FROM emp
GROUP BY ename,deptno
```

- GROUP BY所指定的列并不是必须出现在SELECT列表中。

```
SELECT SUM(sal)
FROM emp
GROUP BY deptno
```

### 10.4.3 HAVING子句

使用HAVING子句限制组

- 记录已经分组。
- 使用过组函数。
- 与HAVING子句匹配的结果才输出。

```
SELECT deptno,AVG(sal)
FROM emp
GROUP BY deptno
HAVING AVG(sal)>2000
```

### 10.4.4 组函数和多表连接

```
SELECT e.deptno,d.dname,COUNT(*)
FROM emp e,dept d
WHERE e.deptno=d.deptno
GROUP BY e.deptno,d.dname
```

### 10.4.5 组函数的嵌套

与单行函数不同，组函数只能嵌套两层。

```
SELECT deptno,COUNT(NVL(comm,0))
FROM emp
GROUP BY deptno
```

## 10.5 子查询

括号内的查询叫做子查询，也叫内部查询，先于主查询执行 。

子查询的结果被主查询（外部查询）使用。

expr operator包括比较运算符：

- 单行运算符：>、<、=、>=、<>、<=。
- 多行运算符：IN、ANY、ALL。

子查询可以嵌于以下SQL子句中：

- FROM子句
- WHERE子句
- HAVING子句

使用：

- 子查询要用括号括起来。
- 将子查询放在比较运算符的右边。
- 对于单行子查询要使用单行运算符。
- 对于多行子查询要使用多行运算符

### 10.5.1 单行子查询

子查询只返回一行一列。

使用单行运算符。

```
SELECT ename,sal
FROM emp
WHERE sal=
      (SELECT MAX(sal)
      FROM emp)
```

### 10.5.2 多行子查询

子查询返回记录的条数可以是一条或多条。

和多行子查询进行比较时，需要使用多行操作符，多行操作符包括：IN、ANY和ALL。

**IN**

```
SELECT deptno,ename,sal
FROM emp
WHERE sal IN
      (SELECT sal
      FROM emp
      WHERE deptno=20)
```

**ANY**

表示和子查询的任意一行结果进行比较，有一个满足条件即可。

- `< ANY`：表示小于子查询结果集中的任意一个，即小于最大值就可以。
- `>ANY`：表示大于子查询结果集中的任意一个，即大于最小值就可以。
- `= ANY`：表示等于子查询结果中的任意一个，即等于谁都可以，相当于IN。

```
SELECT deptno,ename,sal
FROM emp
WHERE sal > ANY
      (SELECT sal
      FROM emp
      WHERE deptno=20)
AND deptno <> 10
```

**ALL**

表示和子查询的所有行结果进行比较，每一行必须都满足条件。

- `< ALL`：表示小于子查询结果集中的所有行，即小于最小值。
- `> ALL`：表示大于子查询结果集中的所有行，即大于最大值。
- `= ALL`：表示等于子查询结果集中的所有行，即等于所有值，通常无意义。

```
SELECT deptno,ename,sal
FROM emp
WHERE sal > ALL
      (SELECT sal
      FROM emp
      WHERE deptno=30)
AND deptno <> 10
```

### 10.5.3 多列子查询

- 多列子查询可以在一个条件表达式内同时和子查询的多个列进行比较。
- 多列子查询通常用IN操作符完成。
- 如果子查询的结果中有一条空值，这条空值导致主查询没有记录返回。 

```
SELECT ename
FROM emp
WHERE empno NOT IN
                (SELECT nvl(mgr,0)
                FROM emp)
```

### 10.5.4 在FROM子句中使用子查询

```
SELECT a.ename,a.deptno,b.sa
FROM emp a,(SELECT deptno,AVG(sal) sa
            FROM emp
            GROUP BY deptno) b
WHERE a.deptno=b.deptno
```

### 10.5.5 ROWNUM

- ROWNUM是一个伪列，伪列是使用上类似于表中的列，而实际并没有存储在表中的特殊列。

- ROWNUM的功能是在每次查询时，返回结果集的顺序号，这个顺序号是在记录输出时才一步一步产生的，第一行 显示为1，第二行为2，以此类推。

```
SELECT ROWNUM,ename
FROM emp
```

### 10.5.6 TOP-N查询

Top-N查询主要是实现表中按照某个列排序，输出最大或最小的N条记录功能。 

- ASC：查询最小的N条记录。
- DESC：查询最大的N条记录。

## 10.6 嵌套子查询

### 10.6.1 嵌套子查询

在通常的子查询中，子查询是以嵌套的方式写在父查询的WHERE、HAVING、FROM子句中，所以被 称为嵌套子查询。

嵌套子查询的执行过程：

- 子查询首先执行一次。
- 用来自子查询的值确认或取消父查询的候选行。

```
SELECT ename,sal
FROM emp e,(SELECT deptno,AVG(sal) sa
            FROM emp
            GROUP BY deptno) d
WHERE e.deptno=d.deptno
AND e.sal>d.sa
```

### 10.6.2 相关子查询

父查询中的行每被处理一次，子查询就执行一次。

```
SELECT ename,sal
FROM emp e
WHERE sal>(SELECT AVG(sal)
           FROM emp
           WHERE deptno=e.deptno)
```

查询过程：

- 取得父查询的候选行。
- 用候选行被子查询引用列的值执行子查询。
- 用来自子查询的值确认或取消候选行。
- 重复步骤1、2、3，直到父查询中无剩余的候选行。

### 10.6.3 EXISTS和NOT EXISTS

- EXISTS判断是否“存在”，具体操作如下：
  - 子查询中如果有记录找到，子查询语句不会继续执行， 返回值为TRUE。
  - 子查询中如果到表的末尾也没有记录找到，返回值为 FALSE。
- EXISTS子查询并没有确切记录返回，只判断是否有记录存在，而且只要找到相关记录，子查询就不需要再执行，然后再进行下面的操作。这样大大提高了语句的执行效率。
- NOT EXISTS正好相反，判断子查询是否没有返回值。如果没有返回值，表达式为真，如果找到一条返回值，则为假。

```
SELECT ename
FROM emp e
WHERE EXISTS (SELECT '1'
             FROM emp
             WHERE mgr=e.empno)
```

注：

- 在EXISTS子句中，并没有确切记录返回，只返回真或假。 所以’1’只是占位用，无实际意义。

```
SELECT ename
FROM emp e
WHERE NOT EXISTS (SELECT '1'
             FROM emp
             WHERE mgr=e.empno)
```

注：

- NOT EXISTS操作符因为运算方法与NOT IN不同，只会返回TRUE或FALSE，不会返回空值，所以不需要考虑子查询去除值的问题。

# 十一、Gradle


# 十二、Kotlin


# 十三、Python


# 十四、UML


# 十五、C


# 十六、Markdown

## 16.1 Markdown基础语法

Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式，广泛用来写博客。

推荐编辑器：Typora、MarkdownPad、有道云笔记等
线上编辑器：简书(https://www.jianshu.com)、Md2All(http://md.aclickall.com/)等

### 16.1.1 标题

在文本前面加上`#`，如一级标题加一个，二级标题加两个，如：

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

### 16.1.2 列表

有序列表直接在文字前面加`1.` `2.` `3.`，如：

```
1.有序列表
2.有序列表
```

无序列表就在文字前面加`- `或`+ `，后面有一个空格，如：

```
- 无序列表
- 无序列表
```

### 16.1.3 分割线

三个或更多的`---` `-------`。

### 16.1.4 引用

在文字前面加`>`，如：

```
> 引用
```

### 16.1.5 粗体

在文字两端加`**`，如：

```
**粗体**
```

### 16.1.6 斜体

在文字两端加`*`，如：

```
*斜体*
```

### 16.1.7 代码引用

单行代码在代码左右加一个`，多行代码则在代码上下加上三个```，如：

```
`单行代码`
```

```
​```
多行代码
多行代码
​```
```
### 16.1.8 图片

`![]()`，[中括号中间写说明]，(小括号中间是图片链接)，如：

```
![image.png](https://upload-images.jianshu.io/upload_images/6025530-547fc28e5dc9365a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```

### 16.1.9 超链接

`[]()`，[中括号中间写索引]，(小括号中间是链接)，如：

```
[我的个人博客](https://lcfu1.github.io/MyNote)
```

### 16.1.10 表格

如下：

```
a |  b  | c
--|-----|----
1 |  1  | 1
2 |  2  | 2
3 |  3  | 3
```

或：

```
|a    |a    |a    |
|:----|:---:|----:|
|1    |1    |1    |
|2    |2    |2    |
|3    |3    |3    |
```

### 16.1.11 特殊符号

```
&copy; & &uml; &trade; &iexcl; &pound; &amp; &lt; &gt; &yen; &euro; &reg; &plusmn; &para; &sect; &brvbar; &macr; &laquo; &middot; X&sup2; Y&sup3; &frac34; &frac14;  &times;  &divide;   &raquo; 18&ordm;C  &quot;  &apos;
```

效果按顺序如下：

&copy; & &uml; &trade; &iexcl; &pound; &amp; &lt; &gt; &yen; &euro; &reg; &plusmn; &para; &sect; &brvbar; &macr; &laquo; &middot; X&sup2; Y&sup3; &frac34; &frac14;  &times;  &divide;   &raquo; 18&ordm;C  &quot;  &apos;

# 十七、网络通信


# 十八、物联网安全


# 十九、大数据


# 二十、推荐网站

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

# 二十一、推荐好书

## 21.1 Android

- 第一行代码 - 郭霖
- Android开发艺术探索 - 任玉刚
- Android编程权威指南（3）
- Android开发进阶从小工到专家 - 何红辉
- 巧用Gradle构建Android应用 - Ken Kousen

## 21.2 Java

- java 2 实用教程(第四版)
- java编程思想

# 二十二、推荐神器

## 22.1 LICEcap(录屏工具)

下载地址：https://licecap.en.softonic.com/ ，下载并安装。
使用步骤：
1.打开，点击Record…，填写文件名，保存。
2.然后LICEcap就会倒计时3秒后开始录制，点击Stop后保存。

效果图：
![20190117_LICEcap](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190117_LICEcap.gif)

## 22.2 Pointofix(桌面画板工具)

下载地址：http://www.pointofix.de/download.php ，下载并安装。
不过安装好的Pointofix不是中文的，需要在官网下载语言翻译包。

![20190117_PointofixLanguagePack](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190117_PointofixLanguagePack.PNG)

语言翻译包的使用可以看上面图片最后的说明，解压并找到`pointofix_translation_zh-cn.ini`，重命名为`pointofix_translation.ini`，然后放到pointofix的安装目录下即可，重启就变成中文了。

## 22.3 Typora（Markdown编辑器）

描述：Markdown编辑器，支持边输入边预览。
官网：https://www.typora.io/ 。

效果图：

![20190118_Typora](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190118_Typora.gif)

## 22.4 HEditor（HTML/CSS/JavaScript在线编辑器）

使用：https://lcfu1.github.io/MyNote/HEditor.html

效果图：

![20190120_HEditor](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190120_HEditor.PNG)

## 22.5 Kotlin在线编辑器

描述：JetBrains官方的kotlin在线编辑器。

使用：<https://try.kotlinlang.org/>

效果图：

![20190120_Kotlin](https://raw.githubusercontent.com/lcfu1/MyNote/master/img/tool/20190120_Kotlin.PNG)

## 22.6 shields

描述：Concise, consistent, and legible badges in SVG and raster format。

项目的github地址：<https://github.com/badges/shields>

使用：<https://shields.io/>

效果：

[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/lcfu1/MyNote)  [![Packagist](https://img.shields.io/packagist/l/doctrine/orm.svg)](https://github.com/lcfu1/MyNote/blob/master/LICENSE)

# 二十三、推荐资源

- https://github.com/open-android/Android
- https://www.jianshu.com/p/9618c038135f