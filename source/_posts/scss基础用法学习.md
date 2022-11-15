---
title: scss基础用法学习
author: 作者
tags: 标签
categories: 分类
description: 这是摘要
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-11-01 10:26:49
updated: 2022-11-01 10:26:49
index_img:
banner_img:
headimg:
img:
cover:
---

### SCSS 教程，基础，日常用法

> 本文是以自己的理解起的结构，要看详细的帮助文档，参阅这里：https://sass-lang.com/documentation/

> 文中用到的方法等，在线实例：https://kylebing.cn/test/scss/

延伸阅读：

> 如何在 JetBrains 系列软件中使用 scss : https://blog.csdn.net/KimBing/article/details/100532939
> 关于 scss 的相关配置：https://kylebing.blog.csdn.net/article/details/106015111

### 你需要了解的: less | sass | scss 都是什么
less 和 scss 是两种 css 预编译语言，就是说通过 less 或者 scss 写的代码最终都会被编译成 css 再使用。
其目的是为了更快、更结构的编写 css 文件，都能使用 变量、逻辑运算、判断、颜色方法、数学方法等等。
scss 比 less 语法更规范些，现在主流用 scss。
我也是从 less 开始的，后来转为了 scss。如果你现在在用 less，我建议你改成 scss，相比之下， 总感觉 less 不太严谨，在做大项目的时候会比较吃力。

scss sass 是同一种东西：
只是有以下不同：

> - scss 需要大括号{}和分号;
> - sass 什么都不用直接裸奔，通过缩进来区分代码等级，像 yaml 语言

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020041117195020.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

### 使用 scss 之前你需要准备的
如果需要即时由 scss 生成 css 文件，最好用 JetBrains 系列软件（webStorm phpStorm IDEA等），里面添加对于 scss 的 File Watcher 即可，在每次scss 文件改变的时候，程序都会自动将 scss 编译到 css。

在 vue 中如何使用 scss，请跳转至本文第八条

> 关于如何添加 scss 支持，看这里： https://blog.csdn.net/KimBing/article/details/100532939
> 更详细的配置，看这里：https://blog.csdn.net/KimBing/article/details/106015111

### 看个小例子
写一个 .btn 类并支持 :hover :active 样式

css

```
.btn { }
.btn:hover{ }
.btn:active{ }
```


scss

```
.btn{
// 此处为 btn 初始样式
    &:hover{
        // hover 样式
    }
    &:active{
        // active 样式
    }
}
```


& 都代指父类
上面这个例子中的 & 代指 .btn
可以看出 scss 的结构要比 css 清晰，并且写的也更少。
下面的 scss 会生成上面的 css。
而这还只是皮毛，保证你用过 scss 之后就不再想用 css 写样式了。

#### 一、变量
变量是以 $ 开头的，可以是颜色，长度，数值等等，还可以是带单位的 12px。
带单位的变量使用中跟普通数值变量一样，比如：

```
$padding-normal: 10px;
.container{
    padding: $padding-normal * 2
}
```



```
.container{
	padding: 20px;
}
```

> 像 js 的变量一样，scss 的变量也是有作用域的，也就是说内部声明的变量是无法在外面使用的。

> 如果想让内部的变量在外部可访问，需要在变量值后面添加 !global 声明。

（还可以通过添加 !default 给变量设置默认值，这个在写一个样式库的时候比较实用，避免别人在没有给变量赋值之前使用）

```
$变量名: 变量值
```



```
// Colors
$red:       #CD594B !global;
$yellow:    #F8CE5E;
$green:     #4B9E65;
$yellow:    #5A8DEE;

// Unites
$btn-padding: 4px;
$btn-lineheight: 26px;
```


实际使用中：

scss

```
.btn-success {
    background-color: $green;
    line-height: $btn-lineheight;
    color: #fff;
}
```


生成 css

```
.btn-success {
    background-color: #4B9E65;
    line-height: 26px;
    color: #fff;
}

```


