##JDCBC
* jdbc :java database Connectivity JAVA数据库连接
* JDBC的API：封装在java.sql包下
* 驱动管理类：DriverManager ，通过该类可以获取到程序与数据库的连接
* 连接接口：Connection ,通过连接接口的对象，可以实现与数据库的增删改查操作，并且
  可以
* 发送指令器接口：Statement，可以通过该接口对象，程序向数据库发送操作指令（sql语句），返回结果
* 结果集（集合）接口：ResultSet，sql执行结果会封装到一个结果集对象的集合中。
###
`		String driver = "com.mysql.jdbc.Driver";
		String url = "jdbc:mysql://localhost:3306/ubdf1907";
		String userName = "root";
		String passWord = "123456";
		//1.准备操作的数据库的驱动架包，MySql

		//2、加载数据库驱动
		Class.forName(driver);
		//创建数据库连接
		Connection conn = DriverManager.getConnection(url, userName, passWord);
		//sql语句
		String sql ="select * from t_class";
		//获取发送指令器的对象，然后执行sql操作，返回结果集
		Statement stmt = conn.createStatement();
		ResultSet resultSet = stmt.executeQuery(sql);
		//处理结果集
		while(resultSet.next()) {
			//获取结果集，数据库中的下标是从1开始

//			//使用下标来获取一行中的各个属性值
//			int cid =resultSet.getInt(1);
//			String cname = resultSet.getString(2);
//			System.out.println(cid+","+cname);

			//使用属性名来获取属性值
//			int cid = resultSet.getInt("cid");
//			String cname = resultSet.getString("cname");
//			System.out.println(cid+","+cname);

			Integer cid = (Integer) resultSet.getObject(1);
			String cname = (String) resultSet.getObject(2);
			System.out.println(cid+","+cname);
		}
		resultSet.close();
		stmt.close();
		conn.close();`

## java连接数据库基本模板
  `//加载驱动实现类
      Class.forName("com.mysql.jdbc.Driver");
      //利用驱动管理器获取数据库连接
      Connection conn =DriverManager.getConnection("jdbc:mysql://localhost:3306/db_chat","root（用户名）","123456（密码）");
      //准备sql语句
      String sql = "";
      //获取发送指令器的对象，执行sql 操作，并返回结果集
      Statement stmt =conn.createStatement();
      //如果是查询
      ResultSet rs = stmt.executeQuery(sql);
      //如果是增删改
      int State  = stmt.executeUpdate(sql);
      //关闭
      `
*  IO : properties类
		 * 使用步骤：1）在项目的src（项目源码）下，创建一个后缀为.properties的文件
		 * 			2)创建properties对象；加载配置文件中的数据

*	读取配置文件
  * Properties prop = new Properties();<br>
	* prop.load(new FileInputStream("src/my.properties"));
