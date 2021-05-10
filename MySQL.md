常见数据库管理系统：

​		Oracle 甲骨文(收购了SUN)、MySQL、DB2、Sybase、"MS SqlServer支持标准sql的数据库管理系统"。银行等传统公司多用Oracle，互联网公司多用MySQL。

1. sql、DB、DBMS分别是什么，他们之间的关系？

   DB：DataBase(数据库，数据库实际上在硬盘上以文件的形式存在)

   DBMS：DataBase Management System(数据库管理系统，常见的：MySQL Oracle DB2 Sybase SqlServer)

   SQL：结构化查询语言，是一门标准通用的语言。标准的sql适合于所有的数据库产品。

   ​			SQL属于高级语言，只要能看懂英语单词的，写出来的sql语句，可以读懂什么意思。

   ​			SQL语句在执行的时候，实际上内容也会先进行编译，然后再执行sql。(sql语句的编译由DBMS完成)。

   DBMS负责执行sql语句，通过执行sql语句来操作DB当中的数据。

   DBMS-(执行)-> SQL -(操作)  -> DB

2. 什么是表table？

   table是数据库的基本组成单元，所有的数据都以表格的形式组织，目的是可读性强。

   一个表包括行和列：

   ​	行：被称为数据/记录(data)

   ​	列：被称为字段(column)

   | 学号(int) | 姓名(varchar) | 年龄 |
   | :-------: | :-----------: | :--: |
   |    110    |     张三      |  20  |
   |    120    |     李四      |  21  |

   每一个字段应该包括哪些属性？

   ​	字段名、数据类型、相关的约束。

3. SQL语句分类：

   DQL(数据查询语言)：查询语句，凡是select语句都是DQL

   DML(数据操作语言)：insert delete update,对表当中的数据进行增删改

   DDL(数据定义语言)：create drop alter,对表结构的增删改

   TCL(事务控制语言)：commit提交事务，rollback回滚事务。

   DCL(数据控制语言)：grant授权、revoke撤销权限等。

4. 导入数据

   第一步：登陆mysql数据库管理系统

   第二步：查看有哪些数据库

   ```mysql
   show databases;(这个不是SQL语句，属于MySQL的命令)
   
   +--------------------+
   | Database           |
   +--------------------+
   | information_schema |
   | mysql              |
   | performance_schema |
   | sakila             |
   | sys                |
   | world              |
   +--------------------+
   ```

   第三步：创建属于我们自己的数据库

   ```mysql
   create database bjpowernode;(这个不是SQL语句，属于MySQL的命令)
   ```

   第四步：使用bjpowernode数据

   ```java
   use bjpowernode;(这个不是SQL语句，属于MySQL的命令)
   ```

   第五步：查看当前使用的数据库中有那些表？

   ```java
   show tables;(这个不是SQL语句，属于MySQL的命令)
   ```

   第六步：初始化数据

   ```mysql
   mysql> source C:\Users\Administrator\Desktop\bjpowernode\bjpowernode.sql
   ```

5. bjpowernode.sql,这个文件以sql结尾，这样的文件被称为"sql脚本"。什么是sql脚本呢？当一个文件的扩展名为.sql，并且该文件中编写了大量的sql语句，我们称这样的文件为sql脚本。

   注意：直接使用source命令可以执行sql脚本。

   sql脚本中的数据量太大的时候，无法打开，请使用source命令完成初始化。

6. 删除数据库：drop database bjpowernode;

7. 查看表结构：

   ```mysql
   show tables;
   
   +-----------------------+
   | Tables_in_bjpowernode |
   +-----------------------+
   | dept                  | 部门表
   | emp                   | 员工表
   | salgrade              | 工资等级表
   +-----------------------+
       
   desc dept;
   +--------+-------------+------+-----+---------+-------+
   | Field  | Type        | Null | Key | Default | Extra |
   +--------+-------------+------+-----+---------+-------+
   | DEPTNO | int         | NO   | PRI | NULL    |       |部门编号
   | DNAME  | varchar(14) | YES  |     | NULL    |       |部门名称
   | LOC    | varchar(13) | YES  |     | NULL    |       |部门位置
   +--------+-------------+------+-----+---------+-------+
   
   desc emp;
   +----------+-------------+------+-----+---------+-------+
   | Field    | Type        | Null | Key | Default | Extra |
   +----------+-------------+------+-----+---------+-------+
   | EMPNO    | int         | NO   | PRI | NULL    |       |员工编号
   | ENAME    | varchar(10) | YES  |     | NULL    |       |员工姓名
   | JOB      | varchar(9)  | YES  |     | NULL    |       |工作岗位
   | MGR      | int         | YES  |     | NULL    |       |上级领导编号
   | HIREDATE | date        | YES  |     | NULL    |       |入职日期
   | SAL      | double(7,2) | YES  |     | NULL    |       |月薪
   | COMM     | double(7,2) | YES  |     | NULL    |       |补助/津贴
   | DEPTNO   | int         | YES  |     | NULL    |       |部门编号
   +----------+-------------+------+-----+---------+-------+
   
   desc salgrade;
   +-------+------+------+-----+---------+-------+
   | Field | Type | Null | Key | Default | Extra |
   +-------+------+------+-----+---------+-------+
   | GRADE | int  | YES  |     | NULL    |       |等级
   | LOSAL | int  | YES  |     | NULL    |       |最低薪资
   | HISAL | int  | YES  |     | NULL    |       |最高薪资
   +-------+------+------+-----+---------+-------+
   ```

8. 表中的数据？

   ```mysql
   mysql> select * from emp;
   
   +-------+--------+-----------+------+------------+---------+---------+--------+
   | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
   |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
   |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
   |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
   |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
   |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
   |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
   |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
   |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
   |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
   |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
   |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
   |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
   |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   
   mysql> select * from dept;
   +--------+------------+----------+
   | DEPTNO | DNAME      | LOC      |
   +--------+------------+----------+
   |     10 | ACCOUNTING | NEW YORK |
   |     20 | RESEARCH   | DALLAS   |
   |     30 | SALES      | CHICAGO  |
   |     40 | OPERATIONS | BOSTON   |
   +--------+------------+----------+
   
   mysql> select * from salgrade;
   +-------+-------+-------+
   | GRADE | LOSAL | HISAL |
   +-------+-------+-------+
   |     1 |   700 |  1200 |
   |     2 |  1201 |  1400 |
   |     3 |  1401 |  2000 |
   |     4 |  2001 |  3000 |
   |     5 |  3001 |  9999 |
   +-------+-------+-------+
   ```

9. 常用命令？

   ```java
   mysql> select database(); 查看当前使用的是哪个数据库
   +-------------+
   | database()  |
   +-------------+
   | bjpowernode |
   +-------------+
   
   mysql> select version();查看mysql的版本号
   +-----------+
   | version() |
   +-----------+
   | 8.0.23    |
   +-----------+
       
   \c 命令，结束一条语句。   
   exit命令，退出mysql。
   
   查看创建表的语句：
   show create table emp;
   ```

------

一、 单表查询

10. 简单的查询语句(DQL)

    语法格式：

    ```mysql
    select 字段名1,字段名2,字段名3,... from 表名;
    ```

    提示：

    	1. 任何一条sql语句以";"结尾。
    	2. sql语句不区分大小写。

    查询员工的年薪？（字段可以参与数学运算。）

    ```mysql
    Select ename, sal * 12 from emp;
    
    +--------+----------+
    | ename  | sal *12  |
    +--------+----------+
    | SMITH  |  9600.00 |
    | ALLEN  | 19200.00 |
    | WARD   | 15000.00 |
    | JONES  | 35700.00 |
    | MARTIN | 15000.00 |
    | BLAKE  | 34200.00 |
    | CLARK  | 29400.00 |
    | SCOTT  | 36000.00 |
    | KING   | 60000.00 |
    | TURNER | 18000.00 |
    | ADAMS  | 13200.00 |
    | JAMES  | 11400.00 |
    | FORD   | 36000.00 |
    | MILLER | 15600.00 |
    +--------+----------+
    ```

    给查询结果的列重命名？

    ```mysql
    select ename,sal*12 as yearsal from emp;
    
    +--------+----------+
    | ename  | yearsal  |
    +--------+----------+
    | SMITH  |  9600.00 |
    | ALLEN  | 19200.00 |
    | WARD   | 15000.00 |
    | JONES  | 35700.00 |
    | MARTIN | 15000.00 |
    | BLAKE  | 34200.00 |
    | CLARK  | 29400.00 |
    | SCOTT  | 36000.00 |
    | KING   | 60000.00 |
    | TURNER | 18000.00 |
    | ADAMS  | 13200.00 |
    | JAMES  | 11400.00 |
    | FORD   | 36000.00 |
    | MILLER | 15600.00 |
    +--------+----------+
    ```

    别名中有中文？

    ```mysql
    select ename, sal*12 as 年薪 from emp;//旧版本不行，新版本行
    select ename, sal*12 as '年薪' from emp;
    select ename, sal*12 '年薪' from emp;//as关键字可以省略
    
    ```

    注意：标准sql语句中要求字符串使用单引号括起来，虽然mysql支持双引号，尽量别用。

11. 条件查询

    语法格式：

    ```mysql
    select 字段,字段... from 表名 where 条件;
    ```

    执行顺序：先from，然后where，最后select

    查询工资等于5000的员工姓名？

    ```mysql
    select ename from emp where sal = 5000;
    
    +-------+
    | ename |
    +-------+
    | KING  |
    +-------+
    ```

    查询SMITH的工资？

    ```mysql
    select sal from emp where ename = 'SMITH';
    
    +--------+
    | sal    |
    +--------+
    | 800.00 |
    +--------+
    ```

    找出工资高于3000的员工？

    ```mysql
    select ename, sal from emp where sal > 3000;
    
    +-------+---------+
    | ename | sal     |
    +-------+---------+
    | KING  | 5000.00 |
    +-------+---------+
    ```

    找出工资不等于3000的员工？

    ```mysql
    select ename, sal from emp where sal <> 3000;
    select ename, sal from emp where sal != 3000;
    
    +--------+---------+
    | ename  | sal     |
    +--------+---------+
    | SMITH  |  800.00 |
    | ALLEN  | 1600.00 |
    | WARD   | 1250.00 |
    | JONES  | 2975.00 |
    | MARTIN | 1250.00 |
    | BLAKE  | 2850.00 |
    | CLARK  | 2450.00 |
    | KING   | 5000.00 |
    | TURNER | 1500.00 |
    | ADAMS  | 1100.00 |
    | JAMES  |  950.00 |
    | MILLER | 1300.00 |
    +--------+---------+
    ```

    找出工资在1100和3000之间的员工，包括1100和3000？

    ```mysql
    select ename, sal from emp where sal >= 1100 and sal <= 3000;
    select ename, sal from emp where sal >= 1100 && sal <= 3000;
    select ename, sal from emp where sal between 1100 and 3000;【1100,3000】左小右大，应用在数字时闭区间，应用在字符串时左闭右开
    select ename, sal from emp where sal between 3000 and 1100;//查询不到任何数据 【3000,1100】
    +--------+---------+
    | ename  | sal     |
    +--------+---------+
    | ALLEN  | 1600.00 |
    | WARD   | 1250.00 |
    | JONES  | 2975.00 |
    | MARTIN | 1250.00 |
    | BLAKE  | 2850.00 |
    | CLARK  | 2450.00 |
    | SCOTT  | 3000.00 |
    | TURNER | 1500.00 |
    | ADAMS  | 1100.00 |
    | FORD   | 3000.00 |
    | MILLER | 1300.00 |
    +--------+---------+
    ```

    找出哪些人没有津贴？

    ```mysql
    select ename, sal, comm from emp where comm is null;
    空不是一个值，不能用等号衡量。
    
    +--------+---------+------+
    | ename  | sal     | comm |
    +--------+---------+------+
    | SMITH  |  800.00 | NULL |
    | JONES  | 2975.00 | NULL |
    | BLAKE  | 2850.00 | NULL |
    | CLARK  | 2450.00 | NULL |
    | SCOTT  | 3000.00 | NULL |
    | KING   | 5000.00 | NULL |
    | ADAMS  | 1100.00 | NULL |
    | JAMES  |  950.00 | NULL |
    | FORD   | 3000.00 | NULL |
    | MILLER | 1300.00 | NULL |
    +--------+---------+------+
    ```

    找出哪些人津贴不为NULL？

    ```mysql
    select ename, sal, comm from emp where comm is not null;
    
    +--------+---------+---------+
    | ename  | sal     | comm    |
    +--------+---------+---------+
    | ALLEN  | 1600.00 |  300.00 |
    | WARD   | 1250.00 |  500.00 |
    | MARTIN | 1250.00 | 1400.00 |
    | TURNER | 1500.00 |    0.00 |
    +--------+---------+---------+
    
    select ename, sal, comm from emp where comm is null or comm=0;
    
    +--------+---------+------+
    | ename  | sal     | comm |
    +--------+---------+------+
    | SMITH  |  800.00 | NULL |
    | JONES  | 2975.00 | NULL |
    | BLAKE  | 2850.00 | NULL |
    | CLARK  | 2450.00 | NULL |
    | SCOTT  | 3000.00 | NULL |
    | KING   | 5000.00 | NULL |
    | TURNER | 1500.00 | 0.00 |
    | ADAMS  | 1100.00 | NULL |
    | JAMES  |  950.00 | NULL |
    | FORD   | 3000.00 | NULL |
    | MILLER | 1300.00 | NULL |
    +--------+---------+------+
    ```

    找出工作岗位是MANAGER和SALESMAN的员工？

    ```mysql
    select ename,job from emp where job = 'MANAGER' or job = 'SALESMAN';
    
    +--------+----------+
    | ename  | job      |
    +--------+----------+
    | ALLEN  | SALESMAN |
    | WARD   | SALESMAN |
    | JONES  | MANAGER  |
    | MARTIN | SALESMAN |
    | BLAKE  | MANAGER  |
    | CLARK  | MANAGER  |
    | TURNER | SALESMAN |
    +--------+----------+
    ```

    and 和 or 联合使用：找出薪资大于1000的并且部门编号是20或30部门的员工

    ```java
    select ename, sal, deptno from emp where sal >1000 and (deptno =20 or deptno = 30);
    注意：当运算符的优先级不确定的时候加小括号。
    
    +--------+---------+--------+
    | ename  | sal     | deptno |
    +--------+---------+--------+
    | ALLEN  | 1600.00 |     30 |
    | WARD   | 1250.00 |     30 |
    | JONES  | 2975.00 |     20 |
    | MARTIN | 1250.00 |     30 |
    | BLAKE  | 2850.00 |     30 |
    | SCOTT  | 3000.00 |     20 |
    | TURNER | 1500.00 |     30 |
    | ADAMS  | 1100.00 |     20 |
    | FORD   | 3000.00 |     20 |
    +--------+---------+--------+
    ```

    in等同于or：找出工作岗位是MANAGER和SALESMAN的员工？

    ```mysql
    select ename,job from emp where job = 'SALESMAN' or job = 'MANAGER';
    select ename,job from emp where job in('SALESMAN', 'MANAGER');
    
    +--------+----------+
    | ename  | job      |
    +--------+----------+
    | ALLEN  | SALESMAN |
    | WARD   | SALESMAN |
    | JONES  | MANAGER  |
    | MARTIN | SALESMAN |
    | BLAKE  | MANAGER  |
    | CLARK  | MANAGER  |
    | TURNER | SALESMAN |
    +--------+----------+
    
    select ename,job,sal from emp where sal in(1000, 5000); //in后面的值不是区间，是具体的值
    
    +-------+-----------+---------+
    | ename | job       | sal     |
    +-------+-----------+---------+
    | KING  | PRESIDENT | 5000.00 |
    +-------+-----------+---------+
    
    not in: 不在这几个值当中
    select ename,job,sal from emp where sal not in(800, 5000);
    
    +--------+----------+---------+
    | ename  | job      | sal     |
    +--------+----------+---------+
    | ALLEN  | SALESMAN | 1600.00 |
    | WARD   | SALESMAN | 1250.00 |
    | JONES  | MANAGER  | 2975.00 |
    | MARTIN | SALESMAN | 1250.00 |
    | BLAKE  | MANAGER  | 2850.00 |
    | CLARK  | MANAGER  | 2450.00 |
    | SCOTT  | ANALYST  | 3000.00 |
    | TURNER | SALESMAN | 1500.00 |
    | ADAMS  | CLERK    | 1100.00 |
    | JAMES  | CLERK    |  950.00 |
    | FORD   | ANALYST  | 3000.00 |
    | MILLER | CLERK    | 1300.00 |
    +--------+----------+---------+
    ```

    模糊查询like？

    （在模糊查询中，必须掌握两个特殊的符号，一个是%，一个是_）

    %代表任意多个字符，_代表任意一个字符。

    

    找出名字当中含有o的？

    ```mysql
    select ename from emp where ename like '%O%';
    
    +-------+
    | ename |
    +-------+
    | JONES |
    | SCOTT |
    | FORD  |
    +-------+
    ```

    找出名字中第二个字母是A的？

    ```mysql
    select ename from emp where ename like '_A%';
    
    +--------+
    | ename  |
    +--------+
    | WARD   |
    | MARTIN |
    | JAMES  |
    +--------+
    ```

    找出名字中有下划线的？

    ```mysql
    select * from t_user;
    +------+----------+
    | id   | name     |
    +------+----------+
    |    1 | zhangsan |
    |    2 | lisi     |
    |    3 | WANG_WU  |
    +------+----------+
    
    select name from t_user where name like '%\_%';
    +---------+
    | name    |
    +---------+
    | WANG_WU |
    +---------+
    
    ```

    找出名字中最后一个字母是T的？

    ```mysql
    select ename from emp where ename like '%T';
    
    +-------+
    | ename |
    +-------+
    | SCOTT |
    +-------+
    ```

