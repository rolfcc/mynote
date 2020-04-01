# Java笔记 进阶--其他

## 目录 <!-- omit in toc -->

- [1. 多线程](#1-%e5%a4%9a%e7%ba%bf%e7%a8%8b)
  - [1-1 可成为线程的类](#1-1-%e5%8f%af%e6%88%90%e4%b8%ba%e7%ba%bf%e7%a8%8b%e7%9a%84%e7%b1%bb)
  - [1-2 构造方法](#1-2-%e6%9e%84%e9%80%a0%e6%96%b9%e6%b3%95)
  - [1-3 方法](#1-3-%e6%96%b9%e6%b3%95)
  - [1-4. 线程同步](#1-4-%e7%ba%bf%e7%a8%8b%e5%90%8c%e6%ad%a5)
- [2. 面向对象设计原则](#2-%e9%9d%a2%e5%90%91%e5%af%b9%e8%b1%a1%e8%ae%be%e8%ae%a1%e5%8e%9f%e5%88%99)
- [3. GUI](#3-gui)
- [4. 网络编程](#4-%e7%bd%91%e7%bb%9c%e7%bc%96%e7%a8%8b)
  - [4-1 InetAddress](#4-1-inetaddress)
  - [4-2 Socket 类](#4-2-socket-%e7%b1%bb)
  - [4-3 ServerSocket 类](#4-3-serversocket-%e7%b1%bb)
  - [4-4 UDP传输](#4-4-udp%e4%bc%a0%e8%be%93)
- [5. 反射](#5-%e5%8f%8d%e5%b0%84)
  - [5-1 使用类](#5-1-%e4%bd%bf%e7%94%a8%e7%b1%bb)
    - [建立一个 Class](#%e5%bb%ba%e7%ab%8b%e4%b8%80%e4%b8%aa-class)
    - [通过 Class 类获取构造函数](#%e9%80%9a%e8%bf%87-class-%e7%b1%bb%e8%8e%b7%e5%8f%96%e6%9e%84%e9%80%a0%e5%87%bd%e6%95%b0)
    - [调用](#%e8%b0%83%e7%94%a8)
  - [5-2 使用成员变量](#5-2-%e4%bd%bf%e7%94%a8%e6%88%90%e5%91%98%e5%8f%98%e9%87%8f)
  - [5-3 使用成员方法](#5-3-%e4%bd%bf%e7%94%a8%e6%88%90%e5%91%98%e6%96%b9%e6%b3%95)
  - [5-4 动态代理](#5-4-%e5%8a%a8%e6%80%81%e4%bb%a3%e7%90%86)

## 1. 多线程

**类：** `Thread`  
**包：** `java.long.Thread`  

### 1-1 可成为线程的类

1. 声明为 Thread 的子类，该子类应重写 Thread 类的 run 方法。  
2. 声明实现 Runnable 接口的类，该类然后实现 run 方法。  

```java
// 子类实现
class PrimeThread extends Thread {
   PrimeThread() {}
   public void run() {}
}

// 线程启动
PrimeThread p = new PrimeThread();
p.start();
```

```java
// 接口实现
class PrimeRun implements Runnable {
    PrimeRun(long minPrime) {}
    public void run() {}
}
// 线程启动
PrimeRun p = new PrimeRun(143);
new Thread(p).start();
```

### 1-2 构造方法

`Thread(ThreadGroup group, Runnable target, String name, long stackSize)`  
可选参数： group 线程组；target 接口实现的类；name 线程名称；stackSize 栈的大小。  

### 1-3 方法

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

### 1-4. 线程同步

关键字 `synchronized` 修饰的方法同时只能被一个线程调用

```java
public synchronized void 类名() {}
```  

## 2. 面向对象设计原则

1. 单一职责：高内聚低耦合。
2. 开闭原则：对扩展开放，对修改关闭；功能更改通过增加代码实现，而非修改可用代码。
3. 里氏替换原则：任何父类均可由其子类代替
4. 依赖注入原则：依赖抽象，而非具体实现，针对抽象类和接口编程
5. 接口分离：一个接口提供一种功能
6. 迪米特原则：一个对象应对其他对象尽可能少的了解

## 3. GUI

## 4. 网络编程

**网络编程三要素：**  

1. IP 地址
2. 端口
3. 协议

### 4-1 InetAddress

**包：** `java.net.InetAddress`

IP地址类，两个子类：Inet4Address, Inet6Address  
分别表示 IPv4 和 IPv6  

```java
InetAddress address1 = InetAddress.getByName("RolfCui");
InetAddress address2 = InetAddress.getByName("192.168.0.101");

System.out.println(address1.toString());
System.out.println(address2.getHostName());
System.out.println(address2.getHostAddress());
```

### 4-2 Socket 类

客户端套接字，封装了IP和端口。

**构造方法：**  
`Socket(String host, int port)`创建一个流套接字并将其连接到指定主机上的指定端口号。  
`Socket(InetAddress address, int port)`创建一个流套接字并将其连接到指定 IP 地址的指定端口号。  

**方法：**  
`OutputStream getOutputStream()`返回此套接字的输出流。  
`InputStream getInputStream()`返回此套接字的输入流。  

### 4-3 ServerSocket 类

服务器端

**构造方法：**  
`ServerSocket(int port)`创建绑定到特定端口的服务器套接字。

**方法：**  
`Socket accept()`侦听并接受到此套接字的连接。 

### 4-4 UDP传输

**DatagramSocket类** 可用于创建UDP传输的发送端和接收端  

**构造方法：**  
`DatagramSocket()`构造数据报套接字并将其绑定到本地主机上任何可用的端口。  
`DatagramSocket(int port)`创建数据报套接字并将其绑定到本地主机上的指定端口。  

**方法：**  
`void receive(DatagramPacket p)`从此套接字接收数据报包。  
`void send(DatagramPacket p)`从此套接字发送数据报包。  

**DatagramPacket类** 封装好的数据包

`DatagramPacket(byte[] buf, int length)`构造 DatagramPacket，用来接收长度为 length 的数据包。  
`DatagramPacket(byte[] buf, int length, InetAddress address, int port)`构造数据报包，用来将长度为 length 的包发送到指定主机上的指定端口号。  

> 带有地址和端口的是**发送用**数据包，不带地址和端口的是**接收用**数据包。

```java
// 发送端
package send_demo;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class SendDemo {

    public static void main(String[] args) throws IOException {
        // 创建发送端 socket 对象
        DatagramSocket ds = new DatagramSocket();

        InetAddress address = InetAddress.getByName("RolfCui");
        String str = "HelloWorld";

        byte[] buf = str.getBytes("UTF-8");
        int length = str.length();
        int port = 8888;
        // 创建数据并打包
        // DatagramPacket(byte[] buf, int length, InetAddress address, int port)
        // 构造数据报包，用来将长度为 length 的包发送到指定主机上的指定端口号。
        DatagramPacket dp = new DatagramPacket(buf, length, address, port);

        // 调用 Socket 对象发送方法数据包
        // void send(DatagramPacket p) 从此套接字发送数据报包。
        ds.send(dp);

        // 关闭
        ds.close();
    }

}
```

```java
// 接收端
package receive_demo;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class ReceiveDemo {

    public static void main(String[] args) throws IOException {
        // 创建接收端端 socket 对象
        DatagramSocket ds = new DatagramSocket(8888);

        byte[] buf = new byte[1024];
        DatagramPacket dp = new DatagramPacket(buf, 1024);

        // 接收数据
        ds.receive(dp);

        // 获取IP
        InetAddress address = dp.getAddress();
        System.out.print(address.toString() + ": ");

        // 解析数据包，显示在屏幕
        byte[] bt = dp.getData();
        int len = dp.getLength();
        String s = new String(bt, 0, len);
        System.out.println(s);

        // 关闭接口
        ds.close();
    }

}
```

## 5. 反射

Java在运行状态中，对任意一个类，都能知道该类所有属性和方法；对任意对象，都能调用它任意方法和属性。这种动态调用的方法称为反射机制。  

反射，就是指通过 class 文件对象，去使用该文件中的成员变量，构造方法，成员方法。  

要想这样使用，必须得到 class 文件对象，其实也就是得到 Class 类的对象。  

Class 类：

- 成员变量：Field 类
- 构造方法：Constructor 类
- 成员方法：Method 类
- 以上均在 java.lang.reflect 下

Class 就是对原类的封装。一个类只有一个 Class，与多少个对象无关。  

```java
// 获取方式一：Object 的 getClass 方式

Persion p1 = new Persion();
Class c1 = p1.getClass();

Persion p2 = new Persion();
Class c2 = p1.getClass();

System.out.println(p1 == p2); // false
System.out.println(c1 == c2); // true

// 获取方式二：类的静态属性 class

Class c3 = Persion.class;
Class c4 = int.class;
Class c5 = Integer.class;

System.out.println(c4 == c5); //false !!!

// 获取方式三：Class 中静态方法
// 抛出 ClassNotFoundException
// 一般写全路径

Class c6 = Class.forName("Persion");
```

开发一般使用第三种。因为可以使用配置文件配置。  

### 5-1 使用类

#### 建立一个 Class

其引用类放在配置文件中，我们不知道是哪一个类。  

```java
Class c = Class.forName("reflect_demo2.Student");
```

#### 通过 Class 类获取构造函数

`Constructor<?>[] getConstructors()`返回一个包含某些 Constructor 对象的数组，这些对象反映此 Class 对象所表示的类的所有公共构造方法。  
`Constructor<?>[] getDeclaredConstructors()`返回 Constructor 对象的一个数组，这些对象反映此 Class 对象表示的类声明的所有构造方法。  

`Constructor<T> getDeclaredConstructor(Class<?>... parameterTypes)`返回一个 Constructor 对象，该对象反映此 Class 对象所表示的类或接口的指定构造方法。  
`Constructor<T> getConstructor(Class<?>... parameterTypes)`返回一个 Constructor 对象，它反映此 Class 对象所表示的类的指定公共构造方法。  

```java
// 无参
Constructor con = c.getConstructor();
// 带参
Constructor con = c.getConstructor(String.class, int.class);
```

如果想访问 private 类，调用其父类方法中的 setAccessible() 方法。

#### 调用

**Constructor&lt;T&gt;:**  
`T newInstance(Object... initargs)`使用此 Constructor 对象表示的构造方法来创建该构造方法的声明类的新实例，并用指定的初始化参数初始化该实例。  

```java
// 无参
Object obj = con.newInstance();
// 带参
Object obj = con.newInstance("sora", 14);
```

> 反射类看不到运行的类！

### 5-2 使用成员变量

使用 Class 的方法来获得 Field  
`Field getField(String name)`返回一个 Field 对象，它反映此 Class 对象所表示的类或接口的指定公共成员字段。  
`Field[] getFields()`返回一个包含某些 Field 对象的数组，这些对象反映此 Class 对象所表示的类或接口的所有可访问公共字段。  

### 5-3 使用成员方法

使用 Class 的方法来获得 Method  
**同上**

### 5-4 动态代理

包 java.lang.reflect  
类 Proxy  
接口 InvocationHandler  

通过这个类和接口可生成动态代理对象，JDK提供的代理只能针对接口做代理，我们有更强大的代理，cglib。

```java
// 主程序
package reflect_proxy;

import java.lang.reflect.Proxy;

public class ProxyDemo {
    public static void main(String[] args) {
        UserDao ud = new UserDaoImpl();
        ud.add();
        ud.delete();
        ud.update();
        ud.find();
        System.out.println("-----------------");

        // 想对谁做代理就传谁
        MyInvocationHandler mi = new MyInvocationHandler(ud);

        // 使用 Proxy 的静态方法
        UserDao proxyObj = (UserDao) Proxy.newProxyInstance(ud.getClass().getClassLoader(), 
                ud.getClass().getInterfaces(), mi);

        proxyObj.add();
        proxyObj.delete();
        proxyObj.update();
        proxyObj.find();
    }
}
```

```java
// 自制 InvocationHandler

package reflect_proxy;

import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;

public class MyInvocationHandler implements InvocationHandler {
    // 1. 返回一个动态代理对象，所以我们需要一个对象
    private Object target; // 目标对象

    // 2. 要有一个带参构造，获得对象
    public MyInvocationHandler(Object target) {
        this.target = target;
    }

    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {

        System.out.println("权限校验");

        Object result = method.invoke(target, args);

        System.out.println("日志记录");

        return result; // 返回的是代理对象
    }

}
```