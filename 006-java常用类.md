## 常用类
####数据类型之间的转换
* 常用方法
  *
* `int i = 10;

		/**
		 * 一 、 基本数据类型 ---> 引用类型
		 */
		/**
		 * JDK1.5 之前API
		 */
		//第一种：通过构建器：
		Integer interger = new Integer(i);
		System.out.println(interger.MAX_VALUE);
		System.out.println(interger.MIN_VALUE);
		System.out.println(interger.toString());
		Double d = new Double(3.14);

		//第二种：通过静态功能方法：valueOf()；
		Integer inter = Integer.valueOf(i);
		System.out.println(inter);
		Float f = Float.valueOf(3.14F);

		/**
		 * jdk1.5 之后API
		 */
		//自动装箱：将基本数据类型包装成引用类型
		Integer num = 20; // Integer num = new Integer(20);
		Double dd = 3.14; // Double d = new Double(3.14);


		/**
		 * 二、引用类型 ----> 基本类型：
		 */
		/**
		 * JDK1.5 之前API
		 */
		Integer num1 = 30;
		//intValue() : 将包装类对象转变成基本类型：
		int num2 = num1.intValue();
		Long l = 50L;
		long ll = l.longValue();
		System.out.println(ll);
		System.out.println(num2);

		/**
		 * JDK1.5 之后API:
		 */
		//（1）自动拆箱：将包装类中的value属性值获取，然后赋值
		int num4 = num1;


		Integer i1 = 30;
		Integer i2 = 5;
		//（2）当包装类对象在进行运算,或者比较时，会自动拆箱（先转成基本类型，然后再参与运算）；
		int num5 = i1 / i2;
		if(i1 > 30) {
			System.out.println("i1");
		}

		/**
		 * 三、字符串转成包装类对象：
		 */
		//字符串100--->Integer;
		String str = "100";
		//通过构造器：
		Integer num3 = new Integer(str);
		//自动拆箱：
		int i4 = new Integer(str);
		System.out.println(num3);

		/**
		 * 四、字符串转成基本数据类型：
		 * parseXXX（） ：
		 */
		//使用静态方法：
		int i3 = Integer.parseInt("200");
		String str1 = "3.1415";
		double d1 = Double.parseDouble(str1);
		String str2 = "true";
		boolean flag = Boolean.parseBoolean(str2);

		/**
		 * 五、基本数据类型转成字符串：
		 * String类的方法：valueOf()
		 */
		// 1)
		String str3 = String.valueOf(300);
		// 2)
		int i5 = 10;
		String str4 = i5 + ""; //"" 空字符串`
### 字符串相关类
* String
* StringBuffer
* StringBuilder
String：不可变字符序列；
StringBuffer：可变字符序列、效率低、线程安全；
StringBuilder(JDK1.5)：可变字符序列、效率高、线程不安全；
* String 相关方法
  * 特殊情况： String s = "abc"+"def";编译时会优化， 常量池中出现的是abcdef
	* str.length()  获取长度
	* charAt(int index) `str.charAt(2)`获取指定下标位置的字符
	* 字符串转为 字符串数组   String[] str1 = str.split(",");//用逗号隔开的字符串数组
	* 字符串转为 字符型数组   char[] c = str.toCharArry();
	* str1.equals(str2 | "abc")  判断两个字符串内容是否一样
	* equalslgnore  忽略大小写判断
	* .compareTo() 比较两个字符串内容的大小
	* str1.indexOf("")  在字符串中查找指定的子字符串
	* str1.lastIndexOf()  查找指定字符串最后出现的位置
	* substring()  截取子字符串  (两种)
	* startsWith()   判断是否是以xxx开头的
	* endsWith()   判断以什么结束的字符串
	* replace ('s','S')  将s  替换为S
	* trim()   去掉前后空格
	* contains()   判断是否含有某一子字符串
	*  concat()   字符串拼接
	*   
* StringBuffer 相关方法
 *  append()   拼接字符串
 *

###时间相关类
* 时间戳  System.currentTimeMillis()
* Java.util.Date类：以对象的方式，来表示当前系统时间
* Java.sql.Date类（子类） ： 对应着数据库中的日期类型
* 两个构造方法：
		 * 	(1)new Date(); 构建当前系统时间对象
		 * 	（1）new Date(long time); 通过long值指定构建系统时间对象
		 * 两个功能方法：
		 * 	(1)date.getTime() ；返回当前date表示时间对应的时间戳
		 * （2）toString() : 显示对象格式：dow mon dd hh:mm:ss zzz yyyy
* SimpleDateFormat : 对日期date类对象进行格式化，解析；
* 构造方法：
		 * 	（1） 无参 : 使用默认格式来对日期进行格式化
		 *  （2）有参 : 可以指定日期格式化的正则匹配格式
		 * 方法：
		 *  格式化：  String format(Date date)
		 *  解析：    Date parse(String time)
* 有参构造：按照指定的正则进行对日期对象格式化，或者解析：
		SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy/MM/dd HH/mm/ss");
	* 注意:在解析时，必须按照指定好的日期格式来进行解析
*  JDK1.8 之后：时间相关类
		 LocalDateTime , LocalDate , LocalTime

### System
* System类内部包含in、out和err三个成员变量，分别代表标准输入流(键盘输入)，标准输出流(显示器)和标准错误输出流(显示器)。
