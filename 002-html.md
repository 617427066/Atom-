# HTML

##  什么是HTML
超文本标记语言
Hyper Text markup language
## 干什么
* 承载内容（页面展示内容）

* 浏览器有三大板块：
  * 解析html+css  ：webkit
  * js  v8引擎

## 标签（元素）
标签名、属性、内容
### 标签类型
* 双标签： 又开始标签和结束标签
* 单标签：只有开始标签 没有结束标签

编辑时样式和最终浏览器显示的样式无关系。

### 快捷键
* 创建标签：标签名字tag name+tab
* 复制光标所在：Ctrl+d
* 父子：parent>son
* 若干相同元素：tag name*个数
* 注释  Ctrl+/
* 找回删除代码或返回刚才 Ctrl+z

### 注释标签
`<!--注释内容-->`

### 分类
* 从表现形式上分为：
  * 行元素：span,b,strong,em,i,s,del,
  * 块元素：div,h,ul,li,table,ol,li, p
  * 行内块标签：img,
* 所有修饰文字的标签全部都是行元素，剩下的是块元素。


* 区别：
   * 行内元素：都在一行显示，宽高就是它内容的宽高，不能设置宽高。
   * 块元素：独占一行，宽度就是父元素宽度，高度就是元素的高度，可以设置宽高。
   * 行内块元素：不会独占一行，又能设置宽高
####  标签分类
| 分类 | 特性 | 代表元素 |
|----|----|----|
| 块标签 | 有宽高属性，同时块标签会独占一行 |h1~h6 p li div|
| 行标签|不具有宽高特性，mrgin属性的值，只有左右没有上下。也不会占一行|字体标签、span|
| 行内块标签|既有行元素的属性即：不会独占一行又有块元素的属性即：可以设置宽高|img、表单元素|


### 字体效果标签
* h标签 标题标签   h1 一级标题  h2  h3....h6
* b标签 和strong（strong可以调整粗细） 标签：加粗
* em 标签(加强) ：斜体
  i 标签:  斜体
  去除斜体 `font-style:normal;`
* s 和 del  标签：删除线
  <s>删除线</s>
* br 标签  换行`<br>`
* u 双标签 ：下划线标签。
#### 区段标签
* hr ：水平线标签（单标签）
<br>`<hr 属性名="   " />`  粗细  size   颜色  color
* p ：文章段落标签（双）
  * pre: 文字段落标签 ，可以保留文本与编辑时的格式

### 属性
* width 宽
* height 高<br>
min-height  最小高度
* 注意： HTML里面只有img 和table 标签可以直接设置宽高，其余必须用css 来设置。
* color  颜色
* size  粗细
* bcakground  背景设置
  * backgrond-color 背景颜色
* border  边框   border-top  上边框
* float 浮动  `float：left`默认为向下排，float可以改变方向
* 文字水平：text-align
* 单行垂直：line-heigh：数值;
* 字体风格：font-style
| 值| 效果|
|---|---|
|normal |	默认值。浏览器显示一个标准的字体样式。|
|italic |	浏览器会显示一个斜体的字体样式。|
|oblique |浏览器会显示一个倾斜的字体样式。|
|inherit	| 规定应该从父元素继承字体样式。|


### 图片
* img(单)
  `<img src="路径" alt="加载失败">`
  1. alt：图片加载失败时显示内容
  2. src： 图片地址
  3. 绝对路径：从根目录或者盘符开始，按照目录结构 一层一层往下写位置 ，或<br>
  者互联网上的一个独立的地址，任意地方都可引用。
  4. 相对路径: 当前的HTML文件，路径依赖于他们之间的相对位置。如果在一个文件夹下同一级   ./图片名字
  5. 路径不要有空格
  6. 上一级目录  ../文件夹或图片
  7. title：当光标移入时的提示
  8. overflow  隐藏图片部分`overflow:hidden`


### div(区块)  万能标签  
1. 写在中间(行内样式)：`<div style="width:300px;   :   ;"></div>`
2. 写在title下面（嵌入样式）<br>
`<style>
div{
    width:000px;
    width:000px;
    width:000px;
}
</style>`
3. 外部样式表：新建css文件<br>
例：`div{
    格式
}`
4. 在原文件内引用(不能写在`<style>`里面,写在title下面)<br>
`<link rel="   " href=" .css">`<br>
5. 修饰哪个标签，就得有哪个，css文件就得用哪个



### 列表标签
+ `<ul><li>小标题</li></ul>`

  无序的 ： 无数字，只有点

+ `<ol><li>   <li></ol>`

  有序的：有123....数字

  * 无序列表type属性：
    1. disc 默认值，实心圆
    2. circle 空心圆
    3. square 实心方块

  * 有序列表type属性:
    1. 数字顺序的有序列表 （默认值） type="1"
    2. 字母顺序的  小写 type="a"  大写 type="A"  


