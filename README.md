## Css基础
### 1.Css选择器
#### (1)普通选择器
1. 不同Css的导入
```js
<link rel="stylesheet" href="./index.css">
<style>
    @import url('./index.css');
</style>
```
2. 基本选择器
```js
*选择器
标签选择器
id选择器
class选择器
```
3. 结构选择器
```js
后代选择器 div p // 选择 div 元素内部的所有 p 元素
子元素选择器 div>p	// 选择父元素为 div 元素的所有 p 元素
兄弟选择器 div+p // 选择紧接在 div 元素之后的 p 元素
后面兄弟选择器 p~ul	// 选择 p 元素同级并在 p 元素后面的所有 ul 元素
```
4. 属性选择器
```js
[title] // 带有 title属性所有元素
[title=_blank] // title属性 等于"_blank" 的所有元素
[title~=a] // title属性包含单词 "a" 的所有元素
[title|=hd] //title 属性值为 "hd"的单词，或hd-cms 以-连接的的独立单词
a[src*="a"]	//src 属性中包含 "a" 字符的每个 a 元素
a[src^="https"]  // src 属性值以 "https" 开头的每个 a 元素
a[src$=".jpeg"] // src 属性以 ".jpeg" 结尾的所有 a 元素
```
#### (2)伪类选择器
1. 动作伪类
```js
a:link // 选择所有未被访问的链接
a:visited // 选择所有已被访问的链接
a:hover // 鼠标移动到元素上时
a:active // 点击正在发生时
input:focus // 选择获得焦点的 input 元素

div:text {
	color: red; // 对应锚点控制选择器
}
<a href="#text">text</a>
<div></div>
<div id="text">
   text 
</div>
```
2. 结构伪类选择器
```js
:root // 选择文档的根元素即 html
:empty // 选择没有内容和空白的元素
span p:first-child // 选择span中元素中p标签,取第一个 
span p:first-of-type //选择类型是 p 的第一个元素
span p:last-child // 选择span中元素中p标签,取最后一个 
span p:last-of-type //选择类型是 p 的最后一个元素
span p:only-child // 选择是唯一子元素的p 标签
span p:only-of-type //  选择同级中类型是p的唯一子元素
span p:nth-child(n) // 选择span中元素中p标签,取第n个 
span p:nth-of-type(n) //选择类型是 p 的第n个元素
span p:nth-last-child(n)  // 选择span中元素中p标签,取倒数第n个 
span p:nth-last-of-type(n) //选择类型是 p 的倒数第n个元素

span p:nth-child(2n)// 选择偶数
span p:nth-child(2n+1)// 选择奇数
span p:nth-child(n+3)// 从第三个开始设置样式
span p:nth-child(-n+3) // 设置前三个元素

ul li:not(:nth-child(1)) // 排除第一个 li 元素
```
3. 表单伪类选择器
```js
input:enabled // 选择每个启用的 input 元素
input:disabled // 选择每个禁用的 input 元素
input:checked // 选择每个被选中的 input 元素
input:required // 包含required属性的元素
input:optional // 不包含required属性的元素
input:valid // 验证通过的表单元素
input:invalid // 验证不通过的表单
```
4. 文本伪类操作
```js
    p::first-letter //选择每个 p 元素的首字母 
    p::first-line //选择每个 p 元素的首行 
    p::before //在每个 p 元素的内容之前插入内容
    p::after //在每个 p 元素的内容之后插入内容

  //   标题插入内容
  <style>
    h2::before {
      content: attr(title);
    }
  </style>
<body>
  <h2 title="标题"></h2> 
</body>
```
### 2.文本控制
#### (1)文本基础
1. 设置字体
```js
<style>
    @font-face {
      font-family: 'font';
      src: url("SourceHanSansSC-Light.otf") format("opentype"),
    }
    h2 {
      font-family: font;
    }
  </style>
```
2. 字体风格
```js
// 字重
font-weight: normal | bold | bolder | lighter | 100 ~900; 
// 字号
font-size:20px| 2em |200%  //em % 参照父级
// 字色
color:red;
// 行高
line-height: 2em;
// 倾斜
font-style: italic|normal;
```
#### (2)文本样式
1. 字母大小写转换
```js
font-variant: small-caps; // 全部转换成大写(小型大写)
text-transform: capitalize; // 首字母大写
text-transform: uppercase; // 全部大写
text-transform: lowercase; // 全部小写
```
2. 文本线条
```js
text-decoration: underline; // 下划线
 text-decoration: line-through; // 中线(删除线)
text-decoration: overline; // 上划线
text-decoration: none; // 清除划线
```
3. 文本阴影
```js
// 参数顺序为：颜色，水平偏移，垂直偏移，模糊度
 text-shadow: red 1px 1px 5px;
```
4. 空白控制
```js
<pre>a   b   c</pre> // pre标签保留空白
  white-space: pre; // 类似pre标签
  white-space:nowrap; // 禁止换行
  white-space:pre-wrap; // 保留空白，保留换行符
  white-space:pre-line; // 空白合并，保留换行符
```
5. 文本溢出控制
```js
/**溢出文本容器后换行处理 */
div {
    overflow-wrap: break-word;
    width: 300px;
    border: 2px solid pink;

}
/**单行文本溢出控制 */
div{
    width: 300px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
/**多行文本溢出控制  */
 div {
      width: 300px;
      /**换行*/
      overflow-wrap: break-word;
      overflow: hidden;
      display: -webkit-box;
      -webkit-box-orient: vertical;
      -webkit-line-clamp: 2;
    }
```
#### (3)段落控制
1. 文本缩进
```js
 text-indent: 2em; // 参照字体
```
2. 文本对齐
```js
/**水平对齐 */
text-align: left|right|center;
/**垂直对齐 */
div p {
      display: inline-block;
      width: 100px;
      height: 100px;
      background-color: red;
      vertical-align: middle;
    }
```
3. 字符间隔
```js
letter-spacing: 3em; //字符间距
word-spacing: 2em; //单词间距
```
4. 排版模式
```js
 writing-mode: vertical-rl; // 水平方向自上而下的书写方式
 writing-mode: horizontal-tb //垂直方向自右而左的书写方式
 writing-mode: vertical-lr // 垂直方向内内容从上到下，水平方向从左到右
```
### 3.盒子模型
#### (1)盒子边距
1. 外边距内边距
```js
// 边距顺序依次为：上、右、下、左。
margin:上、右、下、左。
padding:上、右、下、左。
// 边距顺序依次为：上下，左右
 margin: 0 auto;// 水平居中
 margin-left:-40px;// 负值溢出
```
2. 外边距合并
```js
 <style>
    .div1 {
      margin: 0 auto;
      width: 200px;
      height: 200px;
      border: 1px solid red;
      margin-bottom: 40px;
    }

    .div2 {
      margin-top: 30px;
      margin: 0 auto;
      width: 200px;
      height: 200px;
      border: 1px solid black;
    }
</style>

 // 边距大的那一个
<body>
  <div class="div1">

  </div>
  <div class="div2">

  </div>
</body>
```
3. 设置盒模型
```js
  box-sizing: content-box; // 标准盒子模型
  box-sizing: border-box; // 怪异盒子模型 把boder和padding属性都包含在内容区中。
```
#### (2)盒子边框
1. 边框样式
```js
// 样式顺序为上、右、下、左
 border-style: none // 无边框
 border-style: dotted// 定义点状边框
 border-style:dashed// 定义虚线
 border-style:solid // 定义实线
 border-style:double// 定义双线
 border-style:groove // 定义 3D 凹槽边框
 border-style:ridge // 定义 3D 垄状边框
 border-style:inset // 定义 3D inset 边框
 border-style:outset // 定义 3D outset 边框
```
2. 边框圆角
```js
// 顺序为:上左,上右,下左,下右
  border-radius: 10px 30px 50px 100px
// 行元素绘制圆角
 <style>
    em {
      border-radius: 50%;
      border-bottom: solid 2px red;
    }
  </style>

<body>
<em>asdasdas</em>
</body>
```
3. 轮廓线
```js
outline-style: groove;
outline-width: 20px;
outline-color: red;

outline: 20px solid red;

input{
   outline: none;
}

```
#### (3)元素的隐藏
1. display的属性
```js
display:none // 隐藏元素(相当于去除)
display:block // 显示为块元素
display:inline // 显示为行元素，不能设置宽/高
display:inline-block	//行级块元素，允许设置宽/高
```
2. 隐藏元素
```js
/**display:none是会有回流和重绘 */
display:none // 不保留物理空间
/** visibility: hidden; 不会有回流 */
visibility: hidden; // 保留物理空间
```
3. 溢出控制
```js
 overflow-y: auto; //根据内容自动处理滚动条
 overflow-y: scroll; //显示滚动条
 overflow-y:hidden; //溢出内容隐藏
 // 文本溢出处理看 文本控制内容
```
#### (4)盒子的尺寸控制
1. 撑满盒子
```js
main {
    background: #9b59b6;
    height: 100px;
    box-sizing: border-box;
}

div {
   background: #e67e22;
   width: -webkit-fill-available;
   height: -webkit-fill-available;
}

   <main>
    <div>abcdef</div>
  </main>
```
2. 内容自适应
```js
<style>
    main {
      background: #9b59b6;
      height: 100px;
      box-sizing: border-box;
    }

    div {
      background: #e67e22;
      width:fit-content;
    }
  </style>

<body>
  <main>
    <div>abcdef</div>
  </main>
</body>

```
3. 容器尺寸按最小元素宽度
```js
 <style>
    main {
      background: #9b59b6;
      height: 100px;
      box-sizing: border-box;
      width: min-content;
    }

    div {
      background: #e67e22;
      padding: 10px;
      margin-top: 10px;
    }
  </style>

<body>
  <main>
    <div>abcdef</div>
    <div>abcdefghiklmnopqrst</div>
  </main>
</body>
```
4. 容器尺寸按最大元素宽度
```js
<style>
    main {
      background: #9b59b6;
      height: 100px;
      box-sizing: border-box;
      width: min-content;
    }

    div {
      background: #e67e22;
      padding: 10px;
      margin-top: 10px;
    }
  </style>

<body>
  <main>
    <div>abcdef</div>
    <div>abcdefghiklmnopqrst</div>
  </main>
</body>
```
#### (5)盒子阴影和多边形
1. 基本使用
```js
// 水平偏移,垂直偏移,模糊度,颜色
box-shadow: 10px 10px 5px rgba(100, 100, 100, .5);
```
2. 点击出现阴影
```js
 <style>
    main {
      margin: 0 auto;
      width: 100px;
      height: 100px;
      box-shadow: 5px 5px 2px rgba(100, 100, 100, .5);
    }

    main:active {
      box-shadow: 10px 10px 5px rgba(100, 100, 100, .5);
    }
  </style>


<body>
  <main>

  </main>
</body>
```
3. 设置多边形
```js
  clip-path: circle(50% at center); // 设置圆形
  clip-path: ellipse(50% 80% at 100% 0);
  clip-path: polygon(50% 0, 100% 100%, 0 100%) // 设置三角形(多边形)
```
### 4.背景处理
#### (1)背景样式
1. 背景图片/颜色
```js
background-color: red;
background-image: url(icon-s.jpg); // png| gif |jpeg
```
2. 背景裁切
```js 
 background-clip: content-box	; // 只在内容区域显示
 background-clip: padding-box	; // 不含边框，包括内边距
 background-clip: border-box	// 包括边框
```
3. 背景图片重复
```js
background-repeat: repeat	// 水平、垂直重复
background-repeat: repeat-x	// 水平重复
background-repeat: repeat-y	// 垂直重复
background-repeat: no-repeat	// 不重复
background-repeat: space	// 背景图片对称均匀分布
```
4. 背景滚动
```js
background-attachment: scroll; // 背景滚动
background-attachment: fixed; // 背景固定
```
5. 背景定位
```js
background-position: center; // 居中
background-position: 50% 50%;
background-position: right center;
```
6. 背景尺寸
```js
background-size: 100% 100%;
background-size:cover  // 背景完全覆盖
background-size:contain	// 图片不溢出的放在容器中
```
7. 组合属性
```js
 // 颜色 url 重复 定位 滚动
background: red url(xj-small.png) no-repeat right 50% fixed;
```
#### (2)背景渐变
1. 线性渐变
```js
 background: linear-gradient(red, green); // 默认重上到下
 background: linear-gradient(90deg, red, green);// 按角度进行渐变
 background: linear-gradient(to right, red, green) // 向一个方向渐变
 background: linear-gradient(red, rgb(0, 0, 200), green, rgba(122, 211, 100, 0));// 多色渐变
```
2. 径向渐变
```js
  background: radial-gradient(red, blue, green); // 从里面向外
  background: radial-gradient(100px 200px, red, blue, green); //设置渐变宽高
  background: radial-gradient(at bottom left, red, blue); // 设置左下渐变
   background: radial-gradient(at 50% 100%, red, blue); // 底部中间渐变
```
3. 渐变标识位
```js
  background: linear-gradient(45deg, red 50%, blue 60%); // 50%红色开始渐变
 /**绘制太阳 */
   main {
      margin: 0 auto;
      width: 500px;
      height: 500px;
      background: radial-gradient(red 20%, yellow 40%, black 70%)

    }
```
4. 渐变的中间点
```js
background: linear-gradient(45deg, red, 50%, blue); // 50%中间点
```
5. 渐变重复
```js
  background: repeating-linear-gradient(90deg, blue, 25px, black 25px, 25px, red 50px) // 纯色渐变重复格子
  background: repeating-radial-gradient(50px 50px, red, 25px, black 25px, 25px, yellow 50px)  // 纯色渐变圆轮

```
6. 文字渐变
```js
<style>
    span {
      background: linear-gradient(to right, red, purple);
      -webkit-background-clip: text;
      color: transparent;
      font-size: 30px;
    }
  </style>

<body>
  <span>
    渐变文字
  </span>
</body>
```
### 5.数据的处理
#### (1)表格处理数据
1. 表格标题/内容位置
```js
 <style>
    table caption {
      background: black;
      color: white;
      padding: 10px;
      /**设置表格的标题位置 top/botton */
      caption-side: top;  
    }
    table tr td {
      width: 100px;
        /**表格内容水平居中 */
      text-align: center;
      height: 50px;
      /**表格内容垂直居中 top/middle/bottom	 */
      vertical-align: top;
    }
  </style>

<body>
  <table border="1">
    <caption>aaaaa</caption>
    <tr>
      <td>bbbbb</td>
      <td>ccccc</td>
    </tr>
  </table>
</body>
```
2. 表格边框
```js
 border-spacing: 50px 10px;// 设置单元格间距
 border-collapse: collapse; // 设置边框合并成一条线
 empty-cells: hide; // 隐藏空的单元格
 /**无边框表格 */
  table,
    td {
  border: none;
  border-collapse: collapse;
    }
```
3. 表格的综合案例
```js
<style>
    table,
    td {
      border: none;
      border-collapse: collapse;
      margin: 50px auto;
    }

    table td {
      border-top: 3px groove red;
    }

    table tr td {
      width: 300px;
      height: 50px;
      cursor: pointer;
      vertical-align: middle;
      text-align: center;
    }

    table tr:hover {
      background-color: red;
    }
  </style>

<body>
  <table border="1">
    <thead>
      <tr>
        <td>编号</td>
        <td>标题</td>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>bbbbb</td>
        <td>ccccc</td>
      </tr>
      <tr>
        <td>ddddd</td>
        <td>eeeee</td>
      </tr>
    </tbody>
  </table>
</body>
```
#### (2)列表处理数据
1. 定义列表样式
```js
 list-style-image: radial-gradient(10px 10px, red, black);// 定义符号渐变或者图片
 list-style-type: none; // 隐藏符号样式
 list-style-position: inside; // 控制符号显示在内容外面还是内部 inside/outside	
 list-style: circle inside; // 组合样式
```
2. 定义好看的列表
```js
 <style>
    ul {
      margin: 100px 100px;
      list-style-type: none;
    }

    ul li {
      background-image: radial-gradient(red, yellow);
      margin: 20px;
      padding: 10px;

    }
  </style>

<body>
  <ul>
    <li>1</li>
    <li>1</li>
    <li>1</li>
    <li>1</li>
    <li>1</li>
  </ul>
</body>
```
#### (3)追加内容
1. 提取属性追加
```js
<style>
    h2::after {
      content: attr(title);
      color: rebeccapurple
    }
     h2::before {
      content: attr(title);
      color: rebeccapurple
    }
</style>

<body>
  <h2 title="标题">|</h2>
</body>

```
2. 鼠标放上提示
```js
  <style>
    a:hover:before {
      content: attr(href);
      background-color: gainsboro;
      position: absolute;
      top: 1.3em;
      color: rebeccapurple
    }
  </style>

<body>
  <a href="www.baidu.com">百度一下</a>
</body>
```
3. 表单的提示
```js
  <style>
    input {
      border: none;
      outline: none;
      width: 100%;
    }

    .field {
      position: relative;
      margin: 100px;
    }

    .field::after {
      content: "";
      background-image: linear-gradient(90deg, white, red, green, blue, white);
      display: block;
      height: 3px;
    }

    .field:hover::before {
      content: attr(data-placeholder);
      position: absolute;
      top: -20px;
      left: 0px;
      color: #555;
      font-size: 12px;

    }
  </style>

<body>
  <div class="field" data-placeholder="请输入少于100字的标题">
    <input type="text" />
  </div>
</body>
```
### 6.浮动布局
#### (1)浮动
1. 脱离文档流
```js
float: left	// 向左浮动
float: right // 向右浮动
float: none	// 不浮动
```
2. 浮动边界
```js
// 浮动元素边界不能超过父元素的 padding
main {
  width: 400px;
  border: 1px solid black;
  height: 200px;
  padding: 20px;
}
section {
  width: 100px;
  height: 100px;
  border: 1px solid red;
  float: left;
}

<body>
  <main>
    <section></section>
  </main>
</body>

```
3. 浮动转块
```js
// 浮动元素可以设置宽高
span {
  float: left;
  width: 100px;
  height: 100px;
  border: 1px solid red;

}


<body>
  <main>
    <span></span>
  </main>
</body>
```
#### (2)清除浮动
1. clear清除浮动影响
```js
// 使用场景，一个元素受到另一个元素的浮动影响，不适用于父级元素
<style>
    main {
      width: 400px;
      border: 1px solid black;
      padding: 20px;

    }
    section {
      width: 100px;
      height: 100px;
      border: 1px solid red;

    }
    section:nth-child(1) {
      float: left;
    }
    section:nth-child(2) {
      clear: both;
    }
  </style>

<body>
  <main>
    <section></section>
    <section></section>
  </main>
</body>
```
2. after伪类消除高度塌陷
```js
 <style>
    main {
      width: 400px;
      border: 1px solid black;
      padding: 20px;
    }

    section {
      width: 100px;
      height: 100px;
      border: 1px solid red;
      float: left;
    }

    main::after {
      content: '';
      display: block;
      clear: both;
    }
  </style>


<body>
  <main>
    <section></section>
  </main>
</body>
```
3. BFC消除高度塌陷
```js
// 创建bfc的盒子会把浮动元素也计算上去 ,浮动元素不会遮住bfc元素
<style>
    main {
      width: 400px;
      border: 1px solid black;
      padding: 20px;
      /*  hidden */
      overflow: auto;
      /* inline-block flex grid*/
      display: flow-root;

    }

    section {
      width: 100px;
      height: 100px;
      border: 1px solid red;
      float: left;
    }
  </style>


<body>
  <main>
    <section></section>
  </main>
</body>

```
#### (3)形状浮动
1. 环绕距离控制
```js
  <style>
    p span {
      float: left;
      width: 100px;
      height: 100px;
      margin: 30px;
      background-color: red;
      shape-outside: margin-box;
      /*  
      margin-box	外边距环绕 
      padding-box 内边距环绕
      border-box 边线环绕 
      content-box 内容环绕
      */
    }
  </style>

<body>
  <p>
    <span></span>
    来自百度高中免费听课 重难点视频随时听反复看,针对问题及时解决,高效学习简单学习网,15年精准教学,让学习更简单,
    让教育更公平,注册即可 …广告 上个月有超过 1 万名用户访问了 jd100.com
    热门课程: 同步基础 · 同步提高 · 满分冲刺学习方式: 随时听 · 反复看 · 精准学
  </p>
</body>
```
2. 环绕模式
```js

  <style>
    p span {
      float: left;
      width: 100px;
      height: 100px;
      background-color: red;
      clip-path: circle(50% at center);
      /*
        shape-outside:circle	圆形环绕
        shape-outside:ellipse	椭圆环绕
        shape-outside:url	图片环绕
        shape-outside:polygan	多边环绕
      */
      shape-outside: circle(50%) padding-box;
    }
  </style>


<body>
  <p>
    <span></span>
    来自百度高中免费听课 重难点视频随时听反复看,针对问题及时解决,高效学习简单学习网,15年精准教学,让学习更简单,
    让教育更公平,注册即可 …广告 上个月有超过 1 万名用户访问了 jd100.com
    热门课程: 同步基础 · 同步提高 · 满分冲刺学习方式: 随时听 · 反复看 · 精准学
  </p>
</body>

```
### 7.定位布局
#### (1)相对/绝对定位
1. 定位类型
```js
// 子绝父相
  position:relative	//相对定位
  position:absolute	//绝对定位
  position:fixed	//固定定位
  position:sticky	//粘性定位

top	//距离顶边
bottom	//距离下边
left	//距离左部
right	//距离右边

```
2. 相对定位
```js
// 相对定位是相对于元素原来的位置控制，当元素发生位置偏移时，原位置保留
  <style>
    main {
      margin-top: 100px;
      border: 1px solid #ccc;
      display: flow-root;
    }

    div {
      width: 100px;
      height: 100px;
      background-color: red;
      position: relative;
    }
  </style>

<body>
  <main>
    <div>
    </div>
  </main>
</body>
```
3. 绝对定位以及参照物
```js
 position: absolute; // 绝对定位
 // 父级元素设置了定位属性，绝对定位子元素将参数此父元素进行定位(就近原则)
```
4. 定位居中设置
```js
  <style>
    main {
      width: 500px;
      height: 500px;
      border: 2px solid #ccc;
      position: relative;
    }

    div {
      width: 100px;
      height: 100px;
      background-color: red;
      position: absolute;
      left: 50%;
      top: 50%;
      margin-left: -50px;
      margin-top: -50px;
    }
  </style>

<body>
  <main>
    <div>
    </div>
  </main>
</body>
```
#### (2)层级效果
1. 基本使用
```js
// z-index可以让图片显示
  <style>
    main {
      width: 400px;
      height: 400px;
      border: 3px solid red;
      margin: 0 auto;
      position: relative;
    }

    span {
      position: absolute;
      top: 10px;
      background-color: red;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      text-align: center;
      line-height: 30px;
      z-index: 1;
    }

    section {
      width: 100%;
      height: 100%;
      background-color: black;
      cursor: pointer;
    }
    section:hover {
      z-index: 2;
    }
  </style>

<body>
  <main>
    <span>热</span>
    <section>
    </section>
  </main>
</body>
```
2. 实现购物车效果
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    main {
      margin: 300px auto;
      width: 200px;
      position: relative;
    }

    section {
      height: 50px;
      border: 1px solid #ddd;
      text-align: center;
      line-height: 3em;
      cursor: pointer;
      background-color: white;

    }

    article {
      height: 50px;
      border: 1px solid #ddd;
      background-color: white;
      text-align: center;
      line-height: 3em;
      width: 300px;
      position: absolute;
      z-index: -1;
      right: 0;
      top: 50px;
      display: none;
    }

    main:hover section{
      border-bottom: none;
    }
    main:hover article {
      display: block;
    }
  </style>


