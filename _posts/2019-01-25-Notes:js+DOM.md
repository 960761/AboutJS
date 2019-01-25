
《javascript dom 编程艺术》 4.6星

Day 1 : 2017.5.11 page01-40  
     Javascript history and synax.  

Day 2 : 2017.5012 page 40-73  
介绍了几个常用的函数和使用Js 要注意的细节问题。

Day 3: 5.15 page73-191(中文版)  
     如何使用DOM+JS从html中提取元素的attribute信息并以另外一种方式显示出来，一般为，提取attribute信息，创建html元素，插入到html中。  
     如何私用DOM+JS 设置元素的显示信息，应该使用刷新className而非直接设置style的方式。  

Day 4: page191-end

## 概括笔记：  
这本书重点不是讲解DOM和JS的内容，而是讲解如何正确使用JS+DOM。

从这本书中了解到：  
1.	节点分好几种，其中元素节点，文本节点和属性节点是三种最为常用的类型，对不同的节点类型有时候适用的方法也不同，所以要注意节点的类型。例如element node就没有node value 属性，其nodevalue为null。

2.	使用DOM和JS的关键在于如何正确的使用，在使用时要注意几个原则：  
预留后路：即在不支持javascript的情况下页面也不至于崩溃，在使用某个方法或者属性前判断是否存在是否可用可以提高后兼容性；  

     分离原则：表示层CSS， 结构层HTML和行为层JS+DOM要尽量分离开来，例如control和event handler的绑定放在js而非Html中； 

     循序渐进：首先实现核心功能，然后再逐渐添加充实和完善。  

虽然DOM+JS可以填补网页的内容和修改样式，但还是应该使用HTML来填写必要的内容，使用CSS来设置显示样式，DOM+JS只用来充实网页内容，完善和定制显示效果。在可以使用HTML和CSS的情况下最好不要使用DOM+JS。  

3.	实现网页上面的某种效果往往有不止一种方式，选择实现方式时要思考两点：第一，哪种实现方式更简单容易实现；第二，哪种方式能得到更多浏览器的支持。

4.	使用DOM充实网页内容，通常为提取隐藏在元素attribute中的值提取出来以另一种方式呈现出来，通常为getAttribute, createElement/createTextNode, appendChild/insertBefore;

5.	使用DOM改变显示效果，elem.style.property = xx，但通常不使用这种方式，而是使用DOM修改元素绑定的css class name来实现。

## 细节笔记：  
Js遇到字符串时，单双引号 功能是相同的；

Web浏览器提供的预先定义好的对象称为 宿主对象；window是一个基础的宿主对象

节点类型：
 元素节点，如p, h2等
 文本节点，p元素里面的内容，必须包含在其他元素里面
 属性节点

Document.getElementById()，返回一个对象 javascript区分大小写，所以一定要写正确。

Element.getElementsByTagName() 返回对象数组,可以使用通配符“*”

If(sth) 和 if(sth!=null)功能相同

Object.getAttribute()
Object.setAttribute()  
通过setAttribute()方法对文档做出的修改，将是的文档在浏览器窗口的显示效果和/或行为发生相应变化，
但通过浏览器view source查看文档源代码时看到仍将是原来的属性值，
也即，setAttribute()方法做出的修改不会反映在文档本身的源代码里。
这种现象源自DOM的工作模式：先加载文档静态内容，再以动态方式对他们进行刷新，动态刷新不影响文档的静态内容。
这正是DOM的真正威力和诱人之处，对页面内容的刷新不需要最终用户在他们的浏览器里面执行页面刷新操作就可以实现。