12. 排序(升序、降序)

    按照工资升序，找出 员工名和薪资？

    ```mysql
    select ename,sal from emp order by sal;(默认升序)
    select ename,sal from emp order by sal asc;(升序)
    select ename,sal from emp order by sal desc;(降序)
    +--------+---------+
    | ename  | sal     |
    +--------+---------+
    | SMITH  |  800.00 |
    | JAMES  |  950.00 |
    | ADAMS  | 1100.00 |
    | WARD   | 1250.00 |
    | MARTIN | 1250.00 |
    | MILLER | 1300.00 |
    | TURNER | 1500.00 |
    | ALLEN  | 1600.00 |
    | CLARK  | 2450.00 |
    | BLAKE  | 2850.00 |
    | JONES  | 2975.00 |
    | SCOTT  | 3000.00 |
    | FORD   | 3000.00 |
    | KING   | 5000.00 |
    +--------+---------+
    ```

    按照工资的降序排，当工资相同时按照名字的升序排列

    ```mysql
    select ename,sal from emp order by sal desc, ename asc;
    注意：越靠前的字段越能起到主导作用
    +--------+---------+
    | ename  | sal     |
    +--------+---------+
    | KING   | 5000.00 |
    | FORD   | 3000.00 |
    | SCOTT  | 3000.00 |
    | JONES  | 2975.00 |
    | BLAKE  | 2850.00 |
    | CLARK  | 2450.00 |
    | ALLEN  | 1600.00 |
    | TURNER | 1500.00 |
    | MILLER | 1300.00 |
    | MARTIN | 1250.00 |
    | WARD   | 1250.00 |
    | ADAMS  | 1100.00 |
    | JAMES  |  950.00 |
    | SMITH  |  800.00 |
    +--------+---------+
    ```

    找出工作岗位是SALESMAN的员工，并且要求按照薪资的降序排列。

    ```mysql
    select ename, job, sal from emp where job = 'SALESMAN' order by sal desc;
    +--------+----------+---------+
    | ename  | job      | sal     |
    +--------+----------+---------+
    | ALLEN  | SALESMAN | 1600.00 |
    | TURNER | SALESMAN | 1500.00 |
    | WARD   | SALESMAN | 1250.00 |
    | MARTIN | SALESMAN | 1250.00 |
    +--------+----------+---------+
    ```

13. 分组函数

    count 计数

    sum 求和

    avg 平均值

    max 最大值

    min 最小值

    所有的分组函数都是对"某一组"数据进行操作的。分组函数还有另一个名字：多行处理函数【自动忽略NULL】，多行处理函数的特点：输入多行，最终输出的结果是1行。

    ```mysql
    找出工资总和？
    select sum(sal) from emp;
    +----------+
    | sum(sal) |
    +----------+
    | 29025.00 |
    +----------+
    
    找出最高工资？
    select max(sal) from emp;
    +----------+
    | max(sal) |
    +----------+
    |  5000.00 |
    +----------+
    
    找出最低工资？
    select min(sal) from emp;
    +----------+
    | min(sal) |
    +----------+
    |   800.00 |
    +----------+
    
    计算平均工资？
    select avg(sal) from emp;
    +-------------+
    | avg(sal)    |
    +-------------+
    | 2073.214286 |
    +-------------+
    找出总人数？
    select count(ename) from emp;
    select count(*) from emp;
    +--------------+
    | count(ename) |
    +--------------+
    |           14 |
    +--------------+
    ```

    **分组函数自动忽略NULL;**

    ```mysql
    select count(comm) from emp;
    +-------------+
    | count(comm) |
    +-------------+
    |           4 |
    +-------------+
    ```

    单行处理函数：输入一行，输出一行

    计算每个员工的年薪？

    ```mysql
    select ename, (sal+comm)*12 as yearsal from emp;
    +--------+----------+
    | ename  | yearsal  |
    +--------+----------+
    | SMITH  |     NULL |
    | ALLEN  | 22800.00 |
    | WARD   | 21000.00 |
    | JONES  |     NULL |
    | MARTIN | 31800.00 |
    | BLAKE  |     NULL |
    | CLARK  |     NULL |
    | SCOTT  |     NULL |
    | KING   |     NULL |
    | TURNER | 18000.00 |
    | ADAMS  |     NULL |
    | JAMES  |     NULL |
    | FORD   |     NULL |
    | MILLER |     NULL |
    +--------+----------+
    重点：所有数据库都是这样规定的，只要有NULL参与的运算结果一定是NULL。
    
    ifnull()空处理函数？
    	ifnull(可能为NULL的数据，被当做什么处理):属于单行处理函数
    select ename, ifnull(comm,0) from emp;
    +--------+----------------+
    | ename  | ifnull(comm,0) |
    +--------+----------------+
    | SMITH  |           0.00 |
    | ALLEN  |         300.00 |
    | WARD   |         500.00 |
    | JONES  |           0.00 |
    | MARTIN |        1400.00 |
    | BLAKE  |           0.00 |
    | CLARK  |           0.00 |
    | SCOTT  |           0.00 |
    | KING   |           0.00 |
    | TURNER |           0.00 |
    | ADAMS  |           0.00 |
    | JAMES  |           0.00 |
    | FORD   |           0.00 |
    | MILLER |           0.00 |
    +--------+----------------+
    
    select ename, (sal+ifnull(comm,0))*12 as yearsal from emp;
    +--------+----------+
    | ename  | yearsal  |
    +--------+----------+
    | SMITH  |  9600.00 |
    | ALLEN  | 22800.00 |
    | WARD   | 21000.00 |
    | JONES  | 35700.00 |
    | MARTIN | 31800.00 |
    | BLAKE  | 34200.00 |
    | CLARK  | 29400.00 |
    | SCOTT  | 36000.00 |
    | KING   | 60000.00 |
    | TURNER | 18000.00 |
    | ADAMS  | 13200.00 |
    | JAMES  | 11400.00 |
    | FORD   | 36000.00 |
    | MILLER | 15600.00 |
    +--------+----------+
    ```

    找出工资高于平均工资的员工？

    ```mysql
    select ename,sal from emp where sal > avg(sal); //ERROR 1111 (HY000): Invalid use of group function 无效使用分组函数，原因是SQL语句当中有一个语法规则,分组函数不可直接使用在WHERE子句当中。
    解释：因为group by是在where执行之后才会执行。
    执行顺序：
    select   5
    from     1
    where    2
    group by 3
    having   4
    order by 6
    
    正确的写法：
    select ename,sal from emp where sal > (select avg(sal) from emp);
    +-------+---------+
    | ename | sal     |
    +-------+---------+
    | JONES | 2975.00 |
    | BLAKE | 2850.00 |
    | CLARK | 2450.00 |
    | SCOTT | 3000.00 |
    | KING  | 5000.00 |
    | FORD  | 3000.00 |
    +-------+---------+
    ```

    ```mysql
    count(*)和count(具体的某个字段)，他们有什么区别？
    
    count(*):不是统计某个字段中数据的个数，而是统计总记录条数。(和某个字段无关)
    
    count(comm):表示统计comm字段中不为NULL的数据总数量。
    ```

    分组函数也能组合起来用：

    ```mysql
    select count(*), sum(sal), avg(sal), max(sal), min(sal) from emp;
    +----------+----------+-------------+----------+----------+
    | count(*) | sum(sal) | avg(sal)    | max(sal) | min(sal) |
    +----------+----------+-------------+----------+----------+
    |       14 | 29025.00 | 2073.214286 |  5000.00 |   800.00 |
    +----------+----------+-------------+----------+----------+
    ```

14. group by 和having

    group by:按照某个字段或者某些字段进行分组

    having：having是对分组之后的数据进行再次过滤

    案例：找出每个工作岗位的最高薪资。

    ```mysql
    select max(sal),job from emp group by job;
    注意：分组函数一般都会和group by联合使用，这也是为什么它被称为分组函数的原因。并且任何一个分组函数(count sum avg max min)都是在group by语句执行结束之后才会执行的。当一条sql语句没有group by的话，整张表的数据会自成一组。
    
    +----------+-----------+
    | max(sal) | job       |
    +----------+-----------+
    |  1300.00 | CLERK     |
    |  1600.00 | SALESMAN  |
    |  2975.00 | MANAGER   |
    |  3000.00 | ANALYST   |
    |  5000.00 | PRESIDENT |
    +----------+-----------+
    
    select ename,max(sal), job from emp group by job;
    以上在mysql中，查询结果是有的，但是没有意义，在Oracle数据库中会报错，语法错误。Oracle的语法规则比MySQL语法规则严谨
    注意：当一条语句中有group by的话，select后面只能跟分组函数和参与分组的字段。
    ```

    每个工作岗位的平均薪资

    ```mysql
    select avg(sal),job from emp group by job;
    
    +-------------+-----------+
    | avg(sal)    | job       |
    +-------------+-----------+
    | 1037.500000 | CLERK     |
    | 1400.000000 | SALESMAN  |
    | 2758.333333 | MANAGER   |
    | 3000.000000 | ANALYST   |
    | 5000.000000 | PRESIDENT |
    +-------------+-----------+
    ```

    多个字段能不能联合起来一块分组？

    找出每个部门不同工作岗位的最高薪资？

    ```mysql
    select deptno, job, max(sal) from emp group by deptno, job;
    +--------+-----------+----------+
    | deptno | job       | max(sal) |
    +--------+-----------+----------+
    |     20 | CLERK     |  1100.00 |
    |     30 | SALESMAN  |  1600.00 |
    |     20 | MANAGER   |  2975.00 |
    |     30 | MANAGER   |  2850.00 |
    |     10 | MANAGER   |  2450.00 |
    |     20 | ANALYST   |  3000.00 |
    |     10 | PRESIDENT |  5000.00 |
    |     30 | CLERK     |   950.00 |
    |     10 | CLERK     |  1300.00 |
    +--------+-----------+----------+
    ```

    找出每个部门的最高薪资，要求显示薪资大于2900的数据

    ```mysql
    select max(sal), deptno from emp where sal > 2900 group by deptno;(效率较高)
    select max(sal), deptno from emp group by deptno having max(sal) > 2900;(效率较低)
    +----------+--------+
    | max(sal) | deptno |
    +----------+--------+
    |  3000.00 |     20 |
    |  5000.00 |     10 |
    +----------+--------+
    ```

    找出每个部门的平均薪资,要求显示薪资大于2900的数据(无法使用where语句)

    ```mysql
    select avg(sal), deptno from emp group by deptno having avg(sal) > 2000;
    select avg(sal), deptno from emp where avg(sal) group by deptno; //错误 
    
    +-------------+--------+
    | avg(sal)    | deptno |
    +-------------+--------+
    | 2175.000000 |     20 |
    | 2916.666667 |     10 |
    +-------------+--------+
    ```

    > 总结：一个完整的DQL语句怎么写？
    >
    > select ..           5
    >
    > from ..             1
    >
    > where ..           2
    >
    > group by ..      3
    >
    > having ..          4
    >
    > order by ..       6

