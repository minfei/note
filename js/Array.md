
### Array.from()从一个类似数组或可迭代对象中创建一个新的数组实例

> Array.from(arrayLike[, mapFn[, thisArg]])

- arrayLike 想要转换成数组的伪数组对象或可迭代对象。
- mapFn (可选参数) 如果指定了该参数，新数组中的每个元素会执行该回调函数。
- thisArg (可选参数) 可选参数，执行回调函数 mapFn 时 this 对象。

* String

``` javascript

Array.from('foo');
// ["f", "o", "o"]

```

* Array from a String

``` javascript

Array.from('foo');
// ["f", "o", "o"]

```


* Array from a Set

``` javascript

let s = new Set(['foo', window]);
Array.from(s);
// ["foo", window]

```


* Array from a Map

``` javascript

function f() {
  return Array.from(arguments);
}
f(1, 2, 3);
// [1, 2, 3]

```

* Using arrow functions and Array.from

``` javascript

Array.from([1, 2, 3], x => x + x);      
// [2, 4, 6]

Array.from({length: 5}, (v, i) => i);
// [0, 1, 2, 3, 4]

```


* 数组去重合并

``` javascript

function combine(){
    let arr = [].concat.apply([], arguments);  //没有去重复的新数组
    return Array.from(new Set(arr));
}
var m = [1, 2, 2], n = [2,3,3];
console.log(combine(m,n));                     // [1, 2, 3]

```


### Array.of() 方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。

> Array.of() 和 Array 构造函数之间的区别在于处理整数参数：Array.of(7) 创建一个具有单个元素 7 的数组，而 Array(7) 创建一个包含 7 个 undefined 元素的数组。

``` javascript

Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]

Array(7);          // [ , , , , , , ]
Array(1, 2, 3);    // [1, 2, 3]

```


### concat() 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

* 连接两个数组

``` javascript

var alpha = ['a', 'b', 'c'];
var numeric = [1, 2, 3];

alpha.concat(numeric);
// result in ['a', 'b', 'c', 1, 2, 3]

```


* 连接三个数组

``` javascript

var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];
var nums = num1.concat(num2, num3);
console.log(nums);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]

```


* 将值连接到数组

``` javascript

var alpha = ['a', 'b', 'c'];
var alphaNumeric = alpha.concat(1, [2, 3]);
console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]

```


* 合并嵌套数组

``` javascript

var num1 = [[1]];
var num2 = [2, [3]];

var nums = num1.concat(num2);

console.log(nums);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(nums);
// results in [[1, 4], 2, [3]]

```




### every() 方法测试数组的所有元素是否都通过了指定函数的测试

> every 方法为数组中的每个元素执行一次 callback 函数，直到它找到一个使 callback 返回 false（表示可转换为布尔值 false 的值）的元素。如果发现了一个这样的元素，every 方法将会立即返回 false。否则，callback 为每一个元素返回 true，every 就会返回 true。callback 只会为那些已经被赋值的索引调用。不会为那些被删除或从来没被赋值的索引调用。

* callback 被调用时传入三个参数：元素值，元素的索引，原数组。

``` javascript

function isBigEnough(element, index, array) {
  return (element >= 10);
}
var passed = [12, 5, 8, 130, 44].every(isBigEnough);
// passed is false
passed = [12, 54, 18, 130, 44].every(isBigEnough);
// passed is true

```


### filter() 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。

``` javascript

function isBigEnough(value) {
  return value >= 10;
}
var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]

// ES6 way
const isBigEnough = value => value >= 10;

let [...spread]= [12, 5, 8, 130, 44];
let filtered = spread.filter(isBigEnough);
// filtered is [12, 130, 44]


```



### find() 方法返回数组中满足提供的测试函数的第一个元素的值。否则返回 undefined。

``` javascript

function isBigEnough(element) {
    return element >= 15;
}

var ret1 = [12, 5, 8, 130, 44].find(isBigEnough);
console.log(ret1);
// 130
var objArr = [{id:1, name:'jiankian'}, {id:23, name:'anan'}, {id:188, name:'superme'}, {id:233, name:'jobs'}, {id:288, name:'bill', age:89}, {id:333}] ;
var ret2 = objArr.find((v) => {
    return v.id == 233;
});
console.log(ret2);
// return {id:233, name:'jobs'}

```


###findIndex()方法返回数组中满足提供的测试函数的第一个元素的索引。否则返回-1。

