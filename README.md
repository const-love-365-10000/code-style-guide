>声明，本文《代码风格指南》整合于网上知名团队代码规范和数位前端大牛的风格指南(本文底部附上链接)。取其精华，去其糟粕，立志于写成一篇代码规范、书写方便、且为大多数人接受的代码风格指南。

# 命名规则

## 常用的命名方法

- 小驼峰式(camelCase)，即第一个首字母小写，其余首字母大写，如 `myBlog`
- 大驼峰式(PascalCase)，即所有首字母大写，如`MyBlog`
- 短横线连接式(kebab-case) ，即所有字母小写，用短横线分隔，如`my-blog`
- 下划线连接式(snake_case)，即所有字母小写，用下划线分隔，如`my_blog`

## 项目命名

项目命名采用小写方式+下划线分隔的方式，例如

`my_blog`

## 目录命名

采用小写方式+下划线分隔的方式，并且，如果有复数结构用复数形式，例如

​	`images`

​	`styles`

<!-- more-->

## JS文件命名

采用小写方式+下划线分隔的方式

`my_model.js`

## CSS, SCSS文件命名

采用小写方式+下划线分隔的方式

`account_model.js`

## HTML文件命名

采用小写方式+下划线分隔的方式

`error_report.html`

## 特殊文件命名

有些文件为了醒目，能够让人一眼找到，采用全大写的方式命名，例如

`README.md`

## 变量命名规则

- 命名方式：小驼峰式
- 命名规范： 类型(小写首字母)+对象描述或属性的方式

|   类型   | 小写字母 |
| :------: | :------: |
|  array   |    a     |
| boolean  |    b     |
| function |    fn    |
|   int    |    i     |
|  object  |    o     |
| regular  |    r     |
|  string  |    s     |

```js
let oMenu = document.getElementById("menu");
```

这样看上起就一目了然了。

**如果没有明确的类型，则让名词当前缀。**

## 函数命名规则

- 命名方法：普通函数使用小驼峰命名，构造函数使用大驼峰命名法
- 命名规则： 前缀为动词

| 动词 |              含义               |                   返回值                   |
| :--: | :-----------------------------: | :----------------------------------------: |
| can  | 判断是否可执行某个动作 ( 权限 ) |        true-可执行，false-不可执行         |
| has  |       判断是否含有某个值        |       true-含有此值，false-不含此值        |
|  is  |        判断是否为某个值         |       true-为某个值，false-不为某值        |
| get  |           获取某个值            |            函数返回一个非布尔值            |
| set  |           设置某个值            | 无返回值、返回是否设置成功或者返回链式对象 |

```js
// 设置某个值
function setMenuName(){
	menuName = "123"
}
```

## 常量命名

- 命名方法： 全部大写
- 命名规范： 使用大写字母和下划线来组合命名，下划线用以分割单词。

```JS
const 	MY_COUNT = 1000
```

## 类的成员命名

- 公共属性和方法 : 同变量命名方式
- 私有属性和方法 : 前缀为下划线(_)后面跟公共属性和方法一样的命名方式

推荐：

```js
function Student(name) {
    var _name = name; // 私有成员
 
    // 公共方法
    this.getName = function () {
        return _name;
    }
 
    // 公共方式
    this.setName = function (value) {
        _name = value;
    }
}
var st = new Student('tom');
st.setName('jerry');
console.log(st.getName()); // => jerry：输出_name私有变量的值
```



# 注释规范

## 单行注释