<body>
  <main>
    <section>我的购物车</section>
    <article>购物车中没有商品</article>
  </main>
</body>
```
#### (3)固定/粘性定位
1. 固定定位
```js
// 元素相对于页面固定定位在某个位置，固定定位元素不会在滚动时改变位置 ，
<style>
    body{
      height: 3000px;
    }
    header {
      width: 100%;
      height: 40px;
      background-color: red;
      position: fixed;
    }
  </style>


<body>
  <header></header>
</body>
```
2. 粘性定位
```js
  <style>
    body {
      height: 3000px;
    }

    header {
      width: 100%;
      height: 40px;
      background-color: red;
      position: fixed;
      top: 0;
      z-index: -1;
    }

    nav {
      width: 80%;
      margin: auto;
      height: 40px;
      background-color: pink;
      margin-top: 400px;
      position: sticky;
      top: 0;
    }
  </style>


<body>
  <header>头部</header>
  <nav>导航</nav>
</body>

```
### 8.flex布局
#### (1)弹性盒子(整体)
1. flex布局的声明
```js
display:flex // 块级弹性盒子
display:inline-flex // 行级弹性盒子
```
2. flex-direction盒子排列方向
```js
flex-direction:row	//从左到右水平排列元素（默认值）
flex-direction:row-reverse	//从右向左排列元素
flex-direction:column	//从上到下垂直排列元素
flex-direction:column-reverse	//从下到上垂直排列元素
```
3. flex-wrap溢出换行
```js
flex-wrap: nowrap	//元素不拆行或不拆列（默认值）
flex-wrap: wrap	//容器元素在必要的时候拆行或拆列。
flex-wrap: wrap-reverse	//容器元素在必要的时候拆行或拆列，但是以相反的顺序
```
4. flex-flow组合属性
```js
flex-flow: 排列方向 折行
```
5. justify-content主轴元素排列
```js
justify-content:flex-start	//元素紧靠主轴起点
justify-content:flex-end	//元素紧靠主轴终点
justify-content:center	//元素从弹性容器中心开始
justify-content:space-between	//第一个元素靠起点，最后一个元素靠终点，余下元素平均分配空间
justify-content:space-around	//每个元素两侧的间隔相等。所以，元素之间的间隔比元素与容器的边距的间隔大一倍
justify-content:space-evenly	//元素间距离平均分配
```
6. align-items交叉轴元素排列
```js
 align-items:stretch	//元素被拉伸以适应容器（默认值）
 align-items:center	//元素位于容器的中心
 align-items:flex-start	//元素位于容器的交叉轴开头
 align-items:flex-end	//元素位于容器的交叉轴结尾
