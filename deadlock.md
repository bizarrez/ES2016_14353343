###Deadlock
#####1. 死锁产生：  
count = 10000：    
![count=10000.PNG](http://upload-images.jianshu.io/upload_images/3240775-67f8e098a736b67b.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
count = 20000：  
![count=20000.PNG](http://upload-images.jianshu.io/upload_images/3240775-84dbb7ec6e813d7f.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
count = 5000：  
![count=5000.PNG](http://upload-images.jianshu.io/upload_images/3240775-1aefc8027b44d584.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

#####2. 对上述程序产生死锁的解释：  
关键字 synchronized：当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码；当一个线程访问object的一个synchronized同步代码块或同步方法时，其他线程对object中所有其他synchronized同步代码块或同步方法的访问将被阻塞。  
![image002.jpg](http://upload-images.jianshu.io/upload_images/3240775-a63900eb6a5c2ffc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
在主函数的时间轴中，当t.start()之后，线程t就被插入到调度队列里，当调度到他时，就执行run()。
![image005.jpg](http://upload-images.jianshu.io/upload_images/3240775-441704cf12c1b702.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
这里设置了一个count值，当t.start()执行后，就开始延时，执行b.methodB(a)，当延时结束后，若t.start()尚未执行完毕，主线程中开始执行a.methodA(b)，由于关键字synchroniazed的限制，不能有两个以上的线程同时执行，因此产生死锁。  
#####4. 产生死锁的4个必要条件：  
死锁就是两个或者多个进程，互相请求对方占有的资源。  
* 互斥条件：一个资源每次只能被一个进程使用  
* 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放  
* 不剥夺条件:进程已获得的资源，在末使用完之前，不能强行剥夺  
* 循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系  