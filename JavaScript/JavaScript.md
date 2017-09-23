1.ECMAScript是标准化的,独立于宿主环境的编程语言规范。
  主要规范:语法,类型,语句,关键字,保留字,运算符,对象。
  特点:精简的语言,丰富的库支持(宿主环境),区分大小写,弱类型,分号可有可无。
  目前新版本是ES6。
					
2.主要应用于嵌入浏览器(JavaScript的解释器的一种)宿主环境的Web开发,是所有浏览器唯一支持的通用语言,也用于脱离Web环境来使用写服务器逻辑,如NodeJs(JavaScript的解释器的一种),每种宿主环境都实现ECMAScript并且扩展ECMAScript
   
3.数据类型及表达

    基本类型
				
	var x=1;
		  			
	var x=0.01;
	  			
	var x="HelloWorld";
	  			
	var x='HelloWorld';
	  			
	var x=true;
	  			
	var x=false;
	  			
	var x=null;
	  			
	var x=undefined;
	
	typeof  "11" = "string"               typeof new String("11") = "object"
    typeof  123 = "number"                typeof new Number(123) = "object"
    typeof  true ="boolean"               typeof new Boolean(true) = "object"
    typeof  undefined="undefined"         typeof ref_object = "object"
    typeof  null= "object"
    
 
    特殊
    typeof function(){}= "function"
    typeof new Function()="function"
	  				
	  				
	  				
    对象类型
	  			 	
            直接量对象	
  				
            var x={m:1,m:2}
		  			
            var x={"x":1,"y":2} 	x.m	 	x.n 	x["m"] 		x["n"]
	  			
            var x=[{m:1,n:2},{"m":1,"n":2}];  	x[0].m   	x["1"]["n"]
					
					
            数组
	  	   
            var x=[1,2,3];
            x[0]  	x[1]  	x[2]
            x["0"]	x["1"]	x["2"]		
					
					
            函数
					
            function f(){}
					
            var f=function(){}
					
            var f=new Function();
				
				
            构造函数
				
            function F(){}
            var F=function(){}
				
				
            自定义对象
				
            function Obj(){
                this.a=1;
                this.b="2";
            }
					
            Obj.prototype.shut=function(){
                return this.a+this.b
            }
		   
            new Obj().shut();
					
            Note:无参数的构造器 new Obj 调用(可无括号写法)
				
				
4.浏览器环境下的JS，主要是ES,BOM,DOM,CSS组成,浏览器的顶级对象是window,非浏览器的顶级对象是global(var global=this;)

            宿主环境的初始化后，会在global上赋予预定义的全局值(仅跟ES相关的初始属性)
					
            1.全局属性 undefined，Infinity，NaN
            2.全局函数 isNaN(),parseInt(),eval()
            3.全局构造器 Date() RegExp() String() Object() Array() Number() Boolean()
            4.全局对象 Math JSON
            5.BOM(BOM是浏览器宿主环境对象模型,它是对ECMAScript的扩展,但没有被标准化,是特定的浏览器宿主环境提供的与浏览器交互的对象-浏览器开发厂商不统一,不同浏览器中的BOM不完全相同)
					
                    Window 对象
                    Navigator 对象
                    Screen 对象
                    History 对象
                    Location 对象

            6.DOM(DOM是操作XML,HTML的程序模型,它本身是独立于宿主环境,但是要由某种语言来实现如:ECMAScript语言实现-w3c标准)
					
                    HTML Document
                    HTML Element
                    HTML Attributes
                    HTML Events
						
                    ==========================
                    Anchor 对象
                    Area 对象
                    Base 对象
                    Body 对象
                    Button 对象
                    Form 对象
                    Frame/IFrame 对象
                    Frameset 对象
                    Image 对象
                    Input Button 对象
                    Input Checkbox 对象
                    Input File 对象
                    Input Hidden 对象
                    Input Password 对象
                    Input Radio 对象
                    Input Reset 对象
                    Input Submit 对象
                    Input Text 对象
                    Link 对象
                    Meta 对象
                    Object 对象
                    Option 对象
                    Select 对象
                    Style 对象
                    Table 对象
                    td / th 对象
                    tr 对象
                    Textarea 对象

5.布尔

            下面代表都false，其他都为true
					
                    undefined       系统级的，出乎意料的，错误的值
                    null            程序级的，意料内的，正确的空值
                    0
                    -0
                    NaN
                    ""
				
6.自动垃圾回收

				
7.作用域

            1.全局定义的对象是global的属性，全局访问
					
                    var x=0 <==> global.x=0 <==> this.x=0
                    var x=function(){} <==> global.x=function(){} <==> this.x=function(){}
                    function x(){} <==> global.x=function(){} <==> this.x=function(){}
					
            2.函数内部定义的对象在函数作用域内全局访问,无论在函数中的声明位置
					