```
7. align-content多行交叉轴元素排列
```js
align-content:stretch	//将空间平均分配给元素
align-content:flex-start	//元素紧靠交叉轴起点
align-content:flex-end	//元素紧靠交叉轴终点
align-content:center	//元素从弹性容器中心开始
align-content:space-between	//第一个元素靠起点，最后一个元素靠终点，余下元素平均分配空间
align-content:space-around	//每个元素两侧的间隔相等。所以，元素之间的间隔比元素与容器的边距的间隔大一倍
align-content:space-evenly	//元素间距离平均分配
```
#### (2)弹性元素(单个)
1. align-self单个元素交叉轴排列
```js
align-self:stretch	// 将空间平均分配给元素
align-self:flex-start	// 元素紧靠主轴起点
align-self:flex-end	// 元素紧靠主轴终点
align-self:center	// 元素从弹性容器中心开始
```
2. flex-grow元素可用空间分配
```js
// 用于将弹性盒子的可用空间，分配给弹性元素。可以使用整数或小数声明。
  <style>
    section {
      display: flex;
      width: 500px;
      border: 2px solid red;
      margin: 300px auto;
    }

    div {
      flex-grow: 1;
      width: 100px;
      height: 100px;
      background-color: red;
      margin: 0 10px;
    }
  </style>

<body>
  <section>
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </section>
</body>


```
3. flex-shrink元素挤压比例(防止图片变形)
```js
// flex-shrink: 0; 不会缩小
<style>
    section {
      display: flex;
      width: 500px;
      border: 2px solid red;
      margin: 300px auto;
    }

    div {
      flex-grow: 1;
      width: 300px;
      height: 100px;
      background-color: red;
      margin: 0 10px;
    }

    div:nth-child(1) {
      flex-shrink: 0;
    }
  </style>

<body>
  <section>
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </section>
</body>
```
4. flex-basis元素的基本尺寸
```js
// 可以是长度单位，也可以是百分比。
// lex-basis 优先级大于 width、height。
  <style>
    section {
      display: flex;
      width: 500px;
      border: 2px solid red;
      margin: 300px auto;
    }

    div {
      flex-basis: 50px;
      height: 100px;
      background-color: red;
      margin: 0 10px;
    }

    div:nth-child(1) {
      flex-shrink: 0;
    }
  </style>


<body>
  <section>
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </section>
</body>
```
5. flex组合属性
```js
flex: 1 0 100px; 
/**
 * flex-grow 空间分配
 * flex-shrink 缩放
 * flex-basis 基本尺寸
 */
```
6. order控制弹性元素的位置
```js
// 数值大就靠后
 <style>
    section {
      display: flex;
      width: 500px;
      border: 2px solid red;
      margin: 300px auto;
    }

    div {
      flex: 1 0 100px;
      /* height: 100px; */
      background-color: red;
      margin: 0 10px;
    }

    div:nth-child(1) {
      order: 10;
    }
  </style>

<body>
  <section>
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </section>
</body>
```
7. 定位对flex布局的影响
```js
// 绝对定位会影响flex布局，因为其丢失了原来的位置
// 相对定位不会影响flex布局，因为其原来的位置不会丢失
```
#### (3)flex布局案例
1. flex布局案例
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    body {
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    main {
      flex: 1;
      background-color: #ccc;
    }

    footer {
      height: 50px;
      background-color: red;
      display: flex;
      justify-content: space-between;
    }

    section {
      flex: 1;
      background-color: pink;
      border: 1px solid black;
      display: flex;
      flex-direction: column-reverse;
      align-items: center;
      /* justify-content: center; */
    }

    h4 {
      flex: 0 0 50px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    ul {
      width: 100%;
      display: flex;
      flex-direction: column;
      border: 1px solid red;
      text-align: center;

    }

    li {
      display: flex;
      flex-direction: column;
      justify-content: center;
      flex: 1 0 40px;
      border-bottom: 1px solid black;
      cursor: pointer;
    }

    li:last-child {
      border-bottom: none;
    }
  </style>
</head>

<body>
  <main></main>
  <footer>
    <section>
      <h4>教程</h4>
      <ul>
        <li>css</li>
        <li>php</li>
      </ul>
    </section>
    <section>
      <h4>直播</h4>
    </section>
    <section>
      <h4>软件</h4>
    </section>
  </footer>
</body>
```
2. flex布局自动撑满
```js
 <style>
    * {
      padding: 0;
      margin: 0;
    }

    nav {
      margin: 0 auto;
      width: 1200px;
      height: 60px;
      background-color: #f3f3f3;
      box-shadow: 0 0 0 rgba(0, 0, 0, .3);
      display: flex;
    }

    ul {
      display: flex;
      align-items: center;
    }

    ul:first-child {
      /* 自动撑满把第二个到右边 */
      margin-right: auto;
    }

    ul:first-child li {
      margin: 0 10px;
    }

    ul:last-child li {
      width: 50px;
      height: 50px;
      background-color: red;
      border-radius: 50%;

    }
  </style>


<body>
  <nav>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
    <ul>
      <li></li>
    </ul>
  </nav>

</body>
```
### 9.栅格布局
#### (1)栅格划分
1. 简单的使用
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      display: grid;
      width: 300px;
      height: 300px;
      margin: 110px auto;
      border: 1px solid red;
      /* 画行画列 */
      grid-template-rows: 100px 100px 100px;
      grid-template-columns: 100px 100px 100px;
    }

    div {
      width: 100px;
      height: 100px;
      background-color: pink;
      border: 1px solid;
      padding: 10px;
      background-clip: content-box;
      box-sizing: border-box;
    }
  </style>

<body>
  <article>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>7</div>
    <div>8</div>
    <div>9</div>
  </article>
</body>
```
2. 绘制行列
```js
/**固定宽度 */
  grid-template-rows: 100px 100px;
  grid-template-columns: 100px 100px 100px;
/**百分比 */
  grid-template-rows: 50% 50%;
  grid-template-columns: 25% 25% 25% 25%;
