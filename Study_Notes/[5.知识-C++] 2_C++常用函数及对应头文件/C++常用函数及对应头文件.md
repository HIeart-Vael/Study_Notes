# C++常用函数及对应头文件

C++参考手册：[cppreference.com](https://zh.cppreference.com/)

[TOC]
- [C++常用函数及对应头文件](#c常用函数及对应头文件)
  - [字符串库](#字符串库)
    - [字符检查&大小写转换：](#字符检查大小写转换)
      - [头文件：\<cctype\>](#头文件cctype)
      - [头文件：\<string\>](#头文件string)
      - [头文件：\<cstring\>](#头文件cstring)

## 字符串库

### 字符检查&大小写转换：

#### 头文件：\<cctype\>

| 函数    | 描述                       | 使用                 |
| ------- | -------------------------- | -------------------- |
| isalnum | 检查字母是否为字母或数字   | int isalnum( int c ) |
| isalpha | 检查字母是否为字母         | int isalpha( int c   |
| isdigit | 检查字母是否为数字         | int isdigit( int c ) |
| islower | 检查字母是否为小写         | int islower( int c ) |
| isupper | 检查字母是否为大写         | int isupper( int c ) |
| isspace | 检查字符是否为空白间隔字符 | int isspace( int c ) |
| tolower | 转换字符为小写             | int tolower( int c ) |
| toupper | 转换字符为大写             | int toupper( int c ) |

- is函数：若字符 c 为判断对应字符，则为非零值，否则为 0 。
- to函数： 若字符 c 有相对应的大小写字母，则该函数返回 c 的大小写字母，否则 c 保持不变。
- 返回值是一个可被隐式转换为 char 类型的 int 值。



#### 头文件：\<string\>

| 函数      | 描述                               | 使用                         | 返回值                     |
| --------- | ---------------------------------- | ---------------------------- | -------------------------- |
| getline   | 从输入流读取字符并将它们放进string | getline(input, str, delim\*) | input                      |
| to_string | 转换整数或浮点值为string           | to_string( value )           | 一个包含转换后值的字符串   |
| stoi      | 转换字符串为有符号整数             | stoi( str, pos\*, base\* )   | 对应 str 内容的整数值      |
| size      | 返回字符串的长度                   | str.size()                   | 字符串str的长度            |
| empty     | 判断容器是否为空                   | empty( str )                 | 返回布尔值，空为1，不空为0 |

- input -  获取数据来源的流（如cin）
- str - 放置数据的目标 string
- delim - 分隔字符
- value -  需要转换的数值
- pos - 存储已处理字符数的整数的地址（指针）
- base - 数的底



#### 头文件：\<cstring\>

| 函数 | 描述 | 使用 | 返回值 |
| ---- | ---- | ---- | ------ |
|      |      |      |        |
|      |      |      |        |
|      |      |      |        |
|      |      |      |        |

