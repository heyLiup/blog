## 原型和原型链

 我们写一个构造函数并创建一个对象
```
function Person() {

}
var person = new Person();
person.name = 'zhangsan';
console.log(person.name) // zhangsan
```
有一些概念
- prototype  
    1. 指向的是一个对象，是构造函数创建实例的原型
    2. 只有函数才有prototype属性（由bind返回的函数没有）
    
- __proto__  
    1. 每一个js对象都具有的属性，指向该对象的原型（null没有）
    2. 原型链就是由__proto__构成的
- constructor
    1. 这时，每个原型都有一个constructor属性指向与其关联的构造函数
- 原型链
    1. 当我们去读取一个原型的属性时，在原型上没有找到，就会通过__proto__向原型的原型读取，一直找到顶层为止
    2. 既然原型也是对象，那么我们就可以通过new Object()来创建
    所以原型也是通过Object构造函数产生的  
    3. Object.prototype的原型是什么？ (null)  
       null代表着此处不该有值，意味着Object.prototype是原型链的终点

---

有一些细节
-  我们生成的实例对象是没有constructor属性的，它会去它的构造函数里读取
-  那么__proto__是哪来的？实例对象没有从他的构造函数中获取到__proto__,他是来自于Object.prototype
-  获得对象的原型 ES5里 Object.getPrototypeOf(person)
```
console.log(Object.getPrototypeOf(person) === Person.prototype) // true
```
- 为什么之前没有说继承呢？ 引用《你不知道的JavaScript》中的话
>    继承意味着复制操作，然而 JavaScript 默认并不会复制对象的属性，相反，JavaScript 只是在两个对象之间创建一个关联，这样，一个对象就可以通过委托访问另一个对象的属性和函数，所以与其叫继承，委托的说法反而更准确些。




    


