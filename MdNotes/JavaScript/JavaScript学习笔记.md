# JavaScript学习笔记



## 1. 输入输出

- `alert()`弹框
- `console.log()`控制台打印
- `prompt()`输入框,取的值是字符型的



## 2. 变量

- `var age;`声明变量

 ```javascript
  var a=1,
      b=0,
      c=444;
  //可以这样简写
 ```



### 数据类型



#### 数字型

- infinity，无穷大，前面加-同理
- NaN，非数值
  - isNaN()用于判断非数字，是返回true



#### 字符串型

- 要用引号括住，单双都可以
- 嵌套的话要里外不同，'我是“狗“，单身狗'
- 里面可以写转义符 
- `console.log(str.length);`获取长度
- `console.log('lalal'+n);`拼接



#### 布尔型

- true 是 1
- false 是 0
- 这两个可以参与运算



#### undefind和null

```javascript
var a = undefined;
console.log(a+'ssss');//undefinedssss
console.log(a+1);//NaN

var b = null;
console.log(b+'ssss');//nullssss
console.log(b+1);//1
```



#### 获取数据类型

`console.log(typeof )`



#### 数据类型转换



##### To string 

| 方式             | 示例                   |
| :--------------- | ---------------------- |
| toString()       | alert(num.toString()); |
| String()强制转换 | alert(String(num));    |
| +号拼接          | alert(num+"字符串");   |



##### To number

| 方式                           | 案例                |
| ------------------------------ | ------------------- |
| parseInt(string)转成整数(取整) | parseInt('243')     |
| parseFloat(string)转成浮点数   | parseFloat('23.45') |
| Number()强制转换               | Number('123')       |
| js 隐式转换(- * /)             | '12'-0              |



##### To boolean

| 方式      | 示例            |
| :-------- | --------------- |
| Boolean() | Boolean('true') |

- 代表空、否定的转换为false
- 如''、0、NaN、null、undefined
- 其他值则转换为true



## 3. 运算符

- 不要直接判断两个浮点数是否相等



### 比较运算符

- `>=`
- ` === 或者 !==`全等，要求值和数据类型都一样

- 18=='18'是true
- 18==='18'是false



### 逻辑运算符

- &&     与
- ||      或
- !         非



## 4.流程控制

- if else，switch
- 条件?表达式1:表达式2
- 意思是如果条件真返回1，假返回2



## 5.循环

- for，while等
- continu，break等



## 6.数组



### 创建

- `var arr =new Array();`一个空数组
- `var arr =new Array(2);`一个数组，两个空元素
- `var arr =new Array(2,3);`[2,3]
- `var arr = [];`一个空数组
- `var a1 = [1,2,'iiii',true];`可以数据类型不同



### 长度

- `console.log(arr.length)`



### 新增元素

``` javascript
var arr = [1,2];
arr.length = 3;
console.log(arr[3]);
//输出的是undefined
```

==不要直接给数组名赋值，内容会全部没有了==



### 筛选数组

```javascript
var arr = [1,2,34,45,65,7657,345]
var b = [];
for(var i=0;i<arr.length;i++){
	if(arr[i]>=10){
    	b[b.length]=arr[i];
    }
}
console.log(b); 
```



## 7.函数

- 声明方式
  - `function fn(){}`
  - ` var fun = function(){};` 

- 注意点

```javascript
function getres(n1,n2){
	return [n1+n2,n1-n2,n1*n2,n1/n2];
}
//返回的是数组
```

- arguments的使用

```javascript
function fn(){
	console.log(arguments);//存储的是实参
	console.log(arguments.length);
	console.log(arguments[2]);
}
fn(1,2,3);
//是维数组
/*
	有数组的length属性
	按照索引方式存储
	没有真数组的方法pop(),push()
	可以用循环遍历
*/
```



## 8.对象(甭想了，你没有😭)



### 创建

```javascript
//用字面量
var obj = {
	//！注意：是逗号不是分号
	uname='你对象',
	age=18,
	sex='女',
	sayHi:function(){
		console.log('hi~~~~~~');
	}
}
//调用,两种
console.log(obj.uname);
console.log(obj['age']);
//调用方法
obj.saiHi();


//用new Object
var obj = new Object();
	obj.uname='新对象';
	obj.age=17;
	obj.sex='女';
	obj.saiHi = function(){
		console.log('hi~~~~~~');
	}


//用构造函数
//前两种一次就只能建立一个
//首字母大写
function Star(uname,age,sex){
	this.name=uname;
	this.age=age;
	this.sex=sex;
	this.sing=function(){
		console.log();
	}
}
var liu = new Star('刘',18,'男');
console.log(liu.name);
liu.sing('lalala');
```



### 遍历

```javascript
var obj = {
	uname='你对象',
	age=18,
	sex='女',
	sayHi:function(){
		console.log('hi~~~~~~');
	}
}
for(var k in obj){
	console.log(k);//输出的是属性名
	console.log(obj[k]);//输出的是属性值
}
```



## 9.内置对象



### 查文档