``` javascript

function isBigEnough(element) {
    return element >= 15;
}

var ret1 = [12, 5, 8, 130, 44].findIndex(isBigEnough);
console.log(ret1);
// index of 4th element in the Array is returned,
// so this will result in '3'
var objArr = [{id:1, name:'jiankian'}, {id:23, name:'anan'}, {id:188, name:'superme'}, {id:233, name:'jobs'}, {id:288, name:'bill', age:89}, {id:333}] ;
var ret2 = objArr.findIndex((v) => {
    return v.id == 233;
});
console.log(ret2);
// return 3


```




###forEach() 方法对数组的每个元素执行一次提供的函数。

>没有返回一个新数组! & 没有返回值! 应用场景：为一些相同的元素，绑定事件处理器！

``` javascript

function logArrayElements(element, index, array) {
    console.log("a[" + index + "] = " + element);
}

// 注意索引2被跳过了，因为在数组的这个位置没有项
[2, 5, ,9].forEach(logArrayElements);

// a[0] = 2
// a[1] = 5
// a[3] = 9


```




### includes() 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回false。

>arr.includes(searchElement, fromIndex)

- searchElement 需要查找的元素值。
- fromIndex 可选 从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。


``` javascript

[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true

```


### indexOf()方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。

>arr.indexOf(searchElement) arr.indexOf(searchElement[, fromIndex = 0])


``` javascript

var array = [2, 5, 9];
array.indexOf(2);     // 0
array.indexOf(7);     // -1
array.indexOf(9, 2);  // 2
array.indexOf(2, -1); // -1
array.indexOf(2, -3); // 0

```



### join() 方法将一个数组（或一个类数组对象）的所有元素连接成一个字符串并返回这个字符串

>join() 方法，不会改变数组！

``` javascript

let a = ['Wind', 'Rain', 'Fire'];

console.log(a.join());
// 默认为 ","
// 'Wind,Rain,Fire'

console.log(a.join(""));
// 分隔符 === 空字符串 ""
// "WindRainFire"

console.log(a.join("-"));
// 分隔符 "-"
// 'Wind-Rain-Fire'

```




### keys() 方法返回一个新的Array迭代器，它包含数组中每个索引的键。


``` javascript

let arr = ["a", "b", "c"];

let iterator = arr.keys();
// undefined

console.log(iterator);
// Array Iterator {}

console.log(iterator.next());
// Object {value: 0, done: false}

console.log(iterator.next());
// Object {value: 1, done: false}

console.log(iterator.next());
// Object {value: 2, done: false}

console.log(iterator.next());
// Object {value: undefined, done: true}

```




### lastIndexOf() 方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 fromIndex 处开始。


``` javascript

var array = [2, 5, 9, 2];
var index = array.lastIndexOf(2);
// index is 3
index = array.lastIndexOf(7);
// index is -1
index = array.lastIndexOf(2, 3);
// index is 3
index = array.lastIndexOf(2, 2);
// index is 0
index = array.lastIndexOf(2, -2);
// index is 0
index = array.lastIndexOf(2, -1);
// index is 3

```




###map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果

``` javascript

// ES6
let numbers = [1, 5, 10, 15];
let doubles = numbers.map( x => x ** 2);

// doubles is now [1, 25, 100, 225]
// numbers is still [1, 5, 10, 15]


const numbers = [2, 4, 8, 10];
let halves = numbers.map(x => x / 2);

let numbers = [1, 4, 9];
let roots = numbers.map(Math.sqrt);
// roots is now [1, 2, 3]
// numbers is still [1, 4, 9]

```




###pop()方法从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。

``` javascript

let a = [1, 2, 3];
a.length; // 3

a.pop(); // 3

console.log(a); // [1, 2]
a.length; // 2

```




### push() 方法将一个或多个元素添加到数组的末尾，并返回新数组的长度。

``` javascript

var numbers = [1, 2, 3];
numbers.push(4);

console.log(numbers);
// [1, 2, 3, 4]

numbers.push(5, 6, 7);

console.log(numbers);
// [1, 2, 3, 4, 5, 6, 7]

```



### reduce() 方法对累加器和数组中的每个元素（从左到右）应用一个函数，将其减少为单个值。

>reduce为数组中的每一个元素依次执行callback函数，不包括数组中被删除或从未被赋值的元素，接受四个参数：

- accumulator 累加器累加回调的返回值; 它是上一次调用回调时返回的累积值，或initialValue（如下所示）。
- currentValue 数组中正在处理的元素。
- currentIndex 数组中正在处理的当前元素的索引。 如果提供了initialValue，则索引号为0，否则为索引为1。
- array 调用reduce的数组