#### 字符串拼接，字符串嵌入
将变量直接嵌入字符串，需要用 #{ 变量 } （类似 ES6 中模板字符串中的 ${ 变量 }）

其实 #{} 中是可以插入任意东西的，这里只用到了插入变量，还可以插入方法等等，高级用法。
具体可以看下面关于 @for 的章节

scss

```
$father-class: "card-list";

.#{$father-class}-item{
	padding: 20px;
}
```


css

```
.card-list-item{
   	padding: 20px;
}
```


#### 二、导入文件 @import
通过 @import 可以把多个文件结合到一起
有了这个功能，就可以根据不同功能模块对 scss 文件进行拆分，使其更结构化。
比如，可以分成：变量类，按钮类，列表类，字体类，排版类等等。

> 拆分成多个文件的时候，scss 环境下，以 _开头命名的文件，不会预编译成 .css 文件
> 而 less 则没有这个忽略 _开头文件的功能

比如，我一个项目的 css 结构是这样的：
以 _ 开头的都是整个项目的 css 的结构部分，像底部按键、表单、按钮、通用方法等。

_variables.scss

```
$bg-btn: #ddd;
$color-btn: #444;
```


btn.scss

```
@import "variables";

.btn{
    display: inline-block;
    padding: 3px 6px;
    background-color: $bg-btn; 
    color: $color-btn;
}

```


生成 css

```
.btn{
    display: inline-block;
    padding: 3px 6px;
    background-color: #ddd; 
    color: #444;
}
```

在一般的大型项目中，如 bootstrap，scss 文件的目录是这样的：
项目所有的负责各部件的 scss 文件被盛放到一个文件夹中，然后通过一个 _mixin.scss 文件来集中引用，在主文件中只需要引入 _minxin.scss 一个文件即可，像下面这样的结构。

```
css/
├── _mixin.scss
├── _reset.scss
├── _utility.scss
├── _variables.scss
├── diary.css
├── diary.css.map
├── diary.scss
└── mixins
    ├── _category.scss
    ├── _detail.scss
    ├── _edit.scss
    ├── _index.scss
    ├── _loading.scss
    ├── _long.scss
    ├── _menu.scss
    ├── _navbar.scss
    ├── _regist.scss
    ├── _toast.scss
    └── _weather.scss
```


_minxin.scss 内容

```
@import "./mixins/detail";
@import "./mixins/edit";
@import "./mixins/index";
@import "./mixins/loading";
@import "./mixins/menu";
@import "./mixins/navbar";
@import "./mixins/regist";
@import "./mixins/toast";
@import "./mixins/long";
@import "./mixins/category";
@import "./mixins/weather";
```


diary.scss 项目主样式文件

```
@import "reset";
@import "utility";
@import "variables";
@import "mixin"; // 只需要引入一个即可

.body-normal{background-color: $bg-light;}
.body-white{background-color: white;}

// FRAME
body{
  position: relative;
  @extend .body-normal;
}
.container{
  padding: 45px 0;
  width: 100%;
}
```

引入 css 文件：
比如有一个 animate.css 的 css 文件需要引入到 scss 文件中，只需要这样

```
@import "animate" 
```


##### 优先级
这里需要注意一下优先级，最后引入的文件拥有比前面引入的同级样式更高的优先级。这个是 css 的基础知识。
比如你需要给你的项目添加一个暗黑样式来适配暗黑样式，一般情况下，这个文件需要在最后引入，除非你的暗黑样式里全用了 !important

#### 三、@mixin，@include

##### 1. @mixin @include
这两个最常用的指令，通过 @mixin 定义一个类或方法，在其它地方通过 @include 引用这个方法或类，跟 js 十分相似。

> 如果是方法，还可以定义默认值，也就是说可以某些时候，可以传部分参数。

直接看例子

scss