15. 关于查询结果集的去重？

    ```mysql
    select distinct job from emp;//distinct关键字去除重复记录。
    +-----------+
    | job       |
    +-----------+
    | CLERK     |
    | SALESMAN  |
    | MANAGER   |
    | ANALYST   |
    | PRESIDENT |
    +-----------+
    
    注意：distinct只能出现在所有字段的最前面,表示联合去重
    select distinct deptno,job from emp;
    +--------+-----------+
    | deptno | job       |
    +--------+-----------+
    |     20 | CLERK     |
    |     30 | SALESMAN  |
    |     20 | MANAGER   |
    |     30 | MANAGER   |
    |     10 | MANAGER   |
    |     20 | ANALYST   |
    |     10 | PRESIDENT |
    |     30 | CLERK     |
    |     10 | CLERK     |
    +--------+-----------+
    ```

    统计岗位的数量

    ```mysql
    select count(distinct job) from emp;
    +---------------------+
    | count(distinct job) |
    +---------------------+
    |                   5 |
    +---------------------+
    ```

    

------

二、连接查询

 1. 什么是连接查询？

    在实际开发中，大部分的情况下都不是从单表中查询数据，一般都是多张表联合查询取出最终的结果。在实际开发中，一般一个业务都会对应多张表，比如：学生和班级，起码两张表。

    | stuno | stuname | classno | classname |
    | ----- | ------- | ------- | --------- |
    | 1     | zs      | 1       | 高三1班   |
    | 2     | ls      | 1       | 高三1班   |

    学生和班级信息存储到一张表中，结果就像上面一样，数据会存在大量的重复，导致数据的冗余。

2. 连接查询的分类？

   根据语法出现的年代来划分的话，包括：

   ​		SQL92(一些老的DBA可能还在使用这种语法。DBA：DataBase Administrator，数据库管理员)

   ​		SQL99(比较新的语法)

   根据表的连接方式来划分，包括：

   ​		内连接：

   ​				等值连接

   ​				非等值连接

   ​				自连接

   ​		外连接：

   ​				左外连接(左连接)

   ​				右外连接(右连接)

   ​		全连接(很少用)

   

3.  在表的连接查询方面有一个现象被称为：笛卡尔积现象。

   案例：找出每一个员工的部门名称，要求显示员工名和部门名。

   ```mysql
   DEPT表
   +--------+------------+----------+
   | DEPTNO | DNAME      | LOC      |
   +--------+------------+----------+
   |     10 | ACCOUNTING | NEW YORK |
   |     20 | RESEARCH   | DALLAS   |
   |     30 | SALES      | CHICAGO  |
   |     40 | OPERATIONS | BOSTON   |
   +--------+------------+----------+
   
   EMP表
   +--------+--------+
   | ename  | deptno |
   +--------+--------+
   | SMITH  |     20 |
   | ALLEN  |     30 |
   | WARD   |     30 |
   | JONES  |     20 |
   | MARTIN |     30 |
   | BLAKE  |     30 |
   | CLARK  |     10 |
   | SCOTT  |     20 |
   | KING   |     10 |
   | TURNER |     30 |
   | ADAMS  |     20 |
   | JAMES  |     30 |
   | FORD   |     20 |
   | MILLER |     10 |
   +--------+--------+
   
   select ename, dname from emp, dept;
   +--------+------------+
   | ename  | dname      |
   +--------+------------+
   | SMITH  | OPERATIONS |
   | SMITH  | SALES      |
   | SMITH  | RESEARCH   |
   | SMITH  | ACCOUNTING |
   | ALLEN  | OPERATIONS |
   | ALLEN  | SALES      |
   | ALLEN  | RESEARCH   |
   | ALLEN  | ACCOUNTING |
   ........
   56 rows in set (0.00 sec)
   笛卡尔积现象：当两张表进行连接查询的时候，没有任何条件进行限制，最终的查询结果条数是两张表记录条数的乘积。
   
   关于表的别名：
   	select e.ename, d.dname from emp e, dept d;
   	表的别名有什么好处？
   		第一：执行效率高
   		第二：可读性好
   怎么避免笛卡尔积现象，加条件进行过滤。
   避免了笛卡尔积现象，会减少记录的匹配次数吗？不会，次数还是56次，只不过显示的是有效记录。
   
   
   select e.ename,d.dname from emp e, dept d where e.deptno = d.deptno;
   +--------+------------+
   | ename  | dname      |
   +--------+------------+
   | SMITH  | RESEARCH   |
   | ALLEN  | SALES      |
   | WARD   | SALES      |
   | JONES  | RESEARCH   |
   | MARTIN | SALES      |
   | BLAKE  | SALES      |
   | CLARK  | ACCOUNTING |
   | SCOTT  | RESEARCH   |
   | KING   | ACCOUNTING |
   | TURNER | SALES      |
   | ADAMS  | RESEARCH   |
   | JAMES  | SALES      |
   | FORD   | RESEARCH   |
   | MILLER | ACCOUNTING |
   +--------+------------+
   14 rows in set (0.00 sec)
   ```

4. 内连接值等值连接：最大的特点是：条件是等量关系。

   ```mysql
   SQL92:(太老了，不用了)
   	select e.ename,d.dname from emp e, dept d where e.deptno = d.deptno;
   
   SQL99:(常用的)
   	select e.ename,d.dname from emp e inner join dept d on e.deptno = d.deptno;//inner可以省略，带着inner目的是可读性好一些
   语法：
   	...A join B on 连接条件 where ...
   SQL99语法结构更清晰一些：表的连接条件和后来的where条件分离了。
   ```

5. 内连接之非等值连接：最大的特点是：连接条件中的关系是非等量关系。

   案例：找出每个员工的工资等级，要求显示员工名、工资、工资等级。

   ```mysql
   select ename,sal from emp;
   +--------+---------+
   | ename  | sal     |
   +--------+---------+
   | SMITH  |  800.00 |
   | ALLEN  | 1600.00 |
   | WARD   | 1250.00 |
   | JONES  | 2975.00 |
   | MARTIN | 1250.00 |
   | BLAKE  | 2850.00 |
   | CLARK  | 2450.00 |
   | SCOTT  | 3000.00 |
   | KING   | 5000.00 |
   | TURNER | 1500.00 |
   | ADAMS  | 1100.00 |
   | JAMES  |  950.00 |
   | FORD   | 3000.00 |
   | MILLER | 1300.00 |
   +--------+---------+
   
   select * from salgrade;
   +-------+-------+-------+
   | GRADE | LOSAL | HISAL |
   +-------+-------+-------+
   |     1 |   700 |  1200 |
   |     2 |  1201 |  1400 |
   |     3 |  1401 |  2000 |
   |     4 |  2001 |  3000 |
   |     5 |  3001 |  9999 |
   +-------+-------+-------+
   
   select e.ename,e.sal,s.grade from emp e join salgrade s on e.sal between s.losal and s.hisal;
   +--------+---------+-------+
   | ename  | sal     | grade |
   +--------+---------+-------+
   | SMITH  |  800.00 |     1 |
   | ALLEN  | 1600.00 |     3 |
   | WARD   | 1250.00 |     2 |
   | JONES  | 2975.00 |     4 |
   | MARTIN | 1250.00 |     2 |
   | BLAKE  | 2850.00 |     4 |
   | CLARK  | 2450.00 |     4 |
   | SCOTT  | 3000.00 |     4 |
   | KING   | 5000.00 |     5 |
   | TURNER | 1500.00 |     3 |
   | ADAMS  | 1100.00 |     1 |
   | JAMES  |  950.00 |     1 |
   | FORD   | 3000.00 |     4 |
   | MILLER | 1300.00 |     2 |
   +--------+---------+-------+
   ```

6. 自连接：最大的特点是：一张表看作两张表

   案例：找出每个员工的上级领导，要求显示员工名和对应的领导名。

   ```mysql
   select empno, ename, mgr from emp;
   +-------+--------+------+
   | empno | ename  | mgr  |
   +-------+--------+------+
   |  7369 | SMITH  | 7902 |
   |  7499 | ALLEN  | 7698 |
   |  7521 | WARD   | 7698 |
   |  7566 | JONES  | 7839 |
   |  7654 | MARTIN | 7698 |
   |  7698 | BLAKE  | 7839 |
   |  7782 | CLARK  | 7839 |
   |  7788 | SCOTT  | 7566 |
   |  7839 | KING   | NULL |
   |  7844 | TURNER | 7698 |
   |  7876 | ADAMS  | 7788 |
   |  7900 | JAMES  | 7698 |
   |  7902 | FORD   | 7566 |
   |  7934 | MILLER | 7782 |
   +-------+--------+------+
   
   select a.ename as '员工名', b.ename as '领导名' from emp a inner join emp b on a.mgr = b.empno;
   +--------+--------+
   | 员工名  | 领导名  |
   +--------+--------+
   | SMITH  | FORD   |
   | ALLEN  | BLAKE  |
   | WARD   | BLAKE  |
   | JONES  | KING   |
   | MARTIN | BLAKE  |
   | BLAKE  | KING   |
   | CLARK  | KING   |
   | SCOTT  | JONES  |
   | TURNER | BLAKE  |
   | ADAMS  | SCOTT  |
   | JAMES  | BLAKE  |
   | FORD   | JONES  |
   | MILLER | CLARK  |
   +--------+--------+
   13条
   ```

7. 外连接

   什么是外连接，和内连接有什么区别？

   内连接：假设A和B表进行连接，使用内连接的话，凡是A表和B表能够匹配上的记录查询出来，这就是内连接。AB两张表没有主副之分，两张表是平等的。

   外连接：假设A和B表进行连接，使用外连接的话，AB两张表中有一张表是主表，一张表是副表，主要查询主表中的数据，捎带着查询副表，当副表中的数据没有和主表中的数据匹配上，副表自动模拟出NULL与之匹配。

   外连接的分类：(左外连接/左连接)

   ​		左外连接(左连接)：表示左边的这张表示主表。

   ​		右外连接(右连接)：表示右边的这张表是主表。

   ​		左连接有右连接的写法，右连接有左连接的写法。

   案例：找出每个员工的上级领导，要求显示员工名和对应的领导名。(所有员工必须全部查询出来。)外连接

   ```mysql
   select a.ename as '员工名', b.ename as '领导名' from emp a left outer join emp b on a.mgr = b.empno;
   select a.ename as '员工名', b.ename as '领导名' from emp b right outer join emp a on a.mgr = b.empno; //outer可以省略
   +--------+--------+
   | 员工名 | 领导名 |
   +--------+--------+
   | SMITH  | FORD   |
   | ALLEN  | BLAKE  |
   | WARD   | BLAKE  |
   | JONES  | KING   |
   | MARTIN | BLAKE  |
   | BLAKE  | KING   |
   | CLARK  | KING   |
   | SCOTT  | JONES  |
   | KING   | NULL   |
   | TURNER | BLAKE  |
   | ADAMS  | SCOTT  |
   | JAMES  | BLAKE  |
   | FORD   | JONES  |
   | MILLER | CLARK  |
   +--------+--------+
   14条
   ```

   外连接最重要的特点是：主表的数据无条件的全部查询出来。

   案例：找出哪个部门没有员工。

   ```mysql
   select * from emp;
   +-------+--------+-----------+------+------------+---------+---------+--------+
   | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
   |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
   |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
   |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
   |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
   |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
   |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
   |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
   |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
   |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
   |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
   |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
   |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
   |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   select * from dept;
   +--------+------------+----------+
   | DEPTNO | DNAME      | LOC      |
   +--------+------------+----------+
   |     10 | ACCOUNTING | NEW YORK |
   |     20 | RESEARCH   | DALLAS   |
   |     30 | SALES      | CHICAGO  |
   |     40 | OPERATIONS | BOSTON   |
   +--------+------------+----------+
   
   select d.* from dept d left outer join emp e on d.deptno = e.deptno where e.deptno is null;
   +--------+------------+--------+
   | DEPTNO | DNAME      | LOC    |
   +--------+------------+--------+
   |     40 | OPERATIONS | BOSTON |
   +--------+------------+--------+
   ```

