

<< js, the Good parts >> 4.8

**Chapter 2: Grammar:**  
Js中的number 为 64位，  
 string为16位，单双引号都可，没有单独的字符类型，使用单字符的string来代表字符  
string是immutable不可变的，一旦创建，其值就不再可改变  
falsey value包括： false,  null,  undefined, empty string ‘’, 0, NaN  
for的使用有两种方式，一种是常规的for(xx; xx; xx)，还有一种是 for in，用于枚举property names or keys of an object，在用作第二种方式时，要注意检验这种Property是对象本身的还是从prototype中继承下来的：
~~~
for(myvar in obj){
	if( obj.hasOwnProperty(myvar) ){
	    xxxx
  	}
}
~~~

**Chapter 3: objects**  
在js中，除了number, string ,Boolean, null, undefined之外，全部为Objects类型，比如array, function, regular expression等都是Object ，Objects in java  script are mutable keyed collections。  
An object is a container of properties, where a property has a name and a value. A property name can be any string, including the empty string, a property value can be any javascript value except for undefined.  
Objects in javascript are class-free. Javascript includes a prototype linkage feature that allows one object to inherit the properties of another.  
Object literal： 对象字面值  
Object property name  可以是任何string，甚至可以为empty string，使用双引号，可以用也可以不用，当property name 是合法的javascript  name时，双引号可以省略，否则的话必须要使用双引号。  
获取属性值时两种方式： [ ] or xx.xx  
如果属性名为合法的javascript name ，推荐使用点获取法 object.property  
Objects通过reference进行传递，从来不会被copy  
每个object都被链接到一个prototype object from which it can inherit properties。  
All objects created from object literal are linked to Object.prototype, an  object that comes standard with javascript。  
可以使用 Object.create(type)；来创建prototype 为  type的对象。
在获取某个对象的属性值时，有时候会获取到其原型对象的属性值，这是不希望看到的，为防止这种情况发生，可以使用hasOwnProperty() 方法，这个方法是不检测prototype chain的，还可以使用typeof来检测属性值类型，对于不想要的排除掉。  
在使用for in来获取Object property值时，可能会得到不想要的值，得到的值也是没有固定顺序的；  
使用for（i=0; i<properties.length;i++）来获取时，不用担心原型的问题，而且会以正确的顺序出现。  
尽量避免或减少全局变量的使用，可以使用这种方法：定义唯一一个全局object，然后将需要用的全局变量都定义为此object property即可。

**Chapter 4: functions**  
Objects are collections of name/value pairs having a hidden link to a prototype object。    
Functions objects are linked to a Function.prototype(it is linked to Object.prototype )  
Every function is also created with a prototype property， its value is an object with a constructor property whose value is the function.  
函数是object类型，因此可以作为object使用，比如可以保存为变量，array，作为参数传入或作为返回值返回，可以有methods。  
Function除了定义时的参数之外，还有两个额外的参数：this, arguments  
其中，this的值非常重用，根据invocation pattern的不同赋值方式也有所不同。  

Method invocation pattern:   
函数被作为一个对象的method被调用，此时this指代这个对象。  

Function invocation pattern:   
函授不是作为一个对象的method被调用时，此时this指向global object。  

这个是一个设计错误，当一个函数作为一个对象的inner function时，this并不是指向其outer context object，解决这个问题的方法是，在其outer context中，定义var that = this；然后在次函授内部就可以使用that作为outer context了。  

Constructor invocation pattern:  
Javascript is a prototypal inheritance(原型继承) language. That means that objects can inherit properties directly from other objects. The language is class-free. 这和java, c++等的类继承是根本的不同，但是javascript中new的引入使得javascript的原型继承理解起来有些混淆和难度。  
If a function is invoked with the new  prefix, then a new object will be created with a hidden link to the value of the function’s prototype member, and this will be bound to that new object。  
~~~
// create a constructor function called Quo, it makes an object with a status property
Var Quo = function(string){
	This.status = string;
};
//give all instances of Quo a public method called get_status
Quo.prototype.get_status = function(){
	Return this.status;
}
//make an instance of Quo
Var myQuo = new Quo(“confused”);
Console.log(myQuo.get_status());// return confused
~~~
Apply invocation pattern:  
The apply method let us construct an array of arguments to use to invoke a function. It also let us choose the value of this. The apply method takes two paremeters. The first is the value that should be bound to this, the second is an array of parameters。
~~~  
Var array = [3, 4];
Var sum = add.apply(null, array); 
~~~

Function的一个固有的默认参数 arguments非常有用，可以用来获取所有传入的参数。  
Arguments并不是一个真正的array，而是一个array-like object，这是一个设计上的失误，它虽然有length，但是却缺少所有的array methods。
Javascript allows the basic types of the language to be augmented.   
Adding a method to Object.prototype makes that method available to all objects. By augmenting Function.prototype, we can make a method available to all functions。  

Scope:   
Block scope: all variables defined in a block(凡是用大括号括起来的都是一个block)  are not visible from outside of the block.
但在javascript中没有block scope，只有function scope，也即a variable defined everywhere within a function is visible everywhere within the function。  

Closure :  
Inner functions get access to the parameters and variables of the function they are defined within except this and arguments.  

Module:  
js中使用global variable不太好，使用funtion内部定义的变量在外面又无法访问，通常结合利用function scope and closure来实现module:   
The general pattern of a module if a function that defines private variables and functions;  creates privileged functions which, through closure, will have access to the private variables and functions; and that returns the privileged functions or stores them in an accessible place.

Currying :   
allows to produce a new function by combining a function and an argument.  
Var add1 = add.curry(1);  
The add1 function adds 1 to add function’s arguments.
JS 里面没有curry这个方法，需要augment Function.prototype。
