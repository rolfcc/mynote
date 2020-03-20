# Java笔记 进阶--集合框架

## 目录 <!-- omit in toc -->

- [1. 对象数组](#1-%e5%af%b9%e8%b1%a1%e6%95%b0%e7%bb%84)
- [2. 集合及其迭代器](#2-%e9%9b%86%e5%90%88%e5%8f%8a%e5%85%b6%e8%bf%ad%e4%bb%a3%e5%99%a8)
  - [2-1. Collection](#2-1-collection)
  - [2-2. List](#2-2-list)
  - [2-3. List 的子类](#2-3-list-%e7%9a%84%e5%ad%90%e7%b1%bb)
    - [ArrayList](#arraylist)
    - [Vector](#vector)
    - [LinkedList](#linkedlist)
    - [List 子类练习](#list-%e5%ad%90%e7%b1%bb%e7%bb%83%e4%b9%a0)
      - [ArrayList 去除重复](#arraylist-%e5%8e%bb%e9%99%a4%e9%87%8d%e5%a4%8d)
      - [ArrayList 模拟栈](#arraylist-%e6%a8%a1%e6%8b%9f%e6%a0%88)
  - [2-4. 泛型](#2-4-%e6%b3%9b%e5%9e%8b)
    - [2-4-1. 泛型类](#2-4-1-%e6%b3%9b%e5%9e%8b%e7%b1%bb)
    - [2-4-2. 泛型方法](#2-4-2-%e6%b3%9b%e5%9e%8b%e6%96%b9%e6%b3%95)
    - [2-4-3. 泛型接口](#2-4-3-%e6%b3%9b%e5%9e%8b%e6%8e%a5%e5%8f%a3)
    - [2-4-4. 泛型高级（通配符）](#2-4-4-%e6%b3%9b%e5%9e%8b%e9%ab%98%e7%ba%a7%e9%80%9a%e9%85%8d%e7%ac%a6)
      - [泛型通配符<?>](#%e6%b3%9b%e5%9e%8b%e9%80%9a%e9%85%8d%e7%ac%a6)
      - [? extends E](#extends-e)
      - [? super E](#super-e)
  - [2-5. Set](#2-5-set)
  - [2-6. Set 的子类](#2-6-set-%e7%9a%84%e5%ad%90%e7%b1%bb)
    - [2-6-1. HashSet](#2-6-1-hashset)
    - [2-6-2. TreeSet](#2-6-2-treeset)
- [3. *JDK5 新特性](#3-jdk5-%e6%96%b0%e7%89%b9%e6%80%a7)
  - [3-1. 自动拆装箱](#3-1-%e8%87%aa%e5%8a%a8%e6%8b%86%e8%a3%85%e7%ae%b1)
  - [3-2. 泛型](#3-2-%e6%b3%9b%e5%9e%8b)
  - [3-3. 增强 for](#3-3-%e5%a2%9e%e5%bc%ba-for)
  - [3-4. 静态导入](#3-4-%e9%9d%99%e6%80%81%e5%af%bc%e5%85%a5)
  - [3-5. 可变参数](#3-5-%e5%8f%af%e5%8f%98%e5%8f%82%e6%95%b0)
  - [3-6. 枚举](#3-6-%e6%9e%9a%e4%b8%be)

## 1. 对象数组

```java
Student[] student = new Student[5];
Student s1 = new Student();
student[0] = s1;
```

解析：

1. `Student[] student` 和 `Student s1` 是在栈内生成一个引用（指针）
2. `new` 表示在堆内开辟一个空间
   1. `new Student[5]` 表示生成 5 个引用
   2. `new Student()` 正式开辟一个存放类的空间

## 2. 集合及其迭代器

与数组区别：  

1. 集合长度可变
2. 集合可存放不同类型元素
3. 数组可存放基本数据类型，也可存放引用数据类型。
   集合只能存放引用数据类型。

针对不同需求，Java 提供了不同集合类（数据结构不同）。  

集合的继承关系：  

```Table
Collection -|-> List -|-> ArrayList
            |         |-> Vector
            |         |-> LinkedList
            |-> Set -|-> HashSet
                     |-> TreeSet
```

### 2-1. Collection

Collection 是一个接口  

**添加：**  
`boolean add(Object obj)`添加元素  
`boolean addAll(Collection c)`添加一个集合的元素  
**删除：**  
`void clear()`移除此 collection 中的所有元素  
`boolean remove(Object o)`从此 collection 中移除指定元素的单个实例，如果存在的话（可选操作）。  
`boolean removeAll(Collection c)`移除此 collection 中那些也包含在指定 collection 中的所有元素（可选操作）。  
**判断：**  
`boolean contains(Object o)`如果此 collection 包含指定的元素，则返回 true。  
`boolean containsAll(Collection c)`如果此 collection 包含指定 collection 中的所有元素，则返回 true。  
`boolean isEmpty()`如果此 collection 不包含元素，则返回 true。  
**获取：**  
`Iterator<E> iterator()`返回在此 collection 的元素上进行迭代的迭代器。  
**交集：**  
`boolean retainAll(Collection<?> c)`仅保留此 collection 中那些也包含在指定 collection 的元素（可选操作）。  
**长度：**  
`int size()`返回此 collection 中的元素数。  

**测试：**  
`Collection c = new ArrayList();` ArrayList类是Collection接口的子接口实现类。

**遍历：**  

1. 数组遍历  
   使用`toArray`方法遍历
2. 迭代器遍历

    ```java
    // 初始化
    Collection c = new ArrayList();
    c.add("s1");c.add("s2");c.add("s3");

    Interator it = c.interator();
    // 多态。此处Interator是一个接口。

    while(it.hasNext) {
        String s = (String)it.next();
        System.out.println(s);
    }
    ```

> 迭代器有两个方法，`Object next()` 和 `boolean hasNext()`  
  `Iterator`也是个接口  

### 2-2. List

有序的 Collection 也叫序列。特点：1.有序；2.可重复；3.可根据序号访问。  

**List特有功能：**  
`void add(int index, E element)`在列表的指定位置插入指定元素（可选操作）。(addAll同理)  
`E get(int index)`返回列表中指定位置的元素。  
`ListIterator<E> listIterator()`返回此列表元素的列表迭代器（按适当顺序）。(有序号，可指定位置)  
`E remove(int index)`移除列表中指定位置的元素（可选操作）。  
`E set(int index, E element)`用指定元素替换列表中指定位置的元素（可选操作）。  

**列表迭代器介绍**  
有了序号功能和向前查找功能。  
`boolean hasPrevious()`如果以逆向遍历列表，列表迭代器有多个元素，则返回 true。  
`int nextIndex()`返回对 next 的后续调用所返回元素的索引。  
`E previous()`返回列表中的前一个元素。  
`int previousIndex()`返回对 previous 的后续调用所返回元素的索引。  

**列表迭代器有添加功能**  
`void add(E e)`将指定的元素插入列表（可选操作）。插入迭代器所在位置。  

> 迭代器依赖于集合存在，使用迭代器时不要改变原集合。否则会发生`ConcurrentModificationException`异常。  
> **集合遍历**元素则**集合修改**元素，**迭代器遍历**元素则**迭代器修改**元素。  

### 2-3. List 的子类

#### ArrayList

List 接口的大小可变数组的实现。  

#### Vector

List 接口的顺序表实现，同 ArrayList 但**支持多线程**  
是 Stack 类的父类。  

**Vector 特有功能（旧方法）**  
`void addElement(E obj)`将指定的组件添加到此向量的末尾，将其大小增加 1。  
`E elementAt(int index)`返回指定索引处的组件。  
`Enumeration<E> elements()`返回此向量的组件的枚举。  

> Enumeration（枚举）与迭代器基本相同

**JDK升级：** 更安全，高效，简单。

#### LinkedList

List 接口的链接列表实现。  

**LinkedList 特有功能**  
`void addFirst(E e)`将指定元素插入此列表的开头。  
`void addLast(E e)`将指定元素添加到此列表的结尾。  
`E getFirst()`返回此列表的第一个元素。  
`E getLast()`返回此列表的最后一个元素。  
`E removeFirst()`移除并返回此列表的第一个元素。  
`E removeLast()`移除并返回此列表的最后一个元素。  

#### List 子类练习

##### ArrayList 去除重复

思路一：新建集合，遍历旧集合。每次插入前查重。  
思路二：每次与后面所有元素比。有则删除。删除时总长度减一，删除的位置由后面的元素递补，要注意。

##### ArrayList 模拟栈

### 2-4. 泛型

早期使用 `Object` 代表任意类型。向上转型没问题，但向下转型会报错。故 Java 在1.5后引入泛型。

#### 2-4-1. 泛型类  

1. 把泛型定义在类上。  
2. public class 类名<泛型类型1,...>  
3. 泛型类型必须是引用类型（指针）。  

```java
public class ObjectTool<T> {
// 一个泛型类

    private T obj;

    public T getObj() {
        return obj;
    }

    public void setObj(T obj) {
        this.obj = obj;
    }

}
```

```java
public class ObjectToolDemo {
// 泛型类应用

    public static void main(String[] args) {

        ObjectTool<String> ot = new ObjectTool<String>();

        ot.setObj(new String("长平居士"));
        String s = (String) ot.getObj();
        System.out.println(s);

    }
}
```

#### 2-4-2. 泛型方法  

1. 把泛型定义在方法上
2. public <泛型类型> 返回类型 方法名(泛型类型)

```java
public class ObjectTool {

    public <T> void show(T t) {
        System.out.println(t);
    }

}
```

```java
public static void main(String[] args) {
  ObjectTool<String> ot = new ObjectTool<String>();
  ot.show("Hello world");
}
```

#### 2-4-3. 泛型接口  

```java
public interface Inter<T> {
    public abstract void show(T t);
}
```

```java
public class ObjectTool1 implements Inter<String> {
// 方法一，不常用
    @Override
    public void show(String s) {
        System.out.print(s);
    }

}
```

```java
public class ObjectTool2<T> implements Inter<T> {
// 方法二，常用
    @Override
    public void show(T t) {
        System.out.print(t);
    }

}
```

#### 2-4-4. 泛型高级（通配符）  

```java
// 预设
class Animal {}
class Dog extends Animal {}
class Cat extends Animal {}
```

##### 泛型通配符<?>

任意类型，若没有明确，则是Object以及任意Java类  

```java
// 泛型明确时要前后一致
Collection<Object> c01 = new ArrayList<Object>(); // 正确
Collection<Object> c02 = new ArrayList<Animal>(); // 错误
Collection<Object> c03 = new ArrayList<Dog>();    // 错误
Collection<Object> c04 = new ArrayList<Cat>();    // 错误

// 使用泛型通配符
Collection<?> c05 = new ArrayList<Object>(); // 正确
Collection<?> c06 = new ArrayList<Animal>(); // 正确
Collection<?> c07 = new ArrayList<Dog>();    // 正确
Collection<?> c08 = new ArrayList<Cat>();    // 正确
```

##### ? extends E

向下限定，E及其子类

```java
Collection<? extends Animal> c09 = new ArrayList<Object>(); // 错误
Collection<? extends Animal> c10 = new ArrayList<Animal>(); // 正确
Collection<? extends Animal> c11 = new ArrayList<Dog>();    // 正确
Collection<? extends Animal> c12 = new ArrayList<Cat>();    // 正确
```

##### ? super E

向上限定，E及其父类

```java
Collection<? super Animal> c13 = new ArrayList<Object>(); // 正确
Collection<? super Animal> c14 = new ArrayList<Animal>(); // 正确
Collection<? super Animal> c15 = new ArrayList<Dog>();    // 错误
Collection<? super Animal> c16 = new ArrayList<Cat>();    // 错误
```

### 2-5. Set

无重复元素，无顺序的集合。

### 2-6. Set 的子类

#### 2-6-1. HashSet

哈希表实现的Set接口  
如果是自定义类的集合，需要重写 `hashCode()` 和 `equals()` 两个方法！！自动生成即可。（Alt+Shift+s）  

`LinkedHashSet<E>` 是 `HashSet` 的子类，定义了元素顺序  

#### 2-6-2. TreeSet

有序且唯一  
使用元素的自然顺序对元素进行排序，或者根据创建 set 时提供的 Comparator 进行排序，具体取决于使用的构造方法。  

**自然排序：**  
要想实现自然排序，被排序类必须实现自然排序接口 `Comparable<T>`  
难点：已知主要条件，但需要自己分析次要条件。如：按名字长度排序，则名字长度相同的人会被删除。

**比较器排序：**  
`TreeSet(Comparator<? super E> comparator)`构造一个新的空 TreeSet，它根据指定比较器进行排序。  
其中：`Comparator<T>`是一个接口，最好定义一个其实现类。（只用一次可用内部类）  

## 3. *JDK5 新特性

### 3-1. 自动拆装箱

```java
Integer i =10;  //自动装箱
int b= i;     //自动拆箱
```

### 3-2. 泛型

略。

### 3-3. 增强 for

```java
for(元素数据类型 变量 : 数组或Collection集合) {
   直接使用变量
}
```

> 使用之前要判断数组或集合不能为空

### 3-4. 静态导入

`import static 包名.类名.方法名` 可以导入到方法级别，但方法必须是静态的。之后可直接使用方法。注意不要导入同名方法。  

### 3-5. 可变参数

定义方法时不知道有多少个参数。  
格式：修饰符 返回值类型 方法名 (数据类型... 变量名) {}

```java
public static int sum(int... a) {
// a相当于一个数组

    int s = 0;
    for(int x: a) {
        s += x;
    }

    return s;
}
```

> 如果一个方法有可变参数，那么一定是最后一个参数。

**例：** `java.util.Arrays` 中 `static <T> List<T> asList(T... a)` 返回一个受指定数组支持的固定大小的列表。（数组转集合）  
**注意1：**虽然能把数组转集合，但集合长度不可改变！  
**注意2：**此处第一个 `<T>` 表示泛型方法，第二个 `<T>` 表示泛型类。参数为一个数组。

### 3-6. 枚举
