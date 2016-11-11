###ROS安装流程
ROS——一套框架，底层提供硬件驱动，软件层面支持通用的文件格式。之后的Cartographer实验是基于ROS的仿真功能实现的。
The DOL consists of basically three parts:

####ROS安装笔记
#####1. 设置软件源  
$    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'   

#####2. 设置密钥  
$    sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116  
![1.PNG](http://upload-images.jianshu.io/upload_images/3240775-1947b2d45a053b52.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####3. 安装  
更新软件索引包 
$    sudo apt-get update    
$    sudo apt-get install libgl1-mesa-dev-lts-utopic  

完全安装ROS  
$    sudo apt-get install ros-jade-desktop-full  
![2.PNG](http://upload-images.jianshu.io/upload_images/3240775-f9df5be06cb0ee59.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####4. 初始化rosdep    
$    sudo rosdep init  
![3.PNG](http://upload-images.jianshu.io/upload_images/3240775-85ced651f835fc42.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    rosdep update  
![4.PNG](http://upload-images.jianshu.io/upload_images/3240775-00863e1b22855f91.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####5. 设置环境   
添加ROS的环境变量  
$    echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc  
使环境变量设置立即生效  
$    source ~/.bashrc  

#####6. 安装rosinstall     
$    sudo apt-get install python-rosinstall  
![5.PNG](http://upload-images.jianshu.io/upload_images/3240775-0212aaa2c5b9b24e.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
  
至此，ROS的安装已全部完成。  
  
验证ROS安装成功：  
$    export | grep ROS  
结果(ROS安装路径)：  
![6.PNG](http://upload-images.jianshu.io/upload_images/3240775-01ffc5611c21f984.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
  
###Experimental Experience——实验心得
在本次实验中主要是跟着教程安装与配置ROS，基本没有太大难度。