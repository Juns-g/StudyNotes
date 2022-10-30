# 理解CSS | 青训营笔记

**这是我参与「第四届青训营 」笔记创作活动的的第2天**



## 页面中使用CSS



1. 外链

```html
<link rel="stylesheet" href="css文件地址">
```



2. 嵌入

```html
<style>
	li {
		margin: 0;
	}
</style>
```



3. 内联

```html
<p style="margin: 1em 0"></p>
```



- 如何工作

![image4a166a69e221f0e7.png](https://img.wang.232232.xyz/img/2022/07/25/image4a166a69e221f0e7.png)



## 选择器



### 统配选择器 *

```css
*{
	margin: 0;
	padding: 0;
}
```



### id选择器 #

```html
	<style>
		#iidd{
			color:red;
			font-size: 30px;
			font-weight: 800;
		}
	</style>
	
	<body>
		<h1 id="iidd">id选择器用的</h1>
	</body>
```



### 类选择器 .

```html
	<style>
		.ccc{
			color:red;
			font-size: 30px;
			font-weight: 800;
		}
	</style>
	
	<body>
		<h1 class="ccc">class选择器用的</h1>
	</body>
```



### 属性选择器 []

> [CSS属性选择器详解](https://www.w3school.com.cn/css/css_selector_attribute.asp)

- [title] 只要元素有这个属性就可以被选中

- [att=val] 精确匹配，检查一个元素属性的值是否是 val

```css
/* 所有具有title属性，并且title的值为a的元素，都可以被选中，将文字颜色设置为blue*/
[title=a] {color: blue;}
```

- [att~=val] 一个元素的某个属性的值有很多个（被空格分开），这些值只要有一个匹配上了 val 就行。

```css
/*具有title属性，并且属性值（被空格分开）中有three的元素，可以被选中，将文字的颜色设置为green*/
[title~=three] {color: green;}
```

- [att|=val] 开头匹配，检查一个元素的值是否是以 val 开头，它跟精确匹配的区别是属性只要以 val 开头即可，后面内容不管。

```js
/*具有title属性，并且属性值以h开头的元素，可以被选中，将文字的背景设置为pink*/
[title|=h] {background: pink;}
```



- 示例

```html
	<style>
		input[type="password"] {
			color: greenyellow;
			border-color: skyblue;
		}

		[disabled] {
			color: red;
			border-color: mistyrose;
		}
	</style>

	<body>
		<label>用户名：</label>
		<input value="zhao" disabled>
		<br>
		<br>
		<label>密码：</label>
		<input value="123456" type="password">
	</body>
```

![image2036a4cc4d232b9d.png](https://img.wang.232232.xyz/img/2022/07/25/image2036a4cc4d232b9d.png)



```html
<p><a href="#top">回到顶部辣</a></p>
<p><a href="a.jpg">看看图片捏</a></p>

<style>
	a[href^="#"] {
		/* 用了正则 */
		color: pink;
		background: 0 center/1em 
		url(https://assets.codepen.io/59477/arrow-up.png) no-repeat;
		padding-left: 1.1em;
	}

	a[href$=".jpg"] {
		color: skyblue;
		background: 0 center/1em 
		url(https://assets.codepen.io/59477/image3.png) no-repeat;
		padding-left: 1.2em;
	}
</style>
```

![imageedac988f5db1a064.png](https://img.wang.232232.xyz/img/2022/07/25/imageedac988f5db1a064.png)



### 伪类选择器：

> 源于上文中的a标签笔记
>
> ### 伪类用法
>
> >  a标签href=""的时候，默认状态时:visited状态；a标签没有href属性的时候，默认状态时:active状态，这两种情况都不影响:active和:hover的触发，但是永远不会触发:link
>
>  
>
> 1. link：设置a对象在未被访问前的样式表属性
>
> 2. visited：设置a对象在其链接地址已被访问过时的样式表属性
>
> 3. hover：设置对象在其鼠标悬停时的样式表属性
>
> 4. active：设置对象在被用户激活（在鼠标点击与释放之间发生的事件）时的样式表属性
>
> 	**CSS定义中的顺序是LVHA(link—visited—hover—active)	LoVe,HAte**



```html
<a href="http://acmclub.cn">acmclub.cn</a>
<br><br>
<label>
	用户名：
	<input type="text">
</label>

<style>
	a:link {
		color: black;
	}
	a:visited {
		color: gray;
	}
	a:hover {
		color: pink;
	}
	:focus {
		outline: 2px solid limegreen;
	}
</style>
```

![imageb4d1f8b6034c2d74.png](https://img.wang.232232.xyz/img/2022/07/25/imageb4d1f8b6034c2d74.png)



```html
<ol>
	<li>111</li>
	<li>222</li>
	<li>333</li>
	<li>444</li>
	<li>555</li>
</ol>

<style>
	li {
		list-style-position: inside;
		border-bottom: 1px solid powderblue;
		padding 0.5em;
	}
	li:first-child {
		color: red;
	}
	li:last-child {
		color: red;
		border-bottom: none;
	}
</style>
```

![imageef38ea6d37189552.png](https://img.wang.232232.xyz/img/2022/07/25/imageef38ea6d37189552.png)



## 选择器的组合



### 第一优先级

- 无连接符号

```css
.a.b {
    color: pink;
}
```



### 第二优先级

- ` `、`>`、`~`、`+`

| 名称 | 语法 | 说明 | 示例 |
| ---- | ---- | ---- | ---- |
|直接组合|AB|满足A同时满足B|input:focus|
|后代组合|A B|选中B,如果它是A的子孙|nav a|
|亲子组合|A>B|选中B,如果它是A的子元素|section>p|
|兄弟选择器|A~B|选中B,如果它在A后且和A同级|h2~ p|
|相邻选择器|A+B|选中B,如果它紧跟在A后面|h2+p|

- 懒得写示例代码了捏，到时候看看就造了



## 文本

> [W3School  CSS文本](https://www.w3school.com.cn/css/pro_css_text.asp)



### font-face引入外部字体

```css
/* 引入字体 */
@font-face {
	font-family: zhu-zi-a-wan-e;
	src: url('../fonts/筑紫a丸圆体E.ttf');
    /*url也可以填在线的*/
} 
```



### 样式



- font-size 大小
- font-style 斜体啥的
- font-weight 自重/粗细
- line-height 行高
- [white-space](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space) 空格处理



## 布局



![imageb2c0270658234d00.png](https://img.wang.232232.xyz/img/2022/07/25/imageb2c0270658234d00.png)



### 基础



#### width

- 指定content box宽度

- 取值为长度、百分数、auto

- auto由浏览器根据其它属性确定

- 百分数相对于容器的content box宽度



#### height

- 指定content box高度
- 取值为长度、百分数、auto
- auto取值由内容计算得来
- 百分数相对于容器的content box高度
- 容器有指定的高度时，百分数才生效



#### padding 

- 指定元素四个方向的内边距
- .百分数相对于容器宽度



#### border

- 定容器边框样式、粗细和颜色  [在线演示](https://cdpn.io/webzhao/debug/MWEPPKY)
- 三种属性，可以合并写
	- width
	- style
	- color



#### margin

- 指定元素四个方向的外边距
- 取值可以是长度、百分数、auto(可用于水平居中)
- 百分数相对于容器宽度
- 垂直方向的margin会合并



#### border-box

![image7c1c3e844e3ee0a3.png](https://img.wang.232232.xyz/img/2022/07/25/image7c1c3e844e3ee0a3.png)



```html
<p class="a">
  This is the behavior of width and height as specified by CSS2.1. The
  specified width and height (and respective min/max properties) apply to
  the width and height respectively of the content box of the element.
</p>
<p class="b">
  Length and percentages values for width and height (and respective min/max
  properties) on this element determine the border box of the element.
</p>

<style>
  html {
    font-size: 24px;
  }

  .a {
    width: 100%;
    padding: 1em;
    border: 3px solid #ccc;
  }

  .b {
    box-sizing: border-box;
    width: 100%;
    padding: 1em;
    border: 3px solid #ccc;
  }
</style>
```



![image83548f024585ba1c.png](https://img.wang.232232.xyz/img/2022/07/25/image83548f024585ba1c.png)



#### overflow

- 文本超出文本框时的设置
- [在线演示](https://cdpn.io/webzhao/debug/ZEXqqdK)



### 块级VS行级



| Block Level Box      | Inline Level Box                       |
| -------------------- | -------------------------------------- |
| 不和其它盒子并列摆放 | 和其它行级盒子一起放在一行或拆开成多行 |
| 适用所有的盒模型属性 | 盒模型中的width、height不适用          |



| 块级元素                                             | 行级元素                                       |
| ---------------------------------------------------- | :--------------------------------------------- |
| 生成块级盒子                                         | 生成行级盒子<br>内容分散在多个行盒(line box)中 |
| body、article、div、main、section、h1-6、p、ul、li等 | span、em、strong、cite、code等                 |
| display:block                                        | display:inline                                 |



### display属性

- block  块级盒子
- inline  行级盒子
- inline-block  本身是行级，可以放在行盒中；可以设置宽
	高；作为一个整体不会被拆散成多行
- none  排版时完全被忽略



### 排版



#### 常规流

- 根元素、浮动和绝对定位的元素会脱离常规流
- 其它无素都在常规流之内(in-flow)
- 常规流中的盒子，在某种排版上下文中参与布局



#### 行级排版上下文

- Inline Formatting Context(IFC)
- 只包含行级盒子的容器会创建一个IFC
- IFC内的排版规则
	- 盒子在一行内水平摆放
	- 一行放不下时，换行显示
	- text-align决定一行内盒子的水平对齐
	- vertical-align决定一个盒子在行内的垂直对齐
	- 避开浮动(float)元素



#### 块级排版上下文

- Block Formatting Context(BFC)
- 某些容器会创建一个BFC
	- 根元素
	- 浮动、绝对定位、inline-block
	- Flex子项和Grid子项
	- overflow值不是visible的块盒
	- display:flow-root;
- BFC内的排版规则
	- 盒子从上到下摆放
	- 垂直margin合并
	- BFC内盒子的margin不会与外面的合并
	- BFC不会和浮动元素重叠



#### Flex  Box是什么？

- 一种新的排版上下文
- 它可以控制子级盒子的：
	- 摆放的流向(→←↑↓)
	- 摆放顺序
	- 盒子宽度和高度
	- 水平和垂直方向的对齐
	- 是否允许折行



示例

```html
<div class="container">
  <div class="a">A</div>
  <div class="b">B</div>
  <div class="c">C</div>
</div>
<style>
  .container {
    display: flex;
    border: 2px solid #966;
  }
  .a, .b, .c {
    text-align: center;
    padding: 1em;
  }
  .a {
    background: #fcc;
  }
  .b {
    background: #cfc;
  }
  .c {
    background: #ccf;
  }
</style>
```

![image071e5309dfad0bad.png](https://img.wang.232232.xyz/img/2022/07/25/image071e5309dfad0bad.png)



- justify-content

![image531ddbbe68f0ce97.png](https://img.wang.232232.xyz/img/2022/07/25/image531ddbbe68f0ce97.png)



- align-items

![imageef8f219100780b6b.png](https://img.wang.232232.xyz/img/2022/07/25/imageef8f219100780b6b.png)



- align-self

![imagecbdfab1f399abf45.png](https://img.wang.232232.xyz/img/2022/07/25/imagecbdfab1f399abf45.png)





- Flexibility
	- 可以设置子项的弹性：当容器有剩余空间时，会伸展；容器空间不够时，会收缩。
	- flex-grow有剩余空间时的伸展能力
	- flex-shrink容器空间不足时收缩的能力
	- flex-basis没有伸展或收缩时的基础长度



#### Grid布局

> 建议去了解一下，视频讲的不多



![image2700ce2e90d7bb33.png](https://img.wang.232232.xyz/img/2022/07/25/image2700ce2e90d7bb33.png)



![image891f7b2225656504.png](https://img.wang.232232.xyz/img/2022/07/25/image891f7b2225656504.png)



### position属性

- static  默认值，非定位元素
- relative  相对自身原本位置偏移，不脱离文档流
	- 在常规流里面布局
	- 相对于自己本应该在的位置进行偏移
	- 使用top、left、bottom、right设置偏移长度
	- 流内其它元素当它没有偏移一样布局
	- ![image238f929620540080.png](https://img.wang.232232.xyz/img/2022/07/25/image238f929620540080.png)
- absolute  绝对定位，相对非static祖先元素定位
	- 脱离常规流
	- 相对于最近的非static祖先定位
	- 不会对流内元素布局造成影响
	- ![image6c53c04c64bf9620.png](https://img.wang.232232.xyz/img/2022/07/25/image6c53c04c64bf9620.png)
- fixed  相对于视口绝对定位

