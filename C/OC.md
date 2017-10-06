1.数据类型
+ 与c一致[C](https://github.com/huanx1983/Programming-knowledge-assets/blob/master/C.md)
+ 特殊的 BOOL , id 类型(类似void*指针)

2.OO与过程函数的结合应用,OO语法类似java,概念少于CPP

3.对象的的定义

        NewClassName.h
        
        external int globalVar;
        @interface NewClassName :ParentClassName(CategoryName)<Protocol1,Protocal2,...>
        
        {
        
            type var1;
            type var2;
            ...
        
        }
            @property type property1;
            @property type property1;

            
            +(type) ClassMethod;
            
            -(type) ObjectMethod;
        
        @end
        
        
        
        
        NewClassName.m
        
        
        @interface NewClassName()  //未命名分类,直接interface和implement在 *.m 文件中,可以定义property
        
        int globalVar=0;
        static int fileGlobalVar=0;
        @implements NewClassName
        {
            type implementVar1;
            type implementVar2;
            ...

        }
            @synthesize property1,property2;
        
            +(type) ClassMethod
            {
             
             static type methodStaticvar1  =0;
                                
            }
                   
            -(type) ObjectMethod
             {
             
             static type methodStaticvar2  =0;
                    
            }
        @end
        
        
        object.property1 <==>object.property1() or object.setProperty1(...)
        

4.#import代替#include解决重复导入问题

5.C in OC
+ 就是c语言中的函数,函数不属于class,*.h和*.m中分别定义和实现

+ Block(OC对C的扩展)
    
        BlockReturnType (^BlockName)(arg1Type,arg2Type)=^(arg1Type arg1,arg2Type arg2){
    
            BlockReturnType var=1;
            return var;
    
        }
        
+ 结构
        
        typedef struct _S{
        
            int a;
            int b;
        
        } S;
        



6.OC对象本质




    

