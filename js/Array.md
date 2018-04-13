
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
