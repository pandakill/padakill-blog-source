---
title: Android开发规范
date: 2017-09-20 22:36:14
tags: [Android,开发规范]
categories: [Android]
---
# 项目包名命名规范

## 包名取得好的作用
应用包名主要用于存放各类文件，如果包名命名的好，可以方便程序员在开发的过程中更有效的找到对应的代码相关文件，减轻许多的工作量，
项目能够按文件功能将各类文件妥善存放，相信也能为程序员带来愉悦的开发心情。

## 包名在xian的应用
在自有的android项目中，包名是按两种规则来存放文件和为各类包命名的。

- 第一种结构：首先命名的第一个维度是功能，第二个维度是模块。首先功能为先，最后才是以模块来命名包名。如图1截图所示
- 第二种结构：其实包名的结构，实践之后，发现第一维度使用模块，第二维度是功能的包名似乎能够更好，建立一个公共的包，存放公共的工具、
dataCenter等，模块的包名与dataCenter同级，如果项目一旦壮大的话，第一种包名结构会出现明显的短板。如图2截图所示

例如在两种不同结构的包名在项目中的应用，app的包截图如下：

![图1 第一种结构](http://owl21dcva.bkt.clouddn.com//img/20161111150345978.jpeg)

![图2 第一种结构](http://owl21dcva.bkt.clouddn.com//img/20161111150340306.jpeg)

同样是采用了MVP的框架，但是在项目壮大的时候，图1中的结构在下拉查看的时候，会出现明显的缺点，就是presenter、view、ui三个文件夹的子文件夹
数量太多，在你需要寻找文件的时候很麻烦，会经常跳来跳去。而图1显示的第二种报名结构，相对来说会好一点，例如login模块的presenter、view、
ui都放在了login文件夹当中，在调试和debug迭代的时候就很方便可以找到login这一模块的相关文件和类

## 命名的规范

### 包名一般要求小写
包名一般要求小写，并且尽量不出现下划线等字符，值得注意的是，需要用英文来命名而不是中文。例如views，widget

### 包名要求言简意赅
一般是功能、模块的简写，能够让包名能够一目了然，知道这个包里面放的是什么文件。例如ui、activity等

# java文件命名规范

## 驼峰式命名
java类的命名首字母要求大写，采取驼峰式命名，并且要求以MLY开头；同时要求对类进行注释！！！！！例如：

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午10:15
 * 描述: 此类封装了关于APP城市相关的数据读取与缓存，使用缓存+服务器获取数据的策略
 */
public class PDCityDataCenter {
    private static final String TAG = MLYCityDataCenter.class.getSimpleName();
}
```

## 言简意赅
java类的命名要尽量一目了然，闻其名而知其意；例如：

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: 订单状态页面
 */
public class PDOrderStatusActivity extends BaseAppCompatActivity {
}
```

## 接口文件的命名
如果是一般的接口（interface）文件，则命名为Ixxx.java，例如：

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: mvp的view基类，所有的views都继承该类
 */
public inteface IMVPView {
}
```

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: 欢迎页面的view接口，继承自IMVPView，在这里封装一些view的控制方法
 */
public class IWelcomeActivityView extends IMVPView {
}
```

## 监听器的命名
如果是监听文件的，一般是以On开头，例如：OnGetCityDataListener.java

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: 获取城市数据的监听器，通过OnSuccess回调获取成功
 */
public interface OnGetCityDataListener {
    void OnSuccess(City city);

    void OnFail(int errCode, String errMsg);
}
```

## java变量、方法等的命名

### 成员变量，以m开头

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: app的主页面，继承自BaseAppComPatActivity
 */
public class PDMainActivity extends BaseAppCompatActivity {

    /**
     * 成员变量命名以m开头
     */
    private Context mContext = null;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        mContext = this;
    }
}
```

### 静态变量，以s开头

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午11:15
 * 描述: app的主页面，继承自BaseAppComPatActivity
 */
public class PDMainActivity extends BaseAppCompatActivity {


    /**
     * 成员变量命名以m开头
     */
    private Context mContext = null;

    /**
     * 静态变量命名以s开头
     */
    private static String sTag = null;


    @Override
    public void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);

        mContext = this;
        sTag = this.getClass().getSimpleName();
    }
}
```

### 函数方法的命名
函数方法的命名一般是多个动词+名词组合，同样使用驼峰式命名，方法名首字母小写，要求命名能够描述出该方法的作用，并且尽可能的给函数方法进行
注释说明。

```java
/**
 * 创建人: fangzanpan
 * 创建时间: 16/8/5 上午10:15
 * 描述: 此类封装了关于APP城市相关的数据读取与缓存，使用缓存+服务器获取数据的策略
 */
public class PDCityDataCenter {
    private static final String TAG = PDCityDataCenter.class.getSimpleName();

    private static PDCityDataCenter mInstance = new PDCityDataCenter();
    private static Context mContext = null;


    public PDCityDataCenter getInstance(Context context) {
        mContext = context;
        if (mInstance == null) {
            mInstance = new PDCityDataCenter();
        }
        return mInstance;
    }


    /**
     * 从缓存中读取选中的城市
     *
     * @return 缓存中选中的城市
     */
    public City getCityFromCache() {
    }


