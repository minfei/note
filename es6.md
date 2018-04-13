**ES6的了解**

> 新增模板字符串（为JavaScript提供了简单的字符串插值功能）、箭头函数（操作符左边为输入的参数，而右边则是进行的操作以及返回的值Inputs=>outputs。）、for-of（用来遍历数据—例如数组中的值。）arguments对象可被不定参数和默认参数完美代替。ES6将promise对象纳入规范，提供了原生的Promise对象。增加了let和const命令，用来声明变量。增加了块级作用域。let命令实际上就增加了块级作用域。ES6规定，var命令和function命令声明的全局变量，属于全局对象的属性；let命令、const命令、class命令声明的全局变量，不属于全局对象的属性。。还有就是引入module模块的概念


**let var const**

- let 允许你声明一个作用域被限制在块级中的变量、语句或者表达式
    let绑定不受变量提升的约束，这意味着let声明不会被提升到当前
    该变量处于从块开始到初始化处理的“暂存死区”。

- var 声明变量的作用域限制在其声明位置的上下文中，而非声明变量总是全局的
    由于变量声明（以及其他声明）总是在任意代码执行之前处理的，所以在代码中的任意位置声明变量总是等效于在代码开头声明

- const 声明创建一个值的只读引用 (即指针)
    这里就要介绍下 JS 常用类型
    String、Number、Boolean、Array、Object、Null、Undefined
    其中基本类型 有 Undefined、Null、Boolean、Number、String，保存在栈中；
    复合类型 有 Array、Object ，保存在堆中；

    基本数据当值发生改变时，那么其对应的指针也将发生改变，故造成 const申明基本数据类型时，
    再将其值改变时，将会造成报错， 例如 const a = 3 ; a = 5 时 将会报错；
    但是如果是复合类型时，如果只改变复合类型的其中某个Value项时， 将还是正常使用；

**箭头函数**

- 语法比函数表达式更短，并且不绑定自己的this，arguments，super或 new.target。这些函数表达式最适合用于非方法函数，并且它们不能用作构造函数。


**快速的让一个数组乱序**

```
var arr = [1,2,3,4,5,6,7,8,9,10];
arr.sort(function(){
    return Math.random() - 0.5;
})
console.log(arr);

```  
- 首先： 当return 的值

    - 小于 0 ，那么 a 会被排列到 b 之前；
    - 等于 0 ， a 和 b 的相对位置不变；
    - 大于 0 ， b 会被排列到 a 之前；

- 这里你会 发现起始 的时候数组是正序排列，每当进行一次排列的时候， 都会先随机一个随机数 （注意这里的每一次排列 指 每一个红框指一次排列， 共9次排列 ， 一次排列中可能存在多次比较）；

- 当一次排列的 随机数大于0.5 时 将会进行第二次比较， 当第二次随机数 仍然大于0.5 时 ，将会再 进行一次比较， 直到 随机数大于0.5 或者排列到第一位；

- 当一次排列的 随机数 小于0.5时 当前比较的两项 索引将不会改变 ，继续下一次 的排列；


**最快捷的数组求最大值**
```
var arr = [ 1,5,1,7,5,9];
   Math.max(...arr)  // 9
```   


**更短的数组去重写法**
```
[...newSet([2,"12",2,12,1,2,1,6,12,13,6])]
```  

**说说你对Promise的理解**

- 依照 Promise/A+ 的定义，Promise 有四种状态：
  - pending: 初始状态, 非 fulfilled 或 rejected.

  - fulfilled: 成功的操作.

  - rejected: 失败的操作.

  - settled: Promise已被fulfilled或rejected，且不是pending

- 另外， fulfilled 与 rejected 一起合称 settled
- Promise 对象用来进行延迟(deferred) 和异步(asynchronous ) 计算

**Promise 的构造函数**

- 构造一个 Promise，最基本的用法如下：

```
var promise = new Promise(function(resolve, reject) {

        if (...) {  // succeed

            resolve(result);

        } else {   // fails

            reject(Error(errMessage));

        }
    });
```

- Promise 实例拥有 then 方法（具有 then 方法的对象，通常被称为thenable）。它的使用方法如下：
```
promise.then(onFulfilled, onRejected)
```

- 接收两个函数作为参数，一个在 fulfilled 的时候被调用，一个在rejected的时候被调用，接收参数就是 future，onFulfilled 对应 resolve, onRejected 对应 reject

**什么是 Promise ？**

* Promise 就是一个对象，用来表示并传递异步操作的最终结果
* Promise 最主要的交互方式：将回调函数传入 then 方法来获得最终结果或出错原因
* Promise 代码书写上的表现：以“链式调用”代替回调函数层层嵌套（回调地狱）

**谈一谈你了解ECMAScript6的新特性？**

* 块级作用区域              `let a = 1;`
* 可定义常量                `const PI = 3.141592654;`
* 变量解构赋值              `var [a, b, c] = [1, 2, 3];`
* 字符串的扩展(模板字符串)  ` var sum = `${a + b}`;`
* 数组的扩展(转换数组类型)   `Array.from($('li'));`
* 函数的扩展(扩展运算符)     `[1, 2].push(...[3, 4, 5]);`
* 对象的扩展(同值相等算法)   ` Object.is(NaN, NaN);`
* 新增数据类型(Symbol)      `let uid = Symbol('uid');`
* 新增数据结构(Map)        ` let set = new Set([1, 2, 2, 3]);`
* for...of循环            `for(let val of arr){};`
* Promise对象            ` var promise = new Promise(func);`
* Generator函数          ` function* foo(x){yield x; return x*x;}`
* 引入Class(类)          ` class Foo {}`
* 引入模块体系            ` export default func;`
* 引入async函数[ES7]    
```
async function asyncPrint(value, ms) {
      await timeout(ms);
      console.log(value)
     }

```
**Object.is() 与原来的比较操作符 ===、== 的区别？**

-  == 相等运算符，比较时会自动进行数据类型转换
-  === 严格相等运算符，比较时不进行隐式类型转换
-  Object.is 同值相等算法，在 === 基础上对 0 和 NaN 特别处理

```
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

**什么是 Babel ？**

* Babel 是一个 JS 编译器，自带一组 ES6 语法转化器，用于转化 JS 代码。
这些转化器让开发者提前使用最新的 JS语法(ES6/ES7)，而不用等浏览器全部兼容。
* Babel 默认只转换新的 JS 句法(syntax)，而不转换新的API。
