## CSS 三大特性

### 层叠性

- 就是后写的样式覆盖先写的
- 只有冲突才会层叠

### 继承性

- 例如div内部的p标签会继承div的样式

- 但不是所有的都继承

- 主要继承的是和文字有关的样式

- text-，font-，line-，color等

  - ```html
    body{
    	font: 12px/1.5;
    	<!-- 意思：行高是12px的1.5倍 -->
    };
    div{
    	font 16px;
    	<!-- 行高是16px的1.5倍-->
    }
    ```



### 优先级

- 看权重

| 选择器                 | 权重   |
| ---------------------- | ------ |
| 继承或者*              | 0      |
| 元素（如body，div）    | 1      |
| 类（class="lei"，.lei) | 10     |
| id（id="ai"，#ai)      | 100    |
| 行内样式               | 1000   |
| !important             | 无穷大 |

## 盒子

![盒子模型](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fwww.pianshen.com%2Fimages%2F7%2F99f4bfe569a863057769ae1fc64516af.png&refer=http%3A%2F%2Fwww.pianshen.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1652102521&t=c08b0175ec775a6a77957f8b126c4d6d)

- [border-style](https://interactive-examples.mdn.mozilla.net/pages/css/border-style.html)
  - 主要用的是下面三种
  - solid  实线
  - dashed  虚线
  - dotted  点线
-  border的复合写法没有顺序要求
  - size，style，color
- 也可以上下左右分别设置 

### 清除内外边距

- ```html
  *{
  	margin=0;
  	padding=0;
  }
  ```

### 圆角边框

- border-radius:length;
- 圆形的话就是length为边长的一半
- 圆角矩形则length为高度的一半
- border-radius:10px 20px 30px 40px；从左上开始顺时针的

### 盒子阴影

- x偏移量 | y偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色  
-  **box-shadow**: 2**px** 2**px** 2**px** 1**px** **rgba**(0, 0, 0, 0.2);
- 最后加一个inset就是改成内阴影

