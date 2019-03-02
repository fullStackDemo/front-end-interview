## 相关知识点 ##

> 数据类型、运算、对象、function、继承、闭包、作用域、原型链、事件、RegExp、JSON、Ajax、DOM、BOM、内存泄漏、跨域、异步加载、模板引擎、前端MVC、前端MVVM、路由、模块化、Http、Canvas、jQuery、ECMAScript 2015（ES6）、Node.js、AngularJS、Vue、React......

# Review #

## 1、介绍一下 JS 的基本数据类型 ##


    Undefined、Null、Boolean、Number、String、Symbol (new in ES 6)

## 知识扩展： ##

### 基础类型 ###
   
> 深入了解基本类型和引用类型的值
>   
>  一个变量可以存放两种类型的值，基本类型的值（primitive values）和引用类型的值（reference values）

> ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：Undefined、Null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）



>**基本数据类型的值是按值访问的。**



> - 基本类型的值是不可变的


    var str = "123hello321";     
    str.toUpperCase(); // 123HELLO321    
    console.log(str);  // 123hello321



> - 基本类型的比较是它们的值的比较

    var a = 1;
    var b = true;
    console.log(a == b);// true
    console.log(a === b);   // false
    
 

> 上面 a 和 b 的数据类型不同，但是也可以进行值的比较，这是因为在比较之前，自动进行了数据类型的 隐式转换

> == : 只进行值的比较
> 
> === : 不仅进行值得比较，还要进行数据类型的比较


> - 基本类型的变量是存放在栈内存（Stack）里的


    var a,b;
    a = "zyj";
    b = a;
    console.log(a);   // zyj
    console.log(b);   // zyj
    a = "呵呵";   // 改变 a 的值，并不影响 b 的值
    console.log(a);   // 呵呵
    console.log(b);   // zyj


> 图解如下：栈内存中包括了变量的标识符和变量的值