```
// @mixin 如果没有调用，不会被渲染

@mixin rounded($conor: 5px){ // 定义 mixin 并设置默认值 5px
  -webkit-border-radius: $conor;
  -moz-border-radius: $conor;
  border-radius: $conor;
}

.btn-rounded{
  @include rounded(); // 这里引用上面的 mixin，默认值 5px
}

.btn-big-rounded{
  @include rounded(10px); // 这里引用上面的 mixin，并设置值 10px
}

```


生成 css

```
.btn-rounded{
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    border-radius: 5px;
}
.btn-big-rounded{
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
}
```



> 扩展 ： mixin 想输入多个参数的时候 参数可以这样写

```
@mixin box-shadow($shadow...){ 
  -webkit-box-shadow: $shadow;
  -moz-box-shadow: $shadow;
  box-shadow: $shadow;
}

.btn{
	@include box-shadow(1px 1px 3px rgba(0,0,0,0.2), 1px -1px 13px rgba(0,0,0,0.2))
}
```


可以看到，这个在写适配不同浏览器专有属性的时候十分方便：比如 border-radius transition transform box-shadow 等等

##### 2. @extend 继承
有些时候，需要写的某个类里，包含另一个类的所有声明。就可以直接拿来使用。

> 如： 警告按钮，包含所有警告颜色类的内容。

scss

```
.danger{
  background-color: #FF3B30;
}
.round{
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
.btn{
  display: inline-block;
  padding: 3px 6px;
}

.btn-danger{
  @extend .danger, .round, .btn;
}
```


css

```
.danger, .btn-danger {
  background-color: #FF3B30;
}
.round, .btn-danger {
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
.btn, .btn-danger {
  display: inline-block;
  padding: 3px 6px;
}
```



> @extend 注意事项：
> 不能继承 @extend .danger.text 这种连续组合的类，应该写为 @extend .danger, .text

#### 四、逻辑运算 @if @else, @each, @for

##### 1. @if @else
没什么说的，就是 if else

>《官方文档：if else》

SCSS

```
@if $name == normal {   // 判断 $name 是否为 'normal'
  color: #333;          // 如果是，内部文字颜色为 #333
  border: 1px solid darken($color, 20%);
} @else {
  color: white;
  border: 1px solid darken($color, 5%);
}
```

##### 2. @each
跟 js 中的 Array.forEach(item => {}) 一样，遍历变量所存在的所有数据。
比如下面的例子，会遍历 $btn-styles 中的三个字符串，这里就用到了上面提到的将变量内容作为字符串内容的 #{变量名}

```
$btn-styles: "normal", "primary", "danger";

@each $type in $btn-styles {
  .btn-#{$type}{
    background-color: white;
  }
}

```

CSS

```
.btn-normal  { background-color: white; }
.btn-primary { background-color: white; }
.btn-danger  { background-color: white; }
```


##### 3. @for
- for 用于基于数字的遍历，有两种使用方法
- for $i from 1 to 10 从 1 到 10，不包含 10
  for $i from 1 through 10 从 1 到 10，包含 10
  举个最常用的例子，生成 pb-1 pb-2… pb-8

SCSS

```
@for $gap from 1 through 8 {
  .pb-#{$gap} {
    padding-bottom: 10px * $gap;
  }
}
```


CSS

```
.pb-1 { padding-bottom: 10px; }
.pb-2 { padding-bottom: 20px; }
.pb-3 { padding-bottom: 30px; }
.pb-4 { padding-bottom: 40px; }
.pb-5 { padding-bottom: 50px; }
.pb-6 { padding-bottom: 60px; }
.pb-7 { padding-bottom: 70px; }
.pb-8 { padding-bottom: 80px; }
```


然后你就可以再进一步，生成 mt mb ml mr pt pb pl pr 这些 css 工具类

SCSS

```
$timer: 10px;
@for $item from 1 through 8 {
  .mt-#{$item}{ margin-top:     $timer * $item !important;}
  .mb-#{$item}{ margin-bottom:  $timer * $item !important;}
  .ml-#{$item}{ margin-left:    $timer * $item !important;}
  .mr-#{$item}{ margin-right:   $timer * $item !important;}
  .m-#{$item} { margin:         $timer * $item !important;}

  .pt-#{$item}{ padding-top:    $timer * $item !important;}
  .pb-#{$item}{ padding-bottom: $timer * $item !important;}
  .pl-#{$item}{ padding-left:   $timer * $item !important;}
  .pr-#{$item}{ padding-right:  $timer * $item !important;}
  .p-#{$item} { padding:        $timer * $item !important;}
}
```


