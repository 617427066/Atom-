## JS
* JavaSpcript：基于对象，基于事件驱动的，弱类型的解释性语言。
* JS的任务就是对浏览器里面的内容进行操作



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

### json格式
* 属性："值"
* "属性"："值"
##排序
* 冒泡排序
function f1(arr) {
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
      }
* 选择排序  
function f2(arr) {
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
}

* 快速排序
function quick(arr,start,end) {
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
}