- 双斜杠(//)后空一格
- 代码后注释时还需要在双斜杠前空一格

```js
// 调用一个方法，xxx
getTitle()
let maxCount = 10; // 设置最大量
```

## 多行注释

- 三行内的注释请使用单行注释，超过三行的注释使用多行注释
- 多行注释尽量第一行和最后一行都留空
- 每行第一个字到*都空一格

```js
/*
* 函数说明
* @...
* ...
*/
```

## 函数方法注释

常用注释关键字：

| 注释名   | 语法                                      | 含义                      | 示例                                         |
| -------- | ----------------------------------------- | ------------------------- | -------------------------------------------- |
| @param   | @param 参数名 {参数类型} 描述信息         | 描述参数的信息            | @param name {String} 传入名称                |
| @return  | @return {返回类型} 描述信息               | 描述返回值的信息          | @return {Boolean} true:可执行;false:不可执行 |
| @author  | @author 作者信息 [附属信息：如邮箱、日期] | 描述此函数作者的信息      | @author 张三 2015/07/21                      |
| @version | @version XX.XX.XX                         | 描述此函数的版本号        | @version 1.0.3                               |
| @example | @example 示例代码                         | @example setTitle('测试') |                                              |

```js
/**
 * @param item {object} input元素对象
 * @return void
 * @author xx 2020.8.24
 * @version 1.0.0.1
 * @example setInputValue('titleInput')
 */
function setInputValue(item) {
    item.value = "";
}
```

实际开发中，根据需要来选择注释关键字，一般来说,至少写上`@param` 和 `@return` 。

## 需要添加注释的地方

代码注释在一个项目的后期维护中显的尤为重要，所以我们要为每一个被复用的组件编写组件使用说明，为组件中每一个方法编写方法说明。

以下情况，务必添加注释:

```markdown
1. 公共组件使用说明
2. 各组件中重要函数或者类说明
3. 复杂的业务逻辑处理说明
4. 特殊情况的代码处理说明,对于代码中特殊用途的变量、存在临界值、函数中使用的hack、使用了某种算法或思路等需要进行注释描述
7. 多重 if 判断语句
```



# HTML规范

## 语法

- 缩进使用4个空格（soft tab）
- 嵌套的节点应该缩进
- 属性使用双引号
- 属性名全小写，用短横线（-）分隔
- 不要在自动闭合标签结尾处使用斜线（[HTML5 规范](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag) 指出他们是可选的）；
- 不要忽略可选的关闭标签，例：`</li>` 和 `</body>`。

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
    </head>
    <body>
        <img src="images/company_logo.png" alt="Company">

        <h1 class="hello-world">Hello, world!</h1>
    </body>
</html>
```

## HTML语义化

应当做到HTML语义和样式分离。

不要一套`div`走天下，善用`header`.`main`,`footer`等标签

## HTML5 doctype

规定必须在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；

虽然doctype不区分大小写，但是按照惯例，doctype大写 （[关于html属性，大写还是小写](http://stackoverflow.com/questions/15594877/is-there-any-benefits-to-use-uppercase-or-lowercase-letters-with-html5-tagname)）。

```html
<!DOCTYPE html>
<html>
	...
</html>
```

## lang属性

根据HTML5规范：

> 应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。

必须指定`lang`属性，常用的语言有

- zh
- zh-Hans
- zh-cn
- zh-hk
- zh-tw
- en

`zh-CN`和`zh-Hans`的区别：

- zh-CN 表示用在**中国大陆区域的中文**。包括各种大方言、小方言、繁体、简体等等都可以被匹配到。
- zh-Hans 表示**简体中文**。适用区域范围是全宇宙用中文简体的地方，内容包括各种用简体的方言等。

附上sitepoint的语言列表 [点我](http://reference.sitepoint.com/html/lang-codes)；

## 字符编码

### 字符编码

通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'UTF-8'。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
    </head>
    ...
</html>
```

### IE兼容模式

用 `<meta>` 标签可以指定页面应该用什么版本的IE来渲染；

如果你想要了解更多，请点击[这里](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e)；

不同doctype在不同浏览器下会触发不同的渲染模式（[这篇文章](https://hsivonen.fi/doctype/)总结的很到位）。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    </head>
    ...
</html>
```



## 引入CSS, JS

<u>根据HTML5规范, 通常在引入CSS和JS时不需要指明 `type`，因为 `text/css` 和 `text/javascript` 分别是他们的默认值。</u>

### script标签位置

`<script>`标签建议放到body标签的底部（不要放到</body>外）。

```html
<body>
    ...
	<script></script>
</body>
```

这样做的理由：

- 更好的容错率：如果JS执行出现错误了，最起码页面中的元素还能加载出来，因为DOM文档是从上往下的顺序执行的。 
- 更好的用户体验：head内的js会阻塞页面的传输和页面的渲染，放到body标签的底部可以避免加载js文件导致页面出现长时间的空白。

### link标签位置

link标签用于引入css文件，一般放置于``<head>``标签内，以避免页面元素由于样式缺失造成瞬间的白页或者给用户闪烁感。

### HTML5 规范链接

- [使用link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
- [使用style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
- [使用script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

```html
<!-- External CSS -->
<link rel="stylesheet" href="code_guide.css">

<!-- In-document CSS -->
<style>
    ...
</style>

<!-- External JS -->
<script src="code_guide.js"></script>

<!-- In-document JS -->
<script>
    ...
</script>
```

## 属性顺序

属性应该按照特定的顺序出现以保证易读性；

 ```markdown
  - `class`
  - `id`
  - `name`
  - `data-*` 
  - `src`, `for`, `type`, `href`, `value` , `max-length`, `max`, `min`, `pattern`
  - `placeholder`, `title`, `alt`
  - `aria-*`, `role`
  - `required`, `readonly`, `disabled`
 ```

class是为高可复用组件设计的，所以应处在第一位；

id更加具体且应该尽量少使用，所以将它放在第二位。

## boolean属性

boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要；

更多内容可以参考 [WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes)：

> **boolean属性的存在表示取值为true，不存在则表示取值为false。**

```html
<input type="text"  disabled>
```

## JS生成标签

在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差，不建议使用

## 减少标签数量

在编写HTML代码时，需要尽量避免多余的父节点；

很多时候，需要通过迭代和重构来使HTML变得更少。

## 实用高于完美

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；

任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

# CSS、SCSS规范

## 语法

- 使用soft tab（4个空格）。
- 每条属性声明末尾都需要分号
- 最外层统一使用双引号

## 命名规则

类名采用小写字母+短横线分隔的方式，如

`menu-home`

id采用小驼峰式命名

scss中的变量、函数、混合、placeholder采用小驼峰式命名

```css
/* class */
.element-content {
    ...
}

/* id */
#myDialog {
    ...
}

/* 变量 */
$colorBlack: #000;

/* 函数 */
@function pxToRem($px) {
    ...
}

/* 混合 */
@mixin centerBlock {
    ...
}

/* placeholder */
%myDialog {
    ...
}
```

## 空格

以下几种情况不需要空格：

- 属性名后
- 多个规则的分隔符','前
- `!important` '!'后
- 属性值中'('后和')'前
- 行末不要有多余的空格

以下几种情况需要空格：

- 属性值前
- 选择器'>', '+', '~'前后
- '{'前
- `!important` '!'前
- `@else` 前后
- 属性值中的','后
- 注释'/*'后和'*/'前

```css
/* not good */
.element {
    color :red! important;
    background-color: rgba(0,0,0,.5);
}

/* good */
.element {
    color: red !important;
    background-color: rgba(0, 0, 0, .5);
}

/* not good */
.element ,
.dialog{
    ...
}

/* good */
.element,
.dialog {

}

/* not good */
.element>.dialog{
    ...
}

/* good */
.element > .dialog{
    ...
}

/* not good */
.element{
    ...
}

/* good */
.element {
    ...
}

/* not good */
@if{
    ...
}@else{
    ...
}

/* good */
@if {
    ...
} @else {
    ...
}
```

## 空行

以下几种情况需要空行：

- 文件最后保留一个空行
- '}'后最好跟一个空行，包括scss中嵌套的规则
- 属性之间需要适当的空行，具体见[属性声明顺序](http://alloyteam.github.io/CodeGuide/#css-declaration-order)

```css
/* not good */
.element {
    ...
}
.dialog {
    color: red;
    &:after {
        ...
    }
}

/* good */
.element {
    ...
}

.dialog {
    color: red;

    &:after {
        ...
    }
}
```

## 换行

以下几种情况不需要换行：

- '{'前

以下几种情况需要换行：

- '{'后和'}'前
- 每个属性独占一行
- 多个规则的分隔符','后

```css
/* not good */
.element
{color: red; background-color: black;}

/* good */
.element {
    color: red;
    background-color: black;
}

/* not good */
.element, .dialog {
    ...
}

/* good */
.element,
.dialog {
    ...
}
```

## 注释

注释统一用'/* */'（scss中也不要用'//'），

缩进与下一行代码保持一致；

可位于一个代码行的末尾，与代码间隔一个空格。

```scss
/*
 * Modal header
 */
```

## 引号

最外层统一使用双引号；

url的内容要用引号；

属性选择器中的属性值需要引号。

```css
li[data-type="single"] {
    ...
}
```

## 属性声明顺序

相关的属性声明按不同的作用做分组处理，组之间需要有一个空行。

若同时书写简写属性和其包含的属性，比如`margin`和`margin-top`时，简写属性写在前面

无前缀的标准属性应该写在有前缀的属性后面

```css
.declaration-order {
    display: block;
    float: right;

    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;
    
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    width: 100px;
    height: 100px;
    
    margin: 5px;
    margin-top: 10px
```

## 颜色

颜色16进制用小写字母；

颜色16进制尽量用简写。

颜色尽量少用名称。

## 属性简写

简写需要清楚属性值的正确顺序，否则建议分开声明

`margin` 和 `padding` 建议使用简写

常见的属性简写包括：

- `font`
- `background`
- `transition`
- `animation`

## 媒体查询

<u>**尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。**</u>

```css
.element {
    ...
}

.element-avatar{
    ...
}

@media (min-width: 480px) {
    .element {
        ...
    }

    .element-avatar {
        ...
    }
}
```


## SCSS

提交的代码中不要有 `@debug`；

声明顺序：

- `@extend`
- 不包含 `@content` 的 `@include`
- 包含 `@content` 的 `@include`
- 自身属性
- 嵌套规则

`@import` 引入的文件不需要开头的'_'和结尾的'.scss'；

嵌套最多不能超过5层；

`@extend` 中使用placeholder选择器；

去掉不必要的父级引用符号'&'。

```scss
/* not good */
@import "_dialog.scss";

/* good */
@import "dialog";

/* not good */
.fatal {
    @extend .error;
}

/* good */
.fatal {
    @extend %error;
}

/* not good */
.element {
    & > .dialog {
        ...
    }
}

/* good */
.element {
    > .dialog {
        ...
    }
}
```

## 其他方面

属性值'0'后面不要加单位，如`margin: 0`

保留小数点前面的0（防止看代码的时候看漏，且符合生活习惯）

不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

用 `border: 0;` 代替 `border: none;`

选择器建议不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写），绝对不要超过6层。

发布的代码中不要有 `@import`；

尽量少用'*'选择器。

# JavaScript





> 本文参考文献：
>
> [前端开发规范](https://juejin.im/post/6844903574086877192)
>
> [Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/)
>
> [前端开发命名规范](https://www.jianshu.com/p/cf80698358d5)
>
> 

