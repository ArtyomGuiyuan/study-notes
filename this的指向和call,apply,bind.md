# this的指向和call,apply,bind

## this的指向 

### 谁调用它,this就指向谁

### 1.全局环境中的this
+ 浏览器环境：无论是否在严格模式下，在全局执行环境中（在任何函数体外部）this 都指向全局对象 window;

+ node 环境：无论是否在严格模式下，在全局执行环境中（在任何函数体外部），this 都是空对象 { };

### 2.是否是new绑定
> 如果是 new 绑定，并且构造函数中没有返回 function 或者是 object，那么 this 指向这个新对象。

+ 1.构造函数的返回值不是function或者object.new foo( ) 返回的是this对象

```js
function foo(age){
	this.age = age;
}
	
let alpha = new foo ('21');
	
console.log(alpha.age); //21
	
```

+ 2.构造函数的返回值是function或者object , new bar( )返回的是function bar中返回的对象
```js
function bar(age){
	this.age = age;
	let obj = {a : '2'};
	return obj;
}

let beta = new bar ('hello');
console.log(beta); //{a : ' 2 '}
console.log(beta.age); //undefined
```
### 3.箭头函数的情况
> 箭头函数没有自己的this , 继承外层上下文绑定的this
```javascript
let obj = {
	age : 20,
	info:function(){
		return() => {
			console.log(this.age);
		}
	}
}

let person = {age : 28};
let info = obj.info();

info(); //20

let info2 = obj.info.call(person);
info2(); //28
```

### 4.默认绑定，在不能应用其它绑定规则时使用的默认规则，通常是独立函数调用。
+ 非严格模式： node环境，执行全局对象 global，浏览器环境，执行全局对象 window。
+ 严格模式：执行 undefined
```js
function info( ){
	console.log(this.age);
}
var age = 28;
// 严格模式: 报错
//非严格模式: node下输出undefined (因为全局的age不会挂在 global上)
//非严格模式: 浏览器下输出28 (因为全局的age会挂在 global上)
//严格模式抛出 因为this此时是 undeifined
info( );
```

### 5.隐式绑定，函数的调用是在某个对象上触发的，即调用位置上存在上下文对象。典型的隐式调用为: xxx.fn( )
```js
function info( ){
	console.log(this.age);
}
var person = {
	age:20,
	info
}
var age =28;
person.info();//20 执行的是隐式绑定
```


### 6.函数是否通过call ,apply 调用,或者使用了bind绑定.如果是,那么this绑定的就是指定的对象(归结为显式绑定)
```js
function info( ){
	console.log(this.age);
}

var person = {
	age:20,
	info
}

var age = 28;
var info = this .info;

info.call(person); //20
info.apply(person); //20
info.bind(person)(); //20
```


#### 注意:特殊情况 如果 call,apply 或者 bind 传入的第一个参数值是 undefined 或者 null，严格模式下 this 的值为传入的值 null /undefined。非严格模式下，实际应用的默认绑定规则，this 指向全局对象(node环境为global，浏览器环境为window)


## call apply bind 的使用和区别 
>call、apply、bind的作用是改变函数运行时this的指向

### 1.call 方法第一个参数是要绑定给this的值，后面传入的是一个参数列表。当第一个参数为null、undefined的时候，默认指向window。 

```js
var arr = [1, 2, 3, 89, 46]
var max = Math.max.call(null, arr[0], arr[1], arr[2], arr[3], arr[4])//89
```

### 2.apply接受两个参数，第一个参数是要绑定给this的值，第二个参数是一个参数数组。当第一个参数为null、undefined的时候，默认指向window。

```js
var arr = [1,2,3,89,46]
var max = Math.max.apply(null,arr)//89
```
##### apply 和 call 的用法几乎相同, 唯一的差别在于：当函数需要传递多个变量时, apply 可以接受一个数组作为参数输入, call 则是接受一系列的单独变量。

### 3.bind 和call很相似，第一个参数是this的指向，从第二个参数开始是接收的参数列表。区别在于bind方法返回值是函数以及bind接收的参数列表的使用。

+ bind返回值是函数
```js
var obj = {
    name: 'Dot'
}

function printName() {
    console.log(this.name)
}

var dot = printName.bind(obj)
console.log(dot) // function () { … }
dot()  // Dot

```
#### bind 方法不会立即执行，而是返回一个改变了上下文 this 后的函数。而原函数 printName 中的 this 并没有被改变，依旧指向全局对象 window。

+ 参数的使用
```js
function fn(a, b, c) {
    console.log(a, b, c);
}
var fn1 = fn.bind(null, 'Dot');

fn('A', 'B', 'C');            // A B C
fn1('A', 'B', 'C');           // Dot A B
fn1('B', 'C');                // Dot B C
fn.call(null, 'Dot');      // Dot undefined undefined
```
##### call 是把第二个及以后的参数作为 fn 方法的实参传进去，而 fn1 方法的实参实则是在 bind 中参数的基础上再往后排。


## 总结
### call、apply和bind函数存在的区别:
> bind返回对应函数, 便于稍后调用； apply, call则是立即调用。除此外, 在 ES6 的箭头函数下, call 和 apply 将失效, 对于箭头函数来说:

+ 箭头函数体内的 this 对象, 就是定义时所在的对象, 而不是使用时所在的对象;所以不需要类似于var _this = this这种丑陋的写法
+ 箭头函数不可以当作构造函数，也就是说不可以使用 new 命令, 否则会抛出一个错误
+ 箭头函数不可以使用 arguments 对象,，该对象在函数体内不存在. 如果要用, 可以用 Rest 参数代替
+ 不可以使用 yield 命令, 因此箭头函数不能用作 Generator 函数，什么是Generator函数可自行查阅资料，推荐阅读阮一峰Generator 函数的含义与用法，Generator 函数的异步应用

