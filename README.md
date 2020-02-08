

#一、React Native 介绍

 Facebook于2015年9月15日发布**React Native**，发展成长至今，它成为原生手机端App必不可少的开发模式之一。目前比较成熟的跨平台方案:

```
1）React Native,  Vue+Weex
2）AppCan
3）Flutter
```
React Native已经完成了对多端的支持，实现了真正意义上的面向配置开发: 开发人员可以只使用JavaScript也能编写原生移动，结合React语法构建组件，实现：**Android, iOS 两端代码的复用**，并发布上线。

![ReactNative架构图](images/img01.jpg) 

 React Native产出的并不是**“网页应用”** ， 或者说**“HTML5应用”** ，又或者**“混合应用”** ，而是一个真正的移动应用，从使用感受上和用Objective-C或Java编写的应用相比几乎是无法区分的。



## 1、开发平台选择？

- MacOS系统（推荐）

  >  iOS和Android都全部支持！

- Windows系统和Linux系统

  >  目前只支持Android



## 2、选择React Native的优势？

- 跨平台开发

  >  运用React Native，我们可以使用同一份业务逻辑核心代码来创建原生应用运行在Android端和iOS端；

- 追求极致的用户体验：

  >  热更新和热部署 

- learn once，write everywhere（最具魅力）

  >  React Native不强求一份原生代码支持多个平台，所以不是“Write once, run anywhere”（Java），而是“Learn once, write anywhere”。

![React Native上层架构图](images/img02.png) 



## 3、React Native开发注意事项

 React Native所需要的技术栈比较多，需要良好的 JavaScript功底，最好还需要懂一些iOS和Android原生开发，才能很好驾驭中大型移动端跨平台项目。初学者使用RN开发项目，建议选择：
- 功能适中，交互一般，不需要特别多的系统原生支持
- 对于部分复杂的应用，可以考虑原生+React Native混合开发



#二、React Native环境搭建



##1、Mac OS系统 (RN环境搭建)

###1、安装前注意：



- 在Max OS X 系统中，homebrew在安装软件时可能会碰到 `/usr/local`目录不可写的权限问题。可以使用下面的命令修复：

  ```
  // 使用下面这个命令修改 目录权限
  sudo chown -R `whoami` /usr/local
  // 也可以使用其它权限, 修改
  ```

- 如果命令行提示`command not found`，请加上sudo获得最高权限  



### 2、环境需求 

- 安装Homebrew

  >  Homebrew是OS X的套件(包)管理器，用于安装Node.js和一些其他必须的工具软件。

  - 安装命令

    ```
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ```

-  安装npm 和 Node.js

  >  node.js最好安装最新版本，node安装成功后npm自动也就有了，直接下载安装Node.js，网址：https://nodejs.org/en/download/ ，可以以软件形式安装，或者命令行形式安装：

  ```
  brew install node
  ```

- 安装WatchMan

  >  WatchMan是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。

  ```
  brew install watchman
  ```

  - 验证是否安装成功

  ![验证是否安装成功](images/img03.jpg) 



### 3、React Native安装

- **react - native 安装文档地址**: https://reactnative.cn/docs/getting-started.html

  在安装或者运行程序是如果有任何问题, 第一时间查看文档

- Yarn、React Native的命令行工具（react-native-cli）

  >  Yarn是Facebook提供的替代npm的工具，可以加速node模块的下载。
  >
  > React Native的命令行工具用于执行 `创建、初始化、更新项目、运行打包服务（packager）`等任务。 

- 查看是否安装成功

  > 全局node_moudules中查看

  ![全局node_moudules中查看](images/img04.jpg)  

   

### 4、Xcode安装

React Native 目前需要Xcode 10 或更高版本。我们可以通过 App Store 或是到Apple 开发者官网上下载。安装完Xcode会同时安装 Xcode IDE、Xcode 的命令行工具和 iOS 模拟器。

> 如果使用的不是 Xcode 10 , 使用命令 `react-native init app ` 创建项目后, 在运行Xcode项目时可能报错. 
>
> 可使用下面的命令创建更低版本的 react native 工程项目

```
// 创建指定版本的RN工程项目
npx react-native init MyApp --version 0.44.3
```



### 5、JDK 和 Android Studio



#### 1、安装最新版的JDK

在命令行中输入``` javac -version```来查看你当前安装的JDK版本。

下载安装地址：http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html （资料中已经存放）



#### 2、安装Android studio

在安装过程中请严格执行以下选项：

- 1、选择 Custom 选项

  ![image](images/img05.jpg) 

  

- 2、勾选`Performance`和`Android Virtual Device`

  ![image](images/img06.jpg)  



- 3、安装完成后，在Android Studio的启动欢迎界面中选择 `Configure | SDK Manager` 

  ![image](images/img07.jpg) 

- 4、在`SDK Platforms`窗口中，选择`Show Package Details`，然后在`Android 9.0 (Pie)`中勾选下图所示并安装。

  ![image](images/img08.jpg) 

  

  ![image](images/img09.jpg)   

- 5、在`SDK Tools`窗口中，选择`Show Package Details`，然后在`Android SDK Build Tools`中勾选`Android SDK Build-Tools 28.0.3`（必须有这个版本）。

  ![image](images/img10.jpg) 

- 6、ANDROID_HOME环境变量

  React Native 需要通过环境变量来了解你系统中的 Android SDK 装在什么路径，从而正常进行编译。具体的做法是把下面的命令加入到~/.bash_profile文件中，使用  vi ~/.bash_profile。

  ```
  # 如果你不是通过Android Studio安装的sdk，则其路径可能不同，请自行确定清楚。
  export ANDROID_HOME=$HOME/Library/Android/sdk
  export PATH=$PATH:$ANDROID_HOME/tools
  export PATH=$PATH:$ANDROID_HOME/tools/bin
  export PATH=$PATH:$ANDROID_HOME/platform-tools
  export PATH=$PATH:$ANDROID_HOME/emulator
  ```



