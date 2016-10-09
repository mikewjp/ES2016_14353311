#Lab01 Lab02 DOL安装与配置
## 1.DOL 框架描述
***
###Distributed Operation Layer (DOL)
DOL是一个允许程序在多处理器图形图形架构平台上进行自动绘制图形的框架。

* DOL Application Programming Interface: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.
* OL Functional Simulation: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.
* OL Mapping Optimization: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained. 

## 2.DOL安装笔记
***
### （1）安装一些必要的环境(ubuntu为例)：
`$    sudo apt-get update`

`$	sudo apt-get install ant`

`$ 	sudo apt-get install openjdk-7-jdk`

`$	sudo apt-get install unzip`
### （2）解压文件
新建dol的文件夹 

`$    mkdir dol`

将dolethz.zip解压到 dol文件夹中

`$	unzip dol_ethz.zip -d dol`

解压systemc

`$	tar -zxvf systemc-2.3.1.tgz`
### （3）编译systemc
解压后进入systemc-2.3.1的目录下

`$    cd systemc-2.3.1`

新建一个临时文件夹objdir

`$	mkdir objdir`

进入该文件夹objdir

`$	cd objdir`

运行configure(能根据系统的环境设置一下参数，用于编译)

`$	../configure CXX=g++ --disable-async-updates`

运行configure之后的截图

![doc-1]{lab1/1.png}

编译

`$    sudo make install`

编译完后文件目录如下

`$ cd ..`        

`$ ls`

![doc-2]{lab1/2.png}

记录当前的工作路径(会输出当前所在路径，记下来，待会有用)

`$    pwd`
###（3）编译dol
进入刚刚dol的文件夹

`$    cd ../dol`

修改build_zip.xml文件

找到下面这段话，就是说上面编译的systemc位置在哪里，

`<property name="systemc.inc" value="YYY/include"/>`

`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`

把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）

然后是编译

`$    ant -f build_zip.xml all`

若成功会显示build successful

接着可以试试运行第一个例子

进入build/bin/mian路径下

`$	cd build/bin/main`

然后运行第一个例子

`$	ant -f runexample.xml -Dnumber=1`

成功结果如图

![doc-3]{lab1/3.png}
## 3.实验感想、实验心得
***
* 这次实验是按照PPT的步骤安装和配置DOL的环境。我遇到的第一个问题是虚拟机上的Ubuntu系统不能上网，导致不能下载安装必要的环境。后来经过修改各种网络设置，终于解决了问题。然后还有一个就是直接安装java的jdk时出问题，应该是我用的是64位的系统，所以下载openjdk-7-jdk有问题。然后直接用了TA给的那个jdk8，按照说明一步一步地完成安装配置环境变量，最后就没有问题了。后面的安装都很顺利，没遇到问题。
* 还有一个是觉得markdown的语法很奇怪，虽然的确轻便，但有一些还是很不习惯，例如要两次回车才能换行等。