# Vue

> ## 一些链接：
>
> - [Vue中Vuex的使用](https://blog.csdn.net/lyyrhf/article/details/115217564?spm=1001.2014.3001.5502)
> - [Vue的脚手架开发详细笔记](https://blog.csdn.net/lyyrhf/article/details/115065386?spm=1001.2014.3001.5502)
> - [Vue的组件化开发详细笔记](https://blog.csdn.net/lyyrhf/article/details/114977307?spm=1001.2014.3001.5502)
> - [Vue的MVVM架构及语法超详细笔记](https://blog.csdn.net/lyyrhf/article/details/114976702?spm=1001.2014.3001.5502)
> - [Vue3.x知识图谱](https://gitee.com/jishupang/vue3-knowledge-map)
> - [VUE组件汇总](https://juejin.cn/post/6844903603421839368)
> - [6个实用的vue组件库](https://juejin.cn/post/7121198442105274405)
> - [vue3新文档](https://vuejs.org/)
> - [尚硅谷vue3笔记](https://wekenw.gitee.io/vuenote/)



## 安装配置

### 对于学习

可以这样使用最新版本：

```html
<script src="https://unpkg.com/vue@next"></script>
```

### npm

在用 Vue 构建大型应用时推荐使用 npm 安装

```sh
# 最新稳定版
$ npm install vue@next
```

对于 Vue 3，你应该使用 `npm` 上可用的 Vue CLI v4.5 作为 `@vue/cli`。

```sh
npm install -g @vue/cli
```

### Vite

[Vite](https://cn.vitejs.dev/) 是一个 web 开发构建工具，由于其原生 ES 模块导入方式，可以实现闪电般的冷服务器启动。

通过在终端中运行以下命令，可以使用 Vite 快速构建 Vue 项目。

使用 npm：

```sh
# npm 6.x
$ npm init vite@latest <project-name> --template vue

# npm 7+，需要加上额外的双短横线
$ npm init vite@latest <project-name> -- --template vue

$ cd <project-name>
$ npm install
$ npm run dev
```

或者 pnpm:

```sh
$ pnpm create vite <project-name> -- --template vue
$ cd <project-name>
$ pnpm install
$ pnpm dev
```



## Vue3部分



### Vue3响应式原理

实现原理:

- 通过Proxy（代理）: 拦截对象中任意属性的变化, 包括：属性值的读写、属性的添加、属性的删除等。
- 通过Reflect（反射）: 对源对象的属性进行操作。
- MDN文档中描述的Proxy与Reflect：
	- Proxy：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy
	- Reflect：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect

```js
new Proxy(data, {
  // 拦截读取属性值
  get(target, prop) {
    return Reflect.get(target, prop);
  },
  // 拦截设置属性值或添加新属性
  set(target, prop, value) {
    return Reflect.set(target, prop, value);
  },
  // 拦截删除属性
  deleteProperty(target, prop) {
    return Reflect.deleteProperty(target, prop);
  },
});

proxy.name = "tom";
```



#### Vue2的响应式

- 实现原理：

	- 对象类型：通过`Object.defineProperty()`对属性的读取、修改进行拦截（数据劫持）。

	- 数组类型：通过重写更新数组的一系列方法来实现拦截。（对数组的变更方法进行了包裹）。

		```js
		Object.defineProperty(data, 'count', {
		    get () {}, 
		    set () {}
		})
		```

- 存在问题：

	- 新增属性、删除属性, 界面不会更新。
	- 直接通过下标修改数组, 界面不会自动更新。



### reactive对比ref

- 从定义数据角度对比：
	- ref用来定义：**基本类型数据**。
	- reactive用来定义：**对象（或数组）类型数据**。
	- 备注：ref也可以用来定义**对象（或数组）类型数据**, 它内部会自动通过`reactive`转为**代理对象**。
- 从原理角度对比：
	- ref通过`Object.defineProperty()`的`get`与`set`来实现响应式（数据劫持）。
	- reactive通过使用**Proxy**来实现响应式（数据劫持）, 并通过**Reflect**操作**源对象**内部的数据。
- 从使用角度对比：
	- ref定义的数据：操作数据**需要**`.value`，读取数据时模板中直接读取**不需要**`.value`。
	- reactive定义的数据：操作数据与读取数据：**均不需要**`.value`。



> 个人建议的写法是这样，最后return他的data
>
> ```js
> let data = reactive({
>   person: {},
>   student: {},
> });
> ```



### setup的两个注意点

- setup执行的时机
	- 在beforeCreate之前执行一次，this是undefined。
- setup的参数
	- props：值为对象，包含：组件外部传递过来，且组件内部声明接收了的属性。
	- context：上下文对象
		- attrs: 值为对象，包含：组件外部传递过来，但没有在props配置中声明的属性, 相当于 `this.$attrs`。
		- slots: 收到的插槽内容, 相当于 `this.$slots`。
		- emit: 分发自定义事件的函数, 相当于 `this.$emit`。



### 计算属性与监视



#### 1.computed函数

- 与Vue2.x中computed配置功能一致

- 写法，但是name1和name2中间的空格删掉的话会出bug

	```js
	import { reactive, computed } from "vue";
	export default {
	  name: "Demo",
	  setup() {
	    let person = reactive({
	      name1: "张",
	      name2: "三",
	    });
	    // 简写，不考虑计算属性被修改的情况
	    /* person.fullName = computed(() => {
	      return person.name1 + " " + person.name2;
	    }); */
	
	    //完整写法，考虑读写
	    person.fullName = computed({
	      get() {
	        return person.name1 + " " + person.name2;
	      },
	      set(value) {
	        const nameArr = value.split(" ");
	        person.name1 = nameArr[0];
	        person.name2 = nameArr[1];
	      },
	    });
	    return {
	      person,
	    };
	  },
	};
	```



#### 2.watch函数

- 与Vue2.x中watch配置功能一致

- 两个小“坑”：

	- 监视reactive定义的响应式数据时：oldValue无法正确获取、强制开启了深度监视（deep配置失效）。
	- 监视reactive定义的响应式数据中某个属性时：deep配置有效。

	```js
	// 1. 监视ref定义的一个响应式数据
	watch(
	  sum,
	  (newValue, oldValue) => {
	    console.log(newValue, oldValue);
	  },
	  { immediate: true }
	);
	
	// 2. 监视ref定义的多个响应式数据
	watch(
	  [sum, msg],
	  (newValue, oldValue) => {
	    console.log(newValue, oldValue);
	  },
	  { immediate: true } // 刚出现也执行watch
	);
	
	// 3. 监视reactive定义的一个响应式数据的全部属性
	// ! 此处无法获取正确的oldValue，新旧一样的
	// ! 强制开启了深度监视（deep配置无效）
	watch(
	  person,
	  (newValue, oldValue) => {
	    console.log(newValue, oldValue);
	  },
	  { deep: false } // 此处deep配置无效
	);
	
	// 4. 监视reacive定义的一个响应式数据中的一个属性
	watch(
	  () => person.age,
	  (newValue, oldValue) => {
	    console.log(newValue, oldValue);
	  }
	);
	
	// 5. 监视reacivee定义的一个响应式数据中的某些属性
	// ! 能监听到旧数据了
	watch([() => person.name, () => person.age], (newValue, oldValue) => {
	  console.log(newValue, oldValue);
	});
	
	// 特殊情况
	watch(
	  () => person.job,
	  (newValue, oldValue) => {
	    console.log(newValue, oldValue);
	  },
	  { deep: true } // 监听深层属性，需要开启deep
	);
	```





