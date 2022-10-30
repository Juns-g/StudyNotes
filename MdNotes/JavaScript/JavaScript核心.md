# JavaScript Web APIs

## DOM

### 获取元素

#### 根据id

```html
<!-- getELementByID-->
	<div id="time">2023-4-5</div>
		<script>
			//写在标签后面
			//使用的是驼峰命名法
			//大小写要注意
			//返回的是一个元素对象
			var timer = document.getElementById('time');
			console.log(timer);
			console.log(typeof timer);
			console.dir(timer);			
            //打印返回的元素对象，更好的查看属性和方法
		</script> 
```

#### 根据标签名

```html
<!-- getelementsByTagName -->
		<ul>
			<li>lalallall</li>
			<li>lalallall</li>
			<li>lalallall</li>
		</ul>
		<script>
			var lis = document.getElementsByTagName('li');
			console.log(lis);
			//返回的数组形式
			console.log(lis[1]);
			for(var i = 0;i<lis.length;i++){
				console.log(lis[i]);
			}
            
			var ol = document.getElementsByTagName('ol');
			console.log(ol[0].getElementsByTagName('li'));
			//获取页面中第一个ol里面的li
			
			var ol2=document.getElementById('eee');
			console.log(ol2.getElementsByTagName('li'));
			//用的id获取
		</script>
```

#### 类名(H5新增)

```html
<!-- getElementsByClassName -->
		<div class="bbb">爷是骨灰盒</div>
		<script>
			var hezi=document.getElementsByClassName('bbb');
			console.log(hezi);
		</script>
```

#### 都行(H5新增)

```html
<!-- querySelector,只能得到第一个 -->
		<div class="box">盒子1</div>
		<div class="box">盒子2</div>
		
		<div id="nav">
			<ul>
				<li>lalallall</li>
				<li>lalallall</li>
				<li>lalallall</li>
			</ul>
		</div>		
		<script>
			var firstBox= document.querySelector('.box');//类名
			console.log(firstBox);
			var nav = document.querySelector('#nav');//id
			console.log(nav);
			var li1=document.querySelector('li');//标签
			console.log(li1);
		</script>

<!-- querySelectorAll,可以是所有的-->
		<script	>
			var allBox=document.querySelectorAll('.box');
			console.log(allBox);
			var lis=document.querySelectorAll('li');
			console.log(lis);
		</script>
```

#### 获取body,html元素

```javascript
			//1.获取body
			var bodyEle=document.body;
			console.log(bodyEle);
			console.log(bodyEle);
			//2.获取html
			var htmlEle=document.documentElement;
			console.log(htmlEle);
```

### 事件基础

#### 事件三要素

1. 事件源
2. 事件类型
3. 事件处理程序

```html
		<button id="bt">按钮</button>
		<script>
			var bt=document.getElementById('bt');
			bt.onclick=function(){
				alert('点我干啥啊');
			}
		</script>
```

#### 常见鼠标事件

| 鼠标事件    | 条件             |
| :---------- | :--------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获得鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |

### 操作元素

#### 文字修改

- element.innerText	从起点到终点的内容，但它去除html标签，空格和换行也会去掉

```html
		<button>点点看啊</button>
		<div>当前时间</div>
		<script>
			var btn=document.querySelector('button');
			var div=document.querySelector('div');
			btn.onclick=function(){
				div.innerText=getTime();
			}
			function getTime(){
				var time = new Date();
				var h = time.getHours();
				h = h<10?'0'+h:h;
				var m = time.getMinutes();
				m = m<10?'0'+m:m;
				var s = time.getSeconds();
				s = s<10?'0'+s:s;
			    return h+':'+m+":"+s;
			}
		</script>
```

- element.innerHTML	从起点到终点的全部内容，包括html标签，保留空格和换行

```html
		<div id="1"></div>
		<div id="2"></div>
		<p>
			1
			<span>33333</span>
		</p>
		<script>
			//innerText不识别html标签
			//innerHTML识别，W3C标准
			var div1=document.getElementById('1');
			div1.innerText='<strong>加粗</strong>啦啦啦啦';
			var div2=document.getElementById('2');
			div2.innerHTML='<strong>加粗</strong>啦啦啦啦';
			//都可以读写
			var p=document.querySelector('p');
			console.log(p.innerText);
			console.log(p.innerHTML);
		</script>
```

#### 图片修改

```html
		<button id='1'>111</button>
		<button id='2'>222</button>
		<img src="img/111.png" alt="" title="1">
		<script>
			var y111=document.getElementById('1');
			var y222=document.getElementById('2');
			var img=document.querySelector('img');
			y111.onclick=function(){
				img.src='img/111.png';
				img.title='1';
			}
			y222.onclick=function(){
				img.src='img/222.png';
				img.title='2';
			}
		</script>
```