8.== ===

            对于基本类型:数字，字符串，boolean，是值的比较
            对于对象类型:Date Object Array 是引用值的比较
            
                    == ===  相等 严格相等

                    new String("123")=="123"        true
                    new String("123")==="123"       false
					
                    null==undefined                 true
                    "0"==0                          true
                    0=false                         true
                    "0"=false                       true
				

9.l in r

            l是一个string或可转string的数值
            r是一个object
            判断左“string”是否是右对象的一个key
					
                    var x={m:1,n:2}
					
                    "m"         in  x   true
                    "n"         in 	x   true
                    "toString"  in 	x   true
					
                    var x=[1,2,3]
					
                    "0" in x    true
                    1	in x    true	
                    2	in x    true	
                    3	in x    false 比较key的存在而不是比较值的存在


10.l instanceof r

            l是一个对象实例
            r是一个函数名(js中的类是通过构造函数定义的，所以应该是个函数名)
            包含对父类的检测,prototype检测派生关系
					
                    var x=new Date();

                    x instanceof Date			true
                    x instanceof Obeject		true
                    x instanceof Number			false
					
                    var x=[1,2,3,4]
					
                    x instanceof Array			true
                    x instanceof Obeject		true
                    x instanceof Number			false
					

11.eval()能不用就不用

            代码解释器
					
                    eval("var x = function F(){}"); 定义了一个函数
					

12.typeof

            undefined  						“undefined”
            null							“object”
            true or false					"boolean"
            数字 NaN							"number"
            “123”							"string"
            function x(){}					"function"   函数虽然也是对象 但是js特殊对待
            内置非函数对象						"object"
            非内置宿主对象 bom dom 			宿主各自实现
					

13.delete(ES5 strict mode delete禁止使用)

            删除对象属性或删除数组元素
					
                    var x={m:1,n:2}
                    delete x.m
                    "m" in x        false
					
                    var x=[1,2,3]
                    delete a[2]
                    2 in a			false
                    x.length		3		位置并没有空出来
					
                    不能通过delete删除全局定义的变量
                    var x=1;
                    delete x                   	//error
                    delete global.x				//correct							

14.for in ; for

                     for(var pro in obj){                遍历对象“可枚举的”属性,方法
                            console.log(obj[pro])
                     }
					
                    for(var i=0;i<[1,2,4].length;i++){  遍历数组
					
                     }


15.try{}catch(e){}finally{}




16.use strict 可以不研究 代码更严谨


17.对象特性及分类

            1.看成是“字符(属性名,属性名一定是string)”到基本类型或对象类型无序集合(散列,字典,关联数组)
            2.原型继承是js对象的核心特性
            3.动态加减属性
					
            分类:
            1.EMACScript内置对象或类:Array，Function，Date，RegExp
            2.宿主:web浏览器中的dom,bom(任何HTMLElement,Navigator)，非web浏览器中的其他宿主
            3.自定义对象
            4.属性分为:自定义属性,原型中继承下来的属性

18.创建对象
	
            1.对象直接量:
                    var x={a:1,b:2}       	原型是Object.prototype
					
					
            2.new 创建原型是构造函数的.prototype
                    var x=new Date()        Date.prototype
                    var x=new Array         Array.prototype	
                    var x=new Function()    Function,prototype
					
					
            3.Object.create({})
			

19.JSON.stringfy(Obj)  JSON.parse(json string)



 
				
				
20.html不区分大小写;js,xhtml区分大小写



21.ES5的数组 

                    [1,2,3].forEach(
                            function(e){
					
                            }
                    );
					
                    var newArray=[1,2,3].map(
                            function(x){
                                return  op x;
                            }
                    );
					
                    [1,2,3].sort(function(x1,x2){
					            return  x1>x2
                    });
					
					
22.函数

                    1.参数化输入(变长arguments),可有返回值,可一次定义,多次调用过程体
                    2.每次调用都隐式伴随this传递(当函数挂载在一个对像上时,函数调用就是方法调用,this就是该对象;如果仅仅是函数调用this是undefined)
	                3.可嵌套定义
					
					
	                调用方式:
	                1.函数调用
	                2.方法调用
	                3.构造器调用
	                4.间接调用 call apply
	                  函数可以作为任何对象的方法来调用，即使函数没有在该方法中定义
	                5.匿名调用
	                   (function(x){})(1)
	                   (function F(x,y){})(1,2)
					  	  
					
