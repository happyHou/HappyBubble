# HappyBubble
[![GitHub release](https://img.shields.io/badge/Download-DemoApk&AAR-green.svg)](https://github.com/xujiaji/HappyBubble/releases/tag/v1.2.5) [![maven](https://img.shields.io/badge/bintray-1.2.5-brightgreen.svg)](https://bintray.com/xujiaji/maven/happy-bubble/1.2.5)

![bubble](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/img5.png)

气泡布局的形状可以改变，如四角弧度、气泡颜色、箭头大小和阴影。

气泡Dialog可以根据被点击的view的位置来确定自己展示的位置。

[ENGLISH DOC](https://github.com/xujiaji/HappyBubble/blob/master/README-en.md)

[旧文档](https://github.com/xujiaji/HappyBubble/blob/master/README-old.md)

## 更新

|版本|更新描述|图片|
|:-:|:-|:-:|
|1.2.5|修复位置偏移[#36](https://github.com/xujiaji/HappyBubble/issues/36)||
|1.2.4|修复状态栏高度获取[#31](https://github.com/xujiaji/HappyBubble/issues/31)||
|1.2.3|修复气泡内边距问题||
|1.2.2|新特性“设置气泡边框和边框颜色”[#23](https://github.com/xujiaji/HappyBubble/issues/23)|![1.2.2特性](readme/1_2_2.gif)|
|1.2.1|新特性“设置气泡背景”[#25](https://github.com/xujiaji/HappyBubble/issues/25)|![1.2.1特性](readme/1_2_1.jpeg)|
|1.2.0|箭头的上下圆弧都可以自由定制||
|1.1.9|修复初始位置偏移；新增通过x，y坐标显示HappyDialog||
|1.1.8|修复当设置透明背景时，状态栏文字颜色可能变白色问题||
|1.1.7|修复位置问题，修复`autoPosition`无效问题，修复横屏模式问题。[#13](https://github.com/xujiaji/HappyBubble/issues/13)[#11](https://github.com/xujiaji/HappyBubble/issues/11)[#10](https://github.com/xujiaji/HappyBubble/issues/10)||
|1.1.6|[新增方向优先级:#9](https://github.com/xujiaji/HappyBubble/issues/9)||
|1.1.5|[修复:#8](https://github.com/xujiaji/HappyBubble/issues/8)||
|1.1.4|①新增方法`setLayout(int width, int height, int margin)`，width（设置气泡的宽）、height（设置气泡的高）、margin（设置距离屏幕边缘的间距,只有当设置width或height为MATCH_PARENT才有效）。<br>②`autoPosition(true)`方法准备弃用（现在还可以用），使用新方法`autoPosition(Auto)`,如果两个都使用了会直接用`autoPosition(Auto)`。请参考下方“方法参考表”。<br>③感谢[@wolf8088521](https://github.com/wolf8088521)提供建议[#4](https://github.com/xujiaji/HappyBubble/issues/4)||
|1.1.3|①通过重新调用setClickedView可以直接更新当前dialog的所在位置。<br>②新添加setRelativeOffset(int)方法，设置dialog相对与被点击View的偏移（负值：向被点击view的中心偏移；正值：向被点击view的外侧偏移）<br>③[测试页面SetClickedViewTestActivity.java](app/src/main/java/com/xujiaji/happybubbletest/SetClickedViewTestActivity.java)|![1.1.3.gif](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/1.1.3.gif)|
|1.1.2|修复默认值没有适配屏幕||
|1.1.1|修复大小变化后，没有对应变化位置的问题；修复接触顶部偏位问题；||
|1.1.0|①Dialog交互事件传递到Activity达到不在不关闭Dialog的情况下做其他Activity的操作。<br>②添加自动根据被点击View距离屏幕边缘的距离确定Dialog的位置。<br>③新增“autoPosition”和“setThroughEvent”方法，请参考“BubbleDialog方法参考表”|③<br>![1.1.0.gif](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/1.1.0.gif)|
|1.0.3|继续优化了点击在气泡之外才会被dismiss；修复了Dialog周围会有部分点击无法dismiss；||
|1.0.2|修复点击dialog边缘无法取消||

## 哪些app使用了它？

|玩清单|
|-|
|[![Todo](https://pp.myapp.com/ma_icon/0/icon_52755402_1597028430/96)](https://www.wanqingdan.com/)|

## 如何开始？

在你模块中的build.gradle添加上HappyBubble依赖

``` groovy
repositories {
  mavenCentral()
}

dependencies {
  implementation 'com.github.xujiaji:happy-bubble:1.2.5'
}
```

## 如何使用 HappyBubble-BubbleDialog？

> 方法参考表（不全面）
> 具体详细参数请参照案例代码和[attrs.xml](https://github.com/xujiaji/HappyBubble/blob/master/happy-bubble/src/main/res/values/attrs.xml)

|方法名|参数|描述|
|:-|:-:|:-|
|addContentView|View|添加填充在气泡中的视图|
|setClickedView|View|被点击的View（触发Dialog出现的View）|
|setPosition|enum ... <br> `BubbleDialog.Position:`<br>`LEFT`<br>`TOP`<br>`RIGHT`<br>`BOTTOM`|BubbleDialog相对于被点击的view的位置。如果传入多个位置，那么最前面的位置优先级越高|
|setOffsetX|int|如果您对dialog所展示的x轴位置不满，需要调整x轴方向偏移|
|setOffsetY|int|如果您对dialog所展示的y轴位置不满，需要调整y轴方向偏移|
|setBubbleLayout|BubbleLayout|自定义dialog的气泡布局|
|setTransParentBackground|-|背景透明|
|softShowUp|-|当气泡dialog中有EditText时，软键盘弹出会遮挡EditText时，dialog随软键盘上移。|
|show|-|显示|
|autoPosition| enum <br>`Auto:`<br>`AROUND`<br>`UP_AND_DOWN`<br>`LEFT_AND_RIGHT`|自动确定位置功能，显示在被点击View距离屏幕边缘的最大空间。开启后，“setPosition”功能失效。<br>AROUND：被点击View四周；<br>UP_AND_DOWN：被点击View上下显示；<br>LEFT_AND_RIGHT：被点击View左右显示；|
|setThroughEvent|boolean, boolean|第一个参数isThroughEvent设置是否穿透Dialog手势交互。<br>第二个参数cancelable点击空白是否能取消Dialog，只有当"isThroughEvent=false"时才有效|
|setRelativeOffset|int|设置dialog相对与被点击View的偏移（负值：向被点击view的中心偏移；正值：向被点击view的外侧偏移），设置后会直接影响setOffsetX和setOffsetY方法。|
|setLayout|int，int，int|设置气泡的宽高和距离屏幕边缘的距离<br>第一个参数：width（设置气泡的宽）；<br>第二个参数：height（设置气泡的高）；<br>第三个参数：margin（设置距离屏幕边缘的间距,只有当设置width或height为MATCH_PARENT才有效）。<br>宽高单位为px或MATCH_PARENT|

### 最简单的实现

|||
|-|-|
|![exampel1](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/img_example1.png)|![exampel2](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/img_example2.png)|

``` java
new BubbleDialog(this)
        .addContentView(LayoutInflater.from(this).inflate(R.layout.dialog_view3, null))
        .setClickedView(mButton)
        .show();
```

### 向下偏移8dp

![exampel3](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/img_example3.png)

``` java
new BubbleDialog(this)
        .addContentView(LayoutInflater.from(this).inflate(R.layout.dialog_view3, null))
        .setClickedView(mButton4)
        .setPosition(mPosition)
        .setOffsetY(8)
        .show();
```

### 当想要输入框随软键盘上移时

![exampel4](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/gif_example4.gif)

``` java
new BubbleDialog(this)
        .addContentView(LayoutInflater.from(this).inflate(R.layout.dialog_view, null))
        .setClickedView(mButton12)
        .setPosition(mPosition)
        .softShowUp()
        .show();
```

### 自定义 BubbleLayout

![exampel5](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/20190407164631.png)

``` java
BubbleLayout bl = new BubbleLayout(this);
bl.setBubbleColor(Color.YELLOW);
bl.setShadowColor(Color.RED);
bl.setLookLength(Util.dpToPx(this, 18));
bl.setLookWidth(Util.dpToPx(this, 24));
bl.setBubbleRadius(Util.dpToPx(this, 3));
new BubbleDialog(this)
        .addContentView(LayoutInflater.from(this).inflate(R.layout.dialog_view5, null))
        .setClickedView(mButton8)
        .setPosition(mPosition)
        .setBubbleLayout(bl)
        .show();
```

### 自定义 BubbleDialog，可交互的 BubbleDialog

![exampel6](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/gif_example6.gif)
> 1、布局

``` xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="160dp"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <Button
        android:id="@+id/button13"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button1" />

    <Button
        android:id="@+id/button14"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button2" />

    <Button
        android:id="@+id/button15"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button3" />

</LinearLayout>
```

> 2、自定义 BubbleDialog

``` java

/**
 * 自定义可操作性dialog
 * Created by JiajiXu on 17-12-11.
 */

public class CustomOperateDialog extends BubbleDialog implements View.OnClickListener
{
    private ViewHolder mViewHolder;
    private OnClickCustomButtonListener mListener;

    public CustomOperateDialog(Context context)
    {
        super(context);
        setTransParentBackground();
        setPosition(Position.TOP);
        View rootView = LayoutInflater.from(context).inflate(R.layout.dialog_view4, null);
        mViewHolder = new ViewHolder(rootView);
        addContentView(rootView);
        mViewHolder.btn13.setOnClickListener(this);
        mViewHolder.btn14.setOnClickListener(this);
        mViewHolder.btn15.setOnClickListener(this);
    }

    @Override
    public void onClick(View v)
    {
        if (mListener != null)
        {
            mListener.onClick(((Button)v).getText().toString());
        }
    }

    private static class ViewHolder
    {
        Button btn13, btn14, btn15;
        public ViewHolder(View rootView)
        {
            btn13 = rootView.findViewById(R.id.button13);
            btn14 = rootView.findViewById(R.id.button14);
            btn15 = rootView.findViewById(R.id.button15);
        }
    }

    public void setClickListener(OnClickCustomButtonListener l)
    {
        this.mListener = l;
    }

    public interface OnClickCustomButtonListener
    {
        void onClick(String str);
    }
}

```

> 3、显示

``` java
CustomOperateDialog codDialog = new CustomOperateDialog(this)
        .setPosition(mPosition)
        .setClickedView(mButton10);
codDialog.setClickListener(new CustomOperateDialog.OnClickCustomButtonListener()
{
    @Override
    public void onClick(String str)
    {
        mButton10.setText("点击了：" + str);
    }
});
codDialog.show();
```

### 查看关于BappyDialog的使用代码

[TestDialogActivity 代码](app/src/main/java/com/xujiaji/happybubbletest/TestDialogActivity.java)

### 写法建议

根据[@hm](https://juejin.im/user/57bda1ada633bd005d4bc2a9)该朋友在[文章](https://juejin.im/post/5a333f0af265da431523f408)中反馈的多次点击后位置不对的问题，是由于多次对BappyDialog进行了设置导致，所以建议下方写法。(当然如果对重复调用setClickedView()方法设置不同的被点击的控件来更新位置有需要，是需要写在外面的。)

``` java
if(mBubbleDialog == null)
{
    mBubbleDialog = new BubbleDialog(this)
        .addContentView(LayoutInflater.from(this).inflate(R.layout.dialog_view3, null))
        .setClickedView(mButton4)
        .setPosition(mPosition)
        .setOffsetY(8);
}
mBubbleDialog.show();
```

---

## 如何使用 HappyBubble-BubbleLayout？

### 在XML代码中设置属性值

> 属性参照表

|属性|值|描述|
|:-|:-:|:-|
|lookAt|left, top, right, bottom|箭头指向|
|lookLength|dimension|箭头的长度|
|lookPosition|dimension|箭头相对于x或y轴的位置|
|lookWidth|dimension|箭头的宽度|
|bubbleColor|color|气泡的颜色|
|bubbleRadius|dimension|气泡四角的圆弧|
|bubblePadding|dimension|气泡边缘到BubbleLayout边缘的距离|
|shadowRadius|dimension|阴影的扩散大小|
|shadowX|dimension|阴影在x轴方向的偏移|
|shadowY|dimension|阴影在y轴方向的偏移|
|shadowColor|color|阴影的颜色|

> xml 例子

``` xml
    <com.xujiaji.happybubble.BubbleLayout
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/bubbleLayout"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:layout_margin="16dp"
        app:lookAt="left"
        app:lookLength="16dp"
        app:lookPosition="20dp"
        app:lookWidth="16dp" />
```

### 在java代码中定义属性值

> BubbleLayout 通过“set属性名”方法和invalidate方法来更新BubbleLayout。

``` java
mBubbleLayout.setLook(BubbleLayout.Look.LEFT);
```

> 查看更多

[MainActivity 代码](app/src/main/java/com/xujiaji/happybubbletest/MainActivity.java)

![GIF](https://raw.githubusercontent.com/xujiaji/xujiaji.github.io/pictures/github/HappyBubble/en/gif1.gif)

### demo 下载

[![GitHub release](https://img.shields.io/badge/Download-DemoApk&AAR-green.svg)](https://github.com/xujiaji/HappyBubble/releases/tag/v1.2.5)

---

# License

``` text
   Copyright 2016 XuJiaji

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
