# JavaScript 笔记

## 目录 <!-- omit in toc -->

- [1. 简介](#1-%e7%ae%80%e4%bb%8b)
  - [JS与HTML结合方式](#js%e4%b8%8ehtml%e7%bb%93%e5%90%88%e6%96%b9%e5%bc%8f)
- [2. JS 语言基础](#2-js-%e8%af%ad%e8%a8%80%e5%9f%ba%e7%a1%80)
  - [输出](#%e8%be%93%e5%87%ba)
  - [变量声明](#%e5%8f%98%e9%87%8f%e5%a3%b0%e6%98%8e)
    - [string](#string)
    - [数字](#%e6%95%b0%e5%ad%97)
    - [逻辑](#%e9%80%bb%e8%be%91)
    - [数组](#%e6%95%b0%e7%bb%84)
    - [日期](#%e6%97%a5%e6%9c%9f)
    - [数学](#%e6%95%b0%e5%ad%a6)
    - [随机](#%e9%9a%8f%e6%9c%ba)
    - [转换](#%e8%bd%ac%e6%8d%a2)
  - [语句](#%e8%af%ad%e5%8f%a5)
    - [异常](#%e5%bc%82%e5%b8%b8)
  - [特有运算符](#%e7%89%b9%e6%9c%89%e8%bf%90%e7%ae%97%e7%ac%a6)
    - [比较运算符](#%e6%af%94%e8%be%83%e8%bf%90%e7%ae%97%e7%ac%a6)
    - [类型运算符](#%e7%b1%bb%e5%9e%8b%e8%bf%90%e7%ae%97%e7%ac%a6)
    - [位运算符](#%e4%bd%8d%e8%bf%90%e7%ae%97%e7%ac%a6)
  - [函数](#%e5%87%bd%e6%95%b0)
    - [定义函数](#%e5%ae%9a%e4%b9%89%e5%87%bd%e6%95%b0)
    - [自定义函数](#%e8%87%aa%e5%ae%9a%e4%b9%89%e5%87%bd%e6%95%b0)
    - [函数是对象](#%e5%87%bd%e6%95%b0%e6%98%af%e5%af%b9%e8%b1%a1)
    - [参数](#%e5%8f%82%e6%95%b0)
    - [函数方法 call 与 apply](#%e5%87%bd%e6%95%b0%e6%96%b9%e6%b3%95-call-%e4%b8%8e-apply)
  - [对象](#%e5%af%b9%e8%b1%a1)
    - [类结构体的对象](#%e7%b1%bb%e7%bb%93%e6%9e%84%e4%bd%93%e7%9a%84%e5%af%b9%e8%b1%a1)
    - [创建方法](#%e5%88%9b%e5%bb%ba%e6%96%b9%e6%b3%95)
    - [获取](#%e8%8e%b7%e5%8f%96)
    - [JavaScript for...in 循环](#javascript-forin-%e5%be%aa%e7%8e%af)
    - [添加删除属性](#%e6%b7%bb%e5%8a%a0%e5%88%a0%e9%99%a4%e5%b1%9e%e6%80%a7)
    - [方法](#%e6%96%b9%e6%b3%95)
    - [JavaScript 对象访问器](#javascript-%e5%af%b9%e8%b1%a1%e8%ae%bf%e9%97%ae%e5%99%a8)
    - [对象原型 prototype](#%e5%af%b9%e8%b1%a1%e5%8e%9f%e5%9e%8b-prototype)
  - [事件](#%e4%ba%8b%e4%bb%b6)
  - [正则表达式 RegExp](#%e6%ad%a3%e5%88%99%e8%a1%a8%e8%be%be%e5%bc%8f-regexp)
- [3. JS 进阶](#3-js-%e8%bf%9b%e9%98%b6)
  - [提升 Hoisting](#%e6%8f%90%e5%8d%87-hoisting)
  - [严格模式](#%e4%b8%a5%e6%a0%bc%e6%a8%a1%e5%bc%8f)
  - [this](#this)
  - [JavaScript JSON 快速上手](#javascript-json-%e5%bf%ab%e9%80%9f%e4%b8%8a%e6%89%8b)
    - [JSON 示例](#json-%e7%a4%ba%e4%be%8b)
    - [JavaScript 中 JSON 读取](#javascript-%e4%b8%ad-json-%e8%af%bb%e5%8f%96)
- [4. 表单操作](#4-%e8%a1%a8%e5%8d%95%e6%93%8d%e4%bd%9c)
  - [验证空](#%e9%aa%8c%e8%af%81%e7%a9%ba)
  - [验证数字](#%e9%aa%8c%e8%af%81%e6%95%b0%e5%ad%97)
  - [自动 HTML 表单验证](#%e8%87%aa%e5%8a%a8-html-%e8%a1%a8%e5%8d%95%e9%aa%8c%e8%af%81)
  - [HTML 约束验证](#html-%e7%ba%a6%e6%9d%9f%e9%aa%8c%e8%af%81)
  - [JavaScript 验证 API](#javascript-%e9%aa%8c%e8%af%81-api)

## 1. 简介

弱类型语言，由三部分组成

1. ECMAScript
   - ECMA 欧洲计算机协会
   - 制定js语法，语句
2. BOM
   - broswer object model 浏览器对象模型
3. DOM
   - document ouject model 文档对象模型

### JS与HTML结合方式

1. `<script type="text/javascript"></script>` 直接嵌套
2. `<script src="./JavaScript/01_JSDemo.js"></script>` 通过文件导入

## 2. JS 语言基础

### 输出

- 使用 `window.alert()` 写入警告框
- 使用 `document.write()` 写入 HTML 输出
- 使用 `innerHTML` 写入 HTML 元素
- 使用 `console.log()` 写入浏览器控制台

```JavaScript
<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = 5 + 6;
</script>
```

```JavaScript
<script>
document.write(5 + 6);
</script>
```

```JavaScript
// 在 HTML 文档完全加载后使用 document.write() 将删除所有已有的 HTML
<button onclick="document.write(5 + 6)">试一试</button>
```

### 变量声明

JS的**原始类型**

- string
- number
- boolean
- null
  null 是对象占位符，表示引用为空，`typeof(null)` 会输出 object
- undifined
  `undifined == null` 会输出 true

> 使用 var 定义，根据赋值确定类型

运算符 typeof() 查看数据类型  

#### string

1. 转义字符 `\`
2. 内建属性 length 是`属性`不是`方法`
3. 字符串一般不是对象，也不要把它定义成对象。在使用属性和方法时它会被自动视为对象

**方法：**  
`indexOf()` 和 `lastIndexOf()` 查找子串，从0开始计算位置。找不到返回 `-1` 接受第二个参数作为起始位置  
`search()` 查找子串，不可指定位置，但接受正则表达式（接受正则表达式时返回末尾位置）  

#### 数字

**特殊值：**  
`NaN` 非数  
`Infinity` `-Infinity` 正负无穷  
`0x` 开头是十六进制
`0` 开头是八进制  

**方法：**  
`isNaN()` 判断是否是数字  
`toString(16)` `toString(8)` `toString(2)` 输出为16、8、2进制字符串。  
`toExponential()` 返回字符串形式的四舍五入值。可设定保留多少位小数。  
`toFixed()` 返回字符串值，它包含了指定位数小数的数字。  
`toPrecision()` 返回字符串值，它包含了指定长度的数字。  
`valueOf()` 以数值返回数值。  

**变量变数值：**  

- `Number()` 方法
- `parseInt()` 方法
- `parseFloat()` 方法

> 这些都是全局方法，而非数字的方法  
> Number 能将日期变成毫秒数  

#### 逻辑

#### 数组

`var array-name = [item1, item2, ...];`  
使用数组名时返回完整数组而非指针或引用。  
数组是一个特殊对象，有数字索引。其中可以保存对象，函数，或数组。  
JS数组只能由数字访问，某些语言可以给数组命名，我们称之为散列。  

**属性：**  
`length`  

**方法：**  
`toString()`  
`join()` 同上，可规定分隔符  
`push()` `pop()` push返回新长度，pop返回弹出值  
`shift()` `unshift()` 同上，但向头部添加  
> 运算符delete可以删除数组元素，但会留下空洞  
`splice()` 方法可用于向数组添加/删除元素  

```JavaScript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 1, "Lemon", "Kiwi");
// 向第二个位置插入，删除一个，返回数组
// 得到 Banana,Orange,Lemon,Kiwi,Mango

fruits.splice(0, 1);
// 删除 fruits 中的第0个元素
```

`concat()` 方法通过合并（连接）现有数组来创建一个**新数组**  
`slice()` 方法用数组的某个片段切出新数组。输入两个数字表示开始和结束（不包括结束位置）  

**排序：**  

`sort()` 排序  
> 排序通过比值函数排序，如：`function(a, b){return a-b}`  
`reverse()` 方法反转数组中的元素。  

**数组迭代：**  

`forEach(函数名)` 对每一个项目使用函数  
`map()` 同上，但会新建一个数组  
`filter()` 过滤器创建新数组  

```JavaScript
// 一个过滤函数示例
/**
 * 项目值   value
 * 项目索引 index
 * 数组本身 array
 */
function myFunction(value, index, array) {
  return value > 18;
  // 返回值大于18的数字
}
```

`reduce()`  
`reduceRight()`  
`every()` 方法检查所有数组值是否通过测试。函数同过滤器。  
`some()` 方法检查某些数组值是否通过了测试。函数同过滤器。  
`indexOf()` 方法在数组中搜索元素值并返回其位置。  
`Array.lastIndexOf()` 同上，从后向前  
`find()` 方法返回通过测试函数的第一个数组元素的值。函数同过滤器。  
`findIndex()` 同上，返回底数  

#### 日期

`var d = new Date();`

#### 数学

#### 随机

#### 转换

- Number() 转换数值
- String() 转换字符串
- Boolean() 转换布尔值。

`constructor` **属性**返回所有 JavaScript 变量的构造器函数。  
可以用来检测日期和数组  

### 语句

- if
- switch
  - jdk 1.7 支持 String
  - js 支持 String
- while for do-while
- break continue return
- debugger 停止执行并调用调试函数
- try-catch
- fucntion

#### 异常

同 Java  

- `try` 语句使您能够测试代码块中的错误。
- `catch` 语句允许您处理错误。
- `throw` 语句允许您创建自定义错误。
- `finally` 使您能够执行代码，在 try 和 catch 之后，无论结果如何。

### 特有运算符

#### 比较运算符

`===` 等值且等型
`!==` 不等值或不等型

```JavaScript
var a = 5;

alert(a=="5");  // true
alert(a==5);    // true
alert(a===5);   // true
alert(a==="5"); // false

```

#### 类型运算符

`typeof` 返回变量的类型。  
（建议）`instanceof` 返回 true，如果对象是对象类型的实例。  

#### 位运算符

| 符号  | 作用            |
| :---: | --------------- |
|  `&`  | 与              |
|  `|`  | 或              |
|  `~`  | 非              |
|  `^`  | 异或（不同为1） |
| `<<`  | 零填充左位移    |
| `>>`  | 有符号右位移    |
| `>>>` | 零填充右位移    |

### 函数

#### 定义函数

函数名是特殊的变量  

```JavaScript
function name(参数 1, 参数 2, 参数 3) {
    要执行的代码
}
```

```JavaScript
// 匿名函数
var x = function (a, b) {return a * b};
var z = x(4, 3); // 函数表达式不会提升！！！
```

```JavaScript
// 使用函数构造器
var myFunction = new Function("a", "b", "return a * b");
var x = myFunction(4, 3);
```

#### 自定义函数

```JavaScript
(function () {
    var x = "Hello!!";      //我会调用我自己
})();
```

#### 函数是对象

JavaScript 中的 `typeof` 运算符会为函数返回 "`function`"。  
但是最好是把 JavaScript 函数描述为对象。  
JavaScript 函数都有**属性**和**方法**。  

`arguments.length` 会返回函数被调用时收到的参数数目  
`toString()` 方法以字符串返回函数  

**箭头函数\*：**

> 大于 IE11 可用

```JavaScript
// ES5
var x = function(x, y) {
  return x * y;
}

// ES6
const x = (x, y) => x * y;
// 请使用 const，因为它不会变
```

#### 参数

> JS 不检查参数！！！

**arguments 对象：**  
arguments 对象包含函数调用时使用的**参数数组**。  

#### 函数方法 call 与 apply

**方法重用：**  
使用 `call()` 方法，您可以编写能够在不同对象上使用的方法。  

```JavaScript
var person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
}
var person1 = {
    firstName:"Bill",
    lastName: "Gates",
}
person.fullName.call(person1);  // 将返回 "Bill Gates"
```

```JavaScript
// call甚至可以临时添加更多参数
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"Bill",
  lastName: "Gates"
}
person.fullName.call(person1, "Seattle", "USA");
```

- apply 和 call 基本相同，其不同点在于
  - call() 方法分别接受参数。
  - apply() 方法接受数组形式的参数。

### 对象

JS 对象类似于：

- PHP 中的关联数组
- Python 中的字典
- C 中的哈希表
- Java 中的哈希映射
- Ruby 和 Perl 中的散列

#### 类结构体的对象

`var car = {type:"porsche", model:"911", color:"white"};`  
这段代码把多个值赋给 car 类似一个结构体。  

#### 创建方法

- 定义和创建单个对象，使用对象文字。
- 定义和创建单个对象，通过关键词 new。
- 定义对象构造器，然后创建构造类型的对象。

> 在 ECMAScript 5 中，也可以通过函数 Object.create() 来创建对象。

```JavaScript
// 方法一
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id       : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

// 方法二
var person = new Object();
person.firstName = "Bill";
person.lastName = "Gates";
person.age = 50;
person.eyeColor = "blue";
```

#### 获取

- **对象**
- 方法一：`person.lastName;`
- 方法二：`person["lastName"];`

- **方法**
- `objectName.methodName()`
- 注意：`name = person.fullName;` 不加括号返回函数定义。

#### JavaScript for...in 循环

JavaScript `for...in` 语句遍历对象的属性。

```JavaScript
var person = {fname:"Bill", lname:"Gates", age:62};

for (x in person) {
    txt += person[x];
}
```

#### 添加删除属性

JS 可以为创建好的类中添加新属性  

`person.nationality = "English";`  

`delete` 关键词从对象中删除属性：

```JavaScript
var person = {firstName:"Bill", lastName:"Gates", age:62, eyeColor:"blue"};
delete person.age;   // 或 delete person["age"];
```

#### 方法

JS 中方法可以看作属性的一种

#### JavaScript 对象访问器

JavaScript 访问器（Getter 和 Setter）  
ECMAScript 5 (2009) 引入了 Getter 和 Setter。  

```JavaScript
// 创建对象：
var person = {
    firstName: "Bill",
    lastName: "Gates",
    language: "en",

    get getLang() {
        return this.language;
    },

    /**
     * @param {string} lang
     */
    set setLang(lang) {
        this.language = lang;
    }
};

window.onload = function () {

    // 使用 getter 来显示来自对象的数据：
    document.getElementById("demoa").innerHTML = person.getLang;

    // 使用 setter 来设置对象属性：
    person.setLang = "cn";

    // 显示来自对象的数据：
    document.getElementById("demob").innerHTML = person.language;
}
```

#### 对象原型 prototype

所有 JavaScript 对象都从原型继承属性和方法。所有的对象都将继承属性 prototype  

**添加属性：**  

`Person.prototype.nationality = "English";`  

**添加方法：**  

```JavaScript
Person.prototype.name = function() {
    return this.firstName + " " + this.lastName;
};
```

### 事件

**调用示例：**  

```HTML
<button onclick='document.getElementById("demo").innerHTML=Date()'>现在的时间是？</button>
<button onclick="displayDate()">现在的时间是？</button>
```  

> 单双引号均可

**事件列表：**  

|    事件     | 描述                         |
| :---------: | ---------------------------- |
|  onchange   | HTML 元素已被改变            |
|   onclick   | 用户点击了 HTML 元素         |
| onmouseover | 用户把鼠标移动到 HTML 元素上 |
| onmouseout  | 用户把鼠标移开 HTML 元素     |
|  onkeydown  | 用户按下键盘按键             |
|   onload    | 浏览器已经完成页面加载       |

### 正则表达式 RegExp

语法：`/pattern/modifiers;` `/模式/修饰符`  
可以赋值给变量  

**修饰符：**  
| 修饰符 | 描述                         |
| :----: | ---------------------------- |
|   i    | 执行对大小写不敏感的匹配     |
|   g    | 执行全局匹配（查找所有匹配） |
|   m    | 执行多行匹配                 |

**模式：**  
|  表达式  | 描述                                        |
| :------: | ------------------------------------------- |
| `[abc]`  | 查找方括号之间的任何字符。                  |
| `[0-9]`  | 查找任何从 0 至 9 的数字。                  |
| `(x|y)`  | 查找由 `|` 分隔的任何选项。                 |
|   `\d`   | 查找数字。                                  |
|   `\s`   | 查找空白字符。                              |
|   `\b`   | 匹配单词边界。                              |
| `\uxxxx` | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |
|   `n+`   | 匹配任何包含至少一个 n 的字符串。           |
|   `n*`   | 匹配任何包含零个或多个 n 的字符串。         |
|   `n?`   | 匹配任何包含零个或一个 n 的字符串。         |

## 3. JS 进阶

### 提升 Hoisting

将所有变量**声明**默认提升至顶部，就像老版的C语言那样，不过是自动的（初始化语句不会提升）  
用 `let` 或 `const` 声明的变量和常量不会被提升！  

以前的JS只有两个作用域，全局和函数  
`let` 和 `const` 提供块作用域变量/常量  
（ES2015）提供  

### 严格模式

`"use strict";` 定义 JavaScript 代码应该以“严格模式”执行。放在脚本第一行。

### this

- 在方法中，this 指的是所有者对象。
- 单独的情况下，this 指的是全局对象。
- 在函数中，this 指的是全局对象。
- 在函数中，严格模式下，this 是 undefined。
- 在事件中，this 指的是接收事件的元素。

### JavaScript JSON 快速上手

JSON 是存储和传输数据的格式。  
JSON 经常在数据从服务器发送到网页时使用。  

**简介：**  

- JSON 指的是 JavaScript Object Notation
- JSON 是轻量级的数据交换格式
- JSON 独立于语言
- JSON 是“自描述的”且易于理解

> JSON 的语法是来自 JavaScript 对象符号的语法，但 JSON 格式是纯文本。读取和生成 JSON 数据的代码可以在任何编程语言编写的。  

#### JSON 示例  

```JSON
{
"employees":[
    {"firstName":"Bill", "lastName":"Gates"},
    {"firstName":"Steve", "lastName":"Jobs"},
    {"firstName":"Alan", "lastName":"Turing"}
]
}
```

> 一个雇员对象：包括三条员工记录数组  

- **数据**的结构 `"名称":"值"`
- **数据**由**逗号**分隔
- **花括号**保存**对象**
- **方括号**保存**数组**

#### JavaScript 中 JSON 读取

首先，创建包含 JSON 语法的 JavaScript **字符串**：

```JavaScript
var text = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"Steve" , "lastName":"Jobs" },' +
'{ "firstName":"Alan" , "lastName":"Turing" } ]}';
```

然后，使用 JavaScript 的内建函数 JSON.parse() 来把这个字符串转换为 JavaScript 对象：

```JavaScript
var obj = JSON.parse(text);
```

## 4. 表单操作

### 验证空

```HTML
<!DOCTYPE html>
<html>
<head>
<script>
function validateForm() {
  var x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("必须填写姓名！");
    return false;
  }
}
</script>
</head>
<body>

<form name="myForm" action="/demo/action_page.php" onsubmit="return validateForm()" method="post">
  姓名：<input type="text" name="fname">
  <input type="submit" value="提交">
</form>

</body>
</html>
```

### 验证数字

### 自动 HTML 表单验证

关键字 `required`

```HTML
<input type="text" name="fname" required>
```

### HTML 约束验证

- 约束验证 HTML 输入属性
- 约束验证 CSS 伪选择器
- 约束验证 DOM 属性和方法

### JavaScript 验证 API
