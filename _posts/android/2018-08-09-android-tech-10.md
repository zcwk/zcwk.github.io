---
layout: post
title: Android-自动化测试
category: Android
tags: Android 自动化测试
keywords: Android
---


## 1、Monkey
    是Android SDK自带的测试工具，在测试过程中会向系统发送伪随机的用户事件流，如按键输入、触摸屏输入、手势输入等)，实现对正在开发的应用程序进行压力测试，也有日志输出。实际上该工具只能做程序做一些压力测试，由于测试事件和数据都是随机的，不能自定义，所以有很大的局限性。

## 2、MonkeyRunner
    也是Android SDK提供的测试工具。严格意义上来说MonkeyRunner其实是一个Api工具包，比Monkey强大，可以编写测试脚本来自定义数据、事件。缺点是脚本用Python来写，对测试人员来说要求较高，有比较大的学习成本。

## 3、Instrumentation
    是早期Google提供的Android自动化测试工具类，虽然在那时候JUnit也可以对Android进行测试，但是Instrumentation允许你对应用程序做更为复杂的测试，甚至是框架层面的。通过Instrumentation你可以模拟按键按下、抬起、屏幕点击、滚动等事件。Instrumentation是通过将主程序和测试程序运行在同一个进程来实现这些功能，你可以把Instrumentation看成一个类似Activity或者Service并且不带界面的组件，在程序运行期间监控你的主程序。缺点是对测试人员来说编写代码能力要求较高，需要对Android相关知识有一定了解，还需要配置AndroidManifest.xml文件，不能跨多个App。

## 4、UiAutomator
    也是Android提供的自动化测试框架，基本上支持所有的Android事件操作，对比Instrumentation它不需要测试人员了解代码实现细节（可以用UiAutomatorviewer抓去App页面上的控件属性而不看源码）。基于Java，测试代码结构简单、编写容易、学习成本，一次编译，所有设备或模拟器都能运行测试，能跨App（比如：很多App有选择相册、打开相机拍照，这就是跨App测试）。缺点是只支持SDK 16（Android 4.1）及以上，不支持Hybird App、WebApp。

5、Espresso
    是Google的开源自动化测试框架。相对于Robotium和UIAutomator，它的特点是规模更小、更简洁，API更加精确，编写测试代码简单，容易快速上手。因为是基于Instrumentation的，所以不能跨App。配合Android Studio来编写测试的简单例子6、Selendroid：也是基于Instrumentation的测试框架，可以测试Native App、Hybird App、Web App，但是网上资料较少，社区活跃度也不大。

## 7、Robotium
    也是基于Instrumentation的测试框架，目前国内外用的比较多，资料比较多，社区也比较活跃。缺点是对测试人员来说要有一定的Java基础，了解Android基本组件，不能跨App。

8、Athrun
    是淘宝出的一个移动测试框架/平台，同时支持iOS和Android。Android部分也是基于Instrumentation，在Android原有的ActivityInstrumentationTestCase2类基础上进行了扩展，提供一整套面向对象的API。这里有详细介绍。

9、Appium
    是最近比较热门的框架，社区也很活跃。这个框架应该是是功能最强大的，
    它的优点：开源；支持Native App、Hybird App、Web App；支持Android、iOS、Firefox OS；Server也是跨平台的，你可以使用Mac OS X、Windows或者Linux；
    它的哲理是：用Appium自动化测试不需要重新编译App；支持很多语言来编写测试脚本，Java、Javascript、PHP、Python、C#、Ruby等主流语言；不需要为了自动化测试来重造轮子，因为扩展了WebDriver。（WebDriver是测试WebApps的一种简单、快速的自动化测试框架，所以有Web自动化测试经验的测试人员可以直接上手）；移动端自动化测试应该是开源的；
    它的设计理念：Client/Server架构，运行的时候Server端会监听Client端发过来的命令，翻译这些命令发送给移动设备或模拟器，然后移动设备或模拟器做出响应的反应。正是因为这种架构，所以Client可以使用Appium client libraries多种语言的测试脚本，而且Server端完全可以部署在服务器上，甚至云服务器。Session，每个Client连接到Server以后都会有一个Session ID，而且Client发送命令到Server端都需要这个Session ID，因为这个seesion id代表了你所打开的浏览器或者是移动设备的模拟器。所以你甚至可以打开N个Session，同时测试不同的设备或模拟器。Desired Capabilities，其实就是一个键值对，设置一些测试的相关信息来告诉Server端，我们需要测试iOS、还是Android，或者换是WebApp等信息。Appium Server是Node.js写的，所以可以直接用NPM来进行安装。Appium Clients，Mac OS和Win下提供GUI，不需要装Node.js，方便测试人员操作。相关限制：如果你在Windows使用Appium，你没法使用预编译专用于OS X的.app文件，因为Appium依赖OS X专用的库来支持iOS测试，所以在Windows平台你不能测试iOS Apps。这意味着你只能通过在Mac上来运行iOS测试。总结：在iOS部分是封装了UIAutomation；Android 4.2以上是用UiAutomator，Android 2.3 ~ 4.1用的是 Instrumentation，也就说Appium同时封装了UiAutomator和Instrumentation。所以Appium拥有了以上几大框架的所有优点：跨App，支持Native App、Hybird App、Web App，还支持N种语言来编写你的测试脚本。