/**重复绘制 */
  grid-template-rows: repeat(2, 50%);
  grid-template-columns: repeat(2, 50%);
/**自动填充 */
  grid-template-rows: repeat(auto-fill, 100px);
  grid-template-columns: repeat(auto-fill, 100px);
/**比例划分 */
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: repeat(3, 1fr);
/**定义波动范围 */
  grid-template-rows: repeat(3, minmax(50px, 100px));
  grid-template-columns: repeat(3, 1fr);
/**自动分配 */
  grid-template-rows: repeat(3, auto);
  grid-template-columns: repeat(3, auto);
```
3. 栅格间距
```js
    <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      display: grid;
      width: 300px;
      height: 300px;
      margin: 110px auto;
      border: 1px solid red;
      grid-template-rows: repeat(3, auto);
      grid-template-columns: repeat(3, auto);
      /* 设置间距 */
      row-gap: 10px;
      column-gap: 10px;
      /*简写 */
       gap: 10px;
    }

    div {
      background-color: pink;
      border: 1px solid;
      box-sizing: border-box;
    }
  </style>

<body>
  <article>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>7</div>
    <div>8</div>
    <div>9</div>
  </article>
</body>            
```
#### (2)栅格定位
1. 根据栅格线定位
```js
<style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      display: grid;
      width: 300px;
      height: 300px;
      margin: 110px auto;
      border: 1px solid red;
      grid-template-rows: repeat(3, 100px);
      grid-template-columns: repeat(3, 100px);
    }

    div {
      background-color: pink;
      border: 1px solid;
      box-sizing: border-box;
      /* 定到中间的位置 */
      grid-row-start: 2;
      grid-row-end: 3;
      grid-column-start: 2;
      grid-column-end: 3;
    }
  </style>

<body>
  <article>
    <div>1</div>
  </article>
</body>
```
2. 使用栅格线不规则布局
```js

  <style>
    section {
      width: 400px;
      height: 400px;
      border: 1px solid red;
      margin: 100px auto;
      display: grid;
      grid-template-columns: repeat(2, auto);
      grid-template-rows: repeat(2, auto);
      gap: 0 10px;
    }

    div {
      padding: 10px;
      background-clip: content-box;
      background-color: pink;
    }

    div:first-child {
      grid-row-start: 1;
      grid-row-end: 3;
      grid-column-start: 1;
      grid-column-end: 2;
    }
  </style>

<body>
  <section>
    <div></div>
    <div></div>
    <div></div>
  </section>
</body>
```
3. 使用栅格命名定位
```js
<style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      display: grid;
      width: 300px;
      height: 300px;
      margin: 110px auto;
      border: 1px solid red;
      grid-template-rows: repeat(3, [r] 100px [re]);
      grid-template-columns: repeat(3, [s] 100px [se]);
    }

    div {
      background-color: pink;
      border: 1px solid;
      box-sizing: border-box;
      /*根据命名定位 */
      grid-row-start: r 2;
      grid-row-end: re 2;
      grid-column-start: s 2;
      grid-column-end: se 2;

    }
  </style>


<body>
  <article>
    <div>1</div>
    <!-- <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>7</div>
    <div>8</div>
    <div>9</div> -->
  </article>
</body>

```
4. 根据偏移量定位
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      display: grid;
      width: 300px;
      height: 300px;
      margin: 110px auto;
      border: 1px solid red;
      grid-template-rows: repeat(3, 100px);
      grid-template-columns: repeat(3, 100px);
    }

    div {
      background-color: pink;
      border: 1px solid;
      box-sizing: border-box;
      /*根据span偏移量定位，中间 */
      grid-row-start: 1;
      grid-column-start: 1;
      grid-row-end: span 2;
      grid-column-end: span 2;
    }
  </style>

<body>
  <article>
    <div>1</div>
    <!-- <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>7</div>
    <div>8</div>
    <div>9</div> -->
  </article>
</body>

```
5. 组合属性
```js
grid-row: 2/4; // 开始-结束
grid-column: 2/4; 
// 行开始/列开始/行结束/列结束
grid-area: 2/2/4/4;
```
6. 模拟栅格布局
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    .container {
      width: 1020px;
      margin: 100px auto;
      border: 1px solid red;
    }

    .row {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 10px;
    }

    .col-1 {
      /* 占用一等份 */
      grid-column-end: span 1;
    }

    .col-2 {
      grid-column-end: span 2;
    }

    .col-3 {
      grid-column-end: span 3;
    }

    div {
      background-color: red;
      height: 50px;
      background-clip: content-box;
    }
  </style>

<body>
  <main class="container row">
    <div class="col-1">1</div>
    <div class="col-2">2</div>
    <div class="col-3">3</div>
  </main>
</body>
```
#### (3)栅格区域/流动
1. 使用栅格区域布局
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      width: 100vw;
      height: 100vh;
      background-color: red;
      display: grid;
      grid-template-rows: 60px 1fr 60px;
      grid-template-columns: 60px 1fr;
      grid-template-areas: "header header""nav main""footer footer";
    }

    header {
      grid-area: header;
      background-color: aqua;
    }

    nav {
      grid-area: nav;
      background-color: pink;
    }

    main {
      grid-area: main;
      background-color: #ccc;
    }
    footer{
      grid-area: footer;
      background-color: yellow;
    }
  </style>

<body>
  <article>
    <header></header>
    <nav></nav>
    <main></main>
    <footer></footer>
  </article>
</body>
```
2. 栅格区域布局占位
```js
 <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      width: 100vw;
      height: 100vh;
      background-color: red;
      display: grid;
      grid-template-rows: 60px 1fr 60px;
      grid-template-columns: 60px 1fr;
      grid-template-areas: '. .''. .''footer footer';
    }

    footer {
      grid-area: footer;
      background-color: yellow;
    }
  </style>


<body>
  <article>
    <div>logo</div>
    <div>头部</div>
    <div>导航</div>
    <div>主体</div>
    <footer />
  </article>
</body>

```
3. 栅格对齐
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      margin: 400px auto;
      border: 1px solid black;
      padding: 10px;
      width: 600px;
      height: 400px;
      display: grid;
      grid-template-columns: repeat(4, 60px);
      gap: 10px;
      /* 设置栅格居中 */
      justify-content: center;
      align-content: center;
    }

    div {
      height: 100px;
      background-color: red;
    }
  </style>


<body>
  <article>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </article>
</body>

```
4. 元素对齐(整体)
```js
  <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      margin: 400px auto;
      border: 1px solid black;
      padding: 10px;
      width: 400px;
      height: 400px;
      display: grid;
      grid-template-columns: repeat(4, 100px);
      justify-items: center;
      align-items: center
    }

    div {
      height: 100px;
      width: 30px;
      background-color: red;
    }
  </style>


<body>
  <article>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </article>
</body>
```
5. 元素对齐(个体)
```js
   <style>
    * {
      padding: 0;
      margin: 0;
    }

    article {
      margin: 400px auto;
      border: 1px solid black;
      padding: 10px;
      width: 400px;
      height: 400px;
      display: grid;
      grid-template-columns: repeat(4, 100px);
    }

    div {
      height: 100px;
      width: 30px;
      background-color: red;
    }

    div:first-child {
      justify-self: center;
      align-self: center;
    }
  </style>

<body>
  <article>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </article>
</body>

```
6. 整体对齐简写
```js
// 用于控制栅格的对齐方式，语法如下：
  place-content: //<align-content> <justify-content>
// 控制所有元素的对齐方式，语法结构如下：   
  place-items:// <align-items> <justify-items>
 // 控制单个元素的对齐方式
  place-self: //<align-self> <justify-self>
```
### 10.变形动画
#### (1)移动操作
1. 移动以及过度
```js
/* 定义多个会被覆盖 */
/* 向右移动是正数,向下移动是正数,向外移动是正数*/
transform: translateX(200px); 
transform: translateY(200px);
transform: translateZ(200px);
transform: translate(200px, 200px); // transform: translateX(200px)  translateY(200px) 
transform: translate3d(200px, 200px，200px) // transform: translateX(200px)  translateY(200px) translateZ(200px)
 /* 过度要放入产生动画的元素块 */
transition: 1s;
```
2. 移动过度案例
```js
  <style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    main {
      width: 400px;
      height: 400px;
      border: 1px solid red;
      margin: 100px auto;
      position: relative;
    }

    div {
      width: 200px;
      height: 200px;
      position: absolute;
    }

    div:nth-child(1) {
      background-color: green;
    }

    div:nth-child(2) {
      background-color: yellow;
      /* 过度要放入产生动画的元素块 */
      transition: 1s;
    }

    div:nth-child(2):hover {
      /* 向右移动是正数,向下移动是正数*/
      transform: translateX(200px);
      /* 会覆盖上面的操作 */
      transform: translateY(200px);
      /* 同时移动xy */
      transform: translate(200px, 200px);
    }
  </style>

<body>
  <main>
    <div></div>
    <div></div>
  </main>
</body>
```
3. 元素居中
```js
  <style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    main {
      width: 400px;
      height: 400px;
      border: 1px solid red;
      margin: 100px auto;
      position: relative;
    }

    div {
      width: 200px;
      height: 200px;
      position: absolute;
    }

    div:nth-child(1) {
      background-color: green;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
    }
  </style>

<body>
  <main>
    <div></div>
  </main>
</body>
```
4. Z轴移动和景深
```js
// 放在父级上，即拥有“第二者视角”
// 放在自身、兄弟身上，即以“自己的视角”
perspective: 900px;

transform: perspective(900px);// 自己设置景深
  <style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    main {
      position: relative;
      width: 400px;
      height: 400px;
      border: 1px solid red;
      margin: 100px auto;
      /* 设置景深 */
      perspective: 900px;
    }

    div {
      width: 200px;
      height: 200px;
      position: absolute;
      margin: 100px;
      transform: rotateY(60deg);
      transition: 1s;
    }

    div:nth-child(1) {
      background-color: green;

    }

    div:nth-child(2) {
      background-color: yellow;
    }

    div:nth-child(2):hover {
      transform: rotateY(60deg) translateZ(200px);
    }
  </style>
<body>
  <main>
    <div></div>
    <div></div>
  </main>
</body>

```
5. 炫酷表单的效果
```js
  <style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    main {

      width: 400px;
      height: 400px;
      border: 1px solid red;
      margin: 100px auto;
      background-color: #ccc;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    div {
      position: relative;
      margin-top: 10px;
      overflow: hidden;
    }

    div::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 2px;
      background: linear-gradient(to right, white, green, yellow, red, white);
      transform: translateX(-100%);
      transition: 2s;

    }

    div:hover::before {
      transform: translateX(100%);
    }

    div input {
      border: none;
      outline: none;
      padding: 10px;
    }
  </style>

