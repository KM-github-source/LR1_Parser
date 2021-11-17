# LR1_Parser
基于LR1的语法分析器
**
一、实验内容及需求分析**

**1.1. 实验内容**

本实验要求根据LR(1)分析方法，编写一个类C语言的LR(1)语法分析程序，完成对包含过程调用的类C示例程序的词法和语法分析。

**1.2. 程序功能**

本程序使用LR(1)分析方法编写，支持输入自定义文法，可以自动生成语法分析程序。

向本程序输入已知文法的产生式以及源程序，本程序负责进行词法分析和语法分析，并输出语法分析结果，包括：

1.	是否通过语法分析

2.	若通过语法分析，则还要输出源程序的规约过程和语法树

3.	若无法通过语法分析，输出报错信息以及出错位置

**1.3. 输入信息**

本程序的输入分为两部分，分别是类C语言文法产生式和源程序。该两部分均以文件形式输入。

类C语言文法产生式的输入格式示例如下。基本形式为

产生式左部 -> 产生式右部1 右部2 ...

需要注意的是，->符号的两边、不同的右部符号之间都需要以空格隔开，便于程序一次读入一个完整的文法符号。
 
本程序对源程序的格式无要求，并且支持各种类型的浮点数。

是否支持过程调用取决于输入的文法产生式。示例输入支持过程调用。

**二、项目总体设计**

**项目总体设计说明**

整个项目采用LR(1)分析方法进行设计，分为词法分析和语法分析两大部分。

在词法分析部分，程序读入源程序文件，并按照词法规则对源程序进行整理，使得语法分析器可以更方便地处理输入串。

语法分析部分，程序首先读入文法产生式，由产生式构造出对应的ACTION表和GOTO表；然后每当语法分析器需要读输入串时，就去调用词法分析器相应的接口，获得一个输入符号，并根据LR(1)分析表进行相应移进、归约、接受、报错动作，直到源程序分析完毕或者出现错误为止。