8. 三张表怎么连接查询？

   案例：找出每一个员工的部门名称以及工资等级

   ```mysql
   select * from emp;
   EMP:
   +-------+--------+-----------+------+------------+---------+---------+--------+
   | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
   |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
   |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
   |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
   |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
   |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
   |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
   |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
   |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
   |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
   |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
   |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
   |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
   |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
   +-------+--------+-----------+------+------------+---------+---------+--------+
   
   select * from dept;
   DEPT d
   +--------+------------+----------+
   | DEPTNO | DNAME      | LOC      |
   +--------+------------+----------+
   |     10 | ACCOUNTING | NEW YORK |
   |     20 | RESEARCH   | DALLAS   |
   |     30 | SALES      | CHICAGO  |
   |     40 | OPERATIONS | BOSTON   |
   +--------+------------+----------+
   
   select * from salgrade;
   SALGRADE s
   +-------+-------+-------+
   | GRADE | LOSAL | HISAL |
   +-------+-------+-------+
   |     1 |   700 |  1200 |
   |     2 |  1201 |  1400 |
   |     3 |  1401 |  2000 |
   |     4 |  2001 |  3000 |
   |     5 |  3001 |  9999 |
   +-------+-------+-------+
   
   注意：
   ...
   A
   join
   B
   join
   C
   on
   ...
   表示：A表和B表先进行表连接，连接之后A表继续和C表进行连接
   select
   	e.ename, d.dname, s.grade
   from
   	emp e
   join
   	dept d
   on
   	e.deptno = d.deptno
   join
   	salgrade s
   on
   	e.sal between s.losal and s.hisal;
   
   +--------+------------+-------+
   | ename  | dname      | grade |
   +--------+------------+-------+
   | SMITH  | RESEARCH   |     1 |
   | ALLEN  | SALES      |     3 |
   | WARD   | SALES      |     2 |
   | JONES  | RESEARCH   |     4 |
   | MARTIN | SALES      |     2 |
   | BLAKE  | SALES      |     4 |
   | CLARK  | ACCOUNTING |     4 |
   | SCOTT  | RESEARCH   |     4 |
   | KING   | ACCOUNTING |     5 |
   | TURNER | SALES      |     3 |
   | ADAMS  | RESEARCH   |     1 |
   | JAMES  | SALES      |     1 |
   | FORD   | RESEARCH   |     4 |
   | MILLER | ACCOUNTING |     2 |
   +--------+------------+-------+
   
   要求：找出每一个员工的部门名称、工资等级、以及上级领导。
   select
   	e.ename '员工', d.dname, s.grade, e1.ename '领导'
   from
   	emp e
   join
   	dept d
   on
   	e.deptno = d.deptno
   join
   	salgrade s
   on
   	e.sal between s.losal and s.hisal
   left join
   	emp e1
   on
   	e.mgr = e1.empno;
   +--------+------------+-------+-------+
   | 员工   | dname      | grade | 领导  |
   +--------+------------+-------+-------+
   | SMITH  | RESEARCH   |     1 | FORD  |
   | ALLEN  | SALES      |     3 | BLAKE |
   | WARD   | SALES      |     2 | BLAKE |
   | JONES  | RESEARCH   |     4 | KING  |
   | MARTIN | SALES      |     2 | BLAKE |
   | BLAKE  | SALES      |     4 | KING  |
   | CLARK  | ACCOUNTING |     4 | KING  |
   | SCOTT  | RESEARCH   |     4 | JONES |
   | KING   | ACCOUNTING |     5 | NULL  |
   | TURNER | SALES      |     3 | BLAKE |
   | ADAMS  | RESEARCH   |     1 | SCOTT |
   | JAMES  | SALES      |     1 | BLAKE |
   | FORD   | RESEARCH   |     4 | JONES |
   | MILLER | ACCOUNTING |     2 | CLARK |
   +--------+------------+-------+-------+
   ```


9. 子查询

   select语句中嵌套select语句，被嵌套的select语句是子查询。

   ```mysql
   select
   	..(select).
   from
   	..(select).
   where
   	..(select).
   ```

   ```mysql
   案例：找出高于平均薪资的员工信息。
   select * from emp where sal > avg(sal); //错误的写法,where后面不能直接使用分组函数
   select * from emp where sal > (select avg(sal) from emp);
   +-------+-------+-----------+------+------------+---------+------+--------+
   | EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
   +-------+-------+-----------+------+------------+---------+------+--------+
   |  7566 | JONES | MANAGER   | 7839 | 1981-04-02 | 2975.00 | NULL |     20 |
   |  7698 | BLAKE | MANAGER   | 7839 | 1981-05-01 | 2850.00 | NULL |     30 |
   |  7782 | CLARK | MANAGER   | 7839 | 1981-06-09 | 2450.00 | NULL |     10 |
   |  7788 | SCOTT | ANALYST   | 7566 | 1987-04-19 | 3000.00 | NULL |     20 |
   |  7839 | KING  | PRESIDENT | NULL | 1981-11-17 | 5000.00 | NULL |     10 |
   |  7902 | FORD  | ANALYST   | 7566 | 1981-12-03 | 3000.00 | NULL |     20 |
   +-------+-------+-----------+------+------------+---------+------+--------+
   
   ```

   from后面嵌套子查询

   ```mysql
   案例：找出每个部门平均薪水的薪资等级。
   第一步：找出每个部门平均薪水(按照部门编号分组，求sal的平均值)
   select deptno,avg(sal) as avgsal from emp group by deptno;
   +--------+-------------+
   | deptno | avgsal      |
   +--------+-------------+
   |     20 | 2175.000000 |
   |     30 | 1566.666667 |
   |     10 | 2916.666667 |
   +--------+-------------+
   第二步：将以上的查询结果当做临时表t，让t表和salgrade表连接，条件是：t.avgsal between s.losal and s.hisal
   select t.*, s.grade 
   from t 
   join salgrade s 
   on t.avgsal between s.losal and hisal;  //报错：Table 'bjpowernode.t' doesn't exist
   
   改正：
   select t.*, s.grade 
   from (select deptno,avg(sal) as avgsal from emp group by deptno) t 
   join salgrade s 
   on t.avgsal between s.losal and hisal;
   +--------+-------------+-------+
   | deptno | avgsal      | grade |
   +--------+-------------+-------+
   |     20 | 2175.000000 |     4 |
   |     30 | 1566.666667 |     3 |
   |     10 | 2916.666667 |     4 |
   +--------+-------------+-------+
   ```

   ```mysql
   案例：找出每个部门平均的薪水等级。
   第一步：找出每个员工的薪水等级。
   select ename, sal from emp;
   +--------+---------+
   | ename  | sal     |
   +--------+---------+
   | SMITH  |  800.00 |
   | ALLEN  | 1600.00 |
   | WARD   | 1250.00 |
   | JONES  | 2975.00 |
   | MARTIN | 1250.00 |
   | BLAKE  | 2850.00 |
   | CLARK  | 2450.00 |
   | SCOTT  | 3000.00 |
   | KING   | 5000.00 |
   | TURNER | 1500.00 |
   | ADAMS  | 1100.00 |
   | JAMES  |  950.00 |
   | FORD   | 3000.00 |
   | MILLER | 1300.00 |
   +--------+---------+
   select * from salgrade
   +-------+-------+-------+
   | GRADE | LOSAL | HISAL |
   +-------+-------+-------+
   |     1 |   700 |  1200 |
   |     2 |  1201 |  1400 |
   |     3 |  1401 |  2000 |
   |     4 |  2001 |  3000 |
   |     5 |  3001 |  9999 |
   +-------+-------+-------+
   
   合并
   select e.ename, e.sal, e.deptno, s.grade from emp e join salgrade s on e.sal between s.losal and hisal;
   +--------+---------+--------+-------+
   | ename  | sal     | deptno | grade |
   +--------+---------+--------+-------+
   | SMITH  |  800.00 |     20 |     1 |
   | ALLEN  | 1600.00 |     30 |     3 |
   | WARD   | 1250.00 |     30 |     2 |
   | JONES  | 2975.00 |     20 |     4 |
   | MARTIN | 1250.00 |     30 |     2 |
   | BLAKE  | 2850.00 |     30 |     4 |
   | CLARK  | 2450.00 |     10 |     4 |
   | SCOTT  | 3000.00 |     20 |     4 |
   | KING   | 5000.00 |     10 |     5 |
   | TURNER | 1500.00 |     30 |     3 |
   | ADAMS  | 1100.00 |     20 |     1 |
   | JAMES  |  950.00 |     30 |     1 |
   | FORD   | 3000.00 |     20 |     4 |
   | MILLER | 1300.00 |     10 |     2 |
   +--------+---------+--------+-------+
   
   基于以上的结果，继续按照deptno分组，求grade平均值。
   select e.deptno, avg(s.grade) from emp e join salgrade s on e.sal between s.losal and hisal group by e.deptno;
   +--------+--------------+
   | deptno | avg(s.grade) |
   +--------+--------------+
   |     20 |       2.8000 |
   |     30 |       2.5000 |
   |     10 |       3.6667 |
   +--------+--------------+
   ```

   在select后面嵌套子查询

   ```mysql
   案例：找出每个员工所在的部门名称，要求显示员工名和部门名
   如果直接连接：
   select e.ename, d.dname from emp e join dept d on e.deptno = d.deptno;
   
   换一种方式
   select e.ename, (select d.dname from dept d where e.deptno = d.deptno) as dname from emp e;
   +--------+------------+
   | ename  | dname      |
   +--------+------------+
   | SMITH  | RESEARCH   |
   | ALLEN  | SALES      |
   | WARD   | SALES      |
   | JONES  | RESEARCH   |
   | MARTIN | SALES      |
   | BLAKE  | SALES      |
   | CLARK  | ACCOUNTING |
   | SCOTT  | RESEARCH   |
   | KING   | ACCOUNTING |
   | TURNER | SALES      |
   | ADAMS  | RESEARCH   |
   | JAMES  | SALES      |
   | FORD   | RESEARCH   |
   | MILLER | ACCOUNTING |
   +--------+------------+
   ```

10. union 可以将查询结果集相加

    ```mysql
    案例：找出工作岗位是SALESMAN 和 MANAGER 的员工
    第一种：select ename, job from emp where job = 'MANAGER' or job = 'SALESMAN';
    第二种：select ename, job from emp where job in('MANAGER','SALESMAN');
    第三种：
    select ename, job from emp where job = 'MANAGER'
    union
    select ename, job from emp where job = 'SALESMAN';
    +--------+----------+
    | ename  | job      |
    +--------+----------+
    | JONES  | MANAGER  |
    | BLAKE  | MANAGER  |
    | CLARK  | MANAGER  |
    | ALLEN  | SALESMAN |
    | WARD   | SALESMAN |
    | MARTIN | SALESMAN |
    | TURNER | SALESMAN |
    +--------+----------+
    两张不相干的表中的数据拼接在一起显示？
    select ename from emp
    union
    select dname from dept;
    +------------+
    | ename      |
    +------------+
    | SMITH      |
    | ALLEN      |
    | WARD       |
    | JONES      |
    | MARTIN     |
    | BLAKE      |
    | CLARK      |
    | SCOTT      |
    | KING       |
    | TURNER     |
    | ADAMS      |
    | JAMES      |
    | FORD       |
    | MILLER     |
    | ACCOUNTING |
    | RESEARCH   |
    | SALES      |
    | OPERATIONS |
    +------------+
    ```

11. limit(重点中的重点，以后分页查询全靠它了)

    limit是mysql特有的，其他数据库没有，不通用。Oracle中有一个相同的机制，叫做rownum

    作用是取结果集中的部分数据

    语法机制是：

    ```mysql
    limit startIndex, length
    	startIndex表示起始位置
    	length表示取几个
    案例： 取出工资前五名
    select ename, sal from emp order by sal desc;//排序
    select ename,sal from emp order by sal desc limit 0, 5;//取前5个
    select ename,sal from emp order by sal desc limit 5;//等同于上面
    注意：limit是sql语句最后执行的一个环节
    select ...     5
    from ...       1
    where ...      2
    group by ...   3
    having ...     4
    order by ...   6
    limit ...;     7
    
    通用的标准分页sql？
    每页显示3条记录：
    第1页：0, 3
    第2页：3, 3
    第2页：6, 3
    ...
    第pageNo页： (pageNo - 1) * pageSize, pageSize
    ```

三、创建表

1. 建表语句的语法格式

   ```mysql
   create tabel 表名(
   	字段名1 数据类型,
       字段名2 数据类型,
       字段名3 数据类型,
       ...
   );
   ```

   关于MySQL当中字段的数据类型？

   ```java
   int             整数型(java中的int)
   bigint          长整型(java中的long)
   float           浮点型(java中的float double)
   char            定长字符串(String)
   varchar         可变长字符串(StringBuffer/StringBuilder)
   date            日期类型(对应Java中的java.sql.Date类型)
   BLOB         二进制大对象(存储图片、视频等流媒体信息) Binary Large OBject(对应java中的Object)
   CLOB         字符大对象(存储较大文本，比如，可以存储4G的字符串) Character Large OBject(对应java中的Object)
   ......
   
   char和varchar怎么选择？
       在实际的开发中，当某个字段中的数据长度不发生改变的时候，是定长的，比如：性别、生日等都是采用char。当一个字段的数据长度不确定，例如：简介、姓名等都是采用varchar。
   
   表名在数据库当中一般建议以：t_或者tb1_开始。
   ```

   创建一张学生表，学生信息包括：学号、姓名、性别、班级编号、生日

   学号：bigint

   姓名：varchar

   性别：char

   班级编号：int

   生日：char

   ```mysql
   create table t_student(
   	no bigint,
       name varchar(255),
       sex char(1),
       classno varchar(255),
       birth char(10)
   );
   ```

