**console.assert()方法**

```
//示例代码
//声明一个名为People的构造函数
function People(name,age,performance){
       this.name = name;
       this.age = age;
       this.performance = performance;
}
//引用上面的构造函数People,声明变量people
var people =new People("john",20,[80,90,99]);
//调用console.assert()方法
console.assert( people.performance.length == 3, "长度不准确");

//说明
//上面在调用console.assert()的意思是：
//如果people.performance.length == 3返回的结果是true，
//就不输出"长度不准确"；
//如果people.performance.length == 3返回的结果是false，
//就输出"长度不准确"；
```

**console.count()方法**

```
//实力代码
    //定义一个简单的加法函数addition
    function addition(a, b) {
        //调用console.count()方法
        console.count('addition function called times:');
        return a + b;
    }

    //声明一个变量
    var sum = 0;
    for(var i = 0; i < 20; i++) {
        if(i % 2 == 0) {
             sum = addition(sum, i);
        }
    }
    console.log(sum);

    //说明
    //console.count()方法用于统计代码块被执行的次数，
    //console.count()参数是可选的标题，方便阅读
```

**4.console.debug()方法，console.info()方法  console.warn()方法 , console.error()方法  console.log()方法**

```
//console以上方法支持类似C语言的占位符，
  //如 %s=>字符串, %d=>整数, %f=>浮点数, %o=>object

  //示例代码
  console.log('I %s more than %d %o.', 'want', 3, {animal: 'dogs', color: 'black'});
  console.debug('I like', {'a': 'Dog', 'b': 'Cat'}, 'A');
  console.debug('I %s more than %d %o.', 'want', 3, {animal: 'dogs', color: 'black'});

  console.info('I like', {'a': 'Dog', 'b': 'Cat'}, 'A');
  console.info('I %s more than %d %o.', 'want', 3, {animal: 'dogs', color: 'black'});

  console.warn('I like', {'a': 'Dog', 'b': 'Cat'}, 'A');
  console.warn('I %s more than %d %o.', 'want', 3, {animal: 'dogs', color: 'black'});

  console.error('I like', {'a': 'Dog', 'b': 'Cat'}, 'A');
  console.error('I %s more than %d %o.', 'want', 3, {animal: 'dogs', color: 'black'});

  //说明
  //上面几个方法比较简单，就不细说了
```

**console.dirxml()方法**

```
//示例代码
    console.log(document.getElementById('myDiv'));
    console.dirxml(document.getElementById('myDiv'));

    //说明
    输出网页的某个节点（node）包含的html/xml代码，
    与console.log()功能相似
```

**console.group()方法**

```
console.groupCollapsed()方法
      console.groupEnd()方法

      //示例代码
      console.group('第一组');
      console.log('1.1');
      console.log('1.2');
      console.log('1.3');
      console.groupEnd();

      console.groupCollapsed('第二组');
      console.log('2.1');
      console.log('2.2');
      console.log('2.3');
      console.groupEnd();

      //说明
      //console.group()默认展开
      //console.groupCollapsed()默认关闭
      //console.groupEnd()结束分组
```

**console.profile()方法 console.profileEnd()方法**

```
//示例代码
      function AllFunction(){
          for(var i=0;i<100;i++){
              functionA(10000);
          }
          functionB(10000);
      }

      function functionA(count){ for(var i=0;i<count;i++){} }
      function functionB(count){ for(var i=0;i<count;i++){} }

      console.profile('profile');
      AllFunction();
      console.profileEnd();

      //说明
      //分析profile和profileEnd之间代码的执行情况，即js代码的性能分析。
      //注意，如果代码运行时间过短，则在性能分析时可能会被忽略（如上面的函数functionB）:
      //在浏览器的开发工具中的profile面板里可以看到结果
```

**console.table()方法**

```
//示例代码
//数组
var dataArr = [
    [111, 222, 332],
    [442, 555, 666]
];
console.table(dataArr);

//JSON对象
var dataJson = [
    {'a':'1.11', 'b':'2.2'},
    {'a':'11.1', 'b':'22.2'},
    {'a':'111.1', 'b':'222.2'}
];
console.table(dataJson);

//说明
//table方法用于把data对象用表格的方式显示出来，
//在显示数组或格式一样的JSON数据时很有用：
```


**console.time()方法，console.timeEnd()方法**

```
//示例代码
    console.time('time');
    for(var i = 0; i < 1000; i++) {
        for(var j = 0; j < 1000; j++) { }
    }
    console.timeEnd('time');

    //说明
    //计算time和timeEnd之间代码块的执行时间并显示
    //从而来判断JavaScript语法的性能
```

**console.trace()方法**

```
//示例代码
function add(a,b){
    console.trace();
    return a+b;
}
var x = add3(1,1);
function add3(a,b){return add2(a,b);}
function add2(a,b){return add1(a,b);}
function add1(a,b){return add(a,b);}

//说明
//console.trace()用来追踪函数的调用轨迹
//可以查看函数是怎么样调用的！
```
