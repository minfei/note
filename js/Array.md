
### setTimeout设置为0的意义

> setTimeout设置为0,延迟执行

``` javascript

<button id="makeinput">Add Input</button>
<button id="asynchronous">asynchronous add</button>
<div id="container">
</div>

var button = document.getElementById('makeinput');
var button2 = document.getElementById('asynchronous');
var container = document.getElementById('container');

button.addEventListener('focus', function() {
  console.log('button focused!');
})

button.onmousedown = function() {
  var input = document.createElement('input');
  container.appendChild(input);
  input.addEventListener('focus', function() {
    console.log('input focused!');
  })
  input.focus();
  input.select();
}

button2.addEventListener('focus', function() {
  console.log('button2 focused!');
})

button2.onmousedown = function() {
  var input = document.createElement('input');
  container.appendChild(input);
  input.addEventListener('focus', function() {
    console.log('input2 focused!');
  })
  setTimeout(function() {
    input.focus();
    input.select();
  }, 0)
}

```
