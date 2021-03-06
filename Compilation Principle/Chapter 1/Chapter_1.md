## Chapter 1 绪论

### 1.1 什么是编译

#### 计算机程序设计语言及编译

- 高级语言
  - 类似于数字定义或自然语言的简洁形式
  - 举例： x=2
  - 编写效率高
- 汇编语言
  - 引入助记符
  - 举例：指令：MOV X,2 
  - 依赖于特定机器
  - 编写效率较低
- 机器语言
  - 可以被计算机直接理解
  - 举例：指令：C706 0000 0002 表示将数值2存放到地址0000
  - 与人类表达习惯很不同
  - 难记忆
  - 难编写、难阅读
  - 易写错

汇编：将汇编语言翻译成机器语言的过程

编译：将高级语言（源语言）翻译成汇编语言或机器语言（目标语言）的过程。

#### 编译器在语言处理系统中的位置

- 源程序
  - 预处理器：把存储在不同文件中的源程序聚合在一起，并把被称为宏的编写语句转换位原始语句。
- 经过预处理的源程序
- 编译器
- 汇编语言程序
- 汇编器
  - 可重定位的机器代码：可重定位：在内存中存放的起始位置不是固定的
  - 起始位置+相对位置=绝对位置
- 连接器/加载器
  - 加载器：修改可重定位地址，将修改后的指令和数据放到内存中适当的位置
  - 连接器：将多个可重定位的机器代码问题链接到一起；解决外部内存地址问题。
- 目标机器代码

### 1.2 编译系统的结构

#### 翻译的举例

- 第一步：分析源语言   
  - 词法分析
  - 语法分析
  - 语义分析
- 第二部：生成目标语言

#### 结构

- 分析部分/前端：与源语言相关
  - 词法分析器
  - 语法分析器
  - 语义分析器
  - 中间代码生成器
- 桥梁部分
  - 机器无关代码优化器
- 综合部分/后端：与目标语言相关
  - 目标代码生成器
  - 机器相关代码优化器

### 1.3 词法分析概述

#### 主要任务

- 从左到右进行逐行扫描源程序的字符，识别出各个单词，确定单词的类型，将识别出的单词转换成同一的机内表示------词法单元（token）形式。
- token:<种别码，属性值>
- 类型：
  - 关键字 一词一码
  - 标识符 多词一码
  - 常量     一型一码
  - 运算符 一词一码
  - 界限符 一词一码

### 1-4 语法分析概述

#### 主要任务

- 从词法分析器输出的token序列中识别出各类短语，并构造语法分析树。

#### 举例：变量声明语句的分析树

- 文法：
  - <D>==><T><IDS>;
  - <T>==>int|real|char|bool;
  - <IDS>==>id|<IDS>,id

### 1.5 语义分析概述

#### 主要任务

- 收集标识符的属性信息
  - 种属
    - 简单变量、复合变量（数组、记录）、过程
  - 类型
    - 整型、布尔型
  - 存储位置、长度
  - 值
  - 作用域
  - 参数和返回值信息
- 语义检查
  - 变量或过程未经声明就使用
  - 变量或过程名重复声明
  - 运算分量类型不匹配‘
  - 操作符与操作数之间的类型不匹配
    - 数组下标不是整数
    - 堆非数组变量使用数组访问
    - 堆非过程名使用过程调用
    - ……

### 1.6 中间代码生成和编译器后端概述

#### 常用的中间表示形式

- 三地址码
  - 三地址码由类似于汇编语言的指令序列组成，每个指令最多由三个操作数。
  - 常用的三地址指令
  - 三地址指令的表示
    - 四元式
- 语法结构树/语法

#### 目标代码生成器

- 目标代码生成重要任务为程序中的变量合理分配寄存器

#### 代码优化

- 为改进代码所进行的等价程序变量，使其运行得更快一些，占用空间更少一些。