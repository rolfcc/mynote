# Java笔记 进阶--常见类

## 目录 <!-- omit in toc -->

- [1. String/StringBuffer 和一些常见 I/O 方法](#1-stringstringbuffer-%e5%92%8c%e4%b8%80%e4%ba%9b%e5%b8%b8%e8%a7%81-io-%e6%96%b9%e6%b3%95)
  - [1-1 类 Scanner](#1-1-%e7%b1%bb-scanner)
    - [Scanner 所在包](#scanner-%e6%89%80%e5%9c%a8%e5%8c%85)
    - [Scanner 常见用法](#scanner-%e5%b8%b8%e8%a7%81%e7%94%a8%e6%b3%95)
    - [Scanner 常见构造方法](#scanner-%e5%b8%b8%e8%a7%81%e6%9e%84%e9%80%a0%e6%96%b9%e6%b3%95)
    - [Scanner 常见方法](#scanner-%e5%b8%b8%e8%a7%81%e6%96%b9%e6%b3%95)
    - [Scanner 注意事项](#scanner-%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9)
  - [1-2 类 String](#1-2-%e7%b1%bb-string)
    - [String 所在包](#string-%e6%89%80%e5%9c%a8%e5%8c%85)
    - [String 常见构造方法](#string-%e5%b8%b8%e8%a7%81%e6%9e%84%e9%80%a0%e6%96%b9%e6%b3%95)
    - [String 常用方法](#string-%e5%b8%b8%e7%94%a8%e6%96%b9%e6%b3%95)
      - [1. 字符串判断](#1-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%88%a4%e6%96%ad)
      - [2. 字符串获取功能](#2-%e5%ad%97%e7%ac%a6%e4%b8%b2%e8%8e%b7%e5%8f%96%e5%8a%9f%e8%83%bd)
      - [3. 字符串转换功能](#3-%e5%ad%97%e7%ac%a6%e4%b8%b2%e8%bd%ac%e6%8d%a2%e5%8a%9f%e8%83%bd)
      - [4. 字符串其他功能](#4-%e5%ad%97%e7%ac%a6%e4%b8%b2%e5%85%b6%e4%bb%96%e5%8a%9f%e8%83%bd)
        - [替换](#%e6%9b%bf%e6%8d%a2)
        - [去除两端空格](#%e5%8e%bb%e9%99%a4%e4%b8%a4%e7%ab%af%e7%a9%ba%e6%a0%bc)
        - [比较](#%e6%af%94%e8%be%83)
    - [String 注意事项](#string-%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9)
      - [1. 一旦赋值，不可更改](#1-%e4%b8%80%e6%97%a6%e8%b5%8b%e5%80%bc%e4%b8%8d%e5%8f%af%e6%9b%b4%e6%94%b9)
      - [2. String 两种初始化方法辨析](#2-string-%e4%b8%a4%e7%a7%8d%e5%88%9d%e5%a7%8b%e5%8c%96%e6%96%b9%e6%b3%95%e8%be%a8%e6%9e%90)
  - [1-3 StringBuffer 类](#1-3-stringbuffer-%e7%b1%bb)
    - [StringBuffer 所在包](#stringbuffer-%e6%89%80%e5%9c%a8%e5%8c%85)
    - [StringBuffer 常见构造方法](#stringbuffer-%e5%b8%b8%e8%a7%81%e6%9e%84%e9%80%a0%e6%96%b9%e6%b3%95)
    - [StringBuffer 常用方法](#stringbuffer-%e5%b8%b8%e7%94%a8%e6%96%b9%e6%b3%95)
      - [1. 字符串缓冲区添加](#1-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%bc%93%e5%86%b2%e5%8c%ba%e6%b7%bb%e5%8a%a0)
      - [2. 字符串缓冲区删除](#2-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%bc%93%e5%86%b2%e5%8c%ba%e5%88%a0%e9%99%a4)
      - [3. 字符串缓冲区替换](#3-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%bc%93%e5%86%b2%e5%8c%ba%e6%9b%bf%e6%8d%a2)
      - [4. 字符串缓冲区反转](#4-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%bc%93%e5%86%b2%e5%8c%ba%e5%8f%8d%e8%bd%ac)
      - [5. 字符串缓冲区截取](#5-%e5%ad%97%e7%ac%a6%e4%b8%b2%e7%bc%93%e5%86%b2%e5%8c%ba%e6%88%aa%e5%8f%96)
    - [StringBuffer 注意事项](#stringbuffer-%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9)
      - [1. 回文判断用链式编程优化](#1-%e5%9b%9e%e6%96%87%e5%88%a4%e6%96%ad%e7%94%a8%e9%93%be%e5%bc%8f%e7%bc%96%e7%a8%8b%e4%bc%98%e5%8c%96)
      - [2. StringBuilder 类](#2-stringbuilder-%e7%b1%bb)
- [2. 高级数组操作](#2-%e9%ab%98%e7%ba%a7%e6%95%b0%e7%bb%84%e6%93%8d%e4%bd%9c)
  - [2-1. 排序和查找](#2-1-%e6%8e%92%e5%ba%8f%e5%92%8c%e6%9f%a5%e6%89%be)
  - [2-2. Arrays 类概述及其常用方法](#2-2-arrays-%e7%b1%bb%e6%a6%82%e8%bf%b0%e5%8f%8a%e5%85%b6%e5%b8%b8%e7%94%a8%e6%96%b9%e6%b3%95)
    - [Arrays 所在包](#arrays-%e6%89%80%e5%9c%a8%e5%8c%85)
    - [Arrays 方法](#arrays-%e6%96%b9%e6%b3%95)
- [3. 包装类类型](#3-%e5%8c%85%e8%a3%85%e7%b1%bb%e7%b1%bb%e5%9e%8b)
  - [3-1. 面试题](#3-1-%e9%9d%a2%e8%af%95%e9%a2%98)
- [4. 正则表达式](#4-%e6%ad%a3%e5%88%99%e8%a1%a8%e8%be%be%e5%bc%8f)
  - [4-1. 正则表达式相关功能](#4-1-%e6%ad%a3%e5%88%99%e8%a1%a8%e8%be%be%e5%bc%8f%e7%9b%b8%e5%85%b3%e5%8a%9f%e8%83%bd)
  - [4-2. Pattern 和 Matcher 类](#4-2-pattern-%e5%92%8c-matcher-%e7%b1%bb)
- [5. Math 类](#5-math-%e7%b1%bb)
- [6. Random 类](#6-random-%e7%b1%bb)
- [7. System 类](#7-system-%e7%b1%bb)
- [8. BigInteger 类](#8-biginteger-%e7%b1%bb)
- [9. BigDecimal 类](#9-bigdecimal-%e7%b1%bb)
- [10. Date 类](#10-date-%e7%b1%bb)
- [11. Calendar 类](#11-calendar-%e7%b1%bb)

## 1. String/StringBuffer 和一些常见 I/O 方法  

### 1-1 类 Scanner

#### Scanner 所在包

`java.util.Scanner`  

#### Scanner 常见用法

```java
Scanner sc = new Scanner(System.in);
int i = sc.nextInt();
```

#### Scanner 常见构造方法

`Scanner(File source)`构造一个新的 Scanner，它生成的值是从指定文件扫描的。  
`Scanner(InputStream source)`构造一个新的 Scanner，它生成的值是从指定的输入流扫描的。  

#### Scanner 常见方法

`hasNextXxx`判断是否还有下一个输入项  
`nextXxx`获取下一个输入项  
其中 `Xxx` 代表 Int Double 等数据类型  

#### Scanner 注意事项

问：下面哪个会出问题呢？

```java
Scanner sc = new Scanner(System.in);
int i1 = sc.nextInt();
int i2 = sc.nextInt();
```

```java
Scanner sc = new Scanner(System.in);
int i = sc.nextInt();
String s = sc.nextLine();
```

```java
Scanner sc = new Scanner(System.in);
String s = sc.nextLine();
int i = sc.nextInt();
```

```java
Scanner sc = new Scanner(System.in);
String s1 = sc.nextLine();
String s2 = sc.nextLine();
```

答：第二个！先获取数值再获取字符串会出问题！输入数字后的换行符被系统当成一个空字符串了。

解决：  
一、重新建立一个 Scanner 对象  
二、先全部按字符串获取，然后要什么，转换什么。

### 1-2 类 String  

字符串是常量，字符串缓冲区是变量。

#### String 所在包

`java.lang.String`（默认包，无需导入）

#### String 常见构造方法

`String()`建立空字符串  
`String(byte[] bytes)`用字节数组转成字符串  
`String(byte[] bytes, int offset, int length)`同上，加偏移量和长度  
`String(char[] value)`用字节数组转成字符串  
`String(char[] value, int offset, int count)`同上，加偏移量和长度  
`String(String original)`字符串常量值转成字符串，同 cpp 复制构造函数  

#### String 常用方法

##### 1. 字符串判断

返回 boolean 类型  
`equals(Object anObject)`将此字符串与指定的对象比较。  
`equalsIgnoreCase(String anotherString)`将此 String 与另一个 String 比较，不考虑大小写。  
`contains(CharSequence s)`当且仅当此字符串包含指定的 char 值序列时，返回 true。  
`startsWith(String prefix)`测试此字符串是否以指定的前缀开始。  
`endsWith(String suffix)`测试此字符串是否以指定的后缀结束。  
`isEmpty()`判断空

##### 2. 字符串获取功能

`int length()`返回长度  
`char charAt(int index)`索引处字母  
`int indexOf(int ch)`返回指定字符在此字符串中第一次出现处的索引。  
`int indexOf(int ch, int fromIndex)`返回在此字符串中第一次出现指定字符处的索引，从指定的索引开始搜索。  
`int indexOf(String str)`返回指定子字符串在此字符串中第一次出现处的索引。  
`int indexOf(String str, int fromIndex)`返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始  
`String substring(int beginIndex)`返回一个新的字符串，它是此字符串的一个子字符串。  
`String substring(int beginIndex, int endIndex)`返回一个新字符串，它是此字符串的一个子字符串。  

##### 3. 字符串转换功能

`byte[] getBytes()`使用平台的默认字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中。  
`char[] toCharArray()`将此字符串转换为一个新的字符数组。  
`static String valueOf(int i)`返回 int 参数的字符串表示形式。  
`static String valueOf(char[] data)`返回 char 数组参数的字符串表示形式  
`String toLowerCase()`使用默认语言环境的规则将此 String 中的所有字符都转换为小写。  
`String toUpperCase()`使用默认语言环境的规则将此 String 中的所有字符都转换为大写。  
`String concat(String str)`将指定字符串连接到此字符串的结尾。  

##### 4. 字符串其他功能

###### 替换

`String replace(char oldChar, char newChar)`返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。  

###### 去除两端空格

`String trim()`返回字符串的副本，忽略前导空白和尾部空白。  

###### 比较

得到第一个不同字符的差（编码差值），都相同则返回长度差。  
`int compareTo(String anotherString)`按字典顺序比较两个字符串。  
`int compareToIgnoreCase(String str)`按字典顺序比较两个字符串，不考虑大小写。  

#### String 注意事项

##### 1. 一旦赋值，不可更改

字符串直接赋值是先到**字符串常量池**里面去找：**有**，则直接返回；**没有**，就创建并返回。  
一旦赋值，不可更改，是值不能更改，引用可以更改。  

**例：**

```java
String s = "aaa";
s += "bbb";
/* 结果 s 的值为 aaabbb */
```

> 例子中，s 位于栈中，内容为字符串地址（引用），字符串常量池位于方法区，存放所有字符串

##### 2. String 两种初始化方法辨析

`String s = "abcde"` 与 `String s = new String("abcde")`  

**示例程序：**  

```java
String s1 = "abcde";
String s2 = new String("abcde");

// 比较地址，结果为 false
System.out.println(s1 == s2);
// 比较内容，结果为 true
System.out.println(s1.equals(s2));
```

`String s = "abcde"` 中 `s` 存放于栈中，指向 **方法区.字符串常量池** 中的字符串 "abcde"  
`String s = new String("abcde")` 中 `s` 存放于栈中，指向 **堆** 中一个新建立的字符串，该字符串指向 **方法区.字符串常量池** 中的字符串 "abcde"  

### 1-3 StringBuffer 类

String 每次拼接都要在方法区新开辟一块空间，这样造成空间浪费。StringBuffer是为了解决该问题而设置。  
**线程安全**类，

#### StringBuffer 所在包

`java.lang.String`（默认包，无需导入）

#### StringBuffer 常见构造方法

`StringBuffer()`构造一个其中不带字符的字符串缓冲区，其初始容量为 16 个字符。  
`StringBuffer(int capacity)`构造一个不带字符，但具有指定初始容量的字符串缓冲区。  
`StringBuffer(String str)`构造一个字符串缓冲区，并将其内容初始化为指定的字符串内容。  

#### StringBuffer 常用方法

##### 1. 字符串缓冲区添加

`StringBuffer append(String str)`将需要的变量（不一定是String）追加到字符串中  
> 链式编程：当返回是自身时，可以再次调用该方法  
> 如：`sb.append("aaa").append(22).append(3.99)`得到字符串`"aaa223.99"`  
`StringBuffer insert(int offset, String str)`将字符串插入此字符序列中。同上。  

##### 2. 字符串缓冲区删除

`StringBuffer delete(int start, int end)`移除此序列的子字符串中的字符。  
`StringBuffer deleteCharAt(int index)`移除此序列指定位置的 char。  

##### 3. 字符串缓冲区替换

`StringBuffer replace(int start, int end, String str)`使用给定 String 中的字符替换此序列的子字符串中的字符。  

##### 4. 字符串缓冲区反转

`StringBuffer reverse()`将此字符序列用其反转形式取代。  

##### 5. 字符串缓冲区截取

`String substring(int start)`返回一个新的 String，它包含此字符序列当前所包含的字符子序列。  
`String substring(int start, int end)`返回一个新的 String，它包含此序列当前所包含的字符子序列。  

#### StringBuffer 注意事项

##### 1. 回文判断用链式编程优化

```java
public static boolean isSame(String str) {
    return new StringBuffer(str).reverse().toString().equal(str);
}
```

##### 2. StringBuilder 类

是 StringBuffer 的劣化版，没有多线程保护，但速度更快。操作可替换。  

## 2. 高级数组操作

### 2-1. 排序和查找

### 2-2. Arrays 类概述及其常用方法

#### Arrays 所在包

`java.util.Arrays`

#### Arrays 方法

`toString`方法，数组变字符串  
`sort`排序  
`binarySearch`二分法搜索  

## 3. 包装类类型

> 一般数据类型都有包装类类型，有方法可直接用

Byte, Short, Integer, Long, Float, Double, Character, Boolean.

### 3-1. 面试题

```java
Integer i1 = new Integer(127);
Integer i2 = new Integer(127);
Integer i3 = new Integer(128);
Integer i4 = new Integer(128);
Integer i5 = 128;
Integer i6 = 128;
Integer i7 = 127;
Integer i8 = 127;
```

1. 相同数字用方法 `equals` 都相等。  
2. 用 == 比较：  
   i1 != i2;  
   i3 != i4;  
   i5 != i6;  
   i7 == i8;  
   原因：Integer类对-128到127之间做了一个缓冲池，数据在该范围内，不创建新空间。  

## 4. 正则表达式

规则见Pattern类描述，在 `java.util.regex.Pattern` 包中。  

### 4-1. 正则表达式相关功能

- 判断功能：`matches(String regex)`  
- 分割功能：`String[] split(String regex)`按照给定表达式拆分字符串  

  ```java
  String age = "18-24";
  String regex = "-";
  String[] strArray = ages.split(regex);
  // 得到了两个字符串，18和24
  ```

- 替换功能：`replaceAll(String regex, String replacement)`  

  ```java
  String s = "adsfasgq34523452309asdfgwe";
  String regex = "\\d";
  String ss = "*";
  String result = s.replaceAll(regex, ss);
  ```

### 4-2. Pattern 和 Matcher 类

`java.util.regex.Pattern` 和 `java.util.regex.Pattern`  

- 获取功能：
  
  ```java
  Pattern p = Pattern.compile("a*b");
  Matcher m = p.matcher("aaaaab");
  boolean b = m.matches();
  ```

  ```java
  // 获取 s 中三个字母的字符串
  // 字符串
  String s = "sddf ew jjd ssl ei lsl asdf";
  // 规则（单词边界三个字母单词边界）
  String regex = "\\b\\w{3}\\b";

  // 规则编译成模式对象
  Pattern p = Pattern.compile(regex);
  // 通过模式对象获得匹配器对象
  Matcher m = p.matcher(s);

  //------找一次------
  // 调用匹配器对象的功能，find()方法
  boolean flag = m.find();
  // 获得所需的值
  String ss = m.group();

  //------找多次次------
  while(m.find()) {
    System.out.println(m.group());
  }

  // 注意：先find才能group
  ```

## 5. Math 类

在 `java.lang.Math` 内  

## 6. Random 类

在 `java.util.Random` 内  
使用种子生成随机数，同一种子生成同一组随机数  

## 7. System 类

`static void gc()` 运行垃圾回收器。  
`static long currentTimeMillis()`返回以毫秒为单位的当前时间。  
`static void exit(int status)`终止当前正在运行的 Java 虚拟机。  
`static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`从指定源数组中复制一个数组，复制从指定的位置开始，到目标数组的指定位置结束。  

## 8. BigInteger 类

位置 `java.math.BigInteger`  

`BigInteger add(BigInteger val)`返回其值为 (this + val) 的 BigInteger。  
`BigInteger subtract(BigInteger val)`返回其值为 (this - val) 的 BigInteger。  
`BigInteger multiply(BigInteger val)`返回其值为 (this * val) 的 BigInteger。  
`BigInteger divide(BigInteger val)`返回其值为 (this / val) 的 BigInteger。  
`BigInteger[] divideAndRemainder(BigInteger val)`返回包含 (this / val) 后跟 (this % val) 的两个 BigInteger 的数组。  

## 9. BigDecimal 类

位置：`java.math.BigDecimal`  

作用：防止丢失精度，替代 float 和 double 。  

构造方法：`BigDecimal(String val)` 用 String 构造是最精确的方法。

四则运算：加、减、乘、除同上。  

> `BigDecimal divide(BigDecimal divisor, int scale, int roundingMode)`返回一个 BigDecimal，其值为 (this / divisor)，其标度为指定标度。（几位小数，如何舍取）  

## 10. Date 类

位置：`java.util.Date`  

与字符串相互转化：  

1. DateFormat 类：父类  
   位置：`java.text.Format`
2. SimpleDateFormat 类：子类  
   位置：`java.text.SimpleDateFormat`  

他们的构造方法可以确定日期格式

子类找不到方法去父类找。

`String format(Date date)`将一个 Date 格式化为日期/时间字符串。  
`Date parse(String source)`从给定字符串的开始解析文本，以生成一个日期。  

## 11. Calendar 类

位置：`java.util.Calendar`  
