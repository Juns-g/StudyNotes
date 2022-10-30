# HTML5

1. ```html
   <h1>一级标题，可以从1到6</h1>
   
   <p>段落标签，文字可以独占一行</p>
   
   <i>斜体</i>
   
   <b>加粗</b>
   
   <br>换行
   
   <hr>水平线
   
   &nbsp;空格
   
   <del>文字加删除线</del>
   
   <sup>2</sup>加上标
   
   <u></u>加下划线
   
   <center></center>居中
   ```
   
2. ```html
   <a href="http...">文字，超链接</a>（当前页面跳转）
   <a href="http..." target="_blank">文字，超链接</a>（新页面跳转）
   
   <img src="">图片
   <img src=""title="鼠标画上去的提示" alt="图片加载失败的文字">
   
   <ul><li>小圆点项目，无序列表</li></ul>
   <ul type="disc"><li>实心圆</li></ul>
   <ul type="circle"><li>空心圆</li></ul>
   <ul type="square"><li>方块</li></ul>
   
   <ol><li>有数字，有序列表</li></ol>
   <ol type="1"><li>数字</li></ol>
   <ol type="a"><li>英文</li></ol>
   <ol type="I"><li>罗马数字</li></ol>
   ```
   
3. ```html
    <table>
        <tr></tr>一行
        <td></td>一个单元格
        
        <col>一列
        
   </table>表格
   
   border="1px"表格边框属性
   cellspacing="0"单元格的空隙
   align="center"对齐方式
   
   <td rowspan="4">照片</td>占4行
   <td colspan="3"></td>占三列
   
   <th>相当于加粗水平居中的td</th>
   <colgroup span="6" width="100px"></colgrou>将前六列设置宽度为100px
   
   ```

4. ```html
   <form action="这里是表单提交到的链接地址"></form>
   
   <input type="text" name="loginname">input要有name属性才可提交
   
   <input type="submit" name="" id="" value="提交" />value是按钮的文字
   
   
   ```

5. ```html
     get请求和post请求的区别
   1.get请求通常表示获取数据
   2.post请求通常表示提交数据
   3.get请求发送的数据都写在地址栏上，用户可见
   4.post请求发送的数据用户不可见
   5.get请求不能提交大量数据，但post可以，因此不要混用
   <form action="这里是表单提交到的链接地址"method="post"></form>
   ```

6. ```html
   <span style="background-color: gray;color: white;font-size: 24px;">个人简介</span>span容器，相当于加上边框
   ```

7. <img src="C:\Users\123\AppData\Roaming\Typora\typora-user-images\image-20220304212929357.png" alt="image-20220304212929357" style="zoom: 80%;" />

8. ```html
     <div>
         容器，7中的为样式
     </div>
     ```

9. ```html
     CSS选择器
     <style type="text/css">
     html  标签选择器
         {background-color:#ddd;}
     body  标签选择器
         {argin: 0;}
     #navigation  id选择器
         {height: 80px;line-height: 80px;text-align: center;}
     #bottom
         {height: 40px; line-height: 80px;text-align: center;font-size: 14px;color: grey;}
     .nav  类别选择器
         {text-decoration: none;color: black;margin: 0 15px;}
     #banner img
         {width:100%}
     		</style>
     行内样式的优先级高于内部样式表
     ```

10. ```html
     <!DOCTYPE html>
     <html>
     	<head>
     		<meta charset="utf-8" />
     		<meta name="viewport" content="width=device-width, initial-scale=1">
     		<title></title>
     		<style type="text/css">
     			#p1{
     				color: blue;	/* id选择器优先级第二 100*/
     			}
     			*{
     				color: orange;		/* 通用选择器优先级倒一0 */
     			}
     			.pp{
     				color: green;		/* 类选择器优先级第三 10*/
     			}
     			p{
     				color: red;			/* 标签选择器优先级第四 1*/
     			}
     		</style>
     		
     	</head>
     	<body>
     		
     		<p class="pp"id="p1"style="color: slateblue;">这是个啥色啊</p>
     		<!-- 行内样式优先级最高1000 -->
     	</body>
     </html>
     ```

11. ```html
      css文本属性
      <!DOCTYPE html>
      <html>
      	<head>
      		<meta charset="utf-8">
      		<title></title>
      		<style type="text/css">
      			.p1{color: red;}
      			.p2{font-family: "blackadder itc";}
      			.p3{font-size: 20px;}
      			.p4{font-weight: bold;}
      			.p5{font-style: italic;}
      			.p6{text-indent: 60px;}
      			.p7{text-align: center;}
      			.p8{line-height: 100px;}
      			.p9{height: 100px;background-color: gray;line-height: 100px;}
      			.p10{text-decoration: underline;}
      			
      		</style>
      	</head>
      	<body>
      		<ul>
      			<li class="p1">文字颜色</li>
      			<li class="p2">字体/文字类型</li>
      			<li class="p3">文字大小</li>
      			<li class="p4">加粗</li>
      			<li class="p5">倾斜</li>
      			<li class="p6">首行缩进</li>
      			<li class="p7">水平对齐方式</li>
      			<li class="p8">行高</li>
      			<li class="p9">垂直居中，背景颜色</li>
      			<li class="p10">文本修饰</li>
      			
      		</ul>
      	</body>
      </html>
      
      ```

12. 

