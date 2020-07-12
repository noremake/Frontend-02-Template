学习笔记

JavaScript 语言通识

- 语言按语法分类

  - 非形式语言
    - 中文，英文
  - 形式语言（乔姆斯基谱系）
    - 0型——无限制文法
      - 1型——上下文相关文法
        - 2型——上下文无关文法
          - 3型——正则文法

- 产生式（BNF）—— 巴科思-诺尔范式

  - 用尖括号括起来的名称来表示语法结构名

  - 语法结构分成基础结构和需要用其他语法结构定义的复合结构

    - 基础结构称终结符——Terminal Symbol
    - 复合结构称非终结符——Nonterminal Symbol

  - 引号和中间的字符表示终结符——字符串

  - 可以有括号

  - \* 表示重复多次

  - | 表示或

  - \+ 表示至少一次

    ![img](https://img.mubu.com/document_image/0c748fd3-2363-4ed3-931b-d16c534c61d3-5909199.jpg)

    ![img](https://img.mubu.com/document_image/12962786-88e0-4b5d-9033-5f2ed661ac1f-5909199.jpg)

- 通过产生式理解乔姆斯基谱系

  - 0型 无限制文法
    - ?::=?
  - 1型 上下文相关文法
    - ?<A>?::=?<B>?
  - 2型 上下文无关文法
    - <A>::=?
  - 3型 正则文法
    - <A>::=<A>?

- 现代语言的特例

- 语言的分类

  - 形式语言—用途
    - 数据描述语言
      - JSON,HTML,SQL,CSS
    - 编程语言
      - C,C++,Java,C#,Python,Ruby,Perl,Lisp,T-SQL,Clojure,Haskell,JavaScript
  - 形式语言—表达方式
    - 声明式语言
      - JSON,HTML,XAML,SQL,CSS,Lisp,Clojure,Haskell
    - 命令型语言
      - C,C++,Java,C#,Python,Ruby,Perl

- 编程语言的性质

  - 图灵完备性
    - 命令式——图灵机
      - goto
      - if和while
    - 声明式——lambda
      - 递归
  - 动态与静态（类似于js与java变量的定义）
    - 动态
      - 在用户的设备/在线服务器上
      - 产品实际运行时
      - Runtime（运行时）
    - 静态
      - 在程序员的设备上
      - 产品开发时
      - Compiletime（编译时）
    - 类型系统
      - 动态类型系统与静态配型系统
        - 区分：在谁的电脑上能够保留下来
      - 强类型与弱类型
      - 复合类型
        - 结构体
        - 函数签名
        - 子类型
        - 泛型
          - 逆变
            - 凡是能用Function<Child>的地方，都能用Function<Parent>
          - 协变
            - 凡是能用Array<Parent>的地方，都能用Array<Child>

- 一般命令式编程语言

  - Atom
    - 字符串直接量
    - 数字直接量
  - Expression
    - Atom
    - Operator
    - Punctuator
  - Statement
    - Expression
    - Keyword
    - Punctuator
  - Structure
    - Function
    - Class
    - Process
    - Namespace
  - Program
    - program
      - 实际执行的代码
    - Module
      - 可复用的模块
    - Package
    - Library
  - 语法 --> 语义 --> 运行时

JavaScript 类型

- Number

  - Atom

    - Grammar
      - Literal
      - Variable
      - Keywords
      - Whitespace
      - Line Terminator
    - Runtime
      - Types
      - Execution Context

  - IEEE 754 Double Float （双精度浮点数），二进制表示

    ![img](https://img.mubu.com/document_image/d96bf702-4ec6-481f-a165-99573872c741-5909199.jpg)

    - Sign(1)——符号位
      - 1是 +，0是 -
    - Exponent(11)——指数位
      - 有偏移
      - 基本值：一个1，十个0开始
    - Fraction(52)——精度位

  - Float 把一个数字拆成指数和有效位数

    - 有效位数：精度

    - 指数：范围

      - 最大：十个1， 2的2048次方 - 1
      - 最小：2的-10次方

    - 精度位*指数位*2的指数次方

      - 有一个隐藏位，开头为1（没必要表示出来）

        ![img](https://img.mubu.com/document_image/d89fdb71-f1ac-461b-a4c8-e36bc39f17ca-5909199.jpg)

      - 最大：指数最大 * 52个1

      - 最小：1后面52倍，2的2的-10次方次方

  - DecimalLiteral （十进制）

    - 0
    - 0.
    - .2
    - 1e3

  - BinaryIntegerLiteral （二进制）

  - OctalIntegerLiteral （八进制）

  - HexIntegerLiteral （十六进制）

- String

  - Character（字符）

  - Code Point（码点）——表示 Character

  - Encoding（编码方式）

  - 字符集

    - ASCII（只照顾到英文）
      - 127个字符——26个大小写字母，还有各种制表符换行符
    - Unicode（联合编码集，全球）
      - 范围：000——FFFF
    - UCS
      - 范围：0000——FFFF
    - GB（和 Unicode 不兼容，省空间）
      - GB2312
      - GBK(GB13000)
      - GB18030
    - ISO-8859（和ASCII兼容，但8859内的互不兼容）
    - BIG5（台湾）

  - 编码方式

    - UTF

      ![img](https://img.mubu.com/document_image/f5eafeda-6346-48bf-bf30-73ad10d74397-5909199.jpg)

      - UTF8

        - 8个比特位，默认用一个字节表示一个字符
        - ASCII 编码方式必定是 UTF8 的编码方式，反过来不成立

      - UTF16

        - 16个比特位

      - “一”的码点

        ![img](https://img.mubu.com/document_image/9c581699-ee74-49c8-b369-db178004d881-5909199.jpg)

        - 实际编码 01001100
        - UTF8 中，掺入控制位才能把字符填下，黄色就是控制位，第一节有几个1，表示占几个字节（3个字节），后面都以 10 开头

  - Grammar

    - "abc"
    - 'abc'
    - `abc`

- Boolean

  - true
  - false

- Null & Undefined

  - 都表示控制
  - Null：已经存在
  - Undefined：表示还未被定义，全局变量，用void 0 代表 Undefined

- Object

  - 面向对象三要素
    - identifier
    - state
    - behavior
  - 归类
    - 可以有多个从属关系
  - 分类
    - 只有一个从属关系
  - 设计对象的状态和行为时，对象的行为必须是改变对象状态的——“行为改变状态”原则
  - 在JavaScript运行时，原生对象的描述方式非常简单，我们只需要关心原型和属性两个部分
  - JavaScript 是一个键值对，key有两种
    - 一种是 Symbol：Symbol 名即使一样，
    - 一种是 String
  - 数据属性——Data Property
    - [[value]]
    - writable
      - false时，“.”运算不能修改，但可以通过 define 修改
    - enumerable
    - configurable
  - 访问器属性——Accessor Property
    - get
    - set
    - enumerable
    - configurable
  - 原型机制
  - Object API/Grammar
    - {} . [] Object.defineProperty
    - Object.create/Object.setPrototypeOf/Object.getPrototypeOf
    - new/class/extends
    - new/function/prototype