### 6、安装Genymotion

Genymotion是一个第三方模拟器，它比Google官方的模拟器更易设置且性能更好。

但是，它只针对个人用户免费(可能需要VPN)。

- 下载并安装Genymotion(https://www.genymotion.com/)
- 打开Genymotion,如果你尚未安装VirtualBox,它有可能会提示你安装
- 创建一个模拟器并启动
- 按下`⌘+M` 可以打开开发者菜单(在安装并启动了React Native应用之后)

###### 3）Gradle Daemon
开启Gradle Daemon可以极大地提升java代码的增量编译速度。





##2、Windows系统(RN环境搭建)



**确保所有的命令行操作都在管理员权限下操作** 



### 1、需要安装的插件



####1、Chocolatey

Chocolatey是一个Windows上的包管理器，类似于Mac上的watchMan。一般的安装步骤应该是下面这样, 如果国内访问失败, 请使用翻墙工具:



#### 2、Python 2

```
choco install python2
```



#### 3、Node

```
choco install nodejs.install
```
打开命令提示符窗口，使用Chocolatey来安装NodeJS，或者通过软件安装。安装完node后建议设置npm镜像以加速后面的过程（或使用科学上网工具）。

```
 npm config set registry https://registry.npm.taobao.org --globalnpm
 npm config set disturl https://npm.taobao.org/dist --global
```



### 2、创建并运行React Native项目



####1、React Native的第一个应用

- 执行命令,生成一个工程

  ```
  react-native init 项目名称
  ```

  >  注意:
  >
  > 由于众所周知的网络原因，需要等待一段时间（具体视网络情况而定）。react-native命令行从npm官方源拖代码时会遇上麻烦，可以将npm仓库源替换为国内镜像：

  ```
  npm config set registry https://registry.npm.taobao.org
  npm config set disturl https://npm.taobao.org/dist
  ```

  - 运行截图

    ![image](images/img11.jpg) 

    

- 运行工程文件

  > 不管是 iOS 还是 Android，在开发调试阶段，都需要在 Mac 上启动一个 HTTP 服务，称为`Debug Server`，默认运行在`8081`端口，APP 通 `Debug Server `加载 js。

  ![图1 - 启动React native 服务器](images/img12.jpg) 

  - 客户端运行界面

    ![图2 - 客户端运行界面](images/img13.jpg)  

    

- 把React Native创建的应用跑在Android上
  - 命令行执行cd MyRNDemo,路径切换到项目主目录
  - 命令行执行react-native run-android进行加载运行android 应用。
  - 使用编辑器进行打开和修改index.android.js文件，接着通过菜单按钮选择Reload JS来进行刷新修改



## 3、管理React Native库的版本



在开发中，会经常的去控制React Native的版本库，得以适配各种条件下的开发，那该如何查看、控制ReactNative的版本呢？



###1、查看本地的React Native版本

- 命令行输入:

  ```
  // 查看当前 react-native-cli 的版本 
  react-native --version
  ```

  > 如果上面的命令在react-native 的工程目录下执行,  还会显示当前创建的react-native 的项目版本信息
  >
  > 我们在使用react-native-cli 脚手架创建react-native 项目时, 可以创建具体版本的 react-native 工程, 命令如下:
  >
  > ```
  > npx react-native init MyApp --version 0.44.3
  > ```

- 命令行效果:

  ![image](images/img14.jpg) 

  

###2、 更新本地的React Native版本

- 命令行输入:

  ```
  // -g 表示全局更新
  npm update -g react-native-cli
  ```

  

###3、查询react-native的npm包最新版本

NPM的全称是 `Node Package Manager `，是一个NodeJS包管理和分发工具，已经成为了非官方的发布Node模块（包）的标准。

- npm包地址 ：

  ```
  https://www.npmjs.com/package/react-native
  ```

- 命令行查询： 

  ```
  npm info react-native
  ```

  - 查询效果：
    ![image](images/img15.jpg)  





#三、React Native工程启动流程



## 1、工程结构分析



###1、初始化RN工程

```
// 创建一个react native 工程项目, LKDemo2是项目名称
react-native init LKDemo2
```



### 2、工程目录结构图

![工程目录结构图](images/img16.png) 



###3、工程启动流程分析 

> (此处一iOS为例分析)



####1、index.js文件

- iOS工程或安卓工程一启动，就会加载目录中```index.js```文件，通过```AppRegistry```去注册组件，并且把注册完成的组件输出给iOS端或Android端：

  ```
  // 引入注册组件模块
  import {AppRegistry} from 'react-native';
  // 引入组件汇总模块
  import App from './App';
  // 引入输出组件名称
  import {name as appName} from './app.json';
  
  // 注册组件，程序主入口
  // appName: 注册模块名称
  // () => App: 组件类，程序启动会自动加载该类实例化的组件对象
  AppRegistry.registerComponent(appName, () => App);
  ```

####2、AppDelegate.m 文件

- 通过Xcode打开iOS工程，或者Android Studio打开Android工程，此处以iOS端为例子。找到AppDelegate.m文件，查看客户端加载方法：

  ![AppDelegate.m](images/img17.png)  



- 代理文件中通过该方法加载JS端输出的模块，注意模块的名称两端必须保持一致：

```
initWithBridge:bridge moduleName:@"MyRNDemo" initialProperties:nil
```

- 代理文件解析加载注释如下

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
  // 1. 获取桥接文件
  RCTBridge *bridge = [[RCTBridge alloc] initWithDelegate:self launchOptions:launchOptions];
  // 2. 根据模块加载根视图
  RCTRootView *rootView = [[RCTRootView alloc] initWithBridge:bridge
                                                   moduleName:@"MyRNDemo"
                                            initialProperties:nil];

  rootView.backgroundColor = [[UIColor alloc] initWithRed:1.0f green:1.0f blue:1.0f alpha:1];

  // 3. 设置窗口
  self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
  
  // 4. 设置窗口根控制器的view
  UIViewController *rootViewController = [UIViewController new];
  rootViewController.view = rootView;
  self.window.rootViewController = rootViewController;
  
  // 5. 显示窗口
  [self.window makeKeyAndVisible];
  return YES;
}
```

####3、App.js文件

- App.js文件运行步骤
  - 加载React模块，使用其内部的API，比如：jsx语法；
  - 加载React Native原生组件，比如：`SafeAreaView, StyleSheet, View, Text,Image`等；
  - 自定义组件类，作为模块的输出；
  - 创建样式对象，传入样式对象，根据样式中的对象描述，创建样式表
  - 导出当前模块
```
/**
 * 撩课学院
 * https://itlike.com
 */

