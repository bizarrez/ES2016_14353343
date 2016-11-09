###Cartographer安装流程

#####安装与编译  
#####1. 安装wstool与rosdep  
$    sudo apt-get update    
$    sudo apt-get install -y python-wstool python-rosdep ninja-build  

#####2. 创建一个新的工作环境'catkin_ws'  
$    mkdir catkin_ws
$    cd catkin_ws
$    wstool init src     

#####3. 获取源码  
$    wstool merge -t src 
https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall  
$    wstool update -t src   

#####4. 安装deb dependencies  
$    rosdep init  
$    rosdep update  
$    rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y  

#####5. 安装与编译  
$    catkin_make_isolated --install --use-ninja  
注意： 上面这一步需要翻墙才能访问网址  
$    source install_isolated/setup.bash  
  
#####运行样例  
#####1. 下载2D样例包并运行  
$    wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag    
安装成功：  
![c2.PNG](http://upload-images.jianshu.io/upload_images/3240775-cd4d3b045ae9ad07.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

$    roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag  
运行结果：  
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3240775-87b1ba970ce3b098.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  
  
###Experimental Experience——实验心得
在本次实验中主要是跟着教程安装与配置cartographer，需要注意的是在访问国外网址时要使用vpn翻墙。