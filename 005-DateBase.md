## 数据库
* 数据库的分类
  * 关系型数据库：以实体与实体之间的关系，来构建数据库表<br>
     大型的   oracle  sybase  db2<br>
     中型的   mysql   sqlserver<br>
     小型的  access
  * 非关系型数据库：
    表与表之间不存在关联关系，每一张表都是一个独立个体
  * nosql（不仅仅支持sql）
    MongDB 文档型数据库，以Json字符串形式来存储数据
    内存键值对  memachche  redis（缓存数据库，基于内存存储）
  * 数据仓库
    
### MySQL  sql:
* SQL:structural query language 结构化查询语言
* 重要性  ：所有有价值的数据基本都存在数据库
#### 分类
* DML ：date mainipulation language 数据操作语言
  * insert ：添加行数据<br>
  insert into 表名 VALUES(字段);
  * update  ：修改行数据<br>
  update 表名 set 字段名 = 新的字段值 where 过滤条件
  * delete  ： 删除行数据<br>
  delete from 表名 where 过滤条件
  * select（DQL）  : 选择查询数据
* DDL ：数据定义语言
  * create table ：创建表
  * alter table  ：更改表结构，添加，删除，修改列长度。<br>
  ALTER TABLE 表名 ADD增加/drop删除/MODIFY修改 新字段名 数据类型
  * drop table ： 删除表
  * create index ： 在表中建立索引
* DCL （数据控制语言）
  * commit：提交事务处理
  * rollback ：回滚 （账户A -1000 --1000 -> 账户B）
* DBMS   数据库管理软件  database manager system  <br>
  DB     数据库  database  <br>
  Table   表<br>
  row    行<br>
  column   列


#### SQL 语法规范
* sql语句中，大小写不敏感，无论是命令还是表名
* sql语句可以写在一行或多行，以分号作为一条语句的结束
* 在书写sql语句时，一般也要遵循缩进格式，提高可读性
* sql关键字最好大写，以和其它语句作区分，关键字另起一行

### DML的学习

* select
  * 别名  表的别名
  * 别名 ：一般使用双引号标识
`SELECT employee_id AS "员工编号", last_name AS "员工姓名", salary
FROM employees;
  # 简写
SELECT employee_id 员工编号, last_name 员工姓名, salary
FROM employees;`

  * 通配（代表所有字段）
  select * <br>
  from 表名;
  * 查询某些字段<br>
  select 字段名<br>
  from 表名;
  * WHERE  (可添加过滤条件)
  * AND
  且 同时判断
  * BETWEEN   AND
  在多少和多少之间
  * OR
  或
  * IN(5,9)  是5或者9的
  * 模糊查询 like（%  —）
  1.含有  '%字符%'
  2.开头  '字符%'
  3.结尾 '%%字符'
  4.第2个`'_字符%'`
  5.包含两个  '%字符%字符%'
  * IS NULL
  是空值
  * IS NOT NULL
  不是空值
  * ORDER BY  排序  desc  降序  asc  升序   
  * DISTINCT  去重，在字段前面使用
  * CONCAT(参数，参数，。。。) 拼接
  * LENGTH(字符串)    返回字符串的长度
  * AS 后面跟别名  可以不写
  * 二次排序 ： 先排序第一个条件，当第一个条件相同，在排序第二个条件

### 多表查询  (内连接 和 外连接)
* 笛卡尔积：所有表中的所有记录进行连接
   出现笛卡尔积的场景<br>
   （1）缺省了连接条件<br>
   （2）连接条件无效
* 在多表查询时，如果独立存在的字段，可以省略表别名，如果有重复字段，必须要添加表别名
* 内连接 ：只查询多个表中相互之间能够匹配的行
  * 等值连接 （内连接 INNER JOIN  ON）
  * INNER JOIN = JOIN
   * sql92<br>
   `SELECT e.employee_id , e.department_id , d.department_name
    FROM employees e , departments d
    WHERE e.department_id = d.department_id;`
   * sql99<br>
    sql优化 在查询的过程中给字段添加前缀，可以提高查询效率
   `SELECT e.employee_id , e.department_id , d.department_name
    FROM employees e
    INNER JOIN departments d
    ON e.department_id = d.department_id;`
  * 特殊情况
    因为
   `SELECT * FROM employees
   WHERE 1=2
   或者  WHERE 1!=2;`