// 1. 加载React模块
import React from 'react';

// 2. 加载原生组件
import {
  SafeAreaView,
  StyleSheet,
  View,
  Text,
  StatusBar,
  Image
} from 'react-native';


// 3. 自定义组件（程序入口组件）
const App: () => React$Node = () => {
  return (
    <>
      <StatusBar barStyle="dark-content" />
      <SafeAreaView style={styles.safeView}>
         <View style={styles.viewStyle}>
           <Image
               style={{width: 168, height: 168}}
               source={{uri: 'http://www.itlike.com/template/simple/res/404/img/xiaoliao.png'}}
           />
           <Text style={styles.textStyle}>小撩陪你开启RN学习之旅！</Text>
         </View>
      </SafeAreaView>
    </>
  );
};

// 4. 创建样式对象
// 传入样式对象，根据样式中的对象描述，创建样式表
const styles = StyleSheet.create({
  safeView: {
    flex: 1
  },
  viewStyle: {
    display: 'flex',
    flex: 1,
    justifyContent:'center',
    alignItems: 'center'
  },
  textStyle: {
    fontSize: 20
  }
});

// 5. 导出当前模块
export default App;
```



## 2、语法分析



### 1、JSX语法

JSX语法是一个比较高级但很直观的JS语法糖。我们在创建View的结构时，可以用类似HTML标签的形式创建，当然最终在编译时还是会转换成JS代码。
- 函数中只要返回`组件` ，都需要用`()` 包裹 

  ```
  const App : () => React$Node = () => {
    return (
        <View></View>
    );
  };
  ```

  

- 函数中除字符串以外，赋值时都需要用`{}`包裹 

  ```
   <SafeAreaView style={styles.safeView}> </SafeAreaView>
  ```

  ```
   <Image style={{width: 168, height: 168}} 
   				source={{uri: 'http://www.itlike.com/template/simple/res/404/img/xiaoliao.png'}}
   />
  ```

- 组件内使用变量时，都需要用大括号包裹，否则会被当成普通字符串处理。

  ```
  const str = '引擎计划';
  <Text>{str}</Text>
  ```

  

###2、样式对象文件

内部以键值对的形式，取值如同JS中的对象调用。
```
const styles = StyleSheet.create({
  viewStyle: {
    display: 'flex',
    flex: 1,
    justifyContent:'center',
    alignItems: 'center'
  }
});  
```

 





#四、React Native Flex布局



##1、FlexBox布局介绍



### 1、FlexBox是什么意思呢？

- flexible（形容词）：能够伸缩或者很容易变化，以适应外界条件的变化

- box（名词）：通用的矩形容器

  > 一句话, FlexBox 就是弹性盒子的意思

  

### 2、 什么是FlexBox布局?

弹性盒模型（`The Flexible Box Module` ）,又叫Flexbox，意为“弹性布局”，旨在通过弹性的方式来**对齐** 和 **分布** 容器中内容的**空间** ，使其能适应不同屏幕，为盒装模型提供最大的灵活性。

Flex布局主要思想是：**让容器有能力让其子项目能够改变其宽度、高度（甚至是顺序），以最佳方式填充可用空间；** 

>  **React native 中的FlexBox是这个规范的一个 子集**。 
>
> 也就是说 react Native 中的Flexbox 和 网页中的Flexbox 是有一点差异的



### 3、大部分情况下是处理图中FlexItem在FlexContainer中的位置和尺寸关系

![image](images/img18.jpg) 



## 2、Flexbox开发中应用场景



### 1、Flexbox在布局中能够解决什么问题

- 浮动布局 -- `问题`

- 各种机型屏幕的适配-- `问题`

- 水平和垂直居中-- `问题`

- 自动分配宽度-- `问题`

- ......`问题`

  



###2、flex-flow流

在CSS中，常规的布局是基于块和内联流方向，而Flex布局是基于flex-flow流

>  下图很好解释了Flex布局的思想：

![image](images/img19.jpg) 

容器默认存在两根轴：**水平的主轴（main axis）**和**垂直的交叉轴又称侧轴（cross axis）**。

主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；

交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目Item默认沿主轴排列，单个项目占据的主轴空间叫做main size(主轴尺寸)，占据的交叉轴空间叫做cross size(侧轴尺寸)。



###3、主轴 侧轴

根据伸缩项目排列方式的不同，主轴和侧轴方向也有所变化：

![image](images/img20.jpg) 



## 3、Flexbox的常用属性



### 1、 容器属性

容器属性主要有以下几个:

`flexDirection`  `justfyContent`  `alignItems`  `flexWrap` 



#### 1、 flexDirection

-  flexDirection: `row | row-reverse | column | column-reverse` 

  >  该属性决定主轴的方向（即项目的排列方向）。常用的取值如下: 

  - row：主轴为水平方向，起点在左端。
  - row-reverse：主轴为水平方向，起点在右端。
  - column(默认值)：主轴为垂直方向，起点在上沿。
  - column-reverse：主轴为垂直方向，起点在下沿。

![image](images/img21.jpg)

 

#### 2、justifyContent

- justifyContent:`flex-start | flex-end | center | space-between | space-around`
  >  定义了伸缩项目Item在主轴线的对齐方式 

  - flex-start(默认值)：伸缩项目向一行的起始位置靠齐。
  - flex-end：伸缩项目向一行的结束位置靠齐。
  - center：伸缩项目向一行的中间位置靠齐。
  - space-between：两端对齐，项目之间的间隔都相等。
  - space-around：伸缩项目会平均地分布在行里，两端保留一半的空间。

  ![image](images/img22.jpg)  



####3、alignItems

- alignItems:  `flex-start | flex-end | center | baseline | stretch`

  >  定义项目在交叉轴上如何对齐，可以把其想像成侧轴（垂直于主轴）的“对齐方式”。

  - flex-start：交叉轴的起点对齐。
  - flex-end：交叉轴的终点对齐 。
  - center：交叉轴的中点对齐。
  - baseline：项目的第一行文字的基线对齐。
  - stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

  ![image](images/img23.jpg) 



####4、flexWrap

- flexWrap: `nowrap | wrap | wrap-reverse`

  >  默认情况下，项目都排在一条线（又称"轴线"）上。
  >
  > flex-wrap属性定义，如果一条轴线排不下，如何换行。

  ![image](images/img24.jpg) 

  - nowrap(默认值)：不换行。

  ![image](images/img25.jpg)  
  

  - wrap：换行，第一行在上方。 

  ![image](images/img26.jpg) 
  

  - wrap-reverse：换行，第一行在下方。（和wrap相反）

![image](images/img27.jpg)



###2、item元素属性

item 属性主要有以下几个: 

`flex` `alignSelf` 



#### 1、flex

- flex: “flex-grow”、“flex-shrink”和“flex-basis”三个属性的缩写， 其中第二个和第三个参数（flex-shrink、flex-basis）是可选参数。

  >  默认值为“0 1 auto”。

   宽度 ＝ 弹性宽度 * ( flexGrow / sum( flexGorw ) )

 ![image](images/img28.jpg) 



#### 2、alignSelf

- alignSelf:  “auto | flex-start | flex-end | center | baseline | stretch”

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。

> 默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
>
> alignSelf 元素属性相对于容器属性中的 alignItems 属性, 工程差不多, 一个作用于容器, 

![image](images/img29.jpg) 



## 4、在React Native中使用Flexbox



- 获取当前屏幕的宽度、高度、分辨率

  ```
  const App: () => React$Node = () => {
      return (
          <>
              <StatusBar barStyle="dark-content"/>
              <SafeAreaView style={{flex: 1}}>
                  <View style={{flex: 1, backgroundColor: 'red'}}>
                     <Text>
                       当前屏幕的宽度：{Dimensions.get('window').width + '\n'}
                       当前屏幕的高度：{Dimensions.get('window').height + '\n'}
                       当前屏幕的分辨率：{Dimensions.get('window').scale + '\n'}
                     </Text>
                  </View>
              </SafeAreaView>
          </>
      );
  };
  ```

  



#五、React Native常用的组件-上



## 1、 View组件

React Native组件View，其作用等同于iOS中的`UIView`,  Android中的`android.view` ，或是网页中的`<div>`标签，它是所有页面组件的父组件。

>  使用方式无差异化，基本用于容器使用。

```
const App: () => React$Node = () => {
    return (
        <SafeAreaView style={{flex: 1}}>
          <View style={{flex: 1, backgroundColor: 'cyan'}}>
            <View style={styles.view1}>
              <Text style={{color: '#fff', fontSize: 18}}>内容区域</Text>
            </View>
          </View>
        </SafeAreaView>
    );
};

