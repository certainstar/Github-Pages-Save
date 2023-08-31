---
layout: default
title: 关于java配置
author: certainstar
date: 2023-9-1
---

# 关于java配置

## 为什么要配置java环境

> - [x] _在本项目中，需要用到java对签名服务器进行运行，而配置java环境，则可以更加方便该操作的执行。_

> - [x] ___同时在其他项目中，配置java环境后，需要用到java程序时，不需要在java安装的根目录下 `\bin` 处运行，更加的方便快捷，同时使得java在任意位置均成为内部命令/外部命令，便于对java的控制和使用。___

## 如何判断是否配好java环境

- <span id="judge">在命令行(`win` + `R`,输入 `cmd`,回车 `Enter`)输入以下代码(只用输入>后的代码回车即可):</span>
```cmd
	C:\Users\自己的用户名>java
```

若不是显示 _`java不是内部或外部命令`_ ，而是显示一串正常的中文信息，则说明java环境配置成功，反之则未配置成功。

## 配置步骤

### 第一步：下载

- [x] 首先前往[java官网](https://www.java.com/)下载java，或者可以去[jdk官网](https://www.oracle.com/cn/java/)下载jdk,下面以下载jdk为例([jdk下载网址](https://www.oracle.com/cn/java/technologies/downloads/))(以下均以windows系统为例，其他系统的操作均大同小异)

- [x] 打开jdk下载网址以后，下载符合版本的jdk，建议下载最新版的jdk，但是下载其他版本的也可以，但是如果打不开后续签名服务器中的 _`start.bat`_ 文件，可以在命令行中输入特殊命令进行升级(在配置好java环境以后)。

> 注意下载jdk时要注意是否为电脑系统所匹配的版本，若您不知道如何查看自己的系统是 `ARM64` 还是 `X64` 架构则可在命令行(`win` + `R`,输入 `cmd`,回车 `Enter`)输入以下代码(`只用输入>后的代码回车即可`):
>```cmd
>	C:\Users\自己的用户名>systeminfo
>```
> 后续在 `系统类型` 中即可查看。

- [x] 下载对应的jdk(下载文件的后缀为 `.exe`，即为可执行文件，若下载可执行文件，则按照步骤进行安装。若直接下载 `.zip` 压缩包文件，将其解压后放在一个新的目录下即可)后，按照若安装正常则应该在安装目录下有以下文件夹:`bin`,`conf`,`include`,`jmods`,`legal`,`lib`。还应当有以下文件:`LICENSE`,`README`,`release`。
也可按照以下步骤检查是否安装成功：<span id="change"></span>
	1. 打开安装目录下的 `bin` 文件夹，然后复制所在路径。
		> <span id="copy">复制路径的两种方法：</span>
		> 方法1：直接左键 `bin` 文件夹，`ctrl`+`shift`+`C`
		> 方法2：点击如下图所示的位置进行复制
		<p align="center">
			<img src="../../img/little-Python-software/java配置1.jpg" alt="java配置1">
			<p align="center">
          		<span> java配置1</span>
        	</p>
      	</p>

    2. 打开命令行(步骤同上)，如果你存放jdk的位置 _不为C盘_ ，则在命令行中输入以下命令(`还是只复制>后的内容并回车即可`)(假设jdk储存在D盘)，用来切换到此盘。若为C盘可以直接进入下一步。
	    ```cmd
	    	C:\Users\自己的用户名>D:
	    ```

	3. 在命令行中再输入以下代码(同上)，`cd` 用于切换到后续目录:
		```cmd
			存放jdk的盘:\>cd 刚刚复制的路径
		```
	此时新的命令行显示应该会变为类似以下的代码：
		```cmd
			刚刚复制的路径(以\bin结尾)>
		```
	在>后输入 `java` 后回车，若命令行中出现以下内容(不完整)，则说明下载成功。
		```cmd
						用法：java [options] <主类> [args...]
			           （执行类）
			   或  java [options] -jar <jar 文件> [args...]
			           （执行 jar 文件）
			   或  java [options] -m <模块>[/<主类>] [args...]
			       java [options] --module <模块>[/<主类>] [args...]
			           （执行模块中的主类）
			   或  java [options] <源文件> [args]
			           （执行单个源文件程序）

			 将主类、源文件、-jar <jar 文件>、-m 或
			 --module <模块>/<主类> 后的参数作为参数
			 传递到主类。

			 其中，选项包括：

			    -cp <目录和 zip/jar 文件的类搜索路径>
			    -classpath <目录和 zip/jar 文件的类搜索路径>
			    --class-path <目录和 zip/jar 文件的类搜索路径>
			                  使用 ; 分隔的, 用于搜索类文件的目录, JAR 档案
			                  和 ZIP 档案列表。
			    -p <模块路径>
			    --module-path <模块路径>...
			                  用 ; 分隔的目录列表, 每个目录
			                  都是一个包含模块的目录。
			    --upgrade-module-path <模块路径>...
			                  用 ; 分隔的目录列表, 每个目录
			                  都是一个包含模块的目录, 这些模块
			                  用于替换运行时映像中的可升级模块
			    ......
		```
	> 注：若出现类似 _`版本过旧，该功能...`_ 的字样，则需要更新。如何更新java版本，可在<a href="#basic-commands">基本java命令</a>中查看。 

### 第二步：配置环境变量

> 在这部分开始之前，一定要确保jdk已经安装成功。

- [x] 在windows的开始页面或者在设置中，搜索 `编辑系统环境变量`，点击跳转出来有关 `环境变量` 的选项。或者右键点击 `此电脑(我的电脑)`，点击 `属性`，进入页面后点击 `高级系统设置`，在弹窗页面中点击 `环境变量` 即可。

- [x] 当前页面中会有 `用户变量(U)` 和 `系统变量(S)` 两个项目，点击 `系统变量(S)` 中的 `新建(W)` 按钮，在 `变量名(N)` 中输入 _`JAVA_HOME`_ ，在 `变量值(V)` 中填入下载的jdk的路径，复制路径方法<a href="#copy">同上</a>，然后点击确定。

	> 注意是复制 `jdk\版本号` 文件夹的位置，而不是上述 `bin` 文件夹的位置。

- [x] 然后再 `系统变量(S)` 中找到 `Path` 变量，双击后点击弹出的 `编辑环境变量` 页面中的 `新建(N)` 按钮，添加内容 `%JAVA_HOME%\bin`，随即一直点击确定按钮(`编辑环境变量` 页面的确定，`环境变量` 页面的确定，`系统属性` 页面的确定等等，直到全部页面关闭)即可。

### 第三步：确认是否完成java环境配置

此处可见<a href="#judge">如何判断是否配好java环境</a>。如果仍然没有配置好，请自行检查上述步骤中是否有位置出现差错。如果多次检查后，还是无法正确配置，请自行搜索解决 ~~(开发者也无能为力)~~ 。

## 关于常见的java命令行指令(在windows中)
<span id="basic-commands"></span>

> ___注：以下java命令均需在配置号java环境以后，才能在如何位置打开的命令行中使用(<a href="#open_cmd">如何打开命令行</a>)，否则只能在java下载目录下使用java命令，即打开命令行后切换到下载java位置的`\bin`目录下才可以使用java命令(<a href="#change">如何切换到下载java位置的`\bin`目录</a>)___

### 命令行中java命令应该怎么使用

使用格式类似如下(在>后输入java命令即可，注意空格缩进)：
```cmd
	当前路径>java命令
```

### 常用的java命令以及示例 

- [x] java <ClassName>： 运行已编译的 Java 类。
	> 示例：当前路径>java HelloWorld（运行名为 "HelloWorld" 的类）

- [x] java -jar <JARFileName>： 运行可执行 JAR 文件。
	> 示例：当前路径>java -jar myapp.jar（运行名为 "myapp.jar" 的 JAR 文件）(后续省略 `当前路径>`，只标注java命令)

- [x] java -cp <Classpath> <ClassName>： 指定类路径并运行 Java 类。
	> 示例：java -cp .;lib/* MyApp（在当前目录和 "lib" 目录下查找类并运行 "MyApp"）

- [x] java -D<property>=<value> <ClassName>： 设置 Java 系统属性并运行类。
	> 示例：java -Dfile.encoding=UTF-8 MyApp（设置文件编码属性并运行 "MyApp"）

- [x] java -X<flag> <ClassName>： 设置非标准的启动选项。
	> 示例：java -Xmx512m MyApp（设置最大堆内存为 512 MB 并运行 "MyApp"）

- [x] java -verbose:<flag> <ClassName>： 启用详细输出。
	> 示例：java -verbose:class MyApp（显示类加载信息并运行 "MyApp"）

- [x] java -help 或 java -?： 显示 Java 命令的帮助信息。
	> java -version： 显示 Java 版本信息。
	> java -update : 对当前java版本进行更新(该命令只对老版本的java有用，___新版本中被遗弃，新版本更新java推荐去官网下载最新版本___)

- [x] javap <ClassName>： 反汇编已编译类文件的字节码。
	> 示例：javap MyClass（查看 "MyClass" 类的字节码）

- [x] javac <JavaFileName>： 编译 Java 源代码文件。
	> 示例：javac HelloWorld.java（编译名为 "HelloWorld.java" 的源代码文件）

## 关于常见的命令行命令
> <span id="open_cmd">关于如何打开命令行:</span>
> `win`+`R` 后在 `运行` 弹窗中输入 `cmd` 然后回车。

### 命令行命令应该怎么使用

使用格式类似如下(在>后输入命令行命令即可，注意空格缩进)：
```cmd
	当前路径>命令行命令
```

### 常见命令行命令及其示例

- [x] cd（Change Directory）： 用于更改当前工作目录。
	> 示例：cd Documents（进入 "Documents" 目录）(省略 `当前路径>部分`，后面的同此处)

- [x] ls（List）： 用于列出当前目录中的文件和子目录。
	> 示例：ls 或 ls -l（列出详细信息）

- [x] pwd（Print Working Directory）： 显示当前工作目录的路径。
	> 示例：pwd

- [x] mkdir（Make Directory）： 创建新目录。
	> 示例：mkdir NewFolder（创建名为 "NewFolder" 的目录）

- [x] rm（Remove）： 删除文件或目录。
	> 示例：rm file.txt（删除 "file.txt" 文件）

- [x] cp（Copy）： 复制文件或目录。
	> 示例：cp source.txt destination.txt（将 "source.txt" 复制为 "destination.txt"）

- [x] mv（Move）： 移动文件或目录，也可用于重命名。
	> 示例：mv old.txt new.txt（将 "old.txt" 重命名为 "new.txt"）

- [x] touch： 创建新文件。
	> 示例：touch newfile.txt（创建名为 "newfile.txt" 的文件）

- [x] cat（Concatenate）： 显示文件内容。
	> 示例：cat file.txt

- [x] echo： 在终端中显示文本或将文本输出到文件中。
	> 示例：echo "Hello, World!" 或 echo "Hello" > greeting.txt