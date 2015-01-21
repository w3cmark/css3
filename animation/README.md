# 基于 less 构建的 css3 动画库

## LESS动画优点

+ 快速开发css3动画

+ 采用less mixins写法，不会生成冗余css

+ 已加入主流浏览器前缀，保证最大兼容性

+ LESS-Animation 部分mixins支持传参，自定义动画幅度

> （PS：sublime的less2css插件可能不支持编译本库的一些新写法，建议使用官方less编译、考拉、前端构建工具等方式编译。交流群：145423956）

## 使用方法

本less文件主要包含两个功能：LESS-Prefixer和LESS-animation。

+ 下载 _animation.less 文件，git地址：

```
git@git-wz.gz.netease.com:nie-comm/css3-animation.git

```

+ 在主less文件引入_animation.less

```
@import "_animation.less";

```

### LESS-Prefixer

LESS-Prefixer是一组LESS mixins，可以让你在写css3时，去掉书写各个浏览器的前缀，简化代码书写。

+ 如何使用

假如你写css3的transition：

```
div{
  -webkit-transition:all 0.2s ease-out;
  -o-transition:all 0.2s ease-out;
  -ms-transition:all 0.2s ease-out;
  -moz-transition:all 0.2s ease-out;
  transition:all 0.2s ease-out;
}

```

引入 animation.less 后的写法：

```
div{
  .transition(all 0.2s ease-out);
}
```
+ 支持的属性

```
.transition(@arg)
.transition-delay(@delay)
.transition-duration(@duration)
.transition-property(@property)
.transition-timing-function(@function)
.transition-delay(@delay)
.transition-delay(@delay)
```

```
.transform(@arg)
.transform-origin(@args)
.transform-style(@style)
.rotate(@deg)
.scale(@factor)
.translate(@x,@y)
.translate3d(@x,@y,@z)
.translateHardware(@x,@y)
```

```
.animation(@arg)
.animation-delay(@delay)
.animation-direction(@direction)
.animation-duration(@duration)
.animation-fill-mode(@mode)
.animation-iteration-count(@count)
.animation-name(@name)
.animation-play-state(@state)
.animation-timing-function(@function)
```

```
.flex(@arg)
.flexbox()
```

```
.opacity(@number)
```

```
.box-shadow(@arg)
.box-sizing(@arg)
```

```
.border-color(@arg)
.border-image(@arg)
.border-radius(@arg)
```

```
.background-origin(@arg)
.background-clip(@arg)
.background-size(@arg)
```

```
.columns(@args)
.column-count(@count)
.column-gap(@gap)
.column-width(@width)
.column-rule(@args)
```

```
.gradient(@default, @start, @stop)
.linear-gradient-top(@default,@color1,@stop1,@color2,@stop2)
.linear-gradient-top(@default,@color1,@stop1,@color2,@stop2,@color3,@stop3)
.linear-gradient-top(@default,@color1,@stop1,@color2,@stop2,@color3,@stop3,@color4,@stop4)
.linear-gradient-left(@default,@color1,@stop1,@color2,@stop2)
.linear-gradient-left(@default,@color1,@stop1,@color2,@stop2,@color3,@stop3)
.linear-gradient-left(@default,@color1,@stop1,@color2,@stop2,@color3,@stop3,@color4,@stop4)
```

### LESS-animation

#### mixin直接引用

LESS-animation 是一个基于less，集成一些基础动画的库（所包含的动画可以在上面效果预览），直接调用相应的动画mixins即可。动画帧名和mixin名一致，方便调用。

+ 栗子一：引用 bounce 动画，只需在所在元素节点加入 .bounce();

```
.bounce{
  .bounce();
  .animation(bounce 1s ease-in-out);
}
```

+  栗子二：引用 bounceIn 动画，只需在所在元素节点加入 .bounceIn();

```
.box{
  .bounceIn();
  .animation(bounceIn 1s linear infinite);
}
```

#### mixin传参引用

ps：
+ 新增部分传参功能，可以自定义动画幅度参数，实现同类型动画不同幅度；
+ 传参功能不影响原来上面直接引用，参数都可为空，原来的动画幅度已经设为默认值；

具体动画名和参数说明

| 动画名        | 参数说明   |  栗子  |
| --------   | -----:  | :----:  |
| .bounce(@t; @n) | @t：抖动最小幅度（默认值4px）；@n：动画帧名（默认值bounce）| .bounce(5px; bounceA) |
| .pulse(@t; @n) | @t：放大幅度（默认值1.05）；@n：动画帧名（默认值pulse） | .pulse(1.5; pulseA) |
| .shake(@x; @n)  | @x：抖动最小幅度（默认值10px）；@n：动画帧名（默认值shake）| .shake(20px; shakeA) |
| .swing(@d; @n)  | @d：旋转最小角度（默认值5deg）；@n：动画帧名（默认值swing） | .swing(5deg; swingA) |
| .wobble(@d; @n) | @d：摇摆最小幅度（默认值1deg）；@n：动画帧名（默认值wobble）| .wobble(-2deg; wobbleA) |
| .fadeOut(@x; @y; @n)  | @x：x轴移动距离（默认值0）；@y：y轴移动距离（默认值0）；@n：动画帧名（默认值fadeOut）| .fadeOut(-1000px; 0; fadeOutA) |
| .turnInDown(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnInDown）| .turnInDown(700px; turnInDownA) |
| .turnInUp(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnInUp）| .turnInUp(700px; turnInUpA) |
| .turnInLeft(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnInLeft）| .turnInLeft(700px; turnInLeftA) |
| .turnInRight(@p; @n)  | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnInRight） | .turnInRight(700px; turnInRightA) |
| .turnOutDown(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnOutDown） | .turnOutDown(700px; turnOutDownA) |
| .turnOutUp(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnOutUp） | .turnOutUp(700px; turnOutUpA) |
| .turnOutLeft(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnOutLeft）| .turnOutLeft(700px; turnOutLeftA) |
| .turnOutRight(@p; @n) | @p：perspective值，元素距视图的距离（默认值600px）；@n：动画帧名（默认值turnOutRight）| .turnOutRight(700px; turnOutRightA) |

### 更新日志

+ 20150110 增加turn Entrances（出现）和turn Exits（消失）系列动画

+ 20150120 部分新增动画animation的mixin支持传参

## 效果预览

+ http://www.w3cmark.com/animation/



