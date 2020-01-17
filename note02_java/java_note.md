# Java笔记

## 目录 <!-- omit in toc -->

- [1. Java基本语法](#1-java%e5%9f%ba%e6%9c%ac%e8%af%ad%e6%b3%95)
  - [1-1. 基本数据类型](#1-1-%e5%9f%ba%e6%9c%ac%e6%95%b0%e6%8d%ae%e7%b1%bb%e5%9e%8b)
  - [1-2. 数组和字符串](#1-2-%e6%95%b0%e7%bb%84%e5%92%8c%e5%ad%97%e7%ac%a6%e4%b8%b2)
  - [1-3. 运算符](#1-3-%e8%bf%90%e7%ae%97%e7%ac%a6)
  - [1-4. 语句](#1-4-%e8%af%ad%e5%8f%a5)
  - [1-5. 注释](#1-5-%e6%b3%a8%e9%87%8a)
- [2. 类和对象](#2-%e7%b1%bb%e5%92%8c%e5%af%b9%e8%b1%a1)
  - [2-1. 类](#2-1-%e7%b1%bb)
  - [2-2. 对象](#2-2-%e5%af%b9%e8%b1%a1)
- [3. 包、继承和访问权限](#3-%e5%8c%85%e7%bb%a7%e6%89%bf%e5%92%8c%e8%ae%bf%e9%97%ae%e6%9d%83%e9%99%90)
  - [3-1. 包](#3-1-%e5%8c%85)
  - [3-2. 继承](#3-2-%e7%bb%a7%e6%89%bf)
  - [3-3. 访问权限](#3-3-%e8%ae%bf%e9%97%ae%e6%9d%83%e9%99%90)
- [4. 接口和一些关键字](#4-%e6%8e%a5%e5%8f%a3%e5%92%8c%e4%b8%80%e4%ba%9b%e5%85%b3%e9%94%ae%e5%ad%97)
  - [4-1. super 关键字](#4-1-super-%e5%85%b3%e9%94%ae%e5%ad%97)
  - [4-2. final 关键字](#4-2-final-%e5%85%b3%e9%94%ae%e5%ad%97)
  - [4-3. static 关键字](#4-3-static-%e5%85%b3%e9%94%ae%e5%ad%97)
  - [4-4. 接口](#4-4-%e6%8e%a5%e5%8f%a3)
  - [4-5. 异常处理](#4-5-%e5%bc%82%e5%b8%b8%e5%a4%84%e7%90%86)
- [5. Java的输入和输出类](#5-java%e7%9a%84%e8%be%93%e5%85%a5%e5%92%8c%e8%be%93%e5%87%ba%e7%b1%bb)
- [6. 多线程机制](#6-%e5%a4%9a%e7%ba%bf%e7%a8%8b%e6%9c%ba%e5%88%b6)
  - [6-1. 成员变量](#6-1-%e6%88%90%e5%91%98%e5%8f%98%e9%87%8f)
  - [6-2. 构造函数](#6-2-%e6%9e%84%e9%80%a0%e5%87%bd%e6%95%b0)
  - [6-3. 常用的方法](#6-3-%e5%b8%b8%e7%94%a8%e7%9a%84%e6%96%b9%e6%b3%95)
  - [6-4. 多线程实现](#6-4-%e5%a4%9a%e7%ba%bf%e7%a8%8b%e5%ae%9e%e7%8e%b0)
  - [6-5. 线程同步](#6-5-%e7%ba%bf%e7%a8%8b%e5%90%8c%e6%ad%a5)
- [7. Java网络基础](#7-java%e7%bd%91%e7%bb%9c%e5%9f%ba%e7%a1%80)
  - [7-1. URL类](#7-1-url%e7%b1%bb)
  - [7-2. URLConnection类](#7-2-urlconnection%e7%b1%bb)
  - [7-3. Socket类](#7-3-socket%e7%b1%bb)
  - [7-4. ServerSocket类](#7-4-serversocket%e7%b1%bb)

## 1. Java基本语法

### 1-1. 基本数据类型

|  类型  |      Java表示       |
| :----: | :-----------------: |
| 逻辑型 |       boolean       |
| 整数型 | byte/short/int/long |
| 浮点型 |    float/double     |
| 字符型 |        char         |

> 注1：整数型大小依次是1 2 4 8 字节  
> 注2：常数整数默认int，小数默认double，float要在数字后加f或F。如：1.244f  
> 注3：强制类型转换 `(数据类型) 变量名`

### 1-2. 数组和字符串

- 数组声明  
  声明1：`数组元素类型 数组名[]`  
  声明2：`数组元素类型[] 数组名`  
  二维数组同理  
- 数组创建  
  `数组名 = new 数组元素类型[数组元素个数]`  
- 字符串  
  `String = "一串字符"`

> 注：数组声明和创建可以写在一行  
> `数组元素类型 数组名[] = new 数组元素类型[数组元素个数]`  

### 1-3. 运算符  

略。。。  

### 1-4. 语句  

- if语句  
- switch语句  
- for语句  
- while/do-while语句  
- break/continue语句  

### 1-5. 注释  

略。。。

## 2. 类和对象

### 2-1. 类

```java
class ClassName {
    // 属性/成员变量
    /*正*/ 数据类型/类名 属性名1;
    /*正*/ 数据类型/类名 属性名2 = 值;
    /*误*/ 属性名1 = 值;

    // 构造方法 无返回类型/可重载
    ClassName() {
        方法体，初始化时执行
    }

    // 方法
    返回类型 方法名1() {
        方法体
    }

    // 方法重载，有不同的参数
    返回类型 方法名1(数据类型 参数名 = 默认值) {
        // 通过this调用成员变量，this表示这个类
        this.成员变量；
        局部变量

        方法体
    }
}
```

> 命名惯例
>
> 1. 类：每个单词首字母大写
> 2. 变量名/方法名：第一个单词首字母小写，其他大写
> 3. 常量名：所有字母大写，单词用下划线分开

### 2-2. 对象

声明  
`类名 对象名;`  

分配内存  
`对象名 = new 类的构造方法;`  

使用  
`对象名.属性名;`  
`对象名.方法名(参数);`

实例变量和类变量（静态变量）

```java
class 类名 {
    // 实例变量和类变量
    数据类型 实例变量名;
    static 数据类型 类变量名;

    // 实例方法和类方法
    // 同上
}

class 类名 {
    static {
        // 静态块，效果同上
        数据类型 类变量名;
    }
}
```

使用

```java
类名.类变量;
对象名.实例变量;
```  

> 类方法只能操作类变量，实例方法则不限

## 3. 包、继承和访问权限

### 3-1. 包  

声明所属包：`package` 语句，放在第一句。  
导入其他包：`import` 语句  

### 3-2. 继承  

`class 子类名 extends 父类名 {}`  
> 一个类只能继承一个父类！

### 3-3. 访问权限

|  作用域   | 当前类 | 同package | 子孙类 | 其他package |
| :-------: | :----: | :-------: | :----: | :---------: |
|  public   |   1    |     1     |   1    |      1      |
| protected |   1    |     1     |   1    |      0      |
|   默认    |   1    |     1     |   0    |      0      |
|  private  |   1    |     0     |   0    |      0      |

## 4. 接口和一些关键字  

### 4-1. `super` 关键字  

`super` 在子类中代表父类，类比 `this` 代表自己这个类  

- 使用父类中的属性和方法（解决父类和子类内容重名）

  ```java
  super.父类属性
  super.父类方法
  ```

- 使用父类的构造方法

  ```java
  super();
  // super 完全当类名用
  ```

### 4-2. `final` 关键字  

- 修饰类则该类无法继承
- 修饰属性则属性值无法更改（注意常量名一般大写）
- 修饰方法则方法不能被**重写**
  > 重载：方法名相同，参数不同  
  > 重写：子类与父类中方法名、参数类型数量完全相同，但内容不同  
- 修饰局部变量的引用类型时表示引用类型的地址值不能变，其数据可变

### 4-3. `static` 关键字

- 修饰类变量（静态变量）
- 修饰类方法（静态方法，调用本类内方法时是必须的）
- 修饰静态代码块  
  静态代码块仅在第一次new时执行，非静态代码块在每次new时执行

> static 的含义：  
>
> 1. 静态存储方式（所有同类的对象共享）  
> 2. 作用域仅限于本文件  
> 3. **不需要实例化就可以使用**  
>    想直接调用的属性方法一定要加上 static  
>
> 注意：静态方法无法引用非静态变量

### 4-4. 接口

- 接口定义

  ```java
  interface 接口名{
      // 属性方法默认public
      属性;
      方法;
  }
  ```

- 接口实现

  ```java
  class 类名 implements 接口名{
      // 接口中所有属性与方法
      public 接口属性名;
      public 接口方法名;
  }
  ```

> 接口要注意以下三点：  
>
> 1. 一个类可实现**多个接口**，但只能有**一个父类**
> 2. 接口可以**声明**对象，但不可**实例化**对象。
>    这个很好理解，接口规定了类的格式，但没有具体内容,无法分配内存。只有类可以实例化对象！！！
> 3. Java接口可以类比C/C++中提前声明函数，接口可以与类有不同名字，也可以有不同的实现，更加灵活。

### 4-5. 异常处理

异常处理流程：

```java
try {
    // 可能出现异常的语句
}
catch(异常类 对象名) {
    // 处理异常的语句
}
finally {
    // 终止块：异常处理后执行的语句
}
```

> 异常种类有很多，但他们都是 Exception 类的子类，故catch可写作如下形式：  
> `catch(Exception e) {}`

抛出异常 `throw`  

```java
try {
    throw new 异常类("一段描述");
}
```

抛出异常声明 `throws`

```java
class 类名 {
    返回类型 方法名() throws 异常类1, 异常类2 {
        // 告诉别人本方法可能抛出一个异常，要求处理
        方法块
    }
}
```

## 5. Java的输入和输出类  

`java.io` 包括了所有输入、输出相关的类，此处仅介绍一部分，更多内容参考<a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/package-summary.html" target="_blank">官方文档</a>。

- 面向字节的流类 InputStream/OutputStream  
  对文件的字节流操作，与环境无关，是最常见的IO操作
  - FileInputStream/FileOutputStream 文件读写
  - [DataInputStream/DataOutputStream 数据流读写](./c09_javaio/DataIOStm.java)
  - [BufferedInputStream/BufferedOutputStream 通过缓冲区读写](./c09_javaio/BufferedIOStm.java)
- 面向字符型的流类 Reader/Writer  
  应该是对文本文件的操作吧，毕竟是面向字符  
  - [BufferedReader/BufferedWriter](./c09_javaio/BufferedRW.java)  
    在面对字节操作时，生成的文件时二进制文件。但面对字符操作时，得到的时文本文件。
  - PrintWriter  
    包含 `print` 和 `println`  

## 6. 多线程机制  

Java通过 `Thread` 类支持多线程，通过 `import java.long.Thread` 导入。

### 6-1. 成员变量

规定优先级为1~10，通常为5。

### 6-2. 构造函数

`public Thread(ThreadGroup group, Runnable target, String name)`  
`group` 配置一个属于group线程组的线程  
`target` 调用可执行对象target中的run()方法  
`name` 设置线程名字  
三个参数可任意搭配，也可不填。

### 6-3. 常用的方法  

`public static int activeCount()` 返回线程群中线程数量  
`public static native Thread currentThread()` 返回活动的线程  
`public String getName()` 返回线程名称  
`public int getPriority()` 返回优先级  
`public void setPriotity()` 设置优先级  
`public ThreadGroup getThreadGroup()` 返回当前线程所属线程群  
`public void interrupt()`  中断当前线程  
`public static Boolean interrupted()` 返回中断状态并清除中断状态  
`public boolean isInterrupted()` 返回中断状态，但不改变  
`public Boolean isAlive()` 返回当前线程存活情况  
`public final boolean isDaemon()` 是否为守护线程  
`public void setDaemon()` 设置为守护线程  
`public void setName(String name)` 设置名字  
`public void resume()` 恢复运行状态  
`public void run()` 线程启动  
`public void destroy()` 线程结束  
`public static void sleep(long millis)` 线程睡眠  
`public void start()` 线程运行  
`public void stop()` 线程终止  
`public void suspend()` 线程挂起  
`public static void yield()` 退出线程执行，执行权交给其他线程  

### 6-4. 多线程实现

- 继承 Thread 类

  ```java
  class 类名 extend Thread {
      // 构造函数调用父类
      类名(String name) {
          super(name);
      }

      public void run() {
          // 子类中覆盖 run() 方法
          // 线程执行内容
      }

  }
  ```

- 实现 Runnable 接口

  ```java
  class 类名 implements Runnable {
      public void run() {
          // 执行操作
      }
  }

  // 调用（这个类只是线程任务记录的类，而非创建线程的类。
  类名 r = new 类名();
  Thread mthread = new Thread(r);
  mthread.run();
  ```

### 6-5. 线程同步

关键字 `synchronized` 修饰的方法同时只能被一个线程调用

```java
public synchronized void 类名() {}
```

## 7. Java网络基础

网络相关的类在 `java.net` 下

### 7-1. URL类

- 常用构造函数  
  `URL(String URL)` 建立一个URL类对象  
  `URL(String protocol, String host, int port, String file)` 通过给定的参数(协议、主机名、端口号、文件名)创建URL  
  `URL(URL context, String url)` 使用基地址和相对URL创建  
- 常用方法

### 7-2. URLConnection类

URL类 `openConnection()` 方法返回一个URLConnection类  

### 7-3. Socket类

客户端

### 7-4. ServerSocket类

服务器端
