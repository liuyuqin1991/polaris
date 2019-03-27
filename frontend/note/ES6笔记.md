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
