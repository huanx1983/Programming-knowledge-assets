
			JavaScript分类
					|	
					|---- Client JavaScript	(浏览器端js是ECMAScript一个实现，由ECMAScript BOM DOM组成)
					|	
					|	
					|---- Core JavaScript	(NodeJs是ECMAScript的一个脱离浏览器的一个实现)
						
						  各种脱离浏览器的js平台产生,产生了CommonJS规范
						  CommonJS 试图定义一套普通应用程序使用的API,填补JavaScript标准库过于简单的不足。
						  CommonJS 的终极目标是制定一个像C++标准库一样的规范,使得基于CommonJS API的应用程序可以在不同的环 境下运行。
						  CommonJS 不参与标准库实现,其实现交给像 Node.js 之类的项目来完成
						  CommonJS 规范包括了 模块(modules)、包(packages)、系统(system)、二进制(binary) 
						  					控制台(console)、编码(encodings)、文件系统(file system)
						  					套接字(sockets)、单元测 试(unit testing)
			
1.Node.js
	
				1.一个让JavaScript运行于服务器宿主或PC环境的平台(包括:解释器,宿主系统功能API),不是框架，不是库，是平台
				2.由大量的web使用和非web使用的经验上总结出的平台
				2.为了处理实时web应用而产生
				3.npm(一个完全由JavaScript实现的命令行工具,通过Node.js执行,主要是包(模块)管理工具)
				4.可以开发 web网站,socket服务器,命令行工具,交互终端,图形界面的本地应用,客户端js编译器
				5.内嵌http模块
				6.异步事件代替多线程
			
			
2.NodeJs在 POSIX 标准的操作系统上 如 linux windows mac 都可以安装


3.模块

				1.模块是 Node.js 应用程序的基本组成部分,文件和模块是一一对应的
				
					module.js:
					
					function hello(){
						console.log("Hello!");
					}
					exports.hello=hello;									modules.exports=hello
					
					
					App.js
					//接口对象是exports										//接口对象是hello方法本身
					var useModule = require('./module');					var hello=require('./module');
					useModule.hello();										hello();
 					  
					
4.NodeJs包,模块的集合

				1.一个遵循CommonJS一个文件夹
				2.package.json在顶层目录底下(严格来说这点是最关键的)
				3.二进制文件在bin下
				4.js代码在lib下
				5.文档在doc下
				6.测试在test下
				
				somepackage/
							－package.json
							－bin/
							－lib/
								  -module1.js
								  -module2.js
							－doc/
							－test/
				
				
				package.json
				
				{
					"main":"./lib/module1.js"
				}	
				
				
				var somepackage=require('./somepackage') 
				
				
				==================package.json demo====================
				{
					"name": "mypackage",
					"description": "Sample package for CommonJS. This package demonstrates the required
				       elements of a CommonJS package.",
				    "version": "0.7.0",
				    "keywords": ["package","example" ],
				    "maintainers": [
				       {
				          "name": "Bill Smith",
				          "email": "bills@example.com",
				       }
				    ],
				    "contributors": [
				       {
				          "name": "BYVoid",
				          "web": "http://www.byvoid.com/"
					   } 
					],
				    "bugs": {
				       "mail": "dev@example.com",
				       "web": "http://www.example.com/bugs"
				    },
				    "licenses": [
				       {
				          "type": "GPLv2",
				          "url": "http://www.example.org/licenses/gpl.html"
					  } 
					],
				    "repositories": [
				       {
				          "type": "git",
				          "url": "http://github.com/BYVoid/mypackage.git"
				       }
				    ],
				    "dependencies": {
				       "webkit": "1.2",
				       "ssl": {
				          "gnutls": ["1.0", "2.0"],
				          "openssl": "0.9.8"
				       }
					} 
				}
					
					
			 
			 =====================初始化一个简单结构和package.json=====================		

					cd packageName
					npm init

5.npm 模式

				1.当要把某个包 "作为工程运行" 时的一部分时,通过本地模式获取,如果要 "在命令行" 下使用,则使用全局模式安装 －g
				2.无参数的 npm install 的功能就是 检查当前目录下的 package.json,并自动安装所有指定的依赖
					
					
6.核心
				
				
				宿主:
				1.global对象的属性:console,process
				2.NodeJs由于是模块和包的概念 所以外层定义的 var 不是global的属性 
				
				
				类库:var util =require('util'); 	util.inherits(Sub, Base); 
				
				类库:var util =require('util');  util.inspect(obj);
 				
				类库:var events = require('events');
					var emitter = new events.EventEmitter();
					emitter.on('someEvent', function(arg1, arg2) { console.log('listener2', arg1, arg2);});
					emitter.emit('someEvent', 'arg1', 'arg2');
					
				类库:var fs = require('fs');
					fs.readFile('content.txt', function(err, data) {
					
					 if (err) {
							console.error(err); 
					 } 
					 else {
       						console.log(data);
       				 }
       				});
       				
       			类库:var http = require('http');
       				http.createServer(function(req, res) { 
       				res.writeHead(200, {'Content-Type': 'text/html'}); 
       				res.write('<h1>Node.js</h1>');
					res.end('<p>Hello World</p>');
					}).listen(3000);
      				console.log("HTTP server is listening at port 3000.");
      				

7.高级

				Node.js 的模块可以分为两大类,
				1.核心模块
				  	核心模块就是 Node.js 标准 API 中提供的模块,如 fs、http、net、vm 等,这些都是由 Node.js 官方提供 的模块,
				  	编译成了二进制代码
					直接通过 require 获取核心模块,例如 require('fs')。核心模块拥有最高的加载优先级,如果有模块与其命名冲突, Node.js 总是会加载核心模块
				2.另一类是文件模块
					文件模块则是存储为单独的文件(或文件夹)的模块,可能是 JavaScript 代码、JSON 或 编译好的 C/C++ 代码。
					文件模块的加载方法相对复杂,但十分灵活,尤其是和 npm 结合使 用时。
					在不显式指定文件模块扩展名的时候,Node.js会分别试图加上 .js、.json 和 .node扩展名。
					.js 是 JavaScript 代码,.json 是 JSON 格式的文本,.node 是编译好的 C/C++ 代码。
				
					
				