#### 表单修改

```html
		<button>点我</button>
		<input type="text" value="输入内容">
		<script>
			var btn=document.querySelector('button');
			var input=document.querySelector('input');
			btn.onclick = function(){
				input.value='啊，我被点击了';
				this.disabled=true;//禁用按钮
				//this指向的是btn
			}
		</script>
```

#### 样式修改

```html
		<div style="width: 200px;height: 200px;background-color: pink;"></div>
		<script>
			//js的样式使用驼峰命名法
			//js修改的style样式操作产生的是行内样式，权重较高
			var div=document.querySelector('div');
			div.onclick=function(){
				div.style.backgroundColor='red';
				div.style.width='300px';
			}
		</script>
```

- 直接用className='xxx';调用css更简单

#### 属性操作

```html
		<div id="demo" index="222" class="333"></div>
		<script>
			var div=document.querySelector('div');
			//获取属性
			console.log(div.id);//得到的是自带的属性
			console.log(div.getAttribute('id'));//可以得到自定义的属性
			console.log(div.getAttribute('index'));
			//设置属性值
			div.id='test';
			div.className='lalalla';
			//element.seaAttribute('属性',值)主要修改自定义属性
			div.setAttribute('index',11111);
			div.setAttribute('class',22);
			//移除属性
			div.removeAttribute('index');
		</script>
```

#### H5自定义属性

- 要以data-开头并复制
  - `<div data-index="1"></div>`
- 获取H5自定义属性

```javascript
			//兼容性获取,这个好一点
			element.getAttribute('data-index');
			//H5新增,只能获取data开头的
			//dataset是一个集合，里面存放所有的自定义属性
			element.dataset
			element.dataset.index
			element.dataset['index']
			//如果自定义属性里面用了多个-链接，获取数要用驼峰命名法
			//如自定义的是data-list-name
			element.dataset.listName
			element.dataset.['listName']
```

## 节点操作

### 节点层级

1. 父节点 parentNode

```html
		<div class="box">
			<span class="eeee">x</span>
		</div>
		<script>
			var eeee=document.querySelector('.eeee');
			console.log(eeee.parentNode);
		</script>
```

2. 子节点 parentNode.childNodes

```html
		<ul>
			<li>333</li>
			<li>333</li>
			<li>333</li>
			<li>333</li>
		</ul>
		<script>
			var ul=document.querySelector('ul');
			console.log(ul.childNodes);//包含所有的元素节点和文本节点
			console.log(ul.children);//非标准，常用，获取所有的子元素节点	
		</script>
		

		<ol>
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
		</ol>
		<script>
			var ol=document.querySelector('ol');
			//firsrChild第一个子节点
			console.log(ol.firstChild);
			console.log(ol.lastChild);
			//firstElementChild第一个子元素节点
			console.log(ol.firstElementChild);
			console.log(ol.lastElementChild);
			//实际开发，没有兼容性问题的写法
			console.log(ol.children[0]);
			console.log(ol.children[ol.children.length-1]);
		</script>
		
```

3. 兄弟节点 

```html
		<div>爷是div</div>
		<span>爷是span</span>
		<script>
			var div=document.querySelector('div');
			//下一个兄弟节点，包含元素节点和文本节点
			console.log(div.nextSibling);
			//上一个兄弟节点，包含元素节点和文本节点
			console.log(div.previousSibling);
			//下一个兄弟元素节点
			console.log(div.nextElementSibling);
			//上一个兄弟元素节点
			console.log(div.previousElementSibling);
		</script>
```

### 添加节点

```html
		<ul>
			<li>1111</li>
		</ul>
		<script>
			//创建元素节点
			var li=document.createElement('li');
			//添加节点
			var ul=document.querySelector('ul');
			ul.appendChild(li);
			//添加在前面(child,指定元素)
			var li2=document.createElement('li');
			ul.insertBefore(li2,ul.children[0]);
		</script>
```

### 删除节点

```html
		<button>点击删除</button>
		<ul>
			<li>一</li>
			<li>二</li>
			<li>三</li>
		</ul>
		<script>
			var ul=document.querySelector('ul');
			var btn=document.querySelector('button');
			btn.onclick=function(){
				if(ul.children.length==0){
					this.disabled=true;
				}else{
					//删除节点
					ul.removeChild(ul.children[0]);				
				}
			}
		</script>
```

### 复制节点