![](https://segmentfault.com/img/bVCunf)


### 引用类型 ###



> 除过上面的 6 种基本数据类型外，剩下的就是引用类型了，统称为 Object 类型。细分的话，有：Object 类型、Array 类型、Date 类型、RegExp 类型、Function 类型 等。

> **引用类型的值是按引用访问的**

> 
- 引用类型的值是可变的

    var obj = {name:"zyj"};   // 创建一个对象
    obj.name = "percy";   // 改变 name 属性的值
    obj.age = 21; // 添加 age 属性
    obj.giveMeAll = function(){
      return this.name + " : " + this.age;
    };// 添加 giveMeAll 方法
    obj.giveMeAll();
 

> - 引用类型的比较是引用的比较

    var obj1 = {};// 新建一个空对象 obj1
    var obj2 = {};// 新建一个空对象 obj2
    console.log(obj1 == obj2);// false
    console.log(obj1 === obj2);   // false
    

> 因为 obj1 和 obj2 分别引用的是存放在堆内存中的2个不同的对象，故变量 obj1 和 obj2 的值（引用地址）也是不一样的！


> 引用类型的值是保存在堆内存（Heap）中的对象（Object）
> 


> 与其他编程语言不同，JavaScript 不能直接操作对象的内存空间（堆内存）。

    var a = {name:"percy"};
    var b;
    b = a;
    a.name = "zyj";
    console.log(b.name);// zyj
    b.age = 22;
    console.log(a.age); // 22
    var c = {
      name: "zyj",
      age: 22
    };



> 图解如下：

> - 栈内存中保存了变量标识符和指向堆内存中该对象的指针

> - 堆内存中保存了对象的内容

![](https://segmentfault.com/img/bVCuGx)



> **检测类型**

> typeof：经常用来检测一个变量是不是最基本的数据类型

    var a;
    typeof a;// undefined
    
    a = null;
    typeof a;// object
    
    a = true;
    typeof a;// boolean
    
    a = 666;
    typeof a;// number 
    
    a = "hello";
    typeof a;// string
    
    a = Symbol();
    typeof a;// symbol
    
    a = function(){}
    typeof a;// function
    
    a = [];
    typeof a;// object
    a = {};
    typeof a;// object
    a = /aaa/g;
    typeof a;// object   
    


> instanceof：用来判断某个构造函数的 prototype 属性所指向的对象是否存在于另外一个要检测对象的原型链上



> 简单说就是判断一个引用类型的变量具体是不是某种类型的对象
    
    ({}) instanceof Object  // true
    ([]) instanceof Array   // true
    (/aa/g) instanceof RegExp   // true
    (function(){}) instanceof Function  // true
    
    
    
## 2、介绍一下 JS 有哪些内置对象 ##

    Object 是 JavaScript 中所有对象的父对象
    数据封装类对象：Object、Array、Boolean、Number、String
    其他对象：Function、Argument、Math、Date、RegExp、Error
    
## 3、列举几条 JavaScript 的基本代码规范 ##

    （1）不要在同一行声明多个变量
    （2）如果你不知道数组的长度，使用 push
    （3）请使用 ===/!== 来比较 true/false 或者数值
    （4）对字符串使用单引号 ''(因为大多时候我们的字符串。特别html会出现")
    （5）使用对象字面量替代 new Array 这种形式
    （6）绝对不要在一个非函数块里声明一个函数，把那个函数赋给一个变量。浏览器允许你这么做，但是它们解析不同
    （7）不要使用全局函数
    （8）总是使用 var 来声明变量，如果不这么做将导致产生全局变量，我们要避免污染全局命名空间
    （9）Switch 语句必须带有 default 分支
    （10）使用 /**...*/ 进行多行注释，包括描述，指定类型以及参数值和返回值
    （11）函数不应该有时候有返回值，有时候没有返回值
    （12）语句结束一定要加分号
    （13）for 循环必须使用大括号
    （14）if 语句必须使用大括号
    （15）for-in 循环中的变量应该使用 var 关键字明确限定作用域，从而避免作用域污染
    （16）避免单个字符名，让你的变量名有描述意义
    （17）当命名对象、函数和实例时使用驼峰命名规则
    （18）给对象原型分配方法，而不是用一个新的对象覆盖原型，覆盖原型会使继承出现问题
    （19）当给事件附加数据时，传入一个哈希而不是原始值，这可以让后面的贡献者加入更多数据到事件数据里，而不用找出并更新那个事件的事件处理器
    
    
## 4、call和apply的作用是什么？区别是什么？ ##

    call和apply的功能基本相同，都是实现继承或者转换对象指针的作用；
    唯一不通的是前者参数是罗列出来的，后者是存到数组中的；
    call或apply功能就是实现继承的；与面向对象的继承extends功能相似；但写法不同；
    语法：
    .call(对象[,参数1，参数2,....]);//此地参数是指的是对象的参数，非方法的参数；
    .apply(对象,参数数组)//参数数组的形式:[参数1，参数2,......]
    

## 5、 push()-pop()-shift()-unshift()分别是什么功能？ ##

    push 方法
    将新元素添加到一个数组中，并返回数组的新长度值。
    var a=[1,2,3,4];
    a.push(5);
    pop 方法
    移除数组中的最后一个元素并返回该元素。
    var a=[1,2,3,4];
    a.pop();
    shift 方法
    移除数组中的第一个元素并返回该元素。
    var a=[1,2];
    alert(a.shift());
    unshift 方法
    将指定的元素插入数组开始位置并返回该数组。
    
    
## 6、表述您对javascript this工作原理的理解 ##

    在函数中：this 通常是一个隐含的参数。
    在函数外（顶级作用域中）：在浏览器中this 指的是全局对象；在Node.js中指的是模块(module)的导出(exports)。
    传递到eval()中的字符串：如果eval()是被直接调用的，this 指的是当前对象；如果eval()是被间接调用的，this 就是指全局对象。
    
  [更多了解](http://www.ruanyifeng.com/blog/2018/06/javascript-this.html)


  [You-Don-t-Know-JS-this-Object-Prototypes](https://pepa.holla.cz/wp-content/uploads/2016/08/You-Don-t-Know-JS-this-Object-Prototypes.pdf)
    
## 7、介绍一下 JavaScript 原型，原型链，它们有何特点？

	每个对象都会在其内部初始化一个属性，就是prototype(原型)，
	当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，
	那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，
	于是就这样一直找下去，也就是我们平时所说的原型链的概念。
	关系：instance.constructor.prototype = instance.__proto__
	特点：JavaScript对象是通过引用来传递的，
	我们创建的每个新对象实体中并没有一份属于自己的原型副本，
	当我们修改原型时，与之相关的对象也会继承这一改变。
	当我们需要一个属性时，JavaScript引擎会先看当前对象中是否有这个属性，
	如果没有的话，就会查找它的prototype对象是否有这个属性，
	如此递推下去，一致检索到Object内建对象。
	function Func(){}
	Func.prototype.name = "Xiaosong";
	Func.prototype.getInfo = function() {
	   return this.name;
	}
	var person = new Func();
	console.log(person.getInfo());//"Xiaosong"
	
	

## 8、JavaScript 有几种类型的值？能否画一下它们的内存图？

	栈：原始数据类型（Undefined，Null，Boolean，Number，String）
	堆：引用数据类型（对象、数组、函数）
	两种类型的区别：
	//存储位置不同
	原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
	引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体。
	
![](https://img-blog.csdn.net/20160826144418161)

![](https://img-blog.csdn.net/20180515200511436?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ppYW5nanVhbmphdW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![](https://img-blog.csdn.net/20180515200544240?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ppYW5nanVhbmphdW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

	总结区别
	　　a 声明变量时不同的内存分配：
	　　1）原始值：存储在栈（stack）中的简单数据段，也就是说，它们的值直接存储在变量访问的位置。
	　　　　这是因为这些原始类型占据的空间是固定的，所以可将他们存储在较小的内存区域 – 栈中。这样存储便于迅速查寻变量的值。
	
	　　2）引用值：存储在堆（heap）中的对象，也就是说，存储在变量处的值是一个指针（point），指向存储对象的内存地址。这是因为：引用值的大小会改变，所以不能把它放在栈中，否则会降低变量查寻的速度。相反，放在变量的栈空间中的值是该对象存储在堆中的地址。地址的大小是固定的，所以把它存储在栈中对变量性能无任何负面影响。
	
	　　b 不同的内存分配机制也带来了不同的访问机制　　
	
	　　1）在javascript中是不允许直接访问保存在堆内存中的对象的，所以在访问一个对象时，首先得到的是这个对象在堆内存中的地址，然后再按照这个地址去获得这个对象中的值，这就是传说中的按引用访问。
	　　2）而原始类型的值则是可以直接访问到的。　　
	
	　　c 复制变量时的不同　　
	　　1）原始值：在将一个保存着原始值的变量复制给另一个变量时，会将原始值的副本赋值给新变量，此后这两个变量是完全独立的，他们只是拥有相同的value而已。
	　　2）引用值：在将一个保存着对象内存地址的变量复制给另一个变量时，会把这个内存地址赋值给新变量，也就是说这两个变量都指向了堆内存中的同一个对象，他们中任何一个作出的改变都会反映在另一个身上。（这里要理解的一点就是，复制对象时并不会在堆内存中新生成一个一模一样的对象，只是多了一个保存指向这个对象指针的变量罢了）。多了一个指针　
	　　
	　　d 参数传递的不同（把实参复制给形参的过程）　　
	　　首先我们应该明确一点：ECMAScript中所有函数的参数都是按值来传递的。
	　　但是为什么涉及到原始类型与引用类型的值时仍然有区别呢？还不就是因为内存分配时的差别。 　
	　　1）原始值：只是把变量里的值传递给参数，之后参数和这个变量互不影响。
	　　2）引用值：对象变量它里面的值是这个对象在堆内存中的内存地址，这一点你要时刻铭记在心！因此它传递的值也就是这个内存地址，这也就是为什么函数内部对这个参数的修改会体现在外部的原因了，因为它们都指向同一个对象。

## 9、JavaScript 如何实现继承？

	(1)构造继承
	(2)原型继承
	(3)实例继承
	(4)拷贝继承
	//原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。
	function Parent() { 
	    this.name = 'song';
	}
	function Child() {
	    this.age = 28;
	}
	Child.prototype = new Parent(); //通过原型,继承了Parent
	var demo = new Child();
	alert(demo.age);
	alert(demo.name); //得到被继承的属性
	
### 扩展理解：
既然要实现继承，那么首先我们得有一个父类，代码如下：

	// 定义一个动物类
	function Animal (name) {
	  // 属性
	  this.name = name || 'Animal';
	  // 实例方法
	  this.sleep = function(){
	    console.log(this.name + '正在睡觉！');
	  }
	}
	// 原型方法
	Animal.prototype.eat = function(food) {
	  console.log(this.name + '正在吃：' + food);
	};
	
**1、原型链继承**

核心： 将父类的实例作为子类的原型

	function Cat(){ 
	}
	Cat.prototype = new Animal();
	Cat.prototype.name = 'cat';
	
	//　Test Code
	var cat = new Cat();
	console.log(cat.name);
	console.log(cat.eat('fish'));
	console.log(cat.sleep());
	console.log(cat instanceof Animal); //true 
	console.log(cat instanceof Cat); //true
	
特点：

>1 非常纯粹的继承关系，实例是子类的实例，也是父类的实例
>
>2 父类新增原型方法/原型属性，子类都能访问到

>3 简单，易于实现
>
>

缺点：

>1 要想为子类新增属性和方法，必须要在new Animal()这样的语句之后执行，不能放到构造器中
无法实现多继承

>2 来自原型对象的所有属性被所有实例共享（来自原型对象的引用属性是所有实例共享的）
>
>3 创建子类实例时，无法向父类构造函数传参
>


推荐指数：★★（3、4两大致命缺陷）

**2、构造继承**

核心：使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）

	function Cat(name){
	  Animal.call(this);
	  this.name = name || 'Tom';
	}
	
	// Test Code
	var cat = new Cat();
	console.log(cat.name);
	console.log(cat.sleep());
	console.log(cat instanceof Animal); // false
	console.log(cat instanceof Cat); // true
	
特点：

>1 解决了1中，子类实例共享父类引用属性的问题
>
>2 创建子类实例时，可以向父类传递参数
>
>3 可以实现多继承（call多个父类对象）

缺点：

>1 实例并不是父类的实例，只是子类的实例
>
>2 只能继承父类的实例属性和方法，不能继承原型属性/方法
>
>3 无法实现函数复用，每个子类都有父类实例函数的副本，影响性能
>


推荐指数：★★（缺点3)

**3、实例继承**

核心：为父类实例添加新特性，作为子类实例返回

	function Cat(name){
	  var instance = new Animal();
	  instance.name = name || 'Tom';
	  return instance;
	}
	
	// Test Code
	var cat = new Cat();
	console.log(cat.name);
	console.log(cat.sleep());
	console.log(cat instanceof Animal); // true
	console.log(cat instanceof Cat); // false


特点：

>1 不限制调用方式，不管是new 子类()还是子类(),返回的对象具有相同的效果

缺点：

>1 实例是父类的实例，不是子类的实例
>
>2 不支持多继承


推荐指数：★★

**4、拷贝继承**
	
	function Cat(name){
	  var animal = new Animal();
	  for(var p in animal){
	    Cat.prototype[p] = animal[p];
	  }
	  Cat.prototype.name = name || 'Tom';
	}
	
	// Test Code
	var cat = new Cat();
	console.log(cat.name);
	console.log(cat.sleep());
	console.log(cat instanceof Animal); // false
	console.log(cat instanceof Cat); // true

特点：

>1 支持多继承


缺点：

>1 效率较低，内存占用高（因为要拷贝父类的属性）


>2 无法获取父类不可枚举的方法（不可枚举方法，不能使用for in 访问到）


推荐指数：★（缺点1）

**5、组合继承**

核心：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用


