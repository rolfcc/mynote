# 如何写 .md 文件

- [如何写 .md 文件](#%e5%a6%82%e4%bd%95%e5%86%99-md-%e6%96%87%e4%bb%b6)
  - [参考网站](#%e5%8f%82%e8%80%83%e7%bd%91%e7%ab%99)
  - [markdown 通用语法](#markdown-%e9%80%9a%e7%94%a8%e8%af%ad%e6%b3%95)
    - [1. 标题](#1-%e6%a0%87%e9%a2%98)
    - [2. 引用](#2-%e5%bc%95%e7%94%a8)
    - [3. 列表](#3-%e5%88%97%e8%a1%a8)
      - [无序列表](#%e6%97%a0%e5%ba%8f%e5%88%97%e8%a1%a8)
      - [有序列表](#%e6%9c%89%e5%ba%8f%e5%88%97%e8%a1%a8)
    - [4. 代码](#4-%e4%bb%a3%e7%a0%81)
    - [5. 分割线](#5-%e5%88%86%e5%89%b2%e7%ba%bf)
    - [6. 链接](#6-%e9%93%be%e6%8e%a5)
    - [7. 强调](#7-%e5%bc%ba%e8%b0%83)
    - [8. 图片](#8-%e5%9b%be%e7%89%87)
    - [9. 转义字符](#9-%e8%bd%ac%e4%b9%89%e5%ad%97%e7%ac%a6)
    - [10. 自动链接](#10-%e8%87%aa%e5%8a%a8%e9%93%be%e6%8e%a5)
  - [GFM (GitHub Flavored Markdown)](#gfm-github-flavored-markdown)
    - [11. 高亮语法](#11-%e9%ab%98%e4%ba%ae%e8%af%ad%e6%b3%95)
    - [12. 任务表](#12-%e4%bb%bb%e5%8a%a1%e8%a1%a8)
    - [13. 表格](#13-%e8%a1%a8%e6%a0%bc)
    - [14. @用户](#14-%e7%94%a8%e6%88%b7)
    - [15. 自动为网址添加链接](#15-%e8%87%aa%e5%8a%a8%e4%b8%ba%e7%bd%91%e5%9d%80%e6%b7%bb%e5%8a%a0%e9%93%be%e6%8e%a5)
    - [16. 删除线](#16-%e5%88%a0%e9%99%a4%e7%ba%bf)
  - [注释 &amp; 做锚](#%e6%b3%a8%e9%87%8a-amp-%e5%81%9a%e9%94%9a)

## 参考网站

<a href="https://git-scm.com/doc" target="_blank">markdown 官方基本教程</a><br />
<a href="https://guides.github.com/features/mastering-markdown/#GitHub-flavored-markdown" target="_blank">GitHub 的 markdown 教程（包括GFM）</a><br />
<a href="https://help.github.com/cn/github/writing-on-github" target="_blank">在 GitHub 上编写</a>

## markdown 通用语法

### 1. 标题

用1~6个 `#` 表示一到六级标题  
每个标题都是一个锚点，配合链接可实现页内跳转。

```markdown
# title 1
## title 2
### title 3
#### title 4
##### title 5
###### title 6
```

### 2. 引用

在前面加 `>` ，可嵌套

```markdown
> quote
> > quote 2
```

### 3. 列表

在前面加 `*` 或 `-` ，前面加两个空格表示下一级列表

#### 无序列表

子列表两个空格

```markdown
* item 1
  * subitem 1
* item 2
  1. subitem 2
* item 3
```

#### 有序列表

子列表要四个空格，其他地方不清楚，反正我本地是这样

```markdown
1. item 1
    * subitem 1
2. item 2
    1. subitem 2
3. item 3
```

### 4. 代码

原生 markdown 建立代码块使用4个空格或一个 `Tab`

```markdown
普通段落

    代码区块
```

但一般使用三个 `` ` `` 且在中间有至少一个换行，需在第一行反引号后标注代码块使用语言。不换行无论有多少对反引号均为行内代码。三个及三个个以上反引号均可达到该效果，开始与结束只要输入相同个数的反引号即可。为了输入三个反引号，此处我用四个反引号表示代码块。

````markdown
```markdown
代码区块
```
````

行内代码

```markdown
`代码`
`` `代码` ``
```

### 5. 分割线

同一行三个及以上 `*` 或 `-`

```markdown
***
---
```

### 6. 链接

直接写链接的方法

```markdown
[描述](链接 "title 可选")
```

给链接定义 id 并在链接处引用 id 的方法，此种情况描述可用 id 代替。

```markdown
[描述][id]
[id][]

[id]: 链接 "title 可选"
```

参考式链接为的是让代码看起来与最终结果差不多，但是在没有新窗口打开的情况下，你要用 HTML 来实现该功能，那样看起来其实更乱。。。

页内跳转

```markdown
# title1
## title2

[title1](#title1)
[title2](#title2)
```

### 7. 强调

用 `*` 或 `_` 将需要强调的文字框起来，一对为斜体，两对是加粗。

```markdown
*斜体*
**加粗**
```

### 8. 图片

与链接类似

```markdown
![描述](图片地址 "title 可选")
```

```markdown
![描述](id)

[id]: 图片地址 "title 可选"
```

### 9. 转义字符

使用 `\` 插入普通符号

```普通文本
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```

### 10. 自动链接

文字同链接地址一样，使用 `<` 和 `>` 括起来

```markdown
<地址>
<邮箱>
```

## GFM (GitHub Flavored Markdown)

### 11. 高亮语法

其实上面写过了，注意标注语言，也可以随便写点别的  
如果是可识别的语言，可以高亮语法的。

````markdown
```C
#include <stdio.h>

int main() {
    printf("hello, world");
    return 0;
}
```
````

五颜六色，跟在自己的编辑器上似的：

```C
#include <stdio.h>

int main() {
    printf("hello, world");
    return 0;
}
```

### 12. 任务表

有一个可打勾的框

```markdown
- [ ] 未完成
- [x] 已完成
```

显示如下：

- [ ] 未完成
- [x] 已完成

### 13. 表格

冒号调整对齐方式，注意第一行默认居中

```markdown
| col 1 | col 2 | col 3 |
|-------|:-----:|------:|
| left  | mid   | right |
```

显示如下：

| col 1 | col 2 | col 3 |
|-------|:-----:|------:|
| left  | mid   | right |

逼死强迫症的写法

```markdown
Header1 | Header2
-------------| -
1 | 000000000000002
00003 | 4
```

其实没差，但是生理上无法接受

Header1 | Header2
------------- | -
1 | 000000000000002
00003 | 4

### 14. @用户

等我有对象以后可以试试

### 15. 自动为网址添加链接

所以 `<URL>` 这条语法是没有必要的

### 16. 删除线

```markdown
~~数据删除~~
```

## 注释 & 做锚

使用参考式链接不显示的特性给文本做注释，或者为页内跳转做锚点。

```普通文本
[^_^]:
    看不到我，看不到我，看不到我
[>_<]:
    看不到我，看不到我，看不到我
```

示例，看不到就对了

[^_^]:
    看不到我，看不到我，看不到我
[>_<]:
    看不到我，看不到我，看不到我

其实使用 HTML 的注释才是标准做法，不过这样又不是不能用。

```markdown
<!-- 注释 -->
```