<body>
  <main>
    <div>
      <input type="text" />
    </div>
    <div>
      <input type="text" />
    </div>
  </main>
</body>
```
6. 视图切换效果
```js
<style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    body {
      width: 100vw;
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    main {
      position: relative;
      flex-grow: 1;
    }

    nav {
      height: 10vh;
      background-color: red;
      display: flex;
      justify-content: space-evenly;
      align-items: center;
    }

    nav a {
      display: block;
      text-decoration: none;
      text-transform: uppercase;
      font-size: 1.5em;
      flex: 1;
      height: 10vh;
      line-height: 10vh;
      text-align: center;
      background-color: yellow;
    }

    main>div {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      transform: translateY(-100%);
      transition: 1s;
    }

    main>div:target {
      transform: translateY(0);
    }

    main>div:nth-of-type(1):target {
      background-color: yellowgreen;
    }

    main>div:nth-of-type(2):target {
      background-color: rebeccapurple;
    }

    main>div:nth-of-type(3):target {
      background-color: goldenrod;
    }
  </style>

<body>
  <main>
    <div id="home"></div>
    <div id="video"></div>
    <div id="live"></div>
  </main>
  <nav>
    <a href="#home">home</a>
    <a href="#video">video</a>
    <a href="#live">live</a>
  </nav>
</body>

```
7. 小说打开状态栏效果
```js
  <style>
    * {
      padding: 0;
      margin: 0;
      box-sizing: border-box;
    }

    main {
      display: flex;
      flex-direction: column;
      background-color: red;
      justify-content: space-between;
      height: 100vh;
    }

    header {
      height: 8vh;
      background-color: #aaa;
      transform: translateY(-100%);
      transition: 1s;
    }

    footer {
      height: 15vh;
      background-color: #aaa;
      transform: translateY(100%);
      transition: 1s;
    }

    main:active header,
    main:active footer {
      transform: translateY(0);
    }
  </style>

<body>

  <main>
    <header></header>
    <footer></footer>
  </main>

</body>
```
#### (2)缩放操作
1. 缩放操作
```js
transform: scaleX(.5); // 沿 X 轴缩放一半。
transform: scaleY(.5); // 下面是沿 Y 轴缩放一半。
transform: scale(.5,.5); //  scale可同时设置 X/Y 轴的缩放，如果只设置一个值时表示两轴缩放相同。
transform: scale3d(.5,.5,.5) //  X/Y/Z 三个轴绽放元素。
```
2. 元素拉远和3d效果(拉长Z轴,顶部盒子Z轴放大)
```js
 /* 设置3D transform-style: preserve-3d; */ 
   
<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  main {
    position: relative;
    width: 400px;
    height: 400px;
    border: 1px solid red;
    margin: 100px auto;
    /* 设置景深 */
    transform: perspective(900px) rotateY(45deg);
    /* 设置3D */
    transform-style: preserve-3d;
    transition: 1s;
  }

  div {
    width: 200px;
    height: 200px;
    position: absolute;
    margin: 100px;
    transition: 1s;
  }

  div:nth-child(1) {
    background-color: green;
  }

  div:nth-child(2) {
    background-color: yellow;
    transform: translateZ(-300px);
  }

  body:hover main {
    transform: perspective(900px) rotateY(45deg) scaleZ(3);
  }
</style>

<body>
  <main>
    <div></div>
    <div></div>
  </main>
</body>
```
3. 缩放菜单
```js
 /* 缩放基点   transform-origin: left top;*/
  
<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  main {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translateX(-50%) translateY(-50%);
  }

  ul {
    display: flex;
  }

  strong {
    padding: 10px;
    background-color: red;
    text-transform: uppercase;
    margin-right: 60px;
    cursor: pointer;
  }

  div {
    display: flex;
    flex-direction: column;
    background-color: yellowgreen;
    margin-right: 10px;
    margin-top: 10px;
    /* 缩放基点 */
    transform-origin: left top;
    transform: scale(0);
    transition: .6s;
  }

  li:hover div {
    transform: scale(1);
  }

  a {
    padding: 5px;
    text-align: center;
    border: 1px solid black;
  }
</style>

<body>
  <main>
    <ul>
      <li>
        <strong>VIDEO</strong>
        <div>
          <a href="">HTML</a>
          <a href="">JS</a>
          <a href="">CSS</a>
        </div>
      </li>
      <li>
        <strong>LIVE</strong>
        <div>
          <a href="">PHP</a>
          <a href="">NODEJS</a>
          <a href="">NESTJS</a>
        </div>
      </li>
    </ul>
  </main>
</body>

```
4. 图片放大效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  body {
    width: 100vw;
    height: 100vh;
    box-sizing: border-box;
    background-color: red;
    margin-top: 200px;
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  div {
    width: 200px;
    height: 200px;
    margin-right: 20px;
    overflow: hidden;
    /*  transition: .6s; */
  }

  img {
    width: 100%;
    transition: .6s;
  }

  img:hover {
    transform: scale(1.3);
  }

  /* main:hover div {
    filter: blur(10px);
    transform: scale(.6);
  }

  main:hover div:hover {
    transform: scale(1.6);
    filter: none;
  } */
</style>

<body>
  <main>
    <div><img src="./1.jpg" alt=""></div>
    <div><img src="./1.jpg" alt=""></div>
    <div><img src="./1.jpg" alt=""></div>
  </main>
</body>

```
#### (3)旋转操作 
1. 旋转操作
```js
/**设置可以看到3d */
transform-style: preserve-3d;
transform: rotateX(45deg); // 控制元素按照 X 轴进行旋转操作。
transform: rotateY(45deg); // 控制元素按照 Y 轴进行旋转操作。
transform: rotateZ(45deg); //  控制元素按照 Z 轴进行旋转操作。
transform: rotate(45deg); //  控制元素按照 X/Y轴进行旋转操作。
transform: rotate3d(45deg); //  X/Y/Z 三个轴进行旋转操作。
```
2. 旋转操作案例
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
     transform-style: preserve-3d;
    perspective: 900px;
    transform: perspective(900px) rotateY(45deg);
  }

  div {
    background-color: red;
    width: 200px;
    height: 200px;
    transition: .6s;

  }

  div:hover {
    transform: rotateX(40deg) rotateY(40deg) rotateZ(50deg);
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>

```
3. 时钟案例
```js
<style>
  * {
    padding: 0;
    margin: 0;
    background-color: #ccc;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 100px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
    border-radius: 50%;
    background-image: linear-gradient(90deg, yellow, red);
    position: relative;
  }

  main>div {
    width: 90%;
    height: 90%;
    background-color: #ccc;
    border-radius: 50%;

  }

  .line {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translateX(-50%) translateY(-50%);
    border-radius: 50%;
    width: 80%;
    height: 80%;
    /* background-color: black; */
  }

  .line>div {
    width: 10px;
    height: 100%;
    position: absolute;
    background-color: #fff;
    left: 50%;
  }

  .line>div:nth-child(1) {
    transform: translateX(-50%) rotate(0);
  }

  .line>div:nth-child(2) {
    transform: translateX(-50%) rotate(30deg);
  }

  .line>div:nth-child(3) {
    transform: translateX(-50%) rotate(60deg);
  }

  .line>div:nth-child(4) {
    transform: translateX(-50%) rotate(90deg);
  }

  .line>div:nth-child(5) {
    transform: translateX(-50%) rotate(120deg);
  }

  .line>div:nth-child(6) {
    transform: translateX(-50%) rotate(150deg);
  }

  .line::after {
    content: '';
    width: 80%;
    height: 80%;
    background-color: #ccc;
    position: absolute;
    left: 50%;
    top: 50%;
    border-radius: 50%;
    transform: translateX(-50%) translateY(-50%);
  }

  .line::before {
    content: '';
    width: 20px;
    height: 20px;
    background-color: red;
    position: absolute;
    left: 50%;
    top: 50%;
    border-radius: 50%;
    z-index: 1;
    transform: translateX(-50%) translateY(-50%);
  }

  .hour {
    width: 10px;
    height: 20%;
    position: absolute;
    bottom: 50%;
    background-color: #fff;
    left: 50%;
    transform: translateX(-50%);
  }

  .minute {
    width: 7px;
    height: 25%;
    position: absolute;
    bottom: 50%;
    background-color: #fff;
    left: 50%;
    transform-origin: bottom;
    transform: translateX(-50%) rotate(30deg);
  }

  .second {
    width: 5px;
    height: 30%;
    transform-origin: bottom;
    position: absolute;
    bottom: 50%;
    background-color: #fff;
    left: 50%;
    transform: translateX(-50%) rotate(60deg);
    transition: 10s;
  }

  main:hover .second {
    transform: translateX(-50%) rotate(360deg);
  }
</style>

<body>
  <main>
    <div>
      <div class="line">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
      </div>
      <div class="hour"></div>
      <div class="minute"></div>
      <div class="second"></div>
    </div>

  </main>
</body>

```
#### (4)倾斜操作
1. 旋转操作
```js
transform: skewX(45deg); // 控制元素按照 X 轴进行倾斜操作
transform: skewX(45deg); // 控制元素按照 Y 轴进行倾斜操作
transform: rotate(-45deg,45deg); //  控制元素按照 X/Y轴进行倾斜操作
```
2. 倾斜的案例
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
  }

  div {
    background-color: red;
    width: 200px;
    height: 200px;
    transition: .6s;

  }

  div:hover {
    transform: skew(-45deg, 45deg);
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>
```
3. 倾斜中参数
```js
// 两参数分开写是完全不同的效果
 transform: skew(-45deg, 45deg);
 transform: skewX(-45deg) skewY(45deg);
```
4. 帅气按键
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    /* perspective: 900px; */
    /* transform-style: preserve-3d; */
  }

  div {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 5px solid yellowgreen;
    width: 100px;
    padding: 10px;
    border-radius: 10px;
    position: relative;
    overflow: hidden;
  }

  div::after {
    position: absolute;
    content: '';
    width: 0;
    transform: skew(45deg);
    height: 100%;
    background-color: pink;
    z-index: -1;
    transition: all .8s;
  }

  div:hover::after {
    width: 200%;
  }
</style>

<body>
  <main>
    <div>success</div>
  </main>