* 反单引号： sql有一些保留字和关键字，当字段与他们同名时，加反单引号区分
####非等值连接
* between and
####自连接
* 自己跟自己连接 ，把一张表当做两张表来进行操作
###外连接
* 多张表之间进行关联查询，除了返回满足连接条件的记录，还会返回不满足连接条件的记录。
* 左外连接：除了返回满足连接条件的记录，还会返回左表不满足条件的记录
  * left outer join
  on
* 右外连接：除了返回满足连接条件的记录，还会返回右表不满足条件的记录
  * right join
    on
* 满外连接 ：Mysql中不支持,一般使用UNION关键字代替
  * UNION : 获取查询结果的并集（全部）
#### SQL 函数
* 单行函数：
  * 控制大小写函数：UPPER('abc'),LOWER();
  * 字符控制函数：substring(字符,开始下标,长度)
   instr();
  * 注意：在sql语句中，所有的索引都是从1开始的
  * case  when语句
  `select 输出字段,
  case  打印
  when -- then
   打印
   when -- then
   打印
   else
   打印
   end`
   * ROUND(数字,小数点后保留几位)  四舍五入
   * TRUNCATE(数字,保留几位小数)  截断小数位
   * MOD(数字,除数)  余数
* 通用函数
IFNULL(字段,如果为空，用来替代)
* 多行函数，聚合函数，分组函数（多进一出）,把多个字段的值传递到该函数中，返回一个结果
* 数据库的常用类型：数值型、字符型、日期型（显示当前时间，now()）
   * AVG()  平均
   * MAX()  最大
   * MIN()  最小
   * SUM()  和
   * COUNT() 计数
* 分组函数
 * group by (可以将表中的数据分为若干组，声明在where关键字的后面)
 * having() 组过滤，放在group by后面 可以将函数计算的结果用作过滤条件 ，可以使用列的别名
 * order by 排序

#### 多表子查询
* 子查询 ： 在查询过程中，子查询在主查询之前一次执行完成，子查询的结果会被主查询调用。
* 语法 ：
    * 子查询必须要包含在括号里
    * 将子查询放在比较条件的右侧
* 分类
  * 单行子查询： 返回的结果只有一行，使用单行比较符
  * 多行子查询：返回的结果是多行，使用比较操作符
  * IN ：等于子查询返回结果的任意一个
  * ANY ： 和子查询返回结果中的某一个值比较
  * ALL ： 和子查询返回结果中的所有值进行比较
####总结：
* 语法：
* SELECT  字段 ， 字段， 单行函数 ， 组函数（多行函数）case结构
* FROM 表
* JOIN 表
* ON  连接条件（等值连接，非等值连接）
* WHERE 行过滤条件
* AND  多个行过滤条件
* GROUP BY 分组字段（1个或多个）
*  HAVING 组过滤条件
* AND 多个组过滤条件
* ORDER BY 排序字段（1个或多个）
* limit 限制输出（mysql分页）

### select语句执行顺序
* from 子句组装来自不同表中数据
* where 子句基于指定条件对数据进行过滤
* group by 子句将数据划分若干个组
* 执行分组函数（聚合函数），进行计算
* having 子句对分组数据进行过滤
* 执行表达式（case 结构）
* select 进行数据展示
* order by 子句对指定条件进行数据排序
* limit 子句对数据的输出进行限制。


### 创建表管理表
* create table 创建表
* 语法：create table 表名(字段名,数据类型，。。。。);
* 注意：在创建表时，必须要指定：表名，字段名，数据类型，尺寸。
* `create table t_user(
		id int primary key auto_increment,
		name varchar(20)//字符串 not null//不为空,
		age int not null
	)  ;  创建表格`