2. insert语句插入数据

   语法格式：

   ```mysql
   insert into 表名(字段名1,字段名2,字段名3,...) values(值1,值2,值3,....)
   要求：字段的数量和值的数量相同，并且数据类型要对应相同。
   ```

   ```mysql
   insert into t_student(no,name,sex,classno,birth) values(1, 'zhangsan', '1', 'gaosan1ban', '1950-10-12');
   
   insert into t_student values(1, 'jack', '0', 'gaosan2ban', '1986-10-23');//顺序必须和前面表的顺序必须一致，字段可以省略不写，但是后面的value对数量和顺序都有要求
   
   //一次插入多行数据
   insert into t_student(no,name,sex,classno,birth) values(3, 'rose', '1', 'gaosi2ban', '1952-12-14'),(4, 'laotie', '1', 'gaosi2ban', '1952-12-14')；
   ```

   $$
   
   $$

3. 表的复制以及批量插入

   ```mysql
   语法：
   	create table 表名 as select语句;将查询结果当做表创建出来。
   ```

   将查询结果插入到一张表中？

   ```mysql
   insert into dept1 select * from dept;
   ```

4. 修改数据：update

   ```mysql
   语法格式：
   	update 表名 set 字段名1=值1，字段名2=值2...where 条件;
   ```

   ```mysql
   案例：
   把t_student表中的张三班级改成gaosan3ban,生日改成1960-10-12
   update t_student set classno = 'gaosan3ban', birth = '1960-10-12' where name='zhangsan';
   
   +------+----------+------+------------+------------+
   | no   | name     | sex  | classno    | birth      |
   +------+----------+------+------------+------------+
   |    1 | zhangsan | 1    | gaosan3ban | 1960-10-12 |
   |    3 | rose     | 1    | gaosi2ban  | 1952-12-14 |
   |    4 | laotie   | 1    | gaosi2ban  | 1952-12-14 |
   +------+----------+------+------------+------------+
   ```

   ```mysql
   更新所有数据
   update t_student set classno = 'x', birth = 'y';
   ```

5. 删除数据

   ```mysql
   语法格式：
   	delete from 表名 where 条件;
   注意：没有条件全部删除
   ```

   ```mysql
   怎么删除大表？(重点)
   	truncate table emp1;//表被截断，不可回滚，永久丢失。
   ```

6. 约束(Constraint)

   什么是约束？常见的约束有哪些？

   在创建表的时候，可以给表的字段添加相应的约束，添加约束的目的是为了保证表中数据的合法性、有效性、完整性。

   常见的约束有：

   ​	非空约束(not null)：约束的字段不能为null

   ​	唯一约束(unique)：约束的字段不能重复

   ​	主键约束(primary key)：约束的字段既不能为NULL，也不能重复

   ​	外键约束(foreign key)：

   ​	检查约束(check)[注意Oracle数据库有check约束，但是mysql没有，目前mysql不支持该约束]

   (1) 非空约束 not null

   ```mysql
   drop table if exits t_user;
   create table t_user(
   	id int,
       username varchar(255) not null,
       password varchar(255)
   );
   insert into t_user(id, password) values(1,'123');
   ERROR 1364 (HY000): Field 'username' doesn't have a default value
   
   改正：
   insert into t_user(id, username, password) values(1, 'lisi', '123');
   ```

   (2) 唯一性约束(unique)

   唯一约束修饰的字段具有唯一性，不能重复。**但可以为NULL。**

   ```mysql
   案例：
   drop table if exists t_user;
   create table t_user(
   	id int,
       username varchar(255) unique  //这个叫列级约束
   );
   insert into t_user values(1, 'zhangsan');
   insert into t_user values(2, 'zhangsan');
   ERROR 1062 (23000): Duplicate entry 'zhangsan' for key 't_user.username'
   ```

   ```mysql
   案例：给两个列或者多个列添加unique
   drop table if exists t_user;
   create table t_user(
   	id int,
       usercode varchar(255),
       username varchar(255),
       unique(usercode, username)//多个字段联合添加1个约束，这个叫表级约束
   )
   ```

   注意：not null约束只有列级约束，没有表级约束

   (3) 主键约束

   ```mysql
   drop table if exists t_user;
   create table t_user(
   	id int primary key, //列级约束
       username varchar(255),
       email varchar(255)
   );
   insert into t_user(id, username, email) values(1, 'zs', 'zs@123.com');
   insert into t_user(id, username, email) values(2, 'ls', 'ls@123.com');
   insert into t_user(id, username, email) values(3, 'ww', 'ww@123.com');
   select * from t_user;
   +----+----------+------------+
   | id | username | email      |
   +----+----------+------------+
   |  1 | zs       | zs@123.com |
   |  2 | ls       | ls@123.com |
   |  3 | ww       | ww@123.com |
   +----+----------+------------+
   
   insert into t_user(id, username, email) values(1, 'jack', 'jack@123.com');
   ERROR 1062 (23000): Duplicate entry '1' for key 't_user.PRIMARY'
   
   insert into t_user(username, email) values('jack', 'jack@123.com');
   ERROR 1364 (HY000): Field 'id' doesn't have a default value
   
   根据以上的测试得出：id是主键，因为添加了主键约束，主键字段中的数据不能为NULL，也不能重复。
   ```

   主键相关的术语？

   ```mysql
   主键约束：primary key
   主键字段：id字段添加primary key之后，id叫做主键字段
   主键值：id字段中的每一个值都是主键值。
   ```

   主键字段有什么作用？

   ```mysql
   - 表的设计三范式中有要求，第一范式就要求任何一张表都应该有主键。
   - 主键的作用：主键值是这行记录在这张表当中的唯一表示。(就像一个人的身份证号码一样)
   ```

   主键的分类？？

   ```mysql
   根据主键字段的字段数量来划分：单一主键(推荐使用)、复合主键(多个字段联合起来添加一个主键约束)
   根据主键性质来划分：自然主键(主键值最好是一个和业务没有任何关系的自然数)、业务主键(主键值和系统的业务挂钩，比如拿着银行卡的卡号做主键，不建议使用，最好不要拿着和业务挂钩的字段作为主键)
   ```

   一张表的主键约束只能有1个。(必须记住)

   使用表级约束方式定义主键。

   ```mysql
   drop table if exists t_user;
   create table t_user(
   	id int , 
       username varchar(255),
       email varchar(255),
       primary key(id)
   );
   insert into t_user(id, username, email) values(1, 'zs', 'zs@123.com');
   insert into t_user(id, username, email) values(2, 'ls', 'ls@123.com');
   insert into t_user(id, username, email) values(3, 'ww', 'ww@123.com');
   select * from t_user;
   ```

   mysql提供主键值自增：(非常重要)

   ```mysql
   drop table if exists t_user;
   create table t_user(
   	id int primary key auto_increment,//id字段自动维护一个自增的数字，从1开始，以1递增。
       username varchar(255)
   );
   insert into t_user(username) values('a');
   insert into t_user(username) values('b');
   insert into t_user(username) values('c');
   insert into t_user(username) values('d');
   insert into t_user(username) values('e');
   select * from t_user;
   
   +----+----------+
   | id | username |
   +----+----------+
   |  1 | a        |
   |  2 | b        |
   |  3 | c        |
   |  4 | d        |
   |  5 | e        |
   +----+----------+
   ```

   Oracle当中也提供了一个自增机制，叫做：序列(sequence)

   (4) 外键约束

   外键约束的相关术语：

   ```mysql
   外键约束：foreigh key
   外键字段：添加有外键约束的字段
   外键值：外键字段中的每一个值
   ```

   业务背景：请设计数据库表，用来维护学生和班级的信息？

   ```mysql
   第一种方案：一张表存储所有数据
   no(pk)       name            classno           classname
   1             zs1               101              高三1班
   2             zs2               101              高三1班
   3             zs3               102              高三2班
   4             zs4               102              高三2班
   5             zs5               102              高三2班
   缺点：冗余。【不推荐】
   
   第二种方法：两张表(班级表和学生表)
   t_class 班级表
   cno(pk)                  cname
   -----------------------------------------
   101                       高三1班
   102                       高三2班
   
   t_student 学生表
   sno(pk)                  sname          cno(该字段添加外键约束fk)
   -------------------------------------------------------------------
   1                         zs1                      101
   2                         zs2                      101
   3                         zs3                      102
   4                         zs4                      102
   5                         zs5                      102
   
   
   t_student中的classno字段引用t_class表中的cno字段，此时t_student表叫做子表，t_class表叫做父表。
   删除数据的时候，先删除子表，再删除父表；添加数据的时候，先添加父表，再添加子表。
   创建表的时候，先创建父表，再创建子表。删除表的时候，先删除子表，再删除父表。
   
   drop table if exists t_student;
   drop table if exists t_class;
   
   create table t_class(
   	cno int,
       cname varchar(255),
       primary key(cno)
   );
   create table t_student(
   	sno int,
       sname varchar(255),
       classno int,
       foreign key(classno) references t_class(cno)
   );
   insert into t_class values(101, 'xxxxxxxxxxxxx');
   insert into t_class values(102, 'yyyyyyyyyyyyyyyyy');
   
   insert into t_student values(1, 'zs1', 101);
   insert into t_student values(2, 'zs2', 101);
   insert into t_student values(3, 'zs3', 102);
   insert into t_student values(4, 'zs4', 102);
   insert into t_student values(5, 'zs5', 102);
   
   select * from t_class;
   select * from t_student;
   
   +-----+-------------------+
   | cno | cname             |
   +-----+-------------------+
   | 101 | xxxxxxxxxxxxx     |
   | 102 | yyyyyyyyyyyyyyyyy |
   +-----+-------------------+
   
   +------+-------+---------+
   | sno  | sname | classno |
   +------+-------+---------+
   |    1 | zs1   |     101 |
   |    2 | zs2   |     101 |
   |    3 | zs3   |     102 |
   |    4 | zs4   |     102 |
   |    5 | zs5   |     102 |
   +------+-------+---------+
   
   insert into t_student values(6,'lisi',103);
   ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`bjpowernode`.`t_student`, CONSTRAINT `t_student_ibfk_1` FOREIGN KEY (`classno`) REFERENCES `t_class` (`cno`))
   
   外键值可以为NULL吗？外键可以为NULL。
   
   外键字段引用其他表的某个字段时，被引用的字段必须是主键吗？
   注意：被引用的字段不一定是主键，但至少具有unique约束。
   ```