</body>
```
5. 立体按键
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
  }

  div {
    width: 200px;
    height: 40px;
    background-color: pink;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    transform: skewX(25deg) rotate(-15deg);
  }

  div::before {
    content: '';
    width: 10px;
    height: 100%;
    background-color: black;
    position: absolute;
    left: -10px;
    transform: skewY(-45deg) translate(0, 5px);
  }

  div::after {
    content: '';
    width: 100%;
    height: 10px;
    background-color: black;
    position: absolute;
    bottom: -10px;
    transform: skewX(-45deg) translate(-5px, 0);
  }
</style>

<body>
  <main>
    <div>success</div>
  </main>
</body>
```
#### (5)变形基点
1. transform-origin设置旋转元素参考点
```js
 transform-origin: left top; // 关键字
 transform-origin: 400px 400px; // 单位
  transform-origin: 200% 200%; // 百分比
```
2. 旋转倾斜基点
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
  }

  div {
    width: 200px;
    height: 200px;
    background-color: red;
    transform-origin: left bottom;
    transition: .8s;
  }

  div:hover {
    transform: rotateZ(180deg);

     {/* transform: skewX(45deg); */}
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>

```
3. transform-origin设置Z轴参考点
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
  }

  div {
    width: 200px;
    height: 200px;
    background-color: red;
    transform-origin: center center 200px; 
    transition: .8s;
  }

  div:hover {
    transform: rotateY(235deg);
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>
```
4. 翻开效果的实现
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 400px;
    height: 400px;
    margin: 300px auto;
    border: 1px solid red;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 900px;
    transform-style: preserve-3d;
   
  }

  div {
    width: 300px;
    height: 200px;
    background-color: red;
    position: relative;
    transform-style: preserve-3d;
    transform: perspective(900px) rotateX(45deg);
  }

  div::before,
  div::after {

    background-color: yellowgreen;
    width: 50%;
    height: 100%;
    position: absolute;
    color: white;
    transition: 2s;
  }

  div::before {
    content: '新年';
    left: 0;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    transform-origin: left;
  }

  div::after {
    content: '快乐';
    right: 0;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    transform-origin: right;
  }

  div:hover::before {
    transform: rotateY(-180deg);
  }

  div:hover::after {
    transform: rotateY(180deg);
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>


```
5. 旋转菜单效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  body {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
  }

  nav {
    width: 200px;
    height: 200px;
    background-color: red;
    border-radius: 50%;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  ul {
    /* background-color: black; */
    /* position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%); */
    width: 300px;
    height: 300px;
    /* border: 1px solid black; */
    flex-shrink: 0;
    transform: scale(0);
    transition: 1s;
  }

  nav:hover ul {
    transform: scale(1);
  }

  li {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: red;
    position: absolute;
    transition: 1s;
    transform-origin: 150px 150px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  ul:hover li:nth-child(1) {
    transform: rotate(40deg);
  }

  ul:hover li:nth-child(2) {
    transform: rotate(80deg);
  }

  ul:hover li:nth-child(3) {
    transform: rotate(120deg);
  }

  ul:hover li:nth-child(4) {
    transform: rotate(160deg);
  }

  ul:hover li:nth-child(5) {
    transform: rotate(200deg);
  }

  ul:hover li:nth-child(6) {
    transform: rotate(240deg);
  }

  ul:hover li:nth-child(7) {
    transform: rotate(280deg);
  }

  ul:hover li:nth-child(8) {
    transform: rotate(320deg);
  }

  ul:hover li:nth-child(9) {
    transform: rotate(360deg);
  }
</style>

<body>
  <nav>
    <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </nav>

</body>

```
#### (6)透视和视角
1. 透视景深
```js
/**给父元素设置整体透视，观察子元素(无法观察本身) */
perspective: 900px;
/**给元素设置单独透视,只影响 */
transform: perspective(900px);
```
2. 透视舞台
```js
transform-style:flat //	2D 平面舞台
transform-style:preserve-3d //	3D 透视舞台
```
3. 3D旋转图集
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  article {
    width: 400px;
    height: 400px;
    border: 1px solid red;
    margin: 200px auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  main {
    position: relative;
    border: 1px solid red;
    width: 200px;
    height: 200px;

    transform: perspective(900px) rotateX(45deg);
    transform-style: preserve-3d;
    transform-origin: center center -200px;
    transition: 1s;
  }

  body:hover main {
    transform: perspective(900px) rotateY(555deg);
  }

  div {
    position: absolute;
    width: 200px;
    height: 200px;
    overflow: hidden;
    transform-origin: center center -200px;
    background-color: red;
  }

  img {
    width: 100%;
  }

  div:nth-child(1) {
    transform: rotateY(90deg);
  }

  div:nth-child(2) {
    transform: rotateY(180deg);
  }

  div:nth-child(3) {
    transform: rotateY(270deg);
  }

  div:nth-child(4) {
    transform: rotateY(360deg);
  }
</style>

<body>
  <article>
    <main>
      <div><img src="./1.jpg" alt=""></div>
      <div><img src="./1.jpg" alt=""></div>
      <div><img src="./1.jpg" alt=""></div>
      <div><img src="./1.jpg" alt=""></div>
    </main>
  </article>
</body>
```
4. 观看角度
```js
/**  perspective-origin: left bottom;切换观看加度 */
<style>
  main {
    width: 400px;
    height: 400px;
    border: 1px solid red;
    margin: 100px auto;
    perspective: 900px;
    transform-style: preserve-3d;
    transition: 1s;
  }

  div {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%) rotateY(60deg) translateZ(-300px);
    width: 200px;
    height: 200px;
    background-color: red;

  }

  body:hover main {
    perspective-origin: left bottom;
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>
```
5. 旋转的正方体
```js
<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    list-style: none;
  }

  body {
    background: #34495e;
  }

  main {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 200px;
    height: 200px;
    transform-style: preserve-3d;
    transform-origin: center center 50px;
    transform: translate(-50%, -50%) rotateY(0deg);
    transition: 2s;
  }

  main:hover {
    transform: translate(-50%, -50%) rotate3d(1, 1, 0, 180deg);
  }

  div {
    position: absolute;
    width: 200px;
    height: 200px;
    background: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 4em;
    transform-origin: center center 100px;
  }

  div:nth-child(1) {
    background: #1abc9c;
    transform: rotateY(90deg);
    opacity: .8;
  }

  div:nth-child(2) {
    background: #27ae60;
    transform: rotateY(180deg);
    opacity: .8;
  }

  div:nth-child(3) {
    background: #e67e22;
    transform: rotateY(270deg);
    opacity: .8;
  }

  div:nth-child(4) {
    background: #8e44ad;
    transform: rotateY(360deg);
    opacity: .8;
  }

  div:nth-child(5) {
    transform-origin: top;
    transform: rotateX(90deg);
    background: #ecf0f1;
    opacity: .8;
  }

  div:nth-child(6) {
    background: #ecf0f1;
    opacity: .5;
    transform-origin: bottom;
    transform: rotateX(-90deg);
  }
</style>

<main>
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
  <div>6</div>
</main>

```
6. 隐藏背面
```js
backface-visibility:visible	//背面可见
backface-visibility:hidden	// 背面隐藏

<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    list-style: none;
  }

  body {
    background: #34495e;
  }

  main {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 200px;
    height: 200px;
    transform-style: preserve-3d;
    transition: 2s;
  }

  main:hover {
    transform: rotateY(180deg);
  }

  div {
    position: absolute;
    width: 200px;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 4em;
    transform-origin: center center 100px;
  }

  div:nth-child(1) {
    background-color: red;
  }

  div:nth-child(2) {
    background-color: yellow;
    backface-visibility: hidden;
  }
</style>

<main>
  <div>1</div>
  <div>2</div>
</main>
```
7. 登录注册效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 100vw;
    height: 100vh;
    background-color: #000;
    transform: perspective(900px);
    transform-style: preserve-3d;
    transition: 2s;
  }

  main>div {
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 4em;
    text-transform: uppercase;
    color: white;
    backface-visibility: hidden;

  }

  main>:nth-child(1) {
    background-color: red;
  }

  main>:nth-child(2) {
    background-color: yellow;
    transform: rotateY(180deg);
  }

  nav {
    position: absolute;
    width: 100%;
    bottom: 90px;
    text-align: center;
  }

  a {
    padding: 10px 20px;
    background-color: #000;
    color: white;
  }

  main.login {
    transform: perspective(900px) rotateY(0);
  }

  main.register {
    transform: perspective(900px) rotateY(180deg);
  }

</style>

<main>
  <div>login</div>
  <div>register</div>
</main>
<nav>
  <a onclick="change('login')">login</a>
  <a onclick="change('register')">register</a>
</nav>
<script>
  const main = document.querySelector('main')
  function change(t) {
    switch (t) {
      case 'login':
        main.classList.remove('register')
        main.classList.add('login')
        break;
      case 'register':
        main.classList.remove('login')
        main.classList.add('register')
        break;
    }
  }
</script>
```
### 11.过渡延迟
#### (1)过渡基础
1. 控制过度的属性
```js
 transition-property: all; // 所有属性都有过度效果
 transition-property: background-color; // 背景颜色会有过度
 transition-property: none; // 禁用所以过渡改变
```
2. 监听过渡事件
```js
 <script>
    document.querySelector('main').addEventListener('transitionend', (e) => {
      console.log(e);
    })
  </script>
```
3. 过渡时间
```js
// 设置过渡时间2s
transition-duration:2s 
// 四个属性并设置了两个时间值,1,3 属性使用第一个值，2,4 属性使用第二个值。
transition-property: background-color, transform, opacity, border-radius;
transition-duration: 200ms, 5s;
// 四个属性并设置了三个时间值,1,2,3 属性使用 1,2,3 时间值
transition-property: background-color, transform, opacity, border-radius;
transition-duration: 200ms, 5s, 2s;
```
4. 过渡速度效果
```js
transition-timing-function: linear	// 规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
transition-timing-function: ease	// 开始慢，然后快，慢下来，结束时非常慢（cubic-bezier(0.25,0.1,0.25,1)）
transition-timing-function: ease-in	// 开始慢，结束快（等于 cubic-bezier(0.42,0,1,1)）
transition-timing-function: ease-out	// 开始快，结束慢（等于 cubic-bezier(0,0,0.58,1)）
transition-timing-function: ease-in-out	// 中间快，两边慢（等于 cubic-bezier(0.42,0,0.58,1)）
transition-timing-function: cubic-bezier(n,n,n,n)	// 在 cubic-bezier 函数中定义自己的值
```
5. 过渡步进效果
```js
transition-timing-function:steps(n,start)	//设置 n 个时间点，第一时间点变化状态
transition-timing-function:steps(n,end)	//设置 n 个时间点，第一时间点初始状态
transition-timing-function:step-start	//等于 steps(1,start)，可以理解为从当前步开始
transition-timing-function:step-end	//等于 steps(1,end)，可以理解为从下一步开始
```
6. 过渡延迟
```js
transition-delay: 1s;// 全部延迟一秒
// 可以设置不同属性的延迟时间
transition-property: background-color, transform, border-radius;
transition-delay: 1s, 3s, 5s;
```
7. 组合属性
```js
/**控制过渡属性 过渡速度效果 过渡时间 延迟时间 */
transition: border-radius linear 2s 0s,
            background 2s 2s,
            width linear 2s 4s,
            height linear 2s 4s;

```
#### (2)过渡案例
1. 时钟的步进效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
    background-color: black;
  }

  main {
    width: 200px;
    height: 200px;
    background-color: red;
    margin: 150px auto;
    border-radius: 50%;
    position: relative;
  }

  div {
    width: 5px;
    height: 40%;
    background-color: white;
    position: absolute;
    left: 50%;
    bottom: 50%;
    transform: translateX(-50%);
    transition-duration: 60s;
    transform-origin: bottom;
    transition-timing-function: steps(60, start);
  }

  main::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: yellow;
    z-index: 2;
  }

  main:hover div {
    transform: translateX(-50%) rotateZ(360deg);
  }
