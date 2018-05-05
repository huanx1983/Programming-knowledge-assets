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
        
        
7.Bast Practise
+ let取代var
+ const取代var(特别是全局范围)

+ 单引号取代双引号
        
        const a = "foobar";  bad
        const a = 'foobar';  good
        
+ 数组对变量赋值优先使用解构
        
        const arr = [1, 2, 3, 4];
        
        // bad
        const first = arr[0];
        const second = arr[1];
        
        // good
        const [first, second] = arr;
        
+ 函数的参数如果是对象成员优先使用解构

        // bad
        function getFullName(user) {
          const firstName = user.firstName;
          const lastName = user.lastName;
        }
        
        // good
        function getFullName(obj) {
          const { firstName, lastName } = obj;
        }
        
        // best
        function getFullName({ firstName, lastName }) {
        }
+ 函数返回多值时优先使用解构

        // bad
        function processInput(input) {
          return [left, right, top, bottom];
        }
        
        // good
        function processInput(input) {
          return { left, right, top, bottom };
        }
        
        const { left, right } = processInput(input);
        
+ Class代替prototype

        // bad
        function Queue(contents = []) {
          this._queue = [...contents];
        }
        Queue.prototype.pop = function() {
          const value = this._queue[0];
          this._queue.splice(0, 1);
          return value;
        }
        
        // good
        class Queue {
          constructor(contents = []) {
            this._queue = [...contents];
          }
          pop() {
            const value = this._queue[0];
            this._queue.splice(0, 1);
            return value;
          }
        }
        
+ extends实现继承

        // bad
        const inherits = require('inherits');
        function PeekableQueue(contents) {
          Queue.apply(this, contents);
        }
        inherits(PeekableQueue, Queue);
        PeekableQueue.prototype.peek = function() {
          return this._queue[0];
        }
        
        // good
        class PeekableQueue extends Queue {
          peek() {
            return this._queue[0];
          }
        }
        
+ import 取代 require

        // bad
        const moduleA = require('moduleA');
        const func1 = moduleA.func1;
        const func2 = moduleA.func2;
        
        // good
        import { func1, func2 } from 'moduleA';
        
+ export取代module.exports

        // commonJS的写法
        var React = require('react');
        
        var Breadcrumbs = React.createClass({
          render() {
            return <nav />;
          }
        });
        
        module.exports = Breadcrumbs;
        
        // ES6的写法
        import React from 'react';
        
        class Breadcrumbs extends React.Component {
          render() {
            return <nav />;
          }
        };
        
        export default Breadcrumbs;

        
+ 如果模块默认输出一个函数，函数名的首字母应该小写

        function makeStyleGuide() {
        }
        
        export default makeStyleGuide;
        
+ 如果模块默认输出一个对象，对象名的首字母应该大写

        const StyleGuide = {
          es6: {
          }
        };
        
        export default StyleGuide;
+ http://es6.ruanyifeng.com/#docs/style