生成 CSS

```
.mt-1 { margin-top     : 10px!important}
.mb-1 { margin-bottom  : 10px!important}
.ml-1 { margin-left    : 10px!important}
.mr-1 { margin-right   : 10px!important}
.m-1  { margin         : 10px!important}
.pt-1 { padding-top    : 10px!important}
.pb-1 { padding-bottom : 10px!important}
.pl-1 { padding-left   : 10px!important}
.pr-1 { padding-right  : 10px!important}
.p-1  { padding        : 10px!important}
.mt-2 { margin-top     : 20px!important}
.mb-2 { margin-bottom  : 20px!important}
.ml-2 { margin-left    : 20px!important}
.mr-2 { margin-right   : 20px!important}
.m-2  { margin         : 20px!important}
.pt-2 { padding-top    : 20px!important}
.pb-2 { padding-bottom : 20px!important}
.pl-2 { padding-left   : 20px!important}
.pr-2 { padding-right  : 20px!important}
.p-2  { padding        : 20px!important}
.mt-3 { margin-top     : 30px!important}
.mb-3 { margin-bottom  : 30px!important}
.ml-3 { margin-left    : 30px!important}
.mr-3 { margin-right   : 30px!important}
.m-3  { margin         : 30px!important}
.pt-3 { padding-top    : 30px!important}
.pb-3 { padding-bottom : 30px!important}
.pl-3 { padding-left   : 30px!important}
.pr-3 { padding-right  : 30px!important}
.p-3  { padding        : 30px!important}
.mt-4 { margin-top     : 40px!important}
.mb-4 { margin-bottom  : 40px!important}
.ml-4 { margin-left    : 40px!important}
.mr-4 { margin-right   : 40px!important}
.m-4  { margin         : 40px!important}
.pt-4 { padding-top    : 40px!important}
.pb-4 { padding-bottom : 40px!important}
.pl-4 { padding-left   : 40px!important}
.pr-4 { padding-right  : 40px!important}
.p-4  { padding        : 40px!important}
.mt-5 { margin-top     : 50px!important}
.mb-5 { margin-bottom  : 50px!important}
.ml-5 { margin-left    : 50px!important}
.mr-5 { margin-right   : 50px!important}
.m-5  { margin         : 50px!important}
.pt-5 { padding-top    : 50px!important}
.pb-5 { padding-bottom : 50px!important}
.pl-5 { padding-left   : 50px!important}
.pr-5 { padding-right  : 50px!important}
.p-5  { padding        : 50px!important}
.mt-6 { margin-top     : 60px!important}
.mb-6 { margin-bottom  : 60px!important}
.ml-6 { margin-left    : 60px!important}
.mr-6 { margin-right   : 60px!important}
.m-6  { margin         : 60px!important}
.pt-6 { padding-top    : 60px!important}
.pb-6 { padding-bottom : 60px!important}
.pl-6 { padding-left   : 60px!important}
.pr-6 { padding-right  : 60px!important}
.p-6  { padding        : 60px!important}
.mt-7 { margin-top     : 70px!important}
.mb-7 { margin-bottom  : 70px!important}
.ml-7 { margin-left    : 70px!important}
.mr-7 { margin-right   : 70px!important}
.m-7  { margin         : 70px!important}
.pt-7 { padding-top    : 70px!important}
.pb-7 { padding-bottom : 70px!important}
.pl-7 { padding-left   : 70px!important}
.pr-7 { padding-right  : 70px!important}
.p-7  { padding        : 70px!important}
.mt-8 { margin-top     : 80px!important}
.mb-8 { margin-bottom  : 80px!important}
.ml-8 { margin-left    : 80px!important}
.mr-8 { margin-right   : 80px!important}
.m-8  { margin         : 80px!important}
.pt-8 { padding-top    : 80px!important}
.pb-8 { padding-bottom : 80px!important}
.pl-8 { padding-left   : 80px!important}
.pr-8 { padding-right  : 80px!important}
.p-8  { padding        : 80px!important}
```


