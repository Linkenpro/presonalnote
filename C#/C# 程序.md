##### C# 程序结构

> 一个C# 程序主要包括以下部分：

- 命名空间声明（Namespace declaration）
- 一个 class
- Class 方法
- Class 属性
- 一个 Main 方法
- 语句（Statements）& 表达式（Expressions）
- 注释

> C# 文件的后缀为 **.cs**

```c#
/*using 关键字用于在程序中包含 System 命名空间，一个程序一般有多个 using 语句*/
using System;

/* namespace声明包含了一系列的类，HelloWorldApplication 命名空间包含了类HelloWorld*/
namespace HelloWorldApplication
{
   class HelloWorld
   {
      static void Main(string[] args)
      {
         /* 我的第一个 C# 程序*/
         Console.WriteLine("Hello World");
         /*防止程序从 Visual Studio .NET 启动时屏幕会快速运行并关闭*/
         Console.ReadKey();
      }
   }
}
```

> 注意

- C# 是大小写敏感的。
- 所有的语句和表达式必须以分号（;）结尾。
- 程序的执行从 Main 方法开始。
- 与 Java 不同的是，文件名可以不同于类的名称。

##### 编译 & 执行 C# 程序

如果您使用 Visual Studio.Net 编译和执行 C# 程序，请按下面的步骤进行：

- 启动 Visual Studio。
- 在菜单栏上，选择 File -> New -> Project。
- 从模板中选择 Visual C#，然后选择 Windows。
- 选择 Console Application。
- 为您的项目制定一个名称，然后点击 OK 按钮。
- 新项目会出现在解决方案资源管理器（Solution Explorer）中。
- 在代码编辑器（Code Editor）中编写代码。
- 点击 Run 按钮或者按下 F5 键来运行程序。会出现一个命令提示符窗口（Command Prompt window），显示 Hello World。

您也可以使用命令行代替 Visual Studio IDE 来编译 C# 程序：

- 打开一个文本编辑器，添加上面提到的代码。
- 保存文件为 **helloworld.cs**。
- 打开命令提示符工具，定位到文件所保存的目录。
- 键入 **csc helloworld.cs** 并按下 enter 键来编译代码。
- 如果代码没有错误，命令提示符会进入下一行，并生成 **helloworld.exe** 可执行文件。
- 接下来，键入 **helloworld** 来执行程序。
- 您将看到 "Hello World" 打印在屏幕上。

> 以 Rectangle（矩形）对象为例。它具有 length 和 width 属性。根据设计，它可能需要接受这些属性值、计算面积和显示细节

```c#
using System;
namespace RectangleApplication
{
    class Rectangle
    {
        // 成员变量
        double length;
        double width;
        public void Acceptdetails()
        {
            length = 4.5;    
            width = 3.5;
        }
        public double GetArea()
        {
            return length * width;
        }
        public void Display()
        {
            Console.WriteLine("Length: {0}", length);
            Console.WriteLine("Width: {0}", width);
            Console.WriteLine("Area: {0}", GetArea());
        }
    }
    
    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.Acceptdetails();
            r.Display();
            Console.ReadLine();
        }
    }
}
```

##### *using* 关键字

> 任何 C# 程序中的第一条语句都是

```c#
using System;
```

##### *class* 关键字

> **class** 关键字用于声明一个类。

##### C# 中的注释

- 单行注释——`//`
- 多行注释——`/*多行*/`

##### 成员变量

> 变量是类的属性或数据成员，用于存储数据

##### 成员函数

函数是一系列执行指定任务的语句。类的成员函数是在类内声明

##### 实例化一个类

在上面的程序中，类 *ExecuteRectangle* 是一个包含 *Main()* 方法和实例化 *Rectangle* 类的类。

##### 标识符

标识符是用来识别类、变量、函数或任何其它用户定义的项目。在 C# 中，类的命名必须遵循如下基本规则：

