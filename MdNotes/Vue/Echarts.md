# Echarts

> ## 一些链接：
>
> - [Echarts官网](https://echarts.apache.org/en/index.html)
> - [ECharts案例全网最全版](https://juejin.cn/post/7078834647005822983)
> - [Make A Pre](http://analysis.datains.cn/finance-admin/index.html#/chartLib/all)
> - [*ECharts*案例大全（最新版），含各种案例，实例。](https://juejin.cn/post/7062254510311211044)
> - [*ECharts* 打造在线个人简历](https://juejin.cn/post/6844903734200238094)
> - [如何在 Vue 项目中使用 *echarts*](https://juejin.cn/post/6844903735257202702)
> - [前端深入之Vue篇 丨如何在项目中优雅的使用*Echarts*（上）](https://juejin.cn/post/6844904047187591182)
> - [前端深入之Vue篇 丨如何在项目中优雅的使用Echarts（下）](https://juejin.cn/post/6844904048714317837)
> - [*Echarts*教程](https://juejin.cn/post/6844904170508517390)
> - [Vue-*ECharts*](https://juejin.cn/post/6844903920112762893)
> - [千锋Echarts+Vue3.0数据可视化项目构建](https://www.bilibili.com/video/BV14u411D7qK)
> - [vue-echarts-v3](https://github.com/xlsdg/vue-echarts-v3)



## vue-echarts-v3



### 配置

1. 安装
```powershell
$ npm install --save echarts vue-echarts-v3
```

2. main.js导入
```js
import IEcharts from 'vue-echarts-v3/src/full.js';
```
3. 使用样例

```vue
<template>
	<div class="echarts">
		<IEcharts :option="bar" :loading="loading" @ready="onReady" @click="onClick" />
		<button @click="doRandom">Random</button>
	</div>
</template>

<script type="text/babel">
	import IEcharts from 'vue-echarts-v3/src/full.js';
  export default {
    name: 'view',
    components: {
      IEcharts
    },
    props: {
    },
    data: () => ({
      loading: true,
      bar: {
        title: {
          text: 'ECharts Hello World'
        },
        tooltip: {},
        xAxis: {
          data: ['Shirt', 'Sweater', 'Chiffon Shirt', 'Pants', 'High Heels', 'Socks']
        },
        yAxis: {},
        series: [{
          name: 'Sales',
          type: 'bar',
          data: [5, 20, 36, 10, 10, 20]
        }]
      }
    }),
    methods: {
      doRandom() {
        const that = this;
        let data = [];
        for (let i = 0, min = 5, max = 99; i < 6; i++) {
          data.push(Math.floor(Math.random() * (max + 1 - min) + min));
        }
        that.loading = !that.loading;
        that.bar.series[0].data = data;
      },
      onReady(instance, ECharts) {
        console.log(instance, ECharts);
      },
      onClick(event, instance, ECharts) {
        console.log(arguments);
      }
    }
  };
</script>

<style scoped>
	.echarts {
		width: 400px;
		height: 400px;
	}
</style>
```



## Echarts



### 使用样例

- main.js

```js
import * as echarts from 'echarts';
Vue.prototype.$echarts =echarts    
```

- vue

```vue
<template>
	<div class="echarts">
		<IEcharts :option="bar" :loading="loading" @ready="onReady" @click="onClick" />
		<button @click="doRandom">Random</button>
	</div>
</template>

<script type="text/babel">
	import IEcharts from 'vue-echarts-v3/src/full.js';
  export default {
    name: 'view',
    components: {
      IEcharts
    },
    props: {
    },
    data: () => ({
      loading: true,
      bar: {
        title: {
          text: 'ECharts Hello World'
        },
        tooltip: {},
        xAxis: {
          data: ['Shirt', 'Sweater', 'Chiffon Shirt', 'Pants', 'High Heels', 'Socks']
        },
        yAxis: {},
        series: [{
          name: 'Sales',
          type: 'bar',
          data: [5, 20, 36, 10, 10, 20]
        }]
      }
    }),
    methods: {
      doRandom() {
        const that = this;
        let data = [];
        for (let i = 0, min = 5, max = 99; i < 6; i++) {
          data.push(Math.floor(Math.random() * (max + 1 - min) + min));
        }
        that.loading = !that.loading;
        that.bar.series[0].data = data;
      },
      onReady(instance, ECharts) {
        console.log(instance, ECharts);
      },
      onClick(event, instance, ECharts) {
        console.log(arguments);
      }
    }
  };
</script>

<style scoped>
	.echarts {
		width: 400px;
		height: 400px;
	}
</style>
```



### option配置项

> [官方文档](https://echarts.apache.org/zh/option.html#title)

```js
//具体要配置什么需要参考官方文档
xAxis: {    //直角坐标系 grid 中的 x 轴
    type: 'category',   //坐标轴类型
    data: ["foo","bar","tom"]   //类目数据
},
yAxis: {},  //直角坐标系 grid 中的 y 轴
series: [{
    type: 'bar',    //系列,控制显示什么形状
    data: [5, 10, 15]
}]
```



### 通用配置



#### title

> [官方文档](https://echarts.apache.org/zh/option.html#title)

```js
//title：标题
var option = {
    title: {
        text: "我是辩题", // 主标题
        link: "https://www.bilibili.com", // 设置超链接
		sublink: "https://www.baidu.com",
		target: "self", // 在当前页面打开超链接
        textStyle: {
            color: 'red' // 文字颜色
        },
        borderWidth: 5, // 标题边框
        backgroundColor: "pink",// 背景颜色
        borderColor: 'green', // 标题边框颜色
        borderRadius: 5, // 标题边框圆角
        left: 20, // 标题的位置
        top: 20, // 标题的位置
        x: "center",// 标题居中
		subtext: "副标题"
    }
}
```



#### tooltip

> [官方文档](https://echarts.apache.org/zh/option.html#tooltip)

```javascript
//tooltip:提示框
tooltip:{
    trigger:'item',//触发类型,可选值有item\axis
    triggerOn:'click', //触发时机,看文档
    textStyle:{color:"gray"}，
    // formatter:'{a}{b}' //格式化显示,可选值有 字符串模板\回调函数,具体参考文档
    formatter:function (arg) {
       return arg.name
    }
}
```



#### toolbox

```js
//toolbox:工具按钮
toolbox: {
    feature: {
    saveAsImage: {}, // 将图表保存为图片
    dataView: {}, // 是否显示出原始数据
    restore: {}, // 还原图表
    dataZoom: {}, // 数据缩放
    magicType: { // 将图表在不同类型之间切换,图表的转换需要数据的支持
        type: ['bar', 'line']
        }
    }
}
```



#### legend

```js
//legend:是图例,用于筛选类别,需要和 series 配合使用
legend:{
    show: true, //图例开启或者关闭
	icon: "circle", // 图形
	top: "10%", //位置
	itemWidth: 10, // 宽
	itemHeight: 10, // 高
	textStyle: {
		color: "red",
		fontSize: 20,
		backgroundColor: "yellow"
	},
    data:['项目1','项目2']  //data里面的配置必须和series的name一致
},
series: [
    {
        name:'项目1',
        type: 'bar',
        data: [5, 10, 15]
    },
    {
        name:'项目2',
        type: 'bar',
        data: [3, 6, 9]
    }
]
```



### Grid

> 直角坐标系：只针对柱状图，折线图，散点图有效

```js
//1.控制坐标轴的大小，位置等
var option = {
    grid: {
        show: true, // 显示grid
        borderWidth: 10, // grid的边框宽度
        backgroundColor:"pink",// 背景颜色
        borderColor: 'red', // 边框颜色
        left: 100, // grid距离容器的位置
        top: 100,
        // right:100,
        // bottom:"20%"
        width: 300, // 大小
        height: 150
    }
}
```



```js
//2.控制坐标轴的方向
//坐标轴类型 type
//value : 数值轴, 自动会从目标数据中读取数据
//category : 类目轴, 该类型必须通过 data 设置类目数据
var option = {
    xAxis: {
        type: 'category',
        data: xDataArr,
        position: 'top' //top或bottom
    },
    yAxis: {
        type: 'value',
        position: 'right'   //right或left
    }
}
```



```js
// 3.区域缩放 dataZoom
var option = {
    dataZoom: [
        {
            type: 'slider',//slider : 滑块  inside:依靠鼠标滚轮或者双指缩放
            xAxisIndex: 0   //设置缩放组件控制的是哪个 x 轴, 一般写0即可
        },
        {
            type: 'slider',
            yAxisIndex: 0,//设置缩放组件控制的是哪个y轴, 一般写0即可
            start: 0,//数据窗口范围的起始百分比
            end: 80 //数据窗口范围的结束百分比
        }
    ]
}
```



### 基本图形



#### 柱状图



#####基本配置

```vue
<template>
	<div ref="myChart" id="myChart"></div>
</template>

<script>
	import * as echarts from "echarts";
	export default {
		mounted() {
			// 1.初始化
			let myEcharts = this.$echarts.init(this.$refs.myChart);
			// 2.设置echarts数据
			// 设置轴
			let xData = ["美食", "数码", "日化", "蔬菜"];
			let yData = ["33", "34", "32", "643"];
			// 3.设置配置项
			let option = {
				title: {
					text: "主标题"
				},
				xAxis: {
					data: xData,
					type: "category" // 坐标轴类型 value数据轴 category类目轴
				},
				yAxis: {},
				series: [{
					name: "销量",
					type: "bar", //系列类别
					data: yData
				}]
			}
			// 4.设置图标绘制图标
			myEcharts.setOption(option);
		}
	}
</script>

<style>
	#myChart {
		width: 500px;
		height: 500px;
		border: 1px solid pink;
	}
</style>
```



##### 更多效果

```js
series: [ // 系列，配置图标的类型
	{
		name: "销量",
		type: "bar", //系列类别
		data: yData,
		// 最大值/最小值
		markPoint: {
			data: [ // 标注的数据数组，每一项都是一个对象
				{
					type: "max",
					name: "最大值"
				},
				{
					type: "min",
					name: "最小值"
				}
			]
		},
		// 图表的标线
		markLine: {
			data: [{
				type: "average", // 平均值
				name: "平均值"
			}]
		},
		label: { //设置是否显示数值以及样式
			show: true,
			position: 'top'
		},
		barWidth: '50%', //设置柱状图的宽度
		//color: "red", // 全部轴的颜色
		itemStyle: {
			normal: {
				color: function(parmas) {
					let colorList = [
						"#c45345",
						"#99bcac",
						"#d45635",
						"#k54352"
					]
					return colorList[parmas.dataIndex]
				}
			}
		}
	}
]
```



##### 水平柱状图

```js
xAxis: {
	data: xData,
	type: "category" // 坐标轴类型 value数据轴 category类目轴
},
yAxis: {},
```

==改成==

```js
xAxis: {
	type: "value"
},
yAxis: {
	data: xData,
	type: "category"
},
```



#### 饼状图



##### 基本配置

```vue
<script>
	import * as echarts from "echarts";
	export default {
		mounted() {
			// 初始化
			let myEcharts = this.$echarts.init(this.$refs.myChart);
			// 设置数据
			let data=[
				{value:22,name:"吃的"},
				{value:32,name:"喝的"},
				{value:52,name:"玩的"},
				{value:102,name:"用的"}
			];
			let option={
				title:{
					text:"饼图",
					left:"center"
				},
				legend:{
					left:"left",
					orient:"verical"//布局朝向
				},
				series:[
					{
						name:"统计",
						type:"pie",//饼图
						data
					}
				]
			};
			myEcharts.setOption(option);
		}

	}
</script>
```



##### 更多效果

data数组改成

```js
let data = [
	{value: 22,name: "吃的",itemStyle:{normal:{color:"rgb(177, 213, 200)"}}},
	{value: 32,name: "喝的",itemStyle:{normal:{color:"rgb(254, 220, 94)"}}},
	{value: 52,name: "玩的",itemStyle:{normal:{color:"rgb(174, 208, 238)"}}},
	{value: 102,name: "用的",itemStyle:{normal:{color:"rgb(206, 147, 191)"}}}
];
```

series

```js
series: [{
	name: "统计",
	type: "pie", //饼图
	data,
	// 圆环形 设置饼图半径 第一项内半径 第二项外半径
	radius: ["40%", "70%"],
	// 设置文本标签
	label: {
		show: true,
		position: "inside" // outside外侧 inside内侧 center中心
	},
	roseType: "area", // 是否设置成玫瑰图
	itemStyle: {
		// color:"#c32521",
		shadowBlur: 200, // 阴影
		shadowColor: "reba(0,0,0,..5)"
	}
}]
```



#### 折线图



##### 基本配置

```js
import * as echarts from "echarts";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		// 数据
		let xData = ['一', '二', '三', '四', '五', '六', '日'];
		let data = [324, 564, 76, 12, 765, 342, 56];
		// 配置项
		let option = {
			xAxis: {
				type: "category",
				data: xData,
			},
			yAxis: {
				type: "value"
			},
			series: [{
					type: "line", //折线图
					data
				}

			]
		}
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



##### 更多效果

```js
series: [{
	type: "line", //折线图
	data,
	smooth: "true", //开启平滑的过渡
	areaStyle: {}, // 下面有填充
	markPoint: {
		data: [
			{type: "max",name: "最大值"},
			{type: "min",name: "最小值"}
		]
	},
	markLine: {
		data: [
			{type: "average",name: "平均值"},
		],
	}
}]
```



##### 堆叠效果

- data

```js
let data1 = [324, 564, 76, 142, 765, 342, 56];
let data2 = [344, 564, 86, 2, 77, 212, 55];
let data3 = [364, 764, 266, 92, 453, 382, 52];
let data4 = [384, 364, 726, 42, 75, 42, 76];
```

- series

```js
series: [{
		name: "美食",
		type: "line",
		// 数据的堆叠
		stack: "num", //同类类型的数据需要匹配相同的stack属性值
		data: data1,
		// 样式填充
		areaStyle: {
			// 选中高亮状态
			emphasis: {
				focus: "series" //聚焦当前的区域高亮
			}
		},

	},
	{
		name: "数码",
		type: "line",
		stack: "num",
		data: data2,
		areaStyle: {
			emphasis: {
				focus: "series"
			}
		},
	},
	{
		name: "雨林",
		type: "line",
		stack: "num",
		data: data3,
		areaStyle: {
			emphasis: {
				focus: "series"
			}
		},
		areaStyle: {
			emphasis: {
				focus: "series"
			}
		},
	},
	{
		name: "蔬菜",
		type: "line",
		stack: "num",
		data: data4,
		areaStyle: {
			emphasis: {
				focus: "series"
			}
		},
	},
]
```



#### 散点图



##### 基本配置

```js
import * as echarts from "echarts";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let options = {
			xAxis: {},
			yAxis: {},
            tooltip:{},// 非必须
			series: [{
				type: "scatter", //散点图
				symbolSize: "20", // 点的大小
				data: [
					[180, 80],
					[170, 70],
					[160, 60],
					[150, 50],
					[140, 40],
					[130, 30],
					[120, 20],
					[34, 44],
				],
			}],
		}
		// 设置配置项
		myEcharts.setOption(options);
	}
}
```



##### 更多效果

- series

```js
series: [{
	type: "scatter", //散点图
	symbolSize: "20", // 点的大小
	data: [
		[180, 80],
		[170, 70],
		[160, 60],
		[150, 50],
		[140, 40],
		[130, 30],
		[120, 20],
		[34, 44],
	],
	//图形样式
	//color:"red"//点的颜色
	color: {
		//线性渐变
		type: "liner",
		// 相当于在图形包围盒中的百分比
		// 点的颜色是渐变色
		x: 0,
		y: 0,
		x2: 1,
		y2: 0,
		colorStops: [{
				offset: 0,
				color: "#40c4ff"
			},
			{
				offset: 1,
				color: "rgba(249, 211, 227,0.8)"
			}
		]
	},
	// 鼠标移入点有边框高亮
	emphasis: {
		itemStyle: {
			borderColor: "rgba(206, 147, 191,.5)",
			borderWidth: 30
		}
	}
}]
```



#### k线图



##### 基本配置

```js
import * as echarts from "echarts";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let option = {
			xAxis: {
				data: ['日化', '蔬菜', '水电费', '防水']
			},
			yAxis: {

			},
			series: [{
				type: "candlestick", //k线图
				data: [
					[23, 56, 21, 74],
					[43, 23, 28, 64],
					[27, 57, 54, 3],
					[98, 16, 75, 1],
				],
			}]
		}
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



##### 更多效果

```js
import * as echarts from "echarts";
export default {
	data() {
		return {
			kdata: [
				[23, 56, 21, 74],
				[43, 23, 28, 64],
				[27, 57, 54, 3],
				[98, 16, 75, 1],
			]
		}
	},
	computed: {
		newData() {
			return this.kdata.map(v => v[0])
		}
	},
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let option = {
			xAxis: {
				data: ['日化', '蔬菜', '水电费', '防水']
			},
			yAxis: {

			},
			tooltip: {
				trigger: 'axis',
				axisPointer: {
					type: "cross"
				}
			},
			series: [{
					type: "candlestick", //k线图
					// data: [
					// 	[23, 56, 21, 74],
					// 	[43, 23, 28, 64],
					// 	[27, 57, 54, 3],
					// 	[98, 16, 75, 1],
					// ],
					data: this.kdata,
					itemStyle: {
						color: "#ec5566", //上涨颜色
						color0: "#55da3a", //下跌颜色
						borderColor: "#8a0000",
						borderColor0: "#008f28"
					},
					markPoint: {
						data: [{
								name: "最大值",
								type: "max",
								valueDim: "highest" //在哪个维度上面取max
							},
							{
								name: "最小值",
								type: "min",
								valueDim: "lowest"
							},
							{
								name: "平均值",
								type: "average",
								valueDim: "close"
							}
						]
					}
				},
				{
					type: "line",
					smooth: true,
					data: this.newData
				}
			]
		}
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



#### 雷达图



##### 基本配置

```js
import * as echarts from "echarts";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let option = {
			title: {
				text: "雷达图"
			},
			radar: [{ // 只适用于雷达图
				shape: "circle", //圆形，默认是多边形
				indicator: [ //雷达图的指示器，用来制定雷达图中的多个变量
					{
						name: '易用性',
						max: 100
					},
					{
						name: '功能',
						max: 100
					},
					{
						name: '拍照',
						max: 100
					},
					{
						name: '跑分',
						max: 100
					},
					{
						name: '续航',
						max: 100
					},
					{
						name: '颜值',
						max: 100
					}
				],
			}],
			series: [{
				type: "radar",
				data: [{
					value: [93, 34, 64, 62, 76, 23]
				}]
			}]
		}
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



##### 更多效果

- option

```js
let option = {
	title: {
		text: "雷达图"
	},
	radar: [{ // 只适用于雷达图
		shape: "circle", //圆形，默认是多边形
		indicator: [ //雷达图的指示器，用来制定雷达图中的多个变量
			{name: '易用性',max: 100},
			{name: '功能',max: 100},
			{name: '拍照',max: 100},
			{name: '跑分',max: 100},
			{name: '续航',max: 100},
			{name: '颜值',max: 100}
		],
		radius: 220, //半径
		startAngle: 180, // 坐标系的起始角度
		splitNumber: 4, // 内部层级
		axisName: { // 标志样式
			formatter: "{value}",
			color: "#dd7694"
		},
		splitArea: { // 分割区效果
			areaStyle: { // 分割区样式
				color: ["#88bfb8", "#5da39d", "#3d8e86", "#206864"],
				shadowColor: "0,0,0,.2",
				shadowBlur: 10
			}
		},

	}],
	series: [{
		type: "radar",
		data: [{
			value: [93, 34, 64, 62, 76, 23]
		}],
		areaStyle: { //线围起来的面积颜色
			color: "rgba(238, 121, 89,.9)"
		},
		lineStyle: {
			type: "dashed" //虚线
		}
	}]
}
```



#### 漏斗图



##### 基本配置

- option

```js
let option = {
	title: {
		text: "漏斗图"
	},
	tooltip: {
		tigger: "item",
		formatter: "{a}<br/>{b}:{c}%"
	},
	series: [{
		type: "funnel", //漏斗图
		data: [
			{value:60,name:"美食"},
			{value:50,name:"数码"},
			{value:80,name:"家电"},
			{value:90,name:"生活"},
			{value:100,name:"日用"}
		],
		left: "10%",
	}]
}
```



##### 更多效果

- series

```js
series: [{
	type: "funnel", //漏斗图
	data: [
		{value:60,name:"美食"},
		{value:50,name:"数码"},
		{value:80,name:"家电"},
		{value:90,name:"生活"},
		{value:100,name:"日用"}
	],
	left: "10%",
	sort: "ascending", //排序 默认下小 ascending上小 none根据数据
	itemStyle: {
		borderColor: "pink",
		borderWidth: 3
	},
	label: {
		show: true,
		position: "inside"
	},
	emphasis: {
		label: {
			fontSize: 30
		}
	}
}]
```



#### 仪表盘

- option

```js
let option = {
	series: [{
		type: "gauge", //仪表盘
		data: [{
			value: 45,
			name: "提示信息"
		}],
		detail: {
			valueAnimation: true //动画
		},
		progress: {
			show: true //外圈有颜色变化
		}
	}]
}
```



#### 关系图

```js
import * as echarts from "echarts";
export default {
	data() {
		return {
			list: [ //创建关系图的节点数据
				{
					name: "秦磊",
					id: "1",
					symbolSize: 30 //点的大小
				},
				{
					name: "许泽远",
					id: "2",
					symbolSize: 30
				},
				{
					name: "顾晨茜",
					id: "4",
					symbolSize: 30
				},
				{
					name: "孔建政",
					id: "3",
					symbolSize: 30
				},
				{
					name: "邹子璇",
					id: "5",
					symbolSize: 30
				}
			],
			// 关系数据
			num: [{
					source: "1", //边的节点名称
					target: "2", //目标节点名称
					relation: {
						name: "老婆",
						id: "1"
					}
				},
				{
					source: "1", //边的节点名称
					target: "2", //目标节点名称
					relation: {
						name: "兄弟",
						id: "4"
					}
				},
				{
					source: "4", //边的节点名称
					target: "1", //目标节点名称
					relation: {
						name: "兄弟",
						id: "1"
					}
				},
				{
					source: "3", //边的节点名称
					target: "5", //目标节点名称
					relation: {
						name: "姐妹",
						id: "1"
					}
				},
			]
		}
	},
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let option = {
			series: [{
				type: "graph", //关系图
				data: this.list,
				layout: "force", //引导布局
				itemStyle: {
					color: "#dd7694" //点的颜色
				},
				label: { //图形上的文字
					show: true,
					position: "bottom",
					distance: 6, //距离图形的位置
					fontSize: 16,
					align: "center"
				},
				force: {
					repulsion: 100, //点与点的间距
					qravity: 0.01, //距离中心的距离
					edgeLength: 200 //俩边的距离
				},
				links: this.num, //关系
				edgeLabel: {
					show: true,
					position: "middle",
					formatter: (params) => {
						return params.data.relation.name
					}
				}
			}]
		}
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



#### 树形图



##### 基本配置

```js
import * as echarts from "echarts";
export default {
	data() {
		return {
			list: { //最外层的数据就是数据的根节点
				name: "根节点", //名字
				children: [{
					name: "层级2",
					children: [{
							name: "层级3-1",
							children: [{
									name: "数据1",
									value: 2345
								},
								{
									name: "数据2",
									value: 6545
								},
								{
									name: "数据3",
									value: 2945
								},
								{
									name: "数据4",
									value: 7215
								},
							]
						},
						{
							name: "层级3-2",
							children: [{
									name: "数据1",
									value: 5435
								},
								{
									name: "数据2",
									value: 6455
								},
								{
									name: "数据3",
									value: 2678
								},
								{
									name: "数据4",
									value: 2967
								},
							]
						}
					]
				}]
			}
		}
	},
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		let option = {
			tooltip: {
				trigger: "item"
			},
			series: [{
				type: "tree", //树形图
				data: [this.list],
				symbolSize: 15,
				label: {
					position: "left",
					verticalAlign: "middle", //垂直位置
					align: "center",
					fontSize: 10
				},
				leaves: {
					label: {
						position: "right",
						verticalAlign: "middle",
						align: "center",
					}
				},
				emphasis: { //聚焦
					focus: "descendant"
				}

			}]
		};
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



##### 方向切换

```js
let option = {
	tooltip: {
		trigger: "item",
	},
	series: [{
		type: "tree", //树形图
		data: [this.list],
		symbolSize: 15,
		// left:"20%",//位置
		// 设置布局方向
		orient: "TB", //T上,B下,LR左右,TB就是上下
		label: {
			// rotate:90,//文字旋转度数
			position: "left",
			verticalAlign: "middle", //垂直位置
			align: "center",
			fontSize: 10
		},
		leaves: {
			label: {
				position: "right",
				verticalAlign: "middle",
				align: "center",
			}
		},
		emphasis: { //聚焦
			focus: "descendant"
		}

	}]
};
```



### 高级配置



#### 数据排序

```js
let option = {
	dataset: [{
			// 数据的分类
			dimensions: ["类别", "数量"],
			// 分类数据
			source: [
				["美食", 213],
				["日化", 25],
				["科技", 234],
				["蔬菜", 123],
				["杂项", 73],
			]
		},
		{
			transform: {
				type: "sort",
				config: {
					dimension: "数量",
					order: "desc" //基于数量排序
				}
			}
		},
	],
	xAxis: {
		type: "category",
		axisLabel: {
			interval: 0, //间隔
			rotate: 30, //倾斜
		}
	},
	yAxis: {},
	series: [{
		type: "bar", //柱状图
		encode: { //映射
			x: "类别",
			y: "数量",
		},
		datasetIndex: 1,
	}]
};
```



#### 内置主题设置

> echarts有内置主题，light和dark

```js
//初始化的时候可以改

let myEcharts = this.$echarts.init(this.$refs.myChart,"dark");

let myEcharts = this.$echarts.init(this.$refs.myChart,"light");
```



#### 自定义主题设置

> [官网主题下载](https://echarts.apache.org/zh/download-theme.html)

1. 复制json
2. 在项目中新建js文件`export let essos =`粘贴
3. vue文件里面`import {essos} from "../assets/essos.js";`
4. vue里面使用主题`let myEcharts = this.$echarts.init(this.$refs.myChart, essos);`



#### 地图展示



##### 中国地图

> [百度地图拾取坐标系统](http://api.map.baidu.com/lbsapi/getpoint/index.html)

1. 复制[json](http://datav.aliyun.com/portal/school/atlas/area_selector)
2. 在项目中新建js文件`export let mapData =`粘贴
3. vue文件里面`import {mapData} from "../assets/mapData.js";`

```vue
<template>
	<div ref="myChart" id="myChart"></div>
	<!-- 中国地图展示 -->
</template>

<script>
	import * as echarts from "echarts";
	import {mapData} from "../assets/mapData.js";
	export default {
		mounted() {
			// 初始化
			let myEcharts = this.$echarts.init(this.$refs.myChart);
			// 注册当前使用的地图名
			echarts.registerMap("chinaMap", mapData);
			//第一个自己取，第二个是引入的名字
			let option = {
				geo: { // 地理坐标组件
					type: "map",
					map: "chinaMap",
					roam:true,//平移
					zoom:5,//默认缩放比例
					center: [117.088168,36.205158],//初始化中心点 经纬度自己查
				}
			};
			// 设置配置项
			myEcharts.setOption(option);
		}
	}
</script>

<style>
	#myChart {
		width: 600px;
		height: 600px;
		border: 1px solid pink;
	}
</style>
```



##### 省份地图和效果优化

```js
import * as echarts from "echarts";
import {shanxiMap} from "../assets/shanxiMap.js";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		// 注册当前使用的地图名
		echarts.registerMap("shanxiMap", shanxiMap);
		//第一个自己取，第二个是引入的名字
		let option = {
			geo: { // 地理坐标组件
				type: "map",
				map: "shanxiMap",
				roam: true, //平移
				label: { //显示的文字样式  
					show: true, //默认显示文字
					color: "#80a492",
					fontSize: 10
				},
				itemStyle: {
					areaColor: "#fff799" //地区颜色
				}

			}
		};
		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



##### 地图标记设置与效果

```js
import * as echarts from "echarts";
import {mapData} from "../assets/mapData.js";
export default {
	mounted() {
		// 初始化
		let myEcharts = this.$echarts.init(this.$refs.myChart);
		// 注册当前使用的地图名
		echarts.registerMap("chinaMap", mapData);
		//第一个自己取，第二个是引入的名字
		let option = {
			geo: { // 地理坐标组件
				type: "map",
				map: "chinaMap",
				roam: true, //平移
			},
			series: [{
					type: "scatter", //散点图
					data: [{
						name: "北京市", //数据项的名字
						value: [
							116.46, 39.92, 4000
						]
					}],
					coordinateSystem: "geo", //以坐标系模式设置
					symbolSize: 30, //点的大小
					// label:{
					// 	show:true,//点上的数据是坐标
					// }
				},
				{
					type: "effectScatter", //涟漪效果的散点图
					coordinateSystem: "geo", //以坐标系模式设置
					data: [{
						name: "西安市", //数据项的名字
						value: [
							108.95, 34, 26
						]
					}],
					// 设置涟漪效果的相关配置
					rippleEffect: {
						number: 2, //波纹数量
						scale: 4 //波纹大小
					},
					itemStyle: {
						color: "red"
					}
				}
			]
		}

		// 设置配置项
		myEcharts.setOption(option);
	}
}
```



#### 图表自适应大小

```js
// 设置配置项
myEcharts.setOption(option);

// 在这个下面写
			
//监听页面大小的改变
window.addEventListener("resize",()=>{
	console.log("浏览器大小变化了");
	myEcharts.resize();//图表大小随着页面变化
})
```



##### 加载动画效果

> [千锋视频(有json-server自己模拟axios数据教学)](https://www.bilibili.com/video/BV14u411D7qK?p=38&spm_id_from=pageDriver&vd_source=9928f2a9263e4b4f8d78f76eb5a79a03)

```js
mCharts.showLoading()		//显示加载动画
mCharts.hideLoading()		//隐藏加载动画

//使用场景：
//发送请求前：mCharts.showLoading()	
//发送请求成功的回调：mCharts.hideLoading()
```