#### 五、常用方法

##### 1. 常用颜色方法
> 更多请看这里
> 详见：https://sass-lang.com/documentation/functions

这些方法都可以直接使用，不需要带前缀 color.

```
lighten         (颜色, 百分比)   // 调亮
darken          (颜色, 百分比)   // 调暗
saturate        (颜色, 百分比)   // 调高饱和度
desaturate      (颜色, 百分比)   // 降低饱和度
transparentize  (颜色, 0.0-1.0) // 透明度，注意这里接收的不是百分比，是 0.0-1.0 的小数值
```


不知道别人，反正我最常用的就是颜色方法了。
我自己常常会做一些自己的小工具，一般会定个主题颜色，然后由这个主题颜色生成页面中需要的其它颜色。这个尤其是在定义暗黑模式颜色的时候比较有用，看个我写的例子，我会以 black 为基准，去生成其它颜色：

```
// DARK VALUES
$dark-bg               : lighten(black, 20%) ;
$dark-bg-dark          : lighten(black, 15%) ;
$dark-bg-selector      : lighten(black, 20%) ;
$dark-bg-nav           : lighten(black, 13%) ;
$dark-border           : lighten(black, 20%) ;
$dark-border-active    : lighten(black, 40%) ;
$dark-menu-border      : #484848             ;
$dark-list-header-bg   : lighten(black, 12%) ;
$dark-list-header-text : lighten(black, 90%) ;
$dark-list-bg          : lighten(black, 15%) ;
$dark-list-bg-active   : lighten(black, 20%) ;
$dark-text-title       : lighten(black, 90%) ;
$dark-text             : lighten(black, 70%) ;
$dark-text-subtitle    : lighten(black, 70%) ;
$dark-scroll-thumb     : lighten(black, 30%) ;
```



> 本文在线例子：https://kylebing.cn/test/scss/

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200411172015955.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

SCSS

```
$green: #4B9E65;

.green-original    { background-color: $green;                      }
.green-lighten     { background-color: lighten($green,20%);         }
.green-darken      { background-color: darken($green,20%);          }
.green-saturate    { background-color: saturate($green,20%);        }
.green-desaturate  { background-color: desaturate($green,20%);      }
.green-transparent { background-color: transparentize($green, 0.2); }
```


CSS

```
.green-original    { background-color: #4B9E65;                 }
.green-lighten     { background-color: #88c79c;                 }
.green-darken      { background-color: #2a5939;                 }
.green-saturate    { background-color: #34b55c;                 }
.green-desaturate  { background-color: #62876e;                 }
.green-transparent { background-color: rgba(75, 158, 101, 0.8); }
```


不过一般工作中不需要这些，因为一般工作中都是有定好的 UI 图为基准的，不需要自己调整颜色，直接取就行，这些颜色方法可能就没太大作用。

##### 2. 高级颜色方法，生成一个渐变的 class 组
颜色还可以这么玩，比如你需要展示用户最后登录的时间，这个时间根据距离现在的长短显示不同颜色，比如最近的显示红色，次之的往蓝色方向变化。
此时，就需要用到高级一点的颜色方法，我也是今天（2022-08-12）才用到，所以加了上来。

所有高级的颜色处理方法，都在 sass:color 模块里，里面的方法有下面这些，这些方法在使用的时候需要带前缀 color.，比如要使用 adjust 方法，就写为

```
color.adjust()
```


###### 重要！！！
在使用颜色模块时，需要在 scss 文件的最上面，添加这段话，不然会出错

```
@use "sass:color"
```



> 官方说明：https://sass-lang.com/documentation/modules/color