7. 存储引擎

   1. 完整的建表语句

   ```mysql
   CREATE TABLE `t_x` (
   `id` int(11) DEFAULT NULL
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   建表的时候可以指定存储引擎，也可以指定字符集。mysql默认使用的存储引擎是InnoDB方式，默认采用的字符集是UTF8.

   2. 什么是存储引擎？

      存储引擎这个名字只有在mysql中存在。(Oracle中有对应的机制，但是不叫做存储引擎。Oracle中没有特殊的名字，就叫“表的存储方式”)。

      mysql支持很多存储引擎，每一个存储引擎都对应了一种不同的存储方式。每一个存储引擎都有自己的优缺点，需要在合适的时机选择合适的存储引擎。

   3. 查看当前mysql支持的存储引擎？

      show engines \G

      mysql 5.5.36版本支持的存储引擎有9个：

      ```mysql
      *************************** 1. row ***************************
            Engine: MEMORY
           Support: YES
           Comment: Hash based, stored in memory, useful for temporary tables
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 2. row ***************************
            Engine: MRG_MYISAM
           Support: YES
           Comment: Collection of identical MyISAM tables
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 3. row ***************************
            Engine: CSV
           Support: YES
           Comment: CSV storage engine
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 4. row ***************************
            Engine: FEDERATED
           Support: NO
           Comment: Federated MySQL storage engine
      Transactions: NULL
                XA: NULL
        Savepoints: NULL
      *************************** 5. row ***************************
            Engine: PERFORMANCE_SCHEMA
           Support: YES
           Comment: Performance Schema
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 6. row ***************************
            Engine: MyISAM
           Support: YES
           Comment: MyISAM storage engine
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 7. row ***************************
            Engine: InnoDB
           Support: DEFAULT
           Comment: Supports transactions, row-level locking, and foreign keys
      Transactions: YES
                XA: YES
        Savepoints: YES
      *************************** 8. row ***************************
            Engine: BLACKHOLE
           Support: YES
           Comment: /dev/null storage engine (anything you write to it disappears)
      Transactions: NO
                XA: NO
        Savepoints: NO
      *************************** 9. row ***************************
            Engine: ARCHIVE
           Support: YES
           Comment: Archive storage engine
      Transactions: NO
                XA: NO
        Savepoints: NO
      ```

   4. 常见的存储引擎？

      ```mysql
      *************************** 6. row ***************************
            Engine: MyISAM
           Support: YES
           Comment: MyISAM storage engine
      Transactions: NO
                XA: NO
        Savepoints: NO
      MyISAM这种存储引擎不支持事务。MyISAM存储引擎是MySQL最常用的引擎，但不是默认的。它管理的表具有以下特征：
      - 使用三个文件表示每个表：
      	- 格式文件 = 存储表结构的定义(mytable.frm)
      	- 数据文件 = 存储表行的内容(mytable.MYD)
      	- 索引文件 = 存储表上索引(mytable.MYI)
      - 灵活的AUTO_INCREMENT字段处理
      - 可被转换为压缩、只读表来节省空间
      ```

      ```mysql
      *************************** 7. row ***************************
            Engine: InnoDB
           Support: DEFAULT
           Comment: Supports transactions, row-level locking, and foreign keys
      Transactions: YES
                XA: YES
        Savepoints: YES
        优点：支持事务，这种存储引擎数据的安全得到保障。
        表的结构存储在xxx.frm文件中
        数据存储在tablespace这样的表空间中(逻辑概念)，无法被压缩，无法转换成只读。
        在MySQL服务器崩溃后提供自动恢复机制。InnoDB支持级联删除和级联更新。
      ```

      ```mysql
      *************************** 1. row ***************************
            Engine: MEMORY
           Support: YES
           Comment: Hash based, stored in memory, useful for temporary tables
      Transactions: NO
                XA: NO
        Savepoints: NO
        缺点：不支持事务，数据容易丢失。因为所有数据和索引都是存储在内存当中。
        优点：查询速度最快。
      ```

      ```mysql
      作业题：
      1. 取得每个部门最高薪水的人员名称
      第一步：取得每个部门最高薪水
      select deptno,max(sal) as maxsal from emp group by deptno;
      +--------+---------+
      | deptno | maxsal  |
      +--------+---------+
      |     20 | 3000.00 |
      |     30 | 2850.00 |
      |     10 | 5000.00 |
      +--------+---------+
      第二步：将以上结果当做临时表t,t表和emp e表进行连接，条件是：t.deptno = e.deptno and t.maxsal = e.sal
      select
      	e.ename, t.*
      from
      	(select deptno,max(sal) as maxsal from emp group by deptno) t
      join
      	emp e
      on 
      	t.deptno = e.deptno and t.maxsal = e.sal;
      +-------+--------+---------+
      | ename | deptno | maxsal  |
      +-------+--------+---------+
      | BLAKE |     30 | 2850.00 |
      | SCOTT |     20 | 3000.00 |
      | KING  |     10 | 5000.00 |
      | FORD  |     20 | 3000.00 |
      +-------+--------+---------+
      ```

   5. 事务(Transaction)

      1. 什么是事务？

         一个事务是一个完整的业务逻辑单元，不可再分。

         比如：银行账户转账，从A账户向B账户转账10000.需要执行两条update语句：

         ```mysql
         update t_act set balance = balance - 10000 where actno = 'act-001';
         update t_act set balance = balance + 10000 where actno = 'act-002';
         以上两条DML语句必须同时成功，或者同时失败，不允许出现一条成功，一条失败。
         要想保证DML语句同时成功或者同时失败，那么就需要使用数据库的"事务机制"。
         ```

      2. 和事务相关的语句只有：DML语句。(insert delete update)，create跟事务无关

         为什么？因为它们这三个语句都是和数据库表当中“数据”相关的。事务的存在是为了保证数据的完整性，安全性。

      3. 假设所有的业务都能使用1条DML语句搞定，还需要事务机制吗？不需要。但实际情况不是这样的，通常一个事务需要多条DML语句共同联合完成的。

      ![image-20210508105830934](https://i.loli.net/2021/05/08/yLDXVlH1Qxh6v2p.png)

      4. 事务的特性：

         事务包括四大特性：ACID

         A：原子性：事务是最小的工作单元，不可再分

         C：一致性：事务必须保证多条DML语句同时成功或者同时失败

         I：隔离性：事务A和事务B之间具有隔离

         D：持久性：持久性说的是最终数据必须持久化到硬盘文件中，事务才算成功的结束。

      5. 事务隔离性：

         事务隔离性存在隔离级别，理论上隔离级别包括4个：

         ​	第一级别：读未提交(read uncommitted)

         ​			对方事务还没有提交，我们当前事务可以读取到未提交的数据。读未提交存在脏读(Dirty Read)现象：表示读到了脏的数据。

         ​	第二级别：读已提交(read committed)

         ​			对方事务提交之后的数据我方可以读取到。读已提交存在的问题：不可重复读。这种隔离级别解决了：脏读现象没有了，但带来了不可重复读的问题。

         ​	第三级别：可重复读(repeatable read)

         ​			这种隔离级别解决了：不可重复读问题。这种隔离级别存在的问题是：读取到的数据是幻想。

         ​	第四级别：序列化读/串行化读

         ​			解决了所有问题，但存在效率低的问题，需要事务排队。

         oracle数据库默认的隔离级别是：读已提交。mysql数据库默认的隔离级别是：可重复读。

    6. 索引

       1. 什么是索引？有什么用？

          索引就相当于一本书的目录，通过目录可以快速地找到对应的资源。在数据库方面，查询一张表的时候有两种检索方式：

          ​	第一种方式：全表索引

          ​	第二种方式：根据索引检索(效率高)

          索引为什么可以提高检索效率呢？

          ​	其实最根本的原理是缩小了扫描的范围。

          索引虽然可以提高检索效率，但是不能随意地添加索引，因为索引也是也是数据库当中的对象，也需要数据库不断地维护，是有维护成本的。比如，表中的数据经常被修改这样就不适合添加索引，因为数据一旦被修改，索引需要重新排序，进行维护。

          添加索引是给某一个字段，或者说某些字段添加索引。

       2. 怎么创建索引对象？怎么删除索引对象？

       3. 什么时候考虑给字段添加索引？(满足什么条件)

          - 数据量庞大。(根据客户的需求，根据线上的环境)  
          - 该字段很少的DML操作。(因为字段进行修改操作，索引也需要维护)
          - 该字段经常出现在where子句中。(经常根据哪个字段查询)

       4. 注意：主键和具有unique约束的字段自动会添加索引。所以根据主键查询效率较高。

       5. 查看sql语句的执行计划：

          ```mysql
          mysql> explain select ename,sal from emp where sal=5000;
          +----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
          | id | select_type | table | partitions | type | possible_keys | key  | key_len | ref  | rows | filtered | Extra       |
          +----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
          |  1 | SIMPLE      | emp   | NULL       | ALL  | NULL          | NULL | NULL    | NULL |   14 |    10.00 | Using where |
          +----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
          ```

          给薪资sal字段添加索引：

          ```mysql
          create index emp_sal_index on emp(sal);
          ```

          ```mysql
          mysql> explain select ename,sal from emp where sal=5000;
          +----+-------------+-------+------------+------+---------------+---------------+---------+-------+------+----------+-------+
          | id | select_type | table | partitions | type | possible_keys | key           | key_len | ref   | rows | filtered | Extra |
          +----+-------------+-------+------------+------+---------------+---------------+---------+-------+------+----------+-------+
          |  1 | SIMPLE      | emp   | NULL       | ref  | emp_sal_index | emp_sal_index | 9       | const |    1 |   100.00 | NULL  |
          +----+-------------+-------+------------+------+---------------+---------------+---------+-------+------+----------+-------+
          1 row in set, 1 warning (0.00 sec)
          ```

          删除索引对象

          ```mysql
          drop index 索引名称 on 表名(字段名)：
          ```

       6. 索引底层采用的数据结构是：B+Tree

       7. 索引的实现原理：

          ```mysql
          通过B Tree缩小扫描范围，底层索引进行了排序、分区，索引会携带数据在表中的"物理地址",最终通过索引检索到数据之后，获取到关联的物理地址，通过物理地址定位表中的数据，效率是最高的。
          select ename from emp where ename = 'SMITH';
          通过索引转换为:
          select ename from emp where 物理地址=0x3;
          ```

          ![image-20210508150547322](https://i.loli.net/2021/05/08/ZvrSTIugJLbyt9z.png)

       8. 索引分类：

          ```mysql
          单一索引：给单个字段添加索引
          复合索引：给多个字段联合起来添加1个索引
          主键索引：主键上会自动添加索引
          唯一索引：有unique约束的字段上会自动添加索引
          ```

       9. 索引什么时候失效？

          ```mysql
          select ename from emp where ename like '%A%';
          模糊查询的时候，第一个通配符使用的是%,这个时候索引是失效的。
          ```

   7. 视图(view)

      1. 什么是视图？

         站在不同的角度去看到数据。(同一张表的数据，通过不同的角度去看待)。

      2. 怎么创建视图？怎么删除视图？

         ```mysql
         create view myview as select empno, ename from emp;
         drop view myview;
         
         注意：只有DQL语句才能以视图对象的方式创建出来。
         ```

      3. 对视图进行增删改查，会影响到原表数据。(通过视图影响原表数据的，不是直接操作的原表)。可以对视图进行CRUD操作。

         ```mysql
         create table emp_bak as select * from emp;
         create view myview1 as select empno, ename, sal from emp_bak;
         update myview1 set ename='hehe', sal=1 where empno = 7369;//通过视图修改原表数据
         +-------+--------+-----------+------+------------+---------+---------+--------+
         | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
         +-------+--------+-----------+------+------------+---------+---------+--------+
         |  7369 | hehe   | CLERK     | 7902 | 1980-12-17 |    1.00 |    NULL |     20 |
         |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
         |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
         |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
         |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
         |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
         |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
         |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
         |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
         |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
         |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
         |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
         |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
         |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
         +-------+--------+-----------+------+------------+---------+---------+--------+
         delete from myview1 where empno = 7369; //通过视图删除原表数据。
         ```

      4. 视图的作用？

         视图可以隐藏表的实现细节，保密级别较高的系统，数据库只对外提供相关的视图，java程序员只对视图对象进行CRUD。

   8. DBA命令

      1. 将数据库当中的数据导入

         ```mysql
         在windows的dos命令窗口中执行：(导出整个库)
         	mysqldump bjpowernode>D:\bjpowernode.sql -uroot -p333
         
         在windows的dos命令窗口中执行：(导出指定数据库当中的指定表)
         	mysqldump bjpowernode emp>D:\bjpowernode.sql -uroot -p333
         ```

      2. 导入数据

         ```mysql
         create database bjpowernode;
         use bjpowernode;
         source D:\bjpowernode.sql
         ```

   9. 数据库设计三范式(重点内容， 经常问)

      1. 什么是设计范式？

         设计表的依据，按照这个三范式设计的表不会出现数据冗余。

      2. 三范式都是哪些？

         第一范式：任何一张表都应该有主键，并且每一个字段原子性不可再分。

         第二范式：建立在第一范式的基础之上，所有非主键字段完全依赖主键，不能产生部分依赖。【多对多，三张表，关系表两个外键】

         第三范式：建立在第二范式的基础之上，所有非主键字段直接依赖主键，不能产生传递依赖。【一对多，两张表，多的表加外键】

      > 提醒：在实际的开发中，以满足客户的需求为主，有的时候会拿冗余换执行速度。

      3. 一对一怎么设计？

         ```mysql
         一对一设计有两种方案：主键共享
         t_user_login   用户登录表
         id(pk)     username     password
         ---------------------------------
         1            zs            123
         2            ls            456
         
         t_user_detail 用户详细信息表
         id(pk+fk)   realname      tel       ...
         ------------------------------------------------------------
         1            张三         11111111      
         1            李四         11222222      
         
         一对一设计有两种方案：外键唯一。
         t_user_login 用户登录表
         id(pk)       username      password
         -----------------------------------------------------
         1               zs             123
         2               ls             456
         
         t_user_detail 用户详细信息表
         id(pk)       realname         tel          userid(fk+unique)...
         ------------------------------------------------------------------
         1              张三            1111111            2
         2              李四            1111555            1
         ```

      10. 作业题

          ```mysql
          1. 取得每个部门最高薪水的人员名称
          第一步：取得每个部门最高薪水(按照部门编号分组，找出每一组最大值)
          select deptno,max(sal) as maxsal from emp group by deptno;
          +--------+---------+
          | deptno | maxsal  |
          +--------+---------+
          |     20 | 3000.00 |
          |     30 | 2850.00 |
          |     10 | 5000.00 |
          +--------+---------+
          第二步：将以上的查询结果当做一张临时表t,t和emp表连接，条件：t.deptno = e.deptno and t.maxsal = e.sal
          select
          	e.ename, t.*
          from
          	emp e
          join
          	(select deptno,max(sal) as maxsal from emp group by deptno) t
          on
          	t.deptno = e.deptno and t.maxsal = e.sal;
          +-------+--------+---------+
          | ename | deptno | maxsal  |
          +-------+--------+---------+
          | BLAKE |     30 | 2850.00 |
          | SCOTT |     20 | 3000.00 |
          | KING  |     10 | 5000.00 |
          | FORD  |     20 | 3000.00 |
          +-------+--------+---------+
          ```

          ```mysql
          2. 哪些人的薪水在部门的平均薪水之上
          第一步：找出每个部门的平均薪水
          select deptno, avg(sal) as avgsal from emp group by deptno;
          +--------+-------------+
          | deptno | avgsal      |
          +--------+-------------+
          |     20 | 2175.000000 |
          |     30 | 1566.666667 |
          |     10 | 2916.666667 |
          +--------+-------------+
          第二步：将以上查询结果当做t表，t和emp表连接
          条件：部门编号相同， 并且emp的sal大于t表的avgsal
          select
          	t.*, e.ename, e.sal
          from
          	emp e
          join
          	(select deptno, avg(sal) as avgsal from emp group by deptno) t
          on
          	e.deptno = t.deptno and e.sal > t.avgsal;
          +--------+-------------+-------+---------+
          | deptno | avgsal      | ename | sal     |
          +--------+-------------+-------+---------+
          |     30 | 1566.666667 | ALLEN | 1600.00 |
          |     20 | 2175.000000 | JONES | 2975.00 |
          |     30 | 1566.666667 | BLAKE | 2850.00 |
          |     20 | 2175.000000 | SCOTT | 3000.00 |
          |     10 | 2916.666667 | KING  | 5000.00 |
          |     20 | 2175.000000 | FORD  | 3000.00 |
          +--------+-------------+-------+---------+
          ```

          ```mysql
          3. 取得部门中(所有人的)平均的薪水等级
          第一步：找出每一个人的薪水等级
          select
          	e.ename,e.sal,e.deptno, s.grade
          from
          	emp e
          join
          	salgrade s
          on e.sal between s.losal and s.hisal;
          +--------+---------+--------+-------+
          | ename  | sal     | deptno | grade |
          +--------+---------+--------+-------+
          | SMITH  |  800.00 |     20 |     1 |
          | ALLEN  | 1600.00 |     30 |     3 |
          | WARD   | 1250.00 |     30 |     2 |
          | JONES  | 2975.00 |     20 |     4 |
          | MARTIN | 1250.00 |     30 |     2 |
          | BLAKE  | 2850.00 |     30 |     4 |
          | CLARK  | 2450.00 |     10 |     4 |
          | SCOTT  | 3000.00 |     20 |     4 |
          | KING   | 5000.00 |     10 |     5 |
          | TURNER | 1500.00 |     30 |     3 |
          | ADAMS  | 1100.00 |     20 |     1 |
          | JAMES  |  950.00 |     30 |     1 |
          | FORD   | 3000.00 |     20 |     4 |
          | MILLER | 1300.00 |     10 |     2 |
          +--------+---------+--------+-------+
          
          第二步：基于以上的结果继续按照deptno分组，求grade的平均值
          select
          	e.deptno, avg(s.grade)
          from
          	emp e
          join
          	salgrade s
          on e.sal between s.losal and s.hisal
          group by
          	e.deptno;
          +--------+--------------+
          | deptno | avg(s.grade) |
          +--------+--------------+
          |     20 |       2.8000 |
          |     30 |       2.5000 |
          |     10 |       3.6667 |
          +--------+--------------+
          ```

          ```mysql
          4. 不准用组函数(Max),取得最高薪水(给出两种解决方案)
          第一种：降序，limit 1
          select ename, sal from emp order by sal desc limit 1;
          +-------+---------+
          | ename | sal     |
          +-------+---------+
          | KING  | 5000.00 |
          +-------+---------+
          第二种：Max
          第三种：表的自连接
          select sal from emp where sal not in(select
          	distinct a.sal
          from
          	emp a
          join
          	emp b
          on
          	a.sal < b.sal);
          
          select
          	distinct a.sal
          from
          	emp a
          join
          	emp b
          on
          	a.sal < b.sal;
          +---------+
          | sal     |
          +---------+
          | 5000.00 |
          +---------+
          ```

          ```mysql
          5.取得平均薪水最高的部门的部门编号(至少给出两种解决方案)
          第一种方案：
          第一步：计算平均薪水
          select deptno, avg(sal) as avgsal from emp group by deptno;
          +--------+-------------+
          | deptno | avgsal      |
          +--------+-------------+
          |     20 | 2175.000000 |
          |     30 | 1566.666667 |
          |     10 | 2916.666667 |
          +--------+-------------+
          第二步：找出最高薪水(降序选第一个)
          select deptno, avg(sal) as avgsal from emp group by deptno order by avgsal desc limit 1;
          +--------+-------------+
          | deptno | avgsal      |
          +--------+-------------+
          |     10 | 2916.666667 |
          +--------+-------------+
          第二种方案：
          select max(t.avgsal) from (select avg(sal) as avgsal from emp group by deptno) t;
          +---------------+
          | max(t.avgsal) |
          +---------------+
          |   2916.666667 |
          +---------------+
          select deptno,avg(sal) as avgsal from emp group by deptno having avgsal = (select max(t.avgsal) from (select avg(sal) as avgsal from emp group by deptno) t);
          +--------+-------------+
          | deptno | avgsal      |
          +--------+-------------+
          |     10 | 2916.666667 |
          +--------+-------------+
          ```

          ```mysql
          6.取得平均薪水最高的部门的部门名称
          select
          	d.dname, avg(e.sal) as avgsal
          from
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          group by
          	d.dname
          order by
          	avgsal desc
          limit 1;
          +------------+-------------+
          | dname      | avgsal      |
          +------------+-------------+
          | ACCOUNTING | 2916.666667 |
          +------------+-------------+
          ```

          ```mysql
          7. 求平均薪水的等级最低的部门的部门名称
          第一步：按照部门名称分组，找出每个部门的平均薪水
          select deptno,avg(sal) as avgsal from emp group by deptno;
          第二步：找出每个部门的平均薪水的等级
          以上t表和salgrade表连接，条件：t.avgsal between s.losal and s.hisal
          select
          	t.*, s.grade
          from
          	(select deptno,avg(sal) as avgsal from emp group by deptno) t
          join
          	salgrade s
          on
          	t.avgsal between s.losal and s.hisal;
          +--------+-------------+-------+
          | deptno | avgsal      | grade |
          +--------+-------------+-------+
          |     20 | 2175.000000 |     4 |
          |     30 | 1566.666667 |     3 |
          |     10 | 2916.666667 |     4 |
          +--------+-------------+-------+
          
          平均薪水最低对应的等级一定是最低的。
          select avg(sal) as avgsal from emp group by deptno order by avgsal asc limit 1;
          +-------------+
          | avgsal      |
          +-------------+
          | 1566.666667 |
          +-------------+
          select grade from salgrade where(select avg(sal) as avgsal from emp group by deptno order by avgsal asc limit 1) between losal and hisal;
          +-------+
          | grade |
          +-------+
          |     3 |
          +-------+
          
          select
          	t.*, s.grade
          from
          	(select d.dname,avg(sal) as avgsal from emp e join dept d on e.deptno = d.deptno group by d.dname) t
          join
          	salgrade s
          on
          	t.avgsal between s.losal and s.hisal
          where
          	s.grade = (select grade from salgrade where (select avg(sal) as avgsal from emp group by deptno order by avgsal asc limit 1) between losal and hisal);
          +-------+-------------+-------+
          | dname | avgsal      | grade |
          +-------+-------------+-------+
          | SALES | 1566.666667 |     3 |
          +-------+-------------+-------+
          ```

          ```mysql
          8. 取得比普通员工(员工代码没有在mgr字段上出现的)的最高薪水还要高的领导人姓名
          mysql> select distinct mgr from emp;
          +------+
          | mgr  |
          +------+
          | 7902 |
          | 7698 |
          | 7839 |
          | 7566 |
          | NULL |
          | 7788 |
          | 7782 |
          +------+
          员工编号没有在以上范围内的都是普通员工。
          第一步：找出普通员工的最高薪水！
          not in 在使用的时候，后面小括号中记得排除NULL
          select max(sal) from emp where empno not in (select distinct mgr from emp where mgr is not null);
          +----------+
          | max(sal) |
          +----------+
          |  1600.00 |
          +----------+
          第二步：找出高于1600的
          select ename, sal from emp where sal > (select max(sal) from emp where empno not in (select distinct mgr from emp where mgr is not null));
          +-------+---------+
          | ename | sal     |
          +-------+---------+
          | JONES | 2975.00 |
          | BLAKE | 2850.00 |
          | CLARK | 2450.00 |
          | SCOTT | 3000.00 |
          | KING  | 5000.00 |
          | FORD  | 3000.00 |
          +-------+---------+
          ```

          ```mysql
          9. 取得薪水最高的前五名员工
          select ename,sal from emp order by sal desc limit 5;
          +-------+---------+
          | ename | sal     |
          +-------+---------+
          | KING  | 5000.00 |
          | SCOTT | 3000.00 |
          | FORD  | 3000.00 |
          | JONES | 2975.00 |
          | BLAKE | 2850.00 |
          +-------+---------+
          ```

          ```mysql
          10. 取得薪水最高的第六到第十名员工
          select ename,sal from emp order by sal desc limit 5, 5;
          +--------+---------+
          | ename  | sal     |
          +--------+---------+
          | CLARK  | 2450.00 |
          | ALLEN  | 1600.00 |
          | TURNER | 1500.00 |
          | MILLER | 1300.00 |
          | WARD   | 1250.00 |
          +--------+---------+
          ```

          ```mysql
          11.取得最后入职的5名员工
          日期也可以降序，升序。
          select ename, hiredate from emp order by hiredate desc limit 5;
          +--------+------------+
          | ename  | hiredate   |
          +--------+------------+
          | ADAMS  | 1987-05-23 |
          | SCOTT  | 1987-04-19 |
          | MILLER | 1982-01-23 |
          | JAMES  | 1981-12-03 |
          | FORD   | 1981-12-03 |
          +--------+------------+
          ```

          ```mysql
          12. 取得每个薪水 等级有多少员工
          第一步：找出每个员工的薪水等级
          select e.ename,e.sal,s.grade from emp e join salgrade s on e.sal between s.losal and s.hisal;
          +--------+---------+-------+
          | ename  | sal     | grade |
          +--------+---------+-------+
          | SMITH  |  800.00 |     1 |
          | ALLEN  | 1600.00 |     3 |
          | WARD   | 1250.00 |     2 |
          | JONES  | 2975.00 |     4 |
          | MARTIN | 1250.00 |     2 |
          | BLAKE  | 2850.00 |     4 |
          | CLARK  | 2450.00 |     4 |
          | SCOTT  | 3000.00 |     4 |
          | KING   | 5000.00 |     5 |
          | TURNER | 1500.00 |     3 |
          | ADAMS  | 1100.00 |     1 |
          | JAMES  |  950.00 |     1 |
          | FORD   | 3000.00 |     4 |
          | MILLER | 1300.00 |     2 |
          +--------+---------+-------+
          第二步：继续按照grade分组统计数量
          select
          	s.grade, count(*)
          from
          	emp e
          join
          	salgrade s
          on
          	e.sal between s.losal and s.hisal
          group by
          	s.grade;
          +-------+----------+
          | grade | count(*) |
          +-------+----------+
          |     1 |        3 |
          |     3 |        2 |
          |     2 |        3 |
          |     4 |        5 |
          |     5 |        1 |
          +-------+----------+
          ```

          ```mysql
          13.面试题
          有3个表S(学生表)，C(课程表)，SC(学生选课表)
          S(SNO, SNAME)代表(学号，姓名)
          C(CNO,NAME,CTEACHER) 代表 (课号，课名，教师)
          SC(SNO, CNO, SCGRADE) 代表(学号，课号，成绩)
          问题：
          1.找出没选过"黎明"老师的所有学生姓名。
          2.列出2门以上(含2门)不及格学生姓名及平均成绩。
          3.既学过1号课程又学过2号课所有学生的姓名。
          请使用标准Sql语句写出答案，方言也行(请说明是使用什么方言)。
          ```

          ```mysql
          14.列出所有员工及领导的姓名
          select
          	a.ename '员工', b.ename '领导'
          from
          	emp a
          left join
          	emp b
          on
          	a.mgr = b.empno;
          +--------+-------+
          | 员工   | 领导  |
          +--------+-------+
          | SMITH  | FORD  |
          | ALLEN  | BLAKE |
          | WARD   | BLAKE |
          | JONES  | KING  |
          | MARTIN | BLAKE |
          | BLAKE  | KING  |
          | CLARK  | KING  |
          | SCOTT  | JONES |
          | KING   | NULL  |
          | TURNER | BLAKE |
          | ADAMS  | SCOTT |
          | JAMES  | BLAKE |
          | FORD   | JONES |
          | MILLER | CLARK |
          +--------+-------+
          ```

          ```mysql
          15. 列出受雇日期早于其直接上级的所有员工的编号，姓名，部门名称
          select
          	a.ename '员工', a.hiredate, b.ename '领导', b.hiredate, d.dname
          from
          	emp a
          join
          	emp b
          on
          	a.mgr = b.empno
          join
          	dept d
          on
          	a.deptno = d.deptno
          where
          	a.hiredate < b.hiredate;
          +-------+------------+-------+------------+------------+
          | 员工  | hiredate   | 领导  | hiredate   | dname      |
          +-------+------------+-------+------------+------------+
          | SMITH | 1980-12-17 | FORD  | 1981-12-03 | RESEARCH   |
          | ALLEN | 1981-02-20 | BLAKE | 1981-05-01 | SALES      |
          | WARD  | 1981-02-22 | BLAKE | 1981-05-01 | SALES      |
          | JONES | 1981-04-02 | KING  | 1981-11-17 | RESEARCH   |
          | BLAKE | 1981-05-01 | KING  | 1981-11-17 | SALES      |
          | CLARK | 1981-06-09 | KING  | 1981-11-17 | ACCOUNTING |
          +-------+------------+-------+------------+------------+
          ```

          ```mysql
          16.列出部门名称和这些部门的员工信息，同时列出那些没有员工的部门。
          select
          	e.*, d.dname
          from
          	emp e
          right join
          	dept d
          on
          	e.deptno = d.deptno;
          +-------+--------+-----------+------+------------+---------+---------+--------+------------+
          | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO | dname      |
          +-------+--------+-----------+------+------------+---------+---------+--------+------------+
          |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 | ACCOUNTING |
          |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 | ACCOUNTING |
          |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 | ACCOUNTING |
          |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 | RESEARCH   |
          |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 | RESEARCH   |
          |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 | RESEARCH   |
          |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 | RESEARCH   |
          |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 | RESEARCH   |
          |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 | SALES      |
          |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 | SALES      |
          |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 | SALES      |
          |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 | SALES      |
          |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 | SALES      |
          |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 | SALES      |
          |  NULL | NULL   | NULL      | NULL | NULL       |    NULL |    NULL |   NULL | OPERATIONS |
          +-------+--------+-----------+------+------------+---------+---------+--------+------------+
          ```

          ```mysql
          17.列出至少有5个员工的所有部门
          按照部门编号分组，计数，筛选出>= 5
          select
          	deptno
          from
          	emp
          group by
          	deptno
          having
          	count(*) >= 5;
          +--------+
          | deptno |
          +--------+
          |     20 |
          |     30 |
          +--------+
          ```

          ```mysql
          18.列出薪金比"SMITH"多的所有员工信息
          select ename,sal from emp where sal > (select sal from emp where ename = 'SMITH');
          +--------+---------+
          | ename  | sal     |
          +--------+---------+
          | ALLEN  | 1600.00 |
          | WARD   | 1250.00 |
          | JONES  | 2975.00 |
          | MARTIN | 1250.00 |
          | BLAKE  | 2850.00 |
          | CLARK  | 2450.00 |
          | SCOTT  | 3000.00 |
          | KING   | 5000.00 |
          | TURNER | 1500.00 |
          | ADAMS  | 1100.00 |
          | JAMES  |  950.00 |
          | FORD   | 3000.00 |
          | MILLER | 1300.00 |
          +--------+---------+
          ```

          ```mysql
          19.列出所有"CLERK"(办事员)的姓名及其部门名称，部门的人数
          select
          	e.ename, e.job, d.dname, d.deptno
          from
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          where
          	e.job = 'CLERK';
          +--------+-------+------------+--------+
          | ename  | job   | dname      | deptno |
          +--------+-------+------------+--------+
          | SMITH  | CLERK | RESEARCH   |     20 |
          | ADAMS  | CLERK | RESEARCH   |     20 |
          | JAMES  | CLERK | SALES      |     30 |
          | MILLER | CLERK | ACCOUNTING |     10 |
          +--------+-------+------------+--------+
          
          //每个部门的人数？
          select deptno, count(*) as deptcount from emp group by deptno;
          +--------+-----------+
          | deptno | deptcount |
          +--------+-----------+
          |     20 |         5 |
          |     30 |         6 |
          |     10 |         3 |
          +--------+-----------+
          上面两张表做连接
          select
          	t1.*, t2.deptcount
          from
          	(select
          	e.ename, e.job, d.dname, d.deptno
          from
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          where
          	e.job = 'CLERK') t1
          join
          	(select deptno, count(*) as deptcount from emp group by deptno) t2
          on
          	t1.deptno = t2.deptno;
          +--------+-------+------------+--------+-----------+
          | ename  | job   | dname      | deptno | deptcount |
          +--------+-------+------------+--------+-----------+
          | SMITH  | CLERK | RESEARCH   |     20 |         5 |
          | ADAMS  | CLERK | RESEARCH   |     20 |         5 |
          | JAMES  | CLERK | SALES      |     30 |         6 |
          | MILLER | CLERK | ACCOUNTING |     10 |         3 |
          +--------+-------+------------+--------+-----------+
          ```

          ```mysql
          20. 列出最低薪金大于1500的各种工作及从事此工作的全部雇员人数。
          按照工作岗位分组求最小值
          select job, count(*) from emp group by job having min(sal) > 1500;
          +-----------+----------+
          | job       | count(*) |
          +-----------+----------+
          | MANAGER   |        3 |
          | ANALYST   |        2 |
          | PRESIDENT |        1 |
          +-----------+----------+
          ```

          ```mysql
          21.列出在部门"SALES"<销售部>工作的员工的姓名，假定不知道销售部的部门编号。
          select ename from emp where deptno = (select deptno from dept where dname = 'SALES');
          +--------+
          | ename  |
          +--------+
          | ALLEN  |
          | WARD   |
          | MARTIN |
          | BLAKE  |
          | TURNER |
          | JAMES  |
          +--------+
          ```

          ```mysql
          22. 列出薪金高于公司平均薪金的所有员工，所在部门，上级领导，雇员的工资等级。
          select
          	e.ename '员工', d.dname, l.ename '领导', s.grade
          from 
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          left join
          	emp l
          on
          	e.mgr = l.empno
          join
          	salgrade s
          on
          	e.sal between s.losal and s.hisal
          where
          	e.sal > (select avg(sal) from emp);
          +-------+------------+-------+-------+
          | 员工  | dname      | 领导  | grade |
          +-------+------------+-------+-------+
          | FORD  | RESEARCH   | JONES |     4 |
          | SCOTT | RESEARCH   | JONES |     4 |
          | CLARK | ACCOUNTING | KING  |     4 |
          | BLAKE | SALES      | KING  |     4 |
          | JONES | RESEARCH   | KING  |     4 |
          | KING  | ACCOUNTING | NULL  |     5 |
          +-------+------------+-------+-------+
          ```

          ```mysql
          23. 列出与"SCOTT"从事相同工作的所有员工及部门名称
          select job from emp where ename = 'SCOTT';
          +---------+
          | job     |
          +---------+
          | ANALYST |
          +---------+
          select
          	e.ename, e.job, d.dname
          from 
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          where
          	e.job = (select job from emp where ename = 'SCOTT')
          and
          	e.ename <> 'SCOTT';
          +-------+---------+----------+
          | ename | job     | dname    |
          +-------+---------+----------+
          | FORD  | ANALYST | RESEARCH |
          +-------+---------+----------+
          ```

          ```mysql
          24. 列出薪金等于部门30中员工的薪金的其他员工的姓名和薪金。
          select distinct sal from emp where deptno = 30;
          +---------+
          | sal     |
          +---------+
          | 1600.00 |
          | 1250.00 |
          | 2850.00 |
          | 1500.00 |
          |  950.00 |
          +---------+
          select
          	ename, sal
          from
          	emp
          where
          	sal in (select distinct sal from emp where deptno = 30)
          and
          	deptno <> 30;
          
          Empty set(0.00 sec)
          ```

          ```mysql
          25. 列出薪金高于在部门30工作的所有员工的薪金的员工姓名和薪金，部门名称。
          select max(sal) from emp where deptno = 30;
          +----------+
          | max(sal) |
          +----------+
          |  2850.00 |
          +----------+
          select 
          	e.ename, e.sal, d.dname
          from
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno
          where
          	e.sal > (select max(sal) from emp where deptno = 30);
          +-------+---------+------------+
          | ename | sal     | dname      |
          +-------+---------+------------+
          | JONES | 2975.00 | RESEARCH   |
          | SCOTT | 3000.00 | RESEARCH   |
          | KING  | 5000.00 | ACCOUNTING |
          | FORD  | 3000.00 | RESEARCH   |
          +-------+---------+------------+
          ```

          ```mysql
          26. 列出在每个部门工作的员工数量，平均工资和平均服务期限。没有员工的部门，部门人数是0
          select
          	d.*, count(e.ename), ifnull(avg(e.sal),0) as avgsal, ifnull(avg(timestampdiff(YEAR, hiredate, now())), 0) as avgservicetime
          from
          	emp e
          right join
          	dept d
          on
          	e.deptno = d.deptno
          group by
          	d.deptno, d.dname, d.loc;
          +--------+------------+----------+----------------+-------------+----------------+
          | DEPTNO | DNAME      | LOC      | count(e.ename) | avgsal      | avgservicetime |
          +--------+------------+----------+----------------+-------------+----------------+
          |     10 | ACCOUNTING | NEW YORK |              3 | 2916.666667 |        39.0000 |
          |     20 | RESEARCH   | DALLAS   |              5 | 2175.000000 |        37.2000 |
          |     30 | SALES      | CHICAGO  |              6 | 1566.666667 |        39.5000 |
          |     40 | OPERATIONS | BOSTON   |              0 |    0.000000 |         0.0000 |
          +--------+------------+----------+----------------+-------------+----------------+
          
          ```

          ```mysql
          27. 列出所有员工的姓名、部门名称和工资。
          select
          	e.ename, d.dname, e.sal
          from
          	emp e
          join
          	dept d
          on
          	e.deptno = d.deptno;
          +--------+------------+---------+
          | ename  | dname      | sal     |
          +--------+------------+---------+
          | SMITH  | RESEARCH   |  800.00 |
          | ALLEN  | SALES      | 1600.00 |
          | WARD   | SALES      | 1250.00 |
          | JONES  | RESEARCH   | 2975.00 |
          | MARTIN | SALES      | 1250.00 |
          | BLAKE  | SALES      | 2850.00 |
          | CLARK  | ACCOUNTING | 2450.00 |
          | SCOTT  | RESEARCH   | 3000.00 |
          | KING   | ACCOUNTING | 5000.00 |
          | TURNER | SALES      | 1500.00 |
          | ADAMS  | RESEARCH   | 1100.00 |
          | JAMES  | SALES      |  950.00 |
          | FORD   | RESEARCH   | 3000.00 |
          | MILLER | ACCOUNTING | 1300.00 |
          +--------+------------+---------+	
          ```
          
          ```mysql
          28. 列出所有部门的详细信息和人数
          select
          	d.deptno, d.dname, d.loc, count(e.ename)
          from
          	emp e
          right join
          	dept d
          on
          	e.deptno = d.deptno
          group by
          	d.deptno, d.dname, d.loc;
          +--------+------------+----------+----------------+
          | deptno | dname      | loc      | count(e.ename) |
          +--------+------------+----------+----------------+
          |     10 | ACCOUNTING | NEW YORK |              3 |
          |     20 | RESEARCH   | DALLAS   |              5 |
          |     30 | SALES      | CHICAGO  |              6 |
          |     40 | OPERATIONS | BOSTON   |              0 |
          +--------+------------+----------+----------------+
          ```
          
          ```mysql
          29. 列出各种工作的最低工资及从事此工作的雇员姓名
          select
          	job,min(sal) as minsal
          from
          	emp
          group by
          	job;
          +-----------+---------+
          | job       | minsal  |
          +-----------+---------+
          | CLERK     |  800.00 |
          | SALESMAN  | 1250.00 |
          | MANAGER   | 2450.00 |
          | ANALYST   | 3000.00 |
          | PRESIDENT | 5000.00 |
          +-----------+---------+
          
          select
          	e.ename, t.*
          from
          	emp e
          join
          	(select
          	job,min(sal) as minsal
          from
          	emp
          group by
          	job) t
          on
          	e.job = t.job and e.sal = t.minsal;
          +--------+-----------+---------+
          | ename  | job       | minsal  |
          +--------+-----------+---------+
          | SMITH  | CLERK     |  800.00 |
          | WARD   | SALESMAN  | 1250.00 |
          | MARTIN | SALESMAN  | 1250.00 |
          | CLARK  | MANAGER   | 2450.00 |
          | SCOTT  | ANALYST   | 3000.00 |
          | KING   | PRESIDENT | 5000.00 |
          | FORD   | ANALYST   | 3000.00 |
          +--------+-----------+---------+
          ```
          
          ```mysql
          30.列出各个部门的MANAGER(领导)的最低薪金
          select
          	deptno, min(sal)
          from
          	emp
          where
          	job = 'MANAGER'
          group by
          	deptno;
          +--------+----------+
          | deptno | min(sal) |
          +--------+----------+
          |     20 |  2975.00 |
          |     30 |  2850.00 |
          |     10 |  2450.00 |
          +--------+----------+
          ```
          
          ```mysql
          31. 列出所有员工的年工资，按年薪从低到高排序
          select
          	ename, (sal + ifnull(comm, 0))*12 as yearsal
          from
          	emp
          order by
          	yearsal asc;
          +--------+----------+
          | ename  | yearsal  |
          +--------+----------+
          | SMITH  |  9600.00 |
          | JAMES  | 11400.00 |
          | ADAMS  | 13200.00 |
          | MILLER | 15600.00 |
          | TURNER | 18000.00 |
          | WARD   | 21000.00 |
          | ALLEN  | 22800.00 |
          | CLARK  | 29400.00 |
          | MARTIN | 31800.00 |
          | BLAKE  | 34200.00 |
          | JONES  | 35700.00 |
          | SCOTT  | 36000.00 |
          | FORD   | 36000.00 |
          | KING   | 60000.00 |
          +--------+----------+
          ```
          
          ```mysql
          32. 求出员工领导的薪水超过3000的员工名称与领导
          select
          	a.ename '员工', b.ename '领导'
          from
          	emp a
          join
          	emp b
          on
          	a.mgr = b.empno
          where
          	b.sal > 3000;
          +-------+------+
          | 员工  | 领导 |
          +-------+------+
          | JONES | KING |
          | BLAKE | KING |
          | CLARK | KING |
          +-------+------+
          ```
          
          ```mysql
          33. 求出部门名称中，带'S'字符的部门员工的工资合计、部门人数
          select
          	d.deptno, d.dname, d.loc, count(e.ename), ifnull(sum(e.sal), 0) as sumsal
          from
          	emp e
          right join
          	dept d
          on
          	e.deptno = d.deptno
          where
          	d.dname like '%S%'
          group by
          	d.deptno, d.dname, d.loc;
          +--------+------------+---------+----------------+----------+
          | deptno | dname      | loc     | count(e.ename) | sumsal   |
          +--------+------------+---------+----------------+----------+
          |     20 | RESEARCH   | DALLAS  |              5 | 10875.00 |
          |     30 | SALES      | CHICAGO |              6 |  9400.00 |
          |     40 | OPERATIONS | BOSTON  |              0 |     0.00 |
          +--------+------------+---------+----------------+----------+
          ```
          
          ```mysql
          34. 给任职日期超过30年的员工加薪10%
          update emp set sal = sal * 1.1 where timestampdiff(YEAR, hiredate, now()) > 30;
          select * from emp;
          +-------+--------+-----------+------+------------+---------+---------+--------+
          | EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
          +-------+--------+-----------+------+------------+---------+---------+--------+
          |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880.00 |    NULL |     20 |
          |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1760.00 |  300.00 |     30 |
          |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1375.00 |  500.00 |     30 |
          |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3272.50 |    NULL |     20 |
          |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1375.00 | 1400.00 |     30 |
          |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135.00 |    NULL |     30 |
          |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695.00 |    NULL |     10 |
          |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3300.00 |    NULL |     20 |
          |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500.00 |    NULL |     10 |
          |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1650.00 |    0.00 |     30 |
          |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1210.00 |    NULL |     20 |
          |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045.00 |    NULL |     30 |
          |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300.00 |    NULL |     20 |
          |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430.00 |    NULL |     10 |
          +-------+--------+-----------+------+------------+---------+---------+--------+
          ```
          
          

