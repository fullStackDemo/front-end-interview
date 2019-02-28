## 相关知识点 ##

> 数据类型、运算、对象、function、继承、闭包、作用域、原型链、事件、RegExp、JSON、Ajax、DOM、BOM、内存泄漏、跨域、异步加载、模板引擎、前端MVC、前端MVVM、路由、模块化、Http、Canvas、jQuery、ECMAScript 2015（ES6）、Node.js、AngularJS、Vue、React......

# Review #

## 1、介绍一下 JS 的基本数据类型 ##


    Undefined、Null、Boolean、Number、String、Symbol (new in ES 6)
    
   
> 深入了解基本类型和引用类型的值
>   
>  一个变量可以存放两种类型的值，基本类型的值（primitive values）和引用类型的值（reference values）

> ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：Undefined、Null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）



>### 基本数据类型的值是按值访问的。 ###



> - 基本类型的值是不可变的


    var str = "123hello321";     
    str.toUpperCase(); // 123HELLO321    
    console.log(str);  // 123hello321



> - 基本类型的比较是它们的值的比较

    var a = 1;
    var b = true;
    console.log(a == b);// true
    console.log(a === b);   // false
    
 





 
 



