###Cartographer安装流程

#####安装与编译  
#####0. 安装所有依赖项  
$    sudo apt-get install -y google-mock libboost-all-dev  libeigen3-dev libgflags-dev libgoogle-glog-dev liblua5.2-dev libprotobuf-dev  libsuitesparse-dev libwebp-dev ninja-build protobuf-compiler python-sphinx  ros-indigo-tf2-eigen libatlas-base-dev libsuitesparse-dev liblapack-dev    
![0.PNG](http://upload-images.jianshu.io/upload_images/3240775-461dacfb6ff545b1.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    

#####1. 安装ceres solver 1.11  
$    git clone https://github.com/hitcm/ceres-solver-1.11.0.git  
![1.1.PNG](http://upload-images.jianshu.io/upload_images/3240775-1fe8b1ddafe52862.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    cd ceres-solver-1.11.0/build  
$    cmake ..     
![1.3.PNG](http://upload-images.jianshu.io/upload_images/3240775-56dc8c5a5e116eb9.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    make  
![1.4.PNG](http://upload-images.jianshu.io/upload_images/3240775-2279e43c998efdca.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    sudo make install  
![1.5.PNG](http://upload-images.jianshu.io/upload_images/3240775-011fb1a537d19dff.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####2. 安装cartographer  
$    git clone https://github.com/hitcm/cartographer.git  
![2.1.PNG](http://upload-images.jianshu.io/upload_images/3240775-5c6c3ca8b67ae0ae.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    cd cartographer/build   
$    cmake  ..  
![2.3.PNG](http://upload-images.jianshu.io/upload_images/3240775-c207488a9d1a18ed.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    make  
![2.4.PNG](http://upload-images.jianshu.io/upload_images/3240775-445458e6e405b011.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
$    sudo make install    
![2.5.PNG](http://upload-images.jianshu.io/upload_images/3240775-4605d83f91ca5e17.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
  
#####3. 安装cartographer_ros  
$    sudo apt-get update  
$    sudo apt-get install -y python-wstool python-rosdep ninja-build  
![3.1.PNG](http://upload-images.jianshu.io/upload_images/3240775-3bce842fe6c721f9.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
  
$    mkdir catkin_ws  
$    cd catkin_ws  
$    wstool init src  


下载到catkin_ws下面的src文件夹下面    
$    git clone https://github.com/hitcm/cartographer_ros.git  
到catkin_ws下面运行catkin_make  
$    catkin_make  
![3.2.PNG](http://upload-images.jianshu.io/upload_images/3240775-6ad3b7b6c5f605bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#####4. 数据下载测试  
$    catkin_make_isolated --install --use-ninja  
注意： 上面这一步需要翻墙才能访问网址  
$    source install_isolated/setup.bash  
  
#####4.运行样例  
#####1. 下载2D样例包并运行  
$    wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag    
安装成功：  
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3240775-da1d4ebc927b26b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

$    roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag  
运行结果：  
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3240775-a45d8b9c8094f09e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  
  
###Experimental Experience——实验心得
在本次实验中主要是跟着教程安装与配置cartographer，需要注意的是在首次运行时会报错，此时执行以下两句：  
$    source ~/catkin_ws/devel/setup.bash  
$    rospack profile  
即可正常运行。