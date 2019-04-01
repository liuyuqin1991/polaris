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