</style>

<body>
  <main>
    <div></div>
  </main>
</body>

```
2. 图片切换效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
    background-color: black;
  }

  main {
    width: 400px;
    height: 400px;
    border: 1px solid black;
    margin: 150px auto;
    overflow: hidden;
  }

  div {
    height: 400px;
    width: 400px;
    margin-right: 10px;
    overflow: hidden;
  }

  div:nth-child(2) {
    background-color: red;
    transition-duration: 2s;
    transition-timing-function: step-start;
  }

  main:hover div:nth-child(2) {
    transform: translateY(-400px);
  }
</style>

<body>
  <main>
    <div><img src="1.jpg" alt=""></div>
    <div></div>
  </main>
</body>
```
3. 点赞效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  main {
    width: 100px;
    height: 100px;
    border: 1px solid red;
    margin: 100px auto;
    position: relative;

  }

  i.fa {
    font-size: 100px;
    color: pink;
    position: absolute;
    transition-duration: 0.6s;
  }

  i.active {
    transform: scale(3);
    color: red;
    opacity: 0;
  }

  i.fa:nth-child(1) {
    transform: scale(1);
    opacity: 1;
    color: red;
  }
</style>

<body>
  <main>
    <i class="fa fa-heart" aria-hidden="true"></i>
    <i class="fa fa-heart" aria-hidden="true"></i>
  </main>
  <script>
    document.querySelectorAll('i')[1].addEventListener('click', (e) => {
      e.target.classList.toggle('active')
    })
  </script>
</body>
```
### 12.帧动画
#### (1)帧动画基本使用
1. 关键帧
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes identifier {

    /* 动画开始 */
    0% {
      background-color: pink;
    }

    50% {
      transform: scale(2);
    }

    /* 动画结束 */
    100% {
      background-color: red;
    }
  }

  main {
    width: 100px;
    height: 100px;
    border: 1px solid red;
    margin: 100px auto;
    position: relative;
    background-color: pink;
  }

  .animate {
    animation-name: identifier;
    animation-duration: 4s;
  }
</style>

<body>
  <main class="animate">
  </main>
</body>
```
2. 定义多个动画
```js
/** animation-name: identifier, identifier2; */
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes identifier2 {

    25%,
    75% {
      background: #9b59b6;
      border-radius: 50%;
    }

    50%,
    100% {
      background: #e67e22;
    }
  }

  @keyframes identifier {

    /* 动画开始 */
    0% {}

    25% {
      transform: translateX(400px);
    }

    50% {
      transform: translate(400px, 400px);
    }

    75% {
      transform: translate(0, 400px);
    }

    /* 动画结束 */
    100% {}

  }

  main {
    width: 100px;
    height: 100px;
    border: 1px solid red;
    margin: 100px auto;
    position: relative;
    background-color: pink;
  }

  .animate {
    animation-name: identifier, identifier2;
    animation-duration: 4s;
  }
</style>

<body>
  <main class="animate">
  </main>
</body>

```
3. 动画执行次数
```js
animation-iteration-count:infinite // 无限循环执行
// 执行多个动画次数
animation-name: identifier, background;
animation-duration: 4s;
animation-iteration-count: 1, 2;
```
4. 动画方向
```js
animation-direction:normal	// 从 0%到 100%运行动画
animation-direction:reverse	// 从 100%到 0%运行动画
animation-direction:alternate	// 先从 0%到 100%，然后从 100%到 0%
animation-direction:alternate-reverse	// 先从 100%到 0%，然后从 0%到 100%
```
5. 延迟动画/速率
```js
// 等待
animation-delay:1s 
//速率 
animation-timing-function:ease	// 开始慢，然后快，慢下来，结束时非常慢（cubic-bezier(0.25,0.1,0.25,1)）
animation-timing-function:linear	// 规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
animation-timing-function:ease-in	// 开始慢，结束快（等于 cubic-bezier(0.42,0,1,1)）
animation-timing-function:ease-out	// 开始快，结束慢（等于 cubic-bezier(0,0,0.58,1)）
animation-timing-function:ease-in-out	// 中间快，两边慢（等于 cubic-bezier(0.42,0,0.58,1)）
animation-timing-function:cubic-bezier(n,n,n,n)	// 在 cubic-bezier 函数中定义自己的值
```
6. 步进动画
```js
 animation-timing-function:steps(n,start)	// 设置 n 个时间点，第一时间点变化状态
 animation-timing-function:steps(n,end)	// 设置 n 个时间点，第一时间点初始状态
 animation-timing-function:step-start	// 等于 steps(1,start)，可以理解为从下一步开始
 animation-timing-function:step-end	// 等于 steps(1,end)，可以理解为从当前步开始
```
7. 动画播放状态
```js
animation-play-state:paused	//暂停
animation-play-state:running	//运行
#幻灯片
```
8. 动画填充模式(结束状态)
```js
animation-fill-mode:none	//需要等延迟结束，起始帧属性才应用
animation-fill-mode:backwards //	动画效果在起始帧，不等延迟结束
animation-fill-mode:forwards	// 结束后停留动画的最后一帧
animation-fill-mode:both	// 包含 backwards 与 forwards 规则，即动画效果在起始帧，不等延迟结束，并且在结束后停止在最后一帧
<style>
  main {
    width: 400px;
    height: 400px;
    border: 1px solid red;
    margin: 100px auto;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  div {
    width: 200px;
    height: 200px;
    background-color: pink;
    border-radius: 50%;
  }

  @keyframes identifier {
    0% {
      background-color: red;
    }

    100% {
      background-color: green;
    }
  }

  .animate {
    animation-name: identifier;
    animation-duration: 5s;
  }

  .backwards {
    animation-fill-mode: backwards;
  }

  .both {
    animation-fill-mode: both;
  }

  .forwards {
    animation-fill-mode: forwards;
  }

  .none {
    animation-fill-mode: none;
  }
</style>

<body>
  <main>
    <div class="animate backwards">backwards</div>
    <div class="animate both">both</div>
    <div class="animate forwards">forwards</div>
    <div class="animate none">none</div>
  </main>
</body>

```
9. 组合属性
```js
animation:
animation-name // 动画名
animation-duration // 动画运行时间
animation-timing-function // 动画速率
animation-delay // 动画延迟
animation-iteration-count // 动画重复次数
animation-direction // 动画方向
```
#### (2)帧动画案例
1. 移动小方块
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes identifier {

    /* 动画开始 */
    0% {}

    25% {
      transform: translateX(400px);
    }

    50% {
      transform: translate(400px, 400px);
    }

    75% {
      transform: translate(0, 400px);
    }

    /* 动画结束 */
    100% {}
  }

  main {
    width: 100px;
    height: 100px;
    border: 1px solid red;
    margin: 100px auto;
    position: relative;
    background-color: pink;
  }

  .animate {
    animation-name: identifier;
    animation-duration: 4s;
  }
</style>

<body>
  <main class="animate">
  </main>
</body>

```
2. 移动端开机动画
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes background {

    25% {
      background-color: pink;
    }

    75% {
      background: #9b59b6;
    }

    50% {
      background-color: yellow;
    }

    100% {
      background: #e67e22;
    }
  }

  @keyframes scale {

    /* 动画开始 */
    0% {}

    25% {
      transform: scale(.5);
    }

    50% {
      transform: scale(1) rotate(360deg);
    }

    75% {
      transform: scale(.5);
    }

    /* 动画结束 */
    100% {
      transform: scale(1);
    }

  }

  @keyframes radius {
    25% {
      border-radius: 50%;
    }

    50% {
      border-radius: 0%;
    }

    75% {
      border-radius: 50%;
    }
  }

  main {
    width: 100vw;
    height: 100vh;
    background-color: pink;
    transform: scale(0);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  @keyframes opacity {
    to {
      opacity: .8;
    }
  }

  main::after {
    content: 'Android';
    font-size: 2em;
    color: white;
    opacity: 0;
    animation-name: opacity;
    animation-duration: 2s;
    animation-delay: 2s;
    animation-fill-mode: forwards;
  }

  .animate {
    animation-name: background, scale, radius;
    animation-duration: 2s;
    /* 填充模式 */
    animation-fill-mode: forwards;
  }
</style>

<body>
  <main class="animate">
  </main>
</body>
```
3. 心动效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes scale {
    to {
      transform: scale(.3) rotateZ(45deg);
    }

    from {
      transform: scale(1) rotateZ(45deg);
      opacity: 0;
    }
  }


  main {
    width: 200px;
    height: 200px;
    margin: 100px auto;
    position: relative;
    background-color: red;
    transform: rotateZ(45deg);
  }

  main::before {
    content: '';
    position: absolute;
    width: 200px;
    height: 200px;
    background-color: red;
    border-radius: 50%;
    top: -100px;
  }

  main::after {
    content: '';
    position: absolute;
    width: 200px;
    height: 200px;
    background-color: red;
    border-radius: 50%;
    left: -100px;
  }

  .animate {
    animation-name: scale;
    animation-duration: .5s;
    animation-iteration-count: infinite;
  }
</style>

<body>
  <main class="animate">
  </main>
</body>
```
4. 球落地效果
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  @keyframes ball {
    to {
      transform: translateY(-300px)
    }
  }

  @keyframes shadow {
    from {
      background: #000;
      transform: translateX(-50%) scale(1);
      filter: blur(35px);
    }

    to {
      background: #aaa;
      filter: blur(10px);
    }
  }

  body {
    display: flex;
  }

  main {
    width: 100px;
    height: 100px;
    margin: 400px auto;
    background-color: red;
    border-radius: 50%;
  }

  section {
    width: 400px;
    height: 10px;
    position: absolute;
    top: 500px;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 50%;
    animation-name: shadow;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-direction: alternate;
  }


  .animate {
    animation-name: ball;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-direction: alternate-reverse;
  }
</style>

<body>
  <main class="animate"></main>
  <section></section>
</body>

```
5. 移动端微场景
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }



  body {
    width: 100vw;
    height: 100vh;
    display: grid;
    grid-template-rows: 10vh 1fr 10vh;
  }

  @keyframes header {
    from {
      transform: translateX(-100vw);
    }

    to {
      transform: translateX(0);
    }
  }

  @keyframes footer {
    from {
      transform: scale(0) rotate(360deg);
    }

    to {
      transform: scale(1) rotate(0deg);
    }
  }

  @keyframes main {
    from {
      opacity: 0;
    }

    to {
      opacity: .7;
    }
  }

  header {
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 2em;
    background-color: yellow;
    animation-name: header;
    animation-duration: .5s;
  }

  main {
    background-color: red;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    animation-fill-mode: backwards;
    animation-name: footer;
    animation-duration: .5s;
    animation-delay: 1s;
  }

  div {
    border-radius: 20px;
    width: 80vw;
    height: 30vh;
    opacity: .7;
  }

  div:nth-child(1) {
    background-color: darkorchid;
    animation-fill-mode: backwards;
    animation-name: main;
    animation-duration: .5s;
    animation-delay: 1.5s;
  }

  div:nth-child(2) {
    margin-top: 20px;
    width: 70vw;
    background-color: pink;
    animation-fill-mode: backwards;
    animation-name: main;
    animation-duration: .5s;
    animation-delay: 2.5s;
  }

  footer {
    background-color: green;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 2em;
    /* transform: scale(0);
    animation-fill-mode: forwards; */
    animation-fill-mode: backwards;
    animation-name: footer;
    animation-duration: .5s;
    animation-delay: .5s;
  }