```html
		<ul>
			<li>一</li>
			<li>二</li>
			<li>三</li>
		</ul>
		<script>
			var ul=document.querySelector('ul');
			//括号里面为空或者是false就只克隆标签，不含内容
			var li1=ul.children[0].cloneNode();
			ul.appendChild(li1);
			//括号里面为true就是深克隆
			var li2=ul.children[0].cloneNode(true);
			ul.appendChild(li2);
		</script>

```

## 事件高级

### 注册事件

```html
		<button>传统注册事件</button>
		<button>方法监听注册事件</button>
		<script>
			var btns=document.querySelectorAll('button');
			//传统方式注册事件
			btns[0].onclick=function(){
				alert('hi');
			}
			btns[0].onclick=function(){
				alert('有唯一性，后面的会覆盖前面的');
			}
			//事件监听注册事件addEventListener
			//里面的事件类型是字符串，加引号，不用on
			//同一个元素可以加很多个监听器
			btns[1].addEventListener('click',function(){
				alert('222');
			})
			btns[1].addEventListener('click',function(){
				alert('333');
			})
		</script>
```

### 删除事件

```html
		<div style="height: 30px;width: 30px;background-color: pink;">1</div>
		<div style="height: 30px;width: 30px;background-color: pink;">2</div>
		<div style="height: 30px;width: 30px;background-color: pink;">3</div>
		<script>
			var divs=document.querySelectorAll('div');
			divs[0].onclick=function(){
				alert(111);
				//传统方式删除事件
				divs[0].onclick=null;
			}
			//addEventListener
			divs[1].addEventListener('click',fn);//fn后面不加括号
			function fn(){
				alert(22);
				divs[1].removeEventListener('click',fn);
			}
		</script>
```

### 事件对象

```html
		<div style="height: 30px;width: 30px;background-color: pink;">1</div>
		<script>
			var d=document.querySelector('div');
			d.onclick=function(event){
				console.log(event);
			}
			d.addEventListener('click',function(event){
				console.log(event);
			})
			//event就是一个事件对象，当形参来看
			//他是系统自动创建的
			//他是事件的一系列相关数据的集合
			//可以自己命名event,evt,e
		</script>
```

#### 常见属性和方法

```html
		<div>123</div>
		<ul>
			<li>aa</li>
			<li>aa</li>
			<li>aa</li>
		</ul>
		<script>
			var d=document.querySelector('div');
			//e.target返回的是触发事件的对象
			d.addEventListener('click',function(e){
				console.log(e.target);
				console.log(this);//返回的是绑定事件的对象
			})
			var ul=document.querySelector('ul');
			ul.addEventListener('click',function(e){
				console.log(e.target);//li
				console.log(this);//ul
			})
		</script>
```

```html
		<div>123</div>
		<a href="http://www.baidu.com">百度</a>
		<form action="http://www.baidu.com">
			<input type="submit" value="提交" name="sub">
		</form>
		<script>
			var d=document.querySelector('div');
			//返回事件类型
			d.addEventListener('click',fn);
			d.addEventListener('mouseover',fn);
			d.addEventListener('mouseout',fn);
			function fn(e){
				console.log(e.type);
			}
			//阻止默认行为（事件）让链接不跳转
			var a=document.querySelector('a');
			a.addEventListener('click',function(e){
				e.preventDefault();
			})
			
		</script>
```

- e.stopPropagation()阻止事件冒泡

### 事件委托

```html
		<ul>
			<li>我是小李啊啊啊啊啊啊</li>
			<li>我是小李啊啊啊啊啊啊</li>
			<li>我是小李啊啊啊啊啊啊</li>
			<li>我是小李啊啊啊啊啊啊</li>
		</ul>
		<script>
			var ul=document.querySelector('ul');
			ul.addEventListener('click',function(e){
				e.target.style.backgroundColor='pink';
			})
            //就是父节点设置监听器
		</script>
```

### 常用鼠标事件

```html
		<p>右键点爹试试！</p>
		<script>
			var p=document.querySelector('p');
			//禁用右键菜单
			p.addEventListener('contextmenu',function(e){
				e.preventDefault();
			})
			//禁止选中文字
			p.addEventListener('selectstart',function(e){
				e.preventDefault();
			})
        </script>
```

