### Proxy 对象用于定义基本操作的自定义行为（如属性查找，赋值，枚举，函数调用等）。

> let p = new Proxy(target, handler);

- target 用Proxy包装的目标对象（可以是任何类型的对象，包括原生数组，函数，甚至另一个代理）。

- handler 一个对象，其属性是当执行一个操作时定义代理的行为的函数。


* target

> 一个proxy代理对象由两部分组成target/handle。其中target为目标对象，可以为一个空对象即（target={}），也可以是一个含有属性和方法的对象（target={foo:1,bar:2}）,在进行let proxy=new Proxy(target,handle)的操作后，新的proxy对象会对target进行“浅拷贝”,即proxy、target两个对象会相互影响。即：

``` javascript

let target = { _prop: 'foo', prop: 'foo' };
let proxy = new Proxy(target, handler);
proxy._prop = 'bar';
target._attr = 'new'
console.log(target._prop) // 'bar'
console.log(proxy._attr) //'new'

```


* handle

``` javascript

let handler = {
    get (target, key){
        return target[key]
    },
    set (target, key, value) {
        if (key === 'age') {
            target[key] = value > 0 && value < 100 ? value : 0
        }
        return true;//必须有返回值
    }
};
let target = {};
let proxy = new Proxy(target, handler);
proxy.age = 22 //22


```