const styles = StyleSheet.create({
  view1: {
    width: 150,
    height: 200,
    backgroundColor:'purple',
    marginLeft: 100,
    marginTop: 100,
    padding: 30
  }
});
```



## 2、Text组件

一个用于显示文本的ReactNative组件，和Android中的`TextView`组件或者OC中的`UILabel`组件相类似，专门用来显示基本的文本信息；

>  除了基本的显示布局之外，可以进行嵌套显示，设置样式，以及可以做事件(例如:点击)处理。

- 常用属性
  - `color` 字体颜色
  -  `numberOfLines` (number) 进行设置Text显示文本的行数，如果显示的内容超过了行数，默认其他多余的信息就不会显示了
  - `ellipsizeMode` 这个属性通常和下面的 numberOfLines 属性配合使用，表示当 Text 组件无法全部显示需要显示的字符串时如何用省略号进行修饰。取值：enum('head', 'middle', 'tail', 'clip')
  - `onPress` (fcuntion)  该方法当文本发生点击的时候调用该方法
  - `fontFamily`  字体名称
  - `fontSize`  字体大小
  - `fontStyle`   字体风格(normal,italic)
  - `fontWeight ` 字体粗细权重("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
  - `textShadowOffset`  设置阴影效果{width: number, height: number}
  - `textShadowRadius`  阴影效果圆角
  - `textShadowColor`  阴影效果的颜色
  - `letterSpacing`  字符间距
  - `lineHeight`  行高
  - `textAlign`   文本对其方式("auto", 'left', 'right', 'center', 'justify')
  - `textDecorationLine`  横线位置 ("none", 'underline', 'line-through', 'underline line-through')
  - `textDecorationStyle` 线的风格("solid", 'double', 'dotted', 'dashed')
  -  `textDecorationColor` 线的颜色
  - `writingDirection` 文本方向("auto", 'ltr', 'rtl')



- 课程代码
```
import React, { Component } from 'react';
import { Text, StyleSheet, View } from 'react-native';

export default class LKText extends Component {
    constructor(props) {
        super(props);
        this.state = {
            titleText: '撩课学院',
            subText: '喜欢IT,就上撩课！',
            bodyText: '对酒当歌，人生几何！对酒当歌，人生几何！对酒当歌，人生几何！'
        };
    }

