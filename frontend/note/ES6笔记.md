# ECMAScript 6 笔记

## ECMAScript和JavaScript的关系

ECMAScript是JavaScript的规范，JavaScript是ECMAScript的一种实现（另外的ECMAScript方言还有Jscript和ActionScript）。日常场
合，这两个词是可以互换的。

## ECMAScript 版本更迭

* ECMAScript1.0：1997年
* ECMAScript2.0：1998年6月
* ECMAScript3.0：1999年12月（ES3）
* ECMAScript5.0（也称ECMAScript3.1）：2009年12月（ES5）
* ECMAScript6：2015年6月（ES6）

## let与const

1. **let**
    
* 声明变量
* 代码块内有效 
* 不存在变量提升
* 在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”。
* 不允许重复声明

2. **const**

* 声明只读常量
* 代码块内有效 
* 不存在变量提升
* 在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”。
* 不允许重复声明    

## 赋值解构

ES6允许按照一定模式，从数组，对象和字符串中提取值，对变量进行赋值，这被称为解构（Destructuring）,解构赋值不仅适用于var命令，也适用于let和const命令。

1. 数组的赋值解构

* `let [a, b, c] = [1, 2, 3];`  //a=1,b=2,c=3
* `let [foo, [[bar], baz]] = [1, [[2], 3]];` //foo=1,bar=2,baz=3
* `let [ , , third] = ["foo", "bar", "baz"]; `//third=baz
* `let [x, , y] = [1, 2, 3]; //x=1,y=3`
* `let [head, ...tail] = [1, 2, 3, 4];` //head=1,tail=[2,3,4]
* `let [x, y, ...z] = ['a']; `//x='a',y=undefined,z=[]
* `let [x, y] = [1, 2, 3];` //x=1,y=2
* `let [a, [b], d] = [1, [2, 3], 4];`//a=1,b=2,d=4
* `let [x, y = 'b'] = ['a'];` //x='a',y='b'
* `let [x, y = 'b'] = ['a', undefined];` //x='a',y='b'
* `let [x = 1, y = x] = [];` //x=1,y=1

2. 对象的赋值解构

* `let { foo: foo, bar: bar } = { foo: "aaa", bar: "bbb" };` //foo='aaa',bar='bbb'
* `let { foo, bar } = { foo: "aaa", bar: "bbb" };` //foo='aaa',bar='bbb'
* `let { bar, foo } = { foo: "aaa", bar: "bbb" };` //foo='aaa',bar='bbb'
* `let { foo: baz } = { foo: 'aaa', bar: 'bbb' };` //baz='aaa'

3. 字符串的赋值解构

* `let [a, b, c] = 'hello';` //a='h',b='e',c='l'
* `let {length : len} = 'hello';` //len=5 (类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值)

4. 赋值解构的用途

* 交换变量的值：

`[x, y] = [y, x];`,交换变量x和y的值，这样的写法不仅简洁，而且易读，语义非常清晰
* 从函数返回多个值:
```
// 返回一个数组
function example() {
    return [1, 2, 3];
}
var [a, b, c] = example();

// 返回一个对象
function example() {
    return {
        foo: 1,
        bar: 2
    };
}
var { foo, bar } = example();
```
* 提取JSON数据
```
var jsonData = {
    id: 42,
    status: "OK",
    data: [867, 5309]
};
let { id, status, data: number } = jsonData;
```

* 遍历Map结构
```
var map = new Map();
map.set('first', 'hello');
map.set('second', 'world');

for (let [key, value] of map) {
    console.log(key + " is " + value);
}
// first is hello
// second is world  
```

* 输入模块的指定方法

```
const { SourceMapConsumer, SourceNode } = require("source-map");
```

## 字符串扩展
> ES6加强了对Unicode的支持，支持超过\u0000——\uFFFF之间的字符，并且扩展了字符串对象

* `codePointAt()`：处理4个字节储存的字符，返回一个字符的Unicode编号。
* `String.fromCodePoint()`：从码点返回对应字符。
* 字符串可以被for...of循环遍历。
* `at()`：可以识别Unicode编号大于0xFFFF的字符，返回正确的字符。
* `includes()`：返回布尔值，表示是否找到了参数字符串。
* `startsWith()`：返回布尔值，表示参数字符串是否在源字符串的头部。
* `endsWith()`：返回布尔值，表示参数字符串是否在源字符串的尾部。
* `repeat()`：返回一个新字符串，表示将原字符串重复n次。
* `padStart()`：字符串首部补全。
    
    常见用途是为数值补全指定位数。例如：
    ```
    '1'.padStart(10, '0') // "0000000001"
    '12'.padStart(10, '0') // "0000000012"
    '123456'.padStart(10, '0') // "0000123456"
    ```
