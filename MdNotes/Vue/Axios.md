# Axios

> 一些推荐的文章：
>
> - [掘金](https://juejin.cn/post/6884561821127491597)
>- [axios官方文档的理解](https://ykloveyxk.github.io/2017/02/25/axios全攻略/)
> - [W3Cschool](https://www.w3cschool.cn/jquti/)
> - [官方文档](https://axios-http.com/zh/docs/intro)
> - [Vue中axios的使用](https://blog.csdn.net/lyyrhf/article/details/115217741?spm=1001.2014.3001.5502)
>
> 

## 基本使用

### 发送POST请求

> 默认的是get，get请求可以不设置method

```javascript
// 发送 POST 请求
axios({
	method: 'post',
	url: '/user/12345',
	data: {
		firstName: 'Fred',
		lastName: 'Flintstone'
	}
});
```

请求相应的处理在then和catch回调中

正常->then，异常->catch

```javascript
// 发送 POST 请求
axios({
		method: 'post',
		url: '/user/12345',
		data: {
			firstName: 'Fred',
			lastName: 'Flintstone'
		}
	})
	.then(res => {
		consloe.log(res)
	})
	.catch(err => {
		console.log(err)
	})
```

## 响应结构

```javascript
{
	// `data` 由服务器提供的响应
	data: {},
	// `status` 来自服务器响应的 HTTP 状态码
	status: 200,
	// `statusText` 来自服务器响应的 HTTP 状态信息
	statusText: 'OK',
	// `headers` 服务器响应的头
	headers: {},
	// `config` 是为请求提供的配置信息
	config: {},
	// 'request'
	// `request` is the request that generated this response
	// It is the last ClientRequest instance in node.js (in redirects)
	// and an XMLHttpRequest instance the browser
	request: {}
}
```

> 其中的 data 是后端返回的数据，一般我们也只需要关注 response 中的 data 字段就行

## 创建实例

可以使用自定义配置新建一个 axios 实例 axios.create([config])

```javascript
const instance = axios.create({
	baseURL: 'https://some-domain.com/api/',
	timeout: 1000,
	headers: {
		'X-Custom-Header': 'foobar'
	}
});
```

以下是实例所拥有的方法

- request(config)
- get(url[, config])
- delete(url[, config])
- head(url[, config])
- options(url[, config])
- post(url[, data[, config]])
- put(url[, data[, config]])
- patch(url[, data[, config]])

axios会把这些 方法中的config 会和创建实例时指定的 config 合并到一起使用

## ==请求配置==

### 无备注版

```javascript
{
	url: '/user',
	method: 'get',
	baseURL: 'https://some-domain.com/api/',
	headers: {
		'X-Requested-With': 'XMLHttpRequest'
	},
	transformRequest: [function(data, headers) {
		return data;
	}],
	transformResponse: [function(data) {
		return data;
	}],
	params: {
		ID: 12345
	},
	paramsSerializer: function(params) {
		return Qs.stringify(params, {
			arrayFormat: 'brackets'
		})
	},
	data: {
		firstName: 'Fred'
	},
	timeout: 1000,
	withCredentials: false,
	adapter: function(config) {},
	auth: {
		username: 'janedoe',
		password: 's00pers3cret'
	},
	responseType: 'json',
	responseEncoding: 'utf8',
	xsrfCookieName: 'XSRF-TOKEN',
	xsrfHeaderName: 'X-XSRF-TOKEN',
	onUploadProgress: function(progressEvent) {},
	onDownloadProgress: function(progressEvent) {},
	maxContentLength: 2000,
	validateStatus: function(status) {
		return status >= 200 && status < 300;
	},
	maxRedirects: 5,
	socketPath: null,
	httpAgent: new http.Agent({
		keepAlive: true
	}),
	httpsAgent: new https.Agent({
		keepAlive: true
	}),
	proxy: {
		host: '127.0.0.1',
		port: 9000,
		auth: {
			username: 'mikeymike',
			password: 'rapunz3l'
		}
	},
	cancelToken: new CancelToken(function(cancel) {})
}

```

### 有备注版

```javascript
{
	// `url` 是用于请求的服务器 URL
	url: '/user',
	// `method` 是创建请求时使用的方法
	method: 'get', // default
	// `baseURL` 将自动加在 `url` 前面，除非 `url` 是一个绝对 URL。
	// 它可以通过设置一个 `baseURL` 便于为 axios 实例的方法传递相对 URL
	baseURL: 'https://some-domain.com/api/',
	// `transformRequest` 允许在向服务器发送前，修改请求数据
	// 只能用在 'PUT', 'POST' 和 'PATCH' 这几个请求方法
	// 后面数组中的函数必须返回一个字符串，或 ArrayBuffer，或 Stream
	transformRequest: [function(data, headers) {
		// 对 data 进行任意转换处理
		return data;
	}],
	// `transformResponse` 在传递给 then/catch 前，允许修改响应数据
	transformResponse: [function(data) {
		// 对 data 进行任意转换处理
		return data;
	}],
	// `headers` 是即将被发送的自定义请求头
	headers: {
		'X-Requested-With': 'XMLHttpRequest'
	},
	// `params` 是即将与请求一起发送的 URL 参数
	// 必须是一个无格式对象(plain object)或 URLSearchParams 对象
	params: {
		ID: 12345
	},
	// `paramsSerializer` 是一个负责 `params` 序列化的函数
	// (e.g. https://www.npmjs.com/package/qs, http://api.jquery.com/jquery.param/)
	paramsSerializer: function(params) {
		return Qs.stringify(params, {
			arrayFormat: 'brackets'
		})
	},
	// `data` 是作为请求主体被发送的数据
	// 只适用于这些请求方法 'PUT', 'POST', 和 'PATCH'
	// 在没有设置 `transformRequest` 时，必须是以下类型之一：
	// - string, plain object, ArrayBuffer, ArrayBufferView, URLSearchParams
	// - 浏览器专属：FormData, File, Blob
	// - Node 专属： Stream
	data: {
		firstName: 'Fred'
	},
	// `timeout` 指定请求超时的毫秒数(0 表示无超时时间)
	// 如果请求话费了超过 `timeout` 的时间，请求将被中断
	timeout: 1000,
	// `withCredentials` 表示跨域请求时是否需要使用凭证
	withCredentials: false, // default
	// `adapter` 允许自定义处理请求，以使测试更轻松
	// 返回一个 promise 并应用一个有效的响应 (查阅 [response docs](#response-api)).
	adapter: function(config) {
		/* ... */
	},
	// `auth` 表示应该使用 HTTP 基础验证，并提供凭据
	// 这将设置一个 `Authorization` 头，覆写掉现有的任意使用 `headers` 设置的自定义 `Authorization`头
	auth: {
		username: 'janedoe',
		password: 's00pers3cret'
	},
	// `responseType` 表示服务器响应的数据类型，可以是 'arraybuffer', 'blob', 'document', 'json', 'text', 'stream'
	responseType: 'json', // default
	// `responseEncoding` indicates encoding to use for decoding responses
	// Note: Ignored for `responseType` of 'stream' or client-side requests
	responseEncoding: 'utf8', // default
	// `xsrfCookieName` 是用作 xsrf token 的值的cookie的名称
	xsrfCookieName: 'XSRF-TOKEN', // default
	// `xsrfHeaderName` is the name of the http header that carries the xsrf token value
	xsrfHeaderName: 'X-XSRF-TOKEN', // default
	// `onUploadProgress` 允许为上传处理进度事件
	onUploadProgress: function(progressEvent) {
		// Do whatever you want with the native progress event
	},
	// `onDownloadProgress` 允许为下载处理进度事件
	onDownloadProgress: function(progressEvent) {
		// 对原生进度事件的处理
	},
	// `maxContentLength` 定义允许的响应内容的最大尺寸
	maxContentLength: 2000,
	// `validateStatus` 定义对于给定的HTTP 响应状态码是 resolve 或 reject  promise 。如果 `validateStatus` 返回 `true` (或者设置为 `null` 或 `undefined`)，promise 将被 resolve; 否则，promise 将被 rejecte
	validateStatus: function(status) {
		return status >= 200 && status < 300; // default
	},
	// `maxRedirects` 定义在 node.js 中 follow 的最大重定向数目
	// 如果设置为0，将不会 follow 任何重定向
	maxRedirects: 5, // default
	// `socketPath` defines a UNIX Socket to be used in node.js.
	// e.g. '/var/run/docker.sock' to send requests to the docker daemon.
	// Only either `socketPath` or `proxy` can be specified.
	// If both are specified, `socketPath` is used.
	socketPath: null, // default
	// `httpAgent` 和 `httpsAgent` 分别在 node.js 中用于定义在执行 http 和 https 时使用的自定义代理。允许像这样配置选项：
	// `keepAlive` 默认没有启用
	httpAgent: new http.Agent({
		keepAlive: true
	}),
	httpsAgent: new https.Agent({
		keepAlive: true
	}),
	// 'proxy' 定义代理服务器的主机名称和端口
	// `auth` 表示 HTTP 基础验证应当用于连接代理，并提供凭据
	// 这将会设置一个 `Proxy-Authorization` 头，覆写掉已有的通过使用 `header` 设置的自定义 `Proxy-Authorization` 头。
	proxy: {
		host: '127.0.0.1',
		port: 9000,
		auth: {
			username: 'mikeymike',
			password: 'rapunz3l'
		}
	},
	// `cancelToken` 指定用于取消请求的 cancel token
	// （查看后面的 Cancellation 这节了解更多）
	cancelToken: new CancelToken(function(cancel) {})
}
```

## 配置默认值

axios 可以配置在每一个请求中生效的一些配置项的默认值

### 全局的默认值

可以使用 axios.defaults 来设置

```javaScript
axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
```

### 自定义实例的默认值

也可以通过创建的自定义的对象设置默认值 instance.defaults

```javaScript
// Set config defaults when creating the instance
const instance = axios.create({
  baseURL: 'https://api.example.com'
});
// Alter defaults after instance has been created
instance.defaults.headers.common['Authorization'] = AUTH_TOKEN;
```

### 配置的优先顺序

在创建实例 axios.create() 时传入的配置会被 instance.defaults 中设置的同一个配置的值覆盖，在具体的请求方法中的配置会覆盖前两者

```javaScript
// 使用由库提供的配置的默认值来创建实例
// 此时超时配置的默认值是 `0`
var instance = axios.create();
// 覆写库的超时默认值
// 现在，在超时前，所有请求都会等待 2.5 秒
instance.defaults.timeout = 2500;
// 为已知需要花费很长时间的请求覆写超时设置
instance.get('/longRequest', {
  timeout: 5000
});
```

## 拦截器

- axios.interceptors.request   请求拦截器
- axios.interceptors.response   响应拦截器

```javaScript
// 添加请求拦截器
axios.interceptors.request.use(function (config) {
  // 在发送请求之前做些什么
  config.header["Token"] = "xxxx"
  return config;
}, function (error) {
  // 对请求错误做些什么
  return Promise.reject(error);
});

// 添加响应拦截器
axios.interceptors.response.use(function (response) {
  // 对响应数据做点什么
  if (response.status === 200){
    return response.data
  } else {
    return Promise.reject(new Error('error'))
  }
}, function (error) {
  // 对响应错误做点什么
  return Promise.reject(error);
});
```

如果想要取消拦截器，可以通过使用一个变量来接收设置拦截器时返回的实例，然后使用 eject 来取消拦截器

```javaScript
const myInterceptor = axios.interceptors.request.use(function () {/*...*/});
axios.interceptors.request.eject(myInterceptor);
```

# 一些项目里面的例子

## ACM官网登录

```javascript
login() {
	var obj = {
		username: this.formLabelAlign.username,
		password: this.formLabelAlign.password
	}
	console.log(obj);
	this.$axios({
			method: "POST",
			url: "/user/login",
			headers: {
				"Content-Type": "application/x-www-form-urlencoded",
			},
			params: obj,
		})
		.then((res) => {
			sessionStorage.setItem('token', res.headers.token)
			this.$message.success('登录成功')
			this.$router.push('/backslide')
		})
		.catch(err => {
			this.$message.error('登录错误' + err)
		});
},
```

## 在线考试系统登录

```javascript
login() {
	console.log(JSON.stringify(this.formLabelAlign));
	this.axios({
			url: 'http://43.142.18.70:9090/Login',
			method: 'POST',
			headers: {
				"Content-Type": "application/json"
			},
			data: JSON.stringify(this.formLabelAlign)
		})
		.then(res => {
			if (res.data.code == 200) {
				this.$message.success('登录成功')
				sessionStorage.setItem('nickname', res.data.data.nickname)
				sessionStorage.setItem('uid', res.data.data.id)
				if (sessionStorage.getItem('nickname') == 'teacher')
					this.$router.push('/ExamAdd')
				else if (sessionStorage.getItem('nickname'))
					this.$router.push('/ExamPaper')
			} else if (res.data.msg == '参数错误')
				this.$message.error('账号或密码错误')
			else if (res.data.msg == '系统错误')
				this.$message.error('账号或密码错误')
		})
},
```

## ACM官网后台文件

### 获取

```javascript
getFiles() {
	this.axios
		.get(`/document/getFiles`)
		.then((res) => {
			this.tableData = res.data.data;
			console.log(this.tableData);
		});
},

```

### 上传url

```javascript
addFile() {
	var obj = {
		title: "mi",
		description: "w",
		fileurl: this.input,
	};
	this.dialogFormVisible = false;
	this.$axios({
			method: 'POST',
			url: '/document/addFile',
			headers: {
				"Content-Type": "application/x-www-form-urlencoded",
				token: sessionStorage.getItem("token"),
			},
			params: obj,
		})
		.then((res) => {
			if (res.data.code == 200) {
				this.$message.success("上传成功");
				this.getFiles();
			} else this.$message.error("上传失败");
		})
	this.input = '';
},
```

### 删除url

```javascript
beforeDelete(id) {
		this.$confirm('此操作将删除该图片, 是否继续?', '提示', {
				confirmButtonText: '确定',
				cancelButtonText: '取消',
				type: 'warning'
			})
			.then(() => {
				this.deleteRow(id);
			})
			.catch(() => {
				this.$message({
					type: 'info',
					message: '已取消删除',
				});
			});
	},
	deleteRow(id) {
		console.log(id);
		this.$axios({
				method: "GET",
				url: `/document/deleteFile/${id}`,
				headers: {
					// "Content-Type": "application/x-www-form-urlencoded",
					token: sessionStorage.getItem("token"),
				},
			})
			.then((res) => {
				if (res.data.code == 200) {
					this.$message.success("删除成功");
					this.getFiles();
				} else this.$message.error("删除失败");

			})
	},

```

## ACM官网轮播图上传

```javascript
submit() {
	var obj = {
		title: this.nowShow.title,
		subtitle: this.nowShow.subtitle,
		id: this.nowShow.id,
		imgurl: this.nowShow.imgurl,
		targeturl: this.nowShow.targeturl,
	};
	this.$axios({
			method: "POST",
			url: "/carousel/editCarousel",
			headers: {
				"Content-Type": "application/x-www-form-urlencoded",
				token: sessionStorage.getItem("token"),
			},
			params: obj,
		})
		.then((res) => {
			this.$message.success("修改成功");
			location.reload();
		})
		.catch((err) => {
			this.$message.error("修改失败");
		});
},

```

## 在线考试系统删除试卷

````javascript
beforeDelete(id) {
		this.$confirm('此操作将删除该考试信息, 是否继续?', '提示', {
			confirmButtonText: '确定',
			cancelButtonText: '取消',
			type: 'warning'
		}).then(() => {
			this.deleteRow(id);
		}).catch(() => {
			this.$message({
				type: 'info',
				message: '已取消删除'
			});
		});
	},
	deleteRow(id) {
		this.axios
			.delete(`http://43.142.18.70:9090/ExamDel/${id}`)
			.then((res) => {
				if (res.data.code == 200) {
					this.$message.success("删除成功");
					this.getExam()
				} else this.$message.error("删除失败");
			});
	},

````

## 在线考试系统试卷添加

````javascript
add() {
	this.dialogFormVisible = false;
	this.axios({
			url: `http://43.142.18.70:9090/ExamAdd`,
			method: "POST",
			headers: {
				"Content-Type": "application/json"
			},
			data: JSON.stringify(this.examAdd),
		})
		.then((res) => {
			console.log(res);
			if (res.data.code == 200) {
				this.$message.success("添加成功");
				this.getExam();
			} else {
				this.$message.error("添加失败");
			}
		});
},

````

## 在线考试系统题库上传

````javascript
add() {
	console.log(this.bankAdd);
	this.dialogFormVisible = false;
	this.axios({
		url: "http://43.142.18.70:9090/QuestionBankAdd",
		method: "POST",
		headers: {
			"Content-Type": "application/json"
		},
		data: JSON.stringify(this.bankAdd),
	}).then((res) => {
		console.log(res);
		if (res.data.code == 200) {

			this.$message.success('添加成功')
			this.getBank()
		} else {
			this.$message.error('添加失败')
		}
	});
},

````

## 学生添加

````javascript
studentAdd() {
	console.log(this.newStudent);
	this.dialogFormVisible = false;
	this.axios({
			url: "http://43.142.18.70:9090/StudentAdd",
			method: "POST",
			headers: {
				"Content-Type": "application/json"
			},
			data: JSON.stringify(this.newStudent),
		})
		.then((res) => {
			console.log(res);
			if (res.data.code == 200) {
				this.$message.success('添加成功')
				this.getStudent()
			} else {
				this.$message.error('添加失败')
			}
		});
},

````

# 其他人分享的

一、axios来历

Ajax：Ajax(Asynchronous JavaScript and XML)即异步网络请求，Ajax能够让页面无刷新的请求数据。在旧浏览器页面在向服务器请求数据时，因为返回的是整个页面的数据，页面都会强制刷新一下，这对于用户来讲并不是很友好。并且我们只是需要修改页面的部分数据，但是从服务器端发送的却是整个页面的数据，十分消耗网络资源。而我们只是需要修改页面的部分数据，也希望不刷新页面，因此异步网络请求就应运而生。



原生XMLHttpRequest实现

```java
var request = new XMLHttpRequest();
request.onreadystatechange = function () { 
    if (request.readyState === 4) { 
        if (request.status === 200) { 
            return success(request.responseText);
        } else {
            return fail(request.status);
        }
    } else {
    }
}
request.open('GET', '/api/categories');
request.setRequestHeader("Content-Type", "application/json") 
request.send();

```

Axios（ajax i/o system）：本质上还是对原生XMLHttpRequest的封装，基于promise用于浏览器和node.js的http客户端，可以使用Promise API，符合最新的ES规范。具备如下特点：

1. 在浏览器中创建XMLHttpRequest请求
2. 在node.js中发送http请求
3. 支持Promise API
4. 拦截请求和响应
5. 转换请求和响应数据
6. 取消要求
7. 自动转换JSON数据

二、安装使用

- npm安装


 `npm install axios`



- 通过cdn引入

<script src="https://unpkg.com/axios/dist/axios.min.js"></script>


- 在vue项目的main.js文件中引入axios

`import axios from 'axios'`
`Vue.prototype.$axios = axios`



- 在组件中使用`axios

<script>
	export default {
		mounted(){
			this.$axios.get('/goods.json').then(res=>{
				console.log(res.data);
			})
		}
	}
</script>

三、Axios请求方式
1、axios可以请求的方法：
get：获取数据，请求指定的信息，返回实体对象
post：向指定资源提交数据（例如表单提交或文件上传）
put：更新数据，从客户端向服务器传送的数据取代指定的文档的内容
patch：更新数据，是对put方法的补充，用来对已知资源进行局部更新
delete：请求服务器删除指定的数据

2、get请求示例代码

```javascript
this.$axios.get('/goods.json',{
    			params: {
                    id:1
                }
			}).then(res=>{
					console.log(res.data);
				},err=>{
					console.log(err);
			})
```

```javascript
this.$axios({
		method: 'get',
		url: '/goods.json',
    	params: {
            id:1
        }
	}).then(res=>{
		console.log(res.data);
	},err=>{
		console.log(err);
	})
```


3、post请求
post请求一般分为两种类型

1.form-data 表单提交，图片上传、文件上传时用该类型比较多

2. application/json 一般是用于 ajax 异步请求

application/json请求

```javascript
this.$axios.post('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			},err=>{
				console.log(err);
			})
```





form-data请求

```java
let data = {
	//请求参数
}

let formdata = new FormData();
for(let key in data){
	formdata.append(key,data[key]);
}

this.$axios.post('/goods.json',formdata).then(res=>{
	console.log(res.data);
},err=>{
	console.log(err);
})
```


4、put和patch请求
示例代码
put请求

```java
this.$axios.put('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			})
```


patch请求

```java
this.$axios.patch('/url',{
				id:1
			}).then(res=>{
				console.log(res.data);
			})
```


5、delete请求
示例代码
参数以明文形式提交

```java
this.$axios.delete('/url',{
				params: {
					id:1
				}
			}).then(res=>{
				console.log(res.data);
			})
```


参数以封装对象的形式提交

```java
this.$axios.delete('/url',{
				data: {
					id:1
				}
			}).then(res=>{
				console.log(res.data);
			})
```

//方法二

```java
axios({
    method: 'delete',
    url: '/url',
    params: { id:1 }, 
    data: { id:1 } 
}).then(res=>{
	console.log(res.data);
})
```


6、并发请求
并发请求：同时进行多个请求，并统一处理返回值  通过axios.all(iterable)可实现发送多个请求，参数不一定是数组，只要有iterable接口就行，函数返回的是一个数组

axios.spread(callback)可用于将结果数组展开示例代码

```java
 this.$axios.all([
	this.$axios.get('/goods.json'),
	this.$axios.get('/classify.json')
]).then(
	this.$axios.spread((goodsRes,classifyRes)=>{
		console.log(goodsRes.data);
		console.log(classifyRes.data);
	})
)
```

##### 响应信息(response [schema](https://so.csdn.net/so/search?q=schema&spm=1001.2101.3001.7020))

```java
[{
    data:{},]()
    
status: 200,

statusText: 'ok',
    
headers:{},

config:{}, 

}

axios.get('/user/12345').then(response={
    console.log(response.data);
    console.log(response.status);
    console.log(response.statusText);
    console.log(response.headers);
    console.log(response.config);
})
```



四、Axios实例
1、创建axios实例
可以同时创建多个axios实例

```java
const instance = axios.create({
    baseURL: 'http://localhost:3000/api/products',
    timeout: 1000,
    headers: {'X-Custom-Header':'foobar'}
});
//instance的使用
instance.get('/user',{
    params:{ID:12345}
}).then(res=>console.log(res))
.catch(err=>console.log(err))
```


  axios实例常用配置：

baseURL 请求的域名，基本地址，类型：String
timeout 请求超时时长，单位ms，类型：Number
url 请求路径，类型：String
method 请求方法，类型：String
headers 设置请求头，类型：Object
params 请求参数，将参数拼接在URL上，类型：Object
data 请求参数，将参数放到请求体中，类型：Object

axios全局配置

```java
this.$axios.defaults.timeout = 2000;

this.$axios.defaults.baseURL = 'http://localhost:8080';
```

axios实例配置

```java
let instance = this.$axios.create();
instance.defaults.timeout = 3000;
```

axios请求配置

```java
this.$axios.get('/goods.json',{
				timeout: 3000
			}).then()
```

以上配置的优先级为：请求配置 > 实例配置 > 全局配置

```java
import axios from 'axios'
axios.default.timeout = 1000; 
const instance = axios.create({
    timeout: 2000,  
});

instance.get('/users/123456',{
    timeout: 3000,  
}).then(/*....*/).catch(/*....*/)
```



##### Config配置选项

```java
{
    url: '/user',
    
method:'get',
   
baseURL: 'http://localhost:3000/',

transformRequest: [function(data,headers){

    return data;
}],    
    
transformResponse:[function(data){

    return data;
}],   

headers: {'X-Requested-with':'XMLHttpRequest'},
    
params:{
  ID:12345  
},    

paramsSerializer: function(params){
  return Qs.stringify(params,{arrayFormat:'brackets'});  
},     

data:{
  firstName: 'simon',  
},    

timeout:1000,
    
withCredentials:false,
    
adapter:function(config){
    /*...*/
},    

auth:{
  username:'simon',
  password:'123456',    
},    

 responseType: 'json',   
     
 proxy:{
     host:127.0.0.1,
     port:8080,
     auth:{
         username:'simon',
         password:'123456'    
     }    
 },   

 cancelToken: new CancelToken(cancel=>{})    
}

```

五、拦截器

拦截器：interceptor在请求或响应被处理前拦截它们，主要完成请求参数的解析，将页面表单参数付给值栈中相应属性 执行功能检验程序异常调试工作

1、请求拦截器
示例代码

```java
this.$axios.interceptors.request.use(config=>{
			return config
		},err=>{
		
			return Promise.reject(err);
	})

let instance = $axios.create();
instance.interceptors.request.use(config=>{
    return config
})
```

2、响应拦截器
示例代码

```java
this.$axios.interceptors.response.use(res=>{	

			return res 
		},err=>{
			return Promise.reject(err);
	})
```


3、取消拦截
示例代码

```java
let instance = this.$axios.interceptors.request.use(config=>{
				config.headers = {
					token: ''
				}
				return config
			})
			
//取消拦截
this.$axios.interceptors.request.eject(instance);

```

六、错误处理
示例代码

```java
this.$axios.get('/url').then(res={



		}).catch(err=>{
		
		console.log(err);
	})
```


七、取消请求
示例代码

```java
let source = this.$axios.CancelToken.source();

this.$axios.get('/goods.json',{
				cancelToken: source
			}).then(res=>{
				console.log(res)
			}).catch(err=>{
				console.log(err)
			})
source.cancel('取消后的信息');

```

