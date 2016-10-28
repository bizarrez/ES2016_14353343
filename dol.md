###DOL修改
#####1. 修改example1，使其输出三次方数
主要部分在square.c中：

在这个程序中定义了平方的进程，其中square_fire信号处理函数，读入输入端信号i，将其平方后写出到输出端，重复len次之后停止。
修改方式：
将    i = i * i  修改为  i = i * i * i  
修改前输出结果：  
![e1b.PNG](http://upload-images.jianshu.io/upload_images/3240775-9353bf4a9bb88fc9.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
修改后输出结果：
![e1a.PNG](http://upload-images.jianshu.io/upload_images/3240775-630be2bb847dea4b.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
#####2. 修改example2，让3个square模块变成两个
主要部分在  
其中的<variable value="3" name="N"/>  
定义了模块的个数  
修改方式：  
将    value = 3  修改为   value = 2  
修改前输出结果：  
![e2b.PNG](http://upload-images.jianshu.io/upload_images/3240775-0b78baf32d90885f.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
修改后输出结果：  
![e2a.PNG](http://upload-images.jianshu.io/upload_images/3240775-d6a45b78964f3485.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
#####3. 实验感想
本次实验中，主要学习到了模块与模块之间的连接，\*.c与对应的.h是实现的模块，每个模块要实现2个接口,xxx\_init函数（初始化模块）与xxx\_fire（模块具体实现功能）；./example*.xml里定义了模块与模块之间是怎么连接的，process是进程，将模块框起来，sw\_channel代表连接框与框的通道，connection代表将框和线连起来。