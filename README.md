###Description——DOL框架描述
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

The DOL consists of basically three parts:

- DOL Application Programming Interface: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.

- DOL Functional Simulation: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.

- DOL Mapping Optimization: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained.

###How to install——DOL安装笔记
#####1. 在Ubuntu上安装一些必要的环境  
$    sudo apt-get update   
$    sudo apt-get install ant   
$     sudo apt-get install openjdk-7-jdk
$    sudo apt-get install unzip  
#####2. 下载文件与解压文件  
新建dol的文件夹  
$    mkdir dol  
将dolethz.zip解压到 dol文件夹中  
$    unzip dol_ethz.zip -d dol  
解压systemc  
$    tar -zxvf systemc-2.3.1.tgz  
#####3. 编译systemc  
解压后进入systemc-2.3.1的目录下  
$    cd systemc-2.3.1  
新建一个临时文件夹objdir  
$    mkdir objdir  
进入该文件夹objdir  
$    cd objdir  
运行configure(能根据系统的环境设置一下参数，用于编译)  
$    ../configure CXX=g++ --disable-async-updates  
运行configure之后的截图：  
![](http://upload-images.jianshu.io/upload_images/3240775-065d6c24e1e58a0d.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    sudo make install  
编译完后文件目录如下($ cd ..        $ ls  
![](http://upload-images.jianshu.io/upload_images/3240775-28e8980ed6ebd52f.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
记录当前的工作路径(会输出当前所在路径，记下来，待会有用)  
$    pwd  
![](http://upload-images.jianshu.io/upload_images/3240775-9b5f4fccbeedfb17.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
这里表示我当前的工作路径为 /home/bizarrez/systemc-2.3.1  

#####4. 编译dol  
进入刚刚dol的文件夹  
$    cd ../dol  
修改build\_zip.xml文件  
找到下面这段话，就是说上面编译的systemc位置在哪里  
<property name="systemc.inc" value="YYY/include  />  
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a/>  
把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）  
然后是编译  
$    ant -f build_zip.xml all  
若成功会显示build successful  
![](http://upload-images.jianshu.io/upload_images/3240775-68742d283534fbe1.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####5. 开发环境配置完成  
接着可以试试运行第一个例子  
进入build/bin/mian路径下  
$    cd build/bin/main  
然后运行第一个例子  
$    ant -f runexample.xml -Dnumber=1  

成功结果如图  
![](http://upload-images.jianshu.io/upload_images/3240775-71dc389c30ea19a1.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
###Experimental Experience——实验心得
1. 配置DOL的过程在实验文档中已经非常详尽地描述了，在配置过程中没有遇到难题，感谢师兄师姐们的详细指导。
2. github上仓库的创建过程并不复杂，在Ubuntu上安装git只需要一句命令，创建库等操作也都有相应指导，感谢实验文档与廖雪峰老师的教程。  
3. 本次实验文档需要使用markdown进行编写，它的语法非常简单，并且不需要自己排版，十分便利，markdownpad 2是一款强大的markdown编辑器，对语法要求比较严格，图片的插入也需要先生成URL链接再进行插入，相比起来简书的在线编辑功能也比较方便，图片可以直接拖入。