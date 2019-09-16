## JS
* JavaSpcript：基于对象，基于事件驱动的，弱类型的解释性语言。
* JS的任务就是对浏览器里面的内容进行操作

###html中引入js的方式
* 嵌入式 <script></script>
* 外部js文件  <script src="test.js"></script>
* 行内样式 放在事件后面
### 数据类型
* 基础类型
  * 数值类型 ：number
    var num= 100;
  * 字符串类型 string
   var num= "a"
  * 布尔类型 boolean
  * undefind ：没有值，类型就是undefind
* 引用类型（=对象）
  * 数组
  var num=[];
  * 函数
  var num function();
  * 自定义的对象
  * null
  * json
  var json =[{name:"张三","age":16,}]
### 基本函数
* var：定义变量
* typeof(num) 判断num的类型
* console.log() 打印输出
* alert() 弹出对话框
* prompt("请输入数字") 输入内容
* document.write("");通入程序向HTML里面写内容
* arguments[] 获取实参
* 注意：任何类型和字符串组合起来都是字符串
* arr.sort();排序（有问题）
* 加一个回调函数可解决
arr.sort(function (a,b)){
  return a-b //升序  b-a降序     
}
console.log(arr);
####流程控制
* 顺序执行
* 条件执行
* 循环执行

###语法
* for(var i=0;i<10;i++){}
* if(){}else{}


#### 全局变量，局部变量
* 提高程序运行效率
* 防止变量污染
* 全局变量:放在函数最外层的变量拥有全局的作用域，
* 局部变量：放在函数里面的变量，拥有函数内部的作用域。

###函数
* 函数定义的方法
  * 关键字定义法
  * 直接量
  * 对象的方式
  var c =new function()
  * 自定义的方式（匿名的方式）
  (function(){})
* 函数调用的方式
  * 通过函数名() 调用
  * 自调用的方式
  * 事件调用函数
* 参数
  * 可以接收任何的数据类型
  * 实参和形参是一一对应的
  * 如果说实参少于形参，多出的形参值是undefind
  * 如果实参多于形参，多出的实参用 arguments 来获取。
* 返回值(return)
  * 终止函数的运行
  * 给函数一个返回值

* function a(形参){

}
#### 函数的用法
* 将某一规则集合起来，可以重复利用
* 有类的功能，叫构造函数



### 对象
* js 基于对象
* 引用简写
* 基础类型
* 字符串对象，布尔对象，数值对象
* 引用类型（复杂类型）
* 函数对象，数组对象，自定义的对象
### 数组
* 可以传入任何类型的数据
* var arr=[1,2,3,"abc",true]
* for()循环遍历
* 下标从0开始
* 数组的方法（30多种）
### json格式
* 属性："值"
* "属性"："值"
##排序
* 冒泡排序
`function f1(arr) {
          for(var i =0;i<arr.length-1;i++){
              for(var j =0;j<arr.length-1-i;j++){
                  if(arr[j]>arr[j+1]){
                      var temp= arr[j];
                      arr[j]=arr[j+1];
                      arr[j+1] = temp;
                  }
              }
          }
          document.write(arr);
      }`
* 选择排序  
 `function f2(arr) {
    for (var i = 0; i < arr.length - 1; i++) {
            var index = i;
            for (var j = i + 1; j < arr.length; j++) {
                if (arr[j] < arr[index]) {
                    index = j;
                }
            }
        var tmp = arr[i];
        arr[i] = arr[index];
        arr[index] = tmp;
    }
    document.write(arr);
}`

* 快速排序
`function quick(arr,start,end) {
      var left=start,right=end,temp=arr[start];
      if(start>end){
               return
      }
      while(left<right){
          while(left<right && arr[right]>=temp){
               right--;
           }
           arr[left]=arr[right];
            while(left<right && arr[left]<=temp){
                   left++;
            }
            arr[right]=arr[left];
      }
      arr[left]=temp;
      quick(arr,start,left-1);
      quick(arr,left+1,end);
}`

###创建自己的对象
- 构造函数

#### 原型链
*

####作用域链
* 由内向外

###程序的预解析
* 词法解析：先判断语法有无错误
* 变量解析
* 块
* 函数


#### 加载完后展示
window.onload=function{
  var div = document.querySelector("div");获取div

}

##闭包
* 在一个函数里面，嵌套另外一个函数，当里层函数引用外层函数变量，并且里层调用的时候，闭包形成。
* 能够让局部变量的变化值保存下来。
* 用在需要保留局部变量的时候，但是会造成内存泄露。
```
function fn(){
    var num=0;
    return function (){
      num++;
      console.log(num);
    }
}
var a = fn()
     a()
     a()
     a()
     a()

结果：1,2,3,4
```
###对浏览器进行操作
* bom Browser Object Model
 浏览器对象模型
  * 地址栏（location）
  * 地址栏里出现的：
  1.http:// 协议<br>
  2.用户名和密码（一般不用）
  3.服务器名称 baidui.com <br>
  4.端口<br>
  5.路径<br>
  6.查询字符串 <br>
  7.# 锚链接（定位，业内跳转，一般不用）

* bom属性 ：location属性
  * location.href 获取路径
  * location.protocol 获取协议名
  * location.hostname 服务器名
  * location.host 服务器及端口号
  * location.port 端口号
  * location.pathname  目录和文件名
  * location.search 查询字符串，以问好开头
  * location.hash 锚链接
* history 控制页面前进后退
  * history.forward() 前进// history.go(1)
  * history.back() 后退//history.go(-1)
* dom Document Object Model
文档对象模型
* document 操作文档
   * 对内容进行操作

   * 对属性进行操作<br>
   1.自带的属性<br>
   2.自定义的属性
   * 对样式操作<br>
  1.获取样式<br>
  获取嵌入式和外部样式，行内：getComputedStyle()<br>
  2.设置样式<br>
  div.style.width<br>
  div.style.cssText(对css重新设置，无视其他)="width:;height:;"<br>
  3.获取css中的特殊属性（尺寸，位置）<br>
  1.获取元素真正的尺寸和位置：offsetWidth/Height/Left

* 属性方法
  * document.documentElement.clientWidth/Height 浏览器的宽高
  * document.querySelector();选择器，获取对象（）可以写类名，标签
    * var a = document.querySelector("div");
  * 操作class类，用className
  * 获取样式
  getComputedStyle(目标元素,null).height
  * parseInt(),将字符串解析成整数
  * setInterval() 定时器， 按照指定的时间不断的执行某些代码，单位毫秒
  * setTime0ut定时器，在指定的时间执行一次代码
  * 清除定时器 clearInterval()
  * 获取元素真正的尺寸和位置：offsetWidth/Height/Left
### 事件
* 发生了什么事件
  * 鼠标事件：<br>
  click（点击），dblclick，mousedown（按下鼠标），mouseup（抬起鼠标），mouseover（鼠标放上），mouseout（鼠标移出），mousemove（）
  * 键盘事件<br>
  keydown，keyup，keypress
  * js自带事件<br>
  onload
  * 硬件事件
   检测摄像头是否打开
   * 移动端<br>
   触摸事件：touchstart，touchemove，touchend
* 目标对象是谁（事件源，作用在谁身上）
* 做了什么事情（事件处理程序）
* html对象.on事件=function(){}写事件最简单的一种方式

###选项卡