* sql中常用的数据类型
  * int ：整型数据，存储大小为4个字节
  * char(size) :定长字符数据，如果没有指定尺寸，默认为1个字节，最长为255
  * varchar(size) :可变长字符数据，可以根据字符串的实际长度，进行保存。<br>
    注意：varchar必须指定长度
  * float(m,d):单精度，m代表整数位+小数位，一共多少位，d代表小数位
  * double(m,d)： 双精度
  * date ：日期型数据，默认格式：yyyy-mmm--dd
  * BLOB：大对象类型，以二进制的方式来存储长文本数据。最大可以存储4G的单个文件
  * text： 存储长文本数据(纯文本)，最大可以存储4g的单个文本。

### 关于数据库的日常操作
* show databases; 显示当前mysql数据库中都创建了那些数据库
* use 数据库名; 使用数据库
* show tables; 查询当前数据库下的所有表
* create database 数据库名; 创建数据库
* 第一种
  `create table t_user(
		id int primary key auto_increment,
		name varchar(20)//字符串 not null//不为空,
		age int not null
	)  ;  创建表格`
* 第二种：
   * 使用子查询创建表，
   * 在创建表的过程中，执行一个select 操作，然后将查询结果传入到创建的表中
   * AS关键字，连接创建表和查询表的操作
 `create table t_emp2
  AS
  select employee_id,last_name
  from employees;`
* 只复制表结构，过滤数据 ，where 1=2；
* 查看表结构 describe 表名 或者  desc 表名<br>

* 修改表列 alter
* 通过alter table 来修改
* 给表添加一个新字段
* ALTER TABLE 表名 ADD 新字段名 数据类型
* 删除一个列：
 * alter table 表名 DROP 删除字段 数据类型
* 修改一个列：数据类型，数据长度
  * alter table 表名 MODIFY 新字段名 数据类型
  * 该操作建议使用修改空表，对有数据的表不建议改操作。
* ALTER TABLE t_emp MODIFY last_name INT;
* 重命名表名
* 语法：ALTER TABLE 旧表名 RENAME TO 新表名

* 删除表
* 语法：DROP TABLE 表名

* 清空表 ：将表中所有数据清空
* TRUNCATE TABLE 表名

#### 表数据插入
* 方式一：按照字段默认的顺序赋值
* 语法 insert into 表名 VALUES (字段值。。。);
* INSERT INTO  t_emp VALUES(1,'原泽杨'，8000);

* 方式二：按照指定字段顺序赋值
* 姓名，生日，其他字段赋值为null
* 注意：日期类型需要添加单引号
* INSERT INTO t_emp(emp_name,emp_birthday) VALUES("原泽杨"，'1998-01-10');

* 方式三：基于现有的表，导入数据
`INSERT INTO t_emp(emp_id,emp_name)
select e.emp_id,e.last_name
from emp e;`


#### 更新行数据 update 语句
* 语法 ：update 表名 SET 字段名=新字段值。。。where 过滤条件
* 更新姓名为King的员工的薪水为100000；
`UPDATE t_emp SET emp_salary=100000 WHERE emp_name='King'; `

#### 删除表数据：delete语句
* 语法：delete FROM 表名 where 过滤条件

### 数据库中的约束
* 约束：对表中的字段进行一种强制的规定
* 常用的约束：
  * 非空约束(not null)
  * 唯一性约束(unique)
  * 主键约束(primary KEY),主键=非空+唯一
  * 外键约束(foreign KEY)
  * 检查约束(check):在mysql中无效，在oracle 中有效
  * 默认值约束(default)

* 非空约束
* 添加约束有两种方式: 列级约束、表级约束
* 列级约束
* 在创建表后，添加约束：
* 语法：alter table 表名 MODIFY 字段名 数据类型 约束;
`ALTER TABLE t_stu MODIFY score DOUBLE not NULL;`

* 在创建表后，删除约束：
* 语法：alter table 表名 MODIFY 字段名 数据类型 约束;
`ALTER TABLE t_stu MODIFY score DOUBLE NULL;`

* 唯一约束
 * 注意：在唯一约束下，null值可以插入多次
* 表级约束
* 语法： constraint 约束名称 约束类型（字段名）

