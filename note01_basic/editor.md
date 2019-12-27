# 文本编辑器的选择与使用

## 目录 <!-- omit in toc -->

- [字体](#%e5%ad%97%e4%bd%93)
- [vim/gvim](#vimgvim)
- [emacs](#emacs)
- [Visual Studio Code](#visual-studio-code)
  - [1. VS Code 在用的插件](#1-vs-code-%e5%9c%a8%e7%94%a8%e7%9a%84%e6%8f%92%e4%bb%b6)
    - [中文语言包](#%e4%b8%ad%e6%96%87%e8%af%ad%e8%a8%80%e5%8c%85)
    - [辅助](#%e8%be%85%e5%8a%a9)
    - [Markdown 相关](#markdown-%e7%9b%b8%e5%85%b3)
  - [2. 设置](#2-%e8%ae%be%e7%bd%ae)
  - [3. 常规使用](#3-%e5%b8%b8%e8%a7%84%e4%bd%bf%e7%94%a8)
    - [多重选择](#%e5%a4%9a%e9%87%8d%e9%80%89%e6%8b%a9)
  - [4. Markdown相关](#4-markdown%e7%9b%b8%e5%85%b3)
    - [Markdown All in One 根据标题生成/更新目录](#markdown-all-in-one-%e6%a0%b9%e6%8d%ae%e6%a0%87%e9%a2%98%e7%94%9f%e6%88%90%e6%9b%b4%e6%96%b0%e7%9b%ae%e5%bd%95)
    - [Markdown All in One 快捷键](#markdown-all-in-one-%e5%bf%ab%e6%8d%b7%e9%94%ae)

## 字体

写代码时等宽字体是很重要的。这是一个陈述句，表示客观事实。  
不信？看看国内某些教科书的排版吧。  
还不信？打开 word 复制以下字符。  

```普通文本
oO0IlT7L1|!！[]-——一~`'‘‘"“”,，.?？
```

字体要求，西文一倍宽度，中日韩文字符二倍宽度，方便列编辑。相似符号显示有辨识度，防止看错。

- 文泉驿等宽正黑  
  很早就在用的字体，虽然不一定好看，但至少能用，多年下来已经习惯了。没有粗体，字重全靠渲染，可能出现字符显示不全的问题Windows 控制台和 Windows PowerShell 不认为这是等宽字体，无法使用。Ubuntu 终端似乎也不能使用，不知道为什么。  
  <a href="http://wenq.org/wqy2/index.cgi" target="_blank">官方网站</a>  
  <a href="http://wenq.org/wqy2/index.cgi?Download#ZenHei_Stable" target="_blank">字体下载</a>  
  > 1. 文泉驿等宽正黑已包括在文泉驿正黑里面  
  > 2. Linux 可使用命令行下载  
  >    Ubuntu `sudo apt install ttf-wqy-zenhei`  
  >    Fedora `sudo dnf install wqy-zenhei-fonts`  
  >    时间过久包名可能改变，善用包管理器的补全功能（输一部分包名，按两下 `Tab` 可获得可安装软件列表)

- 等距更纱黑体  
  这次的新发现，英简繁日韩文都有，系统均可识别，尚未发现问题。
  [项目地址](https://github.com/be5invis/Sarasa-Gothic)  
  Win10 可使用应用商店安装，搜索“更纱黑体”。其他系统请使用 npm 包管理器  

[返回](#文本编辑器的选择与使用)

## vim/gvim

放在前面以示信仰，内容太多有空再写。
希望有个支持 vim 的中文输入法，检测 vim 状态，命令模式和末行模式下输入英文。  

[返回](#文本编辑器的选择与使用)

## emacs

不会用，但一定要写上，因为这玩意儿牛逼。  

[返回](#文本编辑器的选择与使用)

## Visual Studio Code

感觉微软越来越牛逼，谷歌越来越傻逼  
附[官方下载](https://code.visualstudio.com/)  

[返回](#文本编辑器的选择与使用)

### 1. VS Code 在用的插件

这玩意儿会根据你写的文档为你推荐插件，不过还是记录下在用的插件。

#### 中文语言包

> Chinese (Simplified) Language Pack for Visual Studio Code

#### 辅助

查看二进制文件（只读）  
> hexdump for VSCode

Vim 插件
> Vim

#### Markdown 相关

你需要的大部分功能
> Markdown All in One

GitHub 风格的预览
> Markdown Preview Github Styling

规范代码风格
> markdownlint

[返回](#文本编辑器的选择与使用)

### 2. 设置

`Ctrl+Shift+P` 打开命令面板，一般使用 `用户设置` ，对某一语言单独设置使用 `语言特定的设置` ，插件设置在用户设置里面。所有设置均可通过修改配置文件来实现。

个人设置 `setting.json`

```json
{
    "git.autofetch": true,
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\wsl.exe",
    "editor.fontFamily": "文泉驿等宽正黑",
    "editor.fontSize": 17,
    "terminal.integrated.fontSize": 18,
    "extensions.ignoreRecommendations": true,
    "terminal.integrated.fontFamily": "等距更纱黑体 T SC",
    "[markdown]": {
        "editor.tabSize": 2
    },
    "editor.multiCursorModifier": "alt",
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "markdown.extension.toc.levels": "2..6"
}
```

项目根目录下建立 `.markdownlint.json` 对 markdownlint 插件设置

```json
{
    "MD013": false,
    "MD033": false
}
```

MD013 是对每行长度限制  
MD033 是禁用 HTML 代码

[返回](#文本编辑器的选择与使用)

### 3. 常规使用

#### 多重选择

选择同样元素 `Ctrl+D` 选择上一个 `Ctrl+U`  
块选择 `Alt+Shift` 或鼠标中键拖动
连续选择 `Ctrl+Shift`

### 4. Markdown相关

#### Markdown All in One 根据标题生成/更新目录

```VS Code
Markdown All in One: Create Table of Contents
Markdown All in One: Update Table of Contents
```

不需要在目录中显示的标题，在行尾加上 `<!-- omit in toc -->`

#### Markdown All in One 快捷键

|        快捷键         |               功能                |
| :-------------------: | :-------------------------------: |
|       `Ctrl+B`        |               加粗                |
|       `Ctrl+I`        |               倾斜                |
| `Ctrl+Shift`+`[`或`]` |             标题等级              |
|       `Ctrl+M`        |             数学公式              |
|        `Alt+C`        | `- [ ] Uncheck` <-> `- [x] Check` |
|     `Alt+Shift+F`     |            表格格式化             |
|  `Ctrl+K` 然后按 `V`  |               预览                |
