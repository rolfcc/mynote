# XML 笔记

## 目录 <!-- omit in toc -->

- [1. XML](#1-xml)
  - [XML 文档验证](#xml-%e6%96%87%e6%a1%a3%e9%aa%8c%e8%af%81)
    - [XML DTD](#xml-dtd)
    - [XML Schema](#xml-schema)
  - [显示](#%e6%98%be%e7%a4%ba)
    - [CSS 方法](#css-%e6%96%b9%e6%b3%95)
    - [XSLT 方法](#xslt-%e6%96%b9%e6%b3%95)
  - [XML 解析](#xml-%e8%a7%a3%e6%9e%90)
    - [XML JavaScript](#xml-javascript)
    - [jaxp](#jaxp)
    - [dom4j](#dom4j)
  - [XML 高级](#xml-%e9%ab%98%e7%ba%a7)
    - [XML 命名空间（XML Namespaces）](#xml-%e5%91%bd%e5%90%8d%e7%a9%ba%e9%97%b4xml-namespaces)
    - [XML CDATA](#xml-cdata)
    - [编码](#%e7%bc%96%e7%a0%81)
- [2. XSL - XSLT](#2-xsl---xslt)
  - [实例研究 如何使用 XSLT 将 XML 转换为 XHTML](#%e5%ae%9e%e4%be%8b%e7%a0%94%e7%a9%b6-%e5%a6%82%e4%bd%95%e4%bd%bf%e7%94%a8-xslt-%e5%b0%86-xml-%e8%bd%ac%e6%8d%a2%e4%b8%ba-xhtml)
  - [说明](#%e8%af%b4%e6%98%8e)
- [3. XSL - XPath](#3-xsl---xpath)
  - [XPath 节点](#xpath-%e8%8a%82%e7%82%b9)
  - [XPath 语法](#xpath-%e8%af%ad%e6%b3%95)
  - [XPath Axes（轴）](#xpath-axes%e8%bd%b4)
  - [XPath 运算符](#xpath-%e8%bf%90%e7%ae%97%e7%ac%a6)
- [4. XSL-FO](#4-xsl-fo)
  - [XSL-FO 文档](#xsl-fo-%e6%96%87%e6%a1%a3)
  - [XSL-FO 区域](#xsl-fo-%e5%8c%ba%e5%9f%9f)
  - [XSL-FO 输出](#xsl-fo-%e8%be%93%e5%87%ba)
  - [XSL-FO 流](#xsl-fo-%e6%b5%81)
  - [XSL-FO 页面](#xsl-fo-%e9%a1%b5%e9%9d%a2)
  - [XSL-FO Blocks（块）](#xsl-fo-blocks%e5%9d%97)
  - [XSL-FO 列表](#xsl-fo-%e5%88%97%e8%a1%a8)
  - [XSL-FO 表格](#xsl-fo-%e8%a1%a8%e6%a0%bc)
  - [XSL-FO 与 XSLT](#xsl-fo-%e4%b8%8e-xslt)
- [5. XQuery](#5-xquery)
- [6. XLink 和 XPointer](#6-xlink-%e5%92%8c-xpointer)
- [7. DTD 和 Schema](#7-dtd-%e5%92%8c-schema)
  - [DTD 快速上手](#dtd-%e5%bf%ab%e9%80%9f%e4%b8%8a%e6%89%8b)
  - [Schema 快速上手](#schema-%e5%bf%ab%e9%80%9f%e4%b8%8a%e6%89%8b)
- [8. XML DOM](#8-xml-dom)
- [9. XForms](#9-xforms)

## 1. XML

```XML
<?xml version="1.0" encoding="ISO-8859-1"?>
<note>
<to>George</to>
<from>John</from>
<heading>Reminder</heading>
<body>Don't forget the meeting!</body>
</note>
```

- 现代 XML 技术
  - 用 XML Schema 定义 XML 的结构和数据类型
  - 用 XSLT 来转换 XML 数据
  - 用 SOAP 来交换应用程序之间的 XML 数据
  - 用 WSDL 来描述网络服务
  - 用 RDF 来描述网络资源
  - 用 XPath 和 XQuery 来访问 XML 数据
  - 用 SMIL 来定义图形

### XML 文档验证

XML 错误会终止您的程序

> 几乎所有的主流浏览器均支持 XML 和 XSLT。

#### XML DTD

文档类型定义（DTD）可定义合法的XML文档构建模块。它使用一系列合法的元素来定义文档的结构。

DTD 可被成行地声明于 XML 文档中，也可作为一个外部引用。

#### XML Schema

W3C 支持一种基于 XML 的 DTD 代替者，它名为 XML Schema

### 显示

#### CSS 方法

`<?xml-stylesheet type="text/css" href="cd_catalog.css"?>`  

#### XSLT 方法

XSLT 是首选的 XML 样式表语言。  
XSLT (eXtensible Stylesheet Language Transformations) 远比 CSS 更加完善。

`<?xml-stylesheet type="text/xsl" href="simple.xsl"?>`  

- 使用方法：
  - 使用 XSLT 显示 XML （浏览器方法）
  - 在服务器上通过 XSLT 转换 XML

### XML 解析

解析方法简介：DOM方式和SAX（Simple API for XML）方式  
DOM：一次将节点封装，可增删改。  
SAX：边运行边读，不可增删改。  

不同的公司提供了针对上述两种方法的解析器，通过API方式提供。  

- sun公司提供 jasp
- dom4j组织提供 dom4j （实际使用较多）
- jdom组织提供 jdom

#### XML JavaScript

参考ajax

#### jaxp

jasp是 Java SE 的一部分，在 `javax.xml.parsers` 中定义了几个工厂类。可调用这些类，得到 DOM 和 SAX 解析器对象。  

`DocumentBuilder` DOM解析器类（抽象类，通过工厂类获得实例）  
`DocumentBuilderFactory` 解析器工厂  

`SAXParser` SAX解析器类  
`SAXParserFactory` 解析器工厂  

**DOM 方法：**  

- `DocumentBuilder`
  - 抽象类，通过 `DocumentBuilderFactory.newDocumentBuilder()` 获取。
- `DocumentBuilderFactory`
  - 抽象类，通过 `DocumentBuilderFactory.newInstance()` 获取。

`Document parse(File f)` 将给定文件的内容解析为一个 XML 文档，并且返回一个新的 DOM Document 对象。  
**返回值** `org.w3c.dom.Document` 接口。表示整个 XML 文档。  
操作和JS很相似。  








#### dom4j

### XML 高级

#### XML 命名空间（XML Namespaces）

```XML
<h:table xmlns:h="http://www.w3.org/TR/html4/">
   <h:tr>
   <h:td>Apples</h:td>
   <h:td>Bananas</h:td>
   </h:tr>
</h:table>
```

#### XML CDATA

术语 CDATA 指的是不应由 XML 解析器进行解析的文本数据（Unparsed Character Data）  
CDATA 部分由 `"<![CDATA[" 开始，由 "]]>"` 结束：

```XML
<script>
<![CDATA[
function matchwo(a,b)
{
if (a < b && a < 0) then
  {
  return 1;
  }
else
  {
  return 0;
  }
}
]]>
</script>
```

#### 编码

`<?xml version="1.0" encoding="UTF-8"?>`

## 2. XSL - XSLT

XSL 指扩展样式表语言（EXtensible Stylesheet Language）。功能类似于 CSS 之于 HTML  

| 组成部分 | 功能                              |
| -------- | --------------------------------- |
| XSLT     | 一种用于转换 XML 文档的语言。     |
| XPath    | 一种用于在 XML 文档中导航的语言。 |
| XSL-FO   | 一种用于格式化 XML 文档的语言。   |

XSLT 是一种用于将 XML 文档转换为 XHTML 文档或其他 XML 文档的语言。  

### 实例研究 如何使用 XSLT 将 XML 转换为 XHTML

**原始文档：**  

```XML
<?xml version="1.0" encoding="ISO-8859-1"?>
<catalog>
  <cd>
    <title>Empire Burlesque</title>
    <artist>Bob Dylan</artist>
    <country>USA</country>
    <company>Columbia</company>
    <price>10.90</price>
    <year>1985</year>
  </cd>
</catalog>
```

**STEP 1：创建 XSL 样式表：**  

创建一个带有转换模板的 XSL 样式表（"cdcatalog.xsl"）：

```XML
<?xml version="1.0" encoding="ISO-8859-1"?>

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
  <body>
    <h2>My CD Collection</h2>
    <table border="1">
    <tr bgcolor="#9acd32">
      <th align="left">Title</th>
      <th align="left">Artist</th>
    </tr>
    <xsl:for-each select="catalog/cd">
    <tr>
      <td><xsl:value-of select="title"/></td>
      <td><xsl:value-of select="artist"/></td>
    </tr>
    </xsl:for-each>
    </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```

**STEP 2：把 XSL 样式表链接到 XML 文档：**  

在第二行添加以下内容。

```XML
<?xml-stylesheet type="text/xsl" href="cdcatalog.xsl"?>
```

### 说明

`<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`  
定义此文档是一个 XSLT **样式表**文档（连同版本号和 XSLT 命名空间属性）。

`<xsl:template match="/">`  
用于构建**模板**，match 表示应用范围，`/` 表示整篇文档。  

`<xsl:value-of select="title"/>`  
取标签内的值  

`<xsl:for-each select="catalog/cd">`  
标签内循环  

`<xsl:sort select="artist"/>`  
写在循环内，对结果根据指定标签排序。

`<xsl:if test="expression">`  
条件语句。  
例：`<xsl:if test="price &gt; 10">`  

`<xsl:choose>`  
多重条件测试。

```XML
<xsl:choose>
  <xsl:when test="expression">
    ... 输出 ...
  </xsl:when>
  <xsl:otherwise>
    ... 输出 ....
  </xsl:otherwise>
</xsl:choose>
```

`<xsl:apply-templates>`  
应用模板  

```XML
<xsl:template match="cd">
  <p>
    <xsl:apply-templates select="title"/>
    <xsl:apply-templates select="artist"/>
  </p>
</xsl:template>
<xsl:template match="title"></xsl:template>
<xsl:template match="artist"></xsl:template>
```

## 3. XSL - XPath

XPath 是一门在 XML 文档中查找信息的语言。XPath 可用来在 XML 文档中对元素和属性进行遍历。  

### XPath 节点

在 XPath 中，有七种类型的节点：**元素**、**属性**、**文本**、命名空间、处理指令、注释以及**文档节点（或称为根节点）**。

五种关系：父（Parent），子（Children），同胞（Sibling），先辈（Ancestor），后代（Descendant）。  

### XPath 语法

**元素选择：**  

| 表达式     | 描述                     |
| ---------- | ------------------------ |
| `nodename` | 选取此节点的所有子节点。 |
| `/`        | 从根节点选取。           |
| `//`       | 选取所有同名元素         |
| `.`        | 选取当前节点。           |
| `..`       | 选取当前节点的父节点。   |
| `@`        | 选取属性。               |

**谓语（Predicates）：**  
谓语用方括号标出。`/bookstore/book[1]` 其中 1 是谓语，表示第一个元素。  

| 谓语           | 意义                    |
| -------------- | ----------------------- |
| [1]            | 第一个元素              |
| [last()]       | 最后一个元素            |
| [last()-1]     | 倒数第二个元素          |
| [position()<3] | 前两个元素              |
| [@lang]        | 带lang属性的元素        |
| [@lang='eng']  | lang属性为eng的元素     |
| [price>35.00]  | 子元素price大于35的元素 |

**通配符：**  

| 通配符 | 描述                 |
| ------ | -------------------- |
| *      | 匹配任何元素节点。   |
| @*     | 匹配任何属性节点。   |
| node() | 匹配任何类型的节点。 |

**路径或**  
表示多个路径，用 `|` 表示

### XPath Axes（轴）

从当前节点定位到其他节点。  

**步：** `轴名称::节点测试[谓语]`  

### XPath 运算符

## 4. XSL-FO

XSL-FO 用于格式化供输出的 XML 数据。  

XSL-FO 文档存储在以 `.fo` 或 `.fob` 为后缀的文件中。以 `.xml` 为后缀存储的 XSL-FO 文档也很常见，这样做的话可以使 XSL-FO 文档更易被 XML 编辑器存取。  

### XSL-FO 文档

XSL-FO 文档是带有输出信息的 XML 文件。  

```XML
<?xml version="1.0" encoding="ISO-8859-1"?>

<fo:root xmlns:fo="http://www.w3.org/1999/XSL/Format">

<fo:layout-master-set>
  <fo:simple-page-master master-name="A4">
    <!-- Page template goes here -->
  </fo:simple-page-master>
</fo:layout-master-set>

<fo:page-sequence master-reference="A4">
  <!-- Page content goes here -->
</fo:page-sequence>

</fo:root>
```

`<fo:root>` 根元素，命名空间  

`<fo:layout-master-set>` 元素含有一个或多个页面模板  

`<fo:simple-page-master>` 元素包含一个单一的页面模板。每个模板须有一个唯一的名称(master-name)  

`<fo:page-sequence>` 元素可描述页面的内容。master-reference 属性使用相同的名称来引用 simple-page-master 模板  

### XSL-FO 区域

XSL-FO 使用矩形框（区域）来显示输出。  

- Pages（页面）
- Regions（区）
- Block areas（块区域）
- Line areas（行区域）
- Inline areas（行内区域）

### XSL-FO 输出

```XML
<fo:page-sequence>
  <fo:flow flow-name="xsl-region-body">
    <fo:block>
      <!-- Output goes here -->
    </fo:block>
  </fo:flow>
</fo:page-sequence>
```

> fo:page-sequence -> fo:flow -> fo:block

### XSL-FO 流

XSL-FO 页面使用来自 `<fo:flow>` 元素的数据进行填充。  

### XSL-FO 页面

XSL-FO 使用名为 "Page Masters" 的页面模板来定义页面的布局。  

### XSL-FO Blocks（块）

XSL-FO 的输出位于块区域中。  

### XSL-FO 列表

XSL-FO 使用列表块（List Block）来定义列表。  

### XSL-FO 表格

XSL-FO 使用 `<fo:table-and-caption>` 元素来定义表格。  

### XSL-FO 与 XSLT

XSL-FO 与 XSLT 可彼此互助。  

## 5. XQuery

解释 XQuery 的最佳方式是：XQuery 相对于 XML，等同于 SQL 相对于数据库。  

## 6. XLink 和 XPointer

XLink 定义在 XML 文档中创建超级链接的标准方法。  
XPointer 允许这些超级链接指向 XML 文档中的更多具体部分（片断）。  

## 7. DTD 和 Schema

DTD（文档类型定义）的作用是定义 XML 文档的合法构建模块。每一个 XML 文件均可携带一个有关其自身格式的描述。  

XML Schema 是基于 XML 的 DTD 替代者。  

### DTD 快速上手

- 创建 `.dtd` 文件
- 有几个元素，在DTD中写几个`<!ELEMENT>`
- 判断简单/复杂元素
  - 复杂元素：<!ELEMENT 元素名称 (item1, item2)>
  - 简单元素：<!ELEMENT 元素名称 (#PCDATA)>
- 在 XML 中引入 DTD 文件 `<!DOCTYPE persion SYSTEM "./demo.dtd">`

**结合方式：**  

1. 内部引用 `<!DOCTYPE 根元素 [内容]>`
2. 外部引用 `<!DOCTYPE 根元素 SYSTEM "路径/文件.dtd">`
3. 网络引用 `<!DOCTYPE 根元素 PUBLIC "DTD名称" "URL">`
     - 框架 struts2 使用的配置文件。

**语法：**  
`<!ELEMENT 元素名 约束>`  

- 简单元素
  - `(#PCDATA)` 文本
  - EMPTY 空
  - ANY 任意
- 复杂元素
  - `(子元素1, 子元素2)`
  - `子元素+` 一个或多个
  - `子元素*` 没有或多个
  - `子元素?` 没有或一个
  - `,` 出现顺序
  - `|` 出现任意一个，枚举

**属性：**  

```XML
<!ATTLIST 元素名
    属性名称 属性类型 属性约束
>
```  

> **属性类型**  
> CDATA 文本，可添加默认值，后面跟字符串即可  
> ENUMERATED 枚举，直接用 `(v1|v2|v3)` 列举  
> ID 值不可重复  
>
> **属性约束**  
> #REQUIRED 属性必须出现  
> #IMPLIED 属性可有可无  
> #FIXED 属性值固定 `#FIXED "属性值"`  

**实体：**  
`<!ENTITY 实体名 "文本">`  
调用
`<name>&实体名;</name>`  

### Schema 快速上手

- DTD加强版，且符合XML语法。
- 一个XML可以有多个Schema，使用命名空间区分。
- 更多的数据类型，比如整数。

**创建：**  

1. 创建一个Schema文件，扩展名是 `.xsd`  
   - 根节点 `<schema>`

## 8. XML DOM

## 9. XForms

XForms 是下一代的 HTML 表单。
XForms 使用 XML 来创建 web 上的输入表单。
