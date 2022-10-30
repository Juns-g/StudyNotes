# 深入JS



## 函数式编程

### 前置知识

#### 函数是一等公民

- 函数可以存储在变量中
- 函数可以作为参数
- 函数作为返回值

```javascript
// 把函数赋值给变量
let fn = function () {
  console.log("hello first-class function");
};
fn();

// 一个示例
const BlogControl = {
  index(post) {
    return Views.index(post);
  },
  show(post) {
    return Views.shoe(post);
  },
};

// 优化
const BlogControl2 = {
  // 赋值的是方法本身，而不是调用
  index: Views.index,
  show: Views.show,
};
```

### 高阶函数

- 可以把函数作为参数传递给另一个函数

```javascript
// 高阶函数-函数作为参数

function forEach(array, fn) {
  for (let i = 0; i < array.length; i++) {
    fn(array[i]);
  }
}

// 测试forEach
let arr = [3, 4, 6, 83, 2];

forEach(arr, function (item) {
  console.log(item);
});

// filter
function ffilter(array, fn) {
  let res = [];
  for (let i = 0; i < array.length; i++) {
    if (fn(array[i])) res.push(array[i]);
  }
  return res;
}

// 测试filter
let r = ffilter(arr, function (item) {
  return item % 2 === 0;
});
console.log(r);

```

- 可以把函数作为另一个函数的返回结果

```js
// 高阶函数-函数作为返回值

function makeFn() {
  let msg = "hello function";
  return function () {
    console.log(msg);
  };
}

// const fn = makeFn();
// fn();

// makeFn()();
// 一个()是返回那个函数，两个()才是调用那个函数

// 写一个once函数，只执行一次的函数
function once(fn) {
  let done = false;
  return function () {
    if (!done) {
      done = true;
      return fn.apply(this, arguments);
    }
  };
}

let pay = once(function (money) {
  console.log(`支付了：${money} RMB`);
});

pay(5);
pay(5);
pay(5);
pay(5);
pay(5);
// 只会输出一次  支付了：5 RMB
```

















## JS异步编程





## 手写Promie源码

