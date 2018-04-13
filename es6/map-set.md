
## Set

> 它类似于数组，但是成员的值都是唯一的，没有重复的值。 Set函数可以接受一个数组（或类似数组的对象）作为参数，用来初始化。

```javascript
var set = new Set([1, 2, 3, 4, 4]);
[...set]
// [1, 2, 3, 4]

var s = new Set();
[2, 3, 5, 4, 5, 2, 2].map(x => s.add(x));
for (let i of s) {
  console.log(i);
}
// 2 3 5 4
```
- set内部的元素可以遍历for...of...
- 四个操作方法：
  - add(value)：添加某个值，返回Set结构本身。
  - delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。
  - has(value)：返回一个布尔值，表示该值是否为Set的成员。
  - clear()：清除所有成员，没有返回值

### Map

> Map结构提供了“值—值”的对应，是一种更完善的Hash结构实现。如果你需要“键值对”的数据结构，Map比Object更合适。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。

```javascript
let iterable = new Map([['a', 1], ['b', 2], ['c', 3]]);

for (let entry of iterable) {
  console.log(entry);
}
// ['a', 1]
// ['b', 2]
// ['c', 3]

for (let [key, value] of iterable) {
  console.log(value);
}

```

- 实例属性和方法：size、set、get、has、delete、clear
- 遍历方法：keys（）、values（）、entries（）、forEach（）

```javascript
var m = new Map();
var o = {p: "Hello World"};

m.set(o, "content")
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false

```

### 传参与解构

```javascript
const full = ({ first, last }) => first + ' ' + last;
// 等同于
function full(person) {
  return person.first + ' ' + person.last;
```

### 简化回调都可以用箭头代替

```javascript
// 正常函数写法
[1,2,3].map(function (x) {
  return x * x;
});
// 箭头函数写法
[1,2,3].map(x => x * x);
// 正常函数写法
var result = values.sort(function (a, b) {
  return a - b;
});
// 箭头函数写法
var result = values.sort((a, b) => a - b);
```

### 与rest结合

```javascript
const numbers = (...nums) => nums;
numbers(1, 2, 3, 4, 5)
// [1,2,3,4,5]
```

### this

箭头函数有几个使用注意点。

（1）函数体内的`this`对象，就是**定义时所在的对象，而不是使用时所在的对象**。

（2）**不可以当作构造函数**，也就是说，不可以使用`new`命令，否则会抛出一个错误。

（3）不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，**可以用Rest参数代替**。

（4）不可以使用`yield`命令，因此箭头函数**不能用作Generator函数**。

箭头函数可以让`this`指向固定化，这种特性很有利于封装回调函数。下面是一个例子，DOM事件的回调函数封装在一个对象里面。但是如果你需要使用函数内部的this，那只能使用function()

```javascript
var handler = {
  id: '123456',
  init: function() {
    document.addEventListener('click',
      event => this.doSomething(event.type), false);   //如果不用箭头函数那this指向document
  },
  doSomething: function(type) {
    console.log('Handling ' + type  + ' for ' + this.id);
  }
```

所以，箭头函数转成ES5的代码如下。

```javascript
// ES6
function foo() {
  setTimeout(() => {
    console.log('id:', this.id);
  }, 100);
// ES5
function foo() {
  var _this = this;    //这里引用了外面的this
  setTimeout(function () {
    console.log('id:', _this.id);
  }, 100);
```

另外，由于箭头函数没有自己的this，所以当然也就不能用call()、apply()、bind()这些方法去改变this的指向。

```javascript
(function() {
  return [
    (() => this.x).bind({ x: 'inner' })()
  ];
}).call({ x: 'outer' });
// ['outer']
```

### arguments,super,target

除了`this`，以下三个变量在箭头函数之中也是不存在的，指向外层函数的对应变量：`arguments`、`super`、`new.target`。

```javascript
function foo() {
  setTimeout(() => {
    console.log('args:', arguments);
  }, 100);
foo(2, 4, 6, 8)
// args: [2, 4, 6, 8]
```
