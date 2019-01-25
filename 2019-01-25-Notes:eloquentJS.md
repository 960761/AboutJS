
《eloquent JS》 4.6

此书有免费电子版和代码测试环境：  

<font color=red>电子版地址：http://eloquentjavascript.net/  （此为第三版）  
Code test : http://eloquentjavascript.net/code/ （此为第三版练习测试网址，但是目前好像不可用）  
https://eloquentjavascript.net/2nd_edition/code/ （此为第二版书籍的代码测试环境，和第三版内容有些小差别）</font>  

此书的内容相比其它的一些入门书籍，内容非常全面，而且要有一定的编程基础，每单元给的小练习也都很不错。

**Chapter 1: values, types and operators**  
介绍了javascript中四种基本的数值类型：number, string, Boolean, undefined(null)  
2015以后的javascript引入let，等同于var，除了一些细微的差别，var定义的变量范围最小就是function scope，但是let 定义的变量可以将范围缩小到更小的block。  
还介绍了一些基本的运算符；  

**Chapter 2: program structure**
介绍了program的构成以及一些简单的流程控制语句：if, while, for

**Chapter 3: functions**
介绍了function的三种方法：  
第一，	像普通变量一样定义 var f = function(){xxxx};  
第二，	声明 function f(){ xxxx }  
第三，	使用箭头定义法 var f= () =>{xxxx};  这种方式验证失败，不知道是不是不支持的原因。  
还介绍了一种常用的编程思维： 递归思想。

**Chapter 4: Data structures: objects and arrays**  
Value.x, value[x]都用来获取value的property值，除了undefined, null外的任何变量都有property值，  
这两种获取属性值的方式有些差别，比如str.length 等同于 str[“length”]，而且dot方式只能适用于合乎变量名规定的property，所以如果property name为2， joe hohn，那么只能使用 [ ] 来获取。  
Object.keys(object)返回所有的Property name   
“pro” in anObject 可以用来判断 名字为 pro的属性值是否是 anObject的一个属性  
Object.assign(o1,o2); 将o2的copy到 o1  
对于number, string, boolean类型变量，其值是immutable的，也即不能更改的；  
对于object，其值则是可以改变的，也即其property可以改变。  
三种基本类型不是Object, array是object  
JSON： JSON.stringify(),  JSON.parse()

**Chapter 5: high-order functions**  
Functions that operate on other functions , either by taking them as arguments or by returning them, are called high-order functions.  
可以理解为函数里面套函数，将函数当成一个value看待，  
如array中的 forEach(), filter(), map(),reduce()等，都是高阶函数，它们都是对array中的每个ele运行一个函数。  
这一章的内容主要是介绍了array的一些高阶函数的使用，array共提供了七个高阶函数：every(), some(), forEach(),filter(), map(), reduce(), reduceRight()。  
这七个高阶函数的内部实现机理弄清楚，很容易理解并使用，还可以编写自己的高阶函数。

**Chapter 6 objects in javascript**  
介绍javascript中的OO概念，OO概念都能理解，但是放到javascript中，再加上一些语法形式很别扭，理解起来很别扭。这一章的内容需要其他书籍的补充，有待加强。

**Chapter 7: project**  

**Chapter 8: bugs and errors**  

**Chapter 9: regular expressions**  

**Chapter 10: modules**   
Var plusOne = Function(“n”, “return n+1;”);  
Console.log(plusOne(4));  
CommonJS modules:   