    render() {
        return (
            <>
                <Text style={styles.baseText}>
                    <Text style={styles.titleText}>
                        {this.state.titleText}{'\n'}
                    </Text>
                    <Text>
                        {this.state.subText}
                    </Text>
                </Text>
                <View style={{backgroundColor:'red', width: 300, height: 200}}>
                    <Text
                        style={{fontSize: 20, lineHeight: 40}}
                        numberOfLines={4}
                        ellipsizeMode='middle'
                    >
                        {this.state.bodyText}
                    </Text>
                </View>
            </>
        );
    }
}

const styles = StyleSheet.create({
    baseText: {
        fontFamily: 'Cochin',
        fontSize: 30
    },
    titleText: {
        fontSize: 40,
        fontWeight: 'bold',
    },
});
```



## 3、Image组件

在开发中还有一个非常重要的组件Image，通过这个组件可以展示各种各样的图片，而且在React Native中该组件可以通过多种方式加载图片资源。包括网络图片、静态资源、临时的本地图片、以及本地磁盘上的图片（如相册）等。



### 1、Image组件三种加载方式

```
 render() {
        return (
            <View>
                {/*本地加载*/}
                <Image
                    source={require('./images/bit.jpeg')}
                    style={{width: 200, height: 200}}
                />
                {/*网络加载*/}
                <Image
                    style={{width: 168, height: 168}}
                    source={{uri: 'http://www.itlike.com/template/simple/res/404/img/xiaoliao.png'}}
                />
                {/*base64加载*/}
                <Image
                    style={{width: 66, height: 58}}
                    source={{uri: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg=='}}
                />
            </View>
        );
    }
```


###2、设置Image组件的显示模式

- resizeMode，常用取值有：`center、repeat、contain、cover、stretch`。

```
render() {
        return (
            <View>
                <Image
                    style={{width: 400, height: 300, resizeMode: 'stretch', backgroundColor:'red'}}
                    source={{uri: 'http://www.itlike.com/template/simple/res/404/img/xiaoliao.png'}}
                />
            </View>
        );
    }
```


##4、ImageBackground组件

- 设置背景图片-ImageBackground组件
```
 render() {
        return (
            <View>
                <ImageBackground
                    source={require('./images/lk.jpg')}
                    style={{width: 400, height: 200}}
                >
                    <Image
                        style={{width: 168, height: 168}}
                        source={{uri: 'http://www.itlike.com/template/simple/res/404/img/xiaoliao.png'}}
                    />
                    <Text style={{color:'#fff'}}>我是小撩同学！</Text>
                </ImageBackground>
            </View>
        );
    }
```



##5、Image组件的小练习

通过一款包包的展示，总结前面所学的View，Text和今天的Image组件，具体效果如下:

![image.png](images/img30.png) 

核心代码：
```
_renderItem() {
        // 1. 组件数组
        let itemArr = [];
        // 2. 遍历数据数组
        for (let i = 0; i < dataArr.length; i++) {
            // 2.1 取出单个数据
            let data = dataArr[i];
            // 2.2 根据数据创建组件装入组件数组
            itemArr.push(
                <View key={i} style={styles.itemViewStyle}>
                    <Image source={{uri: data.icon}} style={{width:80, height:80}}/>
                    <Text>{data.name}</Text>
                </View>
            )
        }
        // 3. 返回数组
        return itemArr;

    }
```





#六、React Native常用的组件-中



## 1、TextInput 组件

文本输入框，相当于OC中的`UITextField`，在用法和属性方面，两者都有很大的借鉴之处：通过键盘将文本输入到应用程序的一个基本的组件。

本组件的属性提供了多种特性的配置，譬如: 自动完成、自动大小写、占位文字，以及多种不同的键盘类型（如纯数字键盘）等等。



- 常用属性

  - `value`:  字符串型 , 文本输入的默认值

  - `onChangeText`:  函数,    监听输入框中输入的值

  - `keyboardType`:   键盘类型, 决定弹出何种软键盘类型，譬如: `numeric`。

    > - **所有平台都可用** ：
    >
    >   `default`  `number-pad` `decimal-pad` `numeric`  `email-address` `phone-pad` 
    >
    > - **仅iOS可用** ：
    >
    >   `ascii-capable`  `numbers-and-punctuation`  `url`  `name-phone-pad`  `twitter`  `web-search` 

  -  `multiline`:   布尔型, 如果值为真，文本输入可以输入多行。默认值为假。

  - `placeholder`: 字符串型, 在文本输入之前字符串将被呈现出来，通常被称为占位文字

  - `placeholderTextColor`:  字符串型, 占位符字符串的文本颜色
  - `autoCapitalize`: 控制TextInput是否要自动将特定字符切换为大写，取值：`characters`所有字符，`words`每一个单词的首字母, `sentences` 每个句子的首字母（默认情况下),`none` 不会自动使用任何东西
  - `clearButtonMode`: enum('never', 'while-editing', 'unless-editing', 'always'), 清除按钮出现在文本视图右侧的时机，仅在单行模式下可用

  - `editable`:  布尔型, 如果值为假，文本是不可编辑的。默认值为真。
  - `onBlur`:  函数,当文本框失去焦点的时候调用此回调函数
  - `onChangeText`: 函数, 当文本输入的文本发生变化时，调用回调函数

  - `onFocus`: 函数, 当输入的文本是聚焦状态时，调用回调函数

  - `returnKeyType`: enum('default', 'go', 'google', 'join', 'next', 'route', 'search', 'send', 'yahoo', 'done', 'emergency-call'), 决定返回键的样式



## 2、Touchable系列组件



###1、高亮触摸  TouchableHighlight

 当手指点击按下的时候，该视图的不透明度会进行降低同时会看到相应的颜色，其实现原理则是在底层新添加了一个View。

>  此外，TouchableHighlight只能进行一层嵌套，不能多层嵌套。

- 常用属性：

  - `activeOpacity`:  number , 设置组件在进行触摸的时候，显示的不透明度(取值在0-1之间)

  - `onHideUnderlay`  function  方法, 当底层被隐藏的时候调用

  - `onShowUnderlay`  function 方法, 当底层显示的时候调用
  - `style`: 可以设置控件的风格演示，该风格演示可以参考View组件的style

  - `underlayColor `: 当触摸或者点击控件的时候显示出的颜色



###2、不透明触摸  TouchableOpacity

该组件封装了响应触摸事件；当点击按下的时候，该组件的透明度会降低。

- 常用属性：

  - `activeOpacity`  number  , 设置当用户触摸的时候，组件的透明度

  - 代码实操

    ```
    render() {
            return (
                <View>
                    <TouchableOpacity
                        style={{width: 100, height: 60, backgroundColor:'red'}}
                        activeOpacity={0.5}
                        onPress={()=>this.activeEvent('点击')}
                        onPressIn={()=>this.activeEvent('按下')}
                        onPressOut={()=>this.activeEvent('抬起')}
                        onLongPress={()=>this.activeEvent('长按')}
                    >
                        <Text>按下</Text>
                    </TouchableOpacity>
    
                    <Text>{this.state.eventTag}</Text>
                </View>
            );
        }
    
        activeEvent(tag){
            this.setState({
                eventTag: tag
            })
        }
    ```

    



## 3、按钮组件

一个简单的跨平台的按钮组件。可以进行一些简单的定制。
```
<Button
  onPress={()=>this.onBtnClick()}
  title="我是一个按钮"
  color="#841584"
/>
```



## 4、案例实操

- 案例主要技术点：充分利用了RN生命周期的钩子函数，实现界面刷新。
  - 利用控件的索引index计算出控件所在的行号和列号
  - 利用列号计算控件的x值
  - 利用行号计算控件的y值

- 案例思路截图

  ![案例思路截图](images/img31.png) 



- 案例效果图

  ![案例效果图](images/img32.png)   

  

- 案例核心代码

```
import React, {Component} from 'react';
import {
    StyleSheet,
    Text,
    View,
    TouchableOpacity,
    Image,
    Dimensions
} from 'react-native';

const {width, height} = Dimensions.get('window');

// 获取本地数据
const dataArr = require('./localData/packageData.json');

export default class LKFlexView extends Component {
    // 构造
    constructor(props) {
        super(props);
        // 初始状态
        this.state = {
            // 购物车数组
            shopArr: []
        };
    }

    render() {
        return (
            <View style={styles.container}>
                {/*上部分*/}
                <View style={styles.topViewStyle}>
                    <TouchableOpacity style={styles.clickBtnStyle} onPress={()=>this._addShop()}>
                        <Text style={styles.btnTextStyle}>添加商品</Text>
                    </TouchableOpacity>
                    <TouchableOpacity style={[styles.clickBtnStyle, {backgroundColor:'red'}]}  onPress={()=>this._removeShop()}>
                        <Text style={styles.btnTextStyle}>删除商品</Text>
                    </TouchableOpacity>
                </View>
                {/*下部分*/}
                <View style={styles.bottomViewStyle}>
                    {this.state.shopArr}
                </View>
            </View >
        );
    }

    /**
     * 添加商品
     */
    _addShop() {
        // 1. 定义相关的常量(总列数, 商品的宽度\高度)
        const cols = 3, shopW = 100, shopH = 120;

        // 2. 取出下标
        let index = this.state.shopArr.length;
        if(index >= 9){
            alert('你已经败家够了!!');
            return;
        }

        // 3. 求出当前盒子所在的行数和列数
        let row = parseInt(index / cols);
        let col = parseInt(index % cols);

        // 4. 求出当前盒子的left和top
        let xSpace = (0.9 * width - cols * shopW) / (cols - 1);
        let ySpace = (0.7 * height - 3 * shopH) / 2;

        let left = col * (shopW + xSpace);
        let top = row * (shopH + ySpace);

        // 5. 创建组件装入数组
        let shopView = (
            <View style={{
                    position:'absolute',
                    left: left,
                    top: top,
                    justifyContent:'center',
                    alignItems:'center'
                  }}
                  key={index}
            >
                <Image source={{uri: dataArr[index].icon}} style={{width:shopW, height:shopW}}/>
                <Text>{dataArr[index].name}</Text>
            </View>
        );

        // 6. 取出购物车数组
        let tempArr = this.state.shopArr;
        tempArr.push(shopView);

        this.setState({
            shopArr: tempArr
        })

    }

    /**
     * 移除商品
     */
    _removeShop() {
        let tempArr = this.state.shopArr;
        if(tempArr.length === 0){
            alert('购物车空空如也~');
            return;
        }

        tempArr.pop();
        this.setState({
            shopArr: tempArr
        })
    }
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: '#999',
    },

    topViewStyle: {
        flexDirection: 'row',
        margin: 30
    },

    clickBtnStyle: {
        width: 120,
        height: 40,
        borderRadius: 10,
        backgroundColor: 'green',

        // 主轴和侧轴都居中
        justifyContent: 'center',
        alignItems: 'center',
        margin: 10
    },

    btnTextStyle: {
        backgroundColor: 'transparent',
        fontSize: 16,
        color: '#fff'
    },

    bottomViewStyle: {
        width: 0.9 * width,
        height: 0.7 * height,
        backgroundColor: '#fff',
        marginLeft: 0.05 * width
    }

});
```





#七、React Native常用的组件-下



## 1、ScrollView组件

从iOS开发的经验来看，`scrollView` 无疑是移动开发中很重要的一个组件，比如后面会学到的`FlatList` 就是继承自它。那么，在开发中比如：焦点图、引导页等地方都有其的影子，那接下来我们一起来搞定它！

> 一个包装了平台的ScrollView（滚动视图）的组件，同时还集成了触摸锁定的“响应者”系统。



### 1、两个要点

- ScrollView必须有一个确定的高度才能正常工作

  > 它实际上所做的就是将一系列不确定高度的子组件装进一个确定高度的容器（通过滚动操作） 
  
  - 通常有两种做法：
    - 第一种： 直接给该ScrollView进行设置高度(不建议)；
    -  第二种：ScrollView中不要加{flex:1}。

- ScrollView内部的其他响应者尚无法阻止ScrollView本身成为响应者



###2、ScrollView中常用的属性

- `contentContainerStyle `
  这些样式会应用到一个内层的内容容器上，所有的子视图都会包裹在内容容器内。

- `horizontal`   bool 
当此属性为true的时候，所有的的子视图会在水平方向上排成一行，而不是默认的在垂直方向上排成一列。默认值为false。

- `onScroll`  function 
在滚动的过程中，每帧最多调用一次此回调函数。调用的频率可以用scrollEventThrottle属性来控制。

- `showsHorizontalScrollIndicator` bool 
当此属性为true的时候，显示一个水平方向的滚动条。

- `showsVerticalScrollIndicator` bool 
当此属性为true的时候，显示一个垂直方向的滚动条。

- `alwaysBounceHorizontal` bool 
当此属性为true时，水平方向即使内容比滚动视图本身还要小，也可以弹性地拉动一截。当horizontal={true}时默认值为true，否则为false。

- `alwaysBounceVertical` bool 
当此属性为true时，垂直方向即使内容比滚动视图本身还要小，也可以弹性地拉动一截。当horizontal={true}时默认值为false，否则为true。

- `contentInset {top: number, left: number, bottom: number, right: number} `
内容范围相对滚动视图边缘的坐标。默认为{0, 0, 0, 0}。

- `contentOffset` 
用来手动设置初始的滚动坐标。默认值为{x: 0, y: 0}。

- `decelerationRate number` 
  一个浮点数，用于决定当用户抬起手指之后，滚动视图减速停下的速度。常见的选项有：

  ```
  Normal: 0.998 (默认值)
  Fast: 0.9
  ```

- `directionalLockEnabled bool `
  当值为真时，滚动视图在拖拽的时候会锁定只有垂直或水平方向可以滚动。默认值为false。

- `maximumZoomScale number `
  允许的最大缩放比例。默认值为1.0。

- `minimumZoomScale number `
  允许的最小缩放比例。默认值为1.0。

(更多请参照官方文档)



###3、ScrollView常用操作

```
import React, {Component} from 'react';
import {View, ScrollView, StyleSheet, Dimensions} from 'react-native';