* `padEnd()`：字符串尾部补全。
* 可以使用模板字符串来编写dom，js混写。例如：
    ```
    //传统写法
    $('#result').append(
    'There are <b>' + basket.count + '</b> ' +
    'items in your basket, ' +
    '<em>' + basket.onSale +
    '</em> are on sale!'
    );
    //模板写法
    $('#result').append(`
    There are <b>${basket.count}</b> items
    in your basket, <em>${basket.onSale}</em>
    are on sale!
    `);
    ```

## 数值扩展

* `Number.isFinite()`：用来检查一个数值是否为有限的（finite）。
* `Number.isNaN()`：判断是否为NaN。
* `Number.parseInt()`：与全局方法parseInt一致，属于模块化优化。
* `Number.parseFloat()`：与全局方法parseFloat一致，属于模块化优化。
* `Number.isInteger()`：判断一个值是否为整数。
* `Math.trunc()`：去除一个数字的小数部分。
* `Math.sign()`：判断一个数是正数，负数还是0，它会返回五种值：1. 参数为正数，返回+1；2. 参数为负数，返回-1；3. 参数为0，返回0；4. 参数为-0，返回-0;5. 其他值，返回NaN

## 数组的扩展

* `Array.from()`：将类数组对象或可遍历对象这两类对象转为真正的数组。
* `Array.of()`：将一组值，转换为数组。
```
Array.of() // []
Array.of(undefined) // [undefined]
Array.of(1) // [1]
Array.of(1, 2) // [1, 2]
```
* `find()与findIndex()`：找出第一个符合条件的数组元素或数组索引，它的参数是一个回调函数，如果没有符合条件的成员，则返回undefined。
```
[1, 4, -5, 10].find((n) => n < 0)
// -5
[1, 5, 10, 15].find(function(value, index, arr) {
return value > 9;
}) // 10
[1, 5, 10, 15].findIndex(function(value, index, arr) {
return value > 9;
}) // 2
```
* `fill()`：使用给定值，填充一个数组。fill方法用于空数组的初始化非常方便。数组中已有的元素，会被全部抹去。
```
['a', 'b', 'c'].fill(7)
// [7, 7, 7]
new Array(3).fill(7)
// [7, 7, 7]
['a', 'b', 'c'].fill(7, 1, 2)
// ['a', 7, 'c']
```
* `entries()，keys()和values()`：用于遍历数组。它们都返回一个遍历器对象，可以
用for...of循环进行遍历，唯一的区别是keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。
```
for (let index of ['a', 'b'].keys()) {
    console.log(index);
}
// 0
// 1
for (let elem of ['a', 'b'].values()) {
    console.log(elem);
}
// 'a'
// 'b'
for (let [index, elem] of ['a', 'b'].entries()) {
    console.log(index, elem);
}
// 0 "a"
// 1 "b"
```
* `includes()`：表示某个数组是否包含给定的值，与字符串的includes方法类似。
```
[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, NaN].includes(NaN); // true
```

## 函数的扩展

* ES6引入rest参数（形式为“...变量名”），用于获取函数的多余参数。rest参数搭配的变量是一个数组，该变量将多余的参数放入数组中。rest参数之后不能再有其他参数（即只能是最后一个参数），否则会报错。

```
function add(...values) {
    let sum = 0;
    for (var val of values) {
        sum += val;
    }
    return sum;
}

add(2, 5, 3) // 10

```

* `...`：扩展运算符（spread）是三个点（...）。它好比rest参数的逆运算，将一个数组转为用逗号分隔的参数序列，该运算符主要用于函数调用。

```
console.log(...[1, 2, 3])
// 1 2 3
console.log(1, ...[2, 3, 4], 5)
// 1 2 3 4 5
[...document.querySelectorAll('div')]
// [<div>, <div>, <div>]

function push(array, ...items) {
    array.push(...items);
}
function add(x, y) {
    return x + y;
}
var numbers = [4, 38];
add(...numbers) // 42

// ES5
new (Date.bind.apply(Date, [null, 2015, 1, 1]))
// ES6
new Date(...[2015, 1, 1]);

//合并数组
// ES5
[1, 2].concat(more)
// ES6
[1, 2, ...more]
var arr1 = ['a', 'b'];
var arr2 = ['c'];
var arr3 = ['d', 'e'];
// ES5的合并数组
arr1.concat(arr2, arr3);
// [ 'a', 'b', 'c', 'd', 'e' ]
// ES6的合并数组
[...arr1, ...arr2, ...arr3]
// [ 'a', 'b', 'c', 'd', 'e' ]
```

## 对象的扩展

