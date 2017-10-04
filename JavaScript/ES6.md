1.模块
  + 当用export default XXX 导出时,就用 import XXX 导入(不带大括号)
  + 一个文件里,有且只能有一个export default,但可以有多个export
  + 当用export XXX 时,就用import { XXX } 导入 (带上大括号)
  + 当一个文件里,既有一个 export default XXX,又有多个export YYY 或者 export ZZZ,导入就用import XXX, {YYY, ZZZ}
  + 当一个文件里出现多个 export 导出很多模块,导入时除了一个一个导入,也可以用import * as jsFile
  
  
  
        ES5模块
        
        exports=module.exports
        
        exports=function A(){}
        
        var A=require(…);
        A()
        or
        require(…)()
        
        export.m=function A(){}
        require(…).m()
  
  
  
2.变量
  + let表示局部变量,const表示局部常量(不污染全局)
  
3.解构
  + 按照一定**模式**，从数组和对象中提取值，对变量进行赋值，这被称为解构
  + 数组
  
        let [a, b, c] = [1, 2, 3];
        let [foo, [[bar], baz]] = [1, [[2], 3]];
  
  + 对象
        
        let { foo, bar } = { foo: "aaa", bar: "bbb" };
        
        let { baz } = { foo: "aaa", bar: "bbb" };
        //baz=undefined
        
        let obj = { first: 'hello', last: 'world' };
        let { first: f, last: l } = obj;
        //f='hello'
        //l='world'
        
  + 字符串
  
        const [a, b, c, d, e] = 'hello';
        a // "h"
        b // "e"
        c // "l"
        d // "l"
        e // "o"
        
  + 函数参数
  
        function add([x, y]){
          return x + y;
        }
        
        add([1, 2]); // 3


4.模版字符
+ 模版字符(类似groovy)
  
        const name = 'lux’;
        console.log(`hello ${name}`);
        
5.箭头函数

+ 不需要function
+ 不需要return 
+ 函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象


6.Class

+ 模版

        class Point extends BaseClass{
            c={x:1,y:2};
            d=2;
            e=function(){
            
            };

            static classMethod() {
                return 'hello';
              }
          constructor(x, y) {
            this.x = x;
            this.y = y;
          }
        
          toString() {
            return '(' + this.x + ', ' + this.y + ')';
          }
        }
        
        let p=new Point();
        
        Point.classMethod();
        p.a;p.b;p.c
        
        
        
        const Point=class Point{}