- [一篇非常详细的js鼠标事件](https://blog.csdn.net/qq_26722321/article/details/111190415)

|  属性   |                             说明                             |
| :-----: | :----------------------------------------------------------: |
| clientX |          以浏览器窗口左上顶角为原点，定位 x 轴坐标           |
| clientY |          以浏览器窗口左上顶角为原点，定位 y 轴坐标           |
| offsetX |      以当前事件的目标对象左上顶角为原点，定位 x 轴坐标       |
| offsetY |      以当前事件的目标对象左上顶角为原点，定位 y 轴坐标       |
|  pageX  | 以 document 对象（即文档窗口）左上顶角为原点，定位 x 轴坐标  |
|  pageY  | 以 document 对象（即文档窗口）左上顶角为原点，定位 y 轴坐标  |
| screenX |           计算机屏幕左上顶角为原点，定位 x 轴坐标            |
| screenY |           计算机屏幕左上顶角为原点，定位 y 轴坐标            |
| layerX  | 最近的绝对定位的父元素（如果没有，则为 document 对象）左上顶角为元素，定位 x 轴坐标 |
| layerY  | 最近的绝对定位的父元素（如果没有，则为 document 对象）左上顶角为元素，定位 y 轴坐标 |

```javascript
			//MouseEvent
			document.addEventListener('click',function(e){
				//client 鼠标在可视区的坐标，有滚动条也一样
				console.log(e.clientX);
				console.log(e.clientY);
				//page 鼠标在页面文档的坐标
				console.log(e.pageX);
				console.log(e.pageY);
				//screen 鼠标在电脑屏幕的坐标
				console.log(e.screenX);
				console.log(e.screenY);
			})
```

### 常用键盘事件

```javascript
			//常用的键盘事件
			//执行顺序是down-press-up
			// keyup 该键弹起时候触发
			document.addEventListener('keyup',function(){
				console.log('弹起了');
			})
			// keydown 该键按下时候触发
			document.addEventListener('keydown',function(){
				console.log('按下了');
			})
			// keypress 该键按下时候触发，但不识别功能键ctrl，shift，箭头等
			document.addEventListener('keypress',function(){
				console.log('按下了');
			})
```

- keyCode

- [百度百科ASCII表](https://baike.baidu.com/item/ASCII/309296?fromtitle=ascii%E7%A0%81)

- [本地](C:\Users\123\Desktop\ACM\工程创新\md笔记\JavaScript\ASCII.md)

```javascript
			// keyCode属性可以得到相应键的ASCII码值
			// keyup和keydown不区分字母大小写
			// keypress区分大小写
			document.addEventListener('keyup',function(e){
				console.log('up:'+e.keyCode);
				console.log(e.key);
			})
			document.addEventListener('keydown',function(e){
				console.log('down:'+e.keyCode);
				console.log(e.key);
			})
			document.addEventListener('keypress',function(e){
				console.log('press:'+e.keyCode);
				console.log(e.key);
			})
```

## BOM

### window对象

#### 常见事件

##### 窗口加载事件

```html
		<button>按钮</button>
		<script>
			// 正常要写在后面才会执行，但是window就可写在任意位置
			// 会等页面内容全部加载完毕之后才会执行
			window.addEventListener('load',function(){
				var b=document.querySelector('button');
				b.addEventListener('click',function(){
					alert('点老子啊');
				})
			})
			window.addEventListener('load',function(){
				//alert(222);
			})
			// 当DOM加载完毕就执行，不包括样式表，图片，flash
			window.addEventListener('DOMContentLoaded',function(){
				//alert(333);
			})
		</script>
```

##### 调整窗口大小事件

```html
		<div>11111</div>
		<script>
			window.addEventListener('load',function(){
				var div=document.querySelector('div');
				window.addEventListener('resize',function(){
					console.log(window.innerWidth);
					console.log('变了啊');
					if(window.innerWidth<=800){
						div.style.display='none';
					}else{
						div.style.display='block';
					}
				})
			})
		</script>
```

### 定时器

```javascript
			// setTimeout 定时器
			// window.setTimeout(调用函数，延时时间ms)
			// window可以省略
			setTimeout(function(){
				console.log('时间到了啊');
			},2000);
			
			function callback(){
				console.log('爆炸啊');
			}
			// 经常添加标识符
			var t1=setTimeout(callback,3000);
			var t2=setTimeout(callback,5000);
			// setTimeout('callback()',3000);这个写法不提倡
```

- 停止计时器

``` html
		<button>点我就不炸了</button>
		<script>
			var b=document.querySelector('button');
			var z=setTimeout(function(){
				console.log('炸啊');
			},5000);
			b.addEventListener('click',function(){
				clearTimeout(z);
			})
		</script>
```

- setInterval()定时器

```javascript
			// setInterval
			// setInterval(调用函数，间隔时间)
			// 每隔一段时间就去调用函数
			setInterval(function(){
				console.log('持续');
			},1000);
```

```html
		<button class="start">开始</button>
		<button class="stop">停止</button>
		<script>
			var start=document.querySelector('.start');
			var stop=document.querySelector('.stop');
			var t=null;//全局变量，null是个空值
			start.addEventListener('click',function(){
				t=setInterval(function(){
					console.log('lallalalalalal');
				},1000);
			})
			stop.addEventListener('click',function(){
				clearInterval(t);//停止计时器
			})
		</script>
```

### this指向问题

```javascript
			// 全局作用域或普通函数中this指向全局对象window（定时器里面的指向window）
			console.log(this);
			function fn(){
				console.log(this);
			}
			window.fn();
			window.setTimeout(function(){
				console.log(this);
			},1000);
			// 方法中谁调用this就指向谁
			var o={
				say:function(){
					console.log(this);// this指向o		
				}
			}
			o.say();
			// 构造函数中this指向构造函数的实例
			function FFF(){
				console.log(this);// this指向fun
			}
			var f=new FFF();
```

### location 对象

| location对象属性 |                返回值                |
| :--------------: | :----------------------------------: |
|    ==.href==     |          返回或设置整个URL           |
|      .host       |   返回主机(域名) www.bilibili.com    |
|      .port       |   返回端口号 如果没写返回空字符串    |
|    .pathname     |               返回路径               |
|   ==.search==    |               返回参数               |
|      .hash       | 返回片段 #后面的内容 常用于链接 锚点 |

- 方法

```html
		<button>点老子啊1</button>
		<button>点老子啊2</button>
		<button>刷新</button>
		<script>
			var btns=document.querySelectorAll('button');
			btns[0].addEventListener('click',function(){
				// assign 记录了浏览历史，可以回退
				location.assign('http://bilibili.com');
			})
			btns[1].addEventListener('click',function(){
				// replace 不记录浏览历史，不可以回退
				location.replace('http://bilibili.com');
			})
			btns[2].addEventListener('click',function(){
				// reload 刷新页面
				location.reload();
			})
		</script>
```

### navigator对象

navigator.useAgent 判断用户使用的哪个终端打开的页面

### history对象

- back() 后退
- forward()前进
- go(参数)参数为1前进1个页面，-1后退一个页面

## PC端网页特效

### offset

```html
		<style>
			*{
				margin: 0;
				padding: 0;
			}
			.father{
				width: 200px;
				height: 200px;
				background-color: pink;
				margin: 100px;
			}
			.son{
				width: 100px;
				height: 100px;
				background-color: purple;
				margin-left: 45px;
			}
		</style>
		<div class="father">
			<div class="son"></div>
		</div>
		<script>
			// offset 系列
			var ff=document.querySelector('.father');
			var ss=document.querySelector('.son');
			// 可以得到元素的偏移 位置 返回不带单位的数值
			console.log(ff.offsetTop);// 相对父元素的上方的偏移
			console.log(ff.offsetLeft);// 相对父元素的左侧的偏移
			// 它以带有定位的父亲为准 如果没有父亲或者父亲没有定位 则以body为准
			console.log(ss.offsetLeft);
			// 可以得到元素的大小 宽度 高度 是包含padding border的
			console.log(ff.offsetWidth);
			console.log(ff.offsetHeight);
			// 返回带有定位的父亲，否则返回body
			console.log(ss.offsetParent);
		</script>
```

### client

```html
		<style>
			.aaaaaa{
				width: 200px;
				height: 200px;
				background-color: pink;
				border: 10px solid red;
			}
		</style>
		<div class="aaaaaa"></div>
		<script>
			// client 宽度 不包含边框，包含padding
			var div=document.querySelector('div');
			console.log(div.clientWidth);
		</script>
```

### scroll

| scroll系列属性       | 作用                                             |
| -------------------- | ------------------------------------------------ |
| element.scrollTop    | 返回被卷去的上侧距离，返回数值不带单位           |
| element.scrollLeft   | 返回被卷去的左侧距离，返回值不带单位             |
| element.scrollWidth  | 返回自身实际的宽度，不含边框，返回会数值不带单位 |
| element.scrollHeight | 返回自身实际的高度，不含边框，返回数值不带单位   |

```html
		<style>
		        .la{
		            width: 200px;
		            height: 200px;
		            background-color: pink;
		            overflow: auto;
		        / / 滚动条
		        }
		</style>
		<div class="la">
		    我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		    我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		    我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		    我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		    我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		</div>
		<script>
		    var div = document.querySelector('div');
		    console.log('div.offsetHeight = ' + div.offsetHeight);
		    console.log('div.scrollHeight = ' + div.scrollHeight);
		    div.addEventListener('scroll',function () {
		        console.log('div.scrollTop = ' + div.scrollTop);
		    })
		</script>
		
```