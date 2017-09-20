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

