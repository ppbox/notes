# 1 vim基础

## 1.1 快速移动

### 编辑模式下的快速删除 

下面几个快捷键除了vim中可以使用，在终端中也可以使用

- ctrl + h: 删除前一个字符
- ctrl + w: 删除前一个单词
- ctrl + u: 删除当前光标到行首

### 快速切换insert和normal模式

- 快速从insert模式切换到normal模式: 使用ctrl+[可以快速切换
- 快速从normal模式切换到insert模式: 使用gi可以快速切换到上次编辑的地方并进入插入模式

### vim快速移动大法索

#### 单词移动

- w/W: 移动到下一个word/WORD开头
- e/E: 移动到当前单词尾
- b/B: 移动到上一个word/WORD开头

> word指以非空白符分割的单词，WORD指以空白符分割的单词。如word-settings是两个words，却是一个WORD

#### 行内移动

行间搜索移动: 同一行快速移动的方式实际上是搜索一个字符并且快速移动到该字符

- 使用f{char}可以快速移动到char字符上
- 如果第一次没有搜索到，分号移动到下一个匹配的字符，逗号则移动到上一个匹配的字符
- F则搜索当前光标前面的匹配字符

#### 水平移动

- 0: 移动到行首的第一个字符
- $: 移动到行尾
- ^: 移动到第一个非空白字符
- g\_: 移动到行尾的非空白字符

#### 页面移动

- gg: 移动到文件开头
- G: 移动到文件结尾
- H/M/L: 移动到屏幕的Head，Middle和Lower
- Ctrl+u，Ctrl+f: 上下翻页
- zz: 把当前光标所在行移动到屏幕中间

## 1.2 快速删改查

### d相关

**d{char}**
快速删除到{char}字符所在的位置，但是不包括char

**d$**
删除到行尾，这行还保留

### r s c (replace, substitude, change)

**r{char}**
在normal模式下快速把光标所在字符改为char

**s**
删除当前字符，并进入插入模式。同时s也可以搭配数字使用，如4s表示删除4个字符并进入插入模式。还有大S会删除当前行，并进入插入模式。

**c**
在d的基础上，删除完后再进入插入模式。（最常用）

### 快速查找

- 用/或?进行前向或反向搜索
- n/N跳转到下一个或上一个匹配
- *或#进行光标所在当前当前的前向和反向的匹配

### 替换

substitute命令允许我们查找并替换文本，支持正则表达式

```
:[range] s/{pattern}/{string}/[flags]
```

- range：表示范围，比如:10,20，替换10-20行之间，%则表示全本
- pattern：表示模式
- string：表示替换后的文本

flags的常用标志：

- g：全局范围内执行
- c：确认confirm，在替换时会提示确认
- n：报告匹配的词数而不替换

## 1.3 vim多文件操作

- buffer：打开文件的内存缓冲区
- window：buffer可视化的分割区
- tab：组织多个窗口为一个工作区

### buffer

使用buffer可以很方便的切换文件：`:ls`列出当前缓冲区，然后用`:b n`跳转到第n个缓冲区

### window

:sp水平分割，:vs垂直分割。ctrl+w+hjkl方向键可以移动当前所操作的窗口。sp和vs后面加文件名，可以打开其他文件。

重排窗口：ctrl+w+=，使所有窗口等宽、等高

### tab

vim的tab是一系列窗口的容器。tab使用的不多

