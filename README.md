#  AnchorTask
锚点任务，可以用来解决多线程加载任务依赖的问题。实现原理是使用有向无环图，常见的，比如 Android 启动优化，通常会进行多线程异步加载

> 我的 CSDN 博客:https://blog.csdn.net/gdutxiaoxu <br>
> 我的掘金：https://juejin.im/user/2207475076966584  <br>
> github: https://github.com/gdutxiaoxu/  <br>
> **微信公众号：程序员徐公(stormjun94)**  <br>
> 知乎：https://www.zhihu.com/people/xujun94  <br>




## 基本使用

第一步：在 moulde build.gradle 配置远程依赖


```
implementation 'com.xj.android:anchortask:1.0.0'
```

最新的版本号可以看这里 [lastedt version](https://dl.bintray.com/xujun94/maven/com/xj/android/anchortask/)

## 具体使用文档

### 有向无环图的实现

[Android 启动优化（一） - 有向无环图
](https://juejin.cn/post/6926794003794903048)

[Android 启动优化（二） - 拓扑排序的原理以及解题思路](https://juejin.cn/post/6930805971673415694)


### 0.1.0 版本

0.1.0 版本使用说明见这里 [AnchorTask 0.1.0 版本使用说明](https://github.com/gdutxiaoxu/AnchorTask/wiki/AnchorTask-0.1.0-%E7%89%88%E6%9C%AC%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)， 0.1.0 版本实现借鉴了 [android-startup](https://github.com/idisfkj/android-startup)，[AppStartFaster](https://github.com/NoEndToLF/AppStartFaster)

[AnchorTask 0.1.0 原理
](https://github.com/gdutxiaoxu/AnchorTask/wiki/AnchorTask-0.1.0-%E5%8E%9F%E7%90%86)

###  1.0.0 版本

[AnchorTask 1.0.0 版本使用说明](https://github.com/gdutxiaoxu/AnchorTask/wiki/AnchorTask-1.0.0-%E7%89%88%E6%9C%AC%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)，参考了阿里 [alpha](https://github.com/alibaba/alpha)

[AnchorTask-1.0.0-原理说明](https://github.com/gdutxiaoxu/AnchorTask/wiki/AnchorTask-1.0.0-%E5%8E%9F%E7%90%86%E8%AF%B4%E6%98%8E)

### 两个版本之间区别


1. 之前的 0.1.0 版本 配置前置依赖任务，是通过 `AnchorTask getDependsTaskList` 的方式，这种方式不太直观，1.0.0 放弃了这种方式，参考阿里 `Alpha` 的方式，通过 `addTask(TASK_NAME_THREE).afterTask(TASK_NAME_ZERO, TASK_NAME_ONE)`
2. 1.0.0 版本新增了 Project 类，并增加 `OnProjectExecuteListener` 监听
3. 1.0.0 版本新增 `OnGetMonitorRecordCallback` 监听，方便统计各个任务的耗时


**如果觉得对你有所帮助的，可以关注我的微信公众号，程序员徐公。主要更新 Android 技术，算法，职场相关的。**

![](https://gitee.com/gdutxiaoxu/blog-picture/raw/master/21/02/%E7%A8%8B%E5%BA%8F%E5%91%98%E5%BE%90%E5%85%AC%20(1).png)

## 特别鸣谢

在实现这个开源框架的时候，借鉴了以下开源框架的思想。AppStartFaster 主要是通过 ClassName 找到相应的 Task，而阿里 alpha 是通过 taskName 找到相应的 Task，并且需要指定 ITaskCreator。两种方式各有优缺点，没有优劣之说，具体看使用场景。

[android-startup](https://github.com/idisfkj/android-startup)

[alpha](https://github.com/alibaba/alpha)

[AppStartFaster](https://github.com/NoEndToLF/AppStartFaster)