* reduce如何运行

``` javascript

[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue;
});


```

* 数组里所有值的和

``` javascript

var sum = [0, 1, 2, 3].reduce(function (a, b) {
  return a + b;
}, 0);
// sum is 6

var total = [ 0, 1, 2, 3 ].reduce(
  ( acc, cur ) => acc + cur,
  0
);


```

* 将二维数组转化为一维

``` javascript

var flattened = [[0, 1], [2, 3], [4, 5]].reduce(
  function(a, b) {
    return a.concat(b);
  },
  []
);
// flattened is [0, 1, 2, 3, 4, 5]

//es6
var flattened = [[0, 1], [2, 3], [4, 5]].reduce(
 ( acc, cur ) => acc.concat(cur),
 []
);


```

* 计算数组中每个元素出现的次数

``` javascript

var names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice'];

var countedNames = names.reduce(function (allNames, name) {
  if (name in allNames) {
    allNames[name]++;
  }
  else {
    allNames[name] = 1;
  }
  return allNames;
}, {});
// countedNames is:
// { 'Alice': 2, 'Bob': 1, 'Tiff': 1, 'Bruce': 1 }


```


* 数组去重
``` javascript

let arr = [1,2,1,2,3,5,4,5,3,4,4,4,4];
let result = arr.sort().reduce((init, current)=>{
    if(init.length===0 || init[init.length-1]!==current){
        init.push(current);
    }
    return init;
}, []);
console.log(result); //[1,2,3,4,5]


```


###reduceRight() 方法接受一个函数作为累加器（accumulator）和数组的每个值（从右到左）将其减少为单个值。


``` javascript

let flattened = [
    [0, 1],
    [2, 3],
    [4, 5]
].reduceRight((a, b) => {
    return a.concat(b);
}, []);

// flattened is [4, 5, 2, 3, 0, 1]

```



### reverse() 方法将数组中元素的位置颠倒。

``` javascript

var myArray = ['one', 'two', 'three'];
myArray.reverse();

console.log(myArray) // ['three', 'two', 'one']

```



### shift() 方法从数组中删除第一个元素，并返回该元素的值。此方法更改数组的长度。

``` javascript

let a = [1, 2, 3];
let b = a.shift();
console.log(a);
// [2, 3]
console.log(b);
// 1

```



### slice() 方法返回一个从开始到结束（不包括结束）选择的数组的一部分浅拷贝到一个新数组对象。且原始数组不会被修改。

``` javascript

arr.slice();
// [0, end]

arr.slice(begin);
// [begin, end]

arr.slice(begin, end);
// [begin, end)

var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
var citrus = fruits.slice(1, 3);

// fruits contains ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
// citrus contains ['Orange','Lemon']

```


### some() 方法测试数组中的某些元素是否通过由提供的函数实现的测试。

``` javascript
function isBigEnough(element, index, array) {
  return (element >= 10);
}
var passed = [2, 5, 8, 1, 4].some(isBigEnough);
// passed is false
passed = [12, 5, 8, 1, 4].some(isBigEnough);
// passed is true

```

### sort() 方法用就地（ in-place ）的算法对数组的元素进行排序，并返回数组


``` javascript

var items = [
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic' },
  { name: 'Zeros', value: 37 }
];

// sort by value
items.sort(function (a, b) {
  return (a.value - b.value)
});

// sort by name
items.sort(function(a, b) {
  var nameA = a.name.toUpperCase(); // ignore upper and lowercase
  var nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }

// names must be equal

  return 0;
});

```


###  splice() 方法通过删除现有元素和/或添加新元素来更改一个数组的内容。

- array.splice(start)

- array.splice(start, deleteCount)

- array.splice(start, deleteCount, item1, item2, ...)

```  javascript

var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

myFish.splice(2, 0, 'drum'); // 在索引为2的位置插入'drum'
// myFish 变为 ["angel", "clown", "drum", "mandarin", "sturgeon"]

myFish.splice(2, 1); // 从索引为2的位置删除一项（也就是'drum'这一项）
// myFish 变为 ["angel", "clown", "mandarin", "sturgeon"]

```


###  unshift() 方法将一个或多个元素添加到数组的开头，并返回新数组的长度。

``` javascript

let a = [1, 2, 3];
a.unshift(4, 5);

console.log(a);
// [4, 5, 1, 2, 3]

```


###  Value

```


```
