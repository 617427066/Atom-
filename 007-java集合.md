## 集合
* 集合分为Collection 和Map 两种体系
* 集合的长度可以动态扩充（底层自动扩充）
* 数据类型：  
      * 如果没有泛型，一个集合可以添加任何类型
      * 有泛型，则只能添加泛型要求的类型
* 集合的特点
  * 在没有泛型的情况下，集合中存储元素时，都是以Object类型对待
  * 在集合存储过程中，如果元素时基本类型，那么会自动装箱。
  * 在集合中，存储的元素都是引用类型。  
* Collection接口：
Set接口：元素无序、不可重复的集合；
List接口：元素有序，可重复的集合；
* Map 接口
  具有映射关系的“key-value对”的集合
#### 集合和数组的区别
* 数组：
   * 数组的长度是指定的，不可扩充
   * 数组只能存放相同数据类型的元素
   * 是基本数据类型
* 集合：
    * 集合没有指定长度，动态的。
    * 在没有泛型的情况下，集合存储任何数据类型的元素，以Object 类型对待
    * 有泛型，按照泛型规定存储
    * 存储的元素都自动装箱，为引用类型

#### 迭代器
* Iterator ite = c1.iterator();<br>
  //遍历<br>
  while（ite.hasNext()）{<br>
  syso(ite.next());<br>
}
###  Collection 接口
* Collection 接口是 List、Set 和 Queue接口的父接口
#### 迭代器
* Iterator迭代器（设计模式的一种），主要用于遍历Collection 集合中的元素。
* Iterator ite = c1.iterator();<br>
  //遍历<br>
  while（ite.hasNext()）{<br>
  syso(ite.next());<br>
}
#### 遍历的四种方法
* 迭代器
Iterator ite = c1.iterator();<br>
while(ite.hasnext()){<br>
  syso(ite.next);<br>
}
* foreach
for(类型 aa : a){  要遍历的元素类型  遍历后的元素名称   要遍历的元素名称<br>
  syso(aa);<br>
}
* for
* toString方法
syso(a.toString);
#### List接口
* List集合类中元素有序、且可重复，集合中的每个元素都有其对应的顺序索引。
* List 接口中的实现类：ArrayList、 LinkedList、  Vector
* 三个实现类的比较
   * ArrayList 可变数组（动态数组），增删效率低，查询效率高
   * LinkedList  双向链表（一个节点有三个部分构成），增删效率高，查询效率低
   * Vector  和ArrayList功能一样，但是线程安全，效率低。
* ArrayList
ArrayList是对象引用的一个”变长”数组，ArrayList 是线程不安全的，
* LinkedList
 * poll
 * push
* Vector
线程安全
#### set的实现类
* HashSet
    * 底层结构：维护了一个HashMap对象，基于哈希表结构存储元素；
    * 底层构成：数组 + 链表 + 红黑树；
* HashSet 具有以下特点：
   * 不能保证元素的排列顺序；
   * HashSet 不是线程安全的；
   * 集合元素可以是 null；
* 当往HashSet集合中存储元素时，首先调用该对象的hashCode方法，返回一个值（Hash值，对象在内存中存储的地址）;<br>
   当对象太多的情况下，hash值有可能会重复，就往后存储，然后分叉，最多分两个叉。
* HashSet 集合判断两个元素相等的标准：两个对象通过 hashCode() 方法比较相等，并且两个对象的<br>
 equals() 方法返回值也相等。
* HashTable  线程安全
* 重写hashCode方法的思路：
	 * 	将对象的所有属性的hash值进行累加，求出一个累加和；
	 * 二次hash ： 就对object类实现的hashCode方法进行重写，求出一个新的hash值，<br>
	 			而该hash值，并不是对象在内存中存储的地址，仅仅是使用新的hash值，<br>
				来决定存储在哈希表中的哪一个位置；
* 重写equals方法的思路;
	 * 	比较对象之间的所有属性，是否相同，如果有一个属性值不同，那么返回false;
	 * 	如果全部相同，返回true；