const screenW = Dimensions.get('window').width;

export default class LKScrollView extends Component {
    constructor(props) {
        super(props);
        this.state = {};
    }

    render() {
        return (
            <ScrollView
                // 决定子视图是横着还是竖着 默认false
                horizontal={true}
                style={styles.container}
                // 是否显示水平滚动条
                showsHorizontalScrollIndicator={false}
                showsVerticalScrollIndicator={false}
                // 是否采用分页
                pagingEnabled={true}
                // 是否可以滚动
                scrollEnabled={true}
            >
                {this._renderItem()}
            </ScrollView>
        );
    }

    _renderItem(){
        // 1. 颜色数组
        let colorArr = ['red', 'green', 'blue', 'yellow', 'purple'];
        // 2. 组件数组
        let itemArr = [];

        // 3. 遍历颜色数组,创建视图装入组件数组
        for(let i=0; i<colorArr.length; i++){
            itemArr.push(
                <View
                    style={{
                        width:screenW,
                        height:300,
                        backgroundColor:colorArr[i]
                    }}
                    key = {i}
                />
            )
        }

        // 4. 返回数组
        return itemArr;
    }
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: '#F5FCFF',
    }
});

```



## 2、RefreshControl组件

这一组件可以用在ScrollView或FlatList内部，为其添加下拉刷新的功能。

当ScrollView处于竖直方向的起点位置（scrollY: 0），此时下拉会触发一个onRefresh事件。



###1、属性方法

- `onRefresh  function`   在视图开始刷新的时候调用
- `refreshing   bool`   视图是否在刷新时显示指示器，也表明当前是否在刷新中
- `colors [ColorPropType] `  android平台适用  进行设置加载进去指示器的颜色，至少设置一种，最多可以设置4种
- `enabled  bool `  android平台适用   用来设置下拉刷新功能是否可用
- `progressBackgroundColor` ColorPropType  设置加载进度指示器的背景颜色
- `size` RefreshLayoutConsts.SIZE.DEFAULT  android平台适用  加载进度指示器的尺寸大小 
- `tintColor` ColorPropType   iOS平台适用  设置加载进度指示器的颜色
- `title string` iOS平台适用  设置加载进度指示器下面的标题文本信息



###2、代码实操

![案例效果图](images/img33.png)  

```
 render() {
        const rows = this.state.rowData.map((row, i)=>(<Row data={row} key={i}/>));
        return (
            <ScrollView
                style={styles.container}
                refreshControl={
                    <RefreshControl
                        refreshing={this.state.isRefreshing}
                        onRefresh={()=>this._onRefresh()}
                        tintColor="#0000ff"
                        title="正在加载数据..."
                        titleColor="#0000ff"
                        colors={['#ff0000', '#00ff00', '#0000ff']}
                        progressBackgroundColor="#ffff00"
                    />
                }
            >
                {rows}
            </ScrollView>
        );

    }