![，](https://img-blog.csdnimg.cn/5c08cce5923a40eeaefd9f3d708b214c.png)

说一下 adjust、change 方法，能看到，这两个方法接收的参数是一样的，其实就是一样的

```
color.change($源颜色, $hue: hue值)
// 它其实可以改变 红蓝绿通道的数值、亮度、透明度等，但这里我们只用 $hue，就是改变颜色的色调

// 颜色操作
@for $item from 0 through 12 {
  .text-level-#{$item}{
    margin-right: 15px;
    font-weight: bold;
    color: color.change($red, $hue: -30deg * $item) !important;
  }
}
```



生成

css

![在这里插入图片描述](https://img-blog.csdnimg.cn/38cc8c508b43461fabb3f242917c58d2.png)

例子页面中

![在这里插入图片描述](https://img-blog.csdnimg.cn/c9e136c477b645b69364e9cda4b2de4b.png)

我实际的应用页面中是这样的

![在这里插入图片描述](https://img-blog.csdnimg.cn/c77ee0ef0258411d8c2f0283a5b5ff09.png)



#### 六、其它

##### 1. 方法 @function
方法以 @function 开头，以 @return 结尾，也就是说，方法的定义，必须要有返回值

> 详见：https://sass-lang.com/documentation/at-rules/function

方法的使用跟上面讲到的颜色方法是一样的。
方向在定义完成后，可以直接写方法名调用，不需要添加前面的@符号，如：

知道文档的 HTML 根字体大小是 14px，目前需要进行动态尺寸适配，知道其它地方的字体在像素单位上的大小，比如 .font-size-normal 的字体大小是 16px，如何快速方便的计算出 (16/14)rem 这样的尺寸呢？对，此时就用到了 Function，非常方便。

> rem 单位是以文档根元素(也就是<html></html>)字体大小为基准的单位，设置成 rem为单位的尺寸后，修改 <html>的字体大小，文档内的以 rem 为单位的尺寸都会跟着变化。
> 这是在适配方面很重要的知识点

SCSS

```
// 比较
$root: 14;

// 定义一个方法用于换算尺寸的方法
// #{} 是输出字符串的，上面有讲
@function size($size) {
  @return #{$size/$root}rem
}

.font-size-normal {
  font-size: size(16); 
}
```


得出来的CSS是这样的

```
.font-size-normal {
  font-size: 1.1428571429rem;
}
```


##### 2. 除以 ÷ 不使用 / 而用 math.div()
SCSS 中为了避免跟 css 的一些字体样式混淆（比如 12/24px），除法不用 / 而是用 math.div() 比如 100 / 5 就是。
不过你需要在 scss 文件的开头，添加 @use "sass:math";

```
@use "sass:math";

.gutter{
	padding: math.div(100px, 5);
}
```


##### 3. 调试方法 @error @warn @debug
像 js 的 console.log console.error一样，用于输出提示信息

- @debug : 普通输出
- @warn : 警告输出
- @error : 错误输出

##### 4. 注释
```
/*  多行注释
        可以多行
        在非压缩模式下，这种注释会被输出到 css 中
*/

// 单行注释
// 这种注释不会输出到 css 中
```



##### 5. 特殊方法
CSS 本身自带一些方法，大多数方法都能与 SCSS 方法和平共存，但有些会产生冲突，如url()

如果 url() 传入的参数是有效的带引号的 url，sass 不会处理它，但还可以往其中插入变量，如果不是有效的带引号的 url，带有方法或变量的，sass 就把它当成正常的方法识别。如：

```
$bg-path: "./pics"

.card-bg{
    background: url("#{$bg-path}/card-bg.png") center center;
}

// 或
.card-bg{
    background: url($bg-path+"/card-bg.png") center center;
}
```


都会输出为

```
.card-bg{
    background: url("./pics/card-bg.png") center center;
}
```


##### 6. vue scss 如何加载字体 font
以 ~@/ 开头就可以了

以相对路径 ../ 的方式是不可以的

```
@font-face {
  font-family: "Impact";
  src: url("~@/assets/font/ImpactPureNumber.ttf");
}

@font-face {
  font-family: "LLPixel";
  src: url("~@/assets/font/LLPixel_only_Letter.ttf");
}
```


#### 七、写个例子 .btn
学会上面的所有内容，我们来写一个例子。
比如，你需要写一个按钮库 .btn-success, .btn-danger, .btn-normal, .btn-warning，如果单个定义的话，会很麻烦，现在有了 SCSS，就可以很方便的实现了。

完成后，效果是这样的:

> 本文在线例子：https://kylebing.cn/test/scss/

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200411172026785.gif)

> 可以 Chrome 打开上面的链接，检查元素，调出调试窗口，点 resources 就可以看到具体的 scss 代码了，还是语法高亮的

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200426175229337.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

SCSS

```
// 定义基础颜色
// 一般在项目中会写在 _variables.scss 文件中
$green          : #4CD964;
$syan           : #5AC8FA;
$blue           : #007AFF;
$purple         : #5856D6;
$magenta        : #FF2D70;
$red            : #FF3B30;
$orange         : #FF9500;
$yellow         : #FFCC00;
$gray           : #8E8E93;

// 定义需要实现的按钮名和颜色，键值对
$btn-types: (
        "normal": white,
        "primary": $blue,
        "success": $green,
        "danger": $red,
        "warning": $orange,
        "second": $gray,
);

/****************************
把一些常用的需要多平台适配的（-webkit-）做成 mixin 方便调用，写的时候代码也简洁
像这种还有 box-shadow transform transition animation 等等
一般在项目中都单独定义成一个文件 _utility.scss，直接引用使用，也方便。
这里只是提一下，可能会对你有所启发
*/

@mixin border-radius($value){
  -webkit-border-radius: $value;
  -moz-border-radius: $value;
  border-radius: $value;
}

/****************************
这里定义最常用的通用方法，比如 .link .btn .block .hidden
一般保存为 _normalize.scss 文件
*/

.unselectable{
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

// .btn 里只放 button 最基础的行为和动作
// 下面循环中的 .btn-xxxx 只处理按钮的颜色变化，这样明了
.btn {
  padding: 6px 10px;
  text-align: center;
  font-size: 1rem;
  cursor: pointer;
  margin-right: 5px;
  @extend .unselectable; // 引用其它类的内容作为自己的内容，也就是扩展
  @include border-radius(5px); // 调用 mixin
  &:active{
    transform: translateY(2px);
  }
}

@each $name, $color in $btn-types {
  .btn-#{$name} {
    @if $name == normal {   // 判断 button 名 是否为 'normal'
      color: #333;          // 如果是，内部文字颜色为 #333
      border: 1px solid darken($color, 20%);
    } @else {
      color: white;
      border: 1px solid darken($color, 5%);
    }
    background-color: $color;
    &:hover{
      background-color: lighten($color, 5%);
    }
    &:active{
      border-color: transparent;
      background-color: darken($color, 15%); // 点击的时候按钮背景颜色深 15%
    }
  }
}
```


上面的 scss 输出为下面的内容，有没有很强大

```
/* buttons */
.unselectable, .btn {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none; }

.btn {
  padding: 6px 10px;
  text-align: center;
  font-size: 1rem;
  cursor: pointer;
  margin-right: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px; }
  .btn:active {
    transform: translateY(2px); }

.btn-normal {
  color: #333;
  border: 1px solid #cccccc;
  background-color: white; }
  .btn-normal:hover {
    background-color: white; }
  .btn-normal:active {
    border-color: transparent;
    background-color: #d9d9d9; }

.btn-primary {
  color: white;
  border: 1px solid #006ee6;
  background-color: #007AFF; }
  .btn-primary:hover {
    background-color: #1a87ff; }
  .btn-primary:active {
    border-color: transparent;
    background-color: #0055b3; }

.btn-success {
  color: white;
  border: 1px solid #37d552;
  background-color: #4CD964; }
  .btn-success:hover {
    background-color: #61dd76; }
  .btn-success:active {
    border-color: transparent;
    background-color: #26b33e; }

.btn-danger {
  color: white;
  border: 1px solid #ff2317;
  background-color: #FF3B30; }
  .btn-danger:hover {
    background-color: #ff534a; }
  .btn-danger:active {
    border-color: transparent;
    background-color: #e30c00; }

.btn-warning {
  color: white;
  border: 1px solid #e68600;
  background-color: #FF9500; }
  .btn-warning:hover {
    background-color: #ffa01a; }
  .btn-warning:active {
    border-color: transparent;
    background-color: #b36800; }

.btn-second {
  color: white;
  border: 1px solid #818187;
  background-color: #8E8E93; }
  .btn-second:hover {
    background-color: #9b9b9f; }
  .btn-second:active {
    border-color: transparent;
    background-color: #68686d; }
```



> 其实这里可以使用渐变优化按钮颜色的，你可以考虑如何实现哟，加油。
> 给个提示: 基础颜色不需要变，只需要用颜色方法对基础颜色进行微调即可产出渐变需要的颜色

如果你想更深入的了解一些东西，可以看个我一直在完善中的项目《标题日记》：

> 在线页面
> https://kylebing.cn/diary/

> 源码
> https://github.com/KyleBing/diary-vue/tree/master/src/assets/scss

![在这里插入图片描述](https://img-blog.csdnimg.cn/2e885c027499465ba947f2b8ce5a85ff.png)

#### 八、Vue 中使用 scss
在 vue 中使用 scss 需要安装两个组件： sass 和 sass-loader

sass 就是用来解析 sass/scss 文件内容的，主流的有两个可选项

- sass
- node-sass
  任选其一即可，但 node-sass 在安装过程中经常出现错误，什么 npm-gpy 错误什么的，我也懒得去看具体是什么原因，烦了就改成 sass 了

>  vue node-sass 安装失败，如何解决，使用 sass 替换

```
"devDependencies": {
    // 其它组件...
    

    "sass": "^1.26.11",
    "sass-loader": "^10.0.2"

},

```


然后在 vue 文件中：

<style lang="scss" scoped >
// scoped 表示在该文件中声明的样式，只在当前文件中有效，不会影响外面样式。
// 具体去查阅 Vue 相关文档
</style>



#### 九、学习 scss 最好的例子
> Bootstrap v5 - scss 语言: https://github.com/twbs/bootstrap

就是去看 bootstrap v5 的样式源码，bootstrap v4 v5 都是用 scss 写的
下载 bootstrap 的 scss 源码，看里面怎么写的，进步很快的。

> 如果想学 less 可以看这篇 less基础用法（SegmentFault | CSDN）， bootstrap v3 就是用 less 写的。
>
> - Bootstrap v3 - less 语言: https://github.com/twbs/bootstrap/tree/v3-dev

#### 十、不太重要的东西
##### 语法概览
**通用**

- 变量声明， $var: value

- 控制声明，@if @each

- @error，@warn，@debug

**CSS**

- 样式，h1 { ... }
- 样式@ @media @font-face
- @at-root
**顶级**

- 导入 @import
- 混合 @mixin
- 方法定义 @function
**表达式**

- 数字 12 100px
- 字符串 Helvetina Neue bold
- 颜色 #ffffff blue
- 布尔值 true false
- null
- 属性值组 border: 1px solid #ccc
- Maps (“background”: red, “foreground”: pink)
**运算符**

- == !=
- +  - * / %
- +  < <= >=
- +  and or not
- + - / 连接字符
- (  )

- ![image-20221101105525333](C:\Users\10258\AppData\Roaming\Typora\typora-user-images\image-20221101105525333.png)**其它**

- 变量 $var
- 方法调用 nth($list,1) var(--main-bg-color)
- 特殊方法 calc(1px + 100%) url(http://myapp.com/assets/logo.png)
- 父选择器 &
- !important