- 标识符必须以字母、下划线或 **@** 开头，后面可以跟一系列的字母、数字（ 0 - 9 ）、下划线（ _ ）、@。
- 标识符中的第一个字符不能是数字。
- 标识符必须不包含任何嵌入的空格或符号，比如 ? - +! # % ^ & * ( ) [ ] { } . ; : " ' / \。
- 标识符不能是 C# 关键字。除非它们有一个 @ 前缀。 例如，@if 是有效的标识符，但 if 不是，因为 if 是关键字。
- 标识符必须区分大小写。大写字母和小写字母被认为是不同的字母。
- 不能与C#的类库名称相同。

##### C# 关键字

关键字是 C# 编译器预定义的保留字，如果您想使用这些关键字作为标识符，可以在关键字前面加上 @ 字符作为前缀

| 关键字    |           |          |            |                        |                       |         |
| --------- | --------- | -------- | ---------- | ---------------------- | --------------------- | ------- |
| abstract  | as        | base     | bool       | break                  | byte                  | case    |
| catch     | char      | checked  | class      | const                  | continue              | decimal |
| default   | delegate  | do       | double     | else                   | enum                  | event   |
| explicit  | extern    | false    | finally    | fixed                  | float                 | for     |
| foreach   | goto      | if       | implicit   | in                     | in (generic modifier) | int     |
| interface | internal  | is       | lock       | long                   | namespace             | new     |
| null      | object    | operator | out        | out (generic modifier) | override              | params  |
| private   | protected | public   | readonly   | ref                    | return                | sbyte   |
| sealed    | short     | sizeof   | stackalloc | static                 | string                | struct  |
| switch    | this      | throw    | true       | try                    | typeof                | uint    |
| ulong     | unchecked | unsafe   | ushort     | using                  | virtual               | void    |
| volatile  | while     |          |            |                        |                       |         |

| **上下文关键字** |        |           |            |         |         |                |
| ---------------- | ------ | --------- | ---------- | ------- | ------- | -------------- |
| add              | alias  | ascending | descending | dynamic | from    | get            |
| global           | group  | into      | join       | let     | orderby | partial (type) |
| partial (method) | remove | select    | set        |         |         |                |

##### C# 数据类型

###### 1.值类型（Value types）

值类型变量可以直接分配给一个值，它们是从类 **System.ValueType** 中派生的，比如 **int、char、float**

| 类型    | 描述                                 | 范围                                                    | 默认值 |
| :------ | :----------------------------------- | :------------------------------------------------------ | :----- |
| bool    | 布尔值                               | True 或 False                                           | False  |
| byte    | 8 位无符号整数                       | 0 到 255                                                | 0      |
| char    | 16 位 Unicode 字符                   | U +0000 到 U +ffff                                      | '\0'   |
| decimal | 128 位精确的十进制值，28-29 有效位数 | (-7.9 x 1028 到 7.9 x 1028) / 100 到 28                 | 0.0M   |
| double  | 64 位双精度浮点型                    | (+/-)5.0 x 10-324 到 (+/-)1.7 x 10308                   | 0.0D   |
| float   | 32 位单精度浮点型                    | -3.4 x 1038 到 + 3.4 x 1038                             | 0.0F   |
| int     | 32 位有符号整数类型                  | -2,147,483,648 到 2,147,483,647                         | 0      |
| long    | 64 位有符号整数类型                  | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 | 0L     |
| sbyte   | 8 位有符号整数类型                   | -128 到 127                                             | 0      |
| short   | 16 位有符号整数类型                  | -32,768 到 32,767                                       | 0      |
| uint    | 32 位无符号整数类型                  | 0 到 4,294,967,295                                      | 0      |
| ulong   | 64 位无符号整数类型                  | 0 到 18,446,744,073,709,551,615                         | 0      |
| ushort  | 16 位无符号整数类型                  | 0 到 65,535                                             | 0      |

> 如需得到一个类型或一个变量在特定平台上的准确尺寸，可以使用 **sizeof** 方法。表达式 *sizeof(type)* 产生以字节为单位存储对象或类型的存储尺寸

```c#
using System;

namespace DataTypeApplication
{
   class Program
   {
      static void Main(string[] args)
      {
         Console.WriteLine("Size of int: {0}", sizeof(int));
         Console.ReadLine();
      }
   }
}
```