* `Object.is()`：比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致。
* `Object.assign()`：用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。Object.assign方法实行的是浅拷贝，而不是深拷贝，方法用途：

    * 为对象添加属性
    ```
    class Point {
        constructor(x, y) {
            Object.assign(this, {x, y});
        }
    }
    ```
    * 为对象添加方法
    ```
    Object.assign(SomeClass.prototype, {
        someMethod(arg1, arg2) {
            ···
        }
        anotherMethod() {
            ···
        }
    });
    ```
    * 克隆对象
    ```
    function clone(origin) {
        return Object.assign({}, origin);
    }
    ```
    * 合并多个对象
    ```
    const merge = (target, ...sources) => Object.assign(target, ...sources);
    ```
    * 为属性指定默认值
    ```
    const DEFAULTS = {
        logLevel: 0,
        outputFormat: 'html'
    };
    function processContent(options) {
        let options = Object.assign({}, DEFAULTS, options);
    }
    ```

* `Object.keys()`：返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键名
* `Object.values()`：返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值。
* `Object.entries()`：返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组。

## Symbol

> 一种新的原始数据类型，表示独一无二的值，它是JavaScript语言的第七种数据类型

* Sybmol生成
```
let s = Symbol();

let s1 = Symbol('foo');

s1.toString() // "Symbol(foo)"
```

* 消除魔术字符串
```
const shapeType = {
    triangle: Symbol()
};

function getArea(shape, options) {
    let area = 0;
    switch (shape) {
        case shapeType.triangle:
            area = .5 * options.width * options.height;
            break;
    }
    return area;
}

getArea(shapeType.triangle, { width: 100, height: 100 });
```

## Proxy

> 在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过
滤和改写

ES6原生提供Proxy构造函数，用来生成Proxy实例。
```
var proxy = new Proxy(target, handler);
```
Proxy对象的所有用法，都是上面这种形式，不同的只是handler参数的写法。其中，new Proxy()表示生成一个Proxy实例，target参数表示所要拦截的
目标对象，handler参数也是一个对象，用来定制拦截行为。

## Reflect

> ES6为了操作对象而提供的新的API

* 将Object对象的一些明显属于语言内部的方法（比如Object.defineProperty），放到Reflect对象上。现阶段，某些方法同时
在Object和Reflect对象上部署，未来的新方法将只部署在Reflect对象上。
* 修改某些Object方法的返回结果，让其变得更合理。比如，Object.defineProperty(obj, name, desc)在无法定义属性时，会抛出一个错误，
而Reflect.defineProperty(obj, name, desc)则会返回false。

```
// 老写法
try {
    Object.defineProperty(target, property, attributes);
    // success
} catch (e) {
    // failure
}

// 新写法
if (Reflect.defineProperty(target, property, attributes)) {
    // success
} else {
    // failure
}

// 老写法
'assign' in Object // true

// 新写法
Reflect.has(Object, 'assign') // true
```

* Reflect对象的方法清单如下，共13个。

    * Reflect.apply(target,thisArg,args)：
    * Reflect.construct(target,args)
    * Reflect.get(target,name,receiver)：查找并返回target对象的name属性，如果没有该属性，则返回undefined。如果name属性部署了读取函数，则读取函数的this绑定receiver。
    ```
    var obj = {
        get foo() { return this.bar(); },
        bar: function() { ... }
    };

    // 下面语句会让 this.bar()
    // 变成调用 wrapper.bar()
    Reflect.get(obj, "foo", wrapper);
    ```
    * Reflect.set(target,name,value,receiver)：设置target对象的name属性等于value。如果name属性设置了赋值函数，则赋值函数的this绑定receiver。
    * Reflect.defineProperty(target,name,desc)
    * Reflect.deleteProperty(target,name)：等同于delete obj[name]。
    * Reflect.has(target,name)：等同于name in obj。
    * Reflect.ownKeys(target)
    * Reflect.isExtensible(target)
    * Reflect.preventExtensions(target)
    * Reflect.getOwnPropertyDescriptor(target, name)
    * Reflect.getPrototypeOf(target)
    * Reflect.setPrototypeOf(target, prototype)

## Set
    
> ES6提供了新的数据结构Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

* Set操作方法

    * `add(value)`：添加某个值，返回Set结构本身。
    * `delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
    * `has(value)`：返回一个布尔值，表示该值是否为Set的成员。
    * `clear()`：清除所有成员，没有返回值。

* Set遍历方法

    * `keys()`：返回键名的遍历器。
    * `values()`：返回键值的遍历器。
    * `entries()`：返回键值对的遍历器。
    * `forEach()`：使用回调函数遍历每个成员。

* Set使用实例

    * 去除数组重复元素
    ```
    // 去除数组的重复成员
    [...new Set(array)]
    ```

