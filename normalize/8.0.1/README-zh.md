## 前言
Normalize-zh.css是根据对Normalize.css的源码分析后，经过学习与整理，将源代码中的英文注释文档翻译为中文版本。

* file:  normalize-zh.css 
* author: mary
* date:  2020/06/21

## Normalize 源码解读

* 源码地址：[https://github.com/necolas/normalize.css/blob/master/normalize.css]
* 源码版本：v8.0.1 
 
### Document
```   
/**
 * 1. Correct the line height in all browsers.
 * 2. Prevent adjustments of font size after orientation changes in iOS.
 */
 
html {
  line-height: 1.15; /* 1 */
  -webkit-text-size-adjust: 100%; /* 2 */
}
``` 
1. 在所有浏览器中修正行高，统一设置。
 
2. 防止在iOS中更改方向后调整字体大小
 >苹果IOS设备调整后会自动调整文字的大小，苹果的意图是为了提升用户体验，比如竖屏状态下是14px，转换为横屏时就变成了20px，把text-size-adjust:100%就不会调整字体大小了。如果把值设置为'text-size-adjust:none'，那么就会导致用户无法放大缩小字体了。

### 专题性内容 Sections 
```
/**
 * Remove the margin in all browsers.
 */

body {
  margin: 0;
}
```
移除所有浏览器body元素默认边距，这里进行统一设置为0.
>不同浏览器下body边距不一样，如Google Chrome（V83.0.4103.106）、FireFox（V79.0a1）、Opera（68.0.3618.165）、IE8：`margin: 8px;` IE7：`margin: 15px 10px;` 
``` 
/**
 * Render the `main` element consistently in IE.
 */

main {
  display: block;
}
```
在IE中一致地渲染`main`元素为`display: block;`
>当低版本浏览器遇到不识别的元素时，会默认把他们当成内联元素(`inline`)，这里重新定义成为`block`元素。
``` 
/**
 * Correct the font size and margin on `h1` elements within `section` and
 * `article` contexts in Chrome, Firefox, and Safari.
 */

h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
```
更正Chrome, Firefox, and Safari中在`section` 和`article` 中使用`h1`元素的字体大小`font size`和边距`margin`
### 分组内容 Grouping content  
``` 
/**
 * 1. Add the correct box sizing in Firefox.
 * 2. Show the overflow in Edge and IE.
 */

hr {
  box-sizing: content-box; /* 1 */
  height: 0; /* 1 */
  overflow: visible; /* 2 */
}
```
1. 修正 Firefox 的` box-sizing`和其他浏览器之间的差异

2. 设置在 Edge and IE中`overflow: visible;`
>在 Firefox 中，hr元素的默认样式很多，和其它浏览器主要的差异有两点：  
1.设置了height为2px;  
2.box-sizing为border-box;  
此样式对这两个问题进行重置，进行统一
``` 
/**
 * 1. Correct the inheritance and scaling of font size in all browsers.
 * 2. Correct the odd `em` font sizing in all browsers.
 */

pre {
  font-family: monospace, monospace; /* 1 */
  font-size: 1em; /* 2 */
}
```
1. 在所有浏览器中更正字体大小的继承和缩放。
 
2. 在所有浏览器中更正奇数的“ em”字体大小。
### 语义化文本标签 Text-level semantics 
```
/**
 * Remove the gray background on active links in IE 10.
 */

a {
  background-color: transparent;
}
```
删除IE 10中活动链接上的灰色背景。
``` 
/**
 * 1. Remove the bottom border in Chrome 57-
 * 2. Add the correct text decoration in Chrome, Edge, IE, Opera, and Safari.
 */

abbr[title] {
  border-bottom: none; /* 1 */
  text-decoration: underline; /* 2 */
  text-decoration: underline dotted; /* 2 */
}
```
1.移除Chrome 57以下版本的底部边框。
2.在Chrome，Edge，IE，Opera和Safari中添加正确的文本修饰线的外观。
>语义`abbr`标签是表示简称或缩写，自身的`title`属性是完整版, 此标签在Firefox下默认有下边框。
>text-decoration用于设置文本的修饰线外观（下划线、上划线、贯穿线/删除线  或 闪烁），是text-decoration-line、text-decoration-color、text-decoration-style 和新出现的text-decoration-thickness属性的缩写。
``` 
/**
 * Add the correct font weight in Chrome, Edge, and Safari.
 */

b,
strong {
  font-weight: bolder;
}
```
Chrome，Safari  ，Edge中统一设置font weight为bolder
>Chrome 给`b`和`strong`设置的属性是`bold`
>Opera 给`b`和`strong`设置的属性是`bold`
>Firefox给`b`和`strong`设置的属性是`700`
``` 
/**
 * 1. Correct the inheritance and scaling of font size in all browsers.
 * 2. Correct the odd `em` font sizing in all browsers.
 */

code,
kbd,
samp {
  font-family: monospace, monospace; /* 1 */
  font-size: 1em; /* 2 */
}
```
1.在所有浏览器中更正字体大小的继承和缩放。
2.在所有浏览器中更正奇数的“ em”字体大小。
``` 
/**
 * Add the correct font size in all browsers.
 */

small {
  font-size: 80%;
}
```
在所有浏览器中统一small的字体大小
>small标签在 HTML 4.01 就已经存在，HTML5 中增强了它的寓意，表示旁注信息，不过此标签在各个浏览器中呈现的字体大小不一样。
``` 
/**
 * Prevent `sub` and `sup` elements from affecting the line height in
 * all browsers.
 */

sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}

sub {
  bottom: -0.25em;
}

sup {
  top: -0.5em;
}
```
在所有浏览器中防止`sub`和`sup`影响行高
>`sup`和`sub`两个标签是用来表示上标和下标，据HTML标准中对`small`，`sub`和`sup`的大小要求都是`smaller`，但`normalize.css`给`small`设的是80%，`sub`和`sup`却是75%，为了保持一致，且不影响其他元素的行高，把两者的`line-height`设为`0`，然后设置它的垂直以baseline开始，设置`top`和`bottom`手动设置两者偏移量。
### 内嵌元素 Embedded content 
``` 
/**
 * Remove the border on images inside links in IE 10.
 */

img {
  border-style: none;
}
```
删除IE 10中链接`<a>`内部图像的边框。
> 在旧版本的浏览器中，图片默认会有一个奇丑无比的蓝色边框。
### 表单 Forms 
``` 
/**
 * 1. Change the font styles in all browsers.
 * 2. Remove the margin in Firefox and Safari.
 */

button,
input,
optgroup,
select,
textarea {
  font-family: inherit; /* 1 */
  font-size: 100%; /* 1 */
  line-height: 1.15; /* 1 */
  margin: 0; /* 2 */
}
```
1.在所有浏览器中更改字体样式。
2.在Firefox和Safari中删除边距。
>有一些浏览器会把form表单中的一些元素textarea，text，button，select中的字体和字体颜色默认会设置成用户的字体或者是浏览器的字体，并不会从父元素继承。
``` 
/**
 * Show the overflow in IE.
 * 1. Show the overflow in Edge.
 */

button,
input { /* 1 */
  overflow: visible;
}
```
* 统一 IE的overflow属性为visible
> 在 IE 中button默认的overflow是hidden，这里统一为visible
``` 
/**
 * Remove the inheritance of text transform in Edge, Firefox, and IE.
 * 1. Remove the inheritance of text transform in Firefox.
 */

button,
select { /* 1 */
  text-transform: none;
}
```
在Edge，Firefox和IE中删除文本转换的继承。 统一各浏览器text-transform不会继承
``` 
/**
 * Correct the inability to style clickable types in iOS and Safari.
 */

button,
[type="button"],
[type="reset"],
[type="submit"] {
  -webkit-appearance: button;
}
```
纠正无法在iOS和Safari中设置可点击类型的样式的问题。
``` 
/**
 * Remove the inner border and padding in Firefox.
 */

button::-moz-focus-inner,
[type="button"]::-moz-focus-inner,
[type="reset"]::-moz-focus-inner,
[type="submit"]::-moz-focus-inner {
  border-style: none;
  padding: 0;
}
```
在Firefox中删除内部边框和填充。
``` 
/**
 * Restore the focus styles unset by the previous rule.
 */

button:-moz-focusring,
[type="button"]:-moz-focusring,
[type="reset"]:-moz-focusring,
[type="submit"]:-moz-focusring {
  outline: 1px dotted ButtonText;
}
```
恢复以前的规则未设置的焦点样式。
``` 
/**
 * Correct the padding in Firefox.
 */

fieldset {
  padding: 0.35em 0.75em 0.625em;
}
```
更正Firefox中fieldset的内边距。
``` 
/**
 * 1. Correct the text wrapping in Edge and IE.
 * 2. Correct the color inheritance from `fieldset` elements in IE.
 * 3. Remove the padding so developers are not caught out when they zero out
 *    `fieldset` elements in all browsers.
 */

legend {
  box-sizing: border-box; /* 1 */
  color: inherit; /* 2 */
  display: table; /* 1 */
  max-width: 100%; /* 1 */
  padding: 0; /* 3 */
  white-space: normal; /* 1 */
}
```
1.更正Edge和IE中的文字换行。
2.纠正IE中来自“ fieldset”元素的颜色继承。
3.删除内边距，使开发人员在所有浏览器中将“ fieldset”元素清零时不会捕捉到。
``` 
/**
 * Add the correct vertical alignment in Chrome, Firefox, and Opera.
 */

progress {
  vertical-align: baseline;
}
```
在Chrome, Firefox, 和Opera的progress元素中添加以baseline垂直居中的样式
>progress是HTML5的新标签，可以定义进度条，但在Chrome, Firefox, 和Opera并没有以baseline垂直对齐。
``` 
/**
 * Remove the default vertical scrollbar in IE 10+.
 */

textarea {
  overflow: auto;
}
```
删除IE 10以上版本中textarea的默认垂直滚动条。
> IE8版本以上中textarea默认的垂直滚动条
``` 
/**
 * 1. Add the correct box sizing in IE 10.
 * 2. Remove the padding in IE 10.
 */
[type="checkbox"],
[type="radio"] {
  box-sizing: border-box; /* 1 */
  padding: 0; /* 2 */
}
```
1. IE10中添加type="checkbox"和type="radio"的box-sizing为content-box的问题。

2. 移除IE10中的内边距。

> IE 8/9/10中 box-sizing 被设置为content-box的问题

> IE 8/9/10 中有多余的内边距

>chrome、FireFox、Opera中
```
input[type="checkbox" i] {    
    box-sizing: border-box;
    margin: 3px 3px 3px 4px; 
}
input[type="radio" i] { 
     box-sizing: border-box;
     margin: 3px 3px 0px 5px; 
 }
```
>IE
```
input[type="checkbox" i] {   
    box-sizing: content-box;
    margin: auto; 
}
input[type="radio" i] { 
     box-sizing: content-box;
     margin: auto; 
 }
```
``` 
/**
 * Correct the cursor style of increment and decrement buttons in Chrome.
 */

[type="number"]::-webkit-inner-spin-button,
[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
```
``` 
/**
 * 1. Correct the odd appearance in Chrome and Safari.
 * 2. Correct the outline style in Safari.
 */

[type="search"] {
  -webkit-appearance: textfield; /* 1 */
  outline-offset: -2px; /* 2 */
}
```
``` 
/**
 * Remove the inner padding in Chrome and Safari on macOS.
 */

[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
```
``` 
/**
 * 1. Correct the inability to style clickable types in iOS and Safari.
 * 2. Change font properties to `inherit` in Safari.
 */

::-webkit-file-upload-button {
  -webkit-appearance: button; /* 1 */
  font: inherit; /* 2 */
}
```
### Interactive 
``` 
/*
 * Add the correct display in Edge, IE 10+, and Firefox.
 */

details {
  display: block;
}
```
``` 
/*
 * Add the correct display in all browsers.
 */

summary {
  display: list-item;
}
```

### Misc 
``` 
/**
 * Add the correct display in IE 10+.
 */

template {
  display: none;
}
```
``` 
/**
 * Add the correct display in IE 10.
 */

[hidden] {
  display: none;
}
```