* 主键约束
  * 非空约束+唯一约束，用来表示表中的唯一的
* 语法：constraint 表名_字段_pk primary key(字段名);

* 外键约束
* 学生表 ，有一个cid, 班级表也有一个cid,当学生表在插入数据时
* 要求学生表的cid字段赋的值必须是班级表中cid字段存在的值；
* 注意：主表在创建外键时，主表字段引用的其它表对应的这个字段，<br>
  要求必须该表的主键 ，否则主表无法创建外键
  #表级约束，创建外键
* 语法：CONSTRAINT 外键名 foreign key(当前的外键字段)REFERENCES 关联表名（关联字段）
* 注意：#注意：在外键约束下，被引用的数据，无法直接删除，<br>
    只能先删除引用数据，然后再删除被引用数据
* 第一步:
DELETE FROM t_stu6 WHERE cid=101;
* 第二步:
DELETE FROM t_class WHERE cid=101;
* 检查约束（check）
* 对某个字段进行约束
* 注意:检查约束在mysql中无效，在oracle中有效

* 默认约束
* 在添加数据是，没有给指定默认值的字段添加数据，则为默认值，反之以添加数据为准。
### 分页
* 分页语法： limt 数字1,数字2
  * 数字1 ：每页显示的数据的起始位置
  * 数字2 : 每页显示的数据条数
  * limt 数字  限制输出前几条
* 公式：limit (当前页-1)* 每页条数，每页条数


* read   读取
* update  更新  update  t_user set age =40 where name ='zs';
* delete  删除  detele from t_user where name = 'zs'
* mysql -uroot -p;   进入数据库
* show databases; 查看所有的数据库
* use world; 进入到某个数据库
* show tables; 查看该数据库有多少张表table；
* select * from city(表名);查看某个表的所有数据
* select * from city  limit 0,5; 查看某个表的前5条数据
* create database db_chat; 创建数据库，注意名字命名规则
* create table t_user(
		id int primary key auto_increment,
		name varchar(20)//字符串 not null//不为空,
		age int not null
	)  ;  创建表格


* insert into t_user(name,age) values('zs',20);  添加数据
* desc table t_user; 描述表格
* drop table t_user;  删除表格
* drop base db_chat; 删除数据库
* delete from t_user where id=2;  删除第2行的数据
*  select * from t_user;  查询所有行所有列
   * select name , age from t_user;

	 * select name , age from t_user where id > 1 or name='ls';

	 *  select name , age from t_user order by name desc;
* select name,age from t_user where name like '_ s%';  模糊查询

## java连接数据库模板
`//加载驱动实现类
  Class.forName("com.mysql.jdbc.Driver");
  //利用驱动管理器获取数据库连接
  Connection conn =DriverManager.getConnection("jdbc:mysql://localhost:3306/db_chat","root（用户名）","123456（密码）");
  //准备sql语句
  `
* JDBC中Statement 接口提供了三种执行 SQL 语句的方法：

   * executeQuery：用于产生单个结果集（ResultSet）的语句，这个方法被用来执行 SELECT 语句，但也只能执行查询语句，执行后返回代表查询结果的ResultSet对象
   * executeUpdate：用于执行 INSERT、UPDATE 或 DELETE 语句以及 SQL DDL（数据定义语言）语句，例如 CREATE TABLE 和 DROP TABLE。
INSERT、UPDATE 或 DELETE 语句的效果是修改表中零行或多行中的一列或多列。executeUpdate 的返回值是一个整数（int），指示受影响的行数（即更新计数）
   * execute：  可用于执行任何SQL语句，返回一个boolean值，表明执行该SQL语句是否返回了ResultSet。
如果执行后第一个结果是ResultSet，则返回true，否则返回false。
但它执行SQL语句时比较麻烦，通常我们没有必要使用execute方法来执行SQL语句，而是使用executeQuery或executeUpdate更适合。
但如果在不清楚SQL语句的类型时则只能使用execute方法来执行该SQL语句了。
使用哪一个方法由 SQL 语句所产生的内容决定。
