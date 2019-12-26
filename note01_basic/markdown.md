# 如何写 .md 文件

[top]: haha

<a href="https://git-scm.com/doc" target="_blank">markdown 官方基本教程</a><br />
<a href="https://guides.github.com/features/mastering-markdown/#GitHub-flavored-markdown" target="_blank">GitHub 的 markdown 教程</a>包括GFM<br />
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

## 注释

使用

```markdown
[^_^]:
    看不到我，看不到我，看不到我
[>_<]:
    看不到我，看不到我，看不到我
```

[^_^]:
    看不到我，看不到我，看不到我
[>_<]:
    看不到我，看不到我，看不到我
    
可注释本行和下一行，重要的是方括号和冒号，括号内些什么无所谓的

[top](#top)










## 图片

```
![说明](图片地址)
```

## 链接/跳转

```
[说明](地址)
[说明](#本文档内任一标题/本页任一元素的id)
```

## 字体

两个星号粗体 一个星号斜体

```
**bold**
*italic*
```

**bold**  
*italic*  

## 表格

```
| col 1 | col 2 | col 3 |
|-------|:-----:|------:|
| left  | mid   | right |
```

| col 1 | col 2 | col 3 |
|-------|:-----:|------:|
| left  | mid   | right |

## 行内代码

反引号  
表示语法里出现的符号**一定要用这个**  

```
`#include <stdio.h>`
```

`#include <stdio.h>`

## 代码块

三对反引号  
上面都这样写的。。。  

## 分割线

三个星号

```
***
```

***