- [MDN](https://developer.mozilla.org/zh-CN/)



### Math对象

- 主要的还是自己查文档，以下为一些常用的

  ```javascript
  Math.PI//π啊
  Math.floor()//向下取整
  Math.ceil()//向上取整
  Math.round()//四舍五入（注意负数）
  Math.abs()//绝对值
  Math.max()//不瞎就行
  Math.min()//不瞎就行
  ```



### 日期对象



#### 基本

```javascript
var date1=new Date();
//直接返回的当前的时间
var date2=new Date(参数);
//最好使用字符串型
//'2022-4-1 8:8:8'
//2019,10,01
//数字型从0开始算的，所以不建议用
```

- 月份是0-11
- 星期是0-6



#### 返回时分秒

```javascript

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
```



#### 时间戳

- 时间戳就是距离1970年1月1日过去的总毫秒数



##### 用valueOf()   getTime();

``` javascript
var date = new Date();
console.log(date.valueOf());
console.log(date.getTime());
//上面两个都是时间戳
```



##### 简单写法(常用)

```javascript
var date1=+new Date();
console.log(date1);
```



##### 更简单的

`console.log(Date.now());`



### 数组对象



#### 检测是否为数组



##### instanceof

```javascript
var arr=[];
var obj={};
console.log(arr instanceof Array);//true
console.log(obj instanceof Array);//false
```



##### Array.isArray()

```javascript
Array.isArray([1, 2, 3]);  
// true
Array.isArray({foo: 123}); 
// false
Array.isArray("foobar");   
// false
Array.isArray(undefined);  
// false
```



#### 添删元素



##### 添加



###### push()和unshift()

```javascript
var sports = ["soccer", "baseball"];
var total = sports.push("football", "swimming");
//添加在末尾，返回的值是数组长度

console.log(sports); 
// ["soccer", "baseball", "football", "swimming"]

console.log(total);  
// 4

//unshift()同理，但是是在开头添加
```



###### apply()合并数组

```javascript
var vegetables = ['parsnip', 'potato'];
var moreVegs = ['celery', 'beetroot'];

// 将第二个数组融合进第一个数组
// 相当于 vegetables.push('celery', 'beetroot');
Array.prototype.push.apply(vegetables, moreVegs);

console.log(vegetables); 
// ['parsnip', 'potato', 'celery', 'beetroot']
```



##### 删除



###### pop()和shift()

```javascript
console.log(arr.pop());
console.log(arr);
//删除末尾，返回值是删除的元素
console.log(arr.shift());
console.log(arr);
//删除开头，返回值是删除的元素
```



#### 排序



##### 翻转reverse()

```javascript
const a = [1, 2, 3];
console.log(a); // [1, 2, 3]
a.reverse(); 
console.log(a); // [3, 2, 1]
```



##### 排序sort

```javascript
var arr = [1,67,3,4];
arr.sort(function(a,b){
    return a-b;//按照升序
});
console.log(arr);
```



#### 索引



##### indexOf()

```javascript
var array = [2, 5, 9];
array.indexOf(2);     // 0
//第一次出现的位置
//用lastIndexOf()就是最后一次出现的位置 （从后面开始查找）
array.indexOf(7);     // -1
//没有就返回-1
array.indexOf(9, 2);  // 2

array.indexOf(2, -1); // -1

array.indexOf(2, -3); // 0
```



#### 转化成字符串

```javascript
//直接使用toString()
var arr = [1,2,3];
console.log(arr.toString());

//使用jion(里面写分隔符)
var arr1=['red','green','blue'];
console.log(arr1.join());//逗号分隔
console.log(arr1.join('-'));//red-green-blue
console.log(arr1.join('&'));//red&green&blue
```



### 字符串对象

- 索引同数组



#### 根据位置返回字符



##### charAt(index)

- 返回指定位置的字符
- str.charAt(2)



##### charCodeAt(index)

- 返回相应索引号的ASCII值



##### str[index]

- 获取制定位置的字符
- HTML5新增



#### 操作方法

- caoncat(str1,str2,str3)	等效于+
- substr(start,length)	截取
- slice(start,end)     截取，取不到end
- substring(start,end)     截取，取不到end，基本同slice，但不接受负值
- str.replace(s, news)    替换，只替换第一个
- split('分隔符')   字符串转换成数组
  - `var str='red,ping'`
  - `console.log(str.split(','));`



## 10.Map对象



### 构造

```javascript
	let myMap1 = new Map([
      [1, 'one'],
      [2, 'two'],
      [3, 'three'],
      [1, 'four']
    ])
    let myMap2 = new Map()
```



### size属性 

- 获取元素个数 由于map的key不能相同，相同则会取后面的那个，所以myMap1的size为3

```javascript
    console.log(myMap1.size) //3
    console.log(myMap2.size) //0
```



### get方法

- 获取value

```javascript
	console.log(myMap1.get(1)) // four
```



### has方法

- 判断是否有对应的key

```javascript
	console.log(myMap1.has(1))// true
```



### keys 

- 返回按照顺序插入的每个元素的key值

```javascript
	let test = myMap1.keys()
	for(let key of test){
		console.log(key)
	}	 
```



### values方法

- 返回按照顺序插入的每个元素的value值得迭代器对象

```javascript
	let test2 = myMap1.values()
    for (let value of test2) {
      	console.log(value)
	}
//  four two three
//注意上面的打印顺序，可以看到构造方法里先出现的key在迭代对象里也先出现，而不是有重复的话先删除再添加，而是重复的话直接覆盖对应的value
```



###  set方法

-  往map里插入或者覆盖对应的key和value 

```javascript
	myMap2.set(6,6)
```



###  entries方法

- 返回包含[key,value]的迭代器对象

```javascript
	const iterator1 = myMap1.entries()
    for (const item of iterator1) {
      	console.log(typeof item,Array.isArray(item), item)
	}
```



### delete方法

- 删除对应的key 同时返回删除之前是否包含该元素

```javascript
	const map1 = new Map();
	map1.set('bar', 'foo');

	console.log(map1.delete('bar'));
	// expected result: true
```



### clear方法

- 清空map对象

```javascript
	myMap1.clear()
```

