## 第一章

------

1. C++中有指针，Java中屏蔽了指针的概念
2. Java底层是C++实现的
3. Java有自动垃圾回收机制有关，简称GC机制。
4. Java能够实现跨平台、跨系统的原因在于，Java代码都运行在Java虚拟机上(JVM),而Java虚拟机再和不同的操作系统打交道。(相当于windows上安装虚拟机去运行linux)
5. Java程序的运行包括两个阶段：

- 编译阶段(主要任务是用javac检查Java源程序是否符合Java语法，符合语法则能生成字节码文件xxx.class)，编译结束之后，可以将class文件拷贝到其他操作系统当中运行。语法是：javac xxx.java

- 运行阶段：

  ![image-20210113223038898](https://i.loli.net/2021/01/13/cl6PFwjxYtN42LI.png)

  y语法是：java 类名，注意java命令后面跟的不是文件路径，而是前面编译阶段生成的类的名字。

6. 注释：(1)单行注释 // 

​                 (2)多行注释 /*......*/ 

​                 (3) javadoc注释 

![image-20210113223126168](https://i.loli.net/2021/01/13/AFDk2NsdMEqJ69X.png)

```java
//java代码格式
public class IdentifierTest01  //IdentifierTest01是一个类名，名字可以修改
{
​	//main是一个方法名
    public static void main(String[] args){   //args是一个变量名
    
​	}
    // doSome 就是方法名
    public static void doSome(){
        // i就是变量名
        int i = 10
    }
}
```

## 第二章

------

1. 关于java语言当中的标识符

   - 什么是标识符？

     - 在java源程序中凡是程序猿有权利自己命名的单词都是标识符

     - 标识符可以是什么元素呢？

       * 类名

       * 方法名

       * 变量名

       * 接口名

       * 常量名

         ......

   - 标识符的命名规则？

     - 一个合法的标识符只能由数字、字符、下划线、美元符号组成，不能包含其他符号
     - 不能由数字开头
     - 严格区分大小写
     - 关键字不能做标识符
     - 理论上无长度限制

   - 标识符的命名规范？

     * 最好见名知意

       ```java
       public class UserService{
           public void login(String username, String password){
               
           }
       }
       ```

     * 遵守驼峰命名方式

     * 类名、接口名：首字母大写，后面每个单词首字母大写

     * 变量名、方法名：首字母小写，后面每个单词首字母大写

     * 常量名：全部大写

       ```java
       SystemService
       UserService
       CustomerService
       ```

2. 字面值

   * 10、100
   * 3.14
   * "abc"
   * 'a'
   * true、false
   * 字面值就是数据、数据在编程语言中是有类型的，包括整数型、浮点型、布尔型、字符串型、字符型。
   * java中所有的字符串型字面值必须使用双引号括起来；java中所有的字符型字面值必须使用单引号括起来

3. 变量

   1. 什么是变量？

      变量本质上说是内存中的一块空间，这块空间“有数据类型”，“有名字”，“有字面值”。

      变量包含三部分：数据类型、名称、字面值【数据】

      变量是内存中存储数据的最基本的单元。

   2. 数据类型的作用？

      不同的数据有不同的类型，不同的数据类型底层会分配不同大小的空间。

      数据类型是指程序在运行阶段应该分配多大的内存空间。

   3. 变量要求：变量中存储的具体的“数据”必须和变量的“数据类型”一致，当不一致的时候编译报错。

   4. 生命/定义变量的语法格式:

      数据类型 变量名;

      * 数据类型:int、float、double...，Java是一种强类型语言

   5. 变量声明之后怎么赋值？

      语法格式：变量名 = 字面值；

      要求：字面值的数据类型必须和变量的数据类型一致。

   6. 变量在一行上可以声明多个

      ```java
      int a, b, c;
      ```

   7. java中的变量必须先声明，再赋值，才能访问。【成员变量没有手动赋值系统会默认赋值，局部变量不会】

      ```java
      public class VarTest01 {
          static int k = 1000;
          static int f;  //成员变量
          public static void main(String[] args){
              int i;  //局部变量
              System.out.println(i);  //报错
              System.out.println(k);  //1000
              System.out.println(f);  //0
              
          }
      }
      
      ```

      ![image-20210115163218260](https://i.loli.net/2021/01/15/fSIRuwxMsQL4o6T.png)

      ```java
      public class VarTest01 {
          public static void main(String[] args){
              int i;
              i = 100;
              System.out.println(i);
          }
      }
      // 不能重复声明变量，比如不能两次int i
      ```

   8. 关于变量的分类：

      * 根据变量声明的位置来分：
        * 局部变量：在方法体当中声明的变量
        * 成员变量：在方法体外【类体之内】声明的变量

4. 数据类型

   * 数据类型：包括基本数据类型和引用数据类型

     * 基本数据类型包括四大类八小种

       * 整数型(byte, short, int, long)
       * 浮点型(float, double)
       * 布尔型(boolean)
       * 字符型(char)

     * 引用数据类型包括：类、接口、数组等【字符串不属于基本数据类型，属于引用数据类型】

       | 基本数据类型 | 占用空间大小【单位：字节】 |        取值范围        | 系统默认值 |
       | :----------: | :------------------------: | :--------------------: | :--------: |
       |     byte     |             1              |        -128~127        |     0      |
       |    short     |             2              |      -32768~32767      |     0      |
       |     int      |             4              | -2147483648~2147483647 |     0      |
       |     long     |             8              |                        |     0      |
       |    float     |             4              |                        |    0.0     |
       |    double    |             8              |                        |    0.0     |
       |   boolean    |             1              |       true/false       |   false    |
       |     char     |             2              |        0~65535         |   \u000    |

     * 整数型当中的byte类型，占用1个字节，所以byte类型的数据占用8个比特位。

     * 关于java中的数字类型，数字都是有正负之分的，所以在数字的二进制当中有一个二进制位被称为“符号位”。并且这个“符号位”在所有二进制位的最左边，0表示正数，1表示负数。

   * byte类型最大值：01111111 = 【10000000(二进制) - 1】 = $2^7-2=127$, 最小值是-128，可以表示256个不同的数字。

     * 在ASCII编码中，'a'→97，'A'→65，'0'→48.，Java采用unicode编码。

       | 编码方式 |        具体种类        |            适用语言             |
       | :------: | :--------------------: | :-----------------------------: |
       |  ASCII   |                        |              英语               |
       |   ISO    |       ISO-8859-1       | 西欧语言，兼容ASCII，不支持中文 |
       |   GBK    | GB2312 < GBK < GB18030 |            简体中文             |
       |   big5   |                        |            繁体中文             |
       | unicode  |  UTF-8 UTF-16 UTF-32   |            所有语言             |

       

     * 大容量转换成小容量(比如int转byte)是需要添加强制类型转换符的，但是有一个特例，当一个整数型字面值没有超出byte，short， char类型的取值范围时，该字面值可以直接赋值给byte，short，char类型的变量。【注意是整数型字面值，而不是表达式】

     * 计算机二进制有三种表示形式：原码、反码、补码。计算机在任何情况下底层表示和存储数据的时候采用了补码形式。正数的补码和原码相同，负数的补码：负数的绝对值对应的二进制码所有二进制位取反，再加1.

   * 运算符

     * 逻辑运算符：

       |            |                                      |
       | :--------: | :----------------------------------: |
       |  &逻辑与   |                                      |
       |   逻辑或   |                                      |
       |  ！逻辑非  |                                      |
       | ^逻辑异或  |  两边的算子只要不一样，结果就是true  |
       |  &&短路与  | 与逻辑与结果一样，只不过存在短路现象 |
       | \|\|短路或 | 与逻辑或结果一样，只不过存在短路现象 |

       ```java
       public class OperatorTest03{
           public static void main (String [] args){
               int x = 10;
               int y = 8;
               # 逻辑与
               System.out.println(x < y & ++x < y);
               System.out.println(x);    //x = 11
               
               # 短路与
               System.out.println(x < y && ++x < y);
               System.out.println(x);     //x = 10
               
           }
       }
       ```

     * 三元运算符/三目运算符/条件运算符

       * 语法规则：

         ​	布尔表达式？表达式1：表达式2

       * 三元运算符的执行原理：

         ​	当布尔表达式的结果是true时，选择表达式1作为整个表达式的执行结果

         ​	当布尔表达式的结果是false时，选择表达式2作为整个表达式的执行结果

       ```java
       public class OperatorTest03{
           public static void main(String[] args){
               boolean sex = false;
               char c = (sex ? '男' : '女')'；
               System.out.println(c);
           }
       }
       ```

   * 控制语句if，switch，for，while，dowhile

     ```java
     public class KeyInputTest{
         public static void main(String[] args){
             //第一步，创建键盘扫描器对象
             java.util.Scanner s = new java.util.Scanner(System.in);
             //第二步，调用Scanner对象的next()方法开始接收用户键盘输入
             String userInputContent = s.next();
             int num = s.nextInt();   //只能输入int类型
         }
     }
     ```

     ```java
     public class IfTest{
         public static void main(String[] args){
             boolean sex = true;
             if(sex){
                 System.out.println("男");
             }else{
                 System.out.println("女");
             }
         }
     }
     //java里的if语句后面没有冒号：
     ```

     ```java
     public class SwitchTest{
         public static void main(String[] args){
             java.util.Scanner s = new java.util.Scanner(System.in);
             System.out.print("请输入数字:");
             int num = s.nextInt();
             switch (num){
                 case 1 :
                     System.out.println("星期一");
                     break;
                 case 2 :
                     System.out.println("星期二");
                     break;
                 case 3 :
                     System.out.println("星期三");
                     break;
                 case 4 :
                     System.out.println("星期四");
                     break;
                 case 5 :
                     System.out.println("星期五");
                     break;
                 case 6 :
                     System.out.println("星期六");
                     break;
                 case 7 :
                     System.out.println("星期日");
                     break;
                 default :
                     System.out.println("对不起，您输入的数字非法!");
             }
             
             
         }
     }
     ```

     ```java
      public class ForTest{
         pulbic static void main(String[] args){
             for(int i = 1; i <= 10; i = i + 1){
                 System.out.println(i);
             }
         }
     }
     ```

     ```java
     public class WhileTest{
         public static void main(String[] args){
             int i = 10;
             int j = 3;
             while(i > j){
                 System.out.println("呵呵");
             }
         }
     }
     ```

     ```java
     public class DoWhileTest{
         public static void main(String[] args){
             int i = 10;
             do{
                 System.out..println(i);
             }while(i > 100);
         }
     }
     //do while语句后面有分号，注意不要丢失
     ```

     ```java
     public class BreakTest{
         public static void main(String[] args){
             for1:for(int j=0;j<3;j++){
                 for2:for(int i=0;i<10;i++){
                     if(i == 5){
                         break for1;//终止for1循环
                     }
                 }
             }
         }
     }
     //break后可指定要终止的循环体, continue也类似
     ```

   * 方法

     * 方法的基础语法：为解决同一类问题写的代码叫方法。对应C语言中的函数。

       ```java
       public class MethodTest{
           public static void main(String[] args){
               MethodTest.sumInt(10,20);
               MethodTest.sumInt(666,888);  
               //在同一个类中，类名可以省略不写，上面的可以省略写为: sumInt(666,888), 在不同类中，不可以省略
           }
           public static void sumInt(int a, int b){
               int c = a + b;
               System.out.println(a + " + " + b + " = " + c);
           }
       }
       // 没有返回值时，返回值类型位置必须写void关键字(当然也可以写为return;)，有返回值时类型位置需要和返回值类型一致。
       ```

     * 方法在执行过程中，在JVM中的内存是如何分配的呢？

       * 方法只定义，不调用，是不会执行的，并且JVM中也不会给该方法分配"运行所属"的内存空间，只有在调用这个方法的时候，才会动态地给这个方法分配所属的内存空间。
       * 在JVM内存划分上有这样三块主要的内存空间(当然除了这三块之外还有其他的内存空间)。方法区内存、堆内存、栈内存。①方法代码片段属于.class字节码文件的一部分，字节码文件在类加载的时候，将其放到了**方法区**当中。所以JVM中的三块主要的内存空间中方法区内存最先有数据，存放了代码片段。代码片段虽然在方法区内存中只有一份，但可以被重复调用。每一次调用这个方法的时候，需要给该方法分配独立的活动场所，在**栈内存**中分配。  

     * 方法重载机制：当有很多功能不同，但是功能很相似时，可以将这些相似的方法进行合并，从而使得相似的需求只使用同一个方法，而不用多次重复定义方法。Java支持方法重载机制，但JavaScript不支持方法重载机制。

       -  什么时候考虑使用重载？-功能相似的时候，尽可能让方法名相同。但是：功能不同/不相似的时候，尽可能让方法名不同。
       -  什么条件满足之后构成了方法重载？1在同一个类当中 2方法名相同 3参数列表不同(数量不同、顺序不同、类型不同)
       -  方法重载和什么有关系和什么没有关系？1方法重载和方法名+参数列表有关系 2方法重载和返回值类型无关

       ```java
       public class OverloadTest{
           public static void main(String[] args){
               //调用方法的时候就像在使用一个方法一样
               //参数的类型不同，对应调用的方法不同。
               //此时区分方法不再依靠方法名了，依靠的是参数的数据类型。
               System.out.println(sum(1,2));
               System.out.println(sum(1.0,2.0));
               System.out.println(sum(1L,2L));
           }
           public static int sum(int a, int b){
               return a + b;
           }
           public static long sum(long a, long b){
               return a + b;
           }
           public static double sum(double a, double b){
               return a + b;
           }
       }
       ```

       ```java
       public class OverloadTest{
           public static void main(String[] args){
               U.p(10);
               U.p(false);
               U.p("abc");
               U.p(3.0)
           }
       }
       class U{
           public static void p(byte b){
               System.out.println(b);
           }
           public static void p(short b){
               System.out.println(b);
           }
           public static void p(int b){
               System.out.println(b);
           }
           public static void p(long b){
               System.out.println(b);
           }
           public static void p(float b){
               System.out.println(b);
           }
           public static void p(double b){
               System.out.println(b);
           }
           public static void p(boolean b){
               System.out.println(b);
           }
           public static void p(char b){
               System.out.println(b);
           }
           public static void p(String b){
               System.out.println(b);
           }
       }
       ```

   * 递归

     ```java
     public class RecursionTest04{
         public static void main(String[] args){
             int n = 5;
             int retValue = method(n);
             System.out.println(retValue);
         }
         
         public static int method(int n){
             if (n == 1){
                 return 1;
             }
             return n * method(n-1);
         }
     }
     ```

     



## 第三章

------

1. 面向过程和面向对象的区别：

   - 面向过程主要关注的点是实现的具体过程和因果关系
     -  优点：对于业务逻辑比较简单的程序，可以达到快速开发，前期投入成本较低
     -  缺点：采用面向过程的方式开发很难解决非常复杂的业务逻辑，另外面向过程的方式导致软件元素之间的“耦合度”非常高，只要其中一环出问题，整个系统受到影响，导致最终的软件扩展力差。另外，由于没有独立体的概念，所以没有组件复用性的功能。
   - 面向对象主要关注点是对象【独立体】能完成哪些功能，即分模块。
     -  优点：耦合度低，扩展力强。更容易解决现实世界中更复杂的业务逻辑，组件复用性强。
     -  缺点：前期投入成本较高，需要进行独立体的抽取，大量的系统分析与设计。
   - C语言是纯面向过程的、C++是半面向对象、Java是纯面向对象。JavaScript是基于对象

2. 面向对象的三大特征：

   - 封装

   - 继承

   - 多态

     所有面向对象的编程语言都有这三大特征。

     采用面向对象的方式开发一个软件，生命周期当中：

     -  面向对象的分析：OOA
     -  面向对象的设计：OOD
     -  面向对象的编程：OOP

3. 类和对象的概念：

   -  类：类在现实世界并不存在，是一个模板、概念，是人类大脑思考抽象的结果。类代表了一类事物，在现实世界中，对象A与对象B之间具有共同特征，进行抽象总结出一个模板，这个模板被称为类。
   -  对象：对象在是际存在的个体。
   -  描述一下整个软件开发的过程：程序员先观察现实世界，从现实世界当中寻找对象，寻找了N多个对象之后，发现所有的对象都有共同特征，程序员在大脑中形成了一个模板【类】，Java程序员可以通过java代码来表述一个类，于是Java程序中有了类的定义。然后通过类就可以创建对象。有了对象之后，可以让对象直接协作起来形成一个系统。
   -  类--【实例化】→对象，对象又被称为实例instance
   -  对象--【抽象】→类
   -  类包括属性【描述对象的状态信息】和方法【描述对象的动作信息】
   -  java语言中所有的class都属于引用数据类型【还有一种基本数据类型】

4. 对象的创建和使用：

   ```java
   public class Student{
       int no;
       int age;
       String name;
       boolean sex;
       String addr;
   }
   public class OOTest{
      public static void main(String[] args){
          //通过一个类可以实例化N个对象
          //实例化对象的语法:new 类名();
          //new是java语言当中的一个运算符
          //new运算符的作用是创建对象，在JVM堆内存当中开辟新的内存空间
          //方法区内存：在类加载的时候，class字节码代码片段被加载到该内存空间当中。
          //栈内存(局部变量)：方法代码片段执行的时候，会给该方法分配内存空间，在栈内存中压栈。
          //堆内存：new的对象在堆内存中存储
          //Student是一个引用数据类型
          //s是一个变量名
          //new Student()是一个学生对象
          //s是一个局部变量【在栈内存中存储】
          //什么是对象？new运算符在堆内存中开辟的内存空间称为对象。
          //什么是引用？引用是一个变量， 只不过这个变量中保存了另一个java对象的内存地址。
          Student s = new Student();
          //java语言中，程序员不能直接操作堆内存，java中没有指针，不像C语言。
          //java语言中，程序员只能通过"引用"去访问堆内存当中的对象内部的实例变量。
          
          s.no = 10;
          s.name = "jack";
          s.age = 20;
          s.sex = true;
          s.addr = "北京";
          
          int stuNo = s.no;
          String stuName = s.name;
          int stuAge = s.age;
          boolean stuSex = s.sex;
          String stuAddr = s.addr;
          
          System.out.println("学号 = " + stuNo);
          System.out.println("姓名 = " + stuName);
          System.out.println("年龄 = " + stuAge);
          System.out.println("性别 = " + stuSex);
          System.out.println("住址 = " + stuAddr);
      }
   
   }
   ```

   ```java
   public class Address{
       //以下都是成员变量之实例变量
       String city;
       String street;
       String zipcode;
   }
   public class User{
       //以下都是成员变量之实例变量
       int no;
       String name;
       Address addr;
   }
   public class OOTest{
       public static void main(String[] args){
           User u = new User();
           //输出User对象内部实例变量的值
           System.out.println(u.no);//0
           System.out.println(u.name);//null
           System.out.println(u.addr);//null
           
           //修改User对象内部实例变量的值
           u.no = 110;
           u.name = "jack";
           u.addr = new Address();
           
           System.out.println(u.name + "居住在哪个城市: " + u.addr.city);
       }
   }
   //引用是一个变量，可以是局部变量，也可以是实例变量。
   ```

   ```java
   public class Address{
       //以下都是成员变量之实例变量
       String city;
       String street;
       String zipcode;
   }
   public class User{
       //以下都是成员变量之实例变量
       int no;
       String name;
       Address addr;
   }
   public class OOTest{
       public static void main(String[] args){
           User u = new User();
           Address a = new Address();
           u.addr = a;
           System.out.println(u.addr.city);//null
           a.city = "天津";
           System.out.println(u.addr.city);//天津
       }
   }
   ```

   ------

   ```java
   public class Husband{
       String name;
       Wife w;
   }
   public class Wife{
       String name;
       Husband h;
   }
   public class OOTest{
       public static void main(String[] args){
           //创建一个丈夫对象
           Husband huangXiaoMing = new Husband();
           huangXiaoMing.name = "黄晓明";
           //创建一个妻子对象
           Wife baby = new Wife();
           baby.name = "baby";
           //结婚【能通过丈夫找到妻子，通过妻子也可以找到丈夫】
           huangXiaoMing.w = baby;
           baby.h = huangXiaoMing;
           //得到以上"黄晓明"的妻子的名字
           System.out.println(huangXiaoMing.name + "的妻子名字叫：" + huangXiaoMing.w.name);
           
           
       }
   }
   ```

   ![G:image-20210223172053568](G:image-20210223172053568.png)

   ```java
   public class OOTest{
       public static void main(String[] args){
           Customer c = new Customer();
           System.out.println(c.id);
           c = null;
           System.out.println(c.id);//会报错：java.lang.NullPointerException
           //编译可以通过，因为符合语法，但 空引用访问"实例"相关的数据一定会出现空指针异常。
       }
   }
   ```

5. ![G:image-20210224213136511](https://i.loli.net/2021/03/04/mZXCS7xNgDPJUyV.png)

   区分一下java中类、对象和属性、方法：

   java中，类是对一组具有相同特征和行为的对象的抽象描述。

   对象是类的具体实现，表示一个独立的、唯一的个体。对象通过类生成，对象一定具备该类的特征和行为。

   类或对象的行为称为方法。可以理解为：一个对象在类中可以做很多东西，能做什么在类里就叫做方法。例如，定义一个猫类，猫类中有一个对象加菲猫，加菲猫可以做很多事情，比如吃、喝、睡觉，这些在类中就称为方法。【对象中包含方法】

6. 封装机制

   - 封装的好处：(1) 封装之后，对于那个事物来说，看不到这个事物比较复杂的那一面，只能看到该事物简单的那一面。复杂性封装，对外提供简单的操作入口。(2) 封装之后才会形成真正的"对象"，真正的"独立体"。(3) 封装就意味着以后的程序可以重复使用，并且这个事物应该适应性比较强，在任何场合都可以使用。(4) 封装之后，对于事物，提高了安全性。

   - 封装的步骤：

     1. 所有属性私有化，使用private关键字进行修饰，private表示私有的，修饰的所有数据智能在本类中访问。

     2. 对外提供简单的操作入口，也就是说以后外部程序要想访问age属性，必须通过这些简单的入口进行访问：对外提供两个公开的方法，分别是set方法和get方法：想修改age属性，调用set方法；想读取age属性，调用get方法。在set方法和get方法执行过程中可以进行安全过滤。

     3. set方法的命名规范：

        ```java
        public void setAge(int a){
            age = a;
        }
        ```

        get方法的命名规范：

        ```java
        public int getAge(){
            return age;
        }
        ```

        【setter and getter方法没有static关键字。有static关键字修饰的方法调用：类名.方法名(实参); 没有static关键字修饰的方法调用:引用.方法名(实参);】

     4. 案例

        ```java
        package com.bjpowernode.javase;
        
        public class Customer {
            private int id;
            private String name;
            private int age;
            private String addr;
        
            public int getId() {
                return id;
            }
        
            public void setId(int id) {
                this.id = id;
            }
        
            public String getName() {
                return name;
            }
        
            public void setName(String name) {
                this.name = name;
            }
        
            public int getAge() {
                return age;
            }
        
            public void setAge(int age) {
                this.age = age;
            }
        
            public String getAddr() {
                return addr;
            }
        
            public void setAddr(String addr) {
                this.addr = addr;
            }
        
        
        
        
        }
        
        ```

        ```java
        package com.bjpowernode.javase;
        
        public class CustomerTest {
            public static void main(String[] args) {
                Customer c = new Customer();
        
                //私有的属性不能在外部直接访问，这就是封装
                //c.id = 410;
        
                //操作入口变成了只能通过set和get方法进行访问
                //在set方法和get方法执行过程中可以进行安全过滤。
                c.setId(100);
                c.setName("zhangsan");
                c.setAge(50);
                c.setAddr("北京大兴区");
        
                System.out.println(c.getId());
                System.out.println(c.getName());
                System.out.println(c.getAge());
                System.out.println(c.getAddr());
            }
        }
        
        ```

7. 构造方法

   - 构造方法又被称为构造函数/构造器/Constructor

   - 构造方法语法结构:

     ```java
     [修饰符列表] 构造方法名(形式参数列表){
         构造方法体;
     }
     ```

   - 普通方法语法结构:

     ```java
     [修饰符列表] 返回值类型 方法名(形式参数列表){
         方法体;
     }
     ```

   - 对于构造方法来说，返回值类型不需要指定，并且也不能写void，只要写上void，就变成普通方法了。

   - 对于构造方法来说，构造方法的方法名必须和类名保持一致。

   - 构造方法的作用：(1) 通过构造方法的调用，可以创建对象。(2) 创建对象的同时，初始化实例变量的内存空间。

   - 构造方法的调用：

     -  普通方法的调用：方法修饰符中有static的时候:类名.方法名(实参列表)、方法修饰符列表中没有static的时候:引用.方法名(实参列表)
     -  new 构造方法名(实参列表)

   - 每一个构造方法实际上执行结束之后都有返回值，但是这个"return 值;"这样的语句不需要写。并且返回值类型是构造方法所在类的类型。由于构造方法的返回值类型就是类本身，所以返回值类型不需要编写。

   - 当一个类中没有定义任何构造方法的话，系统默认给该类提供一个无参数的构造方法，这个构造方法被称为缺省构造器。

   - 当一个类显示的将构造方法定义出来了，那么系统则不再默认为这个类提供缺省构造器。建议开发中手动为当前类提供无参数构造方法，因为无参数构造方法太常用了。

   - 构造方法支持重载机制。

     ```java
     package com.bjpowernode.javase;
     public class ConstructorTest {
         public static void main(String[] args){
               User u1 = new User();
               User u2 = new User(10);
               //调用doSome方法,调用带有static的方法:类名.方法
               ConstructorTest.doSome();
               //doSome();
      
               //调用doOther方法，调用没有static的方法:引用.方法
               ConstructorTest t = new ConstructorTest();
               t.doOther();
          }
      
          public static void doSome(){
              System.out.println("do some!");
          }
      
          public void doOther(){
              System.out.println("do other");
          }
      }
     ```

      ```java
      package com.bjpowernode.javase;
      
      public class Account {
      
          //账号
          private String actno;
      
          //余额
          private double balance;
      
          public String getActno() {
              return actno;
          }
      
          public void setActno(String actno) {
              this.actno = actno;
          }
      
          public double getBalance() {
              return balance;
          }
      
          public void setBalance(double balance) {
              this.balance = balance;
          }
      
          //无参数构造器
          public Account(){
      
          }
          //有参数构造器
          public Account(String s){
              actno = s;
          }
          public Account(double d){
              balance = d;
          }
          public Account(String s, double d){
              actno = s;
              balance = d;
          }
      }
      
      ```

      ```java
      package com.bjpowernode.javase;
      
      public class ConstructorTest02 {
          public static void main(String[] args) {
              Account act1 = new Account();
      //        act1.setActno("111");
              System.out.println("账号：" + act1.getActno());
              System.out.println("余额：" + act1.getBalance());
      
              Account act2 = new Account("110");
      //        act1.setActno("111");
              System.out.println("账号：" + act2.getActno());
              System.out.println("余额：" + act2.getBalance());
      
              Account act3 = new Account("act-001", 10000);
      //        act1.setActno("111");
              System.out.println("账号：" + act3.getActno());
              System.out.println("余额：" + act3.getBalance());
          }
      }
      ```


​     

8. 对象和引用：

   - 对象：目前在使用new运算符在堆内存中开辟的内存空间称为对象。

   - 引用：是一个变量，不一定是局部变量，还可能是成员变量[全局变量]，引用保存了内存地址，指向了堆内存当中的对象。

   - 所有访问实例相关的数据，都需要通过"引用."的方式访问，因为只有通过引用才能找到对象。

   - 只有一个空的引用，访问对象的实例相关的数据会出现空指针异常。

     ```java
     class Student{
         Computer com; // com是一个引用【成员变量中的实例变量】
         static String country = "CN";//静态的成员变量，类变量
         
         public static void doSome(){
             Computer cc; // cc是一个引用【局部变量】
         }
     }
     ```

     ```java
     package study02;
     
     public class Test {
     	private int a;//成员变量
     	private static String str;//静态变量（类变量）
     	
     	public int print(){
     		int b=2;//局部变量
     		return b;
     	}
     	public static void main(String[] args) {
     		Test test=new Test();
     		System.out.println(Test.str);//调用类变量
     		System.out.println(test.str);//调用成员变量
     		System.out.print(test.print());//打印局部变量
     	}
     	//此处变量都使用private修饰而不使用public是为了减少代码的耦合。
     }
     ```

     【- 成员变量：把类内、方法体外定义的变量称为成员变量

     ​    - Java中的成员变量分给两种：(1) 没有static修饰的，这些成员变量是对象中的成员，称为实例变量。(2) 有static修饰的，称为类变量，也叫静态变量。类变量随着类的加载而存在于方法区中。实例变量随着对象的建立而存在于堆内存中。】

9. 参数的传递

   java中方法调用的时候涉及到参数传递的问题，参数传递实际上传递的是**变量中保存的具体值**。只不过这个值有时候是一个字面值，有时候是另一个java对象的内存地址。

   ```java
   package com.bjpowernode.javase;
   
   public class Test01 {
       public static void main(String[] args) {
           int i = 10;
           add(i);
           System.out.println("main -->" + i);
       }
   
       public static void add(int i){ //这里i只是一个形参而已
           i++;
           System.out.println("add --> " + i);
       }
   }
   //add --> 11
   //main -->10
   ```

   ![image-20210303110438395](https://i.loli.net/2021/03/04/oEPqXAZfGyani2R.png)

   ​    

   ```java
   package com.bjpowernode.javase;
   
   public class Test02 {
       public static void main(String[] args) {
           User u = new User(20);
           add(u); //此处的u保存的是创建的对象的内存地址
           System.out.println("main-->" + u.age);
       }
       public static void add(User u){
           u.age++;
           System.out.println("add-->" + u.age);
       }
   }
   
   class User{
       int age;
       public User(int i){
           age = i;
       }
   }
   //add-->21
   //main-->21
   ```

   > 上面两段代码有一点不一样，第一段代码i中存放的是个字面值10【基本数据类型】，而第二段代码中u中存放的是创建的对象User的地址【引用数据类型】。

   ![image-20210303154517012](https://i.loli.net/2021/03/04/SpIciAUHMoNtwrv.png)

10. this关键字

    this是一个引用，是一个变量，this变量中保存了内存地址指向了**自身**，this存储在JVM堆内存java对象内部。创建100个java对象，每一个对象都有this，也就是说有100个不同的this.

    this可以出现在"实例方法"当中，指向当前正在执行这个动作的对象。

    this不能使用在带有static的方法当中。

    ![image-20210303162547509](https://i.loli.net/2021/03/04/7yNi5M8bSYvAneC.png)

    ```java
    package com.bjpowernode.javase;
    
    public class Customer {
        String name;
    
        //构造方法
        public Customer(){
    
        }
    
        //不带有static关键字的一个方法
        //顾客购物的行为
        //每一个顾客购物最终的结果不一样，所以购物行为属于对象级别的行为，由于每个对象在执行购物动作时最终结果不同，所以购物这个动作必须有“对象”的参与
        //重点：没有static关键字的方法被称为“实例方法”，实例方法访问方式："引用."
        //重点：没有static关键字的变量被称为“实例变量”
        //注意：当一个行为/动作执行的过程中需要对象参与，那么这个方法一定要定义为“实例方法”，不要带有static关键字
    
        //以下方法定义为实例方法，因为每一个顾客在真正购物的时候，最终结果是不同的。
        public void shopping(){
            System.out.println(this.name + "在购物！");  /*this就代表当前正在执行这个动作的对象*/
        }
        
        //带有static
        public static void doSome(){
            //这个执行过程中没有“当前对象”，因为带有static的方法是通过类名的方式访问的
            //或者说这个“上下文”当中没有“当前对象”，自然也不存在this(this代表的是当前正在执行这个动作的对象)
    
            //以下程序为什么编译错误？
            //doSome方法调用不是对象去调用， 而是一个类名去调用，执行过程中没有“当前对象”
            //name是一个“实例变量”，以下代码的含义是：访问当前对象的name，没有当前对象，自然也不能访问当前对象的name
            System.out.println(Customer.name);//编译报错
            
            //那如何调用name实例变量？
            Customer c = new Customer();
            System.out.println(c.name);
        }
    }
    
    package com.bjpowernode.javase;
    
    public class Test03 {
        public static void main(String[] args) {
            //创建customer对象
            Customer c1 = new Customer();
            c1.name = "zhangsan";
    
            //c1购物
            c1.shopping();
    
            //再创建customer对象
            Customer c2 = new Customer();
            c2.name = "lisi";
    
            //c2购物
            c2.shopping();
    
        }
    }
    ```

    ```java
    package com.bjpowernode.javase;
    
    public class Test04 {
    
        //实例变量
        int num = 10;
    
        public static void main(String[] args) {
    //        System.out.println(num); //编译错误
    //        System.out.println(this.num); //编译错误
            //想访问num怎么办
            Test04 tt  = new Test04();
            System.out.println(tt.num);
        }
    }
    ```

    ```java
    package com.bjpowernode.javase;
    
    public class Test05 {
        public static void main(String[] args) {
            //调用doSome方法
            Test05.doSome();
    
            //调用doOther方法
            Test05 tt = new Test05();
            tt.doOther();
    
            tt.run();
    
        }
        //带有static
        public static void doSome(){
            System.out.println("do some!");
    
        }
        //实例方法
        public void doOther(){
            System.out.println("do other!");
        }
        //实例方法
        public void run(){
            System.out.println("run execute!");
            this.doOther();
            Test05.doSome();
        }
    }
    /*do some!
    do other!
    run execute!
    do other!
    do some!*/
    ```

    > 结论 ：在带有static的方法当中不能直接访问实例变量和实例方法【反过来，在实例方法中是可以调用带static的方法的】。因为实例变量和实例方法都需要对象的存在。而static的方法当中是没有this的，也就是说当前对象是不存在的，自然也是无法访问当前对象的实例变量和实例方法。

    > this什么时候不能省略？用来区分局部变量和实例变量的时候，this.不能省略

    ```java
    package com.bjpowernode.javase;
    
    public class Date {
        private int year;
        private int month;
        private int day;
    
        //构造函数
    
        /**
         * 需求：当调用以下无参数的构造方法时，默认创建的日期是1970-1-1
         */
        public Date() {
            /*
            this.year = 1970;
            this.month = 1;
            this.day = 1;
             */
            // 以上代码可以通过调用另一个构造方法来完成
            // 但前提是不能创建新的对象
            // new Date(1970,1,1)表示创建了一个全新的对象，不中
    
            //需要采用以下的语法来完成构造方法的调用
            //这种方式不会创建新的对象，但同时又可以达到调用其他的构造方法。
            this(1970,1,1);
        }
    
        public Date(int year, int month, int day) {
            this.year = year;
            this.month = month;
            this.day = day;
        }
    
        // setter and getter
        public int getYear() {
            return year;
        }
    
        public void setYear(int year) {
            this.year = year;
        }
    
        public int getMonth() {
            return month;
        }
    
        public void setMonth(int month) {
            this.month = month;
        }
    
        public int getDay() {
            return day;
        }
    
        public void setDay(int day) {
            this.day = day;
        }
    
        //对外提供一个方法可以将日期打印输出到控制台
        public void print(){
            System.out.println(this.year + "年" + this.month + "月" + this.day + "日");
        }
    
    }
    
    ```

    ```java
    package com.bjpowernode.javase;
    
    import javax.xml.crypto.Data;
    
    public class DateTest {
        public static void main(String[] args) {
            //创建日期对象1
            Date time1 = new Date();
            time1.print();
    
            //创建日期对象2
            Date time2 = new Date(2008,8,8);
            time2.print();
        }
    }
    // 1970年1月1日
    // 2008年8月8日
    ```

    > this可以用在哪里：
    >
    > 	1. 可以用在实例方法当中，代表当前对象【语法格式：this.】
    > 	2. 可以用在构造方法当中，通过当前的构造方法调用其他的构造方法【语法格式：this(实参)；】
    >
    > 重点：this()这种语法只能出现在构造函数第一行。

    ```java
    //练习
    package com.bjpowernode.javase;
    
    public class Test07 {
    
        //带有static的方法
        public static void method1(){
            //调用doSome
            //使用完整方式调用
            Test07.doSome();
            //使用省略方式调用
            doSome();
    
            //调用doOther
            //使用完整方式调用
            Test07 tt3 = new Test07();
            tt3.doOther();
            //使用省略方式调用
            Test07 tt4 = new Test07();
            tt4.doOther();
    
            //访问i
            //完整方式访问
            Test07 tt5 = new Test07();
            System.out.println(tt5.i);
            //省略方式访问
            System.out.println(tt5.i);
    
        }
        //没有static的方法
        public void method2(){
            //调用doSome
            //使用完整方式调用
            Test07.doSome();
            //使用省略方式调用
            doSome();
    
            //调用doOther
            //使用完整方式调用
            this.doOther();
            //使用省略方式调用
            doOther();
    
            //访问i
            //完整方式访问
            System.out.println(this.i);
            //省略方式访问
            System.out.println(i);
    
        }
    
        //主方法
        public static void main(String[] args) {
            //要求在这里编写程序调用method1
            //使用完整方式调用
            Test07.method1();
            //使用省略方式调用
            method1();
    
            //要求在这里编写程序调用method2
            //使用完整方式调用
            Test07 tt = new Test07();
            tt.method2();
            //使用省略方式调用
            Test07 tt2 = new Test07();
            tt2.method2();
        }
    
        //没有static的变量
        int i = 10;
    
        //带有static的方法
        public static void doSome(){
            System.out.println("do some!");
        }
    
        //没有static的方法
        public void doOther(){
            System.out.println("do other!");
        }
    }
    
    ```

    > 总结：
    >
    > 静态调用静态：不需要创建对象，类名.方法
    >
    > 静态调用实例：需要创建对象，引用.方法
    >
    > 实例调用静态：不需要创建对象，类名.方法
    >
    > 实例调用实例：不需要创建对象[已经有了]，this.方法

11. static关键字

    ```java
    package com.bjpowernode.javase;
    
    public class Chinese {
        //身份证号
        String id;
    
        //姓名
        String name;
    
        //国籍【每个对象由于都是由"Chinese类"实例化的，所以每一个中国人的国籍都是中国】
        //无论通过Chinese类实例化多少个java对象，这些java对象的国籍都是中国
        //这种设计方式有缺点，这里声明为实例变量显然不合适，太浪费内存空间，没必要让每一个对象都保留一份国籍内存。
    
        String country;
    
        //构造函数
        public Chinese(){}
    
        public Chinese(String id, String name, String country) {
            this.id = id;
            this.name = name;
            this.country = country;
        }
    }
    
    package com.bjpowernode.javase;
    
    public class ChineseTest {
        public static void main(String[] args) {
            //创建中国人对象1
            Chinese zhangsan =new Chinese("1", "张三","中国");
            System.out.println(zhangsan.country);
    
            //创建中国人对象1
            Chinese lisi =new Chinese("2", "李四", "中国");
            System.out.println(lisi.country);
        }
    }
    
    ```

    内存分析图

    ![image-20210304094143308](https://i.loli.net/2021/03/04/9gJXDyRtUOlfpia.png)

    修改后：

    ```java
    package com.bjpowernode.javase;
    
    public class Chinese {
        //身份证号
        String id;
    
        //姓名
        String name;
    
        //国籍【所有对象国籍都一样，这种特征属于类级别的特征，可以提升为整个模板的特征，可以在变量前添加static关键字修饰】
        //静态变量，在类加载时初始化，不需要创建对象，内存就开辟了。在方法区内存。
        static String country = "中国";
    
        //构造函数
        public Chinese(){}
    
        public Chinese(String id, String name) {
            this.id = id;
            this.name = name;
    
        }
    }
    
    package com.bjpowernode.javase;
    
    public class ChineseTest {
        public static void main(String[] args) {
            //创建中国人对象1
            Chinese zhangsan =new Chinese("1", "张三");
            System.out.println(Chinese.country);
    
            //创建中国人对象1
            Chinese lisi =new Chinese("2", "李四");
            System.out.println(Chinese.country);
        }
    }
    
    ```

    内存分析图

    ![image-20210304094753799](https://i.loli.net/2021/03/04/8d1ayJGXrmhKSBY.png)

    > 结论：
    >
    > 1. 什么时候成员变量声明为实例变量呢？
    >
    >    所有对象都有这个属性，但是这个属性的值会随着对象的变化而变化【不同对象的这个属性具体的值不同】
    >
    > 2. 什么时候成员变量声明为静态变量呢？
    >
    >    所有对象都有这个属性，并且所有对象的这个属性的值是一样的，建议定义为静态变量，节省内存开销。

    ------

    static关键字还可以定义"静态代码块"：

    - 语法格式:

      ```java
      static{
          java语句;
      }
      ```

    - 作用：静态代码块是java为程序员准备的一个特殊时刻，这个时刻被称为类加载时刻。若希望在此刻执行一段特殊的程序，这段程序可以直接放到静态代码块当中。通常在静态代码块中完成预备工作，先完成数据的准备工具，例如：初始化连接池，解析XML配置文件。

    实例代码块：

    - ```java
      {
          java语句
      }
      ```

    - 实例代码块在构造方法执行之前执行，构造方法执行一次，实例代码块对应执行一次。

    - 实例代码块也是java语言为程序员准备的一个特殊时机，这个特殊时机被称为：对象初始化时机。

12. 继承

    - 继承是面向对象三大特征之一【封装、继承、多态】

    - 继承的基本作用是：代码复用。但继承最重要的作用是;有了继承以后才有了“方法的覆盖”和“多态机制”。

    - 继承语法格式：

      ```java
      [修饰符列表] class 类名 extends 父类名{
          类体 = 属性 + 方法
      }
      ```

    - java语言中的继承只支持单继承，一个类不能同时继承很多类，只能继承一个类。在C++中支持多继承。

    - 虽然java语言中只支持单继承，但是一个类也可以间接继承其他类，比如C类继承B类，B类继承A类，A类继承T类，那么C类继承了T类

    - 关于继承中的一些术语：

      B类继承A类，其中：

      ​	A类称为：父类、基类、超类、superclass

      ​	B类称为：子类、派生类、subclass

      ​	java中私有的不支持继承、构造方法不支持继承、其他数据都可以被继承。

    - java语言中假设一个类没有显式地继承任何类，该类默认继承JavaSE库当中提供的java.lang.Object类。

    ```java
    例子：
    package com.bjpowernode.javase.test02;
    
    public class Account {
        private String actno;
        private double balance;
    
        public Account() {
        }
    
        public Account(String actno, double balance) {
            this.actno = actno;
            this.balance = balance;
        }
    
        public String getActno() {
            return actno;
        }
    
        public void setActno(String actno) {
            this.actno = actno;
        }
    
        public double getBalance() {
            return balance;
        }
    
        public void setBalance(double balance) {
            this.balance = balance;
        }
    }
    
    package com.bjpowernode.javase.test02;
    
    public class CreditAccount extends Account{
        private String actno;
        private double balance;
        private double credit;
    
        public CreditAccount() {
        }
    
    
        public double getCredit() {
            return credit;
        }
    
        public void setCredit(double credit) {
            this.credit = credit;
        }
    }
    
    package com.bjpowernode.javase.test02;
    
    public class ExtendsTest {
        public static void main(String[] args) {
            CreditAccount act = new CreditAccount();
            act.setActno("act-001");
            act.setBalance(-1000);
            act.setCredit(0.99);
    
            System.out.println(act.getActno() + "," + act.getBalance() + "," + act.getCredit());
        }
    }
    ```

13. 方法的覆盖

    - 回顾方法重载
      - 方法重载又称为Overload
      - 什么时候使用？党在同一个类中，方法完成的功能是相似的，建议方法名相同， 这样方便程序员的编程，就像在调用一个方法似的，代码美观。
      - 什么条件满足之后构成方法重载？
        - 在同一个类中
        - 方法名相同
        - 参数列表不同：类型、顺序、个数
      - 方法重载和什么无关？
        - 和方法的返回值类型无关
        - 和方法的修饰符列表无关
    - 方法覆盖
      - 方法覆盖又被称为方法重写：英语单词：override/overwrite
      - 什么时候使用方法重写？当父类中的方法已经无法满足当前子类的业务需求，子类有必要将父类中继承过来的方法进行重新编写，这个重新编写的过程称为方法重写/方法覆盖。
      - 代码满足什么条件之后，就构成方法的覆盖呢？
        - 方法覆盖发生在具有继承关系的父子类之间
        - 返回值类型相同，方法名相同，形参列表相同
        - 访问权限不能更低，只能更高
        - 抛出异常不能更多，可以更少
      - 注意：
        - 私有方法不能继承，所以不能覆盖
        - 构造方法不能继承，所以不能覆盖
        - 静态方法不存在覆盖

    ```java
    例子
    package com.bjpowernode.javase.test03;
    //动物类
    public class Animal {
        //动物都是可以移动的
        public void move(){
            System.out.println("动物在移动");
        }
    }
    
    package com.bjpowernode.javase.test03;
    //猫科类
    public class Cat extends Animal {
        public void move(){
            System.out.println("猫在走猫步");
        }
    }
    
    package com.bjpowernode.javase.test03;
    //飞禽类
    public class Bird extends Animal {
        public void move(){
            System.out.println("鸟儿在飞翔");
        }
    }
    
    package com.bjpowernode.javase.test03;
    
    public class YingWu extends Bird {
        @Override
        public void move() {
            System.out.println("鹦鹉飞不起来！");
    
        }
    }
    
    package com.bjpowernode.javase.test03;
    
    public class OverrideTest01 {
        public static void main(String[] args) {
            //创建动物对象
            Animal a = new Animal();
            a.move();
    
            //创建猫科类动物对象
            Cat c =new Cat();
            c.move();
    
            //创建飞禽类动物对象
            Bird b = new Bird();
            b.move();
    
            //创建鹦鹉类动物对象
            YingWu d = new YingWu();
            d.move();
        }
    }
    
    //动物在移动
    //猫在走猫步
    //鸟儿在飞翔
    //鹦鹉飞不起来！
    ```

14. 多态

    父类型引用指向子类型对象这种机制导致程序在编译阶段绑定和运行阶段绑定有两种不同的形态/状态，这种机制就叫做**多态语法机制**。

    多态的作用是什么？

    (1) 降低程序的耦合度，提高程序的扩展力。

    (2) 能使用多态尽量使用多态。

    (3) 父类型引用指向子类型对象

    ```java
    package com.bjpowernode.javase.test03;
    //动物类
    public class Animal {
        //动物都是可以移动的
        public void move(){
            System.out.println("动物在移动");
        }
    }
    
    package com.bjpowernode.javase.test04;
    //猫类
    public class Cat extends Animal{
        @Override
        public void move() {
            System.out.println("猫在走猫步！");
        }
        //不是从父类中继承过来的方法
        public void catchMouse(){
            System.out.println("猫抓老鼠!");
        }
    
    }
    
    package com.bjpowernode.javase.test04;
    
    public class Bird extends Animal{
        @Override
        public void move() {
            System.out.println("鸟儿在飞翔！");
        }
        public void fly(){
            System.out.println("Bird fly！");
        }
    }
    
    package com.bjpowernode.javase.test04;
    
    /**
     *关于java语言当中的多态语法机制：
     * 1、 Animal、Cat、Bird三个类之间的关系：
     *      Cat继承Animal
     *      Bird继承Animal
     *      Cat和Bird之间没有任何继承关系
     * 2、 面向对象三大特征：封装、继承、多态
     * 3、 多态中涉及到的几个概念
     *      * 向上转型(upcasting)
     *          - 子类型 --> 父类型
     *          又被称为：自动类型转换
     *      * 向下转型(downcasting)
     *          - 父类型 --> 子类型
     *          又被称为：强制类型转换【需要加强制类型转换符】
    *       * 注意：无论向上转型还是向下转型，两种类型之间必须要有继承关系，否则编译无法通过。
     */
    public class Test {
        public static void main(String[] args) {
    
            //以前编写的程序
            Animal a1 = new Animal();
            a1.move();
    
            Cat c1 = new Cat();
            c1.move();
            c1.catchMouse();
    
            Bird b1 = new Bird();
            b1.move();
    
            //使用多态语法机制
    
            /**
             * 1. Animal和Cat之间存在继承关系，Animal是父类，Cat是子类
             * 2. Cat is a Animal
             * 3. new Cat()创建的对象的类型是Cat, a2这个引用的数据类型是Animal,
             * 可见它们进行了类型转换，子类型转换为父类型，向上转型upcasting
             * 4. Java中允许这种语法：父类型引用指向子类型对象。
             */
            Animal a2 = new Cat();
            /**
             * 1. java程序分为编译阶段和运行阶段。
             * 2. 编译阶段编译器检查a2这个引用的数据类型Animal,由于Animal.class
             * 字节码文件当中有move()方法，所以编译通过了，这个过程叫做静态绑定/编译阶段绑定。
             * 3. 在程序运行阶段，JVM堆内存中真实创建的对象是Cat对象，那么以下程序在运行阶段
             * 一定会调用Cat对象的move()方法，此时发生了程序的动态绑定/运行阶段绑定。
             * 4. 无论是Cat类有没有重写move方法，运行阶段一定调用的是Cat对象的move方法，
             * 因为底层的真实对象就是Cat对象。
             * 5. 父类型引用指向子类型对象这种机制导致程序在编译阶段绑定和运行阶段绑定有两种
             * 不同的形态/状态，这种机制就叫做多态语法机制。
             */
            a2.move(); //猫在走猫步！，分析原因，a2虽然名义上是Animal对象，但其本质实际上是一个Cat对象，所以会调用Cat对象。
    
            /**
             * 分析以下程序为什么不能调用？
             *      因为编译阶段编译器检查到a2的类型是Animal类型，从Animal.class字节码文件
             *      当中查找catchMouse()方法，最终没有找到该方法，导致静态绑定失败，也就是编译
             *      失败。
             *
             */
            //a2.catchMouse();编译报错
            /**
             * 需求：就想让以上的对象执行catchMouse()方法，怎么办？
             *          a2是无法直接调用的，因为a2的类型是Animal，Animal中没有catchMouse()方法。
             *          可以将a2强制类型转换成Cat类型。
             *          a2的类型是Animal(父类)，转换成Cat类型(子类)，被称为向下转型/downcasting/强制类型转换。
             *   注：向下转型也需要两种类型之间必须有继承关系，不然编译报错。强制类型转换需要加强制类型转换符。
             *
             *   什么时候需要使用向下转型呢？
             *          当调用的方法是子类型中特有的，在父类型当中不存在，必须进行向下转型。
             */
            Cat c2 = (Cat) a2;
            c2.catchMouse();
    
            //再来一波
            Animal a3 = new Bird();
            /**
             * 1. 以下程序编译是没有问题的，因为编译器检查到a3的数据类型是Animal
             * Animal和Cat之间存在继承关系，并且Animal是父类型，Cat是子类型，
             * 父类型转换成子类型叫做向下转型，语法合格。
             * 2. 但是运行阶段会出现异常，因为JVM堆内存中真实存在的对象是Bird类型，Bird对象无法转换成Cat对象，
             * 因为两种类型之间不存在任何继承关系，此时出现了著名的异常：java.lang.ClassCastException，
             * 类型转换异常，这种异常总是在“向下转型的时候”发生。
             */
    
            //Cat c3 = (Cat) a3;
            /**
             * 1. 以上异常只有在强制类型转换的时候会发生，也就是“向下转型”存在隐患(编译通过，运行不通过)
             * 2. 向上转型只要编译通过， 运行一定不会出问题
             * 3. 向下转型编译通过，运行可能出现错误：Animal a3 = new Bird(); Cat c3 = (Cat) a3;
             * 4. 如何避免向下转型出现的ClassCastException呢？ 使用instanceof运算符可以避免出现以上的异常。
             * 5. instanceof运算符怎么用？
             *      (1) 语法格式：(引用 instanceof 数据类型名)
             *      (2) 以上运算符的执行结果类型是布尔类型，结果可能是true/false
             *      (3) 假设(a instanceof Animal)的运行结果
             *          True表示：a这个引用指向的对象是一个Animal类型。
             *          False表示：a这个引用指向的对象不是一个Animal类型。
             * 6. Java规范中要求：在进行强制类型转换之前，建议采用instanceof运算符进行判断，避免ClassCastException异常的发生。
             */
    
            if(a3 instanceof Cat){  //a3是一个Cat类型的对象
                Cat c3 = (Cat)a3;
                c3.catchMouse();
            }else if (a3 instanceof Bird){  //a3是一个Bird类型的对象
                Bird b2 = (Bird) a3;
                b2.fly();
    
            }
    
    
        }
    }
    //动物在移动
    //猫在走猫步！
    //猫抓老鼠!
    //鸟儿在飞翔！
    //猫在走猫步！
    //猫抓老鼠!
    //Bird fly！
    ```

15. final关键字

    final表示最终的，不可变的

    final修饰的类无法被继承

    final修饰的方法无法被覆盖

    final修饰的变量一旦赋值之后，不可重新赋值【不可二次赋值】

    final修饰的实例变量，必须手动赋值，不能采用系统默认值。

    final修饰的引用，一旦指向某个对象之后，不能再指向其它对象，那么被指向的对象无法被垃圾回收器回收。final修饰的引用虽然指向某个对象之后不能指向其它对象，但是所指向的对象内部的内存是可以被修改的。

    final修饰的实例变量是不可变的，这种变量一般和static联合使用，被称为"常量"。

    ```java
    package com.bjpowernode.javase.test06;
    
    public class User {
        int id;
    
        public User(int id) {
            this.id = id;
        }
    }
    
    package com.bjpowernode.javase.test06;
    
    public class FinalTest03 {
        public static void main(String[] args) {
            //创建用户对象
            User u = new User(100);
    
            //又创见一个新的User对象
            //程序执行到此处表示以上对象已经变成垃圾数据，等待垃圾回收器的回收。
            u = new User(200);
    
            //创建用户对象
            final User user = new User(30);
            System.out.println(user.id);
            //user = new User(50); //final修饰的引用，一旦指向某个对象之后，不能再指向其它对象。
            user.id = 50;//final修饰的引用虽然指向某个对象之后不能指向其它对象，但是所指向的对象内部的内存是可以被修改的。
            System.out.println(user.id);
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.test06;
    
    public class FinalTest04 {
        public static void main(String[] args) {
            System.out.println(Chinese.country);
            System.out.println(Math.PI);
        }
    }
    
    //中国人
    class Chinese{
        //国家
        //需求，每个中国人的国际都是中国，而且国籍不会发生改变，为了防止国籍被修改，建议加final修饰。
        //final修饰的实例变量是不可变的，这种变量一般和static联合使用，被称为"常量"
        //常量的定义语法格式：
        //      public static final 类型 常量名 = 值;
        //java规范中要求所有常量的名字全部大写，每个单词之间使用下划线分开。
        public static final String country = "中国";
    }
    
    class Math{
        public static final double PI = 3.1415926;
    }
    //中国
    //3.1415926
    ```

16. 包机制

    - 包又被称为package, java中引入package语法机制主要是为了方便程序的管理，不同功能的类被分门别类放到不同的软件包当中，查找比较方便，管理比较方便，易维护。

    - 怎么定义package？

      - 在java源程序的第一行上编写package语句
      - pack只能编写一个语句
      - 语法结构： package 包名;

    - 包名的命名规范：

      - 公司域名倒序 + 项目名 + 模块名 + 功能名; 采用这种方式重名的几率较低，因为公司域名具有全球唯一性

      - eg: 

        ```java
        package com.bjpowernode.oa.user.service;
        package org.apache.tomcat.core;
        ```

      - 包名要求全部小写，包名也是标识符，必须遵守标识符的命名规则。

      - 一个包将来对应的是一个目录。

      - 使用package机制后，应该怎么编译，怎么运行？

        - 使用了package机制之后，类名不再是Test01了，类名是：com.bjpowernode.javase.day11.Test01

        - 编译：javac java源文件路径(在硬盘上生成一个class文件:Test01.class)

        - 手动方式创建目录，com/bjpowernode/javase/day11，将Test01.class字节码文件放到指定的目录下

        - 运行 ：java com.bjpowernode.javase.day11.Test01

        - 另一种方式(编译 + 运行):

          - 编译：

            ```java
            javac -d 编译之后存放路径 java源文件的路径
            例如 ：将F:\Hello.java文件编译之后放到C:\目录下
                javac -d C:\ F:\Hello.java
            javac -d . *.java 将当前路径中*.java编译之后存放到当前目录下
            ```

          - 运行

            ```java
            JVM的类加载器ClassLoader默认从当前路径下加载。
                保证DOS命令窗口的路径先切换到com所在的路径，
                执行：java com.bjpowernode.javase.day11.Test01
            ```

      - 什么时候需要import？

        - 不是java.lang包下，并且不在同一个包下的时候，需要使用import进行导入。

17.  访问控制权限修饰符：

    1. 访问控制权限修饰符来控制元素的访问范围

    2. 访问控制权限修饰符包括：

       - public【表示公开的，在任何位置都可以访问】
       - protected【同包，子类】
       - 缺省【同包】
       - private【表示私有的，只能在本类中访问】

    3. 访问控制权限修饰符可以修饰类【public和默认能用，其他不行】、属性【4个都可以】、方法【4个都可以】、接口【public和默认能用，其他不行】

    4. 当某个数据只希望子类使用，使用protected进行修饰

    5. 修饰符的范围：

       private < 缺省 < protected < public

    

------

1.  DOS命令：

   - ipconfig(ip地址的配置信息)----->ipconfig /all，可以查看更详细的网络信息【查看本机的IP】

   - 【查看计算机是否可以正常通信】  

     ```
     ping 域名
     ping IP地址
     ping IP地址 -t【-t表示一直ping】
     ```

2.  抽象类

   ![image-20210309150912240](https://i.loli.net/2021/03/09/TtoFMOZD32gzKcd.png)

   -  什么是抽象类？类和类之间具有共同特征，将这些共同特征提取出来，形成的就是抽象类。类本身是不存在的，所以抽象类无法创建对象，也就是无法实例化。

   - 抽象类也属于引用数据类型。

   - 抽象类是无法实例化的，无法创建对象的，所以抽象类是用来被子类继承的。

   - 抽象类的子类还可以是抽象类。

   - 抽象类虽然无法实例化，但是抽象类有构造方法，这个构造方法是供子类使用的。

   - 抽象类关联到一个概念：抽象方法，抽象方法表示没有实现的方法，没有方法体的方法。

     ```java
     public abstract void doSome();
     ```

     抽象方法的特点：没有方法体，以分号结束。前面修饰符列表里有abstract关键字。

     抽象类中不一定有抽象方法，但是抽象方法必须出现在抽象类中。

   - 一个非抽象的类继承抽象类，必须将抽象类中的抽象方法覆盖/重写。

     ```java
     //抽象类
     abstract class Animal{
         //抽象方法
         public abstract void move();
     }
     class Bird extends Animal{} //报错，子类是非抽象的，并且未覆盖Animal中的抽象方法move()
     class Bird extends Animal{
         //需要将从父类中继承过来的抽象方法进行覆盖/重写
         public void move(){}
     }
     
     public class AbstractTest{
         public static void main(String[] args){
             //能不能使用多态？
             //父类型引用指向子类型对象
             Animal a = new Bird();//这就是面向抽象编程。面向抽象编程，不要面向具体编程，降低程序耦合度，提高程序扩展力。
         }
     }
     ```

     

   - 抽象类怎么定义？

     ```java
     [修饰符列表] abstract class 类名{
         类体；
     }
     ```

3.  接口

   - 接口是一种引用数据类型，是完全抽象的(抽象类是半抽象的),编译之后也是一个class字节码文件。

   - 接口怎么定义？

     ```java
     [修饰符列表] interface 接口名{}
     ```

   - 接口支持多继承，一个接口可以继承多个接口

     ```java
     package com.bjpowernode.javase.test07;
     
     public class test01 {
         public static void main(String[] args){
             //访问接口的常量
             System.out.println(MyMath.PI);
             //MyMath.PI = 3.15; 报错无法修改
     
         }
     }
     
     //定义接口
     interface A{}
     interface B{}
     interface C extends A, B{}
     
     //我的数学接口
     interface MyMath{
         //常量,public static可以省略
         public static final double PI = 3.14;
     
     
     
         //抽象方法
         public abstract int sum(int a, int b);
     
         int sum2(int a, int b);//pubilic abstract可以省略。
     }
     ```

   - 接口只包含两部分内容：常量+抽象方法。没有其他内容了。

   - 接口中所有的元素都是public修饰的，都是公开的。

   - 接口中的抽象方法和常量定义时，public abstract修饰符可以省略。

   - 接口中的方法都是抽象的，所以接口中的方法不能有方法体。

   - 类和类之间叫继承，类和接口之间叫做实现。继承使用extends关键字完成，而实现使用implements关键字完成。

     ```java
     package com.bjpowernode.javase.test07;
     
     public class test01 {
         public static void main(String[] args){
             //访问接口的常量
             System.out.println(MyMath.PI);
             //MyMath.PI = 3.15; 报错无法修改
             
             //能使用多态吗？可以
             MyMath mm = new MyMathImplement();
             //调用接口里面的方法(面向接口编程)
             int result1 = mm.sum(10,20);
             System.out.println(result1);
     
             int result2 = mm.sumb(20, 10);
             System.out.println(result2);
     
         }
     }
     
     //定义接口
     interface A{}
     interface B{}
     interface C extends A, B{}
     
     //我的数学接口
     interface MyMath{
         //常量,public static可以省略
         public static final double PI = 3.14;
         //抽象方法
         public abstract int sum(int a, int b);
     
         int sumb(int a, int b);//pubilic abstract可以省略。
     }
     
     //编写一个类，非抽象类
     //class MyMathImplement implements MyMath{} //报错，非抽象类实现抽象类，需要重写所有方法
     
     //修正
     class MyMathImplement implements MyMath{
         public int sum(int a, int b){
             return a + b;
         }
         public int sumb(int a, int b){
             return a - b;
         }
     }
     ```

   - 一个类可以同时实现多个接口，这种机制弥补了java中的缺陷：java中类和类只支持单继承，实际上单继承是为了简单而出现的，现实世界中存在多继承，java中接口弥补了单继承的缺陷。
   
   -  当一个非抽象的类实现接口的话，必须将接口中所有的抽象方法全部实现(覆盖、重写)
   
     ```java
     package com.bjpowernode.javase.test07;
     
     public class test02 {
         public static void main(String[] args) {
     
         }
     }
     
     interface A1{
         void m1();
     }
     interface B1{
         void m2();
     }
     interface C1{
         void m3();
     }
     
     class D implements A1, B1, C1{
         @Override
         public void m1() {
             
         }
     
         @Override
         public void m2() {
     
         }
     
         @Override
         public void m3() {
     
         }
     }
     
     //之前有一个结论：
     无论向上转型还是向下转型，两种类型之间必须要有继承关系，没有继承关系编译器会报错【这句话不适用于接口方面】最终实际上和之前还是一样，需要加instanceof运算符进行判断。
     ```
   
     ```java
     package com.bjpowernode.javase.test07;
     
     
     import com.bjpowernode.javase.test06.A;
     
     /*
     继承和实现都存在的话，代码应该怎么写？
         extends 关键字在前，implements 关键字在后
      */
     public class test03 {
         public static void main(String[] args) {
             //创建对象
             Flyable f = new Cat(); // 多态
             f.fly();
     
             Flyable f2 = new Pig(); //多态
             f2.fly();
     
         }
     
     }
     
     
     //动物类父类
     class Animal{
     
     }
     //可飞翔的接口(是一对翅膀)
     interface Flyable{
         void fly();
     }
     
     //动物类子类：猫类
     //Flyable是一个接口，是一对翅膀的接口，通过接口插到猫身上，让猫变得可以飞翔
     class Cat extends Animal implements Flyable{
         public void fly(){
             System.out.println("飞猫起飞！");
         }
     
     }
     
     //动物类子类：蛇类，不想让它飞，可以不实现Flyable接口
     class Snake extends Animal{
     
     }
     
     class Pig extends Animal implements Flyable{
         public void fly(){
             System.out.println("飞猪起飞！");
         }
     }
     
     class Fish implements Flyable {
         public void fly() {
             System.out.println("飞鱼起飞！");
         }
     }
     
     ```
     
   - 接口在开发中的作用
   
     接口在开发中的作用，类似于多态在开发中的作用
   
     【多态：面向抽象编程，不要面向具体编程，降低程序的耦合度，提高程序的扩展力。】
   
     面向抽象编程可以修改为面向接口编程。具有高扩展性。符合OCP开发原则。接口的使用离不开多态机制，接口+多态才能实现代码高效。
   
     ```java
     public class ChinaCooker implements FoodMenu{
         public ChinaCooker() {
             super();
         }
     
         @Override
         public void xihongshichaojidan() {
             System.out.println("中餐师傅做的西红柿炒鸡蛋！");
     
         }
     
         @Override
         public void yuxiangyousi() {
             System.out.println("中餐师傅做的鱼香肉丝！");
     
         }
     }
     
     package com.bjpowernode.javase.test08;
     
     public class AmericanCooker implements FoodMenu{
         public AmericanCooker() {
             super();
         }
     
         @Override
         public void xihongshichaojidan() {
             System.out.println("西餐师傅做的西红柿炒鸡蛋！");
     
         }
     
         @Override
         public void yuxiangyousi() {
             System.out.println("西餐师傅做的鱼香肉丝！");
     
         }
     }
     
     package com.bjpowernode.javase.test08;
     
     public interface FoodMenu {
         //西红柿炒鸡蛋
         void xihongshichaojidan();
         //鱼香肉丝
         void yuxiangyousi();
     }
     
     package com.bjpowernode.javase.test08;
     //顾客
     public class Customer {
         //先得有一个菜单
         private FoodMenu foodMenu;
     
         //如果以下这样写，就表示写死了(焊接了，没有可插拔了)
         //ChinaCooker cc;
         //AmericanCooker ac;
     
         //顾客是和菜单发生联系的，菜单和不同类型的厨师发生联系
         //所以构造方法的时候输入的参数应该是菜单接口
         public Customer() {
         }
     
         public Customer(FoodMenu foodMenu) {
             this.foodMenu = foodMenu;
         }
     
         public FoodMenu getFoodMenu() {
             return foodMenu;
         }
     
         public void setFoodMenu(FoodMenu foodMenu) {
             this.foodMenu = foodMenu;
         }
     
         //提供一个点菜的方法
         public void order(){
             foodMenu.xihongshichaojidan();
             foodMenu.yuxiangyousi();
         }
     
     }
     
     package com.bjpowernode.javase.test08;
     
     import com.bjpowernode.javase.test06.C;
     
     public class Test {
         public static void main(String[] args) {
             //创建厨师对象
             FoodMenu cooker1 = new AmericanCooker();
             FoodMenu cooker2 = new ChinaCooker();
     
             //创建顾客对象
             Customer customer = new Customer(cooker1);
     
             //顾客点菜
             customer.order();
     
     
         }
     }
     ```
     
     【总结：接口可以解耦合，解开的是调用者和实现者的耦合，以后进行大项目的开发，一般都是将项目分离成一个模块一个模块的，之间采用接口衔接，降低耦合度。】

4. is a ||  has a || like a

```java
is a :Cat is an Animal凡是满足is a的表示继承关系
	A extends B
```

```java
has a:I has a pen 凡是满足has a关系的表示“关联关系”，以属性的形式存在。
    A {
    B b;
}
```

```java
like a: Cooker like a FoodMenu(厨师像一个菜单一样)，凡是能满足like a关系的表示"实现关系"，实现关系通常是：类实现接口。
    A implements B
```

5. 解释scanner

   ```java
   package com.bjpowernode.javase.test09;
   import java.util.Scanner;
   public class Test {
   
   
       public static void main(String[] args) {
           Scanner s = new Scanner(System.in);  //通过 Scanner 类来获取用户的输入。
           
           String str1 = s.next();
           System.out.println("您输入的字符串是:" + str1);
       }
   }
   ```

------

1. JDK类库的根类：Object

   1. 这个类中方法是所有子类通用的，任何一个类默认继承Object,就算没有直接继承，最终也会间接继承。

   2. JAVA中的equals方法：

      java中基本数据雷星星比较是否相等，使用==

      java中所有的引用数据类型比较是否相等，使用equals

   3. finalize()方法：这个方法是protected修饰的，在Object类中这个方法的源代码是

   ```java
   protected void finalize() throws Throwable {}
   ```

   ​	这个方法不需要程序员手动调用，JVM垃圾回收器负责调用这个反方法。

   ​	finalize()方法实际上是SUN公司为java程序员准备的一个时机，垃圾销毁时机。如果希望在对象销毁时执行一段代码的话，这段代码要写到finalize()方法当中。

   ​	提示：java中的垃圾回收器不是轻易启动的，垃圾可能太少，或者时间没到，种种条件下，有可能启动，也有可能不启动。

   ```java
   package com.bjpowernode.javase.test10;
   
   public class Test {
       public static void main(String[] args) {
           //创建对象
           Person p = new Person();
               //怎么把Person对象变成垃圾
               p = null;
   //        for(int i = 0; i<10000000; i++){
   //            Person p = new Person();
   //            p = null;
   //        }
           System.gc();//建议启动垃圾回收器，启动的概率高一些
   
       }
   }
   
   class Person{
       //重写finalize()方法
       //Person类型的对象被垃圾回收器回收的时候，垃圾回收器负责调用:p.finalize();
       protected void finalize() throws Throwable{
           System.out.println("即将被销毁");
       }
   }
   
   
   ```


2. 匿名内部类：

   内部类：在类的内部又定义了一个新的类，就叫内部类。

   内部类的分类：

   - 静态内部类：类似于静态变量
   - 实例内部类：类似于实例变量
   - 局部内部类：类似于局部变量

   ```java
   package com.bjpowernode.javase.test10;
   
   class Test02 {
       //该类在类的内部，所以称为内部类
       //由于前面有static,所以称为"静态内部类"
       static class Inner1{
   
       }
       //没有static叫做实例内部类
       class Inner2{
   
       }
   
       public void doSome(){
   
           //这个类在类的内部，所以称为内部类
           class Inner3{
   
           }
       }
   }
   
   ```

   ```java
   package com.bjpowernode.javase.test10;
   
   public class Test02 {
       public static void main(String[] args) {
           //调用MyMath中的mySum方法
           Mymath mm = new Mymath();
           mm.mySum(new ComputeImpl(),100,200);
       }
   
   }
   
   //负责计算的接口
   interface Compute{
       //抽象方法
       int sum(int a, int b);
   
   }
   //接口的实现类
   class ComputeImpl implements Compute{
       //对方法的实现
       public int sum(int a, int b){
           return a + b;
       }
   }
   
   
   //数学类
   class Mymath{
       //数学类求和方法
       public void mySum(Compute c, int x, int y){
           int reValue = c.sum(x, y);
           System.out.println(x + "+" + y + "=" + reValue);
       }
   }
   
   ```
   
   ```java
   //使用匿名内部类
   package com.bjpowernode.javase.test10;
   
   public class Test02 {
       public static void main(String[] args) {
           //调用MyMath中的mySum方法
           Mymath mm = new Mymath();
           //使用匿名内部类【不建议使用】
           mm.mySum(new Compute() {
               @Override
               public int sum(int a, int b) {
                   return a + b ;
               }
           }, 100, 200);
       }
   
   }
   
   //负责计算的接口
   interface Compute{
       //抽象方法
       int sum(int a, int b);
   
   }
   
   
   
   //数学类
   class Mymath{
       //数学类求和方法
       public void mySum(Compute c, int x, int y){
           int reValue = c.sum(x, y);
           System.out.println(x + "+" + y + "=" + reValue);
       }
   }
   
   ```
   
   ------

1. 数组

   Java语言中的数组是一种引用数据类型，不属于基本数据类型， 数组的父类是Object.

   数组实际上是一个容器，可以 同时容纳多个元素。(数组是一个数据的集合)

   数组当中可以存储基本数据类型的数据，也可以存储引用数据类型的数据。

   数组因为是引用数据，所以数据对象是堆内存当中。

   数组一旦创建，在java中规定，长度不可变。

   数组数据结构的缺点：(1) 由于为了保证数组中每个元素的内存地址连续，所以在数组上随机删除或者增加元素的时候，效率低下，因为会涉及到后面元素统一向前或向后位移的操作。(2) 数组不能存储大数据量，因为很难在内存空间上找到一块特别大的连续的内存空间。

   初始化一维数组：

   - 静态初始化：

     ```java
     int[] array = {100, 2000, 300, 55}
     ```

   - 动态初始化：

     ```java
     int[] array = new int[5]; //这里的5表示数组的元素个数
     ```

     ```Java
     String[] names =new String[6];//初始化6个长度的String类型数据，每个元素默认值为null
     ```

   ```java
   package com.bjpowernode.javase.array;
   
   public class ArrayTest01 {
       public static void main(String[] args) {
           //声明一个int类型的数组，使用静态初始化的方式
           int[] a = {1, 100, 10};
   
           //初始化一个Object类型的数组，采用动态初始化方式
           Object[] objs = new Object[3]; //3个长度，动态初始化，所以每个元素默认值都是null
           System.out.println(objs);  //输出的是地址
   
   
           //数组中每个元素都有下表，通过下表对数组进行存和取
           System.out.println(a[a.length - 1]);
           a[1] = 200;
           System.out.println(a[1]);  //输出的是地址
   
           //遍历
           for(int i = 0; i < a.length; i++){
               System.out.println(a[i]);
           }
       }
   }
   
   ```

   ```java
   package com.bjpowernode.javase.array;
   
   public class ArrayTest02 {
   
       //用户名和密码输入到String[] args数组当中
       public static void main(String[] args) {
           if(args.length != 2){
               System.out.println("请输入程序和参数，参数包括用户名和密码信息");
               return;
           }
   
           String username = args[0];
           String password = args[1];
   
           if(username.equals("admin") && password.equals("123")){
               System.out.println("登陆成功，欢迎[" + username + "]回来");
           }
           else {
               System.out.println("验证失败，用户不存在或者密码错误！");
           }
       }
   }
   ```

   java中对数组的扩容：先新建一个大容量的数组，然后将小容量的数组中的数据一个个拷贝到大数组当中。

   ```java
   package com.bjpowernode.javase.array;
   
   public class ArrayTest03 {
       public static void main(String[] args) {
           int[] src = {1, 11, 22, 3, 4};
           int[] dest = new int[20];
           //调用JDK System类中的arraycopy方法，来完成数组的拷贝
           System.arraycopy(src,1, dest, 3, 2);
           // src:拷贝源 srcPos:拷贝源起始位置 dest:目标 destPos:目标起始位置 length:拷贝长度
   
           //遍历目标数组
           for(int i = 0; i < dest.length; i++){
               System.out.print(dest[i]); // 0001122000000000000000
           }
   
           //数组中如果存储的元素是引用，可以拷贝吗？当然可以
           String[] strs = {"hello", "world","study","java", "oracle", "mysql", "jdbc"};
           String[] newStrs = new String[20];
           System.arraycopy(strs, 0,newStrs, 0, strs.length);
           for (int i = 0; i< newStrs.length; i++){
               System.out.println(newStrs[i]);
           }
   
           Object[] objs = {new Object(), new Object(), new Object()};
           Object[] newObjs = new Object[10];
           //拷贝的是内存地址
           System.arraycopy(objs, 0, newObjs, 0, objs.length);
           for (int i = 0; i< newObjs.length; i++){
               System.out.println(newObjs[i]);
           }
       }
   }
   
   ```

   二维数组

   ```java
   package com.bjpowernode.javase.array;
   
   public class ArrayTest04 {
       public static void main(String[] args) {
           //二维数组
           int[][] a = {
                   {100,233,300},
                   {0,23,30},
                   {10,32,0}
           };
           //取出以上二位数中的第一个一维数组
           int[] a0 = a[0];
           //取出以上二位数中的第一个一维数组的第一个元素
           int a1 = a0[0];
           System.out.println(a1);
   
           //合并以上代码
           System.out.println(a[0][0]);
   
           //遍历
           for(int i=0; i<a.length; i++){
               for(int j=0; j<a[i].length; j++){
                   System.out.print(a[i][j] + " ");
               }
               System.out.println();
           }
           //动态初始化二维数组
           int [][] array = new int[3][4];
           
       }
   }
   
   ```

   ```java
   作业题：
   package com.bjpowernode.javase.array.homework;
   /**
    * 1.作业题：数组模拟栈
    * 要求：
    *  1.这个栈可以存储java中的任何引用类型的数据
    *  2.在栈中提供push方法模拟压栈(栈满了，要有提示信息)
    *  3.在栈中提供pop方法模拟弹栈(栈空了，也要有提示信息)
    *  4.编写测试程序，new对象， 调用push pop反法来模拟压栈、弹栈的动作。
    *  5.假设栈的默认初始化容量是10
    *
    * 2.酒店管理系统的模拟
   
    */
   public class Mystack {
       //向栈当中存储元素，这里使用一维数组模拟
       //为什么使用Object类型数组？因为object类型的栈可以存储java中的任何引用类型的数据
       private Object[] elements;
       //栈帧，永远指向栈顶部元素
       private int index;
   
       public Object[] getElements() {
           return elements;
       }
   
       public void setElements(Object[] elements) {
           this.elements = elements;
       }
   
       public int getIndex() {
           return index;
       }
   
       public void setIndex(int index) {
           this.index = index;
       }
   
       //无参数构造方法
       public Mystack() {
           //一维数组动态初始化
           this.elements = new Object[10];
           //初始化栈帧
           this.index = -1;
       }
       //压栈的方法
       public void push(Object elements){
           if(this.index >= this.elements.length - 1){
               System.out.println("压栈失败，栈已满！");
               return;
           }
           this.index++;
           this.elements[index] = elements;
           System.out.println("压栈" + elements +"成功，栈帧指向" + index);
       }
   
       //弹栈的方法
       public void pop(){
           if(index < 0){
               System.out.println("弹栈失败，栈已空！");
               return;
           }
           System.out.println("弹栈" + elements[index] + "元素成功，");
           index--;
           System.out.println("栈帧指向" + index);
       }
   
   }
   
   package com.bjpowernode.javase.array.homework;
   
   public class ArrayTest {
       public static void main(String[] args) {
           //创建一个栈对象， 初始化容量为10
           Mystack stack = new Mystack();
           //调用方法压栈
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
           stack.push(new Object());
   
           //调用弹栈方法
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
           stack.pop();
   
   
       }
   
   }
   /**
    * 压栈java.lang.Object@12edcd21成功，栈帧指向0
    * 压栈java.lang.Object@34c45dca成功，栈帧指向1
    * 压栈java.lang.Object@52cc8049成功，栈帧指向2
    * 压栈java.lang.Object@5b6f7412成功，栈帧指向3
    * 压栈java.lang.Object@27973e9b成功，栈帧指向4
    * 压栈java.lang.Object@312b1dae成功，栈帧指向5
    * 压栈java.lang.Object@7530d0a成功，栈帧指向6
    * 压栈java.lang.Object@27bc2616成功，栈帧指向7
    * 压栈java.lang.Object@3941a79c成功，栈帧指向8
    * 压栈java.lang.Object@506e1b77成功，栈帧指向9
    * 压栈失败，栈已满！
    * 弹栈java.lang.Object@506e1b77元素成功，
    * 栈帧指向8
    * 弹栈java.lang.Object@3941a79c元素成功，
    * 栈帧指向7
    * 弹栈java.lang.Object@27bc2616元素成功，
    * 栈帧指向6
    * 弹栈java.lang.Object@7530d0a元素成功，
    * 栈帧指向5
    * 弹栈java.lang.Object@312b1dae元素成功，
    * 栈帧指向4
    * 弹栈java.lang.Object@27973e9b元素成功，
    * 栈帧指向3
    * 弹栈java.lang.Object@5b6f7412元素成功，
    * 栈帧指向2
    * 弹栈java.lang.Object@52cc8049元素成功，
    * 栈帧指向1
    * 弹栈java.lang.Object@34c45dca元素成功，
    * 栈帧指向0
    * 弹栈java.lang.Object@12edcd21元素成功，
    * 栈帧指向-1
    */
   ```

   ```java
   //作业题：
   //构建一个酒店管理系统，能够完成“查询房间信息、订房、退房”的功能。
   package com.bjpowernode.javase.array.homework;
   //酒店的房间
   public class Room {
       /**
        * 房间编号:
        * 1楼：101,102,103,104,105..
        * 2楼：201,202,203,204,205..
        * 3楼：301,302,303,304,305..
        * 4楼：401,402,403,404,405..
        *
        */
       private int no;
       /**
        * 房间类型:：b标准间 单人间 总统套房
        *
        *
        */
       private String type;
       /**
        * 房间类型:
        * true表示空闲，房间可以被预定
        * false表示占用，房间不能被预定
        *
        *
        */
       private boolean status;
   
       //构造方法
       public Room() {
       }
   
       public Room(int no, String type, boolean status) {
           this.no = no;
           this.type = type;
           this.status = status;
       }
   
       //setter and getter
       public int getNo() {
           return no;
       }
   
       public void setNo(int no) {
           this.no = no;
       }
   
       public String getType() {
           return type;
       }
   
       public void setType(String type) {
           this.type = type;
       }
   
       public boolean getStatus() {
           return status;
       }
   
       public void setStatus(boolean status) {
           this.status = status;
       }
   
   
       //重写equals方法
       public boolean equals(Object obj){
           if(obj == null || !(obj instanceof Room)) return false;
           if(this == obj) return true;
           Room room = (Room)obj;
           return this.getNo() == room.getNo();
       }
       //重写toString方法
       public String toString(){
           return "[" + no + "," + type + "," + (status?"空闲":"占用") +  "]";
       }
   
   //    //编写一个临时测试程序
   //    public static void main(String[] args) {
   //        Room room = new Room(101, "单人间", false);
   //        System.out.println(room);
   //
   //        Room room1 = new Room(102, "单人间", false);
   //        System.out.println(room.equals(room1));
   //    }
   }
   
   
   package com.bjpowernode.javase.array.homework;
   
   /**
    * 酒店对象，酒店中有二维数组，二维数组模拟大厦
    */
   public class Hotel {
       //二维数组，模拟大厦所有房间
       private Room[][] rooms;
   
       //盖楼通过构造方法
       public Hotel(){
           rooms = new Room[3][10];
           //需要创建30个room对象，放到数组中
           for(int i = 0; i < rooms.length; i++){
               for(int j = 0; j <  rooms[i].length; j++){
                   if(i == 0) {
                       rooms[i][j] = new Room((i+1) * 100 + j+1, "单人间", true);
                   }else if(i == 1){
                       rooms[i][j] = new Room((i+1) * 100 + j+1, "标准间", true);
                   }else if(i == 2){
                       rooms[i][j] = new Room((i+1) * 100 + j+1, "总统套房", true);
                   }
               }
           }
       }
   
       //在酒店对象上提供一个打印房间列表的方法
       public void print(){
           //打印所有房间状态，就是遍历二维数组
           for(int i=0; i<rooms.length; i++){
               for(int j=0; j< rooms[i].length; j++){
                   Room room = rooms[i][j];
                   System.out.print(room);
               }
               System.out.println();
           }
       }
   
       //订房方法,传入要订阅的房间
       public void order(int roomNo){
           //订阅最主要的是将房间对象的status修改为false
   
           Room room = rooms[roomNo / 100 - 1][roomNo % 100 -1];
           room.setStatus(false);
           System.out.println(roomNo + "已订房！");
   
       }
   
       //退房方法
       public void exit(int roomNo){
           //订阅最主要的是将房间对象的status修改为false
           Room room = rooms[roomNo / 100 - 1][roomNo % 100 -1];
           room.setStatus(true);
           System.out.println(roomNo + "已退房！");
   
       }
   }
   
   
   package com.bjpowernode.javase.array.homework;
   
   import java.util.Scanner;
   
   public class HotelMgtSystem {
       public static void main(String[] args) {
   //        //创建酒店对象
           Hotel hotel = new Hotel();
   //        //打印房间状态
   //        hotel.print();
           /**
            * 首先出一个欢迎界面
            */
           System.out.println("欢迎使用酒店管理系统，请认真阅读以下说明");
           while(true) {
   
               System.out.println("【功能对应的功能编号:[1]表示查看房间列表。[2]表示订房。[3]表示退房。[0]表示退出。】");
               Scanner s = new Scanner(System.in);
               System.out.println("请输入功能编号：");
               int i = s.nextInt();
               if (i == 1) {
                   hotel.print();
   
               } else if (i == 2) {
                   System.out.println("请输入订房编号：");
                   int roomNo = s.nextInt();
   
                   hotel.order(roomNo);
   
               } else if (i == 3) {
                   System.out.println("请输入退房编号：");
                   int roomNo = s.nextInt();
                   hotel.exit(roomNo);
   
   
               } else if (i == 0) {
                   //退出系统
                   System.out.println("再见，欢迎下次再来！");
                   return;
   
               }else{
                   System.out.println("输入功能编号有误，请重新输入！");
               }
           }
       }
   }
   
   ```

   

2. 一些算法

   ```java
   package com.bjpowernode.javase.array;
   
   /**
    * 冒泡排序
    */
   public class BubbleSort {
       public static void main(String[] args) {
           int[] arr = {4, 5, 6, 9, 2, 1, 8, 7, 8, 9,45, 74, 5};
   
   //        for(int j = 0; j <(arr.length - 1); j++) {
   //            for (int i = 0; i < arr.length - 1 - j; i++) {
   //                if (arr[i] > arr[i + 1]) {
   //                    int temp = arr[i];
   //                    arr[i] = arr[i + 1];
   //                    arr[i + 1] = temp;
   //                }
   //            }
   //        }
   
           for(int j = (arr.length - 1); j > 0; j--) {
               for (int i = 0; i < j; i++) {
                   if (arr[i] > arr[i + 1]) {
                       int temp = arr[i];
                       arr[i] = arr[i + 1];
                       arr[i + 1] = temp;
                   }
               }
           }
   
   
           //输出冒泡结果
           for(int k = 0; k < arr.length; k++){
               System.out.print(arr[k] + " ");
           }
   
   
       }
   }
   
   package com.bjpowernode.javase.array;
   /**
    * 选择排序：每次从这堆参与比较的数据当中找出最小值，拿着这个最小值和最前面的元素交换位置。
    */
   public class SelectSort {
       public static void main(String[] args) {
           int[] arr = {4, 5, 6, 9, 2, 1, 8, 7, 8, 9,45, 74, 5};
           for(int i = 0; i< arr.length -1; i++){
               //假设起点i下标位置上的元素是最小的
               int min = i;
               for(int j = i+1; j< arr.length; j++){
                   if(arr[j] < arr[min]){
                       min = j;
                   }
               }
               if(min != i) {
                   //交换a[i]和a[min]
                   int temp;
                   temp = arr[min];
                   arr[min] = arr[i];
                   arr[i] = temp;
               }
   
   
           }
   
           //输出排序结果
           for(int k = 0; k < arr.length; k++){
               System.out.print(arr[k] + " ");
           }
   
       }
   }
       
   ```

   ```java
   package com.bjpowernode.javase.array;
   
   /**
    * 数组查找：(1)遍历查找 (2)二分法查找
    */
   public class ArraySearch {
       public static void main(String[] args) {
           int[] arr = {4, 5, 6, 87, 8};
           int index = arraySearch(arr, 87);
           System.out.println(index);
   
           //-----------------------------------------------------------
           //二分法查找
           int[] arr2 = {100,200,300,400,500,600,700};
           int index2 = binarySearch2(arr2, 700);
           System.out.println(index2);
   
       }
       //把遍历查找抽象成一个方法
       public static int arraySearch(int[] arr, int ele) {
           for(int i = 0; i<arr.length; i++){
               if(ele == arr[i]){
                   return i;
               }
           }
           return -1;
           
       }
   
       public static int binarySearch2(int[] arr2, int dest) {
           int begin = 0;
           int end = arr2.length - 1;
           while (begin <= end) {
               int mid = (begin + end) / 2;
               if (arr2[mid] == dest) {
                   return mid;
               } else if (arr2[mid] < dest) {
                   begin = mid + 1;
               } else if (arr2[mid] > dest) {
                   end = mid - 1;
               }
   
           }
           return -1;
       }
   }
   
   ```

3. 常用类

   String类

   -  在JDK当中双引号括起来的字符串都是直接存储在"方法区"的"字符串常量池"当中的。

     ```java
     package com.bjpowernode.javase.array;
     
     public class StringTest {
         public static void main(String[] args) {
             String s1 = "hello";
             String s2 = "hello";
             //分析结果是true还是false？
             // ==比较的是变量中的内存地址
             System.out.println(s1 == s2); //true
     
             String x = new String("xyz");
             String y = new String("xyz");
             System.out.println(x == y); //false
     
             //String类已经重写了equals方法，以下的equals方法调用的是String重写之后的equals方法。
             System.out.println(x.equals(y)); //true
             
         }
     }
     ```

   - 如果需要频繁进行字符串拼接，可以使用StringBuffer()方法

     StringBuffer

     ```java
     package com.bjpowernode.javase.array.homework;
     
     public class StringBuffer02 {
         public static void main(String[] args) {
             //创建一个初始化容量为16个byte[] 数组，字符串缓冲区对象
             StringBuffer stringBuffer = new StringBuffer();
     
             //拼接字符串，统一调用append方法
             stringBuffer.append("a");
             stringBuffer.append("b");
             stringBuffer.append("d");
             stringBuffer.append(3.14);
             stringBuffer.append(true);
             //append方法底层在进行追加的时候，如果byte数组满了，会自动扩容
     
             System.out.println(stringBuffer);
     
         }
     }
     //abd3.14true
     ```

     StringBuilder

     ```java
     package com.bjpowernode.javase.array.homework;
     
     public class StringBuffer02 {
         public static void main(String[] args) {
             //创建一个初始化容量为16个byte[] 数组，字符串缓冲区对象
             StringBuilder stringBuilder = new StringBuilder();
     
             //拼接字符串，统一调用append方法
             stringBuilder.append("a");
             stringBuilder.append("b");
             stringBuilder.append("d");
             stringBuilder.append(3.14);
             stringBuilder.append(true);
     
             System.out.println(stringBuilder);
     
         }
     }
     //abd3.14true
     ```

     > StringBuffer中的方法都有synchronized关键字修饰，表示StringBuffer在多线程环境下运行是安全的
     >
     > StringBuilder中的方法都没有synchronized关键字修饰，表示StringBuilder在多线程环境下运行是不安全的

6. 包装类

   ```java
   package com.bjpowernode.javase.array;
   
   /**
    * java中为8种基本数据类型又对应准备了8种包装类型。8种包装类属于引用数据类型，父类是Object。
    *
    * 8种基本数据类型对应的包装类型名
    * 基本数据类型          包装类型
    * --------------------------------------------
    *    byte              java.lang.Byte(父类Number)
    *    short             java.lang.Short(父类Number)
    *    int               java.lang.Integer(父类Number)
    *    long              java.lang.Long(父类Number)
    *    float             java.lang.Float(父类Number)
    *    double            java.lang.Double(父类Number)
    *    boolean           java.lang.Boolean(父类Object)
    *    char              java.lang.Character(父类Object)
    */
   public class IntegerTest01 {
       //入口
       public static void main(String[] args) {
           /**
            * 有没有这种需求，调用doSome()方法的时候需要传一个数字进去
            * 但是数字属于基本数据类型，而doSome()方法参数的类型是Object
            * 可见doSome()方法无法接收基本数据类型的数字，那怎么办？可以传一个数字对应的包装类进去
            * 现在新版本的idea好像可以直接往里输数字了
            */
           doSome(123);
       }
   
       public static void doSome(Object obj){
           System.out.println(obj);
       }
   }
   
   ```

   ```java
   package com.bjpowernode.javase.array;
   
   public class InterTest02 {
       public static void main(String[] args) {
           //123这个基本数据类型，进行构造方法的包装达到了:基本数据类型向引用数据类型变换
           //基本数据类型 -(转换为) -> 引用数据类型(装箱)
           Integer i =new Integer(123);
   
           //将引用数据类型--(转换为)->基本数据类型(拆箱)
           float f = i.floatValue();
           System.out.println(f);
       }
   }
   
   ```

   自动装箱和自动拆箱

   ```java
   package com.bjpowernode.javase.array;
   //很重要的面试题
   public class IntegerTest06 {
       public static void main(String[] args) {
           Integer a = 128;
           Integer b = 128;
           System.out.println(a == b); //false
   
           /**
            * java中为了提高程序的执行效率，将[-128~127]之间所有的包装对象提前创建好，放到了一个方法区的"整数型常量池"当中，
            * 目的是只要用这个区间的数据就不需要再new了，直接从整数型常量池中取出来。
            *
            * 原理：x变量中保存的对象的内存地址和y变量中保存的对象内存地址是一样的。而a和b的内存地址并不同。
            */
   
           Integer x = 127;
           Integer y = 127;
           System.out.println(x == y); //true
       }
   }
   
   ```

   ```java
   package com.bjpowernode.javase.array;
   
   /**
    * 总结一下之前所学的经典异常？
    *  空指针异常：NullPointerException
    *  类型转换异常：ClassCastException
    *  数组下标越界异常:ArrayIndexOutOfBoundsException
    *  数字格式化异常: NumberFormatException
    */
   
   public class InterTest07 {
       public static void main(String[] args) {
           //手动装箱
           Integer x = new Integer(1000);
           //手动拆箱
           int y = x.intValue();
           System.out.println(y);
   
           Integer a = new Integer("123");
           System.out.println(a);
   
   //        Integer b = new Integer("中文");
   //        System.out.println(b); //报错： NumberFormatException
       }
   }
   
   ```

7. java中对日期的处理

   ```java
   package com.bjpowernode.javase.array;
   /**
    * 1. 获取当前时间
    * 2. String --> Date
    * 3. Date --> String
    */
   
   import java.text.SimpleDateFormat;
   import java.util.Date;
   
   public class DateTest01 {
       public static void main(String[] args) throws Exception{
           //获取系统当前时间
           Date nowTime = new Date();
           System.out.println(nowTime); //Fri Mar 19 21:54:08 CST 2021
   
           //日期格式化
           //SimpleDateFormat是java.text包下的，专门负责日期格式化的
           SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
           String nowTimeStr = sdf.format(nowTime);
           System.out.println(nowTimeStr);//2021-03-19 22:05:55 859
   
           //假设现在有一个日期字符串String,怎么转成Date类型
           String time = "2008-08-08 08:08:08 888";
           SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
           Date dateTime = sdf2.parse(time);
           System.out.println(dateTime);//Fri Aug 08 08:08:08 CST 2008
       }
   }
   
   ```

   ```java
   package com.bjpowernode.javase.array;
   
   /**
    * 获取自1970年1月1日 00:00:00 000到当前系统时间的总毫秒数
    */
   public class DateTest02 {
       public static void main(String[] args) {
           //获取自1970年1月1日 00:00:00 000到当前系统时间的总毫秒数
           long nowTimeMillis = System.currentTimeMillis();
           System.out.println(nowTimeMillis);
   
           //需求：统计一个方法执行所耗费的时长
           long begin = System.currentTimeMillis(); //获取当前时间
           print();
           long end = System.currentTimeMillis();
           System.out.println("耗费时长"+(end - begin)+"毫秒");
   
   
   
       }
   
       //需求：统计一个方法执行所耗费的时长
       public static void print(){
           for(int i=0; i<100000000; i++){
               //System.out.println("i = " + i);
           }
       }
   }
   
   ```

   > 简单总结一下System类的相关属性和方法
   >
   > ```
   > System.out【out是System类的静态变量】
   > System.out.println()【println()方法不是System类的，是PrintStream类的方法】
   > System.gc()【建议开启垃圾回收器】
   > System.currentTimeMillis()【获取自1970年1月1日到系统当前时间的总毫秒数】
   > System.exit(0) 【退出JVM】
   > ```

8. 数字

   ```java
   package com.bjpowernode.javase.number;
   
   import java.text.DecimalFormat;
   
   /**
    * 数字格式化
    */
   public class DecimalFormatTest {
       public static void main(String[] args) {
           //java.text.DecimalFormat专门负责数字格式化
           /**
            * 数字格式有哪些？
            *  #代表任意数字
            *  ,代表千分位
            *  .代表小数点
            *  0代表不够时补0
            */
           DecimalFormat df = new DecimalFormat("###,###.##");
           String s = df.format(1234.56);
           System.out.println(s);
       }
   }
   //1,234.56
   ```

   ```java
   package com.bjpowernode.javase.number;
   
   import com.bjpowernode.javase.test06.B;
   
   import java.math.BigDecimal;
   
   /**
    * BigDecimal属于大数据，精度极高，不属于基本数据类型，属于java对象
    * 这是SUN提供的一个类，专门用在财务软件当中
    * 财务软件中double是不够的，所以用BigDecimal
    */
   public class BigDecimalTest02 {
       public static void main(String[] args) {
           //这个100不是普通的100，是精度极高的100
           BigDecimal v1 = new BigDecimal(100);
           //精度极高的200
           BigDecimal v2 = new BigDecimal(200);
           //求和
           //v1 + v2;这样不行，v1和v2都是引用，不能直接使用+求和。
           BigDecimal v3 = v1.add(v2);
           System.out.println(v3); //300
       }
   }
   
   ```

9. 异常处理

   ```java
   package com.bjpowernode.javase.exception;
   
   /**
    * 1. 异常在java中以类的形式存在，每一个异常类都可以创建异常对象。
    */
   public class ExceptionTest02 {
       public static void main(String[] args) {
           //通过"异常类" 实例化 "异常对象"
           NumberFormatException nfe = new NumberFormatException("数字格式化异常！");
   
           System.out.println(nfe);
   
           NullPointerException npe = new NullPointerException("空指针异常发生了！");
   
           System.out.println(npe);
       }
   }
   ```

   1. 异常以java中以类和对象的形式存在，那么异常的继承结构是怎样的？

      可以使用UML图来描述一下继承结构。画UML图有很多工具。Rational Rose(收费的)

      UML是一种统一建模语言，一种图标式语言(画图的)，UML不是只有java使用，只要是面向对象的编程语言，都有UML。软件设计人员使用的。在UML图中可以描述类和类之间的关系，程序执行的流程，对象的状态。

   2. java的异常处理机制

      Object下有Throwable(可抛出的),Throwable下有两个分支，Error(不可处理，直接退出JVM)和Exception(可处理的)。

      Exception下有两个分支：Exception的直接子类：编译时异常(要求程序员在编写程序阶段必须预先处理，否则编译器报错)。RuntimeException:运行时异常(在编写程序阶段程序员可以预先处理也可以不管)。

      java语言中对异常的处理包括两种方式：(1) 在方法声明的位置上，使用throws关键字，抛给上一级。(2) 使用try...catch语句进行异常的捕捉。java中异常发生之后如果一直上抛，最终抛给了main方法，main方法继续向上抛，抛给了调用者JVM，JVM知道这个异常发生，只有几个结果，终止java程序的执行。

      ```java
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest03 {
          public static void main(String[] args) {
              /**
               * 程序执行到此处发生了ArithmeticException异常，
               * 底层new了一个ArithmeticException异常对象，然后抛出了，
               * 由于是main方法调用了100/0，所以这个异常ArithmeticException抛给了main方法
               * main方法没有处理，将这个异常自动抛给了JVM。
               * ArithmeticException继承RuntimeException,属于运行时异常，在编写程序阶段不需要对这种异常进行预先处理。
               */
              System.out.println(100 / 0);
      
      
          }
      }
      
      ```

      ```java
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest04 {
          public static void main(String[] args) {
              //main方法中调用doSome()方法
              //因为doSome()方法声明位置上有：throws ClassNotFoundException
              //我们在调用doSome()方法的时候必须对这种异常进行预先的处理
              //如果不处理，编译器就报错。
              //doSome();报错，原因在于doSome方法的声明位置上使用了throws ClassNotFoundException
              //而ClassNotFoundException是编译时异常，必须编写代码时处理，没有处理时编译器会报错。
      
          }
      
          /**
           * doSome方法在方法声明的位置上使用了:throws ClassNotFoundException
           * 这个代码表示doSome()方法在执行过程中，有可能会出现ClassNotFoundException异常【类没找到异常】
           * 这个异常直接父类是Exception，所以ClassNotFoundException属于编译时异常。
           * @throws ClassNotFoundException
           */
          public static void doSome() throws ClassNotFoundException{
              System.out.println("doSome!!!");
      
          }
      }
      
      ```

      ```java
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest05 {
          //第一种处理方式：在方法声明的位置上继续使用:throws, 来完成异常的继续上抛，抛给调用者。
          //上抛类似于推卸责任(继续把异常传递给调用者)
          /*public static void main(String[] args) throws ClassNotFoundException {
              doSome();
      
          }*/
      
          //第二种处理方式：try...catch进行捕捉
          //捕捉等于把异常拦下了，异常真正的解决了。
          public static void main(String[] args) {
              try {
                  doSome();
              } catch (ClassNotFoundException e) {
                  e.printStackTrace();
              }
          }
      
          /**
           * doSome方法在方法声明的位置上使用了:throws ClassNotFoundException
           * 这个代码表示doSome()方法在执行过程中，有可能会出现ClassNotFoundException异常【类没找到异常】
           * 这个异常直接父类是Exception，所以ClassNotFoundException属于编译时异常。
           * @throws ClassNotFoundException
           */
          public static void doSome() throws ClassNotFoundException{
              System.out.println("doSome!!!");
      
          }
      }
      
      
      ```

      ```java
      package com.bjpowernode.javase.exception;
      
      import java.io.FileInputStream;
      import java.io.FileNotFoundException;
      import java.io.IOException;
      
      /*
      处理异常的第一种方式：在方法声明的位置上使用throws关键字抛出，谁调用我这个方法，我就抛给谁，抛给调用者来处理。
      处理异常的第二种方式：使用try...catch语句进行异常捕捉，这个异常不会上报，自己把这个事儿处理了，异常抛到此处为止，
      不再上抛了。
       */
      public class ExceptionTest06 {
          //一般不建议在main方法上使用throws，因为这个异常如果真正的发生了，一定会抛给JVM，JVM只有终止
          //异常处理机制的作用就是增强程序的健壮性，怎么能做到，异常发生了也不影响程序的执行。
          //一般main方法中的异常建议使用try...catch进行捕捉，main就不要继续上抛了。
          public static void main(String[] args) throws IOException {
              System.out.println("main begin");
              m1();
              System.out.println("main over");
          }
      
          private static void m1() throws IOException {
              System.out.println("m1 begin");
              m2();
              System.out.println("m1 begin");
          }
          //而且这里不是任意抛的，必须针对下面的FileNotFoundException进行处理
          //抛FileNotFoundException的父类IOException是可以的
          //throws后也可以写多个异常，用逗号分隔开
          private static void m2() throws IOException {
              System.out.println("m2 begin");
              //编译器报错，m3()方法声明位置上有throws FileNotFoundException
              //在这里调用m3()没有对异常进行预处理，所以编译报错，所以选择继续上抛或者捕捉异常。
              m3();
              System.out.println("m2 begin");
          }
      
          private static void m3() throws FileNotFoundException {
              //调用SUN jdk中某个类的构造方法
              /*
              编译报错的原因：
              1. 这里调用了一个构造方法: FileInputStream(String name)
              2. 这个构造方法的声明位置上有：throws FileNotFoundExcepiton
              3. 通过类的继承结构看到：FileNotFoundException父类是IOException，IOException的父类是Exception
              所以FileNotFoundException是编译时异常。编译时异常要求程序员编写程序阶段必须对它进行处理，不处理编译器就报错。
               */
      
              //第一种方式:使用throws继续上抛
              new FileInputStream("1.txt");
          }
      
      }
      
      ```

      ```java
      package com.bjpowernode.javase.exception;
      
      import java.io.FileInputStream;
      import java.io.FileNotFoundException;
      import java.io.IOException;
      
      /*
      处理异常的第一种方式：在方法声明的位置上使用throws关键字抛出，谁调用我这个方法，我就抛给谁，抛给调用者来处理。
      处理异常的第二种方式：使用try...catch语句进行异常捕捉，这个异常不会上报，自己把这个事儿处理了，异常抛到此处为止，
      不再上抛了。
       */
      public class ExceptionTest06 {
          //一般不建议在main方法上使用throws，因为这个异常如果真正的发生了，一定会抛给JVM，JVM只有终止
          //异常处理机制的作用就是增强程序的健壮性，怎么能做到，异常发生了也不影响程序的执行。
          //一般main方法中的异常建议使用try...catch进行捕捉，main就不要继续上抛了。
          public static void main(String[] args) {
              System.out.println("main begin");
              try {
                  m1();
              } catch (FileNotFoundException e) {
                  System.out.println("文件不存在，可能路径错误，也可能该文件被删除了！");
              }
              System.out.println("main over");
          }
      
          private static void m1() throws FileNotFoundException {
              System.out.println("m1 begin");
              m2();
              System.out.println("m1 begin");
          }
          //而且这里不是任意抛的，必须针对下面的FileNotFoundException进行处理
          //抛FileNotFoundException的父类IOException是可以的
          //throws后也可以写多个异常，用逗号分隔开
          private static void m2() throws FileNotFoundException {
              System.out.println("m2 begin");
              //编译器报错，m3()方法声明位置上有throws FileNotFoundException
              //在这里调用m3()没有对异常进行预处理，所以编译报错，所以选择继续上抛或者捕捉异常。
              m3();
              System.out.println("m2 begin");
          }
      
          private static void m3() throws FileNotFoundException {
              //调用SUN jdk中某个类的构造方法
              /*
              编译报错的原因：
              1. 这里调用了一个构造方法: FileInputStream(String name)
              2. 这个构造方法的声明位置上有：throws FileNotFoundExcepiton
              3. 通过类的继承结构看到：FileNotFoundException父类是IOException，IOException的父类是Exception
              所以FileNotFoundException是编译时异常。编译时异常要求程序员编写程序阶段必须对它进行处理，不处理编译器就报错。
               */
      
              //第一种方式:使用throws继续上抛
              new FileInputStream("1.txt");
          }
      
      }
      
      ```

      ```java
   package com.bjpowernode.javase.exception;
      
      import java.io.FileInputStream;
      import java.io.FileNotFoundException;
      import java.io.IOException;
      
      /*
      深入try.catch
          1.catch后面的小括号中的类型可以是具体的异常类型，也可以是该异常类型的父类型
          2.catch可以写多个，建议catch写的时候，精确的一个一个处理
          3.catch写多个时候，从上到下，必须遵守从小到大的原则。
       */
      public class ExceptionTest07 {
          /*
          public static void main(String[] args) throws Exception{
      
          }
          */
          public static void main(String[] args) {
              /*try {
                  new FileInputStream("C:\\Users\\dministrator\\Desktop\\直推式论文\\Transductive zero-shot learning with adaptive structural embedding.pdf");
              } catch (FileNotFoundException e) {
                  System.out.println("文件不存在！");
              }
              System.out.println("hhh");
      
               */
              /*try {
                  new FileInputStream("C:\\Users\\dministrator\\Desktop\\直推式论文\\Transductive zero-shot learning with adaptive structural embedding.pdf");
              } catch (IOException e) {
                  System.out.println("文件不存在！");
              } catch (Exception e){
                  System.out.println("文件不存在！");
              }
              System.out.println("hhh");
      
               */
              try {
                  new FileInputStream("C:\\Users\\dministrator\\Desktop\\直推式论文\\Transductive zero-shot learning with adaptive structural embedding.pdf");
              } catch (FileNotFoundException | ArithmeticException | NullPointerException e) { //jdk 8的新特性
                  System.out.println("文件不存在！");
              }
              System.out.println("hhh");
          }
      
      
      
      }
      
      ```
      
      > 在开发中，选择上抛还是捕捉的原则：如果希望调用者自己处理，就上报，否则，就捕捉。
      
      ```java
      package com.bjpowernode.javase.exception;
      /*
      异常对象有两个非常重要的方法：
          1. 获取异常简单的描述信息
              String msg = exception.getMessage();
          2. 打印异常追踪的堆栈信息：
              exception.printStackTrace();
       */
      public class ExceptionTest08 {
          public static void main(String[] args) {
              NullPointerException e = new NullPointerException("空指针异常");
      
              //获取异常简单描述信息：这个信息实际上就是构造方法上面的String参数
              String msg = e.getMessage();
              System.out.println(msg); //空指针异常
      
              //打印异常堆栈信息
              e.printStackTrace(); //java.lang.NullPointerException: 空指针异常  at com.bjpowernode.javase.exception.ExceptionTest08.main(ExceptionTest08.java:11)
      
              System.out.println("Hello World!");
      
      
          }
      }
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      
      import java.io.FileInputStream;
      import java.io.FileNotFoundException;
      
      /*
      异常对象的两个方法：
          String msg = e.getMessage();
          e.printStackTrace();
       */
      public class ExceptionTest09 {
          public static void main(String[] args) {
              try {
                  m1();
              } catch (FileNotFoundException e) {
                  //获取异常的简单描述信息
                  String msg = e.getMessage();
                  System.out.println(msg);
      
                  //打印异常堆栈追踪信息！
                  //在实际开发中，建议使用这个
                  e.printStackTrace();//这行代码要写上，不然出问题了你也不知道
              }
              //这里程序不耽误执行，很健壮，服务器不会因为遇到异常而宕机
              System.out.println("Hello");
          }
      
          private static void m1() throws FileNotFoundException {
              m2();
          }
      
          private static void m2() throws FileNotFoundException {
              m3();
          }
      
          private static void m3() throws FileNotFoundException {
              new FileInputStream("C:\\Users\\Aministrator\\Desktop\\直推式论文\\Transductive zero-shot learning with adaptive structural embedding.pdf");
          }
      }
      /*
      D:\Java\JDK\bin\java.exe "-javaagent:D:\Java\IntelliJ IDEA 2020.3.2\lib\idea_rt.jar=3740:D:\Java\IntelliJ IDEA 2020.3.2\bin" -Dfile.encoding=UTF-8 -classpath C:\Users\Administrator\Desktop\java_code\out\production\java_code com.bjpowernode.javase.exception.ExceptionTest09
      C:\Users\Aministrator\Desktop\直推式论文\Transductive zero-shot learning with adaptive structural embedding.pdf (系统找不到指定的路径。)
      Hello
      java.io.FileNotFoundException: C:\Users\Aministrator\Desktop\直推式论文\Transductive zero-shot learning with adaptive structural embedding.pdf (系统找不到指定的路径。)
      	at java.base/java.io.FileInputStream.open0(Native Method)
      	at java.base/java.io.FileInputStream.open(FileInputStream.java:211)
      	at java.base/java.io.FileInputStream.<init>(FileInputStream.java:153)
      	at java.base/java.io.FileInputStream.<init>(FileInputStream.java:108)
      	at com.bjpowernode.javase.exception.ExceptionTest09.m3(ExceptionTest09.java:37)
      	at com.bjpowernode.javase.exception.ExceptionTest09.m2(ExceptionTest09.java:33)
      	at com.bjpowernode.javase.exception.ExceptionTest09.m1(ExceptionTest09.java:29)
      	at com.bjpowernode.javase.exception.ExceptionTest09.main(ExceptionTest09.java:14)
       */
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      
      import java.io.FileInputStream;
      import java.io.FileNotFoundException;
      import java.io.IOException;
      
      /*
      关于try...catch中的finally子句：
          1. 在finally子句中的代码是最后执行的，并且是一定会执行的，即使try语句块中的代码出现了异常
             finally子句必须和try一起出现，不能单独编写。
          2. finally语句通常在那些情况下？
       */
      public class ExceptionTest10 {
          public static void main(String[] args) {
              FileInputStream fis = null;//声明位置放到try外面，这样在finally中才能用。
              try {
                  //创建输入流对象
                  fis = new FileInputStream("dfegje");
      
                  String s = null;
                  //这里一定会出现空指针异常
                  s.toString();
      
                  //流使用完之后需要关闭，因为流是占用资源的.
                  //即使以上程序出现了异常，流也必须要关闭！
                  //放在这里有可能流关不了。
                  fis.close();
              } catch (FileNotFoundException e) {
                  e.printStackTrace();
              } catch (IOException e){
      
              } finally {
                  //流的关闭放在这里比较保险
                  //finally中的代码中是一定会执行的，即使try中出现了异常！
                  if(fis != null){
                      try {
                          //close()方法有异常，采用捕捉的方式
                          fis.close();
                      } catch (IOException e) {
                          e.printStackTrace();
                      }
                  }
      
      
              }
          }
      }
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest11 {
          public static void main(String[] args) {
              /*
              try和finally可以配合使用，不用有catch。
              try可以单独使用
              以下代码的执行顺序：
                  先执行try...
                  再执行finally...
                  最后执行return
               */
      
              try{
                  System.out.println("try...");
                  return;
              } finally {
                  System.out.println("finally...");
              }
      
              //这里不能写语句，因为这个代码无法访问到
      //        System.out.println("hello");
          }
      }
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest12 {
          public static void main(String[] args) {
              try{
                  System.out.println("try...");
                  //退出JVM
                  System.exit(0); //退出JVM之后，finally语句中的代码就不执行了
              }finally{
                  System.out.println("finally...");
              }
          }
      }
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      /*
      finally面试题******
       */
      public class ExceptionTest13 {
          public static void main(String[] args) {
              int result = m();
              System.out.println(result); // 100,而不是101
          }
          /*
          java语法规则有些是不能破坏的，一旦这么说了，就必须这么做
              java中，方法体重的代码必须遵循自上而下顺序依次逐行执行
              java中，return语句一旦执行，整个方法必须结束
           */
      
          public static int m() {
              int i = 100;
              try{
                  return i;
              } finally {
                  i++;
              }
          }
      
      }
      /*
      反编译之后的效果
      public static int m(){
          int i = 100;
          int j = i;
          i++;
          return j;
      
      }
       */
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      /*
      final finally finalize有什么区别？
      
       */
      public class ExceptionTest14 {
          public static void main(String[] args) {
              //final是一个关键字，表示最终的，不变的。
              final int i = 100;
      
              //finally也是一个关键字，和try联合使用，使用在异常处理机制中
              try{
      
              } finally {
                  System.out.println("finally....");
              }
      
              //finalize是Object类中的一个方法，作为方法名出现
              //所以finalize是标识符
              //finalize()方法是JVM的GC垃圾回收器负责调用。
              Object obj;
      
          }
      
      }
      
      ```
      
      自定义异常
      
      ```java
      package com.bjpowernode.javase.exception;
      /*
      1. SUN提供的JDK内置的异常肯定是不够用的，在实际的开发中，有很多业务，这些业务
      出现异常之后，JDK中是没有的，和业务挂钩的，所以需要自定义异常
      
      2. Java中怎么自定义异常？
              两步：
                  第一步：编写一个类继承Exception或者RuntimeException
                  第二步：提供两个构造方法，一个无参的，一个带有String参数的
      
       */
      public class MyException extends Exception{ //编译时异常
      
          public MyException() {
          }
      
          public MyException(String message) {
              super(message);
          }
      }
      
      package com.bjpowernode.javase.exception;
      
      public class ExceptionTest15 {
          public static void main(String[] args) {
              //创建异常对象(只new了异常对象， 并没有手动抛出)
              MyException e = new MyException("用户名不能为空！");
      
              //打印异常堆栈信息
              e.printStackTrace();
      
              //获取异常简单描述信息
              String msg = e.getMessage();
              System.out.println(msg);
          }
      }
      
      ```
      
      ```java
      //异常最重要的例子--自定义异常在实际开发中的应用
      package com.bjpowernode.javase.exception;
      /*
      栈操作异常
       */
      public class MyStackOperationException extends Exception{
          public MyStackOperationException() {
          }
      
          public MyStackOperationException(String message) {
              super(message);
          }
      }
      
      
      package com.bjpowernode.javase.exception;
      /**
       * 1.作业题：数组模拟栈
       * 要求：
       *  1.这个栈可以存储java中的任何引用类型的数据
       *  2.在栈中提供push方法模拟压栈(栈满了，要有提示信息)
       *  3.在栈中提供pop方法模拟弹栈(栈空了，也要有提示信息)
       *  4.编写测试程序，new对象， 调用push pop反法来模拟压栈、弹栈的动作。
       *  5.假设栈的默认初始化容量是10
       *
       * 2.酒店管理系统的模拟
      
       */
      public class Mystack {
          //向栈当中存储元素，这里使用一维数组模拟
          //为什么使用Object类型数组？因为object类型的栈可以存储java中的任何引用类型的数据
          private Object[] elements;
          //栈帧，永远指向栈顶部元素
          private int index;
      
          public Object[] getElements() {
              return elements;
          }
      
          public void setElements(Object[] elements) {
              this.elements = elements;
          }
      
          public int getIndex() {
              return index;
          }
      
          public void setIndex(int index) {
              this.index = index;
          }
      
          //无参数构造方法
          public Mystack() {
              //一维数组动态初始化
              this.elements = new Object[10];
              //初始化栈帧
              this.index = -1;
          }
          //压栈的方法
          public void push(Object elements) throws MyStackOperationException {
              if(this.index >= this.elements.length - 1){
                  throw new MyStackOperationException("压栈失败，栈已满！");  //这里修稿了
      
              }
              this.index++;
              this.elements[index] = elements;
              System.out.println("压栈" + elements +"成功，栈帧指向" + index);
          }
      
          //弹栈的方法
          public void pop() throws MyStackOperationException {
              if(index < 0){
                  throw new MyStackOperationException("弹栈失败，栈已空！");
              }
              System.out.println("弹栈" + elements[index] + "元素成功，");
              index--;
              System.out.println("栈帧指向" + index);
          }
      
      }
      
      
      package com.bjpowernode.javase.exception;
      //测试改良之后的MyStack
      public class ExceptionTest16 {
          public static void main(String[] args) {
              //创建栈对象
              Mystack stack = new Mystack();
      
              //压栈
              try {
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  stack.push(new Object());
                  //这里栈满了
                  stack.push(new Object());
              } catch (MyStackOperationException e) {
                  //输出异常的简单信息
                  System.out.println(e.getMessage());
      
                  e.printStackTrace();
              }
      
              //弹栈
              try {
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  stack.pop();
                  //弹栈失败
                  stack.pop();
              } catch (MyStackOperationException e) {
                  System.out.println(e.getMessage());
                  e.printStackTrace();
              }
          }
      }
      
      ```
      
      ```java
      package com.bjpowernode.javase.exception;
      /*
      重写之后的方法不能比重写之前的方法抛出更多(更宽泛)的异常，可以更少
      
      总结异常中的关键字:
          异常捕捉：
              try
              catch
              finally
      
          throws 在方法声明位置上使用，表示上报异常信息给调用者
          throw 手动抛出异常！
      
       */
      class Animal {
          public void doSome(){
      
          }
      
          public void doOther() throws Exception{}
      
      }
      
      class Cat extends Animal {
          //编译报错
          /*public void doSome() throws Exception{
      
          }*/
      
          //编译正常
          //public void doOther(){}
      
          //编译正常
          //public void doOther() throws Exception{}
      
          //编译正常
          public void doOther() throws NullPointerException{}
      
      }
      ```

10. 集合【非常非常重要】

    1. 集合实际上就是一个容器，可以用来容纳其他类型的数据。在实际开发中，假设连接数据库，数据库当中有10条记录，那么假设把这10条记录查询出来，在java程序中会将10条数据封装成10个java对象，然后将10个java对象放到某一个集合当中，将集合传到前端，然后遍历集合，将一个数据一个数据展现出来。

    2. 集合不能直接存储基本数据类型， 另外集合也不能直接存储java对象，集合当中存储的都是java对象的内存地址。或者说集合中存储的是引用。

       ```java
       list.add(100); //自动装箱Interger
       ```

       注意：集合在java中本身是一个容器，是一个对象，集合中任何时候存储的都是“引用”。

    3. 在java中每一个不同的集合，底层会对应不同的数据结构，往不同的集合中存储元素，等于将数据放到了不同的数据结构当中【数据结构、二叉树、链表、哈希表...】

       ```java
       new ArrayList(); 创建一个集合，底层是数组
       new LinkedList(); 创建一个集合对象，底层是链表
       new TreeSet(); 创建一个集合对象，底层是二叉树
       ```

    4. 所有的集合类和集合接口都在java.util包下。

    5. 在java中集合分为两大类：

       1. 以单个形式存储元素：这一类集合中超级父接口：java.util.Collection;
       2. 以键值对的方式存储元素，这一类集合中超级父接口：java.util.Map;

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Collection;
    
    /*
    关于java.util.collection接口中常用的方法
        1. Collection中能存放什么元素？
            没有使用“泛型”之前，Collection中可以存储Object的所有子类型
            使用"泛型"之后，Collection中只能存储某个具体的类型
        2. Collection中的常用方法
            boolean add(Object e) 向集合中添加元素
            int size() 获取集合中元素的个数
            void clear() 清空集合
            boolean contains(Object o) 判断当前集合中是否包含元素哦，返回true false
            boolean remove(Object o) 删除集合中的某个元素
            boolean isEmpty() 判断集合是否为空
            Object[] toAray() 调用这个方法可以把集合转换成数组
     */
    public class CollectionTest01 {
        public static void main(String[] args) {
            //创建一个集合对象
            //Collection c = new Collection(); 接口是抽象的，无法new对象
            //多态
            Collection c = new ArrayList();
            //测试Collection接口中的常用方法
            c.add(1200); //自动装箱，实际上放进去了一个对象的内存地址
            c.add(3.14);
            c.add(new Object());
            c.add(true);
    
            //获取集合中元素的个数
            System.out.println("集合中元素个数是:" + c.size());//4
    
            //清空集合
            c.clear();
            System.out.println("集合中元素个数是:" + c.size());//0
    
            c.add("绿巨人");
    
            //判断集合中是否包含绿巨人
            boolean flag = c.contains("绿巨人");
            System.out.println(flag); //true
    
            //删除集合中某个元素
            c.remove("绿巨人");
            System.out.println("集合中元素个数是:" + c.size());//0
    
            //判断集合是否为空
            System.out.println(c.isEmpty()); //true
    
            c.add("abc");
            c.add("def");
            c.add(100);
            //转换成数组
            Object[] objs = c.toArray();
            for(int i = 0; i < objs.length; i++){
                System.out.println(objs[i]);
            }
            
    
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.sql.SQLOutput;
    import java.util.ArrayList;
    import java.util.Collection;
    import java.util.HashSet;
    import java.util.Iterator;
    
    /**
     * 集合遍历/迭代专题(重点)
     *
     */
    
    public class CollectionTest02 {
        public static void main(String[] args) {
            //创建集合对象
            Collection c = new ArrayList();
            //添加元素
            c.add("abc");
            c.add("def");
            c.add(100);
            c.add(new Object());
    
            //对集合Collection进行遍历/迭代
            //第一步：获取集合对象的迭代器对象Iterator
            Iterator it = c.iterator();
            //第二步：通过以上获取的迭代器对象开始迭代/遍历集合
            /*
            以下两个方法是迭代器对象Iterator中的方法：
                boolean hasNext() 如果仍有元素可以迭代，则返回true
                Object next() 返回迭代的下一个元素
             */
            while(it.hasNext()){
                System.out.println(it.next());
            }
    
    
    
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Collection;
    import java.util.HashSet;
    import java.util.Iterator;
    
    public class CollectionTest03 {
        public static void main(String[] args) {
            //创建集合对象
            Collection c1 = new ArrayList(); //有序可重复
    
            //添加元素
            c1.add(1);
            c1.add(2);
            c1.add(3);
            c1.add(4);
    
            //迭代集合
            Iterator it = c1.iterator();
            while(it.hasNext()){
                System.out.println(it.next());
            }
    
            //HashSet集合：无序不可重复
            Collection c2 = new HashSet();
            c2.add(100);
            c2.add(200);
            c2.add(300);
            c2.add(400);
            Iterator it2 = c2.iterator();
            while(it2.hasNext()){
                System.out.println(it2.next());
            }
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Collection;
    
    /*
    深入Collection集合的contains方法
        boolean contains(Object o) 判断集合中是否包含某个对象o
        在底层是调用了equals方法进行比对
        如果包含返回true，如果不包含返回false
     */
    public class CollectionTest04 {
        public static void main(String[] args) {
            //创建集合对象
            Collection c = new ArrayList();
    
            //向集合中存储元素
            String a = new String("abc");
            System.out.println(a);
            c.add(a);
            c.add(new String("def"));
    
            String x = new String("abc");
            System.out.println(x);
            System.out.println(c.contains(x));  // true
            System.out.println(a == x); // false
    
        }
    }
    //总结：放在集合中的元素要重写equals方法。
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Collection;
    import java.util.Iterator;
    
    public class CollectionTest06 {
        public static void main(String[] args) {
            //创建集合
            Collection c = new ArrayList();
    
            //注意：此时获取的迭代器，指向的是集合中没有元素状态下的迭代器
            //一定要注意：集合结构只要发生改变，迭代器必须重新获取。
            //当集合结构发生了改变，迭代器没有重新获取时，调用next()方法时，会出现
            //java.util.ConcurrentModificationException异常
            //Iterator it = c.iterator();
    
            //添加元素
            c.add(1);
            c.add(2);
            c.add(3);
    
            //获取迭代器
            Iterator it = c.iterator();
            while (it.hasNext()){
                //编写代码时next()方法返回值类型必须是Object
                //Integer i = it.next();
                Object obj = it.next();
                System.out.println(obj);
            }
    
            Collection c2 = new ArrayList();
            c2.add("abc");
            c2.add("def");
            c2.add("xyz");
    
            Iterator it2 = c2.iterator();
            while(it2.hasNext()){
                Object o = it2.next();
                //删除元素，集合结构发生变化
                //在迭代集合元素的过程中，不能调用集合对象的remove方法，删除元素。
                //c2.remove(o);// java.util.ConcurrentModificationException，直接通过集合去删除元素，没有通知迭代器
    
                //使用迭代器来删除可以吗？可以，而且在迭代元素的过程中，一定要使用迭代器Iterator删除元素。
                it2.remove();//删除的一定是迭代器指向的当前元素
                System.out.println(o);
            }
            System.out.println(c2.size());  //0
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.*;
    
    /*
    测试list接口中常用方法
        1. List集合存储元素特点：有序可重复
        2. List既然是Collection接口的子接口，那么肯定List接口有自己“特色”的方法：
            void add(int index, E element)
            E get(int index)
            int indexOf(Object o)
            int lastIndexOf(Object o)
            E remove(int index)
            E set(int index, E element)
     */
    public class ListTest01 {
        public static void main(String[] args) {
            // List mylist = new LinkedList();
            // List myList = new Vector();
            List myList = new ArrayList();
    
            // 添加元素
            myList.add("A");
            myList.add("B");
            myList.add("C");
            myList.add("D");
    
            //在列表指定位置插入指定元素(第一个参数是下标)
            myList.add(1, "King");
    
    //        //迭代
    //        Iterator it = myList.iterator();
    //        while(it.hasNext()){
    //            Object elt = it.next();
    //            System.out.println(elt);
    //        }
    
    //        //根据下标获取元素
    //        Object firstObj = myList.get(0);
    //        System.out.println(firstObj);
    
            //因为有下标，所以List集合有自己比较特殊的遍历方式
            //通过下标遍历【List集合特有的方式，Set没有】
            for(int i=0; i<myList.size(); i++){
                Object obj = myList.get(i);
                System.out.println(obj);
            }
            System.out.println();
    
            //获取指定对象第一次出现处的索引
            System.out.println(myList.indexOf("King"));
    
            //获取指定对象最后一次出现处的索引
            System.out.println(myList.lastIndexOf("C"));
    
            //删除指定下标位置的元素
            myList.remove(0);
            System.out.println(myList.size());
    
            //修改指定位置元素
            myList.set(2, "Sort");
    
    
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.List;
    
    /*
    ArrayList集合：
        1. 默认初始化容量为10(底层先创建了一个长度为0的数组，当添加第一个元素的时候，初始化容量10)
        2. 集合底层是一个Object[]数组
        3. 构造方法：
            new ArrayList();
            new ArrayList(20);
        4. ArrayList集合的扩容：
            原容量的1.5倍
            ArrayList集合底层是数组，怎么优化？尽可能少的扩容。因为数组扩容效率比较低，建议在使用ArrayList时预估初始化容量。
        5. 面试题：这么多的集合中，你用哪个集合最多？答：ArrayList集合。另外检索查找的操作比较多。
    
     */
    public class ArrayListTest01 {
        public static void main(String[] args) {
            List list1 = new ArrayList();
            //size()方法是获取当前集合中元素的个数，不是获取集合的容量
            System.out.println(list1.size());//0
    
    
            //指定初始化容量
            List list2 = new ArrayList(20);
            System.out.println(list2.size());//0
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Collection;
    import java.util.HashSet;
    import java.util.List;
    
    /*
    集合ArrayList的构造方法
     */
    public class ArrayListTest02 {
        public static void main(String[] args) {
            List myList1 = new ArrayList();
            List myList2 = new ArrayList(100);
    
            // 创建一个HashSet集合
            Collection c = new HashSet();
            c.add(100);
            c.add(200);
            c.add(900);
            c.add(50);
    
            //通过这个构造方法可以将HashSet集合转换成List集合。
            List myList3 = new ArrayList(c);
    
    
    
        }
    }
    
    ```

    对于链表数据结构来说：基本单元是节点Node。

    对于单向链表来说，任何一个节点Node中都有两个属性：第一：存储的数据。第二：下一节点的内存地址。

    ![image-20210331203724967](https://i.loli.net/2021/03/31/aKQjAhx5sF3gT6r.png)

    链表优点：由于链表上的元素在空间存储上内存地址不连续，随机增删元素效率较高(因为增删元素不涉及到大量元素位移)，在以后的开发中，如果遇到随机增删集合中元素的业务较多时，使用LinkedList。

    链表缺点：查询效率较低，每一次查找某个元素的时候都需要从头节点开始往下遍历。直到找到为止，所以LinkedList集合检索/查找的效率较低。

    ```java
    package com.bjpowernode.javase.collection;
    
    
    
    /*
    单链表中的节点
    节点是单向链表中基本的单元。
    每一个节点node都有两个属性：一个属性是存储的数据，另一个属性是下一个节点的内存地址。
     */
    public class Node {
        //存储的数据
        Object element;
    
        //下一个节点的内存地址
        Node next;
    
        public Node() {
        }
    
        public Node(Object element, Node next) {
            this.element = element;
            this.next = next;
        }
    }
    
    package com.bjpowernode.javase.collection;
    
    
    
    public class Link {
        Node header;
    
        int size = 0;
        public int size(){
            return size;
        }
    
        //向链表中添加元素的方法
        public void add(Object element){
            //创建一个新的节点对象
            //让之前单链表的末尾节点next指向新节点对象
            if(header == null){
                //说明没有节点
                //new一个新的节点对象，作为头节点对象
                //这个时候的头节点既是一个头节点，又是一个末尾节点。
                header = new Node(element, null);
            }else{
                // 说明头不是空！
                //说明头节点已经存在了
                //找出当前末尾节点，让当前末尾节点的next是新节点
                Node currentLastNode = findLast(header);
                currentLastNode.next = new Node(element, null);
    
            }
            size++;
    
        }
        //专门查找末尾节点的方法
        private Node findLast(Node node) {  //递归
            if(node.next == null){
                //如果一个节点的next是null，说明这个节点就是末尾节点
                return node;
            }
            return findLast(node.next);
        }
    
        //删除链表中某个数据的方法
        public void remove(Object obj){
    
        }
    
        //修改链表中某个数据的方法
        public void modify(Object newObj){
    
        }
    
    
    }
    
    
    package com.bjpowernode.javase.collection;
    
    public class Test {
        public static void main(String[] args) {
            Link link = new Link();
            link.add(100);
            link.add(200);
            link.add(300);
            System.out.println(link.size());
    
        }
    }
    
    ```

    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.*;
    
    /*
    Vector:
        1. 底层也是一个数组
        2. 初始化容量：10
        3. 怎么扩容：扩容之后是原容量的2倍
        4. ArrayList扩容之后是原容量的1.5倍
        5. Vector中所有的方法都是线程同步的，都带有synchronized关键字，线程安全，现在使用较少。
        6. 怎么将一个线程不安全的ArrayList集合转换成线程安全的呢？
            java.util.Collections;
    
            java.util.Collection是集合接口
            java.util.Collection是集合工具类。
     */
    public class VectorTest {
        public static void main(String[] args) {
            //创建一个集合
            List vector = new Vector();
    
            //添加元素
            //默认容量10个
            vector.add(1);
            vector.add(2);
            vector.add(3);
            vector.add(4);
            vector.add(5);
            vector.add(6);
            vector.add(7);
            vector.add(8);
            vector.add(9);
            vector.add(10);
    
            //满了之后扩容
            vector.add(11);
    
            Iterator it = vector.iterator();
            while(it.hasNext()){
                System.out.println(it.next());
            }
    
            //这个可能以后要使用！
            List myList = new ArrayList(); // 非线程安全的
            // 变成线程安全的
            Collections.synchronizedList(myList);  //先记住
            // myList集合就是线程安全的了。
    
            myList.add("111");
            myList.add("222");
            myList.add("222");
    
    
    
    
        }
    
    }
    
    ```
    
    泛型
    
    ```java
    //不使用泛型
    package com.bjpowernode.javase.collection;
    
    import com.bjpowernode.javase.test06.A;
    
    import java.util.ArrayList;
    import java.util.Iterator;
    import java.util.List;
    
    /*
    JDK5.0之后推出的新特性：泛型
     */
    public class GenericTest01 {
        public static void main(String[] args) {
            // 不使用泛型，分析程序存在缺点
            List mylist = new ArrayList();
    
            // 准备对象
            Cat c = new Cat();
            Bird b = new Bird();
    
            //将对象添加到集合当中
            mylist.add(c);
            mylist.add(b);
    
            //遍历集合，取出每个Animal，让它move
            Iterator it = mylist.iterator();
            while(it.hasNext()){
                //通过迭代器取出的就是Object
                Object obj = it.next();
                //obj 中没有move方法，无法调用，需要向下转型
                if(obj instanceof Animal){
                    Animal a = (Animal) obj;
                    a.move();
                }
            }
    
        }
    }
    
    class Animal{
        public void move(){
            System.out.println("动物在移动！");
        }
    }
    
    class Cat extends Animal{
        public void catchMouse(){
            System.out.println("猫抓老鼠");
        }
    
    }
    
    class Bird extends Animal{
        public void fly(){
            System.out.println("鸟儿在飞翔");
        }
    
    }
    
    //使用泛型
    package com.bjpowernode.javase.collection;
    
    import com.bjpowernode.javase.test06.A;
    
    import java.util.ArrayList;
    import java.util.Iterator;
    import java.util.List;
    
    /*
    1. JDK5.0之后推出的新特性：泛型
    2. 泛型这种与法制机，只在程序编译阶段起作用，只是给编译器参考的，运行阶段泛型没用。
     */
    public class GenericTest01 {
        public static void main(String[] args) {
            //使用JDK之后的泛型机制
            //使用泛型List<Animal>之后，表示List集合中只允许存储Animal类型的数据。存储别的就报错了
            List<Animal> mylist = new ArrayList<Animal>();
            //mylist.add("abc");报错
            Cat c = new Cat();
            Bird b = new Bird();
            mylist.add(c);
            mylist.add(b);
    
            //获取迭代器
            //<Animal>表示迭代的是Animal类型
            Iterator<Animal> it = mylist.iterator();
            while (it.hasNext()){
                //使用泛型之后，每一次迭代返回的数据都是Animal类型
                //Animal a = it.next();
                //这里不需要进行强制类型转换了，直接调用。
                //a.move();
                // 调用子类型特有的方法还是需要向下转型的
    
                Animal a = it.next();
                if(a instanceof Cat){
                    Cat x = (Cat)a;
                    x.catchMouse();
                }
                if(a instanceof Bird){
                    Bird y = (Bird)a;
                    y.fly();
                }
            }
    
        }
    }
    
    class Animal{
        public void move(){
            System.out.println("动物在移动！");
        }
    }
    
    class Cat extends Animal{
        public void catchMouse(){
            System.out.println("猫抓老鼠");
        }
    
    }
    
    class Bird extends Animal{
        public void fly(){
            System.out.println("鸟儿在飞翔");
        }
    
    }
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Iterator;
    import java.util.List;
    
    /*
    JDK之后引入了：自动类型推断机制.(又称为钻石表达式)
     */
    public class GenericTestTest02 {
        public static void main(String[] args) {
            // ArrayList<这里的类型会自动推断>，前提是JDK8之后才允许。
            // 自动类型推断，钻石表达式！
            List<Animal> mylist = new ArrayList<>();
    
            mylist.add(new Animal());
            mylist.add(new Cat());
            mylist.add(new Bird());
    
            //遍历
            Iterator<Animal> it = mylist.iterator();
            while (it.hasNext()){
                Animal a = it.next();
                a.move();
            }
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    /*
    自定义泛型可以吗？可以
    泛型：把类型明确的工作推迟到创建对象或调用方法的时候才去明确的特殊类型
    自定义泛型的时候，<>尖括号中的是一个标识符，随便写
    java源代码中经常出现的是：<E> 和 <T>, E是Element单词，T是Type单词。
     */
    public class GenericTest03<A> {  //<标识符随便写>
        public void doSome(A o){
            System.out.println(o);
        }
    
        public static void main(String[] args) {
            //new对象的时候指定了泛型：String类型
            GenericTest03<String> gt = new GenericTest03<>();
            gt.doSome("abc");
            //gt.doSome(100); 类型不匹配
    
            //-----------------------------------------------
            GenericTest03<Integer> gt2 = new GenericTest03<>();
            gt2.doSome(100);
    
            MyIterator<String> mi = new MyIterator<>();
            String s1 = mi.get();
    
            MyIterator<Animal> mi2 = new MyIterator<>();
            Animal a = mi2.get();
        }
    }
    
    
    class MyIterator<T>{
        public T get(){
            return null;
        }
    }
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.ArrayList;
    import java.util.Iterator;
    import java.util.List;
    
    /*
    集合使用foreach
     */
    public class ForEachTest02 {
        public static void main(String[] args) {
            // 创建List集合
            List<String> strList = new ArrayList<>();
            // 添加元素
            strList.add("hello");
            strList.add("world!");
            strList.add("kitty!");
            //遍历，使用迭代器方式
            Iterator<String> it = strList.iterator();
            while(it.hasNext()){
                String s = it.next();
                System.out.println(s);
            }
            //使用下标方式(只针对有下标的集合)
            for(int i=0; i<strList.size(); i++){
                System.out.println(strList.get(i));
            }
            // 使用foreach
            for(String s : strList){ // 因为泛型使用的是String类型，所以是：String s
                System.out.println(s);
            }
    
            List<Integer> list = new ArrayList<>();
            list.add(100);
            list.add(200);
            list.add(300);
            for(Integer i : list){
                System.out.println(i);
            }
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.HashSet;
    import java.util.Set;
    
    /*
    HashSet集合： 无序不可重复
    
    1. 存储时顺序和取出顺序不同
    2. 不可重复
    3. 放到HashSet集合中的元素实际上是放到HashMap集合的key部分了。
     */
    public class HashSetTest01 {
        public static void main(String[] args) {
            //演示一下HashSet集合特点
            Set<String> strs = new HashSet<>();
    
            //添加元素
            strs.add("hello3");
            strs.add("hello4");
            strs.add("hello1");
            strs.add("hello2");
            strs.add("hello3");
            strs.add("hello3");
            strs.add("hello3");
            strs.add("hello3");
    
            //遍历
            for(String s : strs){
                System.out.println(s);
            }
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Set;
    import java.util.TreeSet;
    
    /*
    TreeSet集合存储元素特点：
        1. 无序不可重复，但是存储的元素可以自动按照大小顺序排序
        称为：可排序集合。
        2. 这里的无序指的是存进去的顺序和取出来的顺序不同，并且没有下标
    
     */
    public class TreeSetTest01 {
        public static void main(String[] args) {
            //创建集合对象
            Set<String> strs = new TreeSet<>();
            //添加元素
            strs.add("A");
            strs.add("B");
            strs.add("C");
            strs.add("Z");
            strs.add("Y");
            strs.add("Z");
            strs.add("K");
    
            //遍历
            for (String s :strs){
                System.out.println(s);
                /*
                A
                B
                C
                K
                Y
                Z
                 */
            }
        }
    }
    
    ```
    
    Map
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.HashSet;
    import java.util.Set;
    
    public class MyClass {
        // 声明一个静态内部类
        private static class InnerClass{
            //静态方法
            public static void m1(){
                System.out.println("静态内部类的m1方法执行");
            }
            // 实例方法
            public void m2(){
                System.out.println("静态内部类中的实例方法执行");
            }
        }
    
        public static void main(String[] args){
            // 类名叫做：MyClass.InnerClass
            MyClass.InnerClass.m1();
            // 创建静态内部类对象
            MyClass.InnerClass mi = new MyClass.InnerClass();
            mi.m2();
    
            //给一个Set集合
            //该Set集合中存储的对象是：MyClass.InnerClass类型
            Set<InnerClass> set = new HashSet<>();
    
            //这个集合中存储的是字符串对象
            Set<String> set2 = new HashSet<>();
    
            Set<MyMap.MyEntry<Integer, String>> set3 = new HashSet<>();
        }
    }
    
    
    class MyMap{
        public static class MyEntry<K,V>{
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Collection;
    import java.util.HashMap;
    import java.util.Map;
    
    /*
    java.util.Map接口中常用的方法：
        1. Map和Collection没有继承关系
        2. Map集合以key和value的方式存储数据：键值对
            key和value都是引用数据类型
            key和value都是存储对象的内存地址
        3. Map接口中常用方法:
            V put(K key, V value)  向Map集合中添加键值对
            V get(Object key)  key获取value
            void clear()  清空map集合
            boolean containsKey(Object key)  判断Map中是否包含某个key
            boolean containsValue(Object value)  判断Map中是否包含某个value
            boolean isEmpty()  Map集合中元素个数是否为0
            Set<K> keySet()  获取Map集合所有的key
    
    
            V remove(Object key)  通过key删除键值对
            int size()  获取Map集合中键值对的个数
            Collection<V> values()  获取Map集合中所有的value，返回一个collection
            Set<Map.entry<K,V>> entrySet()  将Map集合转换成Set集合
                map集合：
                key             value
                ------------------------
                1                 zhangsan
                2                 lisi
                3                 wangwu
                4                 zhaoliu
    
                Set set = map1.entrySet();
                set集合对象
                1=zhangsan 【注意：Map集合通过entrySet()方法转换成的这个Set集合，Set集合中元素的类型是Map.Entry<K,V>】
                2=lisi     【Map.Entry和String一样，都是一种类型的名字，只不过：Map.Entry是静态内部类，是Map中的静态内部类】
                3=wangwu
                4=zhaoliu --> 这个东西是个什么？Map.Entry
     */
    public class MapTest01 {
        public static void main(String[] args) {
            // 创建Map集合对象
            Map<Integer, String> map = new HashMap<>();
            // 向Map集合中添加键值对
            map.put(1, "zhangsan");  //1在这里进行了自动装箱。
            map.put(2, "lisi");
            map.put(3, "wangwu");
            map.put(4, "zhaoliu");
            //通过key获取value
            String value = map.get(2);
            System.out.println(value);//lisi
            //获取键值对的数量
            System.out.println("键值对数量：" + map.size());
            //通过key删除key-value
            map.remove(2);
            System.out.println("键值对数量：" + map.size());
            //判断是否包含某个key
            //contains方法底层调用的都是equals进行比对的，所以自定义的类型需要重写equals方法。
            System.out.println(map.containsKey(4));//true
            //判断是否包含某个value
            System.out.println(map.containsValue("wangwu"));//true
            //获取所有的value
            Collection <String> values = map.values();
            for(String s:values){
                System.out.println(s);
            }
    
            //清空map集合
            map.clear();
            System.out.println("键值对的数量：" + map.size());
            //判断是否为空
            System.out.println(map.isEmpty());
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.HashMap;
    import java.util.Iterator;
    import java.util.Map;
    import java.util.Set;
    
    /*
    Map集合的遍历【非常中庸】
     */
    public class MapTest02 {
        public static void main(String[] args) {
            //第一种方式：获取所有的key，通过遍历key，来遍历value
            Map<Integer, String> map = new HashMap<>();
            map.put(1, "zhangsan");  //1在这里进行了自动装箱。
            map.put(2, "lisi");
            map.put(3, "wangwu");
            map.put(4, "zhaoliu");
            //遍历map集合
            //获取所有的key，所有的key是一个Set集合
            Set<Integer> keys = map.keySet();
            //遍历key，通过key获取value
            Iterator<Integer> it = keys.iterator();
            while(it.hasNext()){
                Integer key = it.next();
                String value = map.get(key);
                //System.out.println(key + "=" + value);
            }
            //foreach也可以
            for(Integer key:keys){
                System.out.println(key + "=" + map.get(key));
            }
    
            //第二种方式：Set<Map.Entry<K,V>> entrySet()
            //以上这个方法是把Map集合直接全部转换成Set集合
            //Set集合中元素的类型是：Map.Entry
            Set<Map.Entry<Integer, String>> set = map.entrySet();
            // 遍历Set集合，每一次取出一个Node
            // 迭代器
            Iterator<Map.Entry<Integer, String>> it2 = set.iterator();
            while(it2.hasNext()){
                Map.Entry<Integer, String> node = it2.next();
                Integer key = node.getKey();
                String value = node.getValue();
                System.out.println(key + "=" + value);
            }
    
            //foreach
            for(Map.Entry<Integer, String> node : set){
                System.out.println(node.getKey() + "=" + node.getValue());
            }
    
        }
    }
    
    ```
    
    哈希表数据结构
    
    ![image-20210403182847898](https://i.loli.net/2021/04/03/yMdYiLsJUGmAOpt.png)
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.HashMap;
    import java.util.Map;
    import java.util.Set;
    
    /*
    HashMap集合：
        1. HashMap集合底层是哈希表/散列表的数据结构
        2. 哈希表是一个怎样的数据结构？
            哈希表是数组是单向链表的结合体
            数组：在查询方面效率很高，随机增删方面效率很低
            单向链表：在随机增删方面效率较高，在查询方面效率很低。
            哈希表将以上的两种数据结构融合在一起，充分发挥它们各自的优点。
        3. HashMap集合的底层的源代码：
            public class HashMap{
                //HashMap底层实际上就是一个数组(一维数组)
                Node<K,V>[] table;
    
                //静态的内部类HashMap.Node
                static class Node<K,V>{
                    final int hash; //哈希值(哈希值是key的hashCode()方法的执行结果。hash值通过哈希函数/算法，可以转换存储成数组的下标)
                    final K key; //存储到Map集合中的key
                    v value; //存储到Map集合中的Value
                    Node<K,V> next;// 下一个节点的内存地址
                }
            }
            哈希表/散列表： 一维数组，这个数组中每一个元素是一个单向链表。(数组和链表的结合体)
        4. 最主要掌握的是：
            map.put(k,v)
            v = map.get(k)
            以上这两个方法的实验原理是必须掌握的
        5. HashMap集合的key部分特点：
            无序，不可重复
            为什么无序？因为不一定挂到哪个单向链表上
            不可重复是怎么保证的？equals方法来保证HashMap集合的key不可重复，如果key重复了，value会覆盖
            放在HashMap集合key部分的元素其实就是放到HashSet集合中了，所以HashSet集合中的元素也需要同时重写hashCode()+equals()方法。
        6. 哈希表HashMap使用不当时无法发挥性能！
            假设将所有的hashCode()方法返回值固定伪某个值，那么会导致底层哈希表变成了纯单向链表。这种情况我们称为散列分布不均匀。
            什么是散列分布均匀？
                假设有100个元素，10个单向链表，那么每个单向链表上有10个节点，这是最好的，即散列分布均匀的
                假设将所有的hashCode()方法返回值都设定为不一样的值，那就变成一个一维数组
            所以，散列分布均匀需要重写hashCode()方法时有一定的技巧。
        7. 重点：放在HashCode集合key部分的元素，以及放在HashSet集合中的元素，需要同时重写hashCode和equals方法。
        8. HashMap集合的默认初始化容量是16，默认加载因子是0.75
            这个默认加载因子是当HashMap集合底层数组的容量达到75%的时候，数组开始扩容。
            重点：记住：HashMap集合初始化容量必须是2的倍数，这也是官方推荐的
            这是因为达到散列均匀，为了提高HashMap集合的存取效率，所必须的。
     */
    public class HashMapTest01 {
        public static void main(String[] args) {
            // 测试HashMap集合key部分的元素特点
            // Integer是key，它的hashCode和equals都重写了
            Map<Integer,String> map= new HashMap<>();
            map.put(1111, "zhangsan");
            map.put(6666, "lisi");
            map.put(7777, "wangwu");
            map.put(2222, "zhaoliu");
            map.put(2222, "king");  //key重复的时候value会自动覆盖
    
            System.out.println(map.size());
    
            Set<Map.Entry<Integer, String>> set = map.entrySet();
            for(Map.Entry<Integer, String> entry:set){
                //验证结果：HashMap集合key部分元素：无序不可重复
                System.out.println(entry.getKey() + "=" + entry.getValue());
            }
        }
    }
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Objects;
    
    public class Student {
        private String name;
        public Student(){
    
        }
        public Student(String name){
            this.name = name;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
        // hashCode
        // equals
    //    public boolean equals(Object obj){
    //        if(obj == null || !(obj instanceof Student)) return false;
    //        if(obj == this) return true;
    //        Student s = (Student) obj;
    //        //这个equals调用的是字符串的equals
    //        if(this.name.equals(s.name)) return true;
    //        return false;
    
        @Override
        public boolean equals(Object o) {
            if (this == o) return true;
            if (!(o instanceof Student)) return false;
            Student student = (Student) o;
            return Objects.equals(name, student.name);
        }
    
        @Override
        public int hashCode() {
            return Objects.hash(name);
        }
    }
    
    package com.bjpowernode.javase.collection;
    
    import java.util.HashSet;
    import java.util.Set;
    /*
    注意：如果一个类的equals方法重写了，那么hashCode()方法必须重写。
    并且equals方法返回true，hashCode()方法的返回值必须一样。
        equals方法返回true表示两个对象相同，在同一个单向链表上比较，
        那么对于同一个单向链表上的节点来说，他们的哈希值都是相同的。
        所以hashCode()方法的返回值也应该是相同的。
    
    hashCode()方法和equals()方法不用研究了，直接使用IDEA生成，但是这两个方法需要同时生成。
    
    结论：放在HashMap集合key部分的，以及放在HashSet集合中的元素，需要同时重写hashCode方法和equals方法
    
    在JDK6之后，如果哈希表单向链表中元素超过8个，单向链表会变成红黑树数据结构，当红黑树上的节点数量小于6时，会重新把红黑树变成单向链表数据结构。
     */
    public class HashMapTest02 {
        public static void main(String[] args) {
            Student s1 = new Student("zhangsan");
            Student s2 = new Student("zhangsan");
    
    
            //重写equals方法之前是false
            System.out.println(s1.equals(s2));//false
    
            //重写equals方法之后是true
            System.out.println(s1.equals(s2));//true
    
            System.out.println("s1的hashCode=" + s1.hashCode());//s1的hashCode=2129789493(重写hashCode之后是s1的hashCode=-1432604525)
            System.out.println("s2的hashCode=" + s2.hashCode());//s2的hashCode=1313922862(重写hashCode之后是s2的hashCode=-1432604525)
    
            //s1.equals(s2)结果已经是true了，表示s1和s2是一样的，相同的，那么往HashSet集合中放的话，按说
            //只能放进去1个(HashSet集合特点：无序不可重复)
            Set<Student> students = new HashSet<>();
            students.add(s1);
            students.add(s2);
            System.out.println(students.size());//这个结果按理应该说是1，但是实际结果是2.
            /*向Map集合中存，以及从Map集合中取，都是先调用key的hashCode方法，然后再调用equals方法！equals方法有可能调用，也有可能不调用。
                拿put(k,v)举例，什么时候equals不会调用？
                    k.hashCode()方法返回哈希值
                    哈希值经过哈希算法转换成数组下标
                    数组下标位置上如果是null，equals不需要执行。
                拿get(k)举例，什么时候equals不会调用？
                    哈希值经过哈希算法转换成数组下标
                    数组下标位置上如果是null，equals不需要执行。
    
    
             */
    
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.HashMap;
    import java.util.Map;
    
    /*
    HashMap集合key部分允许null吗？允许,但是主义，HashMap集合的key null的值只能有一个
     */
    public class HashMapTest03 {
        public static void main(String[] args){
            Map map = new HashMap();
            map.put(null, null);
            System.out.println(map.size()); //1
    
            //key重复的话value是覆盖！
            map.put(null, 100);
            System.out.println(map.size()); //1
    
            //通过key获取value
            System.out.println(map.get(null));//100
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Hashtable;
    import java.util.Map;
    
    /*
    Hashtable的key可以为null吗？
        Hashtable的key和value都是不能为null的
        HashMap的key和value都是可以为null的
    
    Hashtable方法都带有synchronized，线程安全
    线程安全有其他的方案，所以Hashtable使用较少
    
    HashMap和Hashtable底层都是哈希表
    Hashtable的初始化容量是11，默认加载因子是0.75
    Hashtable的扩容是：原容量 * 2 + 1
     */
    public class HashtableTest01 {
        public static void main(String[] args) {
            Map map = new Hashtable();
            map.put(null, "123"); //java.lang.NullPointerException
    
            map.put(100, null);//java.lang.NullPointerException
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Properties;
    
    /*
    Properties是一个Map集合，继承Hashtable，Properties的key和value都是String类型
    Properties被称为属性类对象
    Properties是线程安全的
     */
    public class ProperitiesTest01 {
        public static void main(String[] args) {
            //创建一个Properties对象
            Properties pro = new Properties();
            //需要掌握Properties的两个方法，一个存，一个取
            pro.setProperty("url","jdbc:mysql://localhost:3306/bjpowernode");
            pro.setProperty("driver", "com.mysql.jdbc.Drive");
            pro.setProperty("driver", "root");
            pro.setProperty("password", "123");
    
            //通过key获取value
            String url = pro.getProperty("url");
            String driver =pro.getProperty("driver");
            String username =pro.getProperty("driver");
            String password =pro.getProperty("password");
    
            System.out.println(url);
            System.out.println(driver);
            System.out.println(username);
            System.out.println(password);
    
    
        }
    }
    
    ```
    
    树结构
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.TreeSet;
    
    /*
    1. TreeSet集合底层实际上是一个TreeMap
    2. TreeMap集合底层是一个二叉树
    3. 放到TreeSet集合中的元素，等同于放到TreeMap集合key部分了
    4. TreeSet集合中的元素：无序不可重复，但是可以按照元素的大小顺序自动排序
    5. 对于自定义的类型来说，TreeSet可以排序吗？在没有指定指定类的比较方法的时候，代码会报错。
    
     */
    public class TreeSetTest02 {
        public static void main(String[] args) {
            //创建一个TreeSet集合
            TreeSet<String> ts = new TreeSet<>();
            //添加String
            ts.add("zhangsan");
            ts.add("lisi");
            ts.add("wangwu");
            ts.add("zhangsi");
            ts.add("wangliu");
    
            //遍历
            for(String s:ts){
                //按照字典顺序，升序
                System.out.println(s);
            }
    
            TreeSet<Integer> ts2 = new TreeSet<>();
            ts2.add(100);
            ts2.add(200);
            ts2.add(900);
            ts2.add(500);
            ts2.add(800);
            ts2.add(10);
    
            //遍历
            for(Integer e:ts2){
                //按照字典顺序，升序
                System.out.println(e);
            }
    
            Person p1 = new Person(32);
            Person p2 = new Person(20);
            Person p3 = new Person(30);
            Person p4 = new Person(25);
    
            TreeSet<Person> persons = new TreeSet<>();
            persons.add(p1);
            persons.add(p2);
            persons.add(p3);
            persons.add(p4);
    
            //遍历
            for(Person p:persons){
                System.out.println(p);//java.lang.ClassCastException异常
            }
        }
    }
    
    class Person{
        int age;
        public Person(int age){
            this.age = age;
        }
        //重写toString()方法
        public String toString(){
            return "Person[age="+age+"]";
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.TreeSet;
    
    /*
    1. TreeSet集合底层实际上是一个TreeMap
    2. TreeMap集合底层是一个二叉树
    3. 放到TreeSet集合中的元素，等同于放到TreeMap集合key部分了
    4. TreeSet集合中的元素：无序不可重复，但是可以按照元素的大小顺序自动排序
    5. 对于自定义的类型来说，TreeSet可以排序吗？在没有指定指定类的比较方法的时候，代码会报错。所以需要自己写比较规则
    
     */
    public class TreeSetTest02 {
        public static void main(String[] args) {
            //创建一个TreeSet集合
            TreeSet<String> ts = new TreeSet<>();
            //添加String
            ts.add("zhangsan");
            ts.add("lisi");
            ts.add("wangwu");
            ts.add("zhangsi");
            ts.add("wangliu");
    
            //遍历
            for(String s:ts){
                //按照字典顺序，升序
                System.out.println(s);
            }
    
            TreeSet<Integer> ts2 = new TreeSet<>();
            ts2.add(100);
            ts2.add(200);
            ts2.add(900);
            ts2.add(500);
            ts2.add(800);
            ts2.add(10);
    
            //遍历
            for(Integer e:ts2){
                //按照字典顺序，升序
                System.out.println(e);
            }
    
            Person p1 = new Person(32);
            Person p2 = new Person(20);
            Person p3 = new Person(30);
            Person p4 = new Person(25);
    
            TreeSet<Person> persons = new TreeSet<>();
            persons.add(p1);
            persons.add(p2);
            persons.add(p3);
            persons.add(p4);
    
            //遍历
            for(Person p:persons){
                System.out.println(p);//java.lang.ClassCastException异常
            }
        }
    }
    
    class Person{
        int age;
        public Person(int age){
            this.age = age;
        }
        //重写toString()方法
        public String toString(){
            return "Person[age="+age+"]";
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    /*
    放在TreeSet集合中的元素需要实现java.lang.Comparable
    并且还要实现compareTo方法，equals可以不写
     */
    import java.util.TreeSet;
    
    public class TreeSetTest03 {
        public static void main(String[] args) {
            Customer p1 = new Customer(32);
            Customer p2 = new Customer(20);
            Customer p3 = new Customer(30);
            Customer p4 = new Customer(25);
    
            TreeSet<Customer> Customers = new TreeSet<>();
            Customers.add(p1);
            Customers.add(p2);
            Customers.add(p3);
            Customers.add(p4);
    
            //遍历
            for(Customer p:Customers){
                System.out.println(p);//java.lang.ClassCastException异常
            }
        }
    }
    // 放在
    class Customer implements Comparable<Customer>{
        int age;
        public Customer(int age){
            this.age = age;
        }
        //需要在这个方法中编写比较的逻辑，或者说比较的规则，按照什么进行比较！
        //k.compareTo(t.key)
        //拿着参数k和集合中的每一个k进行比较，返回值可能是>0 <0 =0
        //比较规则最终还是由程序员指定的：例如按照年龄升序，或者按照年龄降序
        @Override
        public int compareTo(Customer c) {
            // this是c1
            // c是c2
            // c1和c2比较的时候，就是this和c比较
    //        int age1 = this.age;
    //        int age2 = c.age;
    //        if(age1 == age2){
    //            return 0;
    //        }else if(age1 > age2){
    //            return 1;
    //        }else{
    //            return -1;
    //        }
    
            return this.age - c.age;
        }
        //重写toString
    
        @Override
        public String toString() {
            return "Customer{" +
                    "age=" + age +
                    '}';
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.TreeSet;
    
    /*
    先按照年龄升序，如果年龄一样，再按照姓名升序
     */
    public class TreeSetTest05 {
        public static void main(String[] args) {
            TreeSet<Vip> vips = new TreeSet<>();
            vips.add(new Vip("zhangsi", 20));
            vips.add(new Vip("zhangsan", 20));
            vips.add(new Vip("king", 18));
            vips.add(new Vip("soft", 17));
    
            for(Vip vip:vips){
                System.out.println(vip);
            }
    
        }
    }
    
    class Vip implements Comparable<Vip>{
        String name;
        int age;
    
        public Vip(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        @Override
        public String toString() {
            return "Vip{" +
                    "name='" + name + '\'' +
                    ", age=" + age +
                    '}';
        }
        /*compareTo方法的返回值很重要：
            返回0表示相同，value会覆盖
            返回>0，会继续在右子树上找
            返回<0,会继续在左子树上找
    
         */
        @Override
        public int compareTo(Vip o) {
            //先按照年龄，再按照姓名
            //姓名是String类型，可以直接比
            if(this.age == o.age){
                return this.name.compareTo(o.name);
            }else{
                return this.age - o.age;
            }
    
        }
    }
    /*
    Vip{name='soft', age=17}
    Vip{name='king', age=18}
    Vip{name='zhangsan', age=20}
    Vip{name='zhangsi', age=20}
     */
    ```
    
    自平衡二叉树
    
    ![image-20210406103707339](https://i.loli.net/2021/04/06/QEYcjHgST7DmLl1.png)
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.Comparator;
    import java.util.TreeSet;
    
    /*
    TreeSet集合中元素可排序的第二种方式：使用比较器
    最终的结论：
        放到TreeSet或者TreeMap集合key部分的元素要想做到排序，包括两种方式：
            第一种：放在集合中的元素实现java.lang.Comparable接口
            第二种：在构造TreeSet或者TreeMap集合的时候给它传一个比较器对象
        Comparable和Comparator怎么选择？
            当比较规则不会发生改变的时候，或者说当比较规则只有1个的时候，建议实现Comparable接口
            如果比较规则有多个，并且需要多个比较规则之间频繁切换，建议使用Comparator
            Comparator接口的设计符合OCP原则
     */
    public class TreeSetTest06 {
        public static void main(String[] args) {
            //创建TreeSet集合的时候，需要使用这个比较器
            //TreeSet<WuGui> wuguis = new TreeSet<>();//这样不行，没有通过构造方法传递一个比较器进去
            //给构造方法传递一个比较器
            TreeSet<WuGui> wuGuis = new TreeSet<>(new WuGuiComparator());
            wuGuis.add(new WuGui(1000));
            wuGuis.add(new WuGui(800));
            wuGuis.add(new WuGui(810));
    
            //遍历
            for(WuGui wuGui:wuGuis){
                System.out.println(wuGui);
            }
        }
    }
    
    class WuGui{
        int age;
    
        public WuGui(int age) {
            this.age = age;
        }
    
        @Override
        public String toString() {
            return "WuGui{" +
                    "age=" + age +
                    '}';
        }
    }
    
    //单独编写一个比较器
    //比较器实现java.util.Comparator接口。(Comparable是java.lang包下的，Comparator是java.util包下的)
    class WuGuiComparator implements Comparator<WuGui> {
    
        @Override
        public int compare(WuGui o1, WuGui o2) {
            //按照年龄排序
            return o1.age - o2.age;
        }
    }
    ```
    
    ```java
    package com.bjpowernode.javase.collection;
    
    import java.util.*;
    
    /*
    java.util.Collection 集合接口
    java.util.Collections 集合工具类，方便集合的操作
     */
    public class CollectionsTest {
        public static void main(String[] args) {
            // ArrayList集合不是线程安全的
            List<String> list = new ArrayList<>();
            //变成线程安全的
            Collections.synchronizedList(list);
    
            list.add("abf");
            list.add("abx");
            list.add("abc");
            list.add("abe");
            //排序
            Collections.sort(list);
            for(String s:list){
                System.out.println(s);
            }
    
            List<WuGui2> wuGuis = new ArrayList<>();
            wuGuis.add(new WuGui2(1000));
            wuGuis.add(new WuGui2(8000));
            wuGuis.add(new WuGui2(500));
            //注意：对list集合中的元素排序，需要保证list集合中的元素实现了Comparable接口。
            Collections.sort(wuGuis);
            for(WuGui2 wg:wuGuis){
                System.out.println(wg);
            }
    
            //对set集合怎么排序呢？
            Set<String> set = new HashSet<>();
            set.add("king");
            set.add("kingsoft");
            set.add("king1");
            set.add("king2");
            //将Set集合转换成list集合
            List<String> mylist = new ArrayList<>(set);
            Collections.sort(mylist);
            for (String s:mylist){
                System.out.println(s);
            }
        }
    }
    
    
    class WuGui2 implements Comparable<WuGui2>{
        int age;
    
        public WuGui2(int age) {
            this.age = age;
        }
    
        @Override
        public int compareTo(WuGui2 o) {
            return this.age - o.age;
        }
    
        @Override
        public String toString() {
            return "WuGui2{" +
                    "age=" + age +
                    '}';
        }
    }
    ```

11. IO流：通过IO可以完成硬盘文件的读和写。

    ![image-20210406151919971](https://i.loli.net/2021/04/06/axmMvwb8t9jRk1l.png)

    IO流的分类方式：

    ​	一种方式是按照流的方向进行分类：以内存为参照物：往内存中去，叫做输入(Input), 或者叫做读(Read);从内存中出来，叫做输出(Output).或者叫做写(Write)。

    ​	另一种方式是按照读取数据方式不同进行分类：有的流【字节流】是按照字节的方式读取数据，一次读取1个字节byte，等同于一次读取8个二进制位，这种流是万能的，什么类型的文件都可以读取，包括文本文件、图片、声音文件、视频文件等。有的流【字符流】的方式读取数据的，一次读取一个字符，这种流是为了方便读取普通文本文件而存在的，这种流不能读取：图片、声音、视频等文件，智能读取纯文本文件，连word文件都无法读取。

    java IO流有四大家族：

    ```java
    java.io.InputStream     字节输入流
    java.io.OutputStream    字节输出流
    java.io.Reader    字符输入流
    java.io.Writer    字符输入流
    四大家族的首领都是抽象类。
    所有流都实现了：java.io.Closeable接口，都是可以关闭的，都有close()方法。
        		  流毕竟是一个管道，这个是内存和硬盘之间的通道，用完之后一定要关闭，不然会耗费很多资源。
    所有的输出流都实现了：
        java.io.Flushable接口，都是可刷新的，都有flush()方法。输出流在最终输出之后，一定要flush()刷新一下。否则可能会丢失数据。
    ```

    注意：在java中只要"类名"以Stream结尾的都是字节流。以"Reader/Writer"结尾的都是字符流。	

    java.io包下需要掌握的流有16个：

    ```java
    文件专属：
    java.io.FileInputStream [字节方式] 【掌握】
    java.io.FileOutputStream [字节方式] 【掌握】
    java.io.FileReader [字符方式]
    java.io.FileWriter [字符方式]
    
    转换流(将字节流转换为字符流)：
    java.io.InputStreamReader
    java.io.OutputStreamWriter
    
    缓冲流专属：    
    java.io.BufferedReader
    java.io.BufferedWriter
    java.io.BufferedInputStream
    java.io.BufferedOutputStream
    
    数据流专属：
    java.io.DataInputStream
    java.io.DataOutputStream
    
    标准输出流：
    java.io.ObjectInputStream
    java.io.ObjectOutputStream 【掌握】
    
    对象专属流：    
    java.io.PrintWriter 【掌握】
    java.io.PrintStream 【掌握】
    
    ```

    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileInputStream;
    import java.io.FileNotFoundException;
    import java.io.IOException;
    
    /*
    java.io.FileInputStream:
        1. 文件字节输入流，万能的，任何类型的文件都可以采用这个流来读
        2. 字节的方式，完成输入的操作，完成读的操作
        3.
     */
    public class FileInputStreamTest01 {
        public static void main(String[] args) {
            FileInputStream fis = null;
            //创建文件字节输入流对象
            try {
                fis = new FileInputStream("C:\\Users\\Administrator\\Desktop\\java_code\\chapter23\\src\\com\\bjpowernode\\java\\io\\text");
                //开始读
                int readData = 0;
                while((readData = fis.read()) != -1){
                    System.out.println(readData);
                }
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                //在finally语句块中确保流一定关闭
                if (fis != null){
                    //关闭流的前提是：流不是空。流是null的时候没必要关闭。
                    try {
                        fis.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
    
                }
            }
        }
    }
    
    ```

    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileInputStream;
    import java.io.FileNotFoundException;
    import java.io.IOException;
    
    /*
    java.io.FileInputStream:
        1. 文件字节输入流，万能的，任何类型的文件都可以采用这个流来读
        2. 字节的方式，完成输入的操作，完成读的操作
        3.
     */
    public class FileInputStreamTest01 {
        public static void main(String[] args) {
            FileInputStream fis = null;
            //创建文件字节输入流对象
            try {
                //IDEA默认的当前路径是工程Project的根
                fis = new FileInputStream("C:\\Users\\Administrator\\Desktop\\java_code\\chapter23\\src\\com\\bjpowernode\\java\\io\\text");
                //开始读
    
                //采用byte数组，一次读取多个字节，最多读取数组.length个字节。
                byte[] bytes = new byte[4];//准备一个4个长度的数组，一次最多读取4个字节
                int readCount = 0;
                while((readCount = fis.read(bytes)) != -1){
                    System.out.print(new String(bytes, 0, readCount));
                }
    
    
    
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                //在finally语句块中确保流一定关闭
                if (fis != null){
                    //关闭流的前提是：流不是空。流是null的时候没必要关闭。
                    try {
                        fis.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
    
                }
            }
        }
    }
    
    ```

    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileInputStream;
    import java.io.FileNotFoundException;
    import java.io.IOException;
    
    /*
    FileInputStream类的其他常用方法：
        1. int available():返回流当中剩余的没有读到的字节数量
        2. long skip(long n)：跳过几个字节不多
     */
    public class FileInputStreamTest02 {
        public static void main(String[] args) {
            FileInputStream fis = null;
            try {
                fis = new FileInputStream("C:\\Users\\Administrator\\Desktop\\java_code\\chapter23\\src\\com\\bjpowernode\\java\\io\\text");
                System.out.println("总字节数量：" + fis.available());
    //            //读1个字节
    //            try {
    //                int readByte = fis.read(); //读1个字节
    //                System.out.println("剩下多少个字节没有读：" + fis.available());//13
    //                //
    //            } catch (IOException e) {
    //                e.printStackTrace();
    //            }
    //            byte[] bytes = new byte[fis.available()];
    //            int readCount = fis.read(bytes);
    //            System.out.println(new String(bytes));//abcdefghigklmn
    
                //skip跳过几个字节不读取，这个方法也可能以后会用
                fis.skip(3);
                System.out.println(fis.read());//100
    
    
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if(fis != null){
                    try {
                        fis.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
        }
    }
    
    ```

    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileNotFoundException;
    import java.io.FileOutputStream;
    import java.io.IOException;
    import java.nio.charset.StandardCharsets;
    
    /**
     * java.io.FileOutputStream:
     * 文件字节输出流，负责写
     * 从内存到硬盘
     */
    public class FileOutputStreamTest01 {
        public static void main(String[] args) {
            FileOutputStream fos = null;
    
            try {
                //这种方式谨慎使用，这种方式会将原文件清空，然后重新写入。
                //fos = new FileOutputStream("myfile");
                //以追加的方式在文件末尾写入，不会清空原文件内容
                fos = new FileOutputStream("myfile", true);
                //开始写
                byte[] bytes = {97, 98, 99, 100};
                fos.write(bytes); //将byte数组全部写出, myfile文件不存在时会自动新建
                fos.write(bytes, 0, 2); //将byte数组的一部分写出
    
                //将字符串
                String s = "我是一个中国人，我骄傲！";
                //将字符串转换成byte数组
                byte[] bs = s.getBytes();
                fos.write(bs);
    
    
                //写完之后，最后一定要刷新
                fos.flush();
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if(fos != null){
                    try {
                        fos.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileInputStream;
    import java.io.FileNotFoundException;
    import java.io.FileOutputStream;
    import java.io.IOException;
    
    /*
    使用FileInputStream+FileOutputStream完成文件的拷贝。
    拷贝的过程是一边读，一边写
    使用以上的字节流拷贝文件的时候，文件类型随意，万能的。
     */
    public class Copy01 {
        public static void main(String[] args) {
            FileInputStream fis = null;
            FileOutputStream fos = null;
            try {
                //创建一个输入流对象
                fis = new FileInputStream("myfile");
                //创建一个输出流对象
                fos = new FileOutputStream("youfile");
    
                //最核心的，一边读，一边写
                byte[] bytes = new byte[100 * 1024];//一次最多拷贝100KB
                int readCount = 0;
                while((readCount = fis.read(bytes)) != -1){
                    fos.write(bytes, 0, readCount);
                }
    
    
                //刷新，输出流最后要刷新
                fos.flush();
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
    
            } catch (IOException e) {
                e.printStackTrace();
            } finally{
                //分开try，不要一起try，一起try的时候，其中一个出现异常，可能会影响到另一个流的关闭。
                if(fis != null){
                    try {
                        fis.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
                if(fos != null){
                    try {
                        fos.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileNotFoundException;
    import java.io.FileReader;
    import java.io.IOException;
    
    /*
    FileReader:
        文件字符输入流，只能读取普通文本
        读取文本内容时，比较方便，快捷
     */
    public class FileReaderTest {
        public static void main(String[] args) {
            FileReader reader = null;
            try {
                //创建文件字符输入流
                reader = new FileReader("myfile");
                //开始读
                char[] chars = new char[4];//一次读取4个字符
                int readCount = 0;
                while((readCount = reader.read(chars)) != -1){
                    System.out.print(new String(chars, 0, readCount));
                }
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if(reader != null){
                    try {
                        reader.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileWriter;
    import java.io.IOException;
    
    /*
    FileWriter:
        文件字符输出流，写。
        只能输出普通文本。
     */
    public class FileWriterTest {
        public static void main(String[] args) {
            FileWriter out = null;
            try {
                //创建文件字符输出流文档
                out = new FileWriter("file", true);//append表示是否清空文件原始内容
                //开始写
                char[] chars = {'我', '是', '中', '国', '人'};
                out.write(chars);
                out.write(chars, 2, 3);
                out.write("我是一名java软件工程师！");
    
                //刷新
                out.flush();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if(out != null){
                    try {
                        out.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileNotFoundException;
    import java.io.FileReader;
    import java.io.FileWriter;
    import java.io.IOException;
    
    /*
    使用FileReader FileWriter进行拷贝的话，只能拷贝普通文本文件
     */
    public class Copy02 {
        public static void main(String[] args) {
            FileReader in = null;
            FileWriter out = null;
            try {
                //读
                in = new FileReader("file");
                //写
                out = new FileWriter("copyfile");
    
                // 一边读一边写
                char[] chars = new char[100 * 1024];
                int readCount = 0;
                while((readCount = in.read(chars)) != -1){
                    out.write(chars, 0, readCount);
                }
                //刷新
                out.flush();
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                if(in == null){
                    try {
                        in.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
                if(out == null){
                    try {
                        out.close();
                    } catch (IOException e) {
                        e.printStackTrace();
                    }
                }
            }
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.BufferedReader;
    import java.io.FileNotFoundException;
    import java.io.FileReader;
    
    /*
    BufferedReader:
        带有缓冲区的字符输入流
        使用这个流的时候不需要自定义char数组，或者说不需要自定义byte数组，自带缓冲。
     */
    public class BufferedReaderTest01 {
        public static void main(String[] args) throws Exception {
            FileReader reader = new FileReader("file");
            //当一个流的构造方法中需要一个流的时候，这个被传进来的流叫做：节点流
            //外部负责包装的这个流，叫做：包装流，还有一个名字叫做：处理流。
            //像当前这个程序来说：FileReader就是一个节点流，BufferedReader就是包装流/处理流
            BufferedReader br = new BufferedReader(reader);
    
            //读一行
            String firstLine = br.readLine();
            System.out.println(firstLine);
    
            //br.readLine()方法读取一个文本行，但不带换行符
            String s= null;
            while((s = br.readLine()) != null){
                System.out.print(s);
            }
    
            //关闭流
            //对于包装流来说，只需要关闭最外层流就行，里面的节点流会自动关闭
            br.close();
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.BufferedReader;
    import java.io.FileInputStream;
    import java.io.FileNotFoundException;
    import java.io.InputStreamReader;
    
    public class BufferedReaderTest02 {
        public static void main(String[] args) throws Exception {
            //字节流
            FileInputStream in = new FileInputStream("file");
            //这个构造方法只能传一个字符流，不能传字节流
            //BufferedReader br = new BufferedReader();
    
            //通过转换流转换，将字节流转换为字符流
            InputStreamReader reader = new InputStreamReader(in);
    
            BufferedReader br = new BufferedReader(reader);
    
            String line = null;
            while((line = br.readLine()) != null){
                System.out.println(line);
            }
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    
    import java.io.BufferedWriter;
    import java.io.FileOutputStream;
    import java.io.FileWriter;
    import java.io.OutputStreamWriter;
    
    /*
    BufferedWriter: 带有缓冲的字符输出流
     */
    public class BufferedWriterTest {
        public static void main(String[] args) throws Exception{
            //BufferedWriter out = new BufferedWriter(new FileWriter("copyfile2"));
            BufferedWriter out = new BufferedWriter(new OutputStreamWriter(new FileOutputStream("copy", true)));
            out.write("hello world!");
            out.write("\n");
            out.write("hello kitty!");
            //刷新
            out.flush();
            //关闭
            out.close();
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.DataOutputStream;
    import java.io.FileOutputStream;
    
    /*
    java.io.DataOutputStream: 数据专属流
    这个流可以将数据连同数据的类型一并写入文件
    注意:这个文件不是普通文本文档(这个文件使用记事本打不开)
     */
    public class DataOutputStreamTest {
        public static void main(String[] args) throws Exception{
            //创建数据专属的字节输出流
            DataOutputStream dos = new DataOutputStream(new FileOutputStream("data"));
            byte b = 100;
            short s = 200;
            int i = 300;
            long l = 400L;
            float f = 3.0F;
            double d = 3.14;
            boolean sex = false;
            char c = 'a';
            //写,把数据以及数据的类型一并写入到文件当中
            dos.writeByte(b);
            dos.writeShort(s);
            dos.writeInt(i);
            dos.writeLong(l);
            dos.writeFloat(f);
            dos.writeDouble(d);
            dos.writeBoolean(sex);
            dos.writeChar(c);
            //刷新
            dos.flush();
            dos.close();
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.DataInputStream;
    import java.io.FileInputStream;
    
    /*
    DataInputStream:数据字节输入流
    DataOutputStream:写的文件，只能使用DataInputStream去读，并且读的时候，需要提前知道写入的顺序
    读的顺序需要和写的顺序一致，才可以正常取出数据。
     */
    public class DataInputStreamTest01 {
        public static void main(String[] args) throws Exception{
            DataInputStream dis = new DataInputStream(new FileInputStream("data"));
            //开始读
            byte b = dis.readByte();
            short s = dis.readShort();
            int i = dis.readInt();
            long l = dis.readLong();
            float f = dis.readFloat();
            double d = dis.readDouble();
            boolean sex = dis.readBoolean();
            char c = dis.readChar();
    
            System.out.println(b);
            System.out.println(s);
            System.out.println(i);
            System.out.println(l);
            System.out.println(f);
            System.out.println(d);
            System.out.println(sex);
            System.out.println(c);
    
    
            dis.close();
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileOutputStream;
    import java.io.PrintStream;
    
    /*
    java.io.PrintStream:标准的字节输出流，默认输出到控制台
    可以改变，改变输出到文件,也就是输出log文件中
     */
    public class PrintStreamTest {
        public static void main(String[] args) throws Exception{
            //联合起来写
            System.out.println("hello world!");
    
            //分开写
            PrintStream ps = System.out;
            ps.println("hello");
    
            //标准输出流不需要手动close()关闭
    
            //标准输出流不再指向控制台，指向log文件
            PrintStream printStream = new PrintStream(new FileOutputStream("log"));
            //修改输出方向，将输出方向修改到"log"文件。
            System.setOut(printStream);
            //再输出
            System.out.println("hello world");
            System.out.println("hello kitty");
            System.out.println("hello zhangsan");
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.FileNotFoundException;
    import java.io.FileOutputStream;
    import java.io.PrintStream;
    import java.text.SimpleDateFormat;
    import java.util.Date;
    import java.util.logging.SimpleFormatter;
    
    /*
    日志工具
     */
    public class Logger {
        /*
        记录日志的方法
         */
        public static void log(String args) {
            try {
                //指向一个日志文件
                PrintStream out = new PrintStream(new FileOutputStream("log.txt", true));
                //改变输出方向
                System.setOut(out);
    
                //日期当前时间
                Date nowTime = new Date();
                SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
                String strTime = sdf.format(nowTime);
                System.out.println(strTime + ": " + args);
    
            } catch (FileNotFoundException e) {
                e.printStackTrace();
            }
    
        }
    }
    
    package com.bjpowernode.java.io;
    
    public class LogTest {
        public static void main(String[] args) {
            //测试工具类是否好用
            Logger.log("调用了System类的gc()方法，建议启动垃圾回收");
            Logger.log("调用了UserServicede doSome()方法");
            Logger.log("用户尝试进行登陆，验证失败");
        }
    }
    //写入log日志
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.File;
    import java.text.SimpleDateFormat;
    import java.util.Date;
    
    /*
    File
        1. File类和四大家族没有关系，所以File类不能完成文件的读和写
        2. File对象代表什么？
            文件和目录路径名的抽象表示形式
            C:\Drivers 这是一个File对象
            C:\Drivers\Readme.txt 也是一个File对象
            一个File对象有可能对应的是目录，也可能是文件
            需要掌握File类的常用方法
    
     */
    public class FileTest01 {
        public static void main(String[] args) throws Exception{
            File f1 = new File("newFile");
            System.out.println(f1.exists());//判断指定路径或文件是否存在,返回true 或 false
    
            //如果文件不存在，则以文件的形式创建出来
            if(!f1.exists()){
                f1.createNewFile();
            }
    
            //如果目录不存在，则以目录的形式创建出来
            if(!f1.exists()){
                f1.mkdir();
            }
    
            //获取文件的父路径
            File f3 = new File("chapter23/src/com.bjpowernode.java.io/text.txt");
            String parentPath = f3.getParent();
            System.out.println(parentPath);
    
            //获取父路径的绝对路径
            File parentFile = f3.getParentFile();
            System.out.println("获取绝对路径：" + parentFile.getAbsolutePath());
    
            //获取文件的绝对路径
            System.out.println("文件的绝对路径：" + f3.getAbsolutePath());
    
            //判断是否是一个目录
            System.out.println(f3.isDirectory());
    
            //判断是否是一个文件
            File f4 = new File("file");
            System.out.println(f4.isFile());
    
            //获取文件最后一次修改时间
            long haomiao = f1.lastModified(); //这个毫秒是从1970年到现在的总毫秒数
            //将毫秒数转换成日期
            Date time = new Date(haomiao);
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
            String strTime = sdf.format(time);
            System.out.println(strTime);
    
            //获取文件大小
            System.out.println(f1.length());
    
            //获取当前目录下所有的子文件
            File f = new File("chapter23");
            File[] files = f.listFiles();
            for(File file:files){
                System.out.println(file.getAbsolutePath());
            }
    
    
    
        }
    }
    
    ```
    
    ```java
    package com.bjpowernode.java.io;
    
    import java.io.*;
    
    /*
    拷贝目录
     */
    public class copyall {
        public static void main(String[] args) {
            //拷贝源
            File srcFile = new File("src");
    
            //拷贝目标
            File destFile = new File("F:results");
            
            //调用方法拷贝
            copyDir(srcFile, destFile);
        }
    
        /**
         *
         * @param srcFile 拷贝源
         * @param destFile 拷贝目标
         */
        private static void copyDir(File srcFile, File destFile) {
            if(srcFile.isFile()){
                //srcFile如果是一个文件的话，递归结束
                //是文件的时候需要拷贝
                //....一边读，一边写
                FileInputStream in = null;
                FileOutputStream out = null;
                try {
                    in = new FileInputStream(srcFile);
    
                    String path = (destFile.getAbsolutePath().endsWith("\\")? destFile.getAbsolutePath() : destFile.getAbsolutePath() + "\\") + srcFile.getAbsolutePath().substring(41);
                    out = new FileOutputStream(path);
                    //一边读一边写
                    byte[] bytes = new byte[1024 * 1024];
                    int readCount = 0;
                    while((readCount = in.read(bytes))!= -1){
                        out.write(bytes, 0, readCount);
                    }
    
                    out.flush();
                } catch (FileNotFoundException e) {
                    e.printStackTrace();
                } catch (IOException e) {
                    e.printStackTrace();
                } finally {
                    if (out != null){
                        try {
                            out.close();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                    if (in != null){
                        try {
                            in.close();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                }
    
    
                return;
            }
    
            //获取源下面的子目录
            File[] files = srcFile.listFiles();
            for(File file:files){
                //获取所有文件的(包括目录和文件)绝对路径
                //System.out.println(file.getAbsolutePath());
                if(file.isDirectory()){
                    String srcDir = file.getAbsolutePath();
                    String destDir = (destFile.getAbsolutePath().endsWith("\\")? destFile.getAbsolutePath() : destFile.getAbsolutePath() + "\\") + srcDir.substring(41);
                    File newFile = new File(destDir);
                    if(!newFile.exists()){
                        newFile.mkdirs();
                    }
                }
                //递归调用
                copyDir(file, destFile);
            }
    
    
        }
    }
    
    ```
    
12. 对象的序列化和反序列化

    ![image-20210410170515245](https://i.loli.net/2021/04/10/CHAybOZe2v6EkTd.png)

    ```java
    package com.bjpowernode.java.bean;
    
    import java.io.Serializable;
    
    public class Students implements Serializable {
        private int no;
        private String name;
        private static final long serialVersionUID = 1L;
    
        public Students(){
    
        }
    
        public Students(int no, String name) {
            this.no = no;
            this.name = name;
        }
    
        public int getNo() {
            return no;
        }
    
        public void setNo(int no) {
            this.no = no;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        @Override
        public String toString() {
            return "Students{" +
                    "no=" + no +
                    ", name='" + name + '\'' +
                    '}';
        }
    }
    
    package com.bjpowernode.java.bean;
    
    import java.io.FileOutputStream;
    import java.io.ObjectOutputStream;
    /*
    1. java.io.NotSerializableException:
        Student对象不支持序列化！！
    2. 参与序列化和反序列化的对象，必须实现Serializable接口。
    3. 注意：通过源代码发现，Serializable接口只是一个标志接口：
        public interface Serializable {
        }
        这个接口当中什么代码也没有。
        那么它起到一个什么作用呢？
            起到标识的作用，标志的作用，java虚拟机看到这个类实现了这个接口，可能会对这个类进行特殊待遇。
            Serializable这个标志接口是给java虚拟机参考的，java虚拟机看到这个接口之后，会为该类自动生成
            一个序列化版本号。
    4. 序列化版本号的作用？
    	java.io.InvalidClassException:
    		com.bjpowernode.java.bean.Student;
    		local class incompatible:
    			stream classdesc serialVersionUID = -684255398724514298(十年后),
    			local class serialVersionUID = -3463447116624555755(十年前)
    	java语言中是采用什么机制来区分类的？
    		第一：首先通过类名进行比对，如果类名不一样，肯定不是同一个类
    		第二：如果类名一样，再怎么进行类的区别？靠序列化版本号进行区分。
    		
    	小鹏编写了一个类：com.bjpowernode.java.bean.Student implements Serializable
    	胡浪编写了一个类：com.bjpowernode.java.bean.Student implements Serializable
    	不同的人编写了同一个名字的类，但这两个类确实不是同一个类，这个时候序列化版本就起作用了。
    	对于java虚拟机来说，java虚拟机是可以区分开这两个类的，因为这两个类都实现了Serializable接口，
    	都有默认的序列化版本号，他们的序列化版本号不一样，所以区分开了。(这是自动生成序列化版本号的优点)
    	
    	请思考：
    		这种自动生成序列化版本号有什么缺陷？
    			一旦代码确定之后，不能进行后续的修改，因为只要修改，必然会重新编译，此时会生成全新的序列化版本号，这个时候java虚拟机会认为这是一个全新的类。
    	
    	最终结论：
    		凡是一个类实现了Serializable接口，建议给该类提供一个固定不变的序列版本号。
    		建议将序列化版本号手动写出来，不建议自动生成。
    		
    
     */
    public class ObjectOutputStreamTest01 {
        public static void main(String[] args) throws Exception{
            //创建java对象
            Students s = new Students(1111, "zhangsan");
            //序列化
            ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("students"));
            //序列化对象
            oos.writeObject(s);
            //刷新
            oos.flush();
            //关闭
            oos.close();
        }
    }
    
    package com.bjpowernode.java.bean;
    
    import java.io.FileInputStream;
    import java.io.ObjectInputStream;
    
    /*
    反序列化
     */
    public class ObjectInputStreamTest01 {
        public static void main(String[] args) throws Exception{
            ObjectInputStream ois = new ObjectInputStream(new FileInputStream("students"));
            //开始反序列化
            Object obj = ois.readObject();
            //反序列化回来是一个学生对象，所以会调用学生对象的toString方法。
            System.out.println(obj);
            ois.close();
        }
    
    }
    //Students{no=1111, name='zhangsan'}
    ```

    ```java
    package com.bjpowernode.java.bean;
    
    import java.io.Serializable;
    
    public class User implements Serializable {
        private int no;
        private String name;
        
        //transient关键字表示游离的，不参与序列化
        //private transient String name;
    
        public User() {
        }
    
        public User(int no, String name) {
            this.no = no;
            this.name = name;
        }
    
        public int getNo() {
            return no;
        }
    
        public void setNo(int no) {
            this.no = no;
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        @Override
        public String toString() {
            return "User{" +
                    "no=" + no +
                    ", name='" + name + '\'' +
                    '}';
        }
    }
    
    package com.bjpowernode.java.bean;
    
    import java.io.FileOutputStream;
    import java.io.ObjectOutputStream;
    import java.util.ArrayList;
    import java.util.List;
    
    /*
    一次序列化多个对象呢？
        可以，可以将对象放到集合中，序列化集合。
    提示：
        参与序列化的ArrayList集合以及集合中的元素User都需要实现java.io.Serializable接口
     */
    public class ObjectOutputStreamTest02 {
        public static void main(String[] args) throws Exception{
            List<User> userList = new ArrayList<>();
            userList.add(new User(1, "zhangsan"));
            userList.add(new User(2, "lisi"));
            userList.add(new User(3, "wangwu"));
            ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("users"));
    
            //序列化一个集合，这个集合对象中放了很多其他对象
            oos.writeObject(userList);
    
    
        }
    }
    
    package com.bjpowernode.java.bean;
    
    import java.io.FileInputStream;
    import java.io.ObjectInputStream;
    import java.util.List;
    
    /*
    反序列化
     */
    public class ObjectInputStreamTest02 {
        public static void main(String[] args) throws Exception{
            ObjectInputStream ois = new ObjectInputStream(new FileInputStream("users"));
            //开始反序列化
            //Object obj = ois.readObject();
            //反序列化回来是一个学生对象，所以会调用学生对象的toString方法。
            //System.out.println(obj instanceof List);
    
            //把反序列化得到的对象强转成list
            List<User> userList = (List<User>)ois.readObject();
            for(User user:userList){
                System.out.println(user);
            }
            ois.close();
        }
    }
    
    //User{no=1, name='zhangsan'}
    //User{no=2, name='lisi'}
    //User{no=3, name='wangwu'}
    ```

    IO和Properties联合使用


~~~java
package com.bjpowernode.java.io;
import java.io.FileReader;
import java.util.Properties;
/*
    IO+Properties的联合应用。
    经常改变的数据，可以单独写到一个文件中，使用程序动态读取。
    将来只需要修改这个文件的内容，java代码不需要改动，不需要重新编译，服务器也不需要重启，就可以拿到动态的信息。

    类似于以上机制的这种文件被称为配置文件
    并且当配置文件中的内容格式是：
        key1=value
        key2=value
    的时候，我们把这种配置文件叫做属性配置文件。

    java规范中有要求：属性配置文件建议以.properties结尾，但这不是必须的。
    这种以.properties结尾的文件在java中被称为：属性配置文件。
    其中Properties对象是专门存放属性配置文件内容的一个类

     */
public class IoPropertiesTest01 {
    public static void main(String[] args) throws Exception{
        /*
            Properties是一个Map集合，key和value都是String类型。
            想将userinfo文件中的数据加载到Properties对象当中。
             */

        //新建一个输入流对象
        FileReader reader = new FileReader("userinfo");

        //新建一个Map集合
        Properties pro = new Properties();

        //调用Properties对象的Load方法将文件中的数据加载到Map集合中。
        pro.load(reader);//文件中的数据顺着管道加载到Map集合中，其中等号==左边做key,右边做value

        //通过key来获取value
        String username = pro.getProperty("username");
        System.out.println(username);//admin
    }
}

```
~~~


13. 多线程

    1. 什么是进程？什么是线程？

       进程是一个应用程序(1个进程是一个软件)。线程是一个进程中的执行场景/执行单元。一个进程可以启动多个线程。

    2. 对于java来说，当在DOS命令窗口中输入：java HelloWorld回车之后，会先启动JVM，而JVM就是一个进程。JVM再启动一个主线程调用main方法，同时再启动一个垃圾回收线程负责看护，回收垃圾。最起码，现在的java程序中至少有两个线程并发，一个是垃圾回收线程，一个是执行main方法的主线程。
    3. 在java中，线程A和线程B栈内存是独立不共享的，一个线程一个栈，但是堆内存和方法区内存是共享的。
    4. 使用了多线程机制之后，main方法结束，只意味着主线程结束了，主栈空了，其他的栈(线程)可能还在压栈弹栈。

    ![image-20210412145919329](https://i.loli.net/2021/04/12/bvteoAixVOU7PKD.png)

    5. 对于单核的CPU来说，可以做到真正的多线程并发吗？

       n核CPU表示在同一个时间点上，可以真正地有n个进程并发执行。单核CPU不能够做到真正的多线程并发，但是可以做到给人一种"多线程"并发的感觉。对于单核的CPU来说，在某个时间点上实际上只能处理一件事情，但是由于CPU的处理速度极快，多个线程之间频繁切换执行，给人的感觉是：多个事情同时在做！

       ```java
       package com.bjpowernode.java.thread;
       /*
       分析以下程序，除垃圾回收线程之外，有几个线程？
           1个线程，因为程序只有1个栈。
        */
       public class ThreadTest01 {
           public static void main(String[] args) {
               System.out.println("main begin");
               m1();
               System.out.println("main over");
           }
       
           private static void m1() {
               System.out.println("m1 begin");
               m2();
               System.out.println("m1 over");
           }
       
           private static void m2() {
               System.out.println("m2 begin");
               m3();
               System.out.println("m2 over");
           }
       
           private static void m3() {
               System.out.println("m3 begin");
               System.out.println("m3 over");
           }
       }
       
       ```

       java中，实现线程有两种方式，第一种方式是：编写一个类，直接继承java.lang.Thread，重写run方法。

       ```java
       package com.bjpowernode.java.thread;
       /*
       实现线程的第一种方式：
           编写一个类，直接继承java.lang.Thread,重写run方法
        */
       public class ThreadTest02 {
           public static void main(String[] args) {
               //这里是main方法，这里的代码属于主线程，在主栈中运行。
               //新建一个分支线程对象
               MyThread myThread = new MyThread();
       
               //启动线程
               //myThread.run()不会启动线程，不会分配新的分支栈，这种方式就是单线程。
               myThread.start();//start()方法的作用是：启动一个分支线程，在JVM中开辟了一个新的栈空间，这段代码任务完成之后瞬间就结束了。
                               //这段代码的任务只是为了开启一个新的栈空间，只要新的栈空间开出来，start方法就结束了。线程就启动成功了
                               //启动成功的线程会自动调用run放啊，并且run方法在分支栈的栈底部(压栈)
               //这里的代码还是运行在主线程中
               for(int i=0; i<1000; i++){
                   System.out.println("主线程-->" + i);
               }
           }
       }
       
       class MyThread extends Thread{
           @Override
           public void run() {
               //编写程序，这段程序运行在分支线程中(分支栈)。
               for(int i=0; i<1000; i++){
                   System.out.println("分支线程-->" + i);
               }
           }
       }
       
       ```

       第二种方式：编写一个类，实现java.lang.Runnable接口，实现run方法。

       ```java
       package com.bjpowernode.java.thread;
       /*
       实现线程的第二种方式，编写一个类实现java.lang.Runnable接口。
        */
       public class ThreadTest03 {
           public static void main(String[] args) {
               //创建一个可运行的对象
               //MyRunnable r = new MyRunnable();
               // 将可运行的对象封装成一个线程对象
               //Thread t = new Thread(r);
       
               //合并代码
               Thread t = new Thread(new MyRunnable());
       
               //启动线程
               t.start();
       
               for(int i=0; i<100; i++){
                   System.out.println("主线程-->" + i);
               }
           }
       }
       
       //这并不是一个线程类，是一个可运行的类，它还不是一个线程。
       class MyRunnable implements Runnable{
       
           @Override
           public void run() {
               for(int i=0; i<1000; i++){
                   System.out.println("分支线程-->" + i);
               }
           }
       }
       ```

       第二种方式实现接口比较常用，因为一个类实现了接口，它还可以去继承其他的类，更灵活。

       ```java
       package com.bjpowernode.java.thread;
       /*
       采用匿名内部类实现多线程
        */
       public class ThreadTest04 {
           public static void main(String[] args) {
               //创建线程对象，采用匿名内部类方式
               Thread t = new Thread(new Runnable() {
                   @Override
                   public void run() {
                       for(int i=0; i<1000; i++){
                           System.out.println("分支线程-->" + i);
                       }
                   }
               });
       
               //启动线程
               t.start();
               for(int i=0; i<1000; i++){
                   System.out.println("主线程-->" + i);
               }
           }
       }
       
       ```

       线程的生命周期

       ![image-20210413111155694](https://i.loli.net/2021/04/13/8DPjXG2UpQ6lhxd.png)

    6. 获取当前线程

       ```java
       package com.bjpowernode.java.thread;
       /*
       1.怎么获取当前线程对象？
           Thread t = Thread.currentThread();
           返回值t就是当前线程
       2.获取线程对象的名字
       3.修改线程对象的名字
           线程对象.setName("线程名字“)
        */
       public class ThreadTest05 {
           public static void main(String[] args) {
       
               Thread currentThread = Thread.currentThread();//获取当前进程
               System.out.println(currentThread.getName());//main
               //创建线程对象
               MyThread2 t = new MyThread2();
               //设置线程名字
               t.setName("t1");
               //获取线程的名字
               String tName = t.getName();
               System.out.println(tName);//t1
       
               MyThread2 t2 = new MyThread2();
               t2.setName("t2");
               //获取线程的名字
               System.out.println(t2.getName());//t1
       
               //启动线程
               t.start();
               t2.start();
           }
       }
       
       class MyThread2 extends Thread{
           public void run(){
       
               for(int i=0; i<100; i++){
                   Thread currentThread = Thread.currentThread();//获取当前进程
                   System.out.println(currentThread.getName() + "-->" + i);
               }
           }
       }
       
       
       ```

    7. Thread.sleep()方法

       ```java
       package com.bjpowernode.java.thread;
       /*
       关于线程的sleep方法：
           static void sleep(long millions)
               1. 静态方法
               2. 参数是毫秒
               3. 作用：让当前线程进入休眠，进入阻塞状态，放弃占有CPU时间片，让给其他线程调用。
                   这行代码出现在A线程中，A线程就会进入休眠。
               4. Thread.sleep()方法可以：间隔特定的时间，去执行一段特定的代码，每隔多久执行一次。
       
        */
       public class ThreadTest06 {
           public static void main(String[] args) {
               //让当前线程进入休眠，睡眠5秒
               try {
                   Thread.sleep(1000*5);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
       
               //5秒之后执行这里的代码
               System.out.println("hello world!");
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.thread;
       /*
       关于Thread.sleep()方法的一个面试题：
       
        */
       public class ThreadTest07 {
           public static void main(String[] args) {
               //创建线程对象
               MyThread3 t = new MyThread3();
               t.setName("t");
               t.start();
       
               //调用sleep方法
               try {
                   //问题：这行代码会让线程t进入休眠状态吗？
                   //答案：不会，在执行代码的时候还是会转换成:Thread.sleep(1000*5);
                   //即这行代码的作用是：让*当前线程*进入休眠，也就是main线程进入休眠。
                   t.sleep(1000*5);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
               System.out.println("hello world!");
           }
       }
       
       class MyThread3 extends Thread{
           public void run(){
               for(int i=0; i<10000; i++){
                   System.out.println(Thread.currentThread().getName() + "--->" + i);
               }
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.thread;
       /*
       sleep睡眠太久了，如果希望半道上醒来，你应该怎么办？也就是说怎么叫醒一个正在睡眠的线程？？
           注意：这个不是终止线程的执行，而是终止线程的睡眠。
        */
       public class ThreadTest08 {
           public static void main(String[] args) {
               Thread t = new Thread(new MyRunnable2());
               t.setName("t");
               t.start();
       
               //希望5秒之后，t线程醒来
               try {
                   Thread.sleep(1000 * 5);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
               // 中断t线程的睡眠(这种中断睡眠的方式依靠了java的异常处理机制)
               t.interrupt();
           }
       }
       
       class MyRunnable2 implements Runnable{
           //重点：run()方法当中的异常不能throws,只能try catch
           // 因为run()方法在父类中没有抛出任何异常，子类不能比父类抛出更多的异常。
           @Override
           public void run() {
               System.out.println(Thread.currentThread().getName() + "--> begin");
               try {
                   //睡眠1年
                   Thread.sleep(1000 * 60 * 60 * 24 * 365);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
               //一年之后才会执行到这里
               System.out.println(Thread.currentThread().getName() + "--> begin");
           }
       }
       /*
       t--> begin
       java.lang.InterruptedException: sleep interrupted
       	at java.base/java.lang.Thread.sleep(Native Method)
       	at com.bjpowernode.java.thread.MyRunnable2.run(ThreadTest08.java:31)
       	at java.base/java.lang.Thread.run(Thread.java:832)
       t--> begin
        */
       ```

    8. 强行终止一个线程的执行

       ```java
       package com.bjpowernode.java.thread;
       /*
       在java中怎么强行终止一个线程的执行。
        */
       public class ThreadTest09 {
           public static void main(String[] args) {
               Thread t = new Thread(new MyRunnable3());
               t.setName("t");
               t.start();
       
               //模拟5秒
               try {
                   Thread.sleep(1000 * 5);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
               //5秒后强行终止t线程
               t.stop();//已过时，不建议使用
                        //这种方式存在很大的缺点：容易丢失数据，因为直接将线程杀死了。
       
           }
       }
       
       class MyRunnable3 implements Runnable{
       
           @Override
           public void run() {
               for(int i=0; i<10; i++){
                   System.out.println(Thread.currentThread().getName() + "-->" + i);
                   try {
                       Thread.sleep(1000 );
                   } catch (InterruptedException e) {
                       e.printStackTrace();
                   }
               }
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.thread;
       /*
       怎样合理地终止线程？
        */
       public class ThreadTest10 {
           public static void main(String[] args) {
               MyRunable4 r = new MyRunable4();
               Thread t = new Thread(r);
               t.setName("t");
               t.start();
       
               //模拟5秒
               try {
                   Thread.sleep(5000);
               } catch (InterruptedException e) {
                   e.printStackTrace();
               }
       
               //终止线程
               //你想要什么时候终止t的执行，那么你把标记修改为false，就结束了。
               r.run = false;
           }
       }
       
       
       class MyRunable4 implements Runnable{
       
           boolean run = true;
       
           @Override
           public void run() {
               for (int i=0; i<10; i++){
                   if(run){
                       System.out.println(Thread.currentThread().getName() + "-->" + i);
                       try {
                           Thread.sleep(1000);
                       } catch (InterruptedException e) {
                           e.printStackTrace();
                       }
                   }else{
                       return;
                   }
               }
           }
       }
       ```

    9. 线程调度

       1. 常见的线程调度模型有哪些？

          那个线程的优先级比较高，抢到的CPU时间片的概率就高一些/多一些。java采用的就是抢占式调度模型。

       2. 均分式调度模型：

          平均分配CPU时间片，每个线程占有的CPU时间片时间长度一样。平均分配，一切平等。

          有些编程语言，线程调度模型采用的就是这种方式。

       3. java中提供了哪些方法是和线程调度有关系的？

          实例方法：

          ```java
          void setPriority(int newPriority) 设置线程的优先级
          int getPriority() 获取线程优先级
              最低优先级1
              默认优先级5
              最高优先级10
              优先级比较高的获取CPU时间片可能会多一些。
          
              
          void join() 合并线程
          class MyThread1 extends Thread{
              public void doSome(){
                  MyThread2 t = new MyThread2();
                  t.join(); //当前线程进入阻塞，t线程执行，直到t线程结束，当前线程才可以继续。 
              }
          }
          class MyThread2 extends Thread{
              
          }
          ```

          静态方法

          ```java
          static void yield() 让位方法
              暂停当前正在执行的线程对象，并执行其他线程
              yield()方法不是阻塞方法。让当前线程让位，让给其他线程使用。
              yield()方法的执行会让当前线程从“运行状态”回到“就绪状态”
          ```

          ```java
          package com.bjpowernode.java.thread;
          /*
          关于线程的优先级
          
           */
          public class ThreadTest11 {
              public static void main(String[] args) {
          //        System.out.println("最高优先级" + Thread.MAX_PRIORITY);
          //        System.out.println("默认优先级" + Thread.NORM_PRIORITY);
          //        System.out.println("最低优先级" + Thread.MIN_PRIORITY);
                  Thread.currentThread().setPriority(1);
          
                  //获取当前线程对象，获取当前线程的优先级
                  Thread currentThread = Thread.currentThread();
                  System.out.println(currentThread.getName() + "线程的默认优先级是：" + currentThread.getPriority());//main线程的默认优先级是：5
          
                  Thread t = new Thread(new MyRunnable5());
                  t.setName("t");
                  t.start();//t线程的默认优先级：5
              }
          }
          
          
          class MyRunnable5 implements Runnable{
          
              @Override
              public void run() {
                  System.out.println(Thread.currentThread().getName() + "线程的默认优先级：" + Thread.currentThread().getPriority());
              }
          }
          ```

          ```java
          package com.bjpowernode.java.thread;
          /*
          让位，当前运行的线程暂停，回到就绪状态，让给其他线程。
          静态方法：Thread.yield();
           */
          public class ThreadTest12 {
              public static void main(String[] args) {
                  Thread t = new Thread(new MyRunnable6());
                  t.setName("t");
                  t.start();
          
                  for (int i=0; i<10000; i++){
                      System.out.println(Thread.currentThread().getName() + "--->" + i);
                  }
              }
          }
          
          
          class MyRunnable6 implements Runnable{
          
              @Override
              public void run() {
                  for (int i=0; i<10000; i++){
                      //每100个让位一次
                      if (i%100 == 0){
                          Thread.yield();
                      }
                      System.out.println(Thread.currentThread().getName() + "--->" + i);
                  }
          
              }
          }
          ```

          ```java
          package com.bjpowernode.java.thread;
          /*
          线程合并
           */
          public class ThreadTest13 {
              public static void main(String[] args) {
                  System.out.println("main begin");
          
                  Thread t = new Thread(new MyRunnable7());
          
                  t.setName("t");
                  t.start();
          
                  //合并线程
                  try {
                      t.join();  // t合并到当前线程中，当前线程受阻，t线程执行到结束。
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
          
                  System.out.println("main over");
          
              }
          }
          
          class MyRunnable7 implements Runnable{
          
              @Override
              public void run() {
                  for(int i=0; i<100; i++){
                      System.out.println(Thread.currentThread().getName() + "--->" + i);
                  }
              }
          }
          
          ```

       4. 关于多线程并发环境下， 数据的安全问题

          1. 什么时候在多线程并发环境下，数据存在安全问题？

             三个条件：(1) 多线程并发 (2) 有共享数据 (3) 共享数据有修改行为

          2. 怎么解决线程安全问题呢？

             线程排队执行。(不能并发)。用排队执行解决线程安全问题。这种机制被称为：**线程同步机制**。线程排队会牺牲一部分效率。

          3. 异步编程模型：线程t1和线程t2，各自执行各自的，t1不管t2，t2不管t1，也就是多线程并发。

             同步编程模型：线程t1和线程t2，两个线程之间发生了等待关系，也就是线程排队执行。

          ```java
          package com.bjpowernode.java.thread.threadsafe;
          /*
          银行账户
              不使用线程同步机制，多线程对同一账户进行取款，出现线程安全问题
           */
          public class Account {
              //账号
              private String actno;
          
              //余额
              private double balance;
          
              public Account() {
              }
          
              public Account(String actno, double balance) {
                  this.actno = actno;
                  this.balance = balance;
              }
          
              public String getActno() {
                  return actno;
              }
          
              public void setActno(String actno) {
                  this.actno = actno;
              }
          
              public double getBalance() {
                  return balance;
              }
          
              public void setBalance(double balance) {
                  this.balance = balance;
              }
          
              //取款的方法
              public void withdraw(double money){
                  //取款之前的余额
                  double before = this.getBalance();
          
                  //取款之后的余额
                  double after = before - money;
          
                  //在这里模拟一下网络延迟，100%会出问题
                  try {
                      Thread.sleep(1000);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
          
                  //更新余额
                  //思考：t1执行到这里了，但还没来得及执行这行代码，t2线程进来withdraw方法了，此时一定出问题
                  this.setBalance(after);
              }
          }
          
          
          package com.bjpowernode.java.thread.threadsafe;
          
          public class AccountThread extends Thread{
              //两个线程必须共享同一个账户对象
              private Account act;
          
              //通过构造方法传递过来账户对象
              public AccountThread(Account act){
                  this.act = act;
              }
          
          
              public void run(){
                  //run方法的执行表示取款操作
                  //假设取款5000
                  double money = 5000;
                  act.withdraw(money);
                  System.out.println(Thread.currentThread().getName() + "账户"+act.getActno()+"取款成功，余额"+act.getBalance());
              }
          }
          
          
          package com.bjpowernode.java.thread.threadsafe;
          
          public class Test {
              public static void main(String[] args) {
                  //创建账户对象
                  Account act = new Account("act-001", 10000);
          
                  //创建两个线程
                  Thread t1 = new AccountThread(act);
                  Thread t2 = new AccountThread(act);
          
                  //设置name
                  t1.setName("t1");
                  t2.setName("t2");
          
                  //启动线程取款
                  t1.start();
                  t2.start();
              }
          }
          
          ```

          修改后

          ```java
          package com.bjpowernode.java.thread.threadsafe2;
          /*
          银行账户
              不使用线程同步机制，多线程对同一账户进行取款，出现线程安全问题
           */
          public class Account {
              //账号
              private String actno;
          
              //余额
              private double balance;
          
              public Account() {
              }
          
              public Account(String actno, double balance) {
                  this.actno = actno;
                  this.balance = balance;
              }
          
              public String getActno() {
                  return actno;
              }
          
              public void setActno(String actno) {
                  this.actno = actno;
              }
          
              public double getBalance() {
                  return balance;
              }
          
              public void setBalance(double balance) {
                  this.balance = balance;
              }
          
              //取款的方法
              public void withdraw(double money){
                  //以下这几行代码必须是线程排队的，不能并发
                  //一个线程把这里的代码全部执行结束之后，另一个线程才能进来。
          
                  /*
                  线程同步机制的语法是：
                      synchronized(){
                          //线程同步代码块
                      }
                      synchronized后面小括号中传的这个数据是相当关键的。
                      这个数据必须是多线程共享的数据，才能达到多线程排队。
          
                      ()中写什么？那要看你想让哪些线程同步。
                          假设t1,t2,t3,t4,t5有5个线程，你只希望t1,t2,t3排队，t4,t5不需要排队，怎么办？
                          你一定要在()中写一个t1,t2,t3共享的对象，而这个对象对于t4,t5来说不是共享的。
          
                      这里的共享对象是：账户对象
                      账户对象是共享的，那么this就是账户对象
                      不一定是this,这里只要是多线程共享的那个对象就行。
          
                      在java语言中，任何一个对象都有一把锁，其实这把锁就是标记
          
                      以下代码的执行原理？
                          1. 假设t1和t2线程并发，开始执行以下代码的时候，肯定有一个先一个后。
                          2. 假设t1先执行了，遇到了synchronized,这个时候自动找“后面共享对象”的对象锁
                              找到之后，并占有这把锁，然后执行同步代码块中的程序，在程序执行过程中一直都是
                              占有这把锁的，直到同步代码块代码结束，这把锁才会释放。
                              而t2只能在同步代码块外面等待t1的结束，知道t1把同步代码块执行结束，t1会归还这把锁
                              此时t2终于等到这把锁，然后t2占有这把锁，进入同步代码块执行程序。
          
                          需要注意的是：这个共享对象一定要选好了，这个共享对象一定要选好，这个共享对象一定是
                          你需要排队执行的这些线程对象所共享的。
                   */
                  synchronized (this) {
                      double before = this.getBalance();
                      double after = before - money;
          
                      try {
                          Thread.sleep(1000);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
          
                      //更新余额
          
                      this.setBalance(after);
                  }
              }
          }
          
          
          package com.bjpowernode.java.thread.threadsafe2;
          
          public class AccountThread extends Thread{
              //两个线程必须共享同一个账户对象
              private Account act;
          
              //通过构造方法传递过来账户对象
              public AccountThread(Account act){
                  this.act = act;
              }
          
          
              public void run(){
                  //run方法的执行表示取款操作
                  //假设取款5000
                  double money = 5000;
                  act.withdraw(money);
                  System.out.println(Thread.currentThread().getName() + "账户"+act.getActno()+"取款成功，余额"+act.getBalance());
              }
          }
          
          
          package com.bjpowernode.java.thread.threadsafe2;
          
          public class Test {
              public static void main(String[] args) {
                  //创建账户对象
                  Account act = new Account("act-001", 10000);
          
                  //创建两个线程
                  Thread t1 = new AccountThread(act);
                  Thread t2 = new AccountThread(act);
          
                  //设置name
                  t1.setName("t1");
                  t2.setName("t2");
          
                  //启动线程取款
                  t1.start();
                  t2.start();
              }
          }
          //t2账户act-001取款成功，余额5000.0
          //t1账户act-001取款成功，余额0.0
          ```

          Java中三大变量：实例变量[在堆中]，静态变量[在方法区中], 局部变量[在栈中]。

          以上三大变量中：局部变量永远都不会存在线程安全问题，因为局部变量不共享。(一个线程一个栈。)

          但是，如果使用局部变量的话，建议使用StringBuilder，因为局部变量不存在线程安全问题。

          【总结】synchronized有两种写法：

          ```java
          第一种：同步代码块
              灵活
              synchronized(线程共享对象){
              同步代码块;
          }
          
          第二种：在实例方法上使用synchronized
              表示共享对象一定是this
              并且同步代码块是整个方法体
          
          第三种：在静态方法上使用synchronized
              表示找类锁
              类锁永远只有1把
              就算创建了100个对象，那类锁也只有一把。
          ```

          ```java
          package com.bjpowernode.java.thread.exam1;
          /*
          面试题：doOther方法执行的时候需要等待doSome方法的结束吗？不需要，因为doOther执行不需要锁
           */
          public class Example1 {
              public static void main(String[] args) {
                  MyClass mc = new MyClass();
                  Thread t1 = new MyThread(mc);
                  Thread t2 = new MyThread(mc);
          
                  t1.setName("t1");
                  t2.setName("t2");
          
                  t1.start();
                  try {
                      Thread.sleep(1000);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  t2.start();
              }
          }
          
          class MyThread extends Thread{
              private MyClass mc;
              public MyThread(MyClass mc){
                  this.mc = mc;
              }
          
              public void run(){
                  if(Thread.currentThread().getName().equals("t1")){
                      mc.doSome();
                  }
                  if(Thread.currentThread().getName().equals("t2")){
                      mc.doOther();
                  }
              }
          }
          
          
          class MyClass{
              public synchronized void doSome(){
                  System.out.println("doSome begin");
                  try {
                      Thread.sleep(1000*10);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  System.out.println("doSome over");
          
              }
          
              public void doOther(){
                  System.out.println("doOther begin");
          
                  System.out.println("doOther over");
          
              }
          }
          ```

          ```java
          package com.bjpowernode.java.thread.exam2;
          /*
          面试题：doOther方法执行的时候需要等待doSome方法的结束吗？需要，因为doOther执行需要锁，所以需要等待
           */
          public class Example1 {
              public static void main(String[] args) {
                  MyClass mc = new MyClass();
                  Thread t1 = new MyThread(mc);
                  Thread t2 = new MyThread(mc);
          
                  t1.setName("t1");
                  t2.setName("t2");
          
                  t1.start();
                  try {
                      Thread.sleep(1000);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  t2.start();
              }
          }
          
          class MyThread extends Thread{
              private MyClass mc;
              public MyThread(MyClass mc){
                  this.mc = mc;
              }
          
              public void run(){
                  if(Thread.currentThread().getName().equals("t1")){
                      mc.doSome();
                  }
                  if(Thread.currentThread().getName().equals("t2")){
                      mc.doOther();
                  }
              }
          }
          
          
          class MyClass{
              //synchronized锁的是MyClass对象，而不是方法
              public synchronized void doSome(){
                  System.out.println("doSome begin");
                  try {
                      Thread.sleep(1000*10);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  System.out.println("doSome over");
          
              }
          
              public synchronized void doOther(){
                  System.out.println("doOther begin");
          
                  System.out.println("doOther over");
          
              }
          }
          ```

          ```java
          package com.bjpowernode.java.thread.exam3.exam2;
          /*
          面试题：doOther方法执行的时候需要等待doSome方法的结束吗？需要，因为静态方法是类锁，类锁不管创建了几个对象，类锁只有一把
           */
          public class Example1 {
              public static void main(String[] args) {
                  MyClass mc1 = new MyClass();
                  MyClass mc2 = new MyClass();
          
                  Thread t1 = new MyThread(mc1);
                  Thread t2 = new MyThread(mc2);
          
                  t1.setName("t1");
                  t2.setName("t2");
          
                  t1.start();
                  try {
                      Thread.sleep(1000);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  t2.start();
              }
          }
          
          class MyThread extends Thread{
              private MyClass mc;
              public MyThread(MyClass mc){
                  this.mc = mc;
              }
          
              public void run(){
                  if(Thread.currentThread().getName().equals("t1")){
                      mc.doSome();
                  }
                  if(Thread.currentThread().getName().equals("t2")){
                      mc.doOther();
                  }
              }
          }
          
          
          class MyClass{
              //synchronized应用到静态方法的时候是类锁
              public synchronized static void doSome(){
                  System.out.println("doSome begin");
                  try {
                      Thread.sleep(1000*10);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  System.out.println("doSome over");
          
              }
          
              public synchronized static void doOther(){
                  System.out.println("doOther begin");
          
                  System.out.println("doOther over");
          
              }
          }
          ```

       5. 死锁

          ```java
          package com.bjpowernode.java.deadlock;
          /*
          死锁代码要会写
          因为只有会写的，才会在之后的开发中注意这个事儿，因为死锁很难调试。
          synchronized最好不要嵌套使用，否则容易出现死锁。
           */
          public class Deadlock {
              public static void main(String[] args) {
                  Object o1 = new Object();
                  Object o2 = new Object();
          
                  //t1和t2共享o1和o2
                  Thread t1 = new MyThread1(o1, o2);
                  Thread t2 = new MyThread2(o1, o2);
          
                  t1.start();
                  t2.start();
              }
          }
          
          class MyThread1 extends Thread{
              Object o1;
              Object o2;
              public MyThread1(Object o1, Object o2){
                  this.o1 = o1;
                  this.o2 = o2;
              }
              public void run(){
                  synchronized (o1){
                      try {
                          Thread.sleep(1000);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
                      synchronized (o2){
          
                      }
                  }
              }
          }
          
          class MyThread2 extends Thread{
              Object o1;
              Object o2;
              public MyThread2(Object o1, Object o2){
                  this.o1 = o1;
                  this.o2 = o2;
              }
              public void run(){
                  synchronized (o2){
                      try {
                          Thread.sleep(1000);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
                      synchronized (o1){
          
                      }
                  }
              }
          }
          
          ```

       6. 开发中怎么解决线程安全问题。

          synchronized会让程序的执行效率变低，用户体验不好。系统的用户吞吐量降低。用户体验差，在不得已的情况下再选择线程同步机制。

          第一种方案：尽量使用局部变量代替"实例变量和静态变量"。

          第二种方案：如果必须是实例变量，那么可以考虑创建多个对象，这样实例变量的内存就不共享了。(一个线程对应1个对象，100个线程对应100个对象，对象如果不共享，就没有数据安全问题了。)

          第三种方案：如果不能使用局部变量，对象也不能创建多个，这个时候就只能选择synchronized了，线程同步机制。

       7. 线程的其他内容

          1. 守护线程：Java中线程分为两类：一类是用户线程。一类是守护线程(后台线程)。其中最具有代表性的就是：垃圾回收线程(守护线程)。主线程main方法是一个用户线程

             守护线程的特点：一般守护线程是一个死循环，所有的用户线程只要结束，守护线程自动结束。

             守护线程用在什么地方呢？每天00:00时系统数据自动备份，这个需要使用定时器，并且可以将定时器设置为守护线程。

             ```java
             package com.bjpowernode.java.thread;
             /*
             守护线程
              */
             public class ThreadTest14 {
                 public static void main(String[] args) {
                     Thread t = new BakDataThread();
                     t.setName("备份数据的线程");
             
                     //启动线程之前，将线程设置为守护线程
                     t.setDaemon(true);
                     t.start();
             
                     //主线程：主线程是用户线程
                     for(int i=0; i<10; i++){
                         System.out.println(Thread.currentThread().getName() + "-->"+ i);
                         try {
                             Thread.sleep(1000);
                         } catch (InterruptedException e) {
                             e.printStackTrace();
                         }
                     }
                 }
             }
             
             class BakDataThread extends Thread{
                 public void run(){
                     int i=0;
                     while (true){
                         System.out.println(Thread.currentThread().getName() + "-->"+ (++i));
                         try {
                             Thread.sleep(1000);
                         } catch (InterruptedException e) {
                             e.printStackTrace();
                         }
                     }
                 }
             }
             
             ```

          2. 定时器

             定时器的作用：间隔特定的时间，执行特定的程序。比如每周需要进行银行账户的总账操作，或者进行备份操作。定时器在java中其实可以采用多种方式实现：

             1. sleep方法，这种是最原始的定时器

             2. java类库中已经写好了一个定时器，java.util.Timer,可以直接拿来用，不过这种方式在目前的开发中也很少用，因为现在有很多高级框架都是支持定时任务的。

                在实际的开发中，目前使用较多的是Spring框架中提供的SpringTask框架，这个框架只要进行简单的配置，就可以完成定时器的任务。

                ```java
                package com.bjpowernode.java.thread;
                
                import java.text.ParseException;
                import java.text.SimpleDateFormat;
                import java.util.Date;
                import java.util.Timer;
                import java.util.TimerTask;
                
                /*
                使用定时器指定定时任务
                 */
                public class TimerTest {
                    public static void main(String[] args) throws ParseException {
                        //创建定时器对象
                        Timer timer = new Timer();
                
                        //指定定时任务
                        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
                        Date firstTime = sdf.parse("2021-04-14 10:50:00");
                        timer.schedule(new LogTimerTask(), firstTime, 1000*10);
                    }
                }
                
                //编写一个定时任务类
                //假设这是一个记录日志的定时任务
                class LogTimerTask extends TimerTask{
                
                    @Override
                    public void run() {
                       //编写你需要执行的任务就行了
                        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
                        String strTime = sdf.format(new Date());
                        System.out.println(strTime + ":成功完成了一次数据备份！");
                    }
                }
                
                ```

             3. 实现线程的第三种方式：FutureTask方式，实现Callable接口。(JDK8新特性)

                这种方式实现的线程可以获取线程的返回值。之前讲解的两种方式无法获取线程返回值的，因为run方法返回void。

                思考：系统委派一个线程去执行一个任务，该线程执行完任务之后，可能会有一个执行结果，我们怎么能拿到这个执行结果呢？可以使用第三种方式，实现Callable接口方式。

                ```java
                package com.bjpowernode.java.thread;
                
                import java.util.concurrent.Callable;
                import java.util.concurrent.ExecutionException;
                import java.util.concurrent.FutureTask;//JUC包下的，属于java的并发包，老JDK中没有这个包，新特性。
                
                /*
                实现线程的第三种方式：
                    实现Callable接口
                    这种方式的优点：可以获取到线程的执行结果
                    缺点是：效率比较低，在获取t线程执行结果的时候，当前线程受阻塞，效率较低
                 */
                public class ThreadTest15 {
                    public static void main(String[] args) throws ExecutionException, InterruptedException {
                        //第一步：创建一个"未来任务类"对象
                        //参数非常重要，需要给一个Callable接口的实现类对象
                        FutureTask task = new FutureTask(new Callable() {
                            @Override
                            public Object call() throws Exception {
                                // call()方法就相当于run方法，只不过这个有返回值
                                //线程执行一个任务，执行之后可能会有一个执行结果
                                //模拟执行
                                System.out.println("call method begin");
                                Thread.sleep(1000*10);
                                System.out.println("call method end");
                                int a = 100;
                                int b = 200;
                                return a + b;
                            }
                        });
                
                        //创建线程对象
                        Thread t = new Thread(task);
                
                        //启动线程
                        t.start();
                
                        //这里是main方法，在主线程中
                        //在主线程中，怎么获取t线程结果
                        Object obj = task.get();
                
                        //main方法这里的程序要想执行必须等待get()方法的结束
                        //而get()方法可能需要很久。因为get()方法是为了拿另一个线程的执行结果，需要等待另一个线程执行结束。
                        System.out.println("hello world");
                    }
                }
                
                ```

                

          3. 关于Object类中的wait和notify方法。(生产者和消费者模式)

             wait和notify方法不是线程对象的方法，是java中任何一个java对象都有的方法，因为这两个方法是Object类中自带的。
           
             wait()方法的作用
             
             ```java
             Object o = new Object();
             o.wait();
             表示：让正在o对象上活动的线程进入等待状态，无限期等待，直到被唤醒为止。
             o.wait()方法的调用，会让“当前线程(正在o对象上活动的线程)”进入等待状态。
             ```
             
             notify()方法的作用
             
             ```java
             Object o = new Object();
             o.notify();
             表示：唤醒正在o对象上等待的线程。
             还有一个notifyAll()方法：
                 这个方法是唤醒o对象上处于等待的所有线程。
             ```
             
             ![image-20210415093747564](https://i.loli.net/2021/04/15/DLMZJOE1Yb2WHrC.png)
             
             ```java
             package com.bjpowernode.java.thread;
             
             import java.util.ArrayList;
             import java.util.List;
             
             /*
             1. 使用wait方法和notify方法实现"生产者和消费者模式"
             2. 什么是"生产者和消费者模式"？
                 生产线程负责生产，消费线程负责消费
                 生产线程和消费线程需要达到平衡
                 这是一种特殊的业务需求，在这种特殊的情况下需要使用wait方法和notify方法.
             3. wait和notify方法不是线程对象的方法，是普通java对象都有的方法
             4. wait方法和notify方法建立在线程同步的基础之上，因为多线程要同时操作一个仓库，有线程安全问题
             5. wait方法作用：o.wait()让正在o对象上活动的线程t进入等待状态，并且释放掉t线程之前占有的o对象的锁。
             6. wait方法作用：o.notify()让正在o对象上等待的线程唤醒，只是通知，不会释放o对象上之前占有的锁。
             
             7. 模拟这个需求：
                 仓库采用list集合，list集合假设只能存储1个元素，1个元素就表示仓库满了，0个元素就表示仓库空了
                 保证list集合中永远都是最多存储1个元素
             
                 必须做到：生产1个消费1个
             
             
              */
             public class ThreadTest16 {
                 public static void main(String[] args) {
                     //创建1个仓库对象，共享的
                     List list = new ArrayList();
             
                     //创建两个线程对象
                     //生产者线程
                     Thread t1 = new Thread(new Producer(list));
                     //消费者线程
                     Thread t2 = new Thread(new Consumer(list));
             
                     t1.setName("生产者线程");
                     t2.setName("消费者线程");
             
                     t1.start();
                     t2.start();
                 }
             }
             
             //生产线程
             class Producer implements Runnable{
                 //共享一个仓库
                 private List list;
             
                 public Producer(List list){
                     this.list = list;
                 }
             
                 @Override
                 public void run() {
                     //一直生产(使用死循环来模拟一直生产)
                     while (true) {
                         //给仓库对象list加锁
                         synchronized (list) {
                             if (list.size() > 0) {
                                 //当前线程进入等待状态,并且释放Producer之前占有的list集合的锁
                                 try {
                                     list.wait();
                                 } catch (InterruptedException e) {
                                     e.printStackTrace();
                                 }
                             }else {
                                 //程序能够执行到这里说明仓库是空的，可以生产
                                 Object obj = new Object();
                                 list.add(obj);
                                 System.out.println(Thread.currentThread().getName() + "--->" + obj);
             
                                 // 唤醒消费者进行消费
                                 list.notify();
                             }
                         }
                     }
                 }
             }
             
             //消费线程
             class Consumer implements Runnable{
                 //共享一个仓库
                 private List list;
             
                 public Consumer(List list){
                     this.list = list;
                 }
             
                 @Override
                 public void run() {
                     //一直消费
                     while (true){
                         synchronized (list){
                             if(list.size() == 0){
                                 //仓库已经空了。消费者线程等待，释放掉list集合的锁。
                                 try {
                                     list.wait();
                                 } catch (InterruptedException e) {
                                     e.printStackTrace();
                                 }
                             }else {
                                 //程序能够执行到此处说明仓库中有数据，进行消费。
                                 Object obj = list.remove(0);
                                 System.out.println(Thread.currentThread().getName() + "--->" + obj);
             
                                 //唤醒生产者生产
                                 list.notify();
                             }
                         }
                     }
                 }
             }
             
             
             ```
             
             ```java
             //作业
             package com.bjpowernode.java.thread;
             /*
             使用生产者和消费者模式实现，交替输出：
             假设只有两个线程，输出以下结果：
             t1 --> 1
             t2 --> 2
             t1 --> 3
             t2 --> 4
             ...
             要求：必须交替，并且t1线程负责输出奇数，t2线程负责输出偶数
              */
             public class ThreadTest17 {
                 public static void main(String[] args) {
                     //创建一个数字对象,共享的
                     Num num = new Num();
             
             
                     //创建两个线程对象
                     //奇数线程
                     Thread t1 = new Thread(new jishu(num));
                     //偶数线程
                     Thread t2 = new Thread(new oushu(num));
             
                     t1.setName("t1");
                     t2.setName("t2");
             
                     t1.start();
                     t2.start();
                 }
             }
             
             //奇数线程
             class jishu implements Runnable{
                 //共享一个数字
                 private Num num;
             
                 public jishu(Num num){
                     this.num = num;
                 }
             
             
             
                 @Override
                 public void run() {
                     while (true){
                         synchronized (num){
                             if (num.i % 2 == 0){
                                 try {
                                     num.wait();
                                 } catch (InterruptedException e) {
                                     e.printStackTrace();
                                 }
                             } else {
                                 //程序能够执行到这里说明i是奇数
                                 System.out.println(Thread.currentThread().getName() + "-->" + num.i);
                                 num.i++;
             
                                 //唤醒偶数线程
                                 num.notify();
                             }
             
                         }
                     }
                 }
             }
             
             
             //偶数线程
             class oushu implements Runnable{
                 //共享一个数字
                 private Num num;
             
                 public oushu(Num num){
                     this.num = num;
                 }
             
             
             
                 @Override
                 public void run() {
                     while (true){
                         synchronized (num){
                             if(num.i % 2 != 0){
                                 try {
                                     num.wait();
                                 } catch (InterruptedException e) {
                                     e.printStackTrace();
                                 }
                             } else{
                                 //程序能执行到这里说明i是偶数
                                 System.out.println(Thread.currentThread().getName() + "-->" + num.i);
                                 num.i++;
             
                                 //唤醒奇数线程
                                 num.notify();
                             }
                         }
                     }
                 }
             }
             
             class Num{
                 int i = 1;
             }
             
             ```
    
14. 反射机制

    1. 作用：通过java中的反射机制可以操作字节码文件[class文件]。

    2. 反射机制的相关类在哪个包下？java.lang.reflect.*

    3. 反射机制的类有哪些

       ```java
       java.lang.Class 代表字节码文件
       java.lang.reflect.Method 代表字节码文件中的方法字节码
       java.lang.reflect.Constructor 代表字节码文件中的构造方法字节码
       java.lang.reflect.Field 代表字节码文件中的属性字节码
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.util.Date;
       
       /*
       要操作一个类的字节码，需要首先获取到这个类的字节码，怎么获取java.lang.Class实例？
           三种方式:
               1. Class c = Class.forName("完整类名带包名“);
               2. Class c = 对象.getClass();
               3. Class z = String.class;
        */
       public class ReflectTest01 {
           public static void main(String[] args) {
               /*
               Class.forName()
                   1. 静态方法
                   2. 方法的参数是一个字符串
                   3. 字符串需要的是一个完整类名
                   4. 完整类名必须带有包名。java.lang包不能忽略
                */
               Class c1 = null;
               try {
                   c1 = Class.forName("java.lang.String");//c1代表String.class文件，或者说c1代表String类型
                   Class c2 = Class.forName("java.util.Date");//c2代表Date类型
                   Class c3 = Class.forName("java.lang.Integer");//c3代表Integer类型
                   Class c4 = Class.forName("java.lang.System");//c4代表System类型
               } catch (ClassNotFoundException e) {
                   e.printStackTrace();
               }
       
               //java中任何一个对象都有一个方法：getClass()
               String s = "abc";
               Class x = s.getClass(); //x代表String.class字节码文件，x代表String类型
               System.out.println(c1 == x);
       
               //第三种方式，java语言中任何一种类型，包括基本数据类型， 它都有.class属性
               Class z = String.class; //z代表String类型
               Class k = Date.class; //k代表Date类型
               Class f = int.class; //f代表int类型
               Class e = double.class; //e代表double类型
       
       
       
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import src.com.bjpowernode.java.bean.User;
       
       public class ReflectTest02 {
           public static void main(String[] args) {
               //这是不使用反射机制，创建对象，这种方式代码就写死了，只能创建一个User类型的对象
               User user = new User();
               System.out.println(user);
       
               //这是以反射机制的方式创建对象，是灵活的，代码不需要改动，可以修改配置文件，配置文件修改之后，可以创建出不同的实例对象。
               try {
                   //通过反射机制，获取Class,通过Class来实例化对象
                   Class c = Class.forName("src.com.bjpowernode.java.bean.User");
       
                   //newInstance()这个方法会调用User这个类的无参数构造方法，完成对象的创建。
                   //重点是：newInstance()调用的是无参构造，必须保证无参构造是存在的！
                   Object obj = c.newInstance();
                   System.out.println(obj);
       
               } catch (ClassNotFoundException e) {
                   e.printStackTrace();
               } catch (InstantiationException e) {
                   e.printStackTrace();
               } catch (IllegalAccessException e) {
                   e.printStackTrace();
               }
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.io.FileNotFoundException;
       import java.io.FileReader;
       import java.util.Properties;
       
       /*
       验证反射机制的灵活性
           java代码写一遍，在不改变java源代码的基础之上，可以做到不同对象的实例化
           非常之灵活，符合OCP开闭原则：对扩展开放，对修改关闭。
       
       后期学习高级框架，而工作过程中使用的也是高级框架
       包括：
           ssh ssm
           Spring SpringMVC MyBatis
           Spring Struts Hibernate
       
           这些高级框架底层实现原理：都采用了反射机制，所以反射机制还是重要的
           学会了反射机制有利于理解框架底层的源代码
        */
       public class ReflectTest03 {
           public static void main(String[] args) throws Exception {
               //通过IO流读取classinfo.properties文件
               FileReader reader = new FileReader("chapter25/classinfo.properties");
               //创建属性类对象Map
               Properties pro = new Properties();
       
               //加载
               pro.load(reader);
               //关闭流
               reader.close();
       
               //通过key获取value
               String className = pro.getProperty("className");
               //System.out.println(className);
       
               //通过反射机制实例化对象
               Class c = Class.forName(className);
               Object obj = c.newInstance();
               System.out.println(obj);
       
       
           }
       }
       
       classinfo.properties文件内容为：
       className=java.util.Date
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       /*
       研究一下：Class.forName()发生了什么？
           记住，重点：
               如果你只是希望一个类的静态代码块执行，其它代码一律不执行
               你可以使用：
                   Class.forName("完整类名“)；
               这个方法的执行会导致类加载，类加载时，静态代码块执行
        */
       public class ReflectTest04 {
           public static void main(String[] args) {
               try {
                   Class.forName("src.com.bjpowernode.java.reflect.MyClass");
               } catch (ClassNotFoundException e) {
                   e.printStackTrace();
               }
           }
       }
       
       class MyClass{
           //静态代码块在类加载时执行，并且只执行一次
           static{
               System.out.println("MyClass类的静态代码块执行了");
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.io.FileReader;
       
       /*
       研究一下文件路径的问题
        */
       public class AboutPath {
           public static void main(String[] args) throws Exception{
               //这种方式的路径缺点是：移植性差，在IDEA中默认的当前路径是project的根
               //这个代码假设离开了IDEA，换到了其他位置，可能当前路径就不是project的根，这时这个路径就无效了。
               //FileReader reader = new FileReader("chapter25/classinfo2.properties");
       
               //接下来说一种比较通用的一种路径，即使代码换位置了，这样编写仍然是通用的
               //使用以下通用方式的前提是：这个文件必须在类路径下。
               //什么是类路径下？凡是在src下的都是在类路径下
               //src是类的根路径
       
               /*
               解释：
                   Thread.currentThread() 当前线程对象
                   getContextClassLoader() 是线程对象的方法，可以获取到当前线程的类加载器对象
                   getResource() 这是类加载器对象的方法，当前线程的类加载器默认从类的根路径下加载资源。
                */
               String path = Thread.currentThread().getContextClassLoader()
                       .getResource("classinfo2.properties").getPath();
               System.out.println(path);// /C:/Users/Administrator/Desktop/java_code/out/production/chapter25/classinfo2.properties
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.io.FileReader;
       import java.io.InputStream;
       import java.io.InputStreamReader;
       import java.util.Properties;
       
       public class IoPropertiesTest {
           public static void main(String[] args) throws Exception{
               //获取文件的绝对路径
       //        String path = Thread.currentThread().getContextClassLoader()
       //                .getResource("classinfo2.properties").getPath();
       //        FileReader reader = new FileReader(path);
       
               //直接以流的方式返回
               InputStream reader = Thread.currentThread().getContextClassLoader()
                       .getResourceAsStream("classinfo2.properties");
               Properties pro = new Properties();
               pro.load(reader);
               reader.close();
               //通过key获取value
               String className = pro.getProperty("className");
               System.out.println(className);
           }
       }
       
       ```

       ```java
       //终极方式，最方便的
       package src.com.bjpowernode.java.reflect;
       
       import java.util.ResourceBundle;
       
       /*
       java.util包下提供了一个资源绑定器，便于获取属性配置文件中的内容
       但是使用以下这种方式的时候，属性配置文件xxx.properties必须放到类路径下。
        */
       public class ResourceBundleTest {
           public static void main(String[] args) {
               //资源绑定器，只能绑定xxx.properties文件，并且这个文件必须在类路径下，文件扩展名也必须是properties。
               //并且在写路径的时候，路径后面的扩展名不能写
               ResourceBundle bundle = ResourceBundle.getBundle("classinfo2");
       
               String className = bundle.getString("className");
               System.out.println(className);
           }
       }
       
       ```

       扩展：

       JDK中自带的类加载器

       1. 什么是类加载器？

          专门负责加载类的命令/工具

          ClassLoader

       2. JDK中自带了3个类加载器

          启动类加载器

          扩展类加载器

          应用类加载器

       3. 假设有这样一段代码：String s = "abc";

          代码在开始执行之前，会将所需要的类全部加载到JVM当中。通过类加载器加载，看到以上代码类加载器会找String.class文件，找到就加载，那么是怎么进行加载的呢？

          首先，通过"启动类加载器"加载

          ​	注意：启动类加载器专门加载： C:\Program Files\Java\jdk1.8.0_101\jre\lib\rt.jar

          ​	rt.jar中都是JDK中最核心的类库。

          如果通过"启动类加载器"加载不到的时候，会通过"扩展类加载器"加载。

          注意：扩展类加载器专门加载：C:\Program Files\Java\jdk1.8.0_101\jre\lib\ext\*.jar

          如果"扩展类加载器"没有加载到，那么会通过"应用类加载器"加载。

          注意：应用类加载器专门加载：classpath中的jar包。

       4. java中为了保证类加载的安全，使用了双亲委派机制，优先从启动类加载器中加载，这个称为“父”，“父”无法加载到，再从扩展类加载器中加载，这个称为“母“。如果都加载不到，才会考虑到从应用类加载器中加载，直到加载到为止。

       ```Java
       package src.com.bjpowernode.java.reflect;
       
       import java.lang.reflect.Field;
       import java.lang.reflect.Modifier;
       
       /*
       反射Student类中所有的Field
        */
       public class ReflectTest05 {
           public static void main(String[] args) throws Exception{
               //获取整个类
               Class studentClass = Class.forName("src.com.bjpowernode.java.bean.Student");
               //获取类中所有的public 修饰的 Field
               Field[] fields = studentClass.getFields();
               System.out.println(fields.length);//no
       
               //获取所有的Field
               Field[] fs = studentClass.getDeclaredFields();
               System.out.println(fs.length);
       
               //遍历
               for(Field field:fs){
                   //获取属性的名字
                   System.out.println(field.getName());
       
                   //获取属性的类型
                   Class fieldType = field.getType();
                   String fName = fieldType.getName();
                   System.out.println(fName);
       
                   //获取属性的修饰符列表
                   int i = field.getModifiers();
                   String modifierString = Modifier.toString(i);
                   System.out.println(modifierString);
       
               }
           }
       }
       ------------------------------------------
       package src.com.bjpowernode.java.bean;
       //反射属性Field
       public class Student {
           //Field翻译为字段，其实就是属性/成员
           //4个Field,分别采用了不同的访问控制权限修饰符
           public int no; //Field对象
           private String name;
           protected int age;
           boolean sex;
           public static final double MATH_PI = 3.1415926;
       
       
       }
       
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.lang.reflect.Field;
       import java.lang.reflect.Modifier;
       
       /*
       通过反射机制，反编译一个类的属性Field
        */
       public class ReflectTest06 {
           public static void main(String[] args) throws Exception{
               //创建这个是为了拼接字符串
               StringBuilder s = new StringBuilder();
       
               Class studentClass = Class.forName("java.lang.String");
       
               s.append(Modifier.toString(studentClass.getModifiers())+ " class " + studentClass.getSimpleName() +" {\n");
       
               Field[] fields = studentClass.getDeclaredFields();
               for(Field field:fields){
                   s.append("\t");
                   s.append(Modifier.toString(field.getModifiers())); //获取修饰符
                   s.append(" ");
                   s.append(field.getType().getSimpleName());  //获取类型
                   s.append(" ");
                   s.append(field.getName()); //获取名字
                   s.append(";\n");
               }
       
               s.append("}");
               System.out.println(s);
       
           }
       
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import src.com.bjpowernode.java.bean.Student;
       
       import java.lang.reflect.Field;
       
       /*
       通过反射机制访问一个java对象的属性？
           给属性赋值set
           获取属性的值get
        */
       public class ReflectTest07 {
           public static void main(String[] args) throws Exception{
               //我们不使用反射机制，怎么去访问一个对象的属性呢？
               Student s = new Student();
               //给属性赋值
               s.no = 1111;
               //读属性值
               System.out.println(s.no); //1111
       
               //通过反射机制,怎么去访问一个对象的属性
               Class studentClass = Class.forName("src.com.bjpowernode.java.bean.Student");
               Object obj = studentClass.newInstance(); //Obj 就是 Student对象。(底层调用无参数构造方法)
       
               //获取no属性(根据属性的名称来获取Field)
               Field noFiled = studentClass.getDeclaredField("no");
       
               //给obj对象的no属性赋值
               noFiled.set(obj, 2222); //给obj对象的no属性赋值2222
       
               //读取属性的值
               System.out.println(noFiled.get(obj));
       
               //可以访问私有的属性吗？不可以，除非打破封装
       
               Field nameField = studentClass.getDeclaredField("name");
               //打破封装
               nameField.setAccessible(true);
       
               nameField.set(obj, "jackson");
               System.out.println(nameField.get(obj));
       
       
           }
       }
       
       ```

    4. 可变长度参数

       ```java
       package src.com.bjpowernode.java.reflect;
       /*
       可变长度参数
           int... args这就是可变长度参数
           语法是：类型...(注意:一定是3个点)
       
           1. 可变长度参数要求的参数个数是：0-N个。
           2. 可变长度参数在参数列表中必须在最后一个位置上，而且可变长度参数只能有1个。
           3. 可变长度参数可以当做一个数组来看待。
        */
       public class ArgsTest {
           public static void main(String[] args) {
               m();
               m(10);
               m(10,20);
       
               m2(100);
               m2(100, "abc");
               m2(100, "abc", "def");
               m2(100, "abc", "def", "xyz");
       
               m3("ab", "de", "kk", "ff");
               String[] strs = {"a", "b", "c"};
               //也可以传一个数组
               m3(strs);
           }
       
           public static void m(int... args){
               System.out.println("m方法执行了");
           }
       
           public static void m2(int a, String... args1){
       
           }
       
           public static void m3(String... args){
               //args有length属性，说明args是一个数组！
               //可以将一个
               for(int i=0; i< args.length; i++){
                   System.out.println(args[i]);
               }
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.lang.reflect.Method;
       import java.lang.reflect.Modifier;
       
       /*
       作为了解内容：
           反射Method
        */
       public class ReflectTest08 {
           public static void main(String[] args) throws Exception{
               //获取类
               Class userServiceClass = Class.forName("src.com.bjpowernode.java.service.UserService");
               //获取所有的Method(包括私有的)
               Method[] methods = userServiceClass.getDeclaredMethods();
               System.out.println(methods.length);//2
       
               //遍历Method
               for(Method method:methods){
                   //获取修饰符列表
                   System.out.println(Modifier.toString(method.getModifiers()));
       
                   //获取方法的返回值类型
                   System.out.println(method.getReturnType().getSimpleName());
       
                   //获取方法名
                   System.out.println(method.getName());
       
                   //获取方法的修饰符列表(一个方法的参数可能会有多个)
                   Class[] parameterTypes = method.getParameterTypes();
                   for (Class parameterType : parameterTypes){
                       System.out.println(parameterType.getSimpleName());
                   }
               }
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import java.lang.reflect.Method;
       import java.lang.reflect.Modifier;
       
       /*
       反编译一个类的Method
        */
       public class ReflectTest09 {
           public static void main(String[] args) throws Exception{
               StringBuilder s = new StringBuilder();
               Class userServiceClass = Class.forName("src.com.bjpowernode.java.service.UserService");
               s.append(Modifier.toString(userServiceClass.getModifiers()) + " class " + userServiceClass.getSimpleName() +"{\n");
       
               Method[] methods = userServiceClass.getDeclaredMethods();
               for (Method method:methods){
                   //public boolean login(String name, String password){}
                   s.append("\t");
                   s.append(Modifier.toString(method.getModifiers()));
                   s.append(" ");
                   s.append(method.getReturnType().getSimpleName());
                   s.append(" ");
                   s.append(method.getName());
                   s.append("(");
                   //参数列表
                   Class[] parameterTypes = method.getParameterTypes();
                   for (Class parameterType:parameterTypes){
                       s.append(parameterType.getSimpleName());
                       s.append(",");
                   }
                   s.deleteCharAt(s.length() - 1);
                   s.append("){}\n");
       
               }
               s.append("}");
               System.out.println(s);
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import src.com.bjpowernode.java.service.UserService;
       
       import java.lang.reflect.Method;
       
       /*
       重点：必须掌握，通过反射机制怎么调用一个对象的方法？
       ***** 五颗星
        */
       public class ReflectTest10 {
           public static void main(String[] args) throws Exception{
               //不使用反射机制，怎么调用方法
               UserService userService = new UserService();
               boolean loginSuccess = userService.login("admin", "123");
               System.out.println(loginSuccess?"登陆成功":"登陆失败");
       
               //使用反射机制来调用一个对象的方法应该怎么做
               Class userServiceClass = Class.forName("src.com.bjpowernode.java.service.UserService");
               //创建对象
               Object obj = userServiceClass.getNestHost();
               //获取方法
               Method loginMethod = userServiceClass.getDeclaredMethod("login", String.class, String.class);
               //调用方法
               //反射机制中最最最重要的一个方法，必须记住
               Object retValue = loginMethod.invoke(obj, "admin", "123");
               System.out.println(retValue);
       
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.bean;
       
       public class Vip {
           int no;
           String name;
           String birth;
           boolean sex;
       
           public Vip() {
           }
       
           public Vip(int no, String name, String birth, boolean sex) {
               this.no = no;
               this.name = name;
               this.birth = birth;
               this.sex = sex;
           }
       }
       
       package src.com.bjpowernode.java.reflect;
       
       import java.lang.reflect.Constructor;
       import java.lang.reflect.Modifier;
       
       /*
       反编译一个类的Constructor构造方法
        */
       public class ReflectTest11 {
           public static void main(String[] args) throws Exception {
               StringBuilder s = new StringBuilder();
               Class vipClass = Class.forName("src.com.bjpowernode.java.bean.Vip");
               s.append(Modifier.toString(vipClass.getModifiers()));
               s.append(" class ");
               s.append(vipClass.getSimpleName());
               s.append("{\n");
               //拼接构造方法
               Constructor[] constructors = vipClass.getDeclaredConstructors();
               for (Constructor constructor : constructors){
                   s.append("\t");
                   s.append(Modifier.toString(constructor.getModifiers()));
                   s.append(" ");
                   s.append(vipClass.getSimpleName());
                   s.append("(");
                   //拼接参数
                   Class[] parameterTypes = constructor.getParameterTypes();
                   for (Class parameterType : parameterTypes){
                       s.append(parameterType.getSimpleName());
                       s.append(",");
                   }
                   if(parameterTypes.length >0){
                       s.deleteCharAt(s.length() - 1);
                   }
                   s.append("){}\n");
               }
       
       
               s.append("}");
               System.out.println(s);
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       
       import src.com.bjpowernode.java.bean.Vip;
       
       import java.lang.reflect.Constructor;
       
       /*
       
        */
       public class ReflectTest12 {
           public static void main(String[] args) throws Exception{
               //不使用反射机制怎么创建对象
               Vip v1 = new Vip();
               Vip v2 = new Vip(110, "zhangsan", "2001-10-11", true);
       
               //使用反射机制怎么创建对象呢？
               Class c = Class.forName("src.com.bjpowernode.java.bean.Vip");
               //调用无参数构造方法
               Object obj = c.getSimpleName();
               //调用有参数的构造方法怎么办？
               //第一步：先获取到这个有参数的构造方法
               Constructor con = c.getDeclaredConstructor(int.class, String.class, String.class, boolean.class);
               //第二步：调用构造方法new对象
               Object newObj = con.newInstance(110, "jackson", "1990-10-11", true);
               System.out.println(newObj);
       
       
           }
       }
       
       ```

       ```java
       package src.com.bjpowernode.java.reflect;
       /*
       重点：给你一个类，怎么获取这个类的父类，已经实现了哪些接口？
        */
       public class ReflectTest13 {
           public static void main(String[] args) throws Exception{
               //String举例
               Class stringClass = Class.forName("java.lang.String");
       
               //获取String的父类
               Class superClass = stringClass.getSuperclass();
               System.out.println(superClass.getSimpleName());//Object
       
               //获取String类实现的所有接口(一个类可以实现多个接口)
               Class[] interfaces = stringClass.getInterfaces();
               for(Class in:interfaces){
                   System.out.println(in.getName());
               }
           }
       }
       
       ```

15. 注解

    

    1. 注解，或者叫做注释类型,Annotation

    2. 注解是一种引用数据类型， 编译之后也是生成xxx.class文件

    3. 怎么自定义注解呢？语法格式？
       
        ```java
        [修饰符列表] @interface 注解类型名{
        }
        ```
        
    4. 注解怎么使用，用在什么地方？

        第一：注解使用时的语法格式：@注解类型名

        第二：注解可以出现在类上、属性上、方法上、变量上等...注解还可以出现在注解类型上,几乎可以出现在任何地方

        ```java
        package com.bjpowernode.java.annotation;
        /*
        自定义注解
         */
        public @interface MyAnnotation {
        }
        
        package com.bjpowernode.java.annotation;
        //注解修饰注解
        @MyAnnotation
        public @interface OtherAnnotation {
        }
        
        package com.bjpowernode.java.annotation;
        /*
        1. 注解，或者叫做注释,Annotation
        2. 注解是一种引用数据类型， 编译之后也是生成xxx.class文件
        3. 怎么自定义注解呢？语法格式？
            [修饰符列表] @interface 注解类型名{
            }
         */
        @MyAnnotation
        public class AnnotationTest01 {
            @MyAnnotation
            private int no;
            @MyAnnotation
            public static void m1(){
        
            }
            @MyAnnotation
            public void m2(){
        
            }
            @MyAnnotation
            public AnnotationTest01(){};
        }
        @MyAnnotation
        interface MyInterface{
        
        }
        
        ```

    5. JDK内置了哪些注释呢？

       java.lang包下的注释类型：

       掌握：

       Deprecated 用 @Deprecated 注释的程序元素，不鼓励程序员使用这样的元素，通常是因为它很危险或存在更好的选择。

       掌握：

       Override 表示一个方法声明打算重写超类中的另一个方法声明。

       不用掌握：

       SuppressWarnings指示应该在注释元素(以及包含在该注释元素中的所有程序元素)中取消显示指定的编译器警告。

       ```java
       package com.bjpowernode.java.annotation;
       /*
       关于JDK lang包下的Override注解
       源代码：
       public @interface Override{
       }
        */
       
       // @Override这个注解只能注解方法
       // @Override这个注解是给编译器参考的，和运行阶段没有关系
       // 凡是java中的方法带有这个注解的，编译器都会进行编译检查，如果这个方法不是重写父类的方法，编译器报错。
       //@Override 修饰类会报错
       public class AnnotationTest02 {
           @Override
           public String toString() {
               return "toString";
           }
       }
       
       ```

       元注解：

       用来标注“注解类型”的“注解”，称为元注解。

       常见的元注解有：Target、Retention。

       Target注解用来标注“被标注的注解”可以出现在哪些位置上

       ```java
       @Target(ElementType.METHOD):表示"被标注的注解"只能出现在方法上。
       ```

       Retention注解，用来标注"被标注的注解"最终保存在哪里。

       ```java
       @Retention(RetentionPolicy.SOURCE)：表示该注解只被保留在java源文件中。
       @Retention(RetentionPolicy.CLASS):表示该注解被保存在class文件中。
       @Retention(RetentionPolicy.RUNTIME):表示该注解被保存在class文件中，并且可以被反射机制读取到。
       ```

       ```java
       package com.bjpowernode.java.annotation;
       
       public class AnnotationTest03 {
       
           @Deprecated
           public void doSome(){
               System.out.println("do something1");
           }
           //Deprecated表示这个注解标注的元素已过时
           //这个注解主要是向其他程序员传达一个信息，此方法已过时。
           @Deprecated
           public void doOther(){
               System.out.println("do other...");
           }
       }
       
       class T {
           public static void main(String[] args) {
               AnnotationTest03 at = new AnnotationTest03();
               at.doSome();//表示此方法已过时
               at.doOther();
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.annotation2;
       
       public @interface MyAnnotation {
           /**
            * 我们通常在注解当中可以定义属性，以下这个是MyAnnotation的name属性。
            * 看着像一个方法，但实际上我们称之为属性name
            * @return
            */
           String name();
       
           String color();
       
           int age() default 25;//属性指定默认值
       }
       
       package com.bjpowernode.java.annotation2;
       @Deprecated
       public class MyAnnotationTest {
       
           //报错的原因：如果一个注解当中有属性，那么必须给属性赋值(除非该属性使用default指定了默认值)
           /*@MyAnnotation()
           public void doSome(){
       
           }
       
            */
           //@MyAnnotation(属性名=属性值)
           @MyAnnotation(name="zhangsan", color = "红色")
           public void doSome(){
       
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.annotation3;
       
       public @interface MyAnnotation {
           /*
           指定一个value属性
            */
           String value();
       }
       package com.bjpowernode.java.annotation3;
       
       public class MyAnnotationTest {
           //报错原因：没有指定属性的值
           /*@MyAnnotation()
           public void doSome(){
       
           }
       
            */
           @MyAnnotation(value = "hehe")
           public void doSome(){
       
           }
           @MyAnnotation("haha")
           public void doOther(){
       
           }
       }
       
       
       package com.bjpowernode.java.annotation3;
       /*
       如果一个注解的属性的名字是value，并且只有一个属性的话，在使用的时候，该属性名可以省略。
       
        */
       public @interface OtherAnnotation {
           String name();
       }
       
       package com.bjpowernode.java.annotation3;
       
       public class OtherAnnotationTest {
           //@OtherAnnotation("test")报错了，没有指定属性的值
           @OtherAnnotation(name = "test")
           public void doSome(){};
       }
       
       ```

       ```java
       package com.bjpowernode.java.annotation4;
       
       public enum Season {
           SPRING,SUMMER,AUTUMN,WINTER
       }
       
       package com.bjpowernode.java.annotation4;
       
       public @interface MyAnnotation {
           /*
           注解当中的属性可以是哪一种类型?
               属性的类型可以是：
                   byte short int long float double boolean char String Class 枚举类型
                   以及以上每一种的数组形式。
       
            */
           int value1();
           String value2();
           int[] value3();
           String[] value4();
           Season value5();
           Season[] value6();
           Class parameterType();
           Class[] parameterTypes();
       }
       
       
       
       ```

       ```java
       package com.bjpowernode.java.annotation4;
       
       public @interface OtherAnnotation {
           int age();
       
           String[] email();
       
           Season[] seasonArray();
       }
       
       package com.bjpowernode.java.annotation4;
       
       public class OtherAnnotationTest {
       
           @OtherAnnotation(age=25, email = {"zhangsan@123.com, zhangsan@sohu.com"}, seasonArray = Season.AUTUMN)
           public void doSome(){
       
           }
       
           //如果数组中只有1个元素，大括号可以省略
           @OtherAnnotation(age=25, email = "zhangsan@123.com", seasonArray = {Season.SPRING, Season.SUMMER})
           public void doOther(){
       
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.annotation5;
       
       import java.lang.annotation.ElementType;
       import java.lang.annotation.Retention;
       import java.lang.annotation.RetentionPolicy;
       import java.lang.annotation.Target;
       
       //只允许该注解可以标注类、方法
       @Target({ElementType.TYPE, ElementType.METHOD})
       //希望这个注解可以被反射
       @Retention(RetentionPolicy.RUNTIME)
       public @interface MyAnnotation {
           String value() default "北京大兴区";
       }
       
       package com.bjpowernode.java.annotation5;
       @MyAnnotation
       public class MyAnnotationTest {
           //@MyAnnotation,会报错
           int i;
           @MyAnnotation
           public void doSome(){
               //@MyAnnotation,会报错
               int i;
           }
       }
       
       package com.bjpowernode.java.annotation5;
       
       public class ReflectAnnotationTest {
           public static void main(String[] args) throws Exception{
               //获取这个类
               Class c = Class.forName("com.bjpowernode.java.annotation5.MyAnnotationTest");
               //判断类上面是否有@MyAnnotation
               System.out.println(c.isAnnotationPresent(MyAnnotation.class)); //true
       
               //判断String类上面是否存在这个注解
               Class stringClass = Class.forName("java.lang.String");
               System.out.println(stringClass.isAnnotationPresent(MyAnnotation.class)); //false
       
               if (c.isAnnotationPresent(MyAnnotation.class)){
                   //获取该注解类型
                  MyAnnotation myAnnotation = (MyAnnotation)c.getAnnotation(MyAnnotation.class);
                   System.out.println("类上面的注解对象" + myAnnotation); //类上面的注解对象@com.bjpowernode.java.annotation5.MyAnnotation()
                   //获取注解对象的属性怎么办？和调接口没区别
                   String value = myAnnotation.value();
                   System.out.println(value); //北京大兴区
               }
           }
       }
       
       ```

       ```java
       package com.bjpowernode.java.annotation6;
       
       import java.lang.annotation.ElementType;
       import java.lang.annotation.Retention;
       import java.lang.annotation.RetentionPolicy;
       import java.lang.annotation.Target;
       
       @Retention(RetentionPolicy.RUNTIME)
       @Target(ElementType.METHOD)
       public @interface MyAnnotation {
           String username();
           String password();
       }
       
       
       package com.bjpowernode.java.annotation6;
       
       import java.lang.reflect.Method;
       
       public class MyAnnotationTest {
       
           @MyAnnotation(username = "admin", password = "123")
           public void doSome(){
       
           }
       
           public static void main(String[] args) throws Exception{
               //获取MyAnnotationTest的doSome方法上的注解信息
               Class c =Class.forName("com.bjpowernode.java.annotation6.MyAnnotationTest");
               //获取doSome方法
               Method doSomeMethod = c.getDeclaredMethod("doSome");
               //判断该方法上是否存在这个注解
               if (doSomeMethod.isAnnotationPresent(MyAnnotation.class)){
                   MyAnnotation myAnnotation = doSomeMethod.getAnnotation(MyAnnotation.class);
                   System.out.println(myAnnotation.username()); //admin
                   System.out.println(myAnnotation.password()); //123
               }
           }
       }
       
       ```

       ```java
       需求:
       假设有这样一个注解，叫做：@Id
       这个注解只能出现在类上面，当这个类上有这个注解的时候，要求这个类中必须有一个int类型的id属性。如果没有这个属性就报异常，如果有这个属性就正常执行。
       ```

       ```java
       package com.bjpowernode.java.annotation7;
       
       import java.lang.annotation.ElementType;
       import java.lang.annotation.Retention;
       import java.lang.annotation.RetentionPolicy;
       import java.lang.annotation.Target;
       
       //表示这个注解只能出现在类上面
       @Target(ElementType.TYPE)
       //该注解可以被反射机制读取到
       @Retention(RetentionPolicy.RUNTIME)
       public @interface Id {
       }
       
       //这个注解@Id用来标注类，被标注的类中必须有一个int类型的id属性，没有就报异常。
       
       package com.bjpowernode.java.annotation7;
       @Id
       public class User {
           int id;
           String name;
           String password;
       }
       
       package com.bjpowernode.java.annotation7;
       /*
       自定义异常
        */
       public class HasNotIdPropertyException extends RuntimeException{
           public HasNotIdPropertyException() {
           }
       
           public HasNotIdPropertyException(String message) {
               super(message);
           }
       
           public HasNotIdPropertyException(String message, Throwable cause) {
               super(message, cause);
           }
       
           public HasNotIdPropertyException(Throwable cause) {
               super(cause);
           }
       
           public HasNotIdPropertyException(String message, Throwable cause, boolean enableSuppression, boolean writableStackTrace) {
               super(message, cause, enableSuppression, writableStackTrace);
           }
       }
       
       package com.bjpowernode.java.annotation7;
       
       import java.lang.reflect.Field;
       
       public class Test {
           public static void main(String[] args) throws Exception{
               //获取类
               Class userClass = Class.forName("com.bjpowernode.java.annotation7.User");
               //判断类上是否存在Id注解
               if (userClass.isAnnotationPresent(Id.class)){
                   //当一个类上面有@Id注解的时候，要求类中必须存在int类型的id属性
                   //如果没有int类型的id属性则报异常
       
                   //获取类的属性
                   Field[] fields = userClass.getDeclaredFields();
                   boolean isRight = false;
                   for(Field field : fields){
                       if("id".equals(field.getName()) && "int".equals(field.getType().getSimpleName())){
                           //表示这个类是合法的类。有@Id注解，则这个类中必须有int类型的id
                           isRight = true;
                           break;
                       }
                   }
       
                   //判断是否合法
                   if (!isRight){
                       throw new HasNotIdPropertyException("被@Id注解标注的类中必须要有一个int类型的id属性！");
                   }
               }
           }
       }
       
       ```

       总结：注解到底有什么用？注解在程序中等同于一种标记。如果这个元素上有这个注解怎么办，没有这个注解怎么办！

