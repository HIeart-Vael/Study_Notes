# Markdown生成TOC：

以下方法均支持中文标题。

## 更正——（方法更简单且通用）：

**TOC格式：`[Content](#URL)`**

**URL对大小写及标点不敏感，使用的时候直接去掉URL中的标点即可。**

​	**e.g. `[更正——（方法更简单且通用）：](#更正方法更简单且通用)` —— [更正——（方法更简单且通用）：](#更正方法更简单且通用)**

**（如果遇到不支持中文情况，对文字进行URL编码即可）**



- [Markdown生成TOC：](#markdown%E7%94%9F%E6%88%90toc)
  - [正常情况：](#%E6%AD%A3%E5%B8%B8%E6%83%85%E5%86%B5)
    - [一、TOC标签直接生成](#%E4%B8%80toc%E6%A0%87%E7%AD%BE%E7%9B%B4%E6%8E%A5%E7%94%9F%E6%88%90)
    - [二、手动生成](#%E4%BA%8C%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [三、VSCode插件](#%E4%B8%89vscode%E6%8F%92%E4%BB%B6)
  - [Github生成TOC：](#github%E7%94%9F%E6%88%90toc)
    - [一、手动生成](#%E4%B8%80%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [二、VSCode插件](#%E4%BA%8Cvscode%E6%8F%92%E4%BB%B6)


## 正常情况：

### 一、TOC标签直接生成

```markdown
[TOC]
```



### 二、手动生成

格式：`[目录中显示的标题名称](#内容中的标题名称)` 

简记：`[Content](#URL)`

示例：`[Github生成TOC](#Github生成TOC)` [Github生成TOC：](#Github生成TOC)

- 也可以将标题进行URL编码：



### 三、VSCode插件

插件名：Markdown All in One

使用方法：安装好后 -- Ctrl + Shift + P打开控制面板 -- 输入Create Table of Contents自动生成TOC

效果：

```markdown
- [Markdown生成TOC：](#markdown%E7%94%9F%E6%88%90toc)
  - [正常情况：](#%E6%AD%A3%E5%B8%B8%E6%83%85%E5%86%B5)
    - [一、TOC标签直接生成](#%E4%B8%80toc%E6%A0%87%E7%AD%BE%E7%9B%B4%E6%8E%A5%E7%94%9F%E6%88%90)
    - [二、手动生成](#%E4%BA%8C%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [三、VSCode插件](#%E4%B8%89vscode%E6%8F%92%E4%BB%B6)
  - [Github生成TOC：](#github%E7%94%9F%E6%88%90toc)
    - [一、手动生成](#%E4%B8%80%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [二、VSCode插件](#%E4%BA%8Cvscode%E6%8F%92%E4%BB%B6)
```



## Github生成TOC：

Github比较麻烦，但也与上面类似，解决编码问题即可。

参考手册：[HTML URL 编码参考手册 (w3school.com.cn)](https://www.w3school.com.cn/tags/html_ref_urlencode.asp)

编码工具：[UrlEncode编码/UrlDecode解码 - 站长工具 (chinaz.com)](http://tool.chinaz.com/tools/urlencode.aspx)



### 一、手动生成

- （标题无符号）将各级标题直接进行URL编码。

  e.g. `TOC标签直接生成` -->`TOC%E6%A0%87%E7%AD%BE%E7%9B%B4%E6%8E%A5%E7%94%9F%E6%88%90`

  ```markdown
  [一、TOC标签直接生成](#%E4%B8%80toc%E6%A0%87%E7%AD%BE%E7%9B%B4%E6%8E%A5%E7%94%9F%E6%88%90)
  ```

  

- （标题有符号）去掉符号再对标题进行URL编码。

  e.g. `Github生成TOC：`-->`Github生成TOC` -->`Github%E7%94%9F%E6%88%90TOC`

  - **原理：盲猜对标点符号和大小写不敏感。**
  ```markdown
  - [Github生成TOC：](#github%E7%94%9F%E6%88%90toc)
  ```

  



### 二、VSCode插件

插件名：Markdown All in One

使用方法：

- 安装好后打开`设置` --> `扩展` --> `Markdown All in One` --> `Markdown › Extension › Toc: Slugify Mode`
- 将生成标题 ID 的方法改为`VSCode`

-  打开markdown文件 -- `Ctrl + Shift + P`打开控制面板 -- 输入`Create Table of Contents`自动生成TOC

看一下效果：
- [Markdown生成TOC：](#markdown%E7%94%9F%E6%88%90toc)
  - [正常情况：](#%E6%AD%A3%E5%B8%B8%E6%83%85%E5%86%B5)
    - [一、TOC标签直接生成](#%E4%B8%80toc%E6%A0%87%E7%AD%BE%E7%9B%B4%E6%8E%A5%E7%94%9F%E6%88%90)
    - [二、手动生成](#%E4%BA%8C%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [三、VSCode插件](#%E4%B8%89vscode%E6%8F%92%E4%BB%B6)
  - [Github生成TOC：](#github%E7%94%9F%E6%88%90toc)
    - [一、手动生成](#%E4%B8%80%E6%89%8B%E5%8A%A8%E7%94%9F%E6%88%90)
    - [二、VSCode插件](#%E4%BA%8Cvscode%E6%8F%92%E4%BB%B6)

