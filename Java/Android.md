1.Android是Linux内核的移动操作系统平台


2.Android结构:
		   
	应用层:										系统自带App(联系人,短信)	   
		   
	应用框架层:									Android SDK	 API  
		   
	系统运行层:				C/C++的运行库(SQLITE,OPENGL,WebKit)	   				Dalvik
		   
	Linux Kernel 2.6:		   		(核心OS概念+底层驱动:显示,音频,照相机,蓝牙,WiFi,电源)
	
3.发展版本 Android 2.1,Android 2.2 ... Andriod N(查看覆盖率:http://developer.android.com/ about/dashboards/)   


4.核心特色:


	1.四大组件:
		Activity:
		Service:
		Broadcast Receiver:
		Content Provider:
	
	2.应用层的系统自带App可自行开发替换
	
	3.SQLLite，GeoLocation，Media Support,传感器
	
	
5.开发环境
	
	OS:Mac Windows
	Tools:
	
		JDK:
		Android SDK:官网下载挂代理下载里面的内容
		
		Android Studio:官方推荐
		Eclipse+ADT:比较过时
		InteliiJ Idea: Android Studio是这个的精简版
		
		
6.App的开发版本

		按照目前的覆盖率:
					  min(最低支持版本)设置成4.0
					  target和compile设置成需要支持的最高版本
					  
7.工程目录中的 properties文件可以修改SDK版本，这样IDE中SDK版本会相应变化
		     AndroidManifest.xml 是注册四大组件的地方 是工程的梗概文件
		     
8.开发特点:XML描述UI＋java代码处理UI事件和逻辑

9.
		
					  
					  