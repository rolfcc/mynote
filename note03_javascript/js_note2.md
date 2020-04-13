# JavaScript 笔记 II

## 目录 <!-- omit in toc -->

- [1. JavaScript HTML DOM](#1-javascript-html-dom)
  - [JavaScript HTML DOM 文档和元素](#javascript-html-dom-%e6%96%87%e6%a1%a3%e5%92%8c%e5%85%83%e7%b4%a0)
    - [文档及元素操作](#%e6%96%87%e6%a1%a3%e5%8f%8a%e5%85%83%e7%b4%a0%e6%93%8d%e4%bd%9c)
    - [元素节点导航](#%e5%85%83%e7%b4%a0%e8%8a%82%e7%82%b9%e5%af%bc%e8%88%aa)
  - [HTML 动画](#html-%e5%8a%a8%e7%94%bb)
  - [JavaScript HTML DOM 事件](#javascript-html-dom-%e4%ba%8b%e4%bb%b6)
- [2. JavaScript Browser BOM](#2-javascript-browser-bom)
  - [window](#window)
  - [window.screen](#windowscreen)
  - [window.location](#windowlocation)
  - [window.history](#windowhistory)
  - [window.navigator](#windownavigator)
  - [JavaScript 弹出框](#javascript-%e5%bc%b9%e5%87%ba%e6%a1%86)
  - [定时器](#%e5%ae%9a%e6%97%b6%e5%99%a8)
  - [Cookies](#cookies)
- [3. JavaScript AJAX](#3-javascript-ajax)
  - [XMLHttpRequest 对象](#xmlhttprequest-%e5%af%b9%e8%b1%a1)
    - [创建](#%e5%88%9b%e5%bb%ba)
    - [发送](#%e5%8f%91%e9%80%81)
      - [GET 请求](#get-%e8%af%b7%e6%b1%82)
      - [POST 请求](#post-%e8%af%b7%e6%b1%82)
      - [同步/异步](#%e5%90%8c%e6%ad%a5%e5%bc%82%e6%ad%a5)
      - [onreadystatechange 属性](#onreadystatechange-%e5%b1%9e%e6%80%a7)
    - [服务器响应](#%e6%9c%8d%e5%8a%a1%e5%99%a8%e5%93%8d%e5%ba%94)
- [4. JavaScript JSON](#4-javascript-json)
  - [数据类型](#%e6%95%b0%e6%8d%ae%e7%b1%bb%e5%9e%8b)
  - [JSON vs XML](#json-vs-xml)
  - [JSONP](#jsonp)
- [5. jQuery 简介](#5-jquery-%e7%ae%80%e4%bb%8b)
  - [选择器对比](#%e9%80%89%e6%8b%a9%e5%99%a8%e5%af%b9%e6%af%94)
  - [元素操作对比](#%e5%85%83%e7%b4%a0%e6%93%8d%e4%bd%9c%e5%af%b9%e6%af%94)
  - [CSS操作对比](#css%e6%93%8d%e4%bd%9c%e5%af%b9%e6%af%94)
  - [DOM操作对比](#dom%e6%93%8d%e4%bd%9c%e5%af%b9%e6%af%94)

## 1. JavaScript HTML DOM

当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。  
DOM 是一项 W3C (World Wide Web Consortium) 标准，定义了访问文档的标准，允许程序和脚本动态地访问、更新文档的内容、结构和样式。  

- **Core DOM** - 所有文档类型的标准模型
- **XML DOM** - XML 文档的标准模型
- **HTML DOM \*** - HTML 文档的标准模型

HTML DOM 是 HTML 的标准对象模型和编程接口。它定义了：  

- HTML 元素
  - 属性：能够设置或改变的 HTML 元素的值。
  - 方法：能够（在 HTML 元素上）执行的动作。
  - 事件

### JavaScript HTML DOM 文档和元素

文档代表网页，使用 document 访问并修改网页任意元素  

#### 文档及元素操作

**查找：**  

```JavaScript
document.getElementById(id) // 元素ID
document.getElementsByTagName(name) // 标签名字
document.getElementsByClassName(name) // 类名
```

- getElementById 获得单个节点
- getElementsByTagName 获得 HTMLCollection 对象。是一个**元素**集合，不是数组但可通过下标访问。
- getElementsByClassName 获得 HTML DOM NodeList 对象。是一个**节点**集合。

**修改：**  

```JavaScript
element.innerHTML = "new html content" // 内容
element.attribute = "new value" // 属性
element.setAttribute(attribute, value) // 属性
element.style.property = "new style" // 样式
```

**添加删除：**  

| 方法                            | 描述     |
| ------------------------------- | -------- |
| document.createElement(element) | **创建** |
| document.removeChild(element)   | **删除** |
| document.appendChild(element)   | **添加** |
| document.replaceChild(element)  | **替换** |
| document.write(text)            | **写入** |

**事件处理：**  
`document.getElementById(id).onclick = function(){code}`

#### 元素节点导航

**DOM 节点：**  
根据 W3C HTML DOM 标准，HTML 文档中的所有事物都是节点，包括元素，属性和文本（文本不包含在元素内）。  

**根节点：**  

- document.body - 文档的 body
- document.documentElement - 完整文档

**元素节点导航：**  

- parentNode
- childNodes[nodenumber]
- firstChild
- lastChild
- nextSibling
- previousSibling

**节点属性：**  

- nodeName
- nodeValue
- nodeType

### HTML 动画

```JavaScript
var id = setInterval(frame, 5);
// 设置间隙

function frame() {
    if (/* 测试是否完成 */) {
        clearInterval(id);
    } else {
         /* 改变元素样式的代码 */
    }
}
```

### JavaScript HTML DOM 事件

1. HTML 事件属性：  
   `<button onclick="displayDate()">试一试</button>`
2. 使用 HTML DOM 分配事件：
   `document.getElementById("myBtn").onclick = displayDate;`

| 事件名      | 时机 |
| ----------- | ---- |
| onload      | 载入 |
| onunload    | 离开 |
| onchange    | 改变 |
| onmouseover | 悬浮 |
| onmouseout  | 移出 |
| onmousedown | 点下 |
| onmouseup   | 松开 |
| onclick     | 单击 |

**事件监听器：**  

addEventListener() 方法  
removeEventListener() 方法  

## 2. JavaScript Browser BOM

### window

浏览器窗口，document 也是 window 的一部分  

| 名称               | 作用             |
| ------------------ | ---------------- |
| window.innerHeight | 窗口高度（px）   |
| window.innerWidth  | 窗口宽度（px）   |
| window.open()      | 打开新窗口       |
| window.close()     | 关闭当前窗口     |
| window.moveTo()    | 移动当前窗口     |
| window.resizeTo()  | 重新调整当前窗口 |

### window.screen

对象包含用户屏幕的信息。window 前缀可以去掉。  

| 名称               | 作用     |
| ------------------ | -------- |
| screen.width       | 屏幕宽度 |
| screen.height      | 屏幕高度 |
| screen.availWidth  | 可用宽度 |
| screen.availHeight | 可用高度 |
| screen.colorDepth  | 色深     |
| screen.pixelDepth  | 像素深度 |

### window.location

对象可用于获取当前页面地址（URL）并把浏览器重定向到新页面。window 前缀可以去掉。  

| 名称              | 作用                       |
| ----------------- | -------------------------- |
| location.href     | 返回当前页面的 href (URL)  |
| location.hostname | 返回 web 主机的域名        |
| location.pathname | 返回当前页面的路径或文件名 |
| location.protocol | 返回使用的 web 协议        |
| location.assign   | 加载新文档                 |

### window.history

对象包含浏览器历史。

| 名称              | 作用                         |
| ----------------- | ---------------------------- |
| history.back()    | 等同于在浏览器点击后退按钮   |
| history.forward() | 等同于在浏览器中点击前进按钮 |

### window.navigator

对象包含有关访问者的信息（慎用）。

### JavaScript 弹出框

| 名称      | 作用   |
| --------- | ------ |
| alert()   | 警告框 |
| confirm() | 确认框 |
| prompt()  | 提示框 |

> 换行使用 `\n`

### 定时器

| 名称                   | 作用                       |
| ---------------------- | -------------------------- |
| setTimeout(函数, 毫秒) | 延时一段时间执行函数       |
| setInterval()          | 同上，但持续重复执行该函数 |
| clearTimeout()         | 停止计时                   |
| clearInterval()        | 同上                       |

### Cookies

`document.cookie` 创建，读取，删除 cookie

**创建：**  
创建时，通过 path 参数，您可以告诉浏览器 cookie 属于什么路径。默认情况下，cookie 属于当前页。  
`document.cookie = "username=Bill Gates; expires=Sun, 31 Dec 2017 12:00:00 UTC; path=/";`

**读取：**  
`var x = document.cookie;`

**改变：**  
同创建。

**删除：**  
直接把 expires 参数设置为过去的日期即可  

## 3. JavaScript AJAX

AJAX = Asynchronous JavaScript And XML.  
异步JS和XML（实际运用中也可以时JSON或纯文本文件）  

它包括：

- 浏览器内建的 XMLHttpRequest 对象（从 web 服务器请求数- 据）
- JavaScript 和 HTML DOM（显示或使用数据）

> Ajax 允许通过与场景后面的 Web 服务器交换数据来异步更新网页。这意味着可以更新网页的部分，而不需要重新加载整个页面。

```text
| 浏览器 | ------- Internet ------- | 服务器 |
|--1.发生时间                       |
|--2.创建 XMLHttpRequest 对象       |
|--3.发送 HttpRequest >>>>>>>>>>>>> |--4.处理 HttpRequest
|--6.处理返回数据 <<<<<<<<<<<<<<<<< |--5.创建响应
|--7.更新页面
```

简单来说，用 JavaScript 创建/处理数据，用 XML 等文件传输数据。

### XMLHttpRequest 对象

#### 创建

```JavaScript
var xhttp;
if (window.XMLHttpRequest) {
    xhttp = new XMLHttpRequest();
} else {
    // code for IE6, IE5
    xhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
```

#### 发送

```JavaScript
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();
```

| 方法                     | 描述                     |
| ------------------------ | ------------------------ |
| open(method, url, async) | 规定请求的类型           |
| send()                   | 向服务器发送请求（GET）  |
| send(string)             | 向服务器发送请求（POST） |

> 1. 参数
>    - method：请求的类型：GET 还是 POST
>    - url：服务器（文件）位置
>    - async：true（异步）或 false（同步）
> 2. GET 和 POST
>    - GET 比 POST 更简单更快，在以下情况始终使用 POST：
>    - 缓存文件不是选项（更新服务器上的文件或数据库）
>    - 向服务器发送大量数据（POST 无大小限制）
>    - 发送用户输入（可包含未知字符）

##### GET 请求

在上面的例子中，您可能会获得一个缓存的结果。为了避免此情况，请向 URL 添加一个唯一的 ID：

```JavaScript
xhttp.open("GET", "demo_get.asp?t=" + Math.random(), true);
xhttp.send();
```

如果您需要用 GET 方法来发送信息，请向 URL 添加这些信息：

```JavaScript
xhttp.open("GET", "demo_get2.asp?fname=Bill&lname=Gates", true);
xhttp.send();
```

##### POST 请求

一条简单的 POST 请求：

```JavaScript
xhttp.open("POST", "demo_post.asp", true);
xhttp.send();
```

如需像 HTML 表单那样 POST 数据，请通过 `setRequestHeader()` 添加一个 HTTP 头部。请在 send() 方法中规定您需要发送的数据：

```JavaScript
xhttp.open("POST", "ajax_test.asp", true);
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Bill&lname=Gates");
```

setRequestHeader(header, value) 向请求添加 HTTP 头部

- header：规定头部名称
- value：规定头部值

##### 同步/异步

通过异步发送，JavaScript 不必等待服务器响应，而是可以：

- 在等待服务器响应时执行其他脚本
- 当响应就绪时处理响应

##### onreadystatechange 属性

通过 XMLHttpRequest 对象，您可以定义当请求接收到应答时所执行的函数。  
这个函数是在 XMLHttpResponse 对象的 onreadystatechange 属性中定义的：  

```JavaScript
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    document.getElementById("demo").innerHTML = this.responseText;
  }
};
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();
```

> 如果时同步请求，并不需要这个属性，因为系统会等待回应，什么都不做。

#### 服务器响应

| 属性               | 描述                       |
| ------------------ | -------------------------- |
| onreadystatechange | 传输状态改变时所调用的函数 |
| readyState         | 传输状态                   |
| status             | 状态                       |
| statusText         | 返回状态文本               |

1. readyState  
   - 0: 请求未初始化
   - 1: 服务器连接已建立
   - 2: 请求已接收
   - 3: 正在处理请求
   - 4: 请求已完成且响应已就绪
2. status/statusText
   - 200: "OK"
   - 403: "Forbidden"
   - 404: "Page not found"
   - 等等。。。
3. 当 `readyState` 为 4，`status` 为 200 时，响应就绪

```JavaScript
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "/example/js/ajax_info.txt", true);
  xhttp.send();
}
```

> onreadystatechange 共触发5次 readyState 改变5次

**服务器响应属性：**  

| 属性         | 描述                        |
| ------------ | --------------------------- |
| responseText | 获取字符串形式的响应数据    |
| responseXML  | 获取 XML 数据形式的响应数据 |

**服务器响应方法：**  

| 属性                    | 描述                       |
| ----------------------- | -------------------------- |
| getResponseHeader()     | 从服务器返回特定的头部信息 |
| getAllResponseHeaders() | 从服务器返回所有头部信息   |

> XML HttpRequest 对象有一个內建的 XML 解析器。  
> ResponseXML 属性以 XML DOM 对象返回服务器响应。  

## 4. JavaScript JSON

JSON: JavaScript Object Notation  

> JSON <-> JavaScript 对象
> 文本文件 <-> 程序

**语法：**

- 数据在名称/值对中
- 数据由逗号分隔
- 花括号容纳对象
- 方括号容纳数组

**发送：**  

```JavaScript
var myObj = { name:"Bill Gates",  age:62, city:"Seattle" };
var myJSON =  JSON.stringify(myObj);
window.location = "demo_json.php?x=" + myJSON;
```

**接收：**  

```JavaScript
var myJSON = '{ "name":"Bill Gates",  "age":62, "city":"Seattle" }';
var myObj =  JSON.parse(myJSON);
document.getElementById("demo").innerHTML = myObj.name;
```

**存储：**  

```JavaScript
//存储数据：
myObj = { name:"Bill Gates",  age:62, city:"Seattle" };
myJSON =  JSON.stringify(myObj);
localStorage.setItem("testJSON", myJSON);

//接收数据：
text = localStorage.getItem("testJSON");
obj =  JSON.parse(text);
document.getElementById("demo").innerHTML = obj.name;
```

> JSON --- `parse()` --> JavaScript 对象  
> JSON <-- `stringify()` --- JavaScript 对象  

### 数据类型

1. 在 JSON 中，值必须是以下数据类型之一：
   - 字符串
   - 数字
   - 对象（JSON 对象）
   - 数组
   - 布尔
   - Null
2. JSON 的值不可以是以下数据类型之一：
   - 函数
   - 日期（如果需要，可以转换）
   - undefined

**解析日期：**  
一种方法是字符串转日期，另一种方法是使用 `JSON.parse()` 函数的第二个参数，被称为 reviver。

```JavaScript
var text =  '{ "name":"Bill Gates", "birth":"1955-10-28", "city":"Seattle"}';
var obj = JSON.parse(text);
obj.birth = new Date(obj.birth);

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
```

```JavaScript
var text =  '{ "name":"Bill Gates", "birth":"1955-10-28", "city":"Seattle"}';
var obj = JSON.parse(text, function (key, value) {
    if  (key == "birth") {
        return new Date(value);
    } else {
         return value;
   }});

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
```

### JSON vs XML

**实例：**  

```JSON
{"employees":[
    { "firstName":"Bill", "lastName":"Gates" },
    { "firstName":"Steve", "lastName":"Jobs" },
    { "firstName":"Elon", "lastName":"Musk" }
]}
```

```XML
<employees>
    <employee>
         <firstName>Bill</firstName>
         <lastName>Gates</lastName>
     </employee>
     <employee>
         <firstName>Steve</firstName>
         <lastName>Jobs</lastName>
     </employee>
     <employee>
         <firstName>Elon</firstName>
         <lastName>Musk</lastName>
     </employee>
</employees>
```

### JSONP

JSONP 指的是 JSON with Padding。  
JSONP 是一种无需考虑**跨域问题**即可传送 JSON 数据的方法。  
JSONP 不使用 `XMLHttpRequest` 对象。  
JSONP 使用 &lt;script&gt; 标签取而代之。  

## 5. jQuery 简介

jQuery 一个非官方 JavaScript 库  

### 选择器对比

```JavaScript
var myElement = document.getElementById("id01");
var myElement = $("#id01");

var myElements = document.getElementsByTagName("p");
var myElements = $("p");

var myElements = document.getElementsByClassName("intro");
var myElements = $(".intro");

var myElements = document.querySelectorAll("p.intro");
var myElements = $("p.intro");
```

### 元素操作对比

```JavaScript
// 修改/获取 文本

myElement.textContent = "Hello China!";
myElement.text("Hello China!");

var myText = myElement.textContent || myElement.innerText;
var myText = myElement.text();

// 修改/获取 HTML

var myElement.innerHTML = "<p>Hello World</p>";
var myElement.html("<p>Hello World</p>");

var content = myElement.innerHTML;
var content = myElement.html();
```

### CSS操作对比

```JavaScript
myElement.style.display = "none";
myElement.hide();

myElement.style.display = "";
myElement.show();

myElement.style.fontSize = "35px";
myElement.css("font-size","35px");
```

### DOM操作对比

```JavaScript
element.parentNode.removeChild(element);
$("#id").remove();

var myParent = myElement.parentNode;
var myParent = myElement.parent();
```