    /**
     * 从服务器中读取选中的城市
     *
     * @return 服务器返回的城市
     */
    public City getCityFromServer() {
    }

}
```

## 在Android Studio中设置一些规范
在编译器里面就可以对一些规则进行配置，酱紫在开发中就能很方便而且很顺手的就用起来了。建议大家都可以设置一下。

### 设置Java4个空格
![图3 设置Java4个空格](http://owl21dcva.bkt.clouddn.com//img/%E8%AE%BE%E7%BD%AEJava4%E4%B8%AA%E7%A9%BA%E6%A0%BC.png)

### 设置全局变量和静态变量以m、s开头
![图4 设置全局变量和静态变量以m、s开头](http://owl21dcva.bkt.clouddn.com//img/%E8%AE%BE%E7%BD%AEjava%E5%8F%98%E9%87%8F%E5%89%8D%E7%BC%80.png)

# 资源文件命名规范

## 资源文件命名规范的重要性
资源文件命名以小写字母+下划线组成，名字不怕长就怕太简略，要尽可能一眼能看出该资源文件是用来干什么的，我改怎么去找到这个文件？
鉴于Android开发肯定会存在很多很多的资源，所以最好能够一个一个模块的放好、并且有明显的命名去命名，方便自己也方便他人在二次开发、
bug修复和后续迭代等操作中能够更快的定位到。这个步骤很繁琐，要做好不简单，见微知著，细心耐心！加油吧！！

其实资源文件的命名很难去做一个比较好而系统的规范，这就要求平时开发的时候开发人员能够自觉地去探索和建立一个比较好的、适合项目发展的开发方式。

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <!--
        1. 在命名的时候，最好能以一个 xxxx start 开头 然后以 xxxx end 结束，表明一个模块的资源文件的区块
        2. 同个模块的资源文件，最好能以一个统一的前缀，然后再加以后面的详细描述，这样比较能清晰而且也能减少出现类似资源文件的混淆
        3. 尽量多的在名字里表明用处，多点解释能够更好的让其他人明白你的用途，总比别人去猜或者一定要进来看你的资源文件然后去理解好的多吧
    -->

    <!-- 网络错误提示 start -->
    <string name="network_tips_error">哎呀，网络有点问题</string>
    <string name="network_tips_im_error">当前网络不可用，请检查你的网络设置</string>
    <string name="network_tips_unknown_error">未知错误</string>
    <!-- 网络错误提示 end-->

    <!-- tabhost栏标题 start -->
    <string name="tabhost_title_home">首页</string>
    <string name="tabhost_title_discovery">精选</string>
    <string name="tabhost_title_appointment">预约</string>
    <string name="tabhost_title_my">我的</string>
    <!-- tabhost栏标题 end -->

    <!-- 页面标题 start -->
    <string name="page_title_index">首页</string>
    <string name="page_title_appointment">预约</string>
    <string name="page_title_my_wallet">我的钱包</string>
    <string name="page_title_my_artisan_detail">技师详情</string>
    <string name="page_title_my_product_detail">作品详情</string>
    <!-- 页面标题 end -->
</resources>
```


又例如style文件的命名示例：

```xml
<?xml version="1.0" encoding="utf-8"?>  
<resources>  
   
<!--  
    1. 如果是有存在父子关系的，可以将这几个样式放在附近一起，并且命名以同样的前缀命名  
    2. 其他的参考string文件的命名  
    3. 为什么这里不需要start和end？因为string是单标签的，基本上所有的都是以<string></string>来定义，而style文件一个区块已经用<style></style>来帮助分区块了，所以可以不用start和end来帮助标记。  
-->  
  
    <!-- 订单确认页的textview样式 -->  
    <style name="order_submit_text_style">  
        <item name="android:layout_width">match_parent</item>  
        <item name="android:layout_height">48dp</item>  
        <item name="android:textColor">@color/Black</item>  
        <item name="android:textSize">14sp</item>  
        <item name="android:paddingLeft">15dp</item>  
        <item name="android:layout_marginLeft">8dp</item>  
        <item name="android:layout_marginRight">8dp</item>  
    </style>  
  
    <!-- 全局的分隔线的样式 -->  
    <style name="underline_common_view_sytle">  
        <item name="android:layout_width">match_parent</item>  
        <item name="android:layout_height">1px</item>  
        <item name="android:layout_marginLeft">12dp</item>  
        <item name="android:background">@color/Gray_Line</item>  
    </style>  
  
    <!-- 支付页的分割线样式 -->  
    <style name="underline_pay_view_style">  
        <item name="android:layout_width">match_parent</item>  
        <item name="android:layout_height">1px</item>  
        <item name="android:background">@color/Gray_Line</item>  
    </style>  
  
    <!-- 占满横屏的分割线样式 -->  
    <style name="underline_match_parent" parent="order_underline_view_sytle">  
        <item name="android:layout_marginRight">0dp</item>  
        <item name="android:layout_marginLeft">0dp</item>  
    </style>  
  
    <!-- 支付页的每个栏目的样式 -->  
    <style name="pay_bar_style">  
        <item name="android:layout_width">match_parent</item>  
        <item name="android:layout_height">44dp</item>  
        <item name="android:background">@drawable/listview_item_city_selector</item>  
    </style>  
  
    <!-- 支付页的的样式 -->  
    <style name="pay_text_style">  
        <item name="android:layout_width">match_parent</item>  
        <item name="android:layout_height">44dp</item>  
        <item name="android:background">@color/Black</item>  
    </style>  
  
    <!-- 支付页标题栏的text属性 -->  
    <style name="pay_textbar_text_small_style">  
        <item name="android:layout_width">wrap_content</item>  
        <item name="android:layout_height">wrap_content</item>  
        <item name="android:textColor">@color/theme_color_666666</item>  
        <item name="android:singleLine">true</item>  
        <item name="android:layout_centerVertical">true</item>  
        <item name="android:textSize">12sp</item>  
    </style>  
  
    <!-- 支付页标题栏的text属性 -->  
    <style name="pay_textbar_text_small_deep_style" parent="textbar_text_small_style">  
        <item name="android:textColor">@color/theme_color_333333</item>  
        <item name="android:textSize">12sp</item>  
    </style>  
</resources>  
```