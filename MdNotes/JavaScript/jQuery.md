# jQuery

==jq已经落后很久了，不建议学习！==

> jquery是一个专注于DOM的类库，简化了DOM操作，提高效率
>
> [jQuery官网下载](https://jquery.com/download/)


##  基础

### 选择器

- jQuery的选择器类似于原生的querySelectAll方法

```html
		<h3>我是h3 <span>我是span</span></h3>
		<p>我是p</p>
		<p class="lei">我是类</p>
		<p id="aidi">我是id<span>我是p里面的span</span></p>
		<script>
			// 标签选择器
			$('p').css('background-color','pink');
            // DOM的写法  document.querySelector('p').style.backgroundColor='pink';
            
			// 类选择器
			$('.lei').css('background-color','green');			
            
			// id选择器
			$('#aidi').css('background-color','red');			
            
			// 后代选择器
			$('p span').css('background-color','blue');
		</script>
```


| 选择器                                                       | 实例                       | 选取                                       |
| :----------------------------------------------------------- | :------------------------- | :----------------------------------------- |
| [*](https://www.w3school.com.cn/jquery/selector_all.asp)     | $("*")                     | 所有元素                                   |
| [#*id*](https://www.w3school.com.cn/jquery/selector_id.asp)  | $("#lastname")             | id="lastname" 的元素                       |
| [.*class*](https://www.w3school.com.cn/jquery/selector_class.asp) | $(".intro")                | 所有 class="intro" 的元素                  |
| [*element*](https://www.w3school.com.cn/jquery/selector_element.asp) | $("p")                     | 所有 <p> 元素                              |
| .*class*.*class*                                             | $(".intro.demo")           | 所有 class="intro" 且 class="demo" 的元素  |
|                                                              |                            |                                            |
| [:first](https://www.w3school.com.cn/jquery/selector_first.asp) | $("p:first")               | 第一个 <p> 元素                            |
| [:last](https://www.w3school.com.cn/jquery/selector_last.asp) | $("p:last")                | 最后一个 <p> 元素                          |
| [:even](https://www.w3school.com.cn/jquery/selector_even.asp) | $("tr:even")               | 所有偶数 <tr> 元素                         |
| [:odd](https://www.w3school.com.cn/jquery/selector_odd.asp)  | $("tr:odd")                | 所有奇数 <tr> 元素                         |
|                                                              |                            |                                            |
| [:eq(*index*)](https://www.w3school.com.cn/jquery/selector_eq.asp) | $("ul li:eq(3)")           | 列表中的第四个元素（index 从 0 开始）      |
| [:gt(*no*)](https://www.w3school.com.cn/jquery/selector_gt.asp) | $("ul li:gt(3)")           | 列出 index 大于 3 的元素                   |
| [:lt(*no*)](https://www.w3school.com.cn/jquery/selector_lt.asp) | $("ul li:lt(3)")           | 列出 index 小于 3 的元素                   |
| :not(*selector*)                                             | $("input:not(:empty)")     | 所有不为空的 input 元素                    |
|                                                              |                            |                                            |
| [:header](https://www.w3school.com.cn/jquery/selector_header.asp) | $(":header")               | 所有标题元素 <h1> - <h6>                   |
| [:animated](https://www.w3school.com.cn/jquery/selector_animated.asp) |                            | 所有动画元素                               |
|                                                              |                            |                                            |
| [:contains(*text*)](https://www.w3school.com.cn/jquery/selector_contains.asp) | $(":contains('W3School')") | 包含指定字符串的所有元素                   |
| [:empty](https://www.w3school.com.cn/jquery/selector_empty.asp) | $(":empty")                | 无子（元素）节点的所有元素                 |
| :hidden                                                      | $("p:hidden")              | 所有隐藏的 <p> 元素                        |
| [:visible](https://www.w3school.com.cn/jquery/selector_visible.asp) | $("table:visible")         | 所有可见的表格                             |
|                                                              |                            |                                            |
| s1,s2,s3                                                     | $("th,td,.intro")          | 所有带有匹配选择的元素                     |
|                                                              |                            |                                            |
| [[*attribute*\]](https://www.w3school.com.cn/jquery/selector_attribute.asp) | $("[href]")                | 所有带有 href 属性的元素                   |
| [[*attribute*=*value*\]](https://www.w3school.com.cn/jquery/selector_attribute_equal_value.asp) | $("[href='#']")            | 所有 href 属性的值等于 "#" 的元素          |
| [[*attribute*!=*value*\]](https://www.w3school.com.cn/jquery/selector_attribute_notequal_value.asp) | $("[href!='#']")           | 所有 href 属性的值不等于 "#" 的元素        |
| [[*attribute*$=*value*\]](https://www.w3school.com.cn/jquery/selector_attribute_end_value.asp) | $("[href$='.jpg']")        | 所有 href 属性的值包含以 ".jpg" 结尾的元素 |
|                                                              |                            |                                            |
| [:input](https://www.w3school.com.cn/jquery/selector_input.asp) | $(":input")                | 所有 <input> 元素                          |
| [:text](https://www.w3school.com.cn/jquery/selector_input_text.asp) | $(":text")                 | 所有 type="text" 的 <input> 元素           |
| [:password](https://www.w3school.com.cn/jquery/selector_input_password.asp) | $(":password")             | 所有 type="password" 的 <input> 元素       |
| [:radio](https://www.w3school.com.cn/jquery/selector_input_radio.asp) | $(":radio")                | 所有 type="radio" 的 <input> 元素          |
| [:checkbox](https://www.w3school.com.cn/jquery/selector_input_checkbox.asp) | $(":checkbox")             | 所有 type="checkbox" 的 <input> 元素       |
| [:submit](https://www.w3school.com.cn/jquery/selector_input_submit.asp) | $(":submit")               | 所有 type="submit" 的 <input> 元素         |
| [:reset](https://www.w3school.com.cn/jquery/selector_input_reset.asp) | $(":reset")                | 所有 type="reset" 的 <input> 元素          |
| [:button](https://www.w3school.com.cn/jquery/selector_input_button.asp) | $(":button")               | 所有 type="button" 的 <input> 元素         |
| [:image](https://www.w3school.com.cn/jquery/selector_input_image.asp) | $(":image")                | 所有 type="image" 的 <input> 元素          |
| [:file](https://www.w3school.com.cn/jquery/selector_input_file.asp) | $(":file")                 | 所有 type="file" 的 <input> 元素           |
|                                                              |                            |                                            |
| [:enabled](https://www.w3school.com.cn/jquery/selector_input_enabled.asp) | $(":enabled")              | 所有激活的 input 元素                      |
| [:disabled](https://www.w3school.com.cn/jquery/selector_input_disabled.asp) | $(":disabled")             | 所有禁用的 input 元素                      |
| [:selected](https://www.w3school.com.cn/jquery/selector_input_selected.asp) | $(":selected")             | 所有被选取的 input 元素                    |
| [:checked](https://www.w3school.com.cn/jquery/selector_input_checked.asp) | $(":checked")              | 所有被选中的 input 元素                    |

### jQuery对象

- jQuery对象和DOM对象语法不能混用

```html
		<li>一</li>
		<li>二</li>
		<li>三</li>
		<li>四</li>
		<script>
			// 打印dom和jQ对象的区别
			let li = document.querySelector('li');// 获取的只有第一个li
			console.log('li:', li);
			let $li = $('li');// 获取的是所有的li
			console.log('$li:', $li);
            
			// jQ对象的方法
			$li.css('background-color','hotpink');// 所有的li都变色
            
			// dom对象转jQ对象
			let $li2=$(li);
			$li2.css('background-color','skyblue');// 第一个li变色
		</script>
```

### 链式编程

```html
		<input type="text" id="1">
		<input type="text" id="2">
		<input type="text" id="3">
		<script>
			// 普通方法绑定事件
			$('#1').focus(function(){
				console.log('获得焦点');
			});
			$('#1').blur(function(){
				console.log('失去焦点');
			});
            
			// 链式编程绑定事件
			$('#2')
			.focus(function(){
				console.log('获得焦点');
			})
			.blur(function(){
				console.log('失去焦点');
			})
			.change(function(){
				console.log('内容改变');
			})
            
			// 测试jQuery方法的返回值
			let $t1=$('#3');
			let $t2=$t1.focus(function(){
				console.log('获得焦点');
			})
			console.log($t1 === $t2);// true
		</script>
```

## 常用API

### 过滤方法

```html
		<h3>过滤方法</h3>
		<p>对获取的元素进行过滤，返回的依旧是jQuery对象</p>
		<ul>
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
		</ul>
		<script>
			// first获取第一个元素
			$('li').first().css('background-color', 'red');
            
			// last获取最后一个元素
			$('li').last().css('background-color', 'blue');
            
			// eq(索引值)获取对应位置的元素，索引从零开始
			// 如果是负数，则从集合中的最后一个元素往回计数。
			$('li').eq(1).css('background-color', 'yellow');
			$('li').eq(-2).css('background-color', 'yellow');
			// -1是最后一个，-2是倒数第二个
		</script>
```

### 样式方法

```html
		<style>
			#ceshi{
				width: 200px;
				height: 200px;
				margin-top: 20px;
				border: 1px solid #000;
			}
		</style>
		<div id="ceshi"></div>
		<script>
			// 键值对设置
			$('#ceshi').css('background-color', 'pink');
			$('#ceshi').css('border', '10px solid orange');
			$('#ceshi').css('width', '250px');
			$('#ceshi').css('height', 250);// 默认单位就是px
            
			// 对象方式设置
			$('#ceshi').css({
				backgroundColor: 'skyblue',
				border: '10px solid yellowgreen',
				width: 100,
				height: 100
			})
            
			// 样式获取
			let w=$('#ceshi').css('width');
			console.log('width:',w);
		</script>
```

### 属性操纵

```html
		<a href="#">测试链接</a>
		<img src="">
		<script>
			// 赋值
			$('a').attr('href','https://www.zhihu.com/');
			$('img').attr('src','https://img.wang.232232.xyz/img/2022/07/03/755a7cbada748f187e3100f5a871ae5d.th.png');
			$('img').attr('info','这是info');
			
			// 取值
			let h=$('img').attr('src');
			console.log(h);
			
			// 删除
			$('a').removeAttr('href');
		</script>
```

### value操纵

```html
			<input type="text" class="t">
			<script>
				// 赋值
				$('.t').val('我是通过jq赋值的文字');
				
				// 取值
				$('.t').blur(function(){
					console.log('value:',$('.t').val());
				})
			</script>
```

### 查找方法

```html
			<div class="container">
			  <h4>课程列表</h4>
			  <ul class="course">
			    <li>html</li>
			    <li>css</li>
			    <li>javascript</li>
			  </ul>
			  <h4>校区列表</h4>
			  <ul class="campus">
			    <li class="bj">北京校区</li>
			    <li class="sh">上海校区</li>
			    <li class="gz">广州校区</li>
			    <li class="sz">深圳校区</li>
			  </ul>
			</div>
			<script>
			  // 1. 父元素 parent
			  // $('.course')
			  //   .parent()
			  //   .css('backgroundColor', 'pink')
			
			  // 2. 子元素 children
			  $('.course')
			    .children()
			    .css('backgroundColor', 'skyblue')
			  $('.campus')
			    .children('.bj')
			    .css('backgroundColor', 'pink')
			
			  // 3.  兄弟元素 siblings
			  $('.sz')
			    .siblings()
			    .css('color', 'red')// 不包括他自己
			  $('.sz')
			    .siblings('.gz')
			    .css('backgroundColor', 'yellowgreen')
			
			  // 4. 后代元素 find
			  $('.container')
			    .find('h4')
			    .css('backgroundColor', 'yellowgreen')
			
			  $('.container')
			    .find('li')
			    .css('border', '10px solid orange')
			</script>
```

### 操纵类名

```html
			<style>
			  .test {
			    width: 200px;
			    height: 150px;
			    background-color: green;
			  }
			  .active {
			    background-color: red;
			    border: 5px solid skyblue;
			  }
			</style>
			<!-- 操纵的盒子 -->
			<div class="test"></div>
			<hr />
			<!-- 测试用按钮 -->
			<button id="add" class="layui-btn layui-btn-radius">添加类名</button>
			<button id="remove" class="layui-btn layui-btn-radius layui-btn-normal">移除类名</button>
			<button id="has" class="layui-btn layui-btn-radius layui-btn-warm">判断类名</button>
			<button id="toggle" class="layui-btn layui-btn-radius layui-btn-danger">切换类名</button>
			<script>
			  // 1.  添加类名
			  $('#add').click(function () {
			    $('.test').addClass('active')
			  })
			
			  // 2. 移除类名
			  $('#remove').click(function () {
			    $('.test').removeClass('active')
			  })
			
			  // 3. 判断类名
			  $('#has').click(function () {
			    let res = $('.test').hasClass('active')
			    console.log('res:', res)
			  })
			
			  // 4. 切换类名
			  $('#toggle').click(function () {
			    $('.test').toggleClass('active')
			  })
			</script>
```



## 动画

- 显示，隐藏动画
  - 显示`$('选择器').show(持续时间)`
  - 隐藏`$('选择器').hide(持续时间)`
  - 切换`$('选择器').toggle(持续时间)`
- 淡入淡出动画
  - 淡入`fadeIn(speed,回调函数);`
  - 淡出`fadeOut(speed,回调函数);`
  - 切换`fadeToggle(speed,回调函数);`
  - 渐变至透明度`fadeTo(speed,透明度0-1,回调函数);`
- 展开收起动画
  - 展开`slideDown()`
  - 收起`slideUp()`
  - 切换`slideToggle()`

