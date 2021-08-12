# Git的安装与SSH使用


- [Git的安装与SSH使用](#git的安装与ssh使用)
  - [安装：](#安装)
  - [配置环境变量：](#配置环境变量)
  - [Git 配置：](#git-配置)
    - [用户信息](#用户信息)
    - [查看配置信息](#查看配置信息)
  - [SSH Key配置：](#ssh-key配置)
    - [生成秘钥：](#生成秘钥)
    - [提交公钥：](#提交公钥)
  - [附件：](#附件)
      - [获取项目](#获取项目)
      - [书写代码&推送到服务器](#书写代码推送到服务器)
      - [分支学习](#分支学习)
      - [开发步骤：](#开发步骤)
      - [冲突解决：](#冲突解决)



## 安装：

详见 菜鸟教程 -- Git教程 -- Git安装配置：[Git 安装配置 | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-install-setup.html)

关于镜像站中发布版本中rc的解释：[版本发布中RC的含义什么？](https://blog.csdn.net/jiangbo_phd/article/details/51777411)

安装很简单，什么都不用管，选好安装路径一路next就可以。[Git 详细安装教程（详解 Git 安装过程的每一个步骤）](https://blog.csdn.net/mukes/article/details/115693833)



## 配置环境变量：

将 D:\Program Files\Git\cmd 路径添加到系统环境变量。



## Git 配置：

Git 提供了一个叫做 git config 的工具，专门用来配置或读取相应的工作环境变量。

这些环境变量，决定了 Git 在各个环节的具体工作方式和行为。这些变量可以存放在以下三个不同的地方：

- `/etc/gitconfig` 文件：系统中对所有用户都普遍适用的配置。若使用 `git config` 时用 `--system` 选项，读写的就是这个文件。
- `~/.gitconfig` 文件：用户目录下的配置文件只适用于该用户。若使用 `git config` 时用 `--global` 选项，读写的就是这个文件。
- 当前项目的 Git 目录中的配置文件（也就是工作目录中的 `.git/config` 文件）：这里的配置仅仅针对当前项目有效。每一个级别的配置都会覆盖上层的相同配置，所以 `.git/config` 里的配置会覆盖 `/etc/gitconfig` 中的同名变量。

**在 Windows 系统上，Git 会找寻用户主目录下的 .gitconfig 文件。**主目录即 $HOME 变量指定的目录，一般都是 C:\Documents and Settings\$USER。

此外，Git 还会尝试找寻 /etc/gitconfig 文件，只不过看当初 Git 装在什么目录，就以此作为根目录来定位。

### 用户信息

配置个人的用户名称和电子邮件地址：

```shell
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

如果用了 **--global** 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。

**如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。**

### 查看配置信息

要检查已有的配置信息，可以使用 **git config --list** 命令：

```shell
$ git config --list
http.postbuffer=2M
user.name=runoob
user.email=test@runoob.com
```

有时候会看到重复的变量名，那就说明它们来自不同的配置文件（比如 /etc/gitconfig 和 ~/.gitconfig），不过最终 Git 实际采用的是最后一个。

这些配置我们也可以在 **~/.gitconfig** 或 **/etc/gitconfig** 看到，如下所示：

```shell
vim ~/.gitconfig 
```

显示内容如下所示：

```shell
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
```

也可以直接查阅某个环境变量的设定，只要把特定的名字跟在后面即可，像这样：

```shell
$ git config user.name
runoob
```



## SSH Key配置：

### 生成秘钥：

```shell
ssh-keygen -t rsa -C "你的邮箱"  # 如果是连接GitHub，此处为你在 Github 上注册的邮箱
```

加密方式可选择（rsa | dsa），默认dsa。详细命令解释看这里：[ssh-keygen的详解](https://blog.csdn.net/wh_19910525/article/details/7433164)，写的非常好。

> [关于DSA与RSA](https://blog.csdn.net/qq_35180983/article/details/82665269)
>
> **原理与安全性**
>
>   RSA 与 DSA 都是非对称加密算法。其中RSA的安全性是基于极其困难的大整数的分解（两个素数的乘积）；DSA 的安全性是基于整数有限域离散对数难题。基本上可以认为相同密钥长度的 RSA 算法与 DSA 算法安全性相当。
>
>   有点要注意，RSA 的安全性依赖于大数分解，但是否等同于大数分解一直未能得到理论上的证明，因为没有证明破解 RSA 就一定需要作大数分解。不过也不必太过担心，RSA 从诞生以来，经历了各种攻击，至今未被完全攻破（依靠暴力破解，小于1024位密钥长度的 RSA 有被攻破的记录，但未从算法上被攻破）。
>
> 
> **用途：**
>
>   DSA 只能用于数字签名，而无法用于加密（某些扩展可以支持加密）；RSA 即可作为数字签名，也可以作为加密算法。不过作为加密使用的 RSA 有着随密钥长度增加，性能急剧下降的问题。
>
> 
> **性能：**
>
>   相同密钥长度下，DSA 做签名时速度更快，但做签名验证时速度较慢，一般情况验证签名的次数多于签名的次数。
>
>   相同密钥长度下，DSA （在扩展支持下）解密密文更快，而加密更慢；RSA 正好反过来，一般来说解密次数多于加密次数。不过由于非对称加密算法的先天性能问题，两者都不是加密的好选择。
>
> 
> **业界支持：**
>
>   在业界支持方面，RSA 显然是赢家。RSA 具有更为广泛的部署与支持。



之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。

成功的话会在 **~/** 下生成 **.ssh** 文件夹，进去，打开 **id_rsa.pub**，复制里面的 **key**。

```shell
$ ssh-keygen -t rsa -C "1234567890@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Admin/.ssh/id_rsa):   # 直接回车 （存放公钥和私钥的文件夹路径）
Enter passphrase (empty for no passphrase):    # 直接回车
Enter same passphrase again:                   # 直接回车
Your identification has been saved in  /c/Users/Admin/.ssh/id_rsa.  # （私钥）
Your public key has been saved in /c/Users/Admin/.ssh/id_rsa.pub.   # （公钥） -- 提交给GitHub的公开密钥
The key fingerprint is:
SHA256:MDKVidPTDXIQoJwoqUmI4LBAsg5XByBlrOEzkxrwARI 429240967@qq.com
The key's randomart image is:
+---[RSA 3072]----+
|E*+.+=**oo       |
|%Oo+oo=o. .      |
|%**.o.o.         |
|OO.  o o         |
|+o+     S        |
|.                |
|                 |
|                 |
|                 |
+----[SHA256]-----+
```



### 提交公钥：

注册并登录Github -- 右上角我的头像 -- Settings --SSH and GPG keys -- SSH keys -- New SSH key打开。

将id_rsa.pub文件中的内容拷贝到GitHub页面下面的输入框，并为这个key定义一个名称（通常用来区分不同主机，可以说中文名称），然后保存。

完成！

首次使用新密钥会提示警告，输入yes即可。

```shell
The authenticity of host 'github.com (20.205.243.166)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? # 输入yes即可
```



## 附件：

#### 获取项目

```shell
git clone https_addr
git clone ssh_addr
```



#### 书写代码&推送到服务器

```shell
# 添加文件
git add 文件名    添加指定文件
git add .         添加所有文件
git status       查看当前的状态

# 提交文件
git commit -m '添加内容'

# 推送文件
git push origin master
git push
```



#### 分支学习

```shell
# 主分支：master/main，默认分支

git branch 分支名 # 新建分支
git branch # 查看分支
git checkout 分支名 # 切换分支
```



#### 开发步骤：

```
一个master，一个dev
（1）新建一个dev
（2）切换到dev进行开发
（3）在dev添加文件并且提交文件
（4）切换到master分支
（5）将dev分支合并到master分支 "git merge dev"
（6）推送master到服务端
（7）继续切换到dev进行开发
```



#### 冲突解决：

a和b同时修改同一个文件的同一行代码就会产生冲突。如果a先push，那么b在push的时候就会报错。所以，为了保险起见，只要想向服务端push内容，首先需要pull内容，pull下来之后就会将服务端的代码和本地的代码进行合并，如果有冲突，就会显示冲突(git diff)，如果没有冲突，那就合并成功，然后再push上去即可，如果有冲突，商量解决冲突即可。
