### Map

> 对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值


* clear()方法会移除Map对象中的所有元素。

>apply() 方法调用一个函数, 其具有一个指定的this值，以及作为一个数组（或类似数组的对象）提供的参数。

* String

``` javascript

var myMap = new Map();
myMap.set("bar", "baz");
myMap.set(1, "foo");

myMap.size;       // 2
myMap.has("bar"); // true

myMap.clear();

myMap.size;       // 0
myMap.has("bar")  // false

```

* delete() 方法用于移除 Map 对象中指定的元素。


``` javascript

var myMap = new Map();
myMap.set("bar", "foo");

myMap.delete("bar"); // 返回 true。成功地移除元素
myMap.has("bar");    // 返回 false。"bar" 元素将不再存在于 Map 实例中

```

* entries 返回一个新的包含 [key, value] 对的 Iterator 对象


``` javascript

var myMap = new Map();
myMap.set("0", "foo");
myMap.set(1, "bar");
myMap.set({}, "baz");

var mapIter = myMap.entries();

console.log(mapIter.next().value); // ["0", "foo"]
console.log(mapIter.next().value); // [1, "bar"]
console.log(mapIter.next().value); // [Object, "baz"]

```

* forEach() ?方法将会以插入顺序对 Map 对象中的每一个键值对执行一次参数中提供的回调函数。

* 打印一个 Map 对象中的元素

``` javascript

function logMapElements(value, key, map) {
    console.log("m[" + key + "] = " + value);
}
Map([["foo", 3], ["bar", {}], ["baz", undefined]]).forEach(logMapElements);
// logs:
// "m[foo] = 3"
// "m[bar] = [object Object]"
// "m[baz] = undefined"

```

* get() 方法用来获取一个 Map ?对象中指定的元素。

``` javascript

var myMap = new Map();
myMap.set("bar", "foo");

myMap.get("bar");  // 返回 "foo".
myMap.get("baz");  // 返回 undefined.

```

* 方法has() 返回一个bool值，用来表明map 中是否存在指定元素.


``` javascript

var myMap = new Map();
myMap.set("bar", "foo");

myMap.has("bar");  // returns true
myMap.has("baz");  // returns false

```


* keys() 返回一个新的 Iterator 对象。它包含按照顺序插入Map对象中每个元素的key值。

>

* String

``` javascript

var myMap = new Map();
myMap.set("0", "foo");
myMap.set(1, "bar");
myMap.set({}, "baz");

var mapIter = myMap.keys();

console.log(mapIter.next().value); // "0"
console.log(mapIter.next().value); // 1
console.log(mapIter.next().value); // Object

```


* set() 方法为Map对象添加一个指定键（key）和值（value）的新元素。


``` javascript

var myMap = new Map();

// 添加一个新元素到Map对象
myMap.set("bar", "foo");
myMap.set(1, "foobar");

// 在Map对象中更新一个新元素
myMap.set("bar", "baz");

```


* values() 方法返回一个新的Iterator对象。它包含按顺序插入Map对象中每个元素的value值。

``` javascript

var myMap = new Map();
myMap.set("0", "foo");
myMap.set(1, "bar");
myMap.set({}, "baz");

var mapIter = myMap.values();

console.log(mapIter.next().value); // "foo"
console.log(mapIter.next().value); // "bar"
console.log(mapIter.next().value); // "baz"

```
