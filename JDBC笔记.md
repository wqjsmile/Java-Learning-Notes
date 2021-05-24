1. 什么是JDBC？

   Java DataBase Connectivity(Java语言连接数据库)

   在java语言中编写SQL语句，对mysql数据库中的数据进行CRUD操作

2. JDBC本质上是什么？ java.sql.*这个包下都是JDBC的接口，SUN公司制定的！JDBC实际上的作用是降低Java和数据库之间的耦合度，Java程序员写一套JDBC程序，可以连接任何一个品牌的数据库。

   JDBC整个程序的结构当中有三拨人：

   ​	第一波：SUN公司，负责指定JDBC接口。这些接口已经写好了，在java.sql.*;

   ​	第二波：java.sql.*下面的所有接口都要有实现类，这些实现类是数据库厂家编写的。我们连接的是mysql数据库，mysql数据库厂家的实现类是哪里呢？mysql-connector-java-5.1.23-bin.jar【术语叫做mysql的驱动】。jar包中有很多.class字节码文件，这是mysql数据库厂家写的接口实现！如果连接的是oracle数据库，你需要从网上下载oracle的jar包【术语叫做Oracle的驱动】。

   ​	第三波：我们java程序员，面向JDBC接口写代码就行。

   为什么要面向接口编程？

   ​	解耦合：降低程序的耦合度，提高程序的扩展力。

   ​	多态机制就是非常典型的：面向抽象编程。(不要面向具体编程)

   ```java
   Animal a = new Cat();
   Animal b = new Dog();
   //喂养的方法
   public void feed(Animal a){
       //面向父类型编程
   }
   
   不建议：
       Dog d = new Dog();
       Cat c = new Cat();
   ```

   ![image-20210522171852261](https://i.loli.net/2021/05/22/8FK5hp2cWVrMEwB.png)

   ```java
   模拟一下JDBC本质：
   ----------------------------------------------------------------------------
   JDBC.java:
   /*
   SUN公司负责指定这套JDBC接口
   public interface JDBC{
   	/*
   		连接数据库的方法。
   	*/
   	void getConnection();
   
   }
   ----------------------------------------------------------------------------    
   MySQL.java:
   /*
   	MySQL的数据库厂家负责编写JDBC接口的实现类
   */
   public class MySQL implements JDBC{
       public void getConnection(){
           //具体这里的代码怎么写，对于我们Java程序员来说没关系
           //这段代码涉及到mysql底层数据库的实现原理
           System.out.println("连接MySQL数据库成功！")
       }
   }
   ------------------------------------------------------------------------------
   Oracle.java:
   /*
   	Oracle的数据库厂家负责编写JDBC接口的实现类
   */
   public class Oracle implements JDBC{
       public void getConnection(){
           //具体这里的代码怎么写，对于我们Java程序员来说没关系
           //这段代码涉及到Oracle底层数据库的实现原理
           System.out.println("连接Oracle数据库成功！")
       }
   }
   -------------------------------------------------------------------------------
   SqlServer.java:
   /*
   	SqlServer的数据库厂家负责编写JDBC接口的实现类
   */
   public class SqlServer implements JDBC{
       public void getConnection(){
           //具体这里的代码怎么写，对于我们Java程序员来说没关系
           //这段代码涉及到SqlServer底层数据库的实现原理
           System.out.println("连接SqlServer数据库成功！")
       }
   }
   //实现类被称为驱动。(SqlServer驱动)
   
   --------------------------------------------------------------------------------
   /*
   	java程序员角色
   	不需要关心具体是哪个品牌的数据库，只需要面向JDBC接口写代码
   	面向接口编程，面向抽象编程，不需要面向具体编程
   */
   public class JavaProgrammer
   {
       public static void main(String[] args){
           JDBC jdbc = new MySQL();
           JDBC jdbc = new Oracle();
           
           //创建对象可以通过反射机制。
           Class c = Class.forName("Oracle");
           JDBC jdbc = (JDBC)c.newInstance();
           
           //以下代码都是面向接口调用方法，不需要修改
           jdbc.getConnection();
       }
   }
   ```

   

3. JDBC开发之前的准备工作？

   mysql的驱动jar包，需要配置到classpath当中吗？

   ​	mysql-connector-java-5.1.23-bin.jar里是字节码，是class文件。java虚拟机的类加载器会加载class文件，类加载器怎么能够找到这些class文件呢？需要配置classpath没有配置的情况下， 默认从当前路径下加载class。classpath如果配置死了，例如:classpath=D:\abc,表示固定只从d:\abc目录下找。

   以上的配置是针对于文本编辑器的方式开发，使用IDEA工具的时候，不需要配置以上的环境变量。IDEA有自己的配置方式。

4. JDBC编程六步(需要背会)

   ```java
   
   JDBC编程六步:
   	1. 注册驱动
       (通知java程序我们即将要连接的是哪个品牌的数据库)
       2. 获取数据库连接
       (java进程和mysql进程，两个进程之间的通道开启了)
       (java进程可能在北京，mysql进程可能在上海)
       3. 获取数据库操作对象
       这个对象很重要，用这个对象执行SQL的
       4. 执行SQL语句
       执行CRUD操作
       5. 处理查询结果集
       如果第四步是select语句，才有这个第五步
       6. 释放资源
       关闭所有的资源(因为JDBC毕竟是进程之间的通信，占用很多资源的，需要关闭！)
   ```

   ```java
   import java.sql.Driver;
   import java.sql.DriverManager;
   import java.sql.SQLException;
   import java.sql.Connection;
   import java.sql.Statement;
   
   public class JDBCTest01{
   	public static void main(String[] args){
   		Statement stmt = null;
   		Connection conn = null;
   		try{
   			//1. 注册驱动
   			Driver driver = new com.mysql.cj.jdbc.Driver();//多态，父类型引用指向子类型对象
   			DriverManager.registerDriver(driver);
   			
   			//2.获取连接
   			/*
               什么是URL？
                   统一资源定位符
               任何一个URL都包括：
                   协议+IP地址+端口号port+资源名
                   http://192.168.2.8888/abc
               协议：
                   是一个提前规定好的数据传输格式。通信协议有很多：http、https....
                   在传送数据之前，提前先商量好数据传送的格式
                   这样对方接收到数据之后，就会按照这个格式去解析，拿到有价值的数据。
               IP地址：
                   网络当中定位某台计算机的。
               PORT端口号：
                   定位这台计算机某个服务的。
               资源名：
                   这个服务下的某个资源。
   
               jdbc:mysql://          这是java程序和mysql通信的协议
               localhost              这是本机IP地址，本机IP地址还可以写成：127.0.0.1
               3306                   mysql数据库端口号
               bjpowernode            mysql数据库的名称
   
               jdbc:mysql://192.168.111.123:3306/abc
               如果是oracle数据库的话：
                   oracle:jdbc:thin:@localhost:1521:bjpowernode
                   oracle:jdbc:thin:@  这是oracle和java的通信协议
                   localhost      这是本机IP地址
                   1521           oracle默认端口
                   bjpowernode    oracle中数据库的名字
   
               localhost和127.0.0.1都是本机IP地址
   
   			*/
   			String url = "jdbc:mysql://localhost:3306/bjpowernode";
   			String user = "root";
   			String password = "wqjsmile111";
   			conn = DriverManager.getConnection(url, user, password);
   			System.out.println("数据库连接对象 = " + conn); //数据库连接对象 = com.mysql.cj.jdbc.ConnectionImpl@6166e06f
   			
   			//3. 获取数据库操作对象(Statement专门执行sql语句的)
   			stmt = conn.createStatement();
   			
   			//4. 执行sql
   			String sql = "insert into dept(deptno, dname, loc) values(50, '人事部', '北京')";
   			//专门执行DML语句的(insert delete update)
   			//返回值是"影响数据库中的记录条数"
   			int count = stmt.executeUpdate(sql);
   			System.out.println(count == 1 ? "保存成功" : "保存失败");
   			
   			//5.处理查询结果集
   			
   			
   			
   		} catch(SQLException e){
   			e.printStackTrace();
   		} finally{
   			//6.释放资源
   			// 为了保证资源一定释放，在finally语句块中关闭资源
   			// 并且要遵循从小到大依次关闭
   
   			try{
   				if(stmt != null){
   				stmt.close();
   			}
   			}catch(SQLException e){
   				e.printStackTrace();
   			}
   			
   			try{
   				if(conn != null){
   				conn.close();
   			}
   			}catch(SQLException e){
   				e.printStackTrace();
   			}
   		}
   	}
   	
   }
   ```

   ```java
   /*
   	JDBC完成delete
   */
   import java.sql.*;
   
   public class JDBCTest02{
   	public static void main(String[] args){
   		Connection conn = null;
   		Statement stmt = null;
   		
   		try{
   			//1.注册驱动
   			DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());
   			//2.获取连接
   			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
   			//3.获取数据库操作对象
   			stmt = conn.createStatement();
   			//4.执行SQL语句
   			//JDBC中的sql语句不需要提供分号结尾
   			String sql = "delete from dept where deptno=40";
   			int count = stmt.executeUpdate(sql);
   			System.out.println(count == 1?"删除成功":"删除失败");
   			
   		}catch(SQLException e){
   			e.printStackTrace();
   		}finally{
   
   			//6. 释放资源
   			if(stmt != null){
   				try{
   					stmt.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   			if(conn != null){
   				try{
   					conn.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   		}
   	}
   }
   ```

   ```java
   /*
   	注册驱动的另一种方式(这种方式常用)
   */
   
   import java.sql.*;
   
   public class JDBCTest03{
   	public static void main(String[] args){
   
   		
   		try{
   			//1.注册驱动
   			//这是注册驱动的第一种写法
   			//DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());
   			//注册驱动的第二种方式：常用的
   			//为什么这种方式常用？因为参数是一个字符串，字符串可以写到xxx.properties文件中
   			Class.forName("com.mysql.cj.jdbc.Driver");
   			//2.获取连接
   			Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
   			System.out.println(conn); //com.mysql.cj.jdbc.ConnectionImpl@6166e06f
   			
   		}catch(SQLException e){
   			e.printStackTrace();
   		}catch(ClassNotFoundException e){
   			e.printStackTrace();
   		}
   	}
   }
   ```

   ```java
   /*
   	将连接数据库的所有信息配置到配置文件中
   	实际开发中不建议把连接数据库的信息写死到java程序中
   */
   
   import java.sql.*;
   import java.util.*;
   
   public class JDBCTest04{
   	public static void main(String[] args){
   		//使用资源绑定器绑定属性配置文件
   		ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
   		String driver = bundle.getString("driver");
   		String url = bundle.getString("url");
   		String user = bundle.getString("user");
   		String password = bundle.getString("password");
   		
   		Connection conn = null;
   		Statement stmt = null;
   		
   		try{
   			//1.注册驱动
   			
   			Class.forName(driver);
   			//2.获取连接
   			conn = DriverManager.getConnection(url, user, password);
   			//3.获取数据库操作对象
   			stmt = conn.createStatement();
   			//4.执行SQL语句
   			//JDBC中的sql语句不需要提供分号结尾
   			String sql = "delete from dept where deptno=40";
   			int count = stmt.executeUpdate(sql);
   			System.out.println(count == 1?"删除成功":"删除失败");
   			
   		}catch(Exception e){
   			e.printStackTrace();
   		}finally{
   
   			//6. 释放资源
   			if(stmt != null){
   				try{
   					stmt.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   			if(conn != null){
   				try{
   					conn.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   		}
   	}
   }
   ------------------------------------------------------------------------------------------------
   jdbc.properties文件内容：
   driver = com.mysql.cj.jdbc.Driver
   url = jdbc:mysql://localhost:3306/bjpowernode
   user = root
   password = wqjsmile111
   ```

   ```java
   /*
   	处理查询结果集
   */
   import java.sql.*;
   import java.util.*;
   
   public class JDBCTest05{
   	public static void main(String[] args){
   		//使用资源绑定器绑定属性配置文件
   		ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
   		String driver = bundle.getString("driver");
   		String url = bundle.getString("url");
   		String user = bundle.getString("user");
   		String password = bundle.getString("password");
   		
   		Connection conn = null;
   		Statement stmt = null;
   		ResultSet rs = null;
   		
   		try{
   			//1.注册驱动
   			Class.forName(driver);
   			//2.获取连接
   			conn = DriverManager.getConnection(url, user, password);
   			//3.获取数据库操作对象
   			stmt = conn.createStatement();
   			//4.执行SQL语句
   			//JDBC中的sql语句不需要提供分号结尾
   			String sql = "select empno as a, ename, sal from emp";
   			// int count = stmt.executeUpdate(sql);
   			// System.out.println(count == 1?"删除成功":"删除失败");
   			// int executeUpdate(insert/delete/update)
   			// ResultSet executeQuery(select)
   			rs = stmt.executeQuery(sql); //专门执行DQL语句的方法
   			//5.处理查询结果集
   			
   			while(rs.next()){
   				//光标指向的行有数据
   				//取数据,以下程序的1.2.3说的是第几列
   				// getString()方法的特点是：不管数据库中的数据类型是什么，都以String的形式取出
   				//String empno = rs.getString(1); //JDBC中所有下标从1开始，不是从0开始
   				//String ename = rs.getString(2);
   				//String sal = rs.getString(3);
   				//System.out.println(empno + "," + ename + "," + sal);
   				
   				//重点注意：列名称不是表中的列名称，而是查询结果集的列名称。
   				/*
   				String empno = rs.getString("empno"); //以列名取，而不是以列号取
   				String ename = rs.getString("ename");
   				String sal = rs.getString("sal");
   				System.out.println(empno + "," + ename + "," + sal);
   				*/
   				
   				//除了可以以String类型取出之外，还可以以特定的类型取出
   				/*
   				int empno = rs.getInt(1);
   				String ename = rs.getString(2);
   				double sal = rs.getDouble(3);
   				System.out.println(empno + "," + ename + "," + (sal + 100));
   				*/
   				
   				int empno = rs.getInt("a");
   				String ename = rs.getString("ename");
   				double sal = rs.getDouble("sal");
   				System.out.println(empno + "," + ename + "," + (sal + 200));
   				
   			}
   			
   			
   			
   		}catch(Exception e){
   			e.printStackTrace();
   		}finally{
   
   			//6. 释放资源
   			if(rs != null){
   				try{
   					rs.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   			if(stmt != null){
   				try{
   					stmt.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   			if(conn != null){
   				try{
   					conn.close();
   				}catch(SQLException e){
   					e.printStackTrace();
   				}
   			}
   			
   		}
   	}
   }
   ```

   ![image-20210524111218657](https://i.loli.net/2021/05/24/dZIKwgT7hu3bcmp.png)

5. ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.*;
   import java.util.HashMap;
   import java.util.Map;
   import java.util.Scanner;
   
   /*
   实现功能：
       1. 需求：模拟用户登陆功能的实现
       2. 业务描述：
           程序运行的时候，提供一个输入的入口，可以让用户输入用户名和密码
           用户输入用户名和密码之后，提交信息，java程序收集到用户信息
           Java程序连接数据库验证用户名和密码是否合法
           合法：显示登陆成功
           不合法：显示登陆失败
       3. 数据的准备：
           在实际开发中，表的设计会使用专用的建模工具，我们这里安装一个建模工具：PowerDesigner
           使用PD工具来进行数据库表的设计。(参见user-login.sql脚本)
       4. 当前程序存在的问题：
           用户名: fdsa
           密码：fdsa' or '1' ='1
           登陆成功
           这种现象被称为SQL注入。(黑客经常使用)
       5. 导致SQL注入的根本原因是什么？
           用户输入的信息中含有sql语句的关键字，并且这些关键字参与sql语句的编译过程
           导致SQL语句的原意被扭曲，进而达到sql注入。
   
    */
   public class JDBCTest06 {
       public static void main(String[] args) {
           // 初始化一个界面
           Map<String, String> userLoginInfo = initUI();
           //验证用户名和密码
           boolean loginSuccess = login(userLoginInfo);
           //最后输出结果
           System.out.println(loginSuccess ? "登陆成功":"登陆失败");
       }
   
       /**
        *
        * @param userLoginInfo 用户登陆信息
        * @return false表示失败,true表示成功
        *
        */
       private static boolean login(Map<String, String> userLoginInfo) {
           //打标记的意识
           boolean loginSuccess = false;
           //单独定义变量
           String loginName = userLoginInfo.get("loginName");
           String loginPwd = userLoginInfo.get("loginPwd");
   
           // JDBC代码
           Connection conn = null;
           Statement stmt = null;
           ResultSet rs = null;
   
           try {
               // 1. 注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               // 2. 获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               // 3. 获取数据库操作对象
               stmt = conn.createStatement();
               // 4. 执行sql
               String sql = "select * from t_user where loginName = '"+loginName+"' and loginPwd = '"+loginPwd+"'";
               // 以上正好完成了SQL语句的拼接，以下代码的含义是，发送sql语句给DBMS，DBMS进行sql编译
               // 正好将用户提供的"非法信息"编译进去，导致原sql语句的含义被扭曲了
               rs = stmt.executeQuery(sql);
               // 5. 处理结果集
               if(rs.next()){
                   //登陆成功
                   loginSuccess = true;
               }
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               // 6. 释放资源
               if(rs != null){
                   try{
                       rs.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
               if(stmt != null){
                   try{
                       stmt.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
               if(conn != null){
                   try{
                       conn.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
           }
   
           return loginSuccess;
       }
   
       /**
        * 初始化用户界面
        * @return 用户输入的用户名和密码等登陆信息
        */
       private static Map<String, String> initUI() {
           Scanner s = new Scanner(System.in);
           System.out.print("用户名：");
           String username = s.nextLine();
   
           System.out.print("密码：");
           String password = s.nextLine();
   
           Map<String, String> userLoginInfo = new HashMap<>();
           userLoginInfo.put("loginName", username);
           userLoginInfo.put("loginPwd", password);
   
           return userLoginInfo;
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.*;
   import java.util.HashMap;
   import java.util.Map;
   import java.util.Scanner;
   
   /**
    * 1. 解决SQL注入的问题
    *    只要用户提供的信息不参与SQL语句的编译过程，问题就解决了
    *    即使用户提供的信息中含有SQL语句的关键字，但是没有参与编译，不起作用
    *    要真想用户信息不参与SQL语句的编译，那么必须使用java.sql.PreparedStatement
    *    PreparedStatement接口继承了java.sql.Statement
    *    PreparedStatement是属于预编译的数据库操作对象
    *    PreparedStatement的原理是：预先对SQL语句的框架进行编译，然后再给SQL语句传“值”。
    * 2. 用户名：fdas
    *    密码：fdsa' or '1'='1
    *    登陆失败
    * 3. 解决SQL注入的关键是什么？
    *    用户提供的信息中即使含有sql语句的关键字，但是这些关键字并没有参与编译，不起作用
    * 4. 对比一下Statement和PreparedStatement?
    *    - Statement存在sql注入问题，PreparedStatement解决了SQL注入问题
    *    - Statement是编译一次执行一次，PreparedStatement是编译一次，可执行N次。PreparedStatement效率较高一些。
    *    - PreparedStatement会在编译阶段做类型的安全检查。
    *
    *    综上所述，PreparedStatement使用较多，只有极少数的情况下需要使用Statement
    * 5. 什么情况下必须使用Statement呢？
    *    业务方面要求必须支持SQL注入的时候。
    *    Statement支持SQL注入，凡是业务方面要求是需要进行sql语句拼接的，必须使用Statement。比如购物商城，点按照价格升序排或是降序排，就需要sql语句拼接。
    */
   public class JDBCTest07 {
       public static void main(String[] args) {
           // 初始化一个界面
           Map<String, String> userLoginInfo = initUI();
           //验证用户名和密码
           boolean loginSuccess = login(userLoginInfo);
           //最后输出结果
           System.out.println(loginSuccess ? "登陆成功":"登陆失败");
       }
   
       /**
        *
        * @param userLoginInfo 用户登陆信息
        * @return false表示失败,true表示成功
        *
        */
       private static boolean login(Map<String, String> userLoginInfo) {
           //打标记的意识
           boolean loginSuccess = false;
           //单独定义变量
           String loginName = userLoginInfo.get("loginName");
           String loginPwd = userLoginInfo.get("loginPwd");
   
           // JDBC代码
           Connection conn = null;
           PreparedStatement ps = null; //这里使用PreparedStatement(预编译的数据库操作对象)
           ResultSet rs = null;
   
           try {
               // 1. 注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               // 2. 获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               // 3. 获取预编译的数据库操作对象
               // SQL语句的框子，其中一个？表示一个占位符，一个？将来接收一个"值"，注意，占位符不能使用单引号括起来
               String sql = "select * from t_user where loginName = ? and loginPwd = ?";
               //程序执行到此处，会发送sql语句框子给DBMS，然后DBMS进行sql语句的预先编译
               ps = conn.prepareStatement(sql);
               //给占位符？传值(第1个？下标是1，第2个？下标是2，JDBC中所有下标从1开始)
               ps.setString(1, loginName);
               ps.setString(2, loginPwd);
               // 4. 执行sql
               rs = ps.executeQuery();
               // 5. 处理结果集
               if(rs.next()){
                   //登陆成功
                   loginSuccess = true;
               }
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               // 6. 释放资源
               if(rs != null){
                   try{
                       rs.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
               if(ps != null){
                   try{
                       ps.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
               if(conn != null){
                   try{
                       conn.close();
                   }catch (SQLException e){
                       e.printStackTrace();
                   }
               }
           }
   
           return loginSuccess;
       }
   
       /**
        * 初始化用户界面
        * @return 用户输入的用户名和密码等登陆信息
        */
       private static Map<String, String> initUI() {
           Scanner s = new Scanner(System.in);
           System.out.print("用户名：");
           String username = s.nextLine();
   
           System.out.print("密码：");
           String password = s.nextLine();
   
           Map<String, String> userLoginInfo = new HashMap<>();
           userLoginInfo.put("loginName", username);
           userLoginInfo.put("loginPwd", password);
   
           return userLoginInfo;
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.*;
   import java.util.Scanner;
   
   public class JDBCTest08 {
       public static void main(String[] args) {
           /*
           //用户在控制台输入desc就是降序，输入asc就是升序
           Scanner s = new Scanner(System.in);
           System.out.println("请输入desc或asc, desc表示降序，asc表示升序");
           System.out.print("请输入：");
           String keyWords = s.nextLine();
   
           //执行SQL
           Connection conn = null;
           PreparedStatement ps = null;
           ResultSet rs = null;
           try {
               //注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               //获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               //获取预编译的数据库操作对象
               String sql = "select ename from emp order by ename ?";
               ps = conn.prepareStatement(sql);
               ps.setString(1, keyWords);
               //执行SQL
               rs = ps.executeQuery();
               //遍历结果集
               while(rs.next()){
                   System.out.println(rs.getString("ename"));
               }
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               if(rs != null){
                   try{
                       rs.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               if(ps != null){
                   try{
                       ps.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               if(conn != null){
                   try{
                       conn.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
   
            */
           //用户在控制台输入desc就是降序，输入asc就是升序
           Scanner s = new Scanner(System.in);
           System.out.println("请输入desc或asc, desc表示降序，asc表示升序");
           System.out.print("请输入：");
           String keyWords = s.nextLine();
   
           //执行SQL
           Connection conn = null;
           Statement stmt = null;
           ResultSet rs = null;
           try {
               //注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               //获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               //获取数据库操作对象
               stmt = conn.createStatement();
               //执行SQL
               String sql = "select ename from emp order by ename " + keyWords;
               rs = stmt.executeQuery(sql);
   
               //遍历结果集
               while(rs.next()){
                   System.out.println(rs.getString("ename"));
               }
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               if(rs != null){
                   try{
                       rs.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               if(stmt != null){
                   try{
                       stmt.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               if(conn != null){
                   try{
                       conn.close();
                   }catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
           }
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.Connection;
   import java.sql.DriverManager;
   import java.sql.PreparedStatement;
   import java.sql.SQLException;
   
   /**
    * PreparedStatement完成INSERT DELETE UPDATE
    */
   public class JDBCTest09 {
       public static void main(String[] args) {
   
           Connection conn = null;
           PreparedStatement ps = null;
           try {
               //1. 注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               //2. 获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               //3. 获取预编译的数据库操作对象
               /*String sql = "insert into dept(deptno, dname, loc) values(?,?,?)";
               ps = conn.prepareStatement(sql);
               ps.setInt(1, 60);
               ps.setString(2, "销售部");
               ps.setString(3, "上海");*/
   
               /*String sql = "update dept set dname = ?, loc = ? where deptno = ?";
               ps = conn.prepareStatement(sql);
               ps.setString(1, "研发一部");
               ps.setString(2, "北京");
               ps.setInt(3, 60);*/
   
               String sql = "delete from dept where deptno = ?";
   
               ps = conn.prepareStatement(sql);
               ps.setInt(1, 60);
   
               //4. 执行SQL
               int count = ps.executeUpdate();
               System.out.println(count);
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               if (ps != null){
                   try{
   
                       ps.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
               if (conn != null){
                   try{
                       conn.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
           }
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.Connection;
   import java.sql.DriverManager;
   import java.sql.PreparedStatement;
   import java.sql.SQLException;
   
   /**
    * JDBC事务机制：
    *      1. JDBC中的事务是自动提交的，什么是自动提交？
    *          只要执行任意一条DML语句，则自动提交一次，这是JDBC默认的事物行为
    *          但是在实际的业务开发中，通常都是N条DML语句共同联合才能完成的，必须保证他们这些DML语句在同一个事务中同时成功或同时失败。
    *      2. 以下程序先来验证一下JDBC的事务是否是自动提交机制。
    */
   public class JDBCTest10 {
       public static void main(String[] args) {
           Connection conn = null;
           PreparedStatement ps = null;
           try {
               //1. 注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               //2. 获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               //3. 获取预编译的数据库操作对象
               String sql = "update dept set dname = ? where deptno = ?";
               //第一次给占位符传值
               ps = conn.prepareStatement(sql);
               ps.setString(1, "X部门");
               ps.setInt(2, 30);
               int count = ps.executeUpdate(); //执行第一条UPDATE语句
               System.out.println(count);
   
               //重新给占位符传值
               ps = conn.prepareStatement(sql);
               ps.setString(1, "Y部门");
               ps.setInt(2, 20);//执行第二条UPDATE语句
               count = ps.executeUpdate();
               System.out.println(count);
   
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               if (ps != null){
                   try{
   
                       ps.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
               if (conn != null){
                   try{
                       conn.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
           }
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc;
   
   import java.sql.Connection;
   import java.sql.DriverManager;
   import java.sql.PreparedStatement;
   import java.sql.SQLException;
   
   /**
    * 账务转账演示事务
    * sql脚本：
    *    drop table if exists t_act;
    *    create table t_act(
    *         actno bigint,
    *         balance double(7,2)   //7表示有效数字的个数，2表示小数位的个数
    *    );
    *    insert into t_act(actno, balance) values(111,20000);
    *    insert into t_act(actno, balance) values(222,0);
    *    commit;
    *    select * from t_act;
    *
    *    重点三行代码：
    *        conn.setAutoCommit(false);
    *        conn.commit();
    *        conn.rollback();
    *
    */
   public class JDBCTest11 {
       public static void main(String[] args) throws SQLException {
           Connection conn = null;
           PreparedStatement ps = null;
           try {
               //1. 注册驱动
               Class.forName("com.mysql.cj.jdbc.Driver");
               //2. 获取连接
               conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
               // 将自动提交机制修改为手动提交机制
               conn.setAutoCommit(false); //开启事务
               //3. 获取预编译的数据库操作对象
               String sql = "update t_act set balance = ? where actno = ?";
               ps = conn.prepareStatement(sql);
   
               //给？传值
               ps.setDouble(1, 10000);
               ps.setInt(2, 111);
               int count = ps.executeUpdate();
   
   //            String s = null;
   //            s.toString();
   
               //给？传值
               ps.setDouble(1, 10000);
               ps.setInt(2, 222);
               count += ps.executeUpdate();
   
               System.out.println(count == 2 ? "转账成功":"转账失败");
               //程序能够走到这里说明以上程序没有异常，事务结束，手动提交数据
               conn.commit(); //提交事务
   
           } catch (Exception e) {
               //回滚事务
               if(conn != null){
                   conn.rollback();
               }
               e.printStackTrace();
           } finally {
               if (ps != null){
                   try{
   
                       ps.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
               if (conn != null){
                   try{
                       conn.close();
                   }catch(SQLException e){
                       e.printStackTrace();
                   }
               }
           }
   
       }
   }
   
   ```

   ```java
   package com.bjpowernode.jdbc.utils;
   
   import java.sql.*;
   
   /**
    * JDBC工具类，简化JDBC编程
    */
   public class DBUtil {
       /**
        * 工具类中的构造方法都是私有的
        * 因为工具类当中的方法都是静态的，不需要new对象，直接采用类名调用
        *
        */
       private DBUtil(){}
   
       //静态代码块在类加载时执行，并且只执行一次
       static {
           try {
               Class.forName("com.mysql.cj.jdbc.Driver");
           } catch (ClassNotFoundException e) {
               e.printStackTrace();
           }
       }
   
       /**
        * 获取数据库连接对象
        *
        * @return 连接对象
        * @throws SQLException
        */
       public static Connection getConnection() throws SQLException {
           return DriverManager.getConnection("jdbc:mysql://localhost:3306/bjpowernode", "root", "wqjsmile111");
       }
   
       /**
        * 关闭资源
        * @param conn 连接对象
        * @param ps 数据库操作对象
        * @param rs 结果集
        */
       public static void close(Connection conn, Statement ps, ResultSet rs) {
           if(rs != null){
               try{
                   rs.close();
               }catch (SQLException e){
                   e.printStackTrace();
               }
           }
           if(ps != null){
               try{
                   ps.close();
               }catch (SQLException e){
                   e.printStackTrace();
               }
           }
           if(conn != null){
               try{
                   conn.close();
               }catch (SQLException e){
                   e.printStackTrace();
               }
           }
       }
   }
   --------------------------------------------------------------------------------
   package com.bjpowernode.jdbc;
   
   import com.bjpowernode.jdbc.utils.DBUtil;
   
   import java.sql.Connection;
   import java.sql.PreparedStatement;
   import java.sql.ResultSet;
   import java.sql.SQLException;
   
   /**
    * 这个程序有两个任务：
    *      1.测试DBUtil是否好用
    *      2.模糊查询怎么写？
    */
   public class JDBCTest12 {
       public static void main(String[] args) {
           Connection conn = null;
           PreparedStatement ps = null;
           ResultSet rs = null;
   
           try {
               // 1. 注册驱动 and 2. 获取连接
               conn = DBUtil.getConnection();
   
               // 3. 获取预编译的数据库操作对象
               String sql = "select ename from emp where ename like ?";
               ps = conn.prepareStatement(sql);
               ps.setString(1, "_A%");
   
               rs = ps.executeQuery();
               while(rs.next()){
                   System.out.println(rs.getString("ename"));
               }
   
   
           } catch (Exception e) {
               e.printStackTrace();
           } finally {
               //释放资源
               DBUtil.close(conn, ps, rs);
           }
       }
   }
   结果：
   WARD
   MARTIN
   JAMES
   ```

6.  悲观锁和乐观锁

   ![image-20210524214623651](https://i.loli.net/2021/05/24/hRmSPXcyoKdsJ75.png)

   ```java
   package com.bjpowernode.jdbc;
   
   import com.bjpowernode.jdbc.utils.DBUtil;
   
   import java.sql.Connection;
   import java.sql.PreparedStatement;
   import java.sql.ResultSet;
   import java.sql.SQLException;
   
   /**
    * 这个程序开启一个事务，这个事务专门进行查询，并且使用行级锁
    */
   public class JDBCTest13 {
       public static void main(String[] args) {
           Connection conn = null;
           PreparedStatement ps = null;
           ResultSet rs = null;
           try {
               conn = DBUtil.getConnection();
               //开启事务
               conn.setAutoCommit(false);
   
               String sql = "select ename, job, sal from emp where job = ? for update";
               ps = conn.prepareStatement(sql);
               ps.setString(1, "MANAGER");
   
               rs = ps.executeQuery();
               while(rs.next()){
                   System.out.println(rs.getString("ename") + "," + rs.getString("job") + "," +
                           rs.getDouble("sal"));
               }
   
   
               //提交事务(事务结束)
               conn.commit();
   
   
   
           } catch (SQLException throwables) {
               if(conn != null){
                   try {
                       conn.rollback();
                   } catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               throwables.printStackTrace();
           } finally {
               DBUtil.close(conn, ps, rs);
           }
       }
   }
   ----------------------------------------------------------------------------------
   package com.bjpowernode.jdbc;
   
   import com.bjpowernode.jdbc.utils.DBUtil;
   
   import java.sql.Connection;
   import java.sql.PreparedStatement;
   import java.sql.ResultSet;
   import java.sql.SQLException;
   
   /**
    * 这个程序负责修改被锁定的记录
    */
   public class JDBCTest14 {
       public static void main(String[] args) {
           Connection conn = null;
           PreparedStatement ps = null;
   
           try {
               conn = DBUtil.getConnection();
               conn.setAutoCommit(false);
   
               String sql = "update emp set sal = sal * 1.1 where job = ?";
               ps = conn.prepareStatement(sql);
               ps.setString(1, "MANAGER");
               int count = ps.executeUpdate();
               System.out.println(count);
   
   
               conn.commit();
           } catch (SQLException throwables) {
               if(conn != null){
                   try {
                       conn.rollback();
                   } catch (SQLException e) {
                       e.printStackTrace();
                   }
               }
               throwables.printStackTrace();
           } finally {
               DBUtil.close(conn, ps, null);
           }
       }
   }
   
   ```

   