```



## 3、FlatList组件

高性能的简单列表组件，支持下面这些常用的功能：
*   完全跨平台。
*   支持水平布局模式。
*   行组件显示或隐藏时可配置回调事件。
*   支持单独的头部组件。
*   支持单独的尾部组件。
*   支持自定义行间分隔线。
*   支持下拉刷新。
*   支持上拉加载。
*   支持跳转到指定行（ScrollToIndex）。
*   支持多列布局。

>  如果需要分组/类/区（section），请使用`<SectionList>`



###1、简单使用

```
import React, {Component} from 'react';
import {View, FlatList, StyleSheet, Text, TouchableOpacity} from 'react-native';

export default class LKImage extends Component {
    constructor(props) {
        super(props);
        this.state = {
            dataArr: ['第一行数据','第二行数据','第三行数据','第四行数据','第五行数据']
        };
    }

    render() {
        return (
            <FlatList
                data={this.state.dataArr}
                renderItem={({item, index}) => this._renderRow(item, index)}
                keyExtractor={(item, index) => String(index)}
            />
        );
    }

    _renderRow(rowData,index){
        return(
            <TouchableOpacity
                style={{height:44}}
                onPress={()=>alert('点击了第'+ (index+1) + '行')}
            >
                <Text>{rowData}</Text>
            </TouchableOpacity>
        )
    }
}