</style>

<body>
  <header>header</header>
  <main>
    <div></div>
    <div></div>
  </main>
  <footer>footer</footer>
</body>
```
6. 动画速率展示
```js
<style>
  ul {
    width: 100vw;
    height: 100vh;
    background-color: red;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    align-content: end;
    gap: 2px;
  }

  li {
    background-color: pink;
    height: 500px;
    bottom: 0;
    animation-name: move;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-direction: alternate;
  }

  @keyframes move {
    to {
      transform: translateY(500px);
    }
  }

  li:nth-child(1) {
    animation-timing-function: ease;
  }

  li:nth-child(2) {
    animation-timing-function: ease-in;
  }

  li:nth-child(3) {
    animation-timing-function: ease-out;
  }

  li:nth-child(4) {
    animation-timing-function: ease-in-out;
  }

  li:nth-child(5) {
    animation-timing-function: linear;
  }
</style>

<body>
  <ul>
    <li>ease</li>
    <li>ease-in</li>
    <li>ease-out</li>
    <li>ease-in-out</li>
    <li>linear</li>
  </ul>
</body>
```
7. 小球反复弹跳效果
```js
<style>
  ul {
    width: 100vw;
    height: 100vh;
    background-color: red;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;

  }

  @keyframes ball {
    0% {
      transform: translateY(0);
      animation-timing-function: ease-in;
    }

    30% {
      transform: translateY(10vh);
      animation-timing-function: ease-in;
    }

    60% {
      transform: translateY(40vh);
      animation-timing-function: ease-in;
    }

    80% {
      transform: translateY(60vh);
      animation-timing-function: ease-in;
    }

    95% {
      transform: translateY(75vh);
      animation-timing-function: ease-in;
    }

    15%,
    45%,
    70%,
    85%,
    100% {
      transform: translateY(80vh);
      animation-timing-function: ease-out;
    }
  }

  li {
    grid-column: 2;
    background-color: pink;
    height: 100px;
    width: 100px;
    justify-self: center;
    border-radius: 50%;
    animation-name: ball;
    animation-duration: 2s;
    animation-fill-mode: forwards;
    animation-iteration-count: infinite;
  }
</style>

<body>
  <ul>
    <li></li>
  </ul>
</body>
```
8. 加载按钮
```js
<style>
  main {
    width: 300px;
    height: 300px;
    border: 1px solid red;
    margin: 100px auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  div {
    width: 150px;
    height: 50px;
    background-color: red;
    border-radius: 10px;
    box-shadow: 10px 10px 10px rgba(0, 0, 0, .4);
    transition: .6s;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.2em;
    color: white;
  }

  div:active {
    transform: scale(1.03);
  }

  @keyframes identifier {
    from {
      box-shadow: none;
    }

    30% {
      box-shadow: 3px 0 0 white;
    }

    60% {
      box-shadow: 3px 0 0 white, 9px 0 0 white;
    }

    90% {
      box-shadow: 3px 0 0 white, 9px 0 0 white, 15px 0 0 white;
    }
  }

  div::after {
    content: '';
    margin-left: 3px;
    width: 3px;
    height: 3px;
    display: inline-block;
    /* box-shadow: 3px 0 0 white, 9px 0 0 white, 15px 0 0 white; */
    animation-name: identifier;
    animation-duration: 1s;
    animation-iteration-count: infinite;
  }
</style>

<body>
  <main>
    <div>提交</div>
  </main>
</body>

```
9. CSS轮播图效果
```js
<style>
  main {
    width: 400px;
    height: 200px;
    border: 1px solid red;
    margin: 100px auto;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;
  }

  @keyframes identifier {
    to {
      transform: translateX(-1600px);
    }
  }

  section {
    overflow: hidden;
    display: flex;
    width: 1600px;
    height: 200px;
    position: absolute;
    left: 0;
    animation-name: identifier;
    animation-duration: 8s;
    animation-timing-function: steps(4, end);
    animation-iteration-count: infinite;

  }

  section:hover,
  section:hover+ul::before {
    animation-play-state: paused;
  }

  div {
    width: 400px;
    height: 200px;
  }

  ul {
    position: absolute;
    display: flex;
    left: 50%;
    bottom: 20px;
    transform: translateX(-50%);
  }

  li {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: white;
    margin: 0 5px;
  }

  @keyframes num {
    to {
      transform: translateX(80px);
    }
  }

  ul::before {
    content: '';
    width: 10px;
    height: 10px;
    position: absolute;
    border-radius: 50%;
    left: 5px;
    background-color: black;
    animation-name: num;
    animation-duration: 8s;
    animation-timing-function: steps(4, end);
    animation-iteration-count: infinite;
  }
</style>

<body>
  <main>
    <section>
      <div style="background-color: red;"></div>
      <div style="background-color: gold;"></div>
      <div style="background-color: darkmagenta;"></div>
      <div style="background-color: green;"></div>
    </section>
    <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </main>
</body>

```
### 13.响应式布局
#### (1)媒体设备
1. style定义媒体设备
```js
// all	所有媒体类型
// screen	用于电脑屏幕，平板电脑，智能手机等
// print	打印设备
// speech	应用于屏幕阅读器等发声设备
<!-- 屏幕设备 -->

<style media="screen">
  main {
    color: green;
  }
</style>
<!-- 打印设备 -->
<style media="print">
  main {
    color: red;
  }
</style>

<body>
  <main>
    不同设备
  </main>
</body>
```
2. link定义媒体设备
```js
  <link rel="stylesheet" href="" media="screen">
  <link rel="stylesheet" href="" media="print">
```
3. @import定义媒体设备
```js
@import url(screen.css) screen;
@import url(print.css) print;
```
4. @media定义媒体设备
```js
<style>
  @media screen {
    main {
      color: red;
    }
  }
  @media print {
    main {
      color: green;
    }
  }
</style>


<body>
  <main>
    不同设备
  </main>
</body>

```
#### (2)媒体查询
1. 基本使用
```js
<style>
  nav {
    height: 60px;
    width: 900px;
    display: flex;
    align-items: center;
    background-color: #f3f3f3;
    margin: 0 auto;
  }

  ul {
    display: flex;
  }

  li {
    margin: 0 20px;
  }

  @media screen and (max-width:600px) {
    ul {
      display: none;
    }
  }
</style>


<body>
  <nav>
    <a>淘宝</a>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  </nav>
</body>

```
2. 设备方向
```js
orientation:portrait	// 竖屏设备即高度大于宽度
orientation:landscape	// 横屏设备即宽度大于高度
```
3. 查询条件
```js
  @media screen and (orientation: landscape) {}// 逻辑and
  @media screen,(orientation:landscape) {}// 逻辑或 ,
  @media not screen {}// 逻辑非not
  @media only screen{} // 排除不支持媒体查询的浏览器
```
4. 媒体查询的顺序
```js
<style>
  @media only screen and (max-width:768px) {
    body {
      background-color: green;
    }
  }

  @media only screen and (min-width:768px) {
    body {
      background-color: blue;
    }
  }

  /* 媒体查询小尺寸在上面 */
  @media only screen and (min-width:960px) {
    body {
      background-color: gold;
    }
  }

  @media only screen and (min-width:1200px) {
    body {
      background-color: red;
    }
  }
</style>
```
5. 媒体查询完成菜单的显示展开
```js
<style>
  * {
    padding: 0;
    margin: 0;
  }

  :root {
    font-size: 15px;
  }

  .container {
    width: 1180px;
    margin: 0 auto;
  }

  header {
    border-bottom: 5px solid #16a085;
    box-shadow: 0 5px 5px rgba(0, 0, 0, .2);
  }

  nav {
    display: flex;
    align-items: center;
    padding: 1rem 0;
  }

  ul {
    display: flex;
    align-items: center;
  }

  .logo {
    color: #16a085;
    font-weight: 700;
    margin-right: 20px;
    font-size: 1.3rem;
    cursor: pointer;
  }

  .link {
    margin-right: auto;
  }

  ul li {
    color: #777;
    margin: 0 10px;
  }

  ul li:hover {
    font-weight: 700;
    cursor: pointer;
  }

  .btn a {
    color: #16a085;
    border: 1px solid #16a085;
    border-radius: .3rem;
    padding: .3rem 1rem;
    cursor: pointer;
  }

  .btn a:nth-child(2) {
    background-color: #16a085;
    color: white;
  }

  .label {
    display: none;
  }

  @media only screen and (max-width:960px) {
    .container {
      width: 750px;
      margin: 0 auto;
    }

    .link,
    .btn {
      display: none;
    }

    .logo {
      margin-right: auto;
    }

    .label {
      display: block;
      border: 1px solid #16a085;
      border-radius: .3rem;
      padding: .3rem 1rem;
      font-size: .3rem;
      cursor: pointer;
      background-color: #16a085;
      color: white;
    }

    .link {
      width: 100%;

    }

    ul {
      flex-direction: column;
      align-items: start;
    }

    ul li {
      margin: .5rem 0;
    }

    .btn {
      margin: .5rem 0;
    }

    nav {
      flex-wrap: wrap;
    }

    #toggle:checked+.link,
    #toggle:checked~.btn {
      display: block;
    }
  }
</style>


<body>


  <header>
    <nav class="container">
      <div class="logo">
        java666
      </div>
      <label class="label" onclick="open" for="toggle">
        展开
      </label>
      <input type="checkbox" id="toggle" style="display: none;">
      <div class="link">
        <ul>
          <li>新手启航</li>
          <li>实战项目</li>
          <li>碎片课程</li>
          <li>最新更新</li>
        </ul>
      </div>
      <div class="btn">
        <a>登录</a>
        <a>注册</a>
      </div>
    </nav>
  </header>

</body>
```

