# CSS学习笔记

## CSS背景属性

### 一些后缀对应

|属性|作用|备注|备注|
|:--:|:--:|:--:|:--:|
|background-color|背景颜色|||
|background-image|背景图片|url||
|background:rgba(0,0,0,0.5);|背景颜色半透明|前三个代表颜色，最后一个是透明度，0可省略||
|background-position|背景位置|center right 即处于中右|也可以10px 20px，就是离左10，右20|
|background-clip|暂未学习|||
|background-repeat|背景重复方式|reapeat 重复（no同理）||
|background-size|背景大小|宽度 高度|auto以背景图片的比例缩放背景图片|
|background-size|背景大小|cove 缩放至覆盖背景|contain缩放至可以全部放进背景区，可能留白|
|background-attachment|| fixed 背景固定|scroll 滚动，local 滚动|

### background顺序

background: 颜色 图片地址 平铺 图像滚动 图片位置

个人感觉自己习惯写法就好，可能一行太长也不易阅读

***

## padding

|padding||
|:--:|:--:|
|padding-top|上填充|
|padding-right|右填充|
|padding-bottom|下填充|
|padding-left|左填充|

- padding:25px 50px 75px 100px;
  - 即上右下左填充，也叫内边距
- padding:25px 50px 75px;
  - 上，左右，下
- padding:25px 50px;
  - 上下，左右
- padding:25px;
  - 全部

### margin

marigin是外边距，使用方法几乎同padding