### 自定义列表
* dl  `<dl>`有序列表
* dt   自定义列表条目
* dd 自定义列表的定义



### 超链接标签
* a  标签
  `<a href="http://www.baidu.com">百度</a>`
*  traget
  `_blank 在新的窗口打开（默认）  
  _self     在当前窗口打开`
  `<a href="网址" traget="_self" title="图片">网站名</a>`
* title 光标悬停显示

* 把a标签转换为块标签  display : block;它会独占一行
* 加入float 属性 自动转换为行内块标签
* 取消下划线 ：`text-decoration: none;`

* download 下载
  `<a href="下载地址" download="下载名" >下载</a>`
* 锚链接 (业内跳转)
`<a href="#name"></a>
<a name=""></a>`
* 图片跳转
  `<a href="http://www.baidu.com">
   <img scr="图片地址" alt=" ">
   </a>`

### 实体
* html 中只识别一个空格，不会识别换行，换行加<br>,
  多空格可以用 &nbsp

| 代码 |效果  |代码 |效果  |
|---|---|---|---|
|&quot|`"`|&lt|`<`|
|&gt|`>`|&nbsp|`空格`|
|&sect| § |&amp|`&`|
|&copy|`©`|&curren|`¤`|

### 表格  table
* tr  行
* td  列
* th  表头

| 代码 | 属性 | 属性值  |  描述   |
| :---: | :-----: |---------------- | :----------: |
| table |  width  | 数字      |  表格宽度  |
| table |  height | 数字      |  表格高度  |
| table |  border | 数字      |  表格边框  |
| table | bgcolor | 颜色      |  背景颜色  |
| table | cellspacing  | 数字 |  单元格之间的距离  |
| table | cellpadding  | 数字 |  单元格的内边距  |
| table | align   | left（默认）center right | 表格水平对齐方式 |
|  tr   |  height   bgcolor |               |                 |
|  tr   |  align、valign  | left center right   top  middle botto | 文本水平对齐方式、文本垂直对齐方式 |
|  td   | colspan | 数字   |     横跨的列数（合并列）        |
|  td   | rowspan | 数字   |     横跨的行数（合并行）        |

<table width="300"></table>

## markdown 表格样式
| 效果 |代码|效果 |代码  |  
|---|---|---|---|
| | | | |
* 引用图片
`！[图片名](图片链接路径)`
* 链接
`[名字](链接地址)`

## 盒模型（外边距 边框 内填充 内容）
* padding 内填充  00px  让内容与边框有一定的边界<br>
  `padding:10px`相当于四个方向是同一个值<br>
  `padding:10px 20px`上下 左右<br>
  `padding:10px 20px 30px`上 左右 下<br>
  `padding:1opx 20px 30px 40px`上 右 下 左<br>
  `padding-lift`左填充<br>
  顺时针对称原则（不可设置负值）
* margin 外边距
  顺时针对称原则<br>
  marfin-bottom 下边距  top 上<br>
  注：上下边距不会叠加，只会取最大值，可设置负值
* border  边框
  border：00px（宽度） （样式） （颜色）；<br>
  border-radius  边框圆润程度<br>
  可以单独设置左右上下边框的属性<br>
* box-sizing:border-box 设置内填充的范围。

* 边框样式：<br>
1、none 无样式
2、dotted 点线
3、dashed 虚线<br>
4、solid  实线
5、double 双线
6、groove 槽线<br>
7、ridge 脊线
8、inset 内凹
9、outset  外凸



* display(转换标签)

| 值 | 特性  |
|---|---|
| display:none;|可以让元素隐藏起来并且不占页面空间，浏览器会完全忽略掉这个元素，该元素将不会被显示，也不会占据文档中的位置|
| display：block;| 可以让元素具有块特性将块级元素|
| display:inline;| 可以让块级元素变为行内元素|
| display:inline-block;| 指定元素兼有块级和行级元素的特性，即在行内显示但是可以设定宽高|
* 浮动标签<br>
（为了让块元素在一行无间隙的排列）<br>
float 浮动  `float：left`默认为向下排，float可以改变方向
所有的标签都是可以浮动的，一般是div标签，浮动起来类似行内块
* 文档流
* 清除浮动
  * 设置一个空的div
clear  取值有left、 right、both、none（默认值）<br>
`<div style="clear:both;">`<br>
* 给父元素加一个overflow：hidden


## 补充属性