const styles = StyleSheet.create({});

```



### 2、案例实操-1

![最终效果图](images/img34.png)  



- 核心代码
```
_renderRow(rowData, rowID) {
        return (
            <TouchableOpacity
                style={styles.cellStyle}
                onPress={()=>alert('点击了第' + rowID + '行')}
            >
                {/*左边*/}
                <Image source={{uri: rowData.image}} style={styles.leftImgStyle}/>
                {/*右边*/}
                <View style={styles.rightViewStyle}>
                    <Text
                        numberOfLines={2}
                        style={{fontSize:18}}
                    >
                        {rowData.name}
                    </Text>
                    <Text style={{color:'red'}}>¥{rowData.money}</Text>
                </View>
            </TouchableOpacity>
        )
    }
```



### 3、案例实操-2

![分组案例实操](images/img35.png)  

- 核心代码
```
 _renderRow(rowData, index) {
        console.log(rowData);
        return (
            <View style={styles.cellStyle} key={index}>
                <Image source={{uri: rowData.icon}} style={styles.imgStyle}/>
                <Text>{rowData.name}</Text>
            </View>
        )
    }

    _renderSectionHeader(sectionData) {
        return (
            <View style={styles.sectionHeaderStyle}>
                <Text>{sectionData}</Text>
            </View>
        )
    }
```





#八、React Native Navigation



## 1、安装



### 1、项目集成React Navigation

项目初始化完成后，在项目的根目录下运行命令,集成React Navigation.
```
expo install react-navigation react-native-gesture-handler react-native-reanimated react-native-screens
```


### 2、安装 React Navigation

在已创建的项目的根目录下运行命令安装 React Navigation
```
yarn add react-navigation
yarn add react-native-reanimated 
react-native-gesture-handler 
react-native-screens@^1.0.0-alpha.23
```


###3、iOS和Android中链接对应的库

为了在 iOS 上完成自动链接, 请确保你已经安装了[Cocoapods](https://cocoapods.org/) 然后运行命令
```
cd ios
pod install
cd ..
```
为了完成 ```react-native-screens``` 在 Android 上的安装, 请在```android/app/build.gradle ```中``` dependencies``` 选项中添加下面这两行:
```
implementation 'androidx.appcompat:appcompat:1.1.0-rc01'
implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.1.0-alpha02'
```


## 2、使用



### 1、屏幕切换 (push、pop)

```
this.props.navigation.navigate("组件路由名字")
this.props.navigation.push("组件路由名字")
this.props.navigation.goBack("组件路由名字")
this.props.navigation.popToTop("组件路由名字")
```
navigate: 会判断栈中有没有这个组件, 如果有则回到那个页面,如果没有则创建一个新的组件进行压栈展示;

- `push` : 创建一个新的组件,进行压栈展示;

- `goBack` : 返回上一个页面;

- `popToTop` : 回到首页组件;

  



###2、页面之间传递参数

this.props.navigation.navigate 方法可以传递参数到下一个页面，如下代码所示：

```
<View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
    <Text>首页</Text>
    <Button
      title="跳转到详情页"
      onPress={() =>
        this.props.navigation.navigate('Details', {
          newsId: 'lk001',
          newsName: '撩课1号文件',
          newsTag: '重要'
        })
      }
    />
</View>
```

页面接收参数，如下代码所示：

```
<View
  style={{
      flex: 1,
      alignItems: 'center',
      justifyContent: 'center',
      backgroundColor: 'cyan'
  }}>
    <Text>详情页面</Text>
    <Text>参数1：{JSON.stringify(navigation.getParam('newsId', 'NO-ID'))}</Text>
    <Text>参数2：{JSON.stringify(navigation.getParam('newsName', 'NO-NAME'))}</Text>
    <Text>参数3：{JSON.stringify(navigation.getParam('newsTag', 'NO-TAG'))}</Text>
    <Text>参数4：{JSON.stringify(navigation.state.params)}</Text>
</View>
```



### 3、设置导航标题

navigationOptions 设置导航标题

- 常规设置
```
static navigationOptions = {
      title: '首页',
      headerLeft: () => (
        <Button
          onPress={() => alert('设置')}
          title="设置"
          color="#fff"
        />
      ),
      headerRight: () => (
        <Button
          onPress={() => alert('扫一扫')}
          title="扫一扫"
          color="#fff"
        />
      ),
      headerStyle: {
        backgroundColor: '#f4511e',
      },
      headerTintColor: '#fff',
      headerTitleStyle: {
        fontWeight: 'bold',
        fontSize: 20
      }
    };
```
- 接收上级传递的参数
```
static navigationOptions = ({navigation}) => {
     return {
        title : navigation.getParam("subTitle","撩课学院")
     }
}
```



## 3、Tab navigation

在手机 App 中最常用的导航可能就是基于 Tab 的导航， 这可以是页面底部或标题下方顶部的标签（甚至不要标题）。



###1、 底部Tab切换基本案例

```
import React from 'react';
import { Text, View } from 'react-native';
import { createAppContainer } from 'react-navigation';
import { createBottomTabNavigator } from 'react-navigation-tabs';

class HomeScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center', backgroundColor: 'red' }}>
        <Text>首页</Text>
      </View>
    );
  }
}

class SettingsScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center', backgroundColor: 'green' }}>
        <Text>设置</Text>
      </View>
    );
  }
}

const TabNavigator = createBottomTabNavigator({
  Home: HomeScreen,
  Settings: SettingsScreen,
});

export default createAppContainer(TabNavigator);
```