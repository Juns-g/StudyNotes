# TypeScript学习

==很简单的一小部分，实际使用还需要看文档和更多的学习==

> 链接们：
>
> - [中文TS使用指南](http://www.patrickzhong.com/TypeScript/)
> - [小白都能学会的ts入门指南](https://zhuanlan.zhihu.com/p/365352759)

## 原始数据类型和Any类型

```typescript
let isdone: boolean;
// isdone = [222];// 报错

let age: number;
age = 11;

let firstName: string = 'fgeg';
let secondName: string = `hello,${firstName}`// 模板字符串

let u: undefined = undefined;
let n: null = null;
// todo:了解这俩的区别，面试会问
// 这俩是别的类型的子类型
let nnn: number = undefined;

let notSure: any = 111;//避免变成anyscript
notSure = 'sdfs';
notSure = true;
```



### JS中undefined和nul的区别

参考链接：[区别](https://www.cnblogs.com/redFeather/p/16494141.html)

1. 实际没大差别，都表示某个变量的值是空
2. 在if语句中，都会被自动转为false，相等运算符甚至直接报告两者相等。

```javascript
if(!undefined)
   console.log('undefined is false')
//undefined is false


if(!null)
   console.log('null is false')
//null is false

undefined == null   //true
```

3. 但是：

	undefined === null //false

	null和undefined 两者相等，但是当两者做全等比较时，两者又不等。

	原因：

	null： object类型，代表“空值”，代表一个空对象指针

	undefined： undefined类型

> ## 四、目前的用法
>
> null和undefined基本是同义的，只有一些细微的差别。
>
> （一）null表示“没有对象”，即该处不该有值。典型用法是：
>
> 1、作为函数的参数，表示该函数的参数不是对象。
>
> 2、作为对象原型链的终点。
>
> 
>
> ```
> Object.getPrototypeOf(Object.prototype)
> 
> //null
> ```
>
> （二）undefined表示“缺少值”，即此处应该有一个值，但是还未定义。典型用法：
>
> 1、变量被声明了但未被赋值，就等于undefined
>
> 2、调用函数时，应提供的参数未提供，该参数等于undefined
>
> 3、对象没有赋值的属性，该属性的值为undefined
>
> 4、函数没有返回值时，默认返回undefined
>
> 
>
> ```
> var i;
> i   //undefined
> 
> function f(x){
>    console.log(x)      
> }
> f()   //undefined
> 
> var o=new Object();
> o.p   //undefined
> 
> var x=f(x)
> x   //undefined
> ```
>
> ##  五、总结区别
>
> 1、undefined不是关键字，而null是关键字;
>
> 　　var undefined="" //undefined
>
> 　　var null=""  //会报错
>
> 2、undefined和null被转换为布尔值的时候，两者都为false;
>
> 3、undefined在和null进行==比较时两者相等，全等于比较时两者不等
>
> 4、使用Number()对undefined和null进行类型转换时前者为NaN，后者为0
>
> 5、undefined本质上是window的一个属性，而null是一个对象；



## 数组和元组

```typescript
let arrOfNumbers: number[] = [1, 2, 3]//内部只能是数字
arrOfNumbers.push(32);
console.log(arrOfNumbers);

function test() { console.log(arguments); }
test();

let user: [String, number] = ['fsdf', 222];//只能是规定的格式
// 但是可以添加，本质还是数组
user.push('sdfsd');// 但是只能添加规定那俩种类型
```



## interface接口基础

不存在于JS中的概念，起约束作用

```typescript
interface Iperson {// 建议命名最前面加上I作为提示
	readonly id: Number;// 只读属性，不可改
	name: string;// 必须有的属性
	age: number;
	sex?: string;// 可选属性
}

let viking: Iperson = {
	id: 1,
	name: 'viking',
	age: 20,
	sex: 'man',
}
// viking.id = 23;// 报错
```



## Function函数

```typescript
const add = (x: number, y: number, z?: number): number => {
	// 可选参数放最后
	if (typeof z === 'number') return x + y + z;
	else return x + y;
}
let result = add(1, 3);
console.log(result);

interface ISum {
	(x: number, y: number, z?: number): number;
}

let add2: ISum = add;
```



## 类型推论联合类型和类型断言

```typescript
// type inference
// 没有写类型的话，ts会推测类型
let str = '232';
// str=111;// 报错

// union types
// 联合类型，一个变量可以是多种类型
let numberOrString: number | string;
numberOrString = '2';
numberOrString = 234;
// numberOrString.length// 报错
// numberOrString.toString()// 只能用共有的

// 类型断言，意思就是自己确定类型，不让他报错
function getLength(input: string | number) {
	let str = input as string;//就是认为他是string
	if (str.length) return str.length;
	else {
		let num = input as number;
		return num.toString().length;
	}
}
console.log(getLength('dsfs'));
console.log(getLength(23423));

// type guard
// 在不同的分支中，智能缩小范围
function getLength2(input: string | number) {
	if (typeof input === 'string') return input.length;
	else return input.toString().length;
}
```



## enums枚举

```typescript
// 数字枚举
enum Direction {
	Up = 1,
	Down,
	Left,
	Right,
}
// 下面的成员的值是递增的
console.log(Direction.Up);// 1
console.log(Direction.Down);// 2
console.log(Direction.Left);// 3
console.log(Direction.Right);// 4
console.log(Direction[1]);// Up

// 字符串枚举,需要初始化
enum dddd {
	Up = 'UP',
	Down = 'DOWN',
	Left = 'LEFT',
	Right = 'RIGHT',
}
console.log(dddd.Up);// UP
console.log(dddd.Down);// DOWN
console.log(dddd.Left);// LEFT
console.log(dddd.Right);// RIGHT
console.log(dddd['Up']);// UP

// 应用场景：一般是根据后台返回的状态在前台做处理
```



## generics泛型

```typescript
function echo<T>(arg: T): T {
	return arg;
	// 相当于指定这些都是同一种类型的变量
}
const res = echo(true);

function swap<T, U>(tuple: [T, U]): [U, T] {
	return [tuple[1], tuple[0]];
}
console.log(swap(['sdfsdf', 234234]));

function echoWithArr<T>(arg: T[]): T[] {
	// 这样的解决方法并不好
	console.log(arg.length);
	return arg;
}
const arrs = echoWithArr([1, 2, 3]);

interface IWithLength {
	length: number;
}
function echoWithLength<T extends IWithLength>(arg: T): T {
	// 使用extends满足条件
	console.log(arg.length);
	return arg;
}
const strr = echoWithLength('dsfs');
const obj = echoWithLength({ length: 323 });
const arr2 = echoWithLength([3, 4, 6]);
```



```typescript
class Queue<T> {
	private data = [];
	push(it: T) {
		return this.data.push(it);
	}
	pop(): T {
		return this.data.shift();
	}
}
const q = new Queue<number>();
q.push(1);
// q.push('str');
console.log(q.pop().toFixed());

interface KeyPair<T, U> {
	key: T
	value: U
}
let kp1: KeyPair<number, string>
let kp2: KeyPair<string, number>
let arr: number[] = [1, 2, 3];
let arrTwo: Array<number> = [2, 3, 4]
```

## 类型别名

```typescript
let sum: (x: number, y: number) => number;
const r = sum(1, 2);
type p = (x: number, y: number) => number;
// 可以简写
let sum2: p;
const r2 = sum2(2, 3);

type son = string | number;
let r3: son = '2342';
r3 = 324;

const s: 'name' = 'name';//限定s只能是'name'这个字符串
const nx: 1 = 1;

type dd = 'Up' | 'Down';
let toWhere: dd = 'Down';

// 交叉类型
interface IName {
	name: string;
}
type IPerson = IName & { age: number }
let person: IPerson = { name: 'fds', age: 32 }
```





## 声明文件

```typescript
// axios.get('url')// 这样就有提示了
// axios.post('url', { name: 'fdsf' })

// https://www.typescriptlang.org/dt/search?search=  下载库的链接
import axios from 'axios'
// hbuilderx  alt加单击可以打开文件
axios.get('url')
// axios.post()

// jq不用引入，可以直接使用
```



.d.ts

```typescript
type IOp = 'plus' | 'minus'
// type ICaculator = (op: IOp, nums: number[]) => number
interface ICaculator {
	(op: IOp, nums: number[]): number;
	plus: (nums: number[]) => number;
	minus: (nums: number[]) => number;
}
declare const caculator: ICaculator

export default caculator
```



ts

```typescript
import caculator from './caculator';
caculator('plus', [1, 2])
caculator.plus([1, 2])
```