*  当HashSet在存储元素时，首先调用该对象的hashCode方法，返回一个hash值，根据
		 *  该hash值来决定存储在哈希表中的哪个位置；
		 *  如果hashCode方法返回的hash值不同时，就调用equals方法继续比较了，hashSet直接把该元素直接添加到哈希表中
		 *  如果hashCode方法返回的hash值相同时，那么再调用equals方法来进行判断
     *  当调用完hashcode方法后，还会调用equals方法，来判断集合中的元素和当前对象的属性值是否
		 *   相同，如果相同，新元素就覆盖了旧元素，如果不同，就把新元素添加进去；<br>
		  补充：如果只重写hashCode方法，并没有重写equals方法，那么equals方法比较的是对象之间的地址；
### Java比较器
* 内部比较器（一个参数）
将比较方法，在比较类中实现
  * 步骤  
    1.创建一个比较接口，在该接口中设计一个比较方法`public int CompareTo(Object obj){}`<br>
    2.让准备实现比较功能的类，实现比较接口，从而实现compareTo比较方法<br>
    3.在比较过程中，使用冒泡排序来实现比较接口，从而实现compareTo比较方法
    4.不管是比较方法，排序方法，都应该使用多态的语法，从而避免方法的大量重载。
* 外部比较器（两个参数）
   将比较方法提取到接口中，然后让比较的类来实现
   * 步骤：
   1.构建比较方法的接口<br>
   2.构建具有比较攻能的类.
* JDK中已经有了Comparable 接口，自然排序。具有compareTo 比较方法，默认是升序，可以加-，使它变成降序
* TreeSet
 TreeSet() : 在存储元素时，会调用该元素的CompareTo()方法，通过方法的返回值来决定排序的顺序；
  * 注意：TreeSet要求所有的元素必须要实现Comparable接口，否则就报该异常
  * 特点：1）不允许重复，里面不能存储null对象（null对象无法排序）；<br>
         2）实现了对元素的排序：<br>
1>自然排序（默认，必须实现Comparable接口）；
2>自定义排序；
### Map
* 三个实现类
  * HashMap
  * LinkedHashMap
  * TreeMap
* 构建map集合
`Map map= new HashMap()`
* 常用方法
   * 添加元素 put
   * 删除元素 remove
   * 根据key，获取对应的value `Object obj = map.get();`
   * 判断map中，是否包含指定的key `boolean flag = map.containsKey();`
   * 清除map集合  clear();
   * size()  获取长度
* 遍历map的方法
  * map.tostring();
  * 用映射关系来遍历 entry
    * `1） 获取到map中所有的映射关系：entry对象（包含了一个元素中的key和value）
		 Set entrySet = map.entrySet();
		2）遍历所有的映射关系;
		Iterator iter = entrySet.iterator();
		while(iter.hasNext()) {
			//Entry属于Map类中的一个内容类：
			Map.Entry entry = (Map.Entry)iter.next();
			//获取映射关系对象中的key和value:
			System.out.println(entry.getKey() +" , "+entry.getValue());`
  * 使用set结构获取所有的key
  `Set keySet = map.keySet();
		Iterator iter = keySet.iterator();
		while(iter.hasNext()) {
			Object key = iter.next();
			System.out.println(key +","+map.get(key));`
*  HashMap
  * 底层是哈希表；
  * 允许使用null键和null值，与HashSet一样，不保证映射的顺序。
  * HashMap 判断两个 key 相等的标准是：两个 key 通过 equals() 方法返回 true，hashCode 值也相等。
  * HashMap 判断两个 value相等的标准是：两个 value 通过 equals() 方法返回 true。
* HashMap的存储结构：
  *  JDK 7及以前版本：HashMap是数组+链表结构(即为链地址法)
  *  JDK 8版本发布以后：HashMap是数组+链表+红黑树实现。


###泛型
* 泛型的好处
