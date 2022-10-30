# HTML语法 | 青训营笔记

**这是我参与「第四届青训营 」笔记创作活动的的第1天**



## Tips

- 标签和属性不区分大小写，最好小写
- 空标签可以不闭合，如`input`、`meta`
- 属性值最好用双引号包裹
- 有些属性值可以省略，如`required`、`readonly`



## 标题

- 总共只有h1~h6六级，从大到小



## 列表



### 有序列表

```html
<ol>
	<li>阿凡达</li>
	<li>泰坦尼克号</li>
	<li>复仇者联盟</li>
</ol>
```

![imagea8047c6697b114a3.png](https://img.wang.232232.xyz/img/2022/07/24/imagea8047c6697b114a3.png)



### 无序列表

```html
<ul>
	<li>🍇</li>
	<li>🍉</li>
	<li>🍎</li>
</ul>
```

![image789d99e6d6355b19.png](https://img.wang.232232.xyz/img/2022/07/24/image789d99e6d6355b19.png)



### 自定义列表

| 标签名 | 说明                                    |
| ------ | --------------------------------------- |
| dl     | 表示自定义列表的整体，用于包裹dt/dd标签 |
| dt     | 表示自定义列表的主题                    |
| dd     | 表示自定义列表的针对主题的每一项内容    |

- dd前默认会有缩进效果

```html
<dl>
	<dt>导演：</dt>
	<dd>陈凯歌</dd>
	<dt>主演：</dt>
	<dd>张国荣</dd>
	<dd>张丰毅</dd>
	<dd>巩俐</dd>
	<dt>上映日期：</dt>
	<dd>1993-01-01</dd>
</dl>
```

![image4a4a0aefadf48090.png](https://img.wang.232232.xyz/img/2022/07/24/image4a4a0aefadf48090.png)



## 链接

> 来源：[地址](https://juejin.cn/post/6844904013566066702)



### 定义与用法

- 一些常用属性

| 属性     | 值                                                           | 描述                         |
| -------- | ------------------------------------------------------------ | ---------------------------- |
| download | fileName                                                     | 规定被下载的超链接目标名     |
| href     | URL                                                          | 规定链接指向的页面的 URL     |
| target   | blank【跳转新页面】 /  parent【在父窗体中打开链接】 / self【默认，当前页面跳转】 / top【在当前窗体打开链接，并替换当前的整个窗体(框架页)】 / framename【在指定的框架中打开被链接文档，把frame看做内置浏览器】 | 规定在何处打开链接文档       |
| title    | 说明                                                         | 规定鼠标置于标签上的显示说明 |

具体用法：

```ini
    <a href="">空链接，当前页面跳转，刷新页面</a>
    <a href="//www.baidu.com" target="_blank">打开新窗口，跳转到百度</a>
    <a href="javascript:void(0)" >不跳转，网页上常用于button作用的a标签设置点击事件，阻止跳转</a>
    <a href="mailto:123@qq.com">发送邮件【mailto：会自动检测本机系统是否安装邮箱，如果有就会自动打开邮箱，没有则会提示用户选择邮箱或者没提示】</a>
    <a href="tel:123456789">一键拨打电话</a>
    <a href="sms:123456789">一键发送短信</a>

    <a href="#">空锚点，回到最顶端，不刷新页面</a>

    <a href="#app">跳转</a>
    <p id="app">锚点</p>

    <a href="#app">跳转</a>
    <a href="" name="app">跳转【这种方式只能用a标签的name属性定义才生效】</a>
    
      // 下载，href指示目标地址，download重命名下载文件
    <a href="//www.w3school.com.cn/i/w3school_logo_white.gif" download="w3logo">
        <img border="0" src="//www.w3school.com.cn/i/w3school_logo_white.gif" alt="W3School">
    </a>
```



网址：(推荐第三种)

- `https://baidu.com`
- `http://baidu/com`
- `//baidu.com`



### 伪类用法

>  a标签href=""的时候，默认状态时:visited状态；a标签没有href属性的时候，默认状态时:active状态，这两种情况都不影响:active和:hover的触发，但是永远不会触发:link

 

1. link：设置a对象在未被访问前的样式表属性

2. visited：设置a对象在其链接地址已被访问过时的样式表属性

3. hover：设置对象在其鼠标悬停时的样式表属性

4. active：设置对象在被用户激活（在鼠标点击与释放之间发生的事件）时的样式表属性

	**CSS定义中的顺序是LVHA(link—visited—hover—active)	LoVe,HAte**

	

## 多媒体标签

> 来源：[地址1](https://juejin.cn/post/6952050803251085319)   [地址2](https://juejin.cn/post/7117081102375714846)



### img



#### 属性

- **src**：图片的路径，这是必须有的

- **alt**：在图片加载不出来的情况下，用文字描述图片内容

- **height**：图片高度

- **width**：图片宽度

	**规定图片的高（宽）的情况下，它的宽（高）会自动设置；若同时规定图片的宽和高，图片可能变形**



#### 事件

- **onload**：图片加载错误
- **onerror**：图片加载成功 

```html
<img id="xxx" src="cat.png" alt="一条小猫" width="300" />
    <script>
        xxx.onload = function(){
            console.log("图片加载成功");
        };
        xxx.onerror = function(){
            console.log("图片加载失败");
            xxx.src = "/404.png"; 
            /* 404.png是自己设置的图片，是用于在小猫图片加载失败的情况下显示的图片 */
        };
    </script>
```



#### 响应式

`max-width：100%`，使图片在手机上展示时能够适应手机屏幕

用法：在head里写

```html
<style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        img {
            max-width: 100%;
        }
</style>
```



width:100%和max-width:100%区别：

- width：不管img宽度多少，都显示div宽度

- max-width:100%：如果img宽度大于div宽度，img就显示div100%宽度，否则就显示img的宽度



### audio

> 来源： [地址1](https://juejin.cn/post/6983927031122067486)



#### 标签属性

- `autoplay`：音频会尽快自动播放，不会等待整个音频下载完成
- `controls`：浏览器提供包括声音、播放进度、播放暂停的控制面板（不同浏览器不一致），用户可以控制音频播放
- `loop`：循环播放音频
- `muted`：是否静音，默认值为`false`，表示有声音
- `preload`：预加载，包括`auto`、`metadata`和`none`三个参数值，`auto`表示加载音频，`metadata`表示不加载音频，但是需要获取音频元数据（如音频长度），`none`表示不加载音频。若指定为空字符串，则等效于`auto`。注意`autoplay`属性优先级高于`preload`，若`autoplay`被指定，则会忽略此属性，浏览器将加载音频以供播放
- `src`：嵌入的音频`URL`



#### 设置多个音频资源

  不同浏览器支持的音频播放格式有所不同，一般为了兼容效果，会放置多种音频格式，浏览器会自上而下选择符合的音频格式。

```html
<audio controls>
  <source src="music.ogg" type="audio/ogg" />
  <source src="music.mp3" type="audio/mpeg" />
  <source src="music.wav" type="audio/Wav" />
</audio>
```



#### 元素属性



##### 只读

- `duration`：双进度浮点数，音频的播放时长，以秒为单位。若音频不可用或者音频未加载，则返回`NaN`
- `paused`：若音频被暂停或者未开始播放，则返回`true`
- `ended`：音频是否播放完毕，播放完毕则返回`true`
- `error`：发生错误情况下的`MediaError`对象
- `currentSrc`：返回正在播放或加载的音频的`URL`地址，对应于浏览器在`source`元素中选择的文件
- `seeking`：用户是否在音频中移动或者跳跃到新的播放点



##### 可读写

- `autoplay`：设置音频自动播放，或者查询音频是否设置`autoplay`
- `loop`：设置或者查询音频是否循环播放
- `currentTime`：返回音频当前的播放时间点，双精度浮点数，单位为秒。音频未播放，可用于设置音频开始播放的时间点。音频播放过程中，可用于设置音频播放时间点
- `controls`：显示或隐藏音频控制面板，或者查询控制面板是否可见
- `volume`：返回音量值，介于`0-1`之间的双进度浮点数，或者设置音量值
- `muted`：设置或者查询是否静音
- `playbackRate`：设置或者查询音频的播放速度，`1`表示正常速度，大于`1`表示快进，`0-1`之间表示慢进，`0`表示暂停（控制面板仍然是播放，仅仅是速度为`0`）



##### 特殊属性

建议访问[原地址](https://juejin.cn/post/6983927031122067486#heading-6)查看，比较全面



##### 方法

###### play

  播放音频，返回`Promise`，播放成功时为`resolved`，因为任何原因播放失败为`rejected`，[详细参考](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fplay)。

```javascript
var audio = document.querySelector('audio')

audio
  .play()
  .then(() => { })
  .catch(() => { })
复制代码
```

###### pause

  暂停音频，无返回值，[详细参考](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLMediaElement/pause)。

```javascript
var audio = document.querySelector('audio')

audio.pause()
复制代码
```

###### load

  重新加载`src`指定的资源，[详细参考](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fload)。

```javascript
var audio = document.querySelector('audio')

audio.src = 'music.mp3'
audio.load()
复制代码
```



##### 事件



###### 常用事件

- [loadstart](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Floadstart_event)：开始载入音频时触发
- [durationchange](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fdurationchange_event)：`duration`属性更新时触发
- [loadedmetadata](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Floadedmetadata_event)：音频元数据加载完成时触发
- [loadeddata](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Floadeddata_event)：音频的第一帧加载完成时触发，此时整个音频还未加载完
- [progress](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fprogress_event)：音频正在加载时触发
- [canplay](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fcanplay_event)：浏览器能够开始播放音频时触发
- [canplaythrough](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fcanplaythrough_event)：浏览器预计在不停下来进行缓冲的情况下，能够持续播放指定的音频时会触发



###### 其他事件

- [abort](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fabort_event)：音频终止时触发，非错误导致
- [emptied](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Femptied_event)：音频加载后又被清空，如加载后又调用 load 重新加载
- [ended](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fended_event)：播放结束，若设置`loop`属性，音频播放结束后不会触发
- [error](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Ferror_event)：发生错误
- [play](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fplay_event)：播放事件，第一次播放、暂停后播放会触发
- [playing](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fplaying_event)：播放事件，第一次播放、暂停后播放、播放结束后循环播放会触发
- [pause](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fpause_event)：暂停事件
- [ratechange](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fratechange_event)：播放速率改变
- [seeking](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fratechange_event)：播放点改变开始
- [seeked](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fratechange_event)：播放点改变结束
- [stalled](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fstalled_event)：浏览器尝试获取音频，但是音频不可用时触发
- [suspend](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fsuspend_event)：音频加载暂停时触发
- [timeupdate](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Ftimeupdate_event)：音频`currentTime`改变时触发
- [volumechange](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fvolumechange_event)：音量改变时触发，包括静音
- [waiting](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHTMLMediaElement%2Fwaiting_event)：开始播放前缓冲下一帧时触发



## 表单



### 基础标签

```html
<input placeholder="请输入用户名">

<input type="range">

<input type="number" min="1" max="10">

<input type="date" min="2018-02-10">

<textarea>Hey</textarea>
```

![image543090acef2e89bf.png](https://img.wang.232232.xyz/img/2022/07/24/image543090acef2e89bf.png)



### 复选框



```html
<p>
  <label><input type="checkbox" />🍎</label>
  <label><input type="checkbox" checked />🍏</label>
</p>
```



### 单选框

name标签内容相同的就只可以选一个

```html
<p>
  <label><input type="radio" name="sport" />⚽</label>
  <label><input type="radio" name="sport" />🏀</label>
</p>
```



### 下拉框



```html
<p>
  <select>
    <option>🥑</option>
    <option>🥩</option>
    <option>🥓</option>
  </select>
</p>
```



## 文字



### 引用



```html
<blockquote cite="http://t.cn/RfjKO0F">
  <p>天才并不是自生自长在深林荒野里的怪物， 是由可以使天才生长的民众产生、长育出来的，所以没有 这种民众，就没有天才。</p>
</blockquote>
```



短引用

- cite有斜体

```html
<p>我最喜欢的一本书是<cite>小王子</cite>。</p>
```



- q有引号“”

```html
<p>在<cite>第一章</cite>，我们讲过<q>字符串是不可变量</q>。</p>
```



### 代码



```html
<p><code>const</code>声明创建一个只读的常量。</p>

<pre><code>
const add = (a, b) => a + b;
const multiply = (a, b) => a * b;
</code></pre>
```



### 强调



- strong加粗
- em斜体

```html
<p>在投资之前，<strong>一定要做风险评估</strong>。</p>

<p>Cats <em>are</em> cute animals.</p>
```