### overflow
| 属性值| 描述 |
|---|----|
|hidden|将超出的内容隐藏|
|visible|显示全部内容|
|auto|根据实际情况调整 自适应|
|scroll|始终出现滚动条|
* 单行文本超出省略号<br>
  `white-space:nowrap;
   overflow:hidden;
   text-overflow:ellipsis;`
* 多行超出省略号<br>
`display:-webkit-box;
-webkit-line-camp:3;
font-size:14px;
overflow:hidden;
text-overflow:ellipsis;`
### visibility
主要控制元素的隐藏和显示状态

| 属性值| 描述|
|---|---|
|visible|当前元素为显示状态|
|hidden|当前元素为隐藏状态|

| 属性| 描述|
|---|---|
|overflow|只是对超出容器的内容进行处理|
|display|整个元素的显示状态是不可见的，浏览器会认为这个元素不存在|
|visibility|浏览器认为该元素存在，但是不显示出来，所有该隐藏的元素还会占据原来的位置|

### resize(改变尺寸)
主要处理textarea的缩放
| 属性值| 描述|
|---|---|
|none|不能拖动|
|both|任意拖动|
|horizontal|水平拖动|
|vertical|垂直拖动|


## 字体图标
 * `@font-face`
Unicode模式；在原html文本中加一个link链接那个 .css文件


## 表单form
* 是Web浏览器和Web服务器进行通信的最常用的手段，即通过表单，浏览器不仅能从Web服务器中获得信息，而且还能向Web服务器反馈信息。HTML为此提供了表单(Form)元素来设计和实现这种交互界面。
* <form method='get' action='uek.php'>……</form>（块标签）

|属性|描述|值|
|---|---|---|
|action|数据处理文件|.php .asp .jsp|
|method|数据提交方式|get、post|

### 表单元素input（控件）
* 表单形成的交互界面上有许多元素，负责收集用户输入的各种信息，这些元素一般称为控件。如：单行/多行文本、单元按钮、多选按钮、文本域、下拉菜单、按钮、重置按钮、提交按钮。
* <input type='text' name='user' value='uek' size='10' maxlength='20'>

|属性|描述|
|---|---|
|type|控件类型|
|name|用于数据库获取信息|
|value|指定默认值|
|size|显示文本框长度|
|maxlength|用户可以出入的最多大字符数|
|disabled|用来设置或获取控件是否可用|
|readOnly|用来设置空间的只读属性，只能复制和读取|

* 控件类型
|控件类型| 值|
|---|---|
|单行文本|text|
|密码|password|
|单选按钮|radio|
|复选按钮|checkbox|
|文件域|file|
|按钮|button|
|重置按钮|reset|
|提交按钮|submit|

### 下拉框 select
* >HTML是通过`<select>`和`<option>`标记来定义输入列表框的。列表框标记`<select>`是成对出现标记，首标记`<select>`和尾标记</select>之间的内容就是一个列表框的内容。`<option>`标记用于定义列表框中的各个选项
* `<select name="uek" size="1" multiple>
  　　<option value="webui" selected="selected">前端工程师</>
  　　<option value="ui" selected="selected">ui设计师</>
  　　<option value="php" selected="selected">php工程师</>
  </select>`

  |属性|描述|值|
  |---|---|---|
  |name|指定列表框的文本（必选）|自定义|
  |size|用于定义列表框的长度（可选）|Number|
  |multiple|属性表示可以多选，按Ctrl可以多选。默认单选|ture|

* 下拉选项 option<br>
用于定义列表框中的选项。它必须嵌套在列表框标记中使用，一个列表框中有几个选项，就要有几个标记与之相对应。<option>标记有2个属性：value和selected，它们都是可选的.

|属性|描述|
|---|---|
|value|属性的参数值是当该项被选中并提交后，web浏览器传送给服务器的数据。缺少时，浏览器将传送选项的内容|
|selected|属性用来指定选项的初始状态，表示该选项在初始时是被选中的|

### 文本域
文本域用来定义多行文本

|属性|描述|
|---|----|
|name|用于指定文本输入框的名字|
|cols|cols属性用于规定文本输入框的宽度。属性的参数值是数字，表示一行所能显示的最大字符数|
|rows|用于规定文本输入框的高度。属性的参数值是数字，表示该文本输入框所占的行数|

### 自动聚焦lable
* 用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上
*  `<input type='radio' name='sex' value='nan' id='sex'>
  <label for='idname'> </label>
  <label>
    <input type='radio' name='sex' value='nan' id='sex'>
  </label>`

### fieldset
* 标签将表单内容的一部分打包，生成一组相关表单的字段。
* <fieldset>
    <legend>fieldset名称</legend>
    <!-- 加入你的内容 -->
   </fieldset>
* fieldset 元素可将表单内的相关元素分组。 <legend> 标签为 fieldset 元素定义标题。
