

[TOC]

# 读View源码总结

从今天开始，尝试阅读`View`的源码，也不知道能不能坚持下来，开始吧！加油~

## View简介

`View`是所有视图控件的**基类**，占据屏幕的一个矩形区域，负责绘制，处理与用户的交互。**子类** `ViewGroup`是存放`View`的容器。

一个手机App的界面就是由一个或多个`View`组成的，所有在**窗口**（Window） 的`View`们被排列在一棵树上，可以通过Java代码或者写布局xml文件的方式“画”界面。其实制作界面真的就像是在“画画”一样，把我们想在手机屏幕上展现出来，只不过我们这幅画不是静态的，经常还要跟用户交互。

对于视图`View`，程序猿们通常的操作包括**设置属性**、**设置焦点**、**设置监听器**、**设置可见性**。 这些比较具体的内容我还没由读到，读到的时候会详细的写下来，能力一般～～。

### 解释解释自定义View需要覆盖的方法

**创建**：

1. **构造方法**：不用解释了吧，还不知道，还是先放放Android，先学好Java，也不迟。
2. `onFinishInflate`：布局xml文件被加载完毕后回调的函数。

布局（Layout）：

1. onMeasure（）：明确View的尺寸
2. onLayout（）：把View摆在屏幕上的位置
3. onSizeChanged：View的尺寸变化时回调

绘图（Draw）：

1. onDraw（）：往View上绘制图案

执行事件（Event processing）

1. onKeyDown：按下硬件时回调，现在手机实体按键越来越少，就是下开机键、音量键等等。
2. onKeyUp：按键弹起时回调，相信用到这个方法的时候不多。
3. onTrackballEvent：Trackball翻译成**轨迹球**，都不知道是个球？？谁来解释一下🍷
4. onTouchEvent：触摸屏幕时的回调，这个是自定义View中比较常用的方法。

焦点（Focus）

1. onFocusChanged：获取焦点或失去焦点时回调，目前还不知道焦点是干什么用的。
2. onWindowFocusChanged：Window获取或失去焦点是回调

依附（Attaching）

1. onAttachToWindow：View依附于Window上时回调
2. onDetachedFromWindow：View不在Window上时回调
3. onWindowVisibilityChanged：Window的可见性改变时回调

### 位置（Position）

在手机屏幕上，你看到的View不管是圆形，三角形还是什么形，其实他们多是长方形，不信可以打开**开发者模式－显示布局边界**看看，这是我最经常用的选项，临摹别人的好界面很有用。

介绍几个容易混淆的有关位置的方法：

1. getLeft：这个View的左边界与直接父View的左边界的距离。
2. getTop：与getLeft类似
3. getWidth：View的宽度
4. getHeight：View的高度
5. getRight：getLeft（）与getWidth（）之和。
6. getBottom：getTop（）与get Height（）之和。

### 尺寸、padding（真不知该怎么翻）、间距（margin）

1. getMeasuredWidth()与 getMeasuredHeight()：这两个方法与上面介绍的Layout（布局）的onMeasure有关，只有当View被裁剪完，View的真正大小才能被确定。
2. padding：View的内容与View的边界的距离
3. margin：View的边界与直接父View边界的距离，左边界与左边界比较，以此类推。

### 布局（Layout）

布局有两个过程—`measure` 和`layout` 。measure的过程中，会对View树上下遍历，来确定或者计算得到View的长和宽，并将长和宽保存下来。然后执行第二步layout，同样需要上下的遍历，通过计算最终将View摆放好，到底如何计算，接下来我会对`measure(int,int)`和`layout(int,int,int,int)`代码分析。

measure方法执行完毕后，View自己以及它的孩子View的长宽也就被确定了，`getMeasureWidth`和`getMeasureHeight`就可以返回View的长宽了，这也是为什么在`Activity.onCreate`中调用上面这两个方法，返回的都是0的原因。裁剪的过程中，父View可能会不止一次的调用measure方法。

有关`View.MeasureSpec`,与View有关测量的属性对照表

| MeasureSpec常量 | 对应的属性               | 解释                                   |
| ------------- | ------------------- | ------------------------------------ |
| EXACTLY       | MATCH_PARENT, 明确的尺寸 | View给出了明确                            |
| AT_MOST       | WRAP_CONTENT        | 父View一般会尽量满足子View的需求，但不能超过父View提供的尺寸 |
| UNSPECIFIED   |                     | 不会                                   |



### 设置属性

### 设置焦点

### 设置可见性