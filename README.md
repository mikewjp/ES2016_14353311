#Lab01 Lab02 DOL��װ������
## 1.DOL �������
***
###Distributed Operation Layer (DOL)
DOL��һ����������ڶദ����ͼ��ͼ�μܹ�ƽ̨�Ͻ����Զ�����ͼ�εĿ�ܡ�

* DOL Application Programming Interface: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.
* OL Functional Simulation: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.
* OL Mapping Optimization: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained. 

## 2.DOL��װ�ʼ�
***
### ��1����װһЩ��Ҫ�Ļ���(ubuntuΪ��)��
`$    sudo apt-get update`

`$	sudo apt-get install ant`

`$ 	sudo apt-get install openjdk-7-jdk`

`$	sudo apt-get install unzip`
### ��2����ѹ�ļ�
�½�dol���ļ��� 

`$    mkdir dol`

��dolethz.zip��ѹ�� dol�ļ�����

`$	unzip dol_ethz.zip -d dol`

��ѹsystemc

`$	tar -zxvf systemc-2.3.1.tgz`
### ��3������systemc
��ѹ�����systemc-2.3.1��Ŀ¼��

`$    cd systemc-2.3.1`

�½�һ����ʱ�ļ���objdir

`$	mkdir objdir`

������ļ���objdir

`$	cd objdir`

����configure(�ܸ���ϵͳ�Ļ�������һ�²��������ڱ���)

`$	../configure CXX=g++ --disable-async-updates`

����configure֮��Ľ�ͼ

![doc-1]{lab1/1.png}

����

`$    sudo make install`

��������ļ�Ŀ¼����

`$ cd ..`        

`$ ls`

![doc-2]{lab1/2.png}

��¼��ǰ�Ĺ���·��(�������ǰ����·��������������������)

`$    pwd`
###��3������dol
����ո�dol���ļ���

`$    cd ../dol`

�޸�build_zip.xml�ļ�

�ҵ�������λ�������˵��������systemcλ�������

`<property name="systemc.inc" value="YYY/include"/>`

`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`

��YYY�ĳ���ҳpwd�Ľ����ע�⣬����  64λ ϵͳ�Ļ�����lib-linuxҪ�ĳ�lib-linux64��

Ȼ���Ǳ���

`$    ant -f build_zip.xml all`

���ɹ�����ʾbuild successful

���ſ����������е�һ������

����build/bin/mian·����

`$	cd build/bin/main`

Ȼ�����е�һ������

`$	ant -f runexample.xml -Dnumber=1`

�ɹ������ͼ

![doc-3]{lab1/3.png}
## 3.ʵ����롢ʵ���ĵ�
***
* ���ʵ���ǰ���PPT�Ĳ��谲װ������DOL�Ļ������������ĵ�һ��������������ϵ�Ubuntuϵͳ�������������²������ذ�װ��Ҫ�Ļ��������������޸ĸ����������ã����ڽ�������⡣Ȼ����һ������ֱ�Ӱ�װjava��jdkʱ�����⣬Ӧ�������õ���64λ��ϵͳ����������openjdk-7-jdk�����⡣Ȼ��ֱ������TA�����Ǹ�jdk8������˵��һ��һ������ɰ�װ���û�������������û�������ˡ�����İ�װ����˳����û�������⡣
* ����һ���Ǿ���markdown���﷨����֣���Ȼ��ȷ��㣬����һЩ���Ǻܲ�ϰ�ߣ�����Ҫ���λس����ܻ��еȡ