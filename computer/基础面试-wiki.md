
# README.md
# wiki

JS 基础面试题升级版


# 00-前言\01-开始.md
# 前言

在正式教程开始之前，我想先就以下几点简单唠叨几句，算是教程的开篇前言吧。但是绝对不是废话，不信你就听听看。

## 关于面试

- 面试工程师（年薪20-30万） —— 以基础知识为主
- 面试技术专家（年薪30-50万） —— 以工作经验为主
- 面试架构师（年薪50万以上） —— 以解决方案为主

**本教程主要针对第一种，把前端面试涉及到的基础知识讲明白，而且本教程只有 JS 相关的基础知识**。工作经验这个是没法传授的，只能自己在实际工作中慢慢总结。解决方案就更是不可复制的。有没有发现 —— 越往上越无法言传，越不能结构化 —— 很简单，越复杂越多变的东西，越无法结构化。

另外，在面试过程中，有很多的技巧和注意事项，会让你加分不少，教程的最后会教给大家。

## 关于基础

《喜剧之王》中一本《演员的自我修养》多次出现在镜头中，如果有人问我“程序员的自我修养”最重要的是什么 ——— 我肯定回答是**基础知识**。这也是为何 BAT 等给钱最多的公司面试时如此重视基础知识的原因。

如果你有疑问，你现在就可以先让自己变傻 —— 先不要问为什么，把本教程所有的基础知识都学会再说。如果你觉得自己很聪明，那你将学不好编程。想做好任何事情，首先要让自己变成一个傻子。

随着你对基础知识的逐渐掌握，你会发现你之前的一些疑问，都会慢慢消解。学习后面的任何知识，也将变得更加有效率，比如 Vue React 等框架。


# 01-从题目到基础知识\01-开始.md
# 从题目到基础知识

- 列出几个面试题，思考如何解答
- 思考如何搞定所有面试题（题目是无穷无尽的，做不完）
- 思考前端知识体系


# 01-从题目到基础知识\02-几个面试题.md
# 几个面试题

## 出题

- JS 中使用 `typeof` 能得到的哪些类型
- 何时使用 `===` 何时使用 `==`
- `window.onload` 和 `DOMContentLoaded` 的区别
- 用 JS 创建 10 个 `<a>` 标签，点击的时候弹出来对应的序号
- 手写节流、防抖
- Promise 解决了什么问题？

## 思考

面对这些题目，有些可能你已经有了答案，有些可能一时半会儿想不来，有些可能一点都不了解。没关系，我们这里先不做解答，先要根据以上题目**思考以下几个问题**：

- 拿到一个面试题，你第一时间看到的是什么
- 又如何看待网上搜出来的永远也看不完的题海
- 如何对待接下来遇到的面试题？

到这里，建议大家不要急于看接下来的教程，而是花几分钟的时间自己去想一下以上提出来的几点，第一章的几节内容，都会根据这几点思考来展开讲述。

## 接下来

下一节，将一起讨论一下以上的几个思考问题


# 01-从题目到基础知识\03-如何搞定所有面试题.md
# 如何搞定所有面试题

------

## 思考的解答

对上一节的思考，做一下解答。

- **拿到一个面试题，你第一时间看到的是什么？**—— 应该是知识点，这道题的考点，面试官出这道题，到底想考你什么。
- **又如何看待网上搜出来的永远也看不完的题海？**—— 以不变应万变，看那些题目考察的知识点是什么？题可以千变万化，但是知识点就这么多
- **如何对待接下来的面试题？**—— 先通过已有的题目，捋出前端考察的所有知识点（即本教程），然后再拿着这些知识点，去对应接下来的面试题。

------

## 题目的知识点

然后，我们把上一节每个题目考察的知识点总结一下，要核心知识点，牵强附会的先不管

### JS中使用`typeof`能得到的哪些类型

**JS 基础，变量的类型。** 同类型的题目还有：如何判断一个变量是数组？值类型和引用类型的区别？如何实现深度拷贝？

### 何时使用`===`何时使用`==`

**变量的运算，强制类型转换。** 同类型的题目还有：快速将字符串转换为数字`+str`，以及快速将数字转换为字符串`num + ''`

### window.onload 和 DOMContentLoaded 的区别

**页面渲染过程。** 同类型的题目还有：为何把`<script>`放在`<body>`底部，把 CSS 引用放在`<head>`中

### 用 JS 创建 10 个`<a>`标签，点击的时候弹出来对应的序号

**闭包和作用域。** 同类型的题目还有：jquery 或者 zepto 等为何代码都包括在一个`(function(window){...})(window)`中

### 手写节流函数

**网页性能和体验优化** 同类型的题目还有：防抖函数，常见的性能优化方案

### Promise 解决了什么问题

**异步** 同类型的问题还有：异步和同步的区别，异步有哪些应用场景，定时器的使用等

------

## 接下来

上面介绍了好多个知识点，那么前端一共有多少个知识点？什么样的知识体系才能覆盖所有的面试题？下一节解答。


# 01-从题目到基础知识\04-前端知识体系.md
# 前端知识体系

## 什么是体系

先看看前任总结的高效学习的方式（无论针对哪个行业，无论是工作还是考学，都适用）

- 找准领域的范围和**体系** （可见体系在其中起到了**决定性作用**）
- 针对每个部分刻意训练
- 在实际应用中及时反馈

PS：以上学习方法请不要质疑！！！不要质疑！！！不要质疑！！！

那么什么是知识体系？—— **结构化的知识范围** 要有两个特点

- 能涵盖所有知识点
- 结构化，有组织，易扩展 （就像我们大学要分学院、分专业、分班）

## 知识体系目录

- ES 基础语法（ECMA 262 标准） —— 变量、逻辑、函数、原型、闭包、异步等语法规范
- JS-WEB-API（W3C 标准）—— 如 HTML CSS JS-WEB-API（如 DOM BOM 操作） HTTP 等等
- 开发环境 —— 代码版本管理，代码架构方式、调试工具、工程化等
- 运行环境 —— 浏览器如何加载、解析和渲染页面
- 其他综合性问题，如性能优化

## 特别提醒 ！！！（一定要重点提出来）

以上知识体系，并不是最全面的前端知识体系，而仅仅是符合我们本课程的知识体系。例如它暂时还没有 vue React nodejs 等领域的知识点。

内容太多，无法在一门课中全部讲完，我会专门抽出时间，单独讲解全面的前端知识体系。


# 01-从题目到基础知识\05-总结.md
# 总结

- 列出几个面试题，思考如何解答
- 思考如何搞定所有面试题（题目是无穷无尽的，做不完）
- 思考前端知识体系


# 02-JS基础知识\01-开始.md
# JS 基础知识

- 变量的类型和计算
- 原型和原型链
- 作用域和闭包
- 异步和单线程
- （模块化）

PS：模块化本应该放在此处，但是需要 webpack 支持，因此讲到 webpack 时再补充模块化的知识


# 02-JS基础知识\02-总结.md
# JS 基础知识 - 总结

- 变量的类型和计算
- 原型和原型链
- 作用域和闭包
- 异步和单线程
- （模块化）

PS：模块化本应该放在此处，但是需要 webpack 支持，因此讲到 webpack 时再补充模块化的知识


# 02-JS基础知识\02-变量的类型和计算\01-题目.md
# 变量的类型和计算 - 题目

- `typeof` 能判断哪些类型
- 何时使用 `==` 何时使用 `===`
- 值类型和引用类型的区别
- 手写深拷贝

值类型和引用类型的区别是场景题

```js
// 值类型和引用类型的区别
const obj1 = { x: 100, y: 200 }
const obj2 = obj1
let x1 = obj1.x
obj2.x = 101
x1 = 102
console.log(obj1) // 这里打印出什么？
```


# 02-JS基础知识\02-变量的类型和计算\02-知识点.md
# 变量类型和计算 - 知识点

------

## 变量类型

### 值类型和引用类型

```js
// 值类型
let a = 100
let b = a
a = 200
console.log(b) // 100
```

```js
// 引用类型
let a = { age: 20 }
let b = a
b.age = 21
console.log(a.age) // 21
```

（画图解释其中的玄机 —— 用一个 excel 表格即可表示）

### 常见值类型

```js
const a // undefined
const s = 'abc'
const n = 100
const b = true
const s = Symbol('s')
```

### 常见引用类型

```js
const obj = { x: 100 }
const arr = ['a', 'b', 'c']
const n = null // 特殊引用类型，指针指向为空地址
function fn() {} // 特殊引用类型，但不用于存储数据，所以没有“拷贝、复制函数”这一说
```

### 类型判断

typeof 作用

- 能判断所有值类型
- 能判断函数
- 能识别引用类型，仅此而已

```js
// 判断所有值类型
let a
console.log(a) // 'undefined'
const str = 'abc'
typeof str  // 'string'
const n = 100
typeof n // 'number'
const b = true
typeof b // 'boolean'
const s = Symbol('s')
typeof s // 'symbol'
```

```js
// 能判断函数
typeof console.log // 'function'
typeof function () {} // 'function'

// 能识别引用类型（不能再继续识别）
typeof null // 'object'
typeof ['a', 'b'] // 'object'
typeof { x: 100 } // 'object'
```

------

## 变量计算

变量计算一本用于值类型，引用类型会通过 API 来修改数据。

- 数字 加减乘除
- 字符串 拼接
- 逻辑运算 && || ! == if-else

这其中，会隐含比较大的坑 —— **强制类型转换**

### 字符串拼接（ + 号）

```javascript
const a = 100 + 10   // 110
const b = 100 + '10' // '10010'
const c = true + '10' // 'true10'
```

### == 和 ===

```javascript
// == 会尝试强制类型转换
100 == '100'   // true
0 == ''  // true
0 == false // true
false == '' // true
null == undefined  // true
```

总之，`==` 会尝试进行强制类型转换，至于转换的规则大家没必要，只需要记住一点

- 所有的地方都用 `===`
- 除了判断是 null 或者 undefined 时用 `if (obj.a == null)` —— 这也是 jQuery 源码中的方式

```js
const obj = { x: 100 }
if (obj.a == null) { }
// 相当于：
if (obj.a === null || obj.a === undefined) { }
```

### 逻辑运算

首先认识一个概念

- **falsely 变量**，即 `!!a === false` 的
- **truely 变量**，即 `!!a === true` 的

falsely 变量有如下，（其余的就是 truely 变量）

- 0
- NaN
- ''
- null
- undefined
- false 本身

所有的逻辑运算中，都会用这个规则去判断 true 或者 false

```javascript
// truely 变量
const a = true
if (a) {
    // ....
}
const b = 100
if (b) {
    // ....
}

// falsely 变量
const c = ''
if (c) {
    // ....
}
const d = null
if (d) {
    // ...
}
let e
if (e) {
    // ...
}
```

```js
// 逻辑运算的示例
console.log(10 && 0)  // 0
console.log('' || 'abc')  // 'abc'
console.log(!window.abc)  // true
```

------

## 深拷贝

依赖于类型判断，所有最后讲

```js
// 深拷贝
function deepClone(obj = {}) {
    if (typeof obj !== 'object' || obj == null ) {
        // 不是对象或者数组形式，或是 null ，直接返回
        return obj
    }

    // 初始化返回结果
    let result
    if (obj instanceof Array) {
        result = []
    } else {
        result = {}
    }

    // 变量
    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            // 保证不是原型属性（原型和原型链部分会讲解）

            // 递归调用
            result[key] = deepClone(obj[key])
        }
    }

    // 返回结果
    return result
}

const obj1 = { x: 100, y: 200 }
const obj2 = deepClone(obj1)
obj1.x = 101
console.log(obj2) // x: 100
```

为何计算机不默认把引用类型赋值作为深拷贝？

- 耗费性能
- 占用空间


# 02-JS基础知识\02-变量的类型和计算\03-解答.md
# 变量类型和计算 - 解答

## JS中使用`typeof`能得到的哪些类型

针对这个题目，可以通过以下程序进行验证

```javascript
typeof undefined // 'undefined'
typeof 'abc' // 'string'
typeof 123 // 'number'
typeof true // 'boolean'
typeof Symbol('s') // 'symbol'
typeof {}  // 'object'
typeof [] // 'object'
typeof null // 'object'
typeof console.log // 'function'
```

## 何时使用`===` 何时使用`==`

- 所有的地方都用 `===`
- 除了判断是 null 或者 undefined 时用 `if (obj.a == null)` —— 这也是 jQuery 源码中的方式

```js
const obj = { x: 100 }
if (obj.a == null) { }
// 相当于：
if (obj.a === null || obj.a === undefined) { }
```

## 值类型和引用类型的区别

```js
// 值类型和引用类型的区别
const obj1 = { x: 100, y: 200 }
const obj2 = obj1
let x1 = obj1.x
obj2.x = 101
x1 = 102
console.log(obj1) // { x: 101, y: 200 }
```

## 手写深拷贝

不再重复写


# 02-JS基础知识\03-原型和原型链\01-题目.md
# 原型和原型链 - 题目

## 前言

- JS 是基于原型 prototype 继承的语言
- ES6 可使用类 class 继承（语法糖，本质还是原型继承）

**【重点提示】ES6 已经普及使用，原先构造函数的实现方式已经成为历史。** 所以本次升级版，以讲解 class 为主，不会再从构造函数讲起。

## 题目

- 如何准确判断一个变量是数组类型
- 实现一个简易的 jQuery ，考虑插件和扩展性 —— **PS: 虽然 jQuery 已应用不多，但借助学习原型非常好**
- class 是语法糖，其本质是什么？


# 02-JS基础知识\03-原型和原型链\02-知识点.md
# 原型和原型链 - 知识点

## class

```js
// 声明一个类
class Student {
    constructor(name, number) {
        // 属性
        this.name = name
        this.number = number
    }
    // 方法
    sayHi() {
        console.log(`姓名 ${this.name}，学号 ${this.number}`)
    }
}

// 用类来声明对象
let xialuo = new Student('夏洛', 100)
xialuo.sayHi()
let madongmei = new Student('马冬梅', 101)
madongmei.sayHi()
```

## 继承

```js
// 父类
class People {
    constructor(name) {
        this.name = name
    }
    eat() {
        console.log(`${this.name} eat something`)
    }
}
// 子类
class Student extends People {
    constructor(name, number) {
        super(name)
        this.number = number
    }
    sayHi() {
        console.log(`姓名 ${this.name}，学号 ${this.number}`)
    }
}
// 子类
class Teacher extends People {
    constructor(name, major) {
        super(name)
        this.major = major
    }
    teach() {
        console.log(`${this.name} teach you ${this.major}`)
    }
}

const xialuo = new Student('夏洛', 100)
xialuo.sayHi()
const wanglaoshi = new Teacher('王老师', '语文')
wanglaoshi.teach()
```

## 类型判断

引用类型使用 instanceof

```js
xialuo instanceof Student // true
xialuo instanceof People // true
xialuo instanceof Object // true

[] instanceof Array // true
[] instanceof Object // true

{} instanceof Object // true
```

## 原型

以第二个例子为继承的例子

```js
// class 实际上是函数，可见是语法糖
typeof People // 'function'
typeof Student // 'function'
```

```js
// 隐式原型和显示原型
console.log( xialuo.__proto__ )
console.log( Student.prototype )
console.log( xialuo.__proto__ === Student.prototype )
```

显示原型和隐式原型的关系（可**画图**说明！！！）

- 每个 class 都有 prototype 显示原型
- 每个实例都有 __proto__ 隐式原型
- 实例的 __proto__ 指向对应 class 的 prototype

基于原型的执行逻辑

- 执行实例方法时，如 `xiaoluo.sayHi()`
- 会先从实例自身属性查找（可通过 `hasOwnProperty` 判断）
- 如果找不到则自动去 __proto__ 查找

## 原型链

以第二个例子为继承的例子。

```js
console.log( Student.prototype.__proto__ )
console.log( People.prototype )
console.log( People.prototype === Student.prototype.__proto__ )
```

继续补充原型**图示**！！！

根据之前的规则，再去演练 `xialuo.eat()`

## 原型和原型链综合演练

根据以上规则和图示，综合演练

- `xialuo.name`
- `xialuo.sayHi()`
- `xialuo.eat()`

继续延伸，`xialuo.hasOwnProperty` 从哪里得来？ —— 继续补充原型**图示**！！！

## 重点提示！！！

- class 是 ES6 语法规范，ECMA-262 标准
- ECMA 只是规定语法，即我们的代码编写方式
- 实现方式 ECMA 不管，以上是 V8 引擎实现方式 —— 但现在绝大多数运行环境都是用 v8 引擎（各个浏览器和 nodejs）


# 02-JS基础知识\03-原型和原型链\03-解答.md
# 原型和原型链 - 解答

## 如何准确判断一个变量是数组类型

instanceof

## 实现一个简易的 jQuery ，考虑插件和扩展性

基本框架

```js
class jQuery {
    constructor(selector) {
        const result = document.querySelectorAll(selector)
        const length = result.length
        for (let i = 0; i < length; i++) {
            this[i] = selectorResult[i]
        }
        this.length = length
    }
    get(index) {
        return this[index]
    },
    each(fn) {
        for (let i = 0; i < this.length; i++) {
            const elem = this[i]
            fn(elem)
        }
        return this
    },
    on(type, fn) {
        return this.each(elem => {
            elem.addEventListener(type, fn, false)
        })
    }
}
```

插件机制

```js
// 使用继承 —— 基于 jQuery 基本功能，再造一个更强大的轮子
class myJQuery extends jQuery {
    constructor(selector) {
        super(selector)
    }
    // 扩展自己的方法
    addClass(className) {
    },
    style(data) {
    }
}

// 使用原型 —— 还用 jQuery ，仅仅扩展一个功能而已
jQuery.prototype.dialog = function (info) {
    console.log(this) // this 即 jQuery 对象
}
```

## class 是语法糖，其本质是什么？

- 原型图示
- 执行规则


# 02-JS基础知识\04-作用域和闭包\01-题目.md
# 作用域和闭包 - 题目

- this 的不同应用场景
- 创建 10 个`<a>`标签，点击的时候弹出来对应的序号
- 实际开发中闭包的应用
- 手写 bind 函数

```js
// 创建 10 个`<a>`标签，点击的时候弹出来对应的序号
let i, a
for (i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function (e) {
        e.preventDefault()
        alert(i)
    })
    document.body.appendChild(a)
}
```


# 02-JS基础知识\04-作用域和闭包\02-知识点.md
# 作用域和闭包 - 知识点

## 作用域

所谓作用域，即一个变量的合法使用范围

```js
let a = 0
function fn1() {
    let a1 = 100

    function fn2() {
        let a2 = 200

        function fn3() {
            let a3 = 300
            return a + a1 + a2 + a3
        }
        fn3()
    }
    fn2()
}
fn1()
```

作用域分类

- 全局作用域：在全局定义的变量，全局都可用，像 document
- 函数作用域：在某个函数中定义的变量，只能用于当前函数，像 a b
- 块级作用域（ES6）：只能活跃于当前的块，示例如下

```js
// ES6 块级作用域
if (true) {
    let x = 100
}
console.log(x)  // 会报错
```

## 自由变量

- 一个变量在该作用域没有被定义，但被使用
- 向上级作用域去寻找该变量，层层往上找 —— 如上面的示例

## 闭包

闭包 —— 作用域应用的一个特殊情况。一般有两种书写形式：

- 函数作为参数被传入
- 函数作为返回值

```js
// 函数作为返回值
function create() {
    let a = 100
    return function () {
        console.log(a)
    }
}
let fn = create()
let a = 200
fn()

// 函数作为参数
function print(fn) {
    let a = 200
    fn()
}
let a = 100
function fn() {
    console.log(a)
}
print(fn)
```

以上代码得出 —— 要在**函数定义的地方（不是执行的地方）**去寻找上级作用域！！！

## 闭包示例

```js
// 隐藏数据，只提供 API
function createCache() {
    let data = {}  // 闭包中的数据，被隐藏，不被外界访问
    return {
        set: function (key, val) {
            data[key] = val
        },
        get: function (key) {
            return data[key]
        }
    }
}
let c = createCache()
c.set('a', 100)
console.log( c.get('a') )
```

## this

- 作为普通函数调用
- 使用 `call` `apply` `bind`
- 作为对象方法调用
- 在 class 的方法中调用
- 箭头函数

```js
// this 场景题 - 1
function fn1() {
    console.log(this)
}
fn1() // 打印什么

fn1.call({ x: 100 }) // 打印什么

const fn2 = fn1.bind({ x: 200 })
fn2() // 打印什么

// this 场景题 - 2
const zhangsan = {
    name: '张三',
    sayHi() {
        console.log(this)
    },
    wait() {
        setTimeout(function() {
            console.log(this)
        })
    },
    waitAgain() {
        setTimeout(() => {
            console.log(this)
        })
    }
}
zhangsan.sayHi() // 打印什么
zhangsan.wait() // 打印什么
zhangsan.waitAgain() // 打印什么

// this 场景题 - 2
class People {
    constructor(name) {
        this.name = name
        this.age = 20
    }
    sayHi() {
        console.log(this)
    }
}
const zhangsan = new People('张三')
zhangsan.sayHi() // 打印什么
```


# 02-JS基础知识\04-作用域和闭包\03-解答.md
# 作用域和闭包 - 解答

## this 的不同应用场景

- 作为普通函数调用
- 使用 `call` `apply` `bind`
- 作为对象方法调用
- 在 class 的方法中调用
- 箭头函数

## 创建 10 个`<a>`标签，点击的时候弹出来对应的序号

```js
// 创建 10 个`<a>`标签，点击的时候弹出来对应的序号
let i, a
for (i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function (e) {
        e.preventDefault()
        alert(i)
    })
    document.body.appendChild(a)
}
```

怎么解决？—— 把 `let` 移动到 `for` 里即可

## 实际开发中闭包的应用

参考之前的示例。再次强调闭包中自由变量的寻找方式！！！

```js
// 隐藏数据，只提供 API
function createCache() {
    let data = {}  // 闭包中的数据，被隐藏，不被外界访问
    return {
        set: function (key, val) {
            data[key] = val
        },
        get: function (key) {
            return data[key]
        }
    }
}
let c = createCache()
c.set('a', 100)
console.log( c.get('a') )
```

## 手写 bind 函数

先回顾 bind 函数的应用

```js
function fn1(a, b) {
    console.log('this', this)
    console.log(a, b)
}
const fn2 = fn1.bind({ x: 100 }, 10, 20) // bind 返回一个函数，并会绑定上 this
fn2()
```

手写 bind

```js
Function.prototype.bind1 = function () {
    // 将参数解析为数组
    const args = Array.prototype.slice.call(arguments)

    // 获取 this（取出数组第一项，数组剩余的就是传递的参数）
    const t = args.shift()

    const self = this // 当前函数

    // 返回一个函数
    return function () {
        // 执行原函数，并返回结果
        return self.apply(t, args)
    }
}
```


# 02-JS基础知识\05-异步\01-题目.md
# 异步 - 题目

- 同步和异步的区别是什么？分别举一个同步和异步的例子
- 一个关于`setTimeout`的笔试题
- 手写用 Promise 加载一张图片
- 前端使用异步的场景有哪些

```javascript
// setTimeout 笔试题
console.log(1)
setTimeout(function () {
    console.log(2)
}, 1000)
console.log(3)
setTimeout(function () {
    console.log(4)
}, 0)
console.log(5)
```


# 02-JS基础知识\05-异步\02-知识点.md
# 异步 - 知识点

## 单线程和异步

单线程

- JS 是单线程语言，没法创建线程（简单来说，只能同时做一件事，没法先等待一件事儿，然后同时做另外一件事）
- JS 可启动进程，来同时做多件事，如 Web Worker
- JS 执行和 DOM 渲染也是同一个线程

异步

- 如果有等待的情况（网络请求、定时任务），不能卡住
- 需要异步

```js
// 异步
console.log(100)
setTimeout(function () {
    console.log(200)
}, 1000)
console.log(300)

// 同步
console.log(100)
alert(200)
console.log(300)
```

同步和异步

- 基于单线程
- 异步不会阻塞代码运行
- 同步会阻塞代码运行

## 应用场景

哪些地方可能会阻塞呢？

- 网络请求，如 ajax 图片加载
- 定时任务，如 setTimeout

```js
// ajax
console.log('start')
$.get('./data1.json', function (data1) {
    console.log(data1)
})
console.log('end')
```

这里主要学习异步语法，ajax 的其他操作后面会详细讲解

```js
// 图片加载
console.log('start')
let img = document.createElement('img')
img.onload = function () {
    console.log('loaded')
}
img.src = '/xxx.png'
console.log('end')
```

图片加载，常用于前端统计打点。

```js
// setTimeout
console.log(100)
setTimeout(function () {
    console.log(200)
}, 1000)
console.log(300)
```

```js
// setInterval
console.log(100)
setInterval(function () {
    console.log(200)
}, 1000)
console.log(300)
```

## callback hell

```js
const url1 = '/data1.json'
const url2 = '/data2.json'
const url3 = '/data3.json'

// 获取第一份数据
$.get(url1, (data1) => {
    console.log(data1)

    // 获取第二份数据
    $.get(url2, (data2) => {
        console.log(data2)

        // 获取第三份数据
        $.get(url3, (data3) => {
            console.log(data3)

            // 还可能获取更多的数据
        })
    })
})
```

## Promise

```js
function getData(url) {
    return new Promise((resolve, reject) => {
        $.get(url, (data) => {
            resolve(data)
        })
    })
}
const url1 = '/data1.json'
const url2 = '/data2.json'
const url3 = '/data3.json'
getData(url1).then(data1 => {
    console.log(data1)
    return getData(url2)
}).then(data2 => {
    console.log(data2)
    return getData(url3)
}).then(data3 => {
    console.log(data3)
})
```


# 02-JS基础知识\05-异步\03-解答.md
# 异步 - 解答

## 同步和异步的区别是什么？分别举一个同步和异步的例子

- 基于单线程
- 异步不会阻塞代码运行
- 同步会阻塞代码运行

## 一个关于`setTimeout`的笔试题

```javascript
// setTimeout 笔试题
console.log(1)
setTimeout(function () {
    console.log(2)
}, 1000)
console.log(3)
setTimeout(function () {
    console.log(4)
}, 0)
console.log(5)
// 结果顺序 1 3 5 4 2
```

## 手写用 Promise 依次加载两张图片

```js
function loadImg(src) {
    const promise = new Promise((resolve, reject) => {
        const img = document.createElement('img')
        img.onload = () => {
            resolve(img)
        }
        img.onerror = () => {
            reject(new Error(`图片加载失败 ${src}`))
        }
        img.src = src
    })
    return promise
}

const src = 'http://www.imooc.com/static/img/index/logo_new.png'

loadImg(src).then(img => {
    console.log(img.width)
    return img
}).then(img => {
    console.log(img.height)
}).catch(ex => {
    console.error(ex)
})
```

## 前端使用异步的场景有哪些

- 网络请求，如 ajax 图片加载
- 定时任务，如 setTimeout


# 03-JS-Web-API\01-开始.md
# JS-Web-API 开始

- DOM 操作
- BOM 操作
- 事件
- ajax
- 存储


# 03-JS-Web-API\02-DOM\01-题目.md
# DOM 题目

- DOM 是哪种基本的数据结构？
- DOM 操作的常用 API 有哪些
- DOM 节点的 attr 和 property 有何区别
- 如何一次性插入多个 DOM 节点，考虑性能


# 03-JS-Web-API\02-DOM\02-知识点.md
# DOM 知识点

## DOM 的本质

讲 DOM 先从 html 讲起，讲 html 先从 XML 讲起。XML 是一种可扩展的标记语言，所谓可扩展就是它可以描述任何结构化的数据，它是一棵树！

```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
  <other>
    <a></a>
    <b></b>
  </other>
</note>
```

HTML 是一个有既定标签标准的 XML 格式，标签的名字、层级关系和属性，都被标准化（否则浏览器无法解析）。同样，它也是一棵树。

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <div>
        <p>this is p</p>
    </div>
</body>
</html>
```

我们开发完的 html 代码会保存到一个文档中（一般以`.html`或者`.htm`结尾），文档放在服务器上，浏览器请求服务器，这个文档被返回。因此，最终浏览器拿到的是一个文档而已，文档的内容就是 html 格式的代码。

但是浏览器要把这个文档中的 html 按照标准渲染成一个页面，此时浏览器就需要将这堆代码处理成自己能理解的东西，也得处理成 JS 能理解的东西，因为还得允许 JS 修改页面内容呢。

基于以上需求，浏览器就需要把 html 转变成 DOM，html 是一棵树，DOM 也是一棵树。对 DOM 的理解，可以暂时先抛开浏览器的内部因此，先从 JS 着手，即可以认为 DOM 就是 JS 能识别的 html 结构，一个普通的 JS 对象或者数组。

【附带一个 chrome Element 的截图】

## DOM 节点操作

### 获取 DOM 节点

```javascript
const div1 = document.getElementById('div1') // 元素
const divList = document.getElementsByTagName('div')  // 集合
console.log(divList.length)
console.log(divList[0])

const containerList = document.getElementsByClassName('.container') // 集合
const pList = document.querySelectorAll('p') // 集合
```

### prototype

DOM 节点就是一个 JS 对象，它符合之前讲述的对象的特征 ———— 可扩展属性

```javascript
const pList = document.querySelectorAll('p')
const p = pList[0]
console.log(p.style.width)  // 获取样式
p.style.width = '100px'  // 修改样式
console.log(p.className)  // 获取 class
p.className = 'p1'  // 修改 class

// 获取 nodeName 和 nodeType
console.log(p.nodeName)
console.log(p.nodeType)
```

### Attribute

property 的获取和修改，是直接改变 JS 对象，而 Attibute 是直接改变 html 的属性。两种有很大的区别

```javascript
const pList = document.querySelectorAll('p')
const p = pList[0]
p.getAttribute('data-name')
p.setAttribute('data-name', 'imooc')
p.getAttribute('style')
p.setAttribute('style', 'font-size:30px;')
```

## DOM 树操作

新增节点

```javascript
const div1 = document.getElementById('div1')
// 添加新节点
const p1 = document.createElement('p')
p1.innerHTML = 'this is p1'
div1.appendChild(p1) // 添加新创建的元素
// 移动已有节点。注意是移动！！！
const p2 = document.getElementById('p2')
div1.appendChild(p2)
```

获取父元素

```javascript
const div1 = document.getElementById('div1')
const parent = div1.parentNode
```

获取子元素

```javascript
const div1 = document.getElementById('div1')
const child = div1.childNodes
```

删除节点

```javascript
const div1 = document.getElementById('div1')
const child = div1.childNodes
div1.removeChild(child[0])
```

还有其他操作的API，例如获取前一个节点、获取后一个节点等，但是面试过程中经常考到的就是上面几个。

## DOM 性能

DOM 操作是昂贵的 —— 非常耗费性能。因此针对频繁的 DOM 操作一定要做一些处理。

例如缓存 DOM 查询结果

```js
// 不缓存 DOM 查询结果
for (let = 0; i < document.getElementsByTagName('p').length; i++) {
    // 每次循环，都会计算 length ，频繁进行 DOM 查询
}

// 缓存 DOM 查询结果
const pList = document.getElementsByTagName('p')
const length = pList.length
for (let i = 0; i < length; i++) {
    // 缓存 length ，只进行一次 DOM 查询
}
```

再例如，插入多个标签时，先插入 Fragment 然后再统一插入DOM

```js
const listNode = document.getElementById('list')

// 创建一个文档片段，此时还没有插入到 DOM 树中
const frag = document.createDocumentFragment()

// 执行插入
for(let x = 0; x < 10; x++) {
    const li = document.createElement("li")
    li.innerHTML = "List item " + x
    frag.appendChild(li)
}

// 都完成之后，再插入到 DOM 树中
listNode.appendChild(frag)
```


# 03-JS-Web-API\02-DOM\03-解答.md
# DOM 解答

## DOM 是哪种基本的数据结构？

树

## DOM 操作的常用 API 有哪些

- 获取节点，以及获取节点的 Attribute 和 property
- 获取父节点 获取子节点
- 新增节点，删除节点

## DOM 节点的 attr 和 property 有何区别

- property 只是一个 JS 属性的修改
- attr 是对 html 标签属性的修改

## 如何一次性插入多个 DOM 节点，考虑性能

- 使用 fragment
- 先插入节点
- 最后再插入 DOM 树


# 03-JS-Web-API\03-BOM\01-题目.md
# BOM 题目

- 如何检测浏览器的类型
- 拆解 url 的各部分


# 03-JS-Web-API\03-BOM\02-知识点.md
# BOM 知识点

DOM 是浏览器针对下载的 HTML 代码进行解析得到的 JS 可识别的数据对象。而 BOM（浏览器对象模型）是浏览器本身的一些信息的设置和获取，例如获取浏览器的宽度、高度，设置让浏览器跳转到哪个地址。

- navigator
- screen
- location
- history

这些对象就是一堆非常简单粗暴的 API 没人任何技术含量，讲起来一点意思都没有，大家去 MDN 或者 w3school 这种网站一查就都明白了。面试的时候，面试官基本不会出太多这方面的题目，因为只要基础知识过关了，这些 API 即便你记不住，上网一查也都知道了。

```javascript
// navigator
var ua = navigator.userAgent
var isChrome = ua.indexOf('Chrome')
console.log(isChrome)

// screen
console.log(screen.width)
console.log(screen.height)

// location
console.log(location.href)
console.log(location.protocol) // 'http:' 'https:'
console.log(location.pathname) // '/learn/199'
console.log(location.search)
console.log(location.hash)

// history
history.back()
history.forward()
```


# 03-JS-Web-API\03-BOM\03-解答.md
# BOM 解答

## 如何检测浏览器的类型

```javascript
var ua = navigator.userAgent
var isChrome = ua.indexOf('Chrome')
console.log(isChrome)
```

## 拆解url的各部分

```javascript
console.log(location.href)
console.log(location.protocol) // 'http:' 'https:'
console.log(location.pathname) // '/learn/199'
console.log(location.search)
console.log(location.hash)
```


# 03-JS-Web-API\04-事件\01-题目.md
# 事件 题目

- 编写一个通用的事件监听函数
- 描述DOM事件冒泡流程
- 对于一个无线下拉加载图片的页面，如何给每个图片绑定事件


# 03-JS-Web-API\04-事件\02-知识点.md
# 事件 知识点

## 事件绑定

```javascript
const btn = document.getElementById('btn1')
btn.addEventListener('click', event => {
    console.log('clicked')
})
```

通用的事件绑定函数

```js
function bindEvent(elem, type, fn) {
    elem.addEventListener(type, fn)
}
const a = document.getElementById('link1')
bindEvent(a, 'click', e => {
    e.preventDefault() // 阻止默认行为
    alert('clicked')
})
```

## 事件冒泡

```html
<body>
    <div id="div1">
        <p id="p1">激活</p>
        <p id="p2">取消</p>
        <p id="p3">取消</p>
        <p id="p4">取消</p>
    </div>
    <div id="div2">
        <p id="p5">取消</p>
        <p id="p6">取消</p>
    </div>
</body>
```

对于以上 html 代码结构，点击`p1`时候进入激活状态，点击其他任何`p`都取消激活状态，如何实现？

```javascript
const p1 = document.getElementById('p1')
const body = document.body
bindEvent(p1, 'click', e => {
    e.stopPropagation() // 注释掉这一行，来体会事件冒泡
    alert('激活')
})
bindEvent(body, 'click', e => {
    alert('取消')
})
```

如果我们在`p1` `div1` `body`中都绑定了事件，它是会根据 DOM 的结构，来冒泡从下到上挨个执行的。但是我们使用`e.stopPropagation()`就可以阻止冒泡。

## 代理

我们设定一种场景，如下代码，一个`<div>`中包含了若干个`<a>`，而且还能继续增加。那如何快捷方便的为所有的`<a>`绑定事件呢？

```html
<div id="div1">
    <a href="#">a1</a>
    <a href="#">a2</a>
    <a href="#">a3</a>
    <a href="#">a4</a>
</div>
<button>点击增加一个 a 标签</button>
```

这里就会用到事件代理，我们要监听`<a>`的事件，但要把具体的事件绑定到`<div>`上，然后看事件的触发点，是不是`<a>`

```javascript
const div1 = document.getElementById('div1')
div1.addEventListener('click', e => {
    const target = e.target
    if (e.nodeName === 'A') {
        alert(target.innerHTML)
    }
})
```

那我们现在完善一下之前写过的通用事件绑定函数，加上事件代理

```javascript
function bindEvent(elem, type, selector, fn) {
    if (fn == null) {
        fn = selector
        selector = null
    }
    elem.addEventListener(type, e => {
        let target
        if (selector) {
            target = e.target
            if (target.matches(selector)) {
                fn.call(target, e)
            }
        } else {
            fn(e)
        }
    })
}
```

然后这样使用

```js
// 使用代理
const div1 = document.getElementById('div1')
bindEvent(div1, 'click', 'a', e => {
    console.log(this.innerHTML)
})

// 不使用代理
const a = document.getElementById('a1')
bindEvent(div1, 'click', e => {
    console.log(a.innerHTML)
})
```

最后，使用代理的优点

- 使代码简洁
- 减少浏览器的内存占用


# 03-JS-Web-API\04-事件\03-解答.md
# 事件 解答

## 编写一个通用的事件监听函数

```js
function bindEvent(elem, type, selector, fn) {
    if (fn == null) {
        fn = selector
        selector = null
    }
    elem.addEventListener(type, function (e) {
        let target
        if (selector) {
            target = e.target
            if (target.matches(selector)) {
                fn.call(target, e)
            }
        } else {
            fn(e)
        }
    })
}
```

## 描述DOM事件冒泡流程

- DOM 树形结构
- 事件会顺着触发元素往上冒泡

## 对于一个无线下拉加载图片的页面，如何给每个图片绑定事件

使用代理，优点

- 使代码简洁
- 减少浏览器的内存占用


# 03-JS-Web-API\05-ajax\01-题目.md
# ajax 题目

- 实现一个基本的 ajax
- 跨域的几种实现方式


# 03-JS-Web-API\05-ajax\02-知识点.md
# ajax 知识点

## XMLHttpRequest

```javascript
const xhr = new XMLHttpRequest()
xhr.open("GET", "/api", false)
xhr.onreadystatechange = function () {
    // 这里的函数异步执行，可参考之前 JS 基础中的异步模块
    if (xhr.readyState == 4) {
        if (xhr.status == 200) {
            alert(xhr.responseText)
        }
    }
}
xhr.send(null)
```

有同学可能疑问：难道考我们这个，去上班就一定让我们写原生 JS 不让用 jquery 吗？———— 当然不是，这就是考察基础知识掌握的一种手段，而掌握好了基础知识，并不一定马上就用上，但是一定会增加你干活的效率。毕竟招你进来是干活的，要快！

## 状态码说明

### readyState

xhr.readyState 的状态吗说明

- 0 - (未初始化）还没有调用send()方法 
- 1 -（载入）已调用send()方法，正在发送请求 
- 2 -（载入完成）send()方法执行完成，已经接收到全部响应内容
- 3 -（交互）正在解析响应内容 
- 4 -（完成）响应内容解析完成，可以在客户端调用了 

### status

http 状态吗有 `2xx` `3xx` `4xx` `5xx` 这几种，比较常用的有以下几种

- 200 正常
- 301 永久重定向；302 临时重定向；304 资源未被修改；
- 404 找不到资源；403 权限不允许；
- 5xx 服务器端出错了

## 跨域

### 什么是跨域

浏览器中有“同源策略”，即一个域下的页面中，无法通过 ajax 获取到其他域的接口。例如慕课网有一个接口`http://m.imooc.com/course/ajaxcourserecom?cid=459`，你自己的一个页面`http://www.yourname.com/page1.html`中的 ajax 无法获取这个接口。这正是命中了“同源策略”。如果浏览器哪些地方忽略了同源策略，那就是浏览器的安全漏洞，需要紧急修复。

url 哪些地方不同算作跨域？

- 协议
- 域名
- 端口

但是html中几个标签能逃避过同源策略——`<script src="xxx">`、`<img src="xxxx"/>`、`<link href="xxxx">`，这俩标签的 `src` 或 `href` 可以加载其他域的资源，不受同源策略限制。

因此，这是三个标签可以做一些特殊的事情。

- `<img>`可以做打点统计，因为统计方并不一定是同域的，在讲解JS基础知识异步的时候有过代码示例。除了能跨域之外，`<img>`几乎没有浏览器兼容问题，它是一个非常古老的标签。
- `<script>`和`<link>`可以使用CDN，CDN基本都是其他域的链接。
- 另外`<script>`还可以实现JSONP，能获取其他域接口的信息，接下来马上讲解。

但是请注意，所有的跨域请求方式，最终都需要信息提供方来做出相应的支持和改动，也就是要经过信息提供方的同意才行，否则接收方是无法得到他们的信息的，浏览器是不允许的。

### JSONP

首先，有一个概念要你要明白，例如访问`http://coding.m.imooc.com/classindex.html`的时候，服务器端就一定有一个`classindex.html`文件吗？—— 不一定，服务器可以拿到这个请求，然后动态生成一个文件，然后返回。
同理，`<script src="http://coding.m.imooc.com/api.js">`也不一定加载一个服务器端的静态文件，服务器也可以动态生成文件并返回。OK，接下来正式开始。

例如我们的网站和慕课网，肯定不是一个域。我们需要慕课网提供一个接口，供我们来获取。首先，我们在自己的页面这样定义

```html
<script>
window.callback = function (data) {
    // 这是我们跨域得到信息
    console.log(data)
}
</script>
```

然后慕课网给我提供了一个`http://coding.m.imooc.com/api.js`，内容如下（之前说过，服务器可动态生成内容）

```js
callback({x:100, y:200})
```

最后我们在页面中加入`<script src="http://coding.m.imooc.com/api.js"></script>`，那么这个js加载之后，就会执行内容，我们就得到内容了

### jQuery 实现 jsonp

提供方提供的数据：

```js
callback({
    "x": 100,
    "y": 200
})
```

接收方的写法：

```js
$.ajax({
    url: 'http://localhost:8882/x-origin.json',
    dataType: 'jsonp',
    jsonpCallback: 'callback',
    success: function (data) {
        console.log(data)
    }
})
```

### 服务器端设置 http header

这是需要在服务器端设置的，作为前端工程师我们不用详细掌握，但是要知道有这么个解决方案。而且，现在推崇的跨域解决方案是这一种，比 JSONP 简单许多。

```js
response.setHeader("Access-Control-Allow-Origin", "http://localhost:8011");  // 第二个参数填写允许跨域的域名称，不建议直接写 "*"
response.setHeader("Access-Control-Allow-Headers", "X-Requested-With");
response.setHeader("Access-Control-Allow-Methods", "PUT,POST,GET,DELETE,OPTIONS");

// 接收跨域的cookie
response.setHeader("Access-Control-Allow-Credentials", "true");
```


# 03-JS-Web-API\05-ajax\03-解答.md
# ajax 解答

## 手动编写一个 ajax，不依赖第三方库

```js
function ajax(url, successFn) {
    const xhr = new XMLHttpRequest()
    xhr.open("GET", url, false)
    xhr.onreadystatechange = function () {
        // 这里的函数异步执行，可参考之前 JS 基础中的异步模块
        if (xhr.readyState == 4) {
            if (xhr.status == 200) {
                successFn(xhr.responseText)
            }
        }
    }
    xhr.send(null)
}
```

## 跨域的几种实现方式

- JSONP
- 服务器端设置 http header


# 03-JS-Web-API\06-存储\01-题目.md
# 题目

- 请描述一下 cookie，sessionStorage 和 localStorage 的区别？


# 03-JS-Web-API\06-存储\02-知识点.md
# 知识点

## cookie

cookie 本身不是用来做服务器端存储的（计算机领域有很多这种“狗拿耗子”的例子，例如 css 中的 float），它设计是用来在服务器和客户端进行信息传递的，因此我们的每个 http 请求都带着 cookie。但是 cookie 也具备浏览器端存储的能力（例如记住用户名和密码），因此就被开发者用上了。

使用起来也非常简单`document.cookie = ....`即可。

但是 cookie 有它致命的缺点：

- 存储量太小，只有 4KB
- 所有 http 请求都带着，会影响获取资源的效率
- API 简单，需要封装才能用

## locationStorage 和 sessionStorage

后来，HTML5标准就带来了`sessionStorage`和`localStorage`，先拿`localStorage`来说，它是专门为了浏览器端缓存而设计的。其优点有：

- 存储量增大到 5M
- 不会带到 http 请求中
- API 适用于数据存储 `localStorage.setItem(key, value)` `localStorage.getItem(key)`

`sessionStorage`的区别就在于它是根据 session 过去时间而实现，而`localStorage`会永久有效，应用场景不懂。例如，一些重要信息需要及时失效的放在`sessionStorage`中，一些不重要但是不经常设置的信息，放在`localStorage`

另外告诉大家一个小技巧，iOS系统的safari浏览器的隐藏模式，使用`localStorage.setItem`，因此使用时尽量加入到`try-catch`中


# 03-JS-Web-API\06-存储\03-解答.md
# 解答

## 请描述一下 cookie，sessionStorage 和 localStorage 的区别？

- 容量
- 是否会携带到 ajax 中
- API易用性


# 04-开发环境\01-开始.md
# 开发环境

通过询问开发环境的问题，就能了解候选人的工作状态。

- git
- 调试工具
- 抓包
- webpack（补充 JS 模块化）
- linux 常用命令，包括 vim


# 04-开发环境\02-git.md
# git

## 题目

- git 常用命令

## 写出一些常用的 git 命令

- git add .
- git checkout xxx
- git commit -m "xxx"
- git push origin master
- git pull origin master
- git stash / git stash pop

## 简述多人使用 git 协作开发的基本流程

- git branch
- git checkout -b xxx / git checkout xxx
- git merge xxx

以及 merge 时需要解决冲突


# 04-开发环境\03-调试工具.md
# 调试工具

chrome 控制台

- element 查看元素
- console 查看打印结果和报错
- debugger 断点调试
- network 网络请求
- Application 查看 cookie 和存储


# 04-开发环境\04-抓包.md
# 抓包

移动端开发，没有 chrome 控制台的 network ，如何看网络请求呢？

- 查看移动端 h5 页的网络请求
- windows 一般用 fiddler
- mac os 一般用 charles

演示

- 手机和电脑连到同一个局域网
- 将手机代理到电脑上
- 手机浏览网页，即可抓包

**如果是 https 请求，需要安装证书**


# 04-开发环境\05-webpack.md
# wepback

参考 https://www.imooc.com/article/287156

【注意】webpack 功能非常强大，内容非常多，本节只讲一些最常见的应用

## 初始化

- `npm init -y`
- `npm i webpack webpack-cli -D`
- 新建 `src/index.js`，随便写点什么
- 新建 `webpack.config.js` 配置 `mode` `entry` `output`
- package.json 中增加 `"build": "webpack"`
- 运行 `npm run build`

## 启动服务

- `npm i html-webpack-plugin -D` ，并引用、配置插件
- 新建 `src/index.html`
- `npm i webpack-dev-server -D` ，并引用、配置
- package.json 中增减 `"dev": "webpack-dev-server"`
- 运行 `npm run dev`

## babel

ES6 编译为 ES5

- `npm i babel-loader @babel/core @babel/preset-env -D`
- 增加 babel-loader 配置
- 增加 `.babelrc` 文件
- 在 `src/index.js` 中增加一个箭头函数和 `class`，看打包结果

## 模块化

webpack4 默认支持 ES6 Module

```js
// 一个一个导出
export function fn() {
    console.log('fn')
}
export const name = 'b'
```

```js
// 一块导出
function fn() {
    console.log('fn')
}
const name = 'b'

export {  // 注意这里不能有 default ！！！
    fn,
    name
}
```

## 打包到生产环境

- 新建 `webpack.prod.js` ，注意 `mode: 'production'`
- 加上 `contentHash`
- 修改 package.json `"build": "webpack --config webpack.prod.js",`
- 运行 `npm run build` ，看打包出来的代码是被压缩过的


# 04-开发环境\06-linux命令.md
# linux 服务器的基本命令

线上服务器一般使用 linux 服务器，而且是 server 版本的 linux，没有桌面也没有鼠标，如何操作呢？

**登录**

入职之后，一般会有现有的用户名和密码，拿来之后直接登录就行。运行 `ssh name@server` 然后输入密码即可登录

**目录操作**

- 创建目录 `mkdir`
- 删除目录 `rm -rf`
- 定位目录 `cd `
- 查看目录文件 `ls` `ll`
- 修改目录名 `mv `
- 拷贝目录 `cp`

**文件操作**

- 创建文件 `touch ` `vi `
- 删除文件 `rm`
- 修改文件名 `mv`
- 拷贝文件 `cp` `scp`

**文件内容操作**

- 查看文件 `cat` `head` `tail`
- 编辑文件内容 `vi `
- 查找文件内容 `grep `


# 06-运行环境\01-开始.md
# 运行环境

- 页面加载过程
- 性能和体验优化
- 安全


# 06-运行环境\03-性能优化.md
# 性能优化

这本身就是一个大问题，会直接被问“如何提高前端性能”。而且这些性能优化的事儿，已经远远超出了 JS 知识的范畴，只不过面试会问到，我必须告诉大家一些基本的回答方式。

这种问题没有正确答案，特别是不同层面关注的点不一样

------

## 优化原则和方向

原则

- 多使用内存、缓存或者其他方法
- 减少 CPU 计算、较少网络

方向

- **加载页面和静态资源**
- **页面渲染**

------

## 加载资源优化

- 静态资源的压缩合并（JS代码压缩合并、CSS代码压缩合并、雪碧图）
- 静态资源缓存（资源名称加 MD5 戳）
- 使用 CND 让资源加载更快
- 使用 SSR 后端渲染，数据直接突出到 HTML 中

------

## 渲染优化

- CSS 放前面 JS 放后面
- 懒加载（图片懒加载、下拉加载更多）
- 减少DOM 查询，对 DOM 查询做缓存
- 减少DOM 操作，多个操作尽量合并在一起执行（`DocumentFragment`）
- 节流和防抖
- 尽早执行操作（`DOMContentLoaded`）

------

## 详细解说

### 静态资源的压缩合并

如果不合并，每个都会走一遍之前介绍的请求过程

```html
<script src="a.js"></script>
<script src="b.js"></script>
<script src="c.js"></script>
```

如果压缩了，就只走一遍请求过程

```html
<script src="abc.js"></script>
```

### 静态资源缓存

通过连接名称控制缓存

```html
<script src="abc_1.js"></script>
```

只有内容改变的时候，链接名称才会改变

```html
<script src="abc_2.js"></script>
```

### 使用 CND 让资源加载更快

```html
<script src="https://cdn.bootcss.com/zepto/1.0rc1/zepto.min.js"></script>
```

### 使用 SSR 后端渲染

如果提到 Vue 和 React 时，可以说一下

### CSS 放前面 JS 放后面

将浏览器渲染的时候，已经提高

### 懒加载

一开始先给为 src 赋值成一个通用的预览图，下拉时候再动态赋值成正式的图片

```html
<img src="preview.png" data-realsrc="abc.png"/>
```

### DOM 查询做缓存

两端代码做一下对比

```js
// 不缓存 DOM 查询结果
for (let = 0; i < document.getElementsByTagName('p').length; i++) {
    // 每次循环，都会计算 length ，频繁进行 DOM 查询
}

// 缓存 DOM 查询结果
const pList = document.getElementsByTagName('p')
const length = pList.length
for (let i = 0; i < length; i++) {
    // 缓存 length ，只进行一次 DOM 查询
}
```

总结：DOM 操作，无论查询还是修改，都是非常耗费性能的，尽量减少

### 合并 DOM 插入

DOM 操作是非常耗费性能的，因此插入多个标签时，先插入 Fragment 然后再统一插入DOM

```js
const listNode = document.getElementById('list')

// 创建一个文档片段，此时还没有插入到 DOM 树中
const frag = document.createDocumentFragment()

// 执行插入
for(let x = 0; x < 10; x++) {
    const li = document.createElement("li")
    li.innerHTML = "List item " + x
    frag.appendChild(li)
}

// 都完成之后，再插入到 DOM 树中
listNode.appendChild(frag)
```

### 尽早执行操作

```js
window.addEventListener('load', function () {
    // 页面的全部资源加载完才会执行，包括图片、视频等
})
document.addEventListener('DOMContentLoaded', function () {
    // DOM 渲染完即可执行，此时图片、视频还可能没有加载完
})
```

### 节流和防抖

例如要在文字改变时触发一个 change 事件，通过 keyup 来监听。使用**防抖**。

```js
const textarea = document.getElementById('text')
let timer
textarea.addEventListener('keyup', () => {
    if (timer) {
        clearTimeout(timer)
    }
    timer = setTimeout(() => {
        // 触发 change 事件

        // 清空定时器
        timer = null
    }, 100)
})
```

可以把防抖时间单独抽离出来实现

```js
// 手写防抖
function debounce(fn, delay = 200) {
    // timer 在闭包中
    let timer = null

    // 返回一个函数
    return function() {
        if (timer) {
            clearTimeout(timer)
        }
        timer = setTimeout(() => {
            fn.apply(this, arguments) // 透传 this 和函数参数
            timer = null // 触发过了，重新计时
        }, delay)
    }
}

const textarea = document.getElementById('text')
textarea.addEventListener('keyup', debounce(() => {
    // 触发 change 事件
}))
```

在拖拽时，随时要检测当前的位置信息（如是否覆盖了目标元素的位置），可用**节流**。

```js
// <p id="p1" draggable="true">拖动我!</p>

const p1 = document.getElmentById('p1')
p1.addEventListener('drag', e => {
    // 这样会打印很频繁，如果在其中再做一些 DOM 查询，那就出现卡顿
    console.log('鼠标位置', e.offsetX, e.offsetY)
})
```

使用节流

```js
// 手写节流
function throttle(fn, delay = 100) {
    // timger 在闭包中
    let timer = null

    // 返回一个函数
    return function(){
        //当我们发现这个定时器存在时，则表示定时器已经在运行中，还没到该触发的时候，则 return
        if (timer) {
            return
        }
        // 定时器不存在了，说明已经触发过了，重新计时
        timer = setTimeout(()=>{
            fn.apply(this, arguments) // 透传 this 和函数参数
            timer = null // 清空定时器
        }, delay)
    }
}

// 再次实现
p1.addEventListener('drag', throttle(e => {
    console.log('鼠标位置', e.offsetX, e.offsetY)
})
```


# 06-运行环境\04-安全性.md
# 安全性

## 题目

- 【面试】常见的 web 攻击方式有哪些，简述原理？如何预防？

## 解决

关于前端安全的知识，建议阅读《白帽子讲web安全》，作者也是一位很传奇的人物，这本书写的浅显易懂，很适合前端工程师阅读。

### 常见的 web 攻击方式有哪些，简述原理？如何预防？

上学的时候就知道有一个“SQL注入”的攻击方式。例如做一个系统的登录界面，输入用户名和密码，提交之后，后端直接拿到数据就拼接 SQL 语句去查询数据库。如果在输入时进行了恶意的 SQL 拼装，那么最后生成的 SQL 就会有问题。但是现在稍微大型的一点系统，都不会这么做，从提交登录信息到最后拿到授权，都经过层层的验证。因此，SQL 注入都只出现在比较低端小型的系统上。

**前端端最常见的攻击就是 XSS（Cross Site Scripting，跨站脚本攻击）**，很多大型网站（例如 FaceBook 都被 XSS 攻击过）。举一个例子，我在一个博客网站正常发表一篇文章，输入汉字、英文和图片，完全没有问题。但是如果我写的是恶意的 js 脚本，例如获取到`document.cookie`然后传输到自己的服务器上，那我这篇博客的每一次浏览，都会执行这个脚本，都会把自己的 cookie 中的信息偷偷传递到我的服务器上来。

预防 XSS 攻击就得对输入的内容进行过滤，过滤掉一切可以执行的脚本和脚本链接。大家可以参考[xss.js](https://github.com/leizongmin/js-xss)这个开源工具。

简单总结一下，XSS 其实就是攻击者事先在一个页面埋下攻击代码，让登录用户去访问这个页面，然后偷偷执行代码，拿到当前用户的信息。

**还有一个比较常见的攻击就是 CSRF/XSRF（Cross-site request forgery，跨站请求伪造）**。它是借用了当前操作者的权限来偷偷的完成某个操作，而不是拿到用户的信息。例如，一个购物网站，购物付费的接口是`http://buy.com/pay?id=100`，而这个接口在使用时没有任何密码或者 token 的验证，只要打开访问就付费购买了。一个用户已经登录了`http://buy.com`在选择商品时，突然收到一封邮件，而这封邮件正文有这么一行代码`<img src="http://buy.com/pay?id=100"/>`，他访问了邮件之后，其实就已经完成了购买。

预防 CSRF 就是加入各个层级的权限验证，例如现在的购物网站，只要涉及到现金交易，肯定输入密码或者指纹才行。


# 06-运行环境\02-页面加载\01-题目.md
# 题目

- 从输入url到得到html的详细过程
- window.onload 和 DOMContentLoaded 的区别


# 06-运行环境\02-页面加载\02-知识点.md
# 知识点

## 浏览器加载资源的过程

### 加载资源的形式

- 输入 url 加载 html
- http://coding.m.imooc.com
- 加载 html 中的静态资源
- `<script src="/static/js/jquery.js"></script>`

### 加载一个资源的过程

- 浏览器根据 DNS 服务器得到域名的 IP 地址
- 向这个 IP 的机器发送 http 请求
- 服务器收到、处理并返回 http 请求
- 浏览器得到返回内容

## 浏览器渲染页面的过程

- 根据 HTML 结构生成 DOM Tree
- 根据 CSS 生成 CSS Rule
- 将 DOM 和 CSSOM 整合形成 RenderTree
- 根据 RenderTree 开始渲染和展示
- 遇到`<script>`时，会执行并阻塞渲染

## 几个示例

### 最简单的页面

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <p>test</p>
</body>
</html>
```

### 引用 css

css 内容

```css
div {
    width: 100%;
    height: 100px;
    font-size: 50px;
}
```

html 内容

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" type="text/css" href="test.css">
</head>
<body>
    <div>test</div>
</body>
</html>
```

最后思考为何要把 css 放在 head 中？？？


### 引入 js

js 内容

```js
document.getElementById('container').innerHTML = 'update by js'
```

html 内容

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <div id="container">default</div>
    <script src="index.js"></script>
    <p>test</p>
</body>
</html>
```

思考为何要把 JS 放在 body 最后？？？

### 有图片

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <p>test</p>
    <p><img src="test.png"/></p>
    <p>test</p>
</body>
</html>
```

引出`window.onload`和`DOMContentLoaded`

```js
window.addEventListener('load', function () {
    // 页面的全部资源加载完才会执行，包括图片、视频等
})
document.addEventListener('DOMContentLoaded', function () {
    // DOM 渲染完即可执行，此时图片、视频还可能没有加载完
})
```


# 06-运行环境\02-页面加载\03-解答.md
# 解答

## 从输入url到得到html的详细过程

- 浏览器根据 DNS 服务器得到域名的 IP 地址
- 向这个 IP 的机器发送 http 请求
- 服务器收到、处理并返回 http 请求
- 浏览器得到返回内容

## window.onload 和 DOMContentLoaded 的区别

- 页面的全部资源加载完才会执行，包括图片、视频等
- DOM 渲染完即可执行，此时图片、视频还没有加载完


# 07-其他\01-技巧and注意事项.md
# 注意事项

## 简历

- 简洁明了，重点突出你做过那些有技术性的项目，标明你使用过的技术以及解决方案
- 博客，反思总结的能力
- 开源，保持技术热情
- 简历一定要真实，不要造假（能力上真实，并非事实上的真实）

## 面试过程中

- 如何看待加班？加班就像借钱，救急不救穷
- 千万不可挑战面试官，不要反考面试官
- 学会给面试官惊喜。针对已经回答的问题，最好能有所补充（或者说出你的解题思路也好），但是不要扯开话题，不宜过多
- 遇到不会回答的问题，说出你知道的也可以，能得50分也比白卷好
- 谈谈你的缺点 ———— 别傻乎乎的吧自己缺点都说出来，说一些你最近正要学习但是还没完全学会的知识就好了。


# 08-面试题讲解\01-面试题.md
# 面试题

## var 和 let const 的区别

- var 是 ES5 及之前的语法，let const 是 ES6 语法
- var 和 let 是变量，可修改；const 是常量，不可修改
- var 有变量提升，let const 没有
- var 没有块级作用域，let const 有 （ES6 语法有块级作用域）

```js
// var 变量提升
console.log('a', a)
var a = 100

// let 没有变量提升
console.log('b', b)
let b = 200
```

```js
// var 没有块级作用域
for (var i = 0; i < 10; i++) {
    var j = 1 + i
}
console.log(i, j)

// let 有块级作用域
for (let x = 0; x < 10; x++) {
    let y = 1 + x
}
console.log(x, y)
```

## typeof 有哪些返回类型？

```js
// 判断所有值类型
let a
console.log(a) // 'undefined'
const str = 'abc'
typeof str  // 'string'
const n = 100
typeof n // 'number'
const b = true
typeof b // 'boolean'
const s = Symbol('s')
typeof s // 'symbol'
```

## 列举强制类型转换和隐式类型转换

- 强制 `parseInt` `parseFloat`
- 隐式 `if` ，`==` ， `+` 拼接字符串

## 手写深度比较，如 lodash isEqual

```js
// 实现如下效果
const obj1 = {a: 10, b: { x: 100, y: 200 }}
const obj2 = {a: 10, b: { x: 100, y: 200 }}
isEqual(obj1, obj2) === true
```

```js
// 判断是否是 object
function isObject(obj) {
    return typeof obj === 'object' && obj !== null
}
// 全相等
function isEqual(obj1, obj2) {
    if (!isObject(obj1) || !isObject(obj2)) {
        // 值类型，不是对象或数组（注意，equal 时一般不会有函数，这里忽略）
        return obj1 === obj2
    }
    if (obj1 === obj2) {
        // 两个引用类型全相等（同一个地址）
        return true
    }
    // 两个都是引用类型，不全相等
    // 1. 先取出 obje2 obj2 的 keys，比较个数
    const obj1Keys = Object.keys(obj1)
    const obj2Keys = Object.keys(obj2)
    if (obj1Keys.length !== obj2Keys.length) {
        // keys 个数不相等，则不是全等
        return false
    }
    // 2. 以 obj1 为基准，和 obj2 依次递归比较
    for (let key in obj1) {
        // 递归比较
        const res = isEqual(obj1[key], obj2[key])
        if (!res) {
            // 遇到一个不相等的，则直接返回 false
            return false
        }
    }
    // 3. 都相等，则返回 true
    return true
}
```

## `split()` 和 `join()` 的区别

```js
'1-2-3'.split('-')
[1,2,3].join('-')
```

## 数组的 `pop` `push` `unshift` `shift` 分别做什么

注意以下几点

- 函数作用是什么？
- 返回值是什么？
- 对原数组是否造成影响？
- 如何对原数组不造成影响？`concat` `slice` `map` `filter`

【扩展】数组 API 的纯函数和非纯函数

**纯函数** —— 1. 不改变来源的数组； 2. 返回一个数组

- concat
- map
- filter
- slice

```js
const arr = [100, 200, 300]
const arr1 = arr.concat([400, 500])
const arr2 = arr.map(num => num * 10)
const arr3 = arr.filter(num => num > 100)
const arr4 = arr.slice(-1)
```

**非纯函数**

情况1，改变了原数组

- push
- reverse
- sort
- splice

情况2，未返回数组

- push
- forEach
- reduce
- some

## 数组 slice 和 splice 的区别？

slice - 切片；splice - 剪接；

```js
// slice()
const arr1 = [10, 20, 30, 40, 50]
const arr2 = arr1.slice() // arr2 和 arr1 不是一个地址，纯函数，重要！！！

// arr.slice(start, end)
const arr1 = [10, 20, 30, 40, 50]
const arr2 = arr1.slice(1, 4) // [20, 30, 40]

// arr.slice(start)
const arr1 = [10, 20, 30, 40, 50]
const arr2 = arr1.slice(2) // [30, 40, 50]

// 负值
const arr1 = [10, 20, 30, 40, 50]
const arr2 = arr1.slice(-2) // [40, 50]
```

```js
// arr.splice(index, howmany, item1, ....., itemX)
const arr1 = [10, 20, 30, 40, 50]
const arr2 = arr1.splice(1, 2, 'a', 'b', 'c') // [20, 30]
// arr1 会被修改，不是纯函数，即有副作用
```

## `[10, 20, 30].map(parseInt)` 的结果是什么？

```js
// 拆解开就是
[10, 20, 30].map((num, index) => {
    return parseInt(num, index)
    // parseInt 第二个参数是进制
    // 如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。
    // 如果该参数小于 2 或者大于 36，则 parseInt() 将返回 NaN
})
```

```js
// 可以对比
[10, 20, 30].map((num, index) => {
    return parseInt(num, 10)
})
```

## ajax 请求中 get 和 post 的区别

- get 一般用于查询操作，post 一般用于提交操作
- get 参数在 url 上，post 在请求体内
- 安全性：post 请求易于防止 CSRF

（post 代码演示：网页，postname）

## call 和 apply 的区别

- `fn.call(this, p1, p2, p3)`
- `fn.apply(this, arguments)`

## 事件委托（代理）是什么

```javascript
const p1 = document.getElementById('p1')
const body = document.body
bindEvent(p1, 'click', e => {
    e.stopPropagation() // 注释掉这一行，来体会事件冒泡
    alert('激活')
})
bindEvent(body, 'click', e => {
    alert('取消')
})
```

## 闭包是什么，有什么特性，对页面有什么影响

知识点回顾

- 回归作用域和自由变量
- 闭包的应用场景：函数作为参数被传入，函数作为返回值被返回
- 关键点：自由变量的查找，要在函数定义的地方，而不是执行的地方

对页面的影响

- 变量内存得不到释放，可能会造成内存积累（不一定是泄露）

```js
// 自由变量示例 —— 内存会被释放
let a = 0
function fn1() {
    let a1 = 100

    function fn2() {
        let a2 = 200

        function fn3() {
            let a3 = 300
            return a + a1 + a2 + a3
        }
        fn3()
    }
    fn2()
}
fn1()
```

```js
// 闭包 函数作为返回值 —— 内存不会被释放
function create() {
    let a = 100
    return function () {
        console.log(a)
    }
}
let fn = create()
let a = 200
fn() // 100

// 闭包 函数作为参数 —— 内存不会被释放
function print(fn) {
    let a = 200
    fn()
}
let a = 100
function fn() {
    console.log(a)
}
print(fn) // 100
```

## 如何阻止事件冒泡和默认行为

`event.stopPropagation()`
`event.preventDefault()`

## 添加 删除 替换 插入 移动 DOM 节点的方法

（粘贴一下代码片段，作为回顾）

## 怎样减少 DOM 操作？

- 缓存 DOM 查询结果
- 多次操作，合并到一次插入

（粘贴一下代码片段，作为回顾）

## 解释 jsonp 的原理，以及为什么不是真正的 ajax

- 浏览器的同源策略，什么是跨域？
- 哪些 html 标签能绕过跨域？
- jsonp 原理

## document load 和 document ready 的区别

```js
window.addEventListener('load', function () {
    // 页面的全部资源加载完才会执行，包括图片、视频等
})
document.addEventListener('DOMContentLoaded', function () {
    // DOM 渲染完即可执行，此时图片、视频还可能没有加载完
})
```

## `==` 和 `===` 的不同

- == 会尝试进行类型转换
- === 严格相等

## 函数声明与函数表达式的区别？

```js
const res = sum(10, 20)
console.log(res) // 30

// 函数声明
function sum(x, y) {
    return x + y
}
```

```js
const res = sum(100, 200)
console.log(res) // 报错！！！

// 函数表达式
const sum = function(x, y) {
    return x + y
}
```

## `new Object()` 和 `Object.create()` 的区别

示例一

```js
const obj1 = {
    a: 10,
    b: 20,
    sum() {
        return this.a + this.b
    }
}
const obj2 = new Object({
    a: 10,
    b: 20,
    sum() {
        return this.a + this.b
    }
})
const obj3 = Object.create({
    a: 10,
    b: 20,
    sum() {
        return this.a + this.b
    }
})
// 分别打印看结构
```

示例二

```js
const obj1 = {
    a: 10,
    b: 20,
    sum() {
        return this.a + this.b
    }
}
const obj2 = new Object(obj1)
console.log(obj1 === obj2) // true
const obj3 = Object.create(obj1)
console.log(obj1 === obj3) // false

const obj4 = Object.create(obj1)
console.log(obj3 === obj4) // false

// 然后修改 obj1 ，看 obj2 obj3 和 obj4
obj1.printA = function () {
    console.log(this.a)
}
```

## 对作用域上下文和 this 的理解，场景题

```js
const User = {
    count: 1,
    getCount: function() {
        return this.count
    }
}
console.log(User.getCount()) // what?
const func = User.getCount
console.log( func() ) // what?
```

## 对作用域和自由变量的理解，场景题

```js
let i
for(i = 1; i <= 3; i++) {
  setTimeout(function(){
      console.log(i)
  }, 0)
}
// what?
```

## 判断字符串以字母开头，后面可以是数字，下划线，字母，长度为 6-30

`const reg = /^[a-zA-Z]\w{5,29}$/`

- 查看正则表达式规则 https://www.runoob.com/regexp/regexp-syntax.html
- 查看常见正则表达式

```js
/\d{6}/ // 邮政编码
/^[a-z]+$/ // 小写英文字母
/^[A-Za-z]+$/ // 英文字母
/^\d{4}-\d{1,2}-\d{1,2}$/ // 日期格式
/^[a-zA-Z]\w{5,17}$/ // 用户名（字母开头，字母数字下划线，5-17位）
/\d+\.\d+\.\d+\.\d+/ // 简单的 IP 地址格式
```

## 以下代码，分别 alert 出什么？

```js
let a = 100
function test() {  
    alert(a)
    a = 10
    alert(a)
}
test()
alert(a)
// what?
```

## 手写 trim 函数，保证浏览器兼容性

```js
String.prototype.trim= function (){
    return this.replace(/^\s+/,"").replace(/\s+$/,"")
}
```

知识点：原型，this，正则

## 如何获取多个数值中的最大值？

```js
Math.max(10, 30, 20, 40)
// 以及 Math.min
```

```js
function max() {
    const nums = Array.prototype.slice.call(arguments) // 变为数组
    let max = 0
    nums.forEach(n => {
        if (n > max) {
            max = n
        }
    })
    return max
}
```

## 如何用 JS 实现继承？

class 代码

## 程序中捕获异常的方法

```js
try {
    // todo
} catch (ex) {
    console.error(ex) // 手动捕获 catch
} finally {
    // todo
}
```

```js
// 自动捕获 catch（但对跨域的 js 如 CDN 的，不会有详细的报错信息）
window.onerror = function (message, source, lineNom, colNom, error) {
}
```

## 什么是 JSON ？

首先，json 是一种数据格式标准，本质是一段字符串，独立于任何语言和平台。注意，json 中的字符串都必须用双引号。

```json
{
    "name": "张三",
    "info": {
        "single": true,
        "age": 30,
        "city": "北京"
    },
    "like": ["篮球", "音乐"]
}
```

其次，JSON 是 js 中一个内置的全局变量，有 `JSON.parse` 和 `JSON.stringify` 两个 API 。

## 获取当前页面 url 参数

自己实现

```js
// const url = 'https://www.xxx.com/path/index.html?a=100&b=200&c=300#anchor'
function query(name) {
    const search = location.search.substr(1) // 去掉前面的 `?`
    const reg = new RegExp(`(^|&)${name}=([^&]*)(&|$)`, 'i')
    const res = search.match(reg)
    if (res === null) {
        return null
    }
    return decodeURIComponent(res[2])
}
console.log( query('a') )
console.log( query('c') )
```

新的 API `URLSearchParams`

```js
const pList = new URLSearchParams(location.search)
pList.get('a')
```

## 将 url 参数解析为 JS 对象？

自己编写

```js
function queryToObj() {
    const res = {}
    const search = location.search.substr(1) // 去掉前面的 `?`
    search.split('&').forEach(paramStr => {
        const arr = paramStr.split('=')
        const key = arr[0]
        const val = arr[1]
        res[key] = val
    })
    return res
}
```

新的 API `URLSearchParams`

```js
function queryToObj() {
    const res = {}
    const pList = new URLSearchParams(location.search)
    pList.forEach((val, key) => {
        res[key] = val
    })
    return res
}
```

## 实现数组 flatern ，考虑多层级

```js

function flat(arr) {
    // 验证 arr 中，还有没有深层数组，如 [1, [2, 3], 4]
    const isDeep = arr.some(item => item instanceof Array)
    if (!isDeep) {
        return arr // 没有深层的，则返回
    }

    // 多深层的，则 concat 拼接
    const res = Array.prototype.concat.apply([], arr) // 回归上文，apply 和 call 的区别
    return flat(res) // 递归调用，考虑多层
}
flat([[1,2], 3, [4,5, [6,7, [8, 9, [10, 11]]]]])
```

## 数组去重

要考虑：

- 顺序是否一致？
- 时间复杂度

ES5 语法手写。

```js
// 写法一
function unique(arr) {
    const obj = {}
    arr.forEach(item => {
        obj[item] = 1 // 用 Object ，去重计算高效，但顺序不能保证。以及，非字符串会被转换为字符串！！！
    })
    return Object.keys(obj)
}
unique([30, 10, 20, 30, 40, 10])
```

```js
// 写法二
function unique(arr) {
    const res = []
    arr.forEach(item => {
        if (res.indexOf(item) < 0) { // 用数组，每次都得判断是否重复（低效），但能保证顺序
            res.push(item)
        }
    })
    return res
}
unique([30, 10, 20, 30, 40, 10])
```

用 ES6 Set

```js
// 数组去重
function unique(arr) {
    const set = new Set(arr)
    return [...set]
}
unique([30, 10, 20, 30, 40, 10])
```

## 手写深拷贝

粘贴代码

【注意】`Object.assign` 不是深拷贝，可以顺带讲一下用法

- `Object.assign(obj1, {...})`
- `const obj2 = Object.assign({}, obj1, {...})`

## 介绍一下 RAF requestAnimationFrame

想用 JS 去实现动画，老旧的方式是用 setTimeout 实时刷新，但这样效率非常低，而且可能会出现卡顿。

- 想要动画流畅，更新频率是 60帧/s ，即每 16.6ms 更新一次试图。太慢了，肉眼会感觉卡顿，太快了肉眼也感觉不到，资源浪费。
- 用 setTimeout 需要自己控制这个频率，而 requestAnimationFrame 不用自己控制，浏览器会自动控制
- 在后台标签或者隐藏的`<iframe>`中，setTimeout 依然会执行，而 requestAnimationFrame 会自动暂停，节省计算资源

（代码演示）

## 对前端性能优化有什么了解？一般都通过那几个方面去优化的？

原则

- 多使用内存、缓存或者其他方法
- 减少 CPU 计算、较少网络

方向

- 加载页面和静态资源
- 页面渲染


# 08-面试题讲解\02-面试题-202109升级\01-Map和Object区别.md
# Map 和 Object 的不同

## API 不同

```js
// 初始化
const m = new Map([
    ['key1', 'hello'],
    ['key2', 100],
    ['key3', { x: 10 }]
])

// 新增
m.set('name', '双越')

// 删除
m.delete('key1')

// 判断
m.has('key2')

// 遍历
m.forEach((value, key) => console.log(key, value))

// 长度（Map 是有序的，下文会讲，所有有长度概念）
m.size
```

## 以任意类型为 key

```js
const m = new Map()
const o = { p: 'Hello World' }

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```

## Map 是有序结构

Object key 不能按照既定顺序输出

```js
// Object keys 是无序的
const data1 = {'1':'aaa','2':'bbb','3':'ccc','测试':'000'}
Object.keys(data1) // ["1", "2", "3", "测试"]

const data2 = {'测试':'000','1':'aaa','3':'ccc','2':'bbb'};
Object.keys(data2); // ["1", "2", "3", "测试"]
```

Map key 可以按照既定顺序输出

```js
const m1 = new Map([
    ['1', 'aaa'],
    ['2', 'bbb'],
    ['3', 'ccc'],
    ['测试', '000']
])
m1.forEach((val, key) => { console.log(key, val) })
const m2 = new Map([
    ['测试', '000'],
    ['1', 'aaa'],
    ['3', 'ccc'],
    ['2', 'bbb']
])
m2.forEach((val, key) => { console.log(key, val) })
```

## Map 很快

Map 作为纯净的 key-value 数据结构，它比 Object 承载了更少的功能。<br>
Map 虽然有序，但操作很快，和 Object 效率相当。

```js
// Map
const m = new Map()
for (let i = 0; i < 1000 * 10000; i++) {
    m.set(i + '', i)
}
console.time('map find')
m.has('2000000')
console.timeEnd('map find')
console.time('map delete')
m.delete('2000000')
console.timeEnd('map delete')
```

```js
// Object
const obj = {}
for (let i = 0; i < 1000 * 10000; i++) {
    obj[i + ''] = i
}
console.time('obj find')
obj['200000']
console.timeEnd('obj find')
console.time('obj delete')
delete obj['200000']
console.timeEnd('obj delete')
```

另外，Map 有序，指的是 key 能按照构架顺序输出，并不是说它像数组一样是一个有序结构 —— 否则就不会这么快了<br>
但这就足够满足我们的需求了。

## WeakMap

WeakMap 也是弱引用。但是，**WeakMap 弱引用的只是键名 key ，而不是键值 value**。

```js
// 函数执行完，obj 会被销毁，因为外面的 WeakMap 是“弱引用”，不算在内
const wMap = new WeakMap()
function fn() {
    const obj = {
        name: 'zhangsan'
    }
    // 注意，WeakMap 专门做弱引用的，因此 WeakMap 只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。其他的无意义
    wMap.set(obj, 100) 
}
fn()
// 代码执行完毕之后，obj 会被销毁，wMap 中也不再存在。但我们无法第一时间看到效果。因为：
// 内存的垃圾回收机制，不是实时的，而且是 JS 代码控制不了的，因此这里不一定能直接看到效果。
```

另外，WeakMap 没有 `forEach` 和 `size` ，只能 `add` `delete` `has` 。因为弱引用，其中的 key 说不定啥时候就被销毁了，不能遍历。

WeakMap 可以做两个对象的关联关系，而不至于循环引用，例如：

```js
const userInfo = { name: '双越' }
const cityInfo = { city: '北京' }

// // 常规关联，可能会造成循环引用
// userInfo.city = cityInfo
// cityInfo.user = userInfo

// 使用 WeakMap 做关联，则无任何副作用
const user_to_city = new WeakMap()
user_to_city.set(userInfo, cityInfo)
```

## 总结

- key 可以是任意数据类型
- key 会按照构建顺序输出
- 很快
- WeakMap 弱引用


# 08-面试题讲解\02-面试题-202109升级\02-Set和数组的区别.md
# Set 和数组的区别

## Set 元素不能重复

```js
const arr = [10, 20, 30, 30, 40]
const set = new Set([10, 20, 30, 30, 40]) // 会去重
console.log(set) // Set(4) {10, 20, 30, 40}
```

```js
// 数组去重
function unique(arr) {
    const set = new Set(arr)
    return [...set]
}
unique([10, 20, 30, 30, 40])
```

## API 不一样

```js
// 初始化
const set = new Set([10, 20, 30, 30, 40]) 

// 新增（没有 push unshift ，因为 Set 是无序的，下文会讲）
set.add(50)

// 删除
set.delete(10)

// 判断
set.has(20)

// 长度
set.size

// 遍历
set.forEach(val => console.log(val))

// set 没有 index ，因为是无序的
```

## Set 是无序的，而数组是有序的 —— 这一点很少有人提到，却很关键！！！

先看几个测试

- 数组：前面插入元素 vs 后面插入元素
- 数组插入元素 vs Set 插入元素
- 数组寻找元素 vs Set 寻找元素

```js
// 构造一个大数组
const arr = []
for (let i = 0; i < 1000000; i++) {
    arr.push(i)
}

// 数组 前面插入一个元素
console.time('arr unshift')
arr.unshift('a')
console.timeEnd('arr unshift') // unshift 非常慢
// 数组 后面插入一个元素
console.time('arr push')
arr.push('a')
console.timeEnd('arr push') // push 很快

// 构造一个大 set
const set = new Set()
for (let i = 0; i < 1000000; i++) {
    set.add(i)
}

// set 插入一个元素
console.time('set test')
set.add('a')
console.timeEnd('set test') // add 很快

// 最后，同时在 set 和数组中，寻找一个元素
console.time('set find')
set.has(490000)
console.timeEnd('set find') // set 寻找非常快
console.time('arr find')
arr.includes(490000)
console.timeEnd('arr find') // arr 寻找较慢
```

什么是无序，什么是有序？参考 `x1-有序和无序.md`

- 无序：插入、查找更快
- 有序：插入、查找更慢

因此，如果没有**强有序**的需求，请用 Set ，会让你更快更爽！

## WeakSet

WeekSet 和 Set 类似，区别在于 —— 它不会对元素进行引用计数，更不容易造成内存泄漏。

```js
// 函数执行完，obj 就会被 gc 销毁
function fn() {
    const obj = {
        name: 'zhangsan'
    }
}
fn()
```

```js
// 函数执行完，obj 不会被销毁，因为一直被外面的 arr 引用着
const arr = []
function fn() {
    const obj = {
        name: 'zhangsan'
    }
    arr.push(obj)
}
fn()
```

```js
// 函数执行完，obj 会被销毁，因为外面的 WeakSet 是“弱引用”，不算在内
const wSet = new WeakSet()
function fn() {
    const obj = {
        name: 'zhangsan'
    }
    wSet.add(obj) // 注意，WeakSet 就是为了做弱引用的，因此不能 add 值类型！！！无意义
}
fn()
```

【注意】内存的垃圾回收机制，不是实时的，而且是 JS 代码控制不了的，因此这里不一定能直接看到效果。
WeekSet 没有 `forEach` 和 `size`，只能 `add` `delete` 和 `has`。因为垃圾回收机制不可控（js 引擎看时机做垃圾回收），那其中的成员也就不可控。

## 总结

- Set 值不能重复
- Set 是无序结构
- WeakSet 对元素若引用


# 08-面试题讲解\02-面试题-202109升级\03-reduce.md
# 数组求和

## 传统方式

```js
function sum(arr) {
    let res = 0
    arr.forEach(n => res = res + n)
    return res
}
const arr = [10, 20, 30]
console.log( sum(arr) )
```

## reduce 方法的使用

```js
// 累加器
const arr1 = [10, 20, 30, 40, 50]
const arr1Sum = arr1.reduce((sum, curVal, index, arr) => {
    console.log('reduce function ......')
    console.log('sum', sum)
    console.log('curVal', curVal)
    console.log('index', index)
    console.log('arr', arr)

    return sum + curVal // 返回值，会作为下一次执行的 sum
}, 0)
console.log('arr1Sum', arr1Sum)
```

## reduce 的其他用法

```js
// 计数
function count(arr, value) {
    // 计算 arr 中有几个和 value 相等的数
    return arr.reduce((c, item) => {
        return item === value ? c + 1 : c
    }, 0)
}
const arr2 = [10, 20, 30, 40, 50, 10, 20, 10]
console.log( count(arr2, 20) )
```

```js
// 数组输出字符串
const arr3 = [
    { name: 'xialuo', number: '100' },
    { name: 'madongmei', number: '101' },
    { name: 'zhangyang', number: '102' }
]
// // 普通做法 1（需要声明变量，不好）
// let arr3Str = ''
// arr3.forEach(item => {
//     arr3Str += `${item.name} - ${item.number}\n`
// })
// console.log(arr3Str)
// // 普通做法 2（map 生成数组，再进行 join 计算）
// console.log(
//     arr3.map(item => {
//         return `${item.name} - ${item.number}`
//     }).join('\n')
// )
// reduce 做法（只遍历一次，即可返回结果）
console.log(
    arr3.reduce((str, item) => {
        return `${str}${item.name} - ${item.number}\n`
    }, '')
)
```


# 08-面试题讲解\02-面试题-202109升级\04-手写Promise.md
# 手写 Promise

要从 0 实现一个 Promise/A+ 的所有功能，是非常复杂的。面试一共 1h ，不可能考这么详细。<br>
再者，绝大部分程序员也无法短时间、高质量的写出一个完整的 Promise 。因为日常不写，只用。

所以，面试考察“手写 Promise”考察的就是一个设计思路，编码能力。并不是真让你写出来使用。

Promise 基本功能（面试时能写出这些，就足够了）
- 初始化
- 异步执行
- `then` `catch` 和 链式调用
- `.resolve` `.reject`
- `.all` `.race`

写代码……

------

`const v = fn1(this.value)` 返回值可能是一个 promise 实例


# 08-面试题讲解\02-面试题-202109升级\x1-有序和无序.md
# 附：有序和无序

单独解释有序和无序数据结构

## 形象的比喻

假象一个场景：一个大操场，一万个学生，你是管理这些学生的老师。

**无序结构**：放羊式散养，但你要认识每个人（费脑子），有一个花名册

- 新增一个学生：记录下这个学生的名字，把学生丢进操场，爱去哪儿去哪儿，别跑了就行。
- 查找一个学生：根据学生的名字，你站在高处一眼把学生认出来。（或者，那一根线把学生的手和名单上的名字牵起来，查找时根据名字，牵线拉出来）

（此处画个图。。。）

**有序结构**：排好队，一个挨一个，你不用认识每个人，也无需要花名册

- 最前面插入一个学生：让 10000 个人挨个往后挪一个位置，空出最前面的位置，插入学生
- 中间插入一个学生：找位置加塞进去，后面每个学生都往后挪一个位置（5000 个人挨个往后挪）
- 最后面插入一个学生：比较简单，直接排队尾即可
- 查找学生：从第一名学生开始，挨个往后查找，直到找到为止

（此处画个图。。。）

## Array 和 Object

抛开 ES6 的 Map 和 Set 不谈。其实 ES5 中数组和对象，就是有序和无序。

```js
// 有序
const arr = [ /* 一万个学生 */ ]
arr.unshift('张三') // 最前面插入一位
arr.splice(4999, 0, '李四') // 中间插入一位
arr.push('王五') // 最后插入一位
arr.includes('xxx') // 查找一个学生

// 无序
const obj = {
    'zhangsan': true, // 光记录名字，其他信息没有，就随便用 true 代替了
    'lisi': true.
    // 一共一万个学生
}
obj['wangwu'] = true // 插入一个学生
'xxx' in obj // 查找一个学生
```

## 应用场景

虽然大家平常都用数组和对象，但对有序和无序的场景并不一定有考虑到。举一个 vnode 例子。

```js
{ // tag attrs children 可以是无序的
    tag: 'div',
    attrs: { // id className style 可以是无序的
        id: 'div1',
        className: 'container'
        style: 'color: red;'
    },
    children: [ // children 必须是有序的！！！否则渲染就乱了！！！
        {
            tag: 'img',
            attrs: { src: 'xxx.png', alt: 'xxx' }
        },
        'hello',
        'world'
    ]
}
```

还有：栈和队列，必须是有序的，顺序不能乱。。。

## 总结

- 有序结构
    - 优点：组织有序，不混乱
    - 缺点：插入、查找太慢
- 无序结构
    - 优点：插入、查找很快
    - 缺点：无序

【思考】有没有一种数据结构能整合两者的优点呢？—— 二叉树，以及二叉树的其他变种（数据结构内容，不课程不讲）


# 09-升级-JS异步进阶\00-开始.md
# 异步进阶

之前将 JS 异步，重点在实际**应用**，这是基本要求。—— 单线程，异步场景，promise 应用等。
而本章重点在**进阶和原理**，大厂常考。

从思维导图来看，补充的内容不多，但实际内容非常多，而且很重要。特别是对于面试。

- event-loop
- promise 进阶
- async/await
- 微任务 & 宏任务

------

**课程宣传文案**，增加以下关键词：event-loop async/await 微任务/宏任务

**修改现有小节的标题**

补充思维导图


# 09-升级-JS异步进阶\01-题目.md
# 异步 题目

- 描述 event loop 运行机制（可画图）
- Promise 哪几种状态，如何变化？
- 宏任务和微任务的区别
- 场景题：Promise catch 连接 then
- 场景题：Promise 和 setTimeout 顺序
- 场景题：各类异步执行顺序问题
- **手写 Promise**

## Promise catch 连接 then

```js
// 第一题
Promise.resolve().then(() => {
    console.log(1)
}).catch(() => {
    console.log(2)
}).then(() => {
    console.log(3)
})
// 1 3

// 第二题
Promise.resolve().then(() => {
    console.log(1)
    throw new Error('erro1')
}).catch(() => {
    console.log(2)
}).then(() => {
    console.log(3)
})
// 1 2 3

// 第三题
Promise.resolve().then(() => {
    console.log(1)
    throw new Error('erro1')
}).catch(() => {
    console.log(2)
}).catch(() => { // 注意这里是 catch
    console.log(3)
})
// 1 2
```

## async/await 语法问题

```js
async function fn() {
    return 100
}
(async function () {
    const a = fn() // ??               // promise
    const b = await fn() // ??         // 100
})()
```

```js
(async function () {
    console.log('start')
    const a = await 100
    console.log('a', a)
    const b = await Promise.resolve(200)
    console.log('b', b)
    const c = await Promise.reject(300)
    console.log('c', c)
    console.log('end')
})() // 执行完毕，打印出那些内容？
```

## Promise 和 setTimeout 顺序

```js
console.log(100)
setTimeout(() => {
    console.log(200)
})
Promise.resolve().then(() => {
    console.log(300)
})
console.log(400)
// 100 400 300 200
```

## 执行顺序问题

```js
async function async1 () {
  console.log('async1 start')
  await async2() // 这一句会同步执行，返回 Promise ，其中的 `console.log('async2')` 也会同步执行
  console.log('async1 end') // 上面有 await ，下面就变成了“异步”，类似 cakkback 的功能（微任务）
}

async function async2 () {
  console.log('async2')
}

console.log('script start')

setTimeout(function () { // 异步，宏任务
  console.log('setTimeout')
}, 0)

async1()

new Promise (function (resolve) { // 返回 Promise 之后，即同步执行完成，then 是异步代码
  console.log('promise1') // Promise 的函数体会立刻执行
  resolve()
}).then (function () { // 异步，微任务
  console.log('promise2')
})

console.log('script end')

// 同步代码执行完之后，屡一下现有的异步未执行的，按照顺序
// 1. async1 函数中 await 后面的内容 —— 微任务
// 2. setTimeout —— 宏任务
// 3. then —— 微任务
```


# 09-升级-JS异步进阶\02-event-loop.md
# event loop

写一段代码，画图讲解即可

```js
console.log('Hi')

setTimeout(function cb1() {
    console.log('cb1') // cb 即 callback
}, 5000)

console.log('Bye')
```

------

DOM 事件，也用 event loop

```html
<button id="btn1">提交</button>

<script>
console.log('Hi')

$('#btn1').click(function (e) {
    console.log('button clicked')
})

console.log('Bye')
</script>
```


# 09-升级-JS异步进阶\03-promise.md
# Promise

- 三种状态
- 状态和 then catch
- 常用 API

先回顾一下 Promise 的基本使用

```js
// 加载图片
function loadImg(src) {
    const p = new Promise(
        (resolve, reject) => {
            const img = document.createElement('img')
            img.onload = () => {
                resolve(img)
            }
            img.onerror = () => {
                const err = new Error(`图片加载失败 ${src}`)
                reject(err)
            }
            img.src = src
        }
    )
    return p
}
const url = 'https://img.mukewang.com/5a9fc8070001a82402060220-140-140.jpg'
loadImg(url).then(img => {
    console.log(img.width)
    return img
}).then(img => {
    console.log(img.height)
}).catch(ex => console.error(ex))
```

## 三种状态

三种状态 pending resolved rejected

（画图表示转换关系，以及转换不可逆）

```js
// 刚定义时，状态默认为 pending
const p1 = new Promise((resolve, reject) => {

})

// 执行 resolve() 后，状态变成 resolved
const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve()
    })
})

// 执行 reject() 后，状态变成 rejected
const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject()
    })
})

```

```js
// 直接返回一个 resolved 状态
Promise.resolve(100)
// 直接返回一个 rejected 状态
Promise.reject('some error')
```

## 状态和 then catch

状态变化会触发 then catch —— 这些比较好理解，就不再代码演示了

- pending 不会触发任何 then catch 回调
- 状态变为 resolved 会触发后续的 then 回调
- 状态变为 rejected 会触发后续的 catch 回调

-----

then catch 会继续返回 Promise ，**此时可能会发生状态变化！！！**

```js
// then() 一般正常返回 resolved 状态的 promise
Promise.resolve().then(() => {
    return 100
})

// then() 里抛出错误，会返回 rejected 状态的 promise
Promise.resolve().then(() => {
    throw new Error('err')
})

// catch() 不抛出错误，会返回 resolved 状态的 promise
Promise.reject().catch(() => {
    console.error('catch some error')
})

// catch() 抛出错误，会返回 rejected 状态的 promise
Promise.reject().catch(() => {
    console.error('catch some error')
    throw new Error('err')
})
```

看一个综合的例子，即那几个面试题

```js
// 第一题
Promise.resolve().then(() => {
    console.log(1)
}).catch(() => {
    console.log(2)
}).then(() => {
    console.log(3)
})

// 第二题
Promise.resolve().then(() => { // 返回 rejected 状态的 promise
    console.log(1)
    throw new Error('erro1')
}).catch(() => { // 返回 resolved 状态的 promise
    console.log(2)
}).then(() => {
    console.log(3)
})

// 第三题
Promise.resolve().then(() => { // 返回 rejected 状态的 promise
    console.log(1)
    throw new Error('erro1')
}).catch(() => { // 返回 resolved 状态的 promise
    console.log(2)
}).catch(() => {
    console.log(3)
})
```

## 常用 API

Promise.all
Promise.race


# 09-升级-JS异步进阶\04-async.md
# async/await

- 语法介绍
- 和 Promise 的关系
- 异步本质
- for...of

**有很多 async 的面试题，例如** （这些题目也可以补充到第一节中！！！）
- async 直接返回，是什么
- async 直接返回 promise
- await 后面不加 promise
- 等等，需要找出一个规律

## 语法介绍

用同步的方式，编写异步。

```js
function loadImg(src) {
    const promise = new Promise((resolve, reject) => {
        const img = document.createElement('img')
        img.onload = () => {
            resolve(img)
        }
        img.onerror = () => {
            reject(new Error(`图片加载失败 ${src}`))
        }
        img.src = src
    })
    return promise
}

async function loadImg1() {
    const src1 = 'http://www.imooc.com/static/img/index/logo_new.png'
    const img1 = await loadImg(src1)
    return img1
}

async function loadImg2() {
    const src2 = 'https://avatars3.githubusercontent.com/u/9583120'
    const img2 = await loadImg(src2)
    return img2
}

(async function () {
    // 注意：await 必须放在 async 函数中，否则会报错
    try {
        // 加载第一张图片
        const img1 = await loadImg1()
        console.log(img1)
        // 加载第二张图片
        const img2 = await loadImg2()
        console.log(img2)
    } catch (ex) {
        console.error(ex)
    }
})()
```

## 和 Promise 的关系

- async 函数返回结果都是 Promise 对象（如果函数内没返回 Promise ，则自动封装一下）

```js
async function fn2() {
    return new Promise(() => {})
}
console.log( fn2() )

async function fn1() {
    return 100
}
console.log( fn1() ) // 相当于 Promise.resolve(100)
```

- await 后面跟 Promise 对象：会阻断后续代码，等待状态变为 resolved ，才获取结果并继续执行
- await 后续跟非 Promise 对象：会直接返回

```js
(async function () {
    const p1 = new Promise(() => {})
    await p1
    console.log('p1') // 不会执行
})()

(async function () {
    const p2 = Promise.resolve(100)
    const res = await p2
    console.log(res) // 100
})()

(async function () {
    const res = await 100
    console.log(res) // 100
})()

(async function () {
    const p3 = Promise.reject('some err')
    const res = await p3
    console.log(res) // 不会执行
})()
```

- try...catch 捕获 rejected 状态

```js
(async function () {
    const p4 = Promise.reject('some err')
    try {
        const res = await p4
        console.log(res)
    } catch (ex) {
        console.error(ex)
    }
})()
```

总结来看：

- async 封装 Promise
- await 处理 Promise 成功
- try...catch 处理 Promise 失败

## 异步本质

await 是同步写法，但本质还是异步调用。

```js
async function async1 () {
  console.log('async1 start')
  await async2()
  console.log('async1 end') // 关键在这一步，它相当于放在 callback 中，最后执行
}

async function async2 () {
  console.log('async2')
}

console.log('script start')
async1()
console.log('script end')
```

即，只要遇到了 `await` ，后面的代码都相当于放在 callback 里。

## for...of

```js
// 定时算乘法
function multi(num) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(num * num)
        }, 1000)
    })
}

// // 使用 forEach ，是 1s 之后打印出所有结果，即 3 个值是一起被计算出来的
// function test1 () {
//     const nums = [1, 2, 3];
//     nums.forEach(async x => {
//         const res = await multi(x);
//         console.log(res);
//     })
// }
// test1();

// 使用 for...of ，可以让计算挨个串行执行
async function test2 () {
    const nums = [1, 2, 3];
    for (let x of nums) {
        // 在 for...of 循环体的内部，遇到 await 会挨个串行计算
        const res = await multi(x)
        console.log(res)
    }
}
test2()
```


# 09-升级-JS异步进阶\05-微任务和宏任务.md
# 宏任务和微任务

## 介绍

- 宏任务：setTimeout setInterval DOM 事件
- 微任务：Promise（对于前端来说）
- 微任务比宏任务执行的更早

```js
console.log(100)
setTimeout(() => {
    console.log(200)
})
Promise.resolve().then(() => {
    console.log(300)
})
console.log(400)
// 100 400 300 200
```

## event loop 和 DOM 渲染

再次回顾 event loop 的过程

- 每一次 call stack 结束，都会触发 DOM 渲染（不一定非得渲染，就是给一次 DOM 渲染的机会！！！）
- 然后再进行 event loop

```js
const $p1 = $('<p>一段文字</p>')
const $p2 = $('<p>一段文字</p>')
const $p3 = $('<p>一段文字</p>')
$('#container')
            .append($p1)
            .append($p2)
            .append($p3)

console.log('length',  $('#container').children().length )
alert('本次 call stack 结束，DOM 结构已更新，但尚未触发渲染')
// （alert 会阻断 js 执行，也会阻断 DOM 渲染，便于查看效果）
// 到此，即本次 call stack 结束后（同步任务都执行完了），浏览器会自动触发渲染，不用代码干预

// 另外，按照 event loop 触发 DOM 渲染时机，setTimeout 时 alert ，就能看到 DOM 渲染后的结果了
setTimeout(function () {
    alert('setTimeout 是在下一次 Call Stack ，就能看到 DOM 渲染出来的结果了')
})
```

## 宏任务和微任务的区别

- 宏任务：DOM 渲染后再触发
- 微任务：DOM 渲染前会触发

```js
// 修改 DOM
const $p1 = $('<p>一段文字</p>')
const $p2 = $('<p>一段文字</p>')
const $p3 = $('<p>一段文字</p>')
$('#container')
    .append($p1)
    .append($p2)
    .append($p3)

// // 微任务：渲染之前执行（DOM 结构已更新）
// Promise.resolve().then(() => {
//     const length = $('#container').children().length
//     alert(`micro task ${length}`)
// })

// 宏任务：渲染之后执行（DOM 结构已更新）
setTimeout(() => {
    const length = $('#container').children().length
    alert(`macro task ${length}`)
})
```

再深入思考一下：为何两者会有以上区别，一个在渲染前，一个在渲染后？—— 刨根问底！

- 微任务：ES 语法标准之内，JS 引擎来统一处理。即，不用浏览器有任何关于，即可一次性处理完，更快更及时。
- 宏任务：ES 语法没有，JS 引擎不处理，浏览器（或 nodejs）干预处理。


# 09-升级-JS异步进阶\06-问题解答.md
# 问题解答

- 描述 event loop 运行机制（可画图）
- 场景题：Promise catch 连接 then
- 场景题：Promise 和 setTimeout 顺序
- 场景题：各类异步执行顺序问题
- 宏任务和微任务的区别

回顾知识点：

- event loop
- Promise
- async/await
- 微任务和宏任务


# 10-升级-面试准备\01-开始.md
# 面试准备

引导语：先来看看技术之外的事情，关于面试的了解和准备。非常重要！！！

- 前端面试的环节和流程
- JD 分析
- 如何写简历
- 面试前的准备工作和注意事项

------

校招和社招，分开讲


# 10-升级-面试准备\02-前端面试的环节和流程.md
# 前端面试的环节和流程

## 什么是面试

面试是测查和评价人员能力素质的一种考试活动。
具体地说，面试是一种经过组织者**精心设计**，在特定场景下，以考官对考生的面对面交谈与观察为主要手段，由表及里测评考生的**知识、能力、经验**等有关素质的一种考试活动。

## 简历筛选

- 员工内推
- 猎头推荐
- hr 收集（主动查找，接收邮件）

哪种方式最早拿到候选人的联系方式（或简历），那就属于哪个渠道。

## 面试环节

社招和校招，需要的技术能力不一样

- 一面
- 二面（其中可能会有若干轮**交叉面试**）
- 三面
- hr

## 课程需要做的

帮你通过简历筛选，帮你通过一面或者二面的基础知识考察。

剩余的历程，可以参考其他课程。


# 10-升级-面试准备\03-JD分析.md
# JD 分析

## JD 是什么

JD 即用人单位发布的职位职责描述。主题内容包括：职位描述，岗位要求

从 JD 我们能找到

- 工作内容。如做 PC 还是做移动端，有些还涉及微信开发，或者地图开发等
- 技术栈。如 Vue 还是 React
- 经验要求。如要求 3-5 年（从薪资也能看出来）

但要注意

- JD 是 hr 发布的
- 不规范的公司，JD 也“不靠谱”
- 因此，也不用太刻意的在乎 JD ，大胆的去面试就行

## 案例分析

从拉勾网上找个两个职位，作为案例分析。

- 小牛电动车 https://www.lagou.com/jobs/6988295.html
- 樊登小读者 https://www.lagou.com/jobs/6060415.html


# 10-升级-面试准备\04-如何写简历.md
# 如何写简历

## 简历是什么

简历，就像高考作文，阅卷时间非常短。因此，简历要争取在**最短时间**内表达出你的优势。

PS：有同学可能说“我觉得自己没有优势啊” —— 你会的，就是你的优势，就会有人需要。

## 简历包含的内容

- 基本信息
    - 姓名，性别，电话，邮箱
    - 年龄可以不写，从你的教育经历可以预估出来
    - 头像无所谓（但漂亮女生会受欢迎，因为程序猿男生居多，招个美女有助于活跃团队气氛）
- 学历，英语，或者其他培训
    - 写最高学历，隐藏不具有竞争力的学历
    - 写上哪年入学哪年毕业，还有专业
- 专业技能
    - 表现自己的核心技能，核心技术栈，别太琐碎
- 工作经历
    - 如实写即可
- 项目经历
    - 写 2-4 个最具表现力的项目即可（根据工作年限）
    - 不用写太多
- 博客或者开源
    - 没多少内容就别写了

## 注意事项

- 页面不要太花哨，简洁明了
- 专业技能写的太琐碎，且不条理。恨不得把自己会的都写上
- 注意用词，“精通” “熟练” 慎用（程序猿都是很严谨的）
- 项目经历要写清楚自己的角色和贡献
- 开源和博客要保证有内容
- 能力不能造假！！！—— 但经历可以变化，例如写一个其他人做过的项目，但你也同样能 hold 住

## 案例分析

注意屏蔽掉用户信息

## 简历如何投递

- 海投
- 猎头
- 内推


# 10-升级-面试准备\05-注意事项.md
# 注意事项

## 准备工作

- 看 JD ，有不会的内容临时查一查
- 打印纸质简历，带着纸和笔
- 最好带着自己的电脑，现场写代码还是用自己的电脑舒服

## 面试中的注意事项

面试要有时间观念，不要迟到。（程序员这个职业就很在乎时间观念，不喜欢拖沓的人）

衣着要适当，尽量是常规的休闲装。

为何离职？不要抱怨或者吐槽前公司，多从自己的角度找原因，例如自己想要更好的发展平台

能加班吗？—— 看你自己情况，有些公司就是加班，你能否适应？如实回答即可

不要挑战面试官，即便是他错了。搞清楚你此行的目的。

遇到不会的问题，表现的积极正面。如让面试官给一个提示，或者给指点一下，表现的自己想要去弄懂这个问题。而不是说不懂，就完事儿了。

## 其他

可以再看看我写的手记《面试中需要避免的几个情况》https://www.imooc.com/article/300475


# 11-升级-CSS面试题\01-开始.md
# CSS 面试题

参考之前的 CSS 面试题，包括文档，代码，视频

## 需要改动

增加 vw/vh

修改课程的思维导图


# 12-升级-http面试题\00-开始.md
# http 面试题

前端主要写页面，光有页面系统是不能运行的，还需要数据。数据的增删改查，都要和后端进行交互，即调用后端接口。而这就需要 http 协议。

但是在学习本章内容之前，你一定要保证自己已经熟练使用 ajax 了！！！
否则学习将遇到障碍。

（画图，解释 http 过程）


# 12-升级-http面试题\01-题目.md
# 题目

- http 常见的状态码有哪些
- http 常见的 header 有哪些
- 什么是 Restful API
- 请描述 http 缓存机制
- https 如何加密数据 —— 先待定！！！


# 12-升级-http面试题\02-http状态码.md
# http 状态码

注意，无论是状态码规范，还是整个 http 协议规范，都是前后端的一个**约定**，需要大家都来遵守。
所谓约定或者规范，不是强制的，你可以不遵守。
但是如果大家都遵守，你特立独行，就会慢慢的被孤立。就像早期的 IE 浏览器。

所以，无论是这里的 http 协议，还是开发中其他的事情。我们都要尽量去遵守业界的规范，参照业界的标准 —— **当然，前提是你得知道有哪些规范（知识体系的范围）**

## 状态码分类

- 1xx 服务器收到请求
- 2xx 成功
- 3xx 重定向
- 4xx 客户端错误
- 5xx 服务器错误

## 常见状态码

http 协议中的状态码有很多，但只有一些是我们常用的。也是面试常考的。

- 200 成功
- 301 永久重定向（同时返回一个 location ，写明重定向的 url）。例如一个网站的网址永久性的切换了
- 302 临时重定向（同时返回一个 location ，写明重定向的 url）。例如短链跳转
- 304 资源未修改过
- 404 未找到资源
- 403 没有权限，例如需要登录之后才能请求
- 500 服务器内部错误，例如服务器代码异常
- 504 网关超时，例如上游服务器连接失败（服务器不是一台机器，可能会有很多台）

## 仅仅是一个规定

再次强调一下，这些状态码仅仅是一个规定。所以前端后端，都要自觉遵守这个规定。


# 12-升级-http面试题\03-methods.md
# http methods

## 常用 methods

之前，常用的方法就是 get 和 post

- get 从服务端获取数据
- post 向服务端提交数据

现在，随着技术更新，以及 Restful API 设计（下文会讲）。有更多的 methods 被应用

- get 获取数据
- post 新建数据
- patch/put 更新数据
- delete 删除数据

## Restful API

Restful API 是前后端接口的一种设计规范，经历了几年的发展，已经被全面应用。前端面试常考。

- 传统 API 设计：把每个 API 当做一个功能
- Restful API 设计：把每个 API 当做一个资源标识

需要用到的手段

- 不使用 url 参数
- 使用 method 表示操作类型

例如要获取一个列表

- （不使用 url 参数）
- 传统 API 设计：`/api/list?pageIndex=2` —— 一个功能
- Restful API 设计：`/api/list/2` —— 一个资源

再例如要操作一个数据

- 传统 API 设计（每个 API 都是功能）
    - `/api/create-blog` ，post 请求
    - `/api/udpate-blog?id=101`，post 请求
    - `/api/get-blog?id=101`， get 请求
- Restful API 设计（每个 API 都是资源）
    - `/api/blog` ，post 请求
    - `/api/blog/101` ，patch 请求
    - `/api/blog/101` ，get 请求


# 12-升级-http面试题\04-http-headers.md
# http headers

headers 有很多，只讲一下最常用的，也是面试常考的。

## request headers

浏览器发送请求时，传递给服务端的信息

- Accept 浏览器可接收的数据类型
- Accept-Encoding 浏览器可接收的压缩算法，如 gzip
- Accept-Language 浏览器可接收的语言，如 zh-CN
- Connection: keep-alive 一次 TCP 连接重复使用
- cookie
- Host
- User-Agent 浏览器信息
- Content-type 发送数据的类型，常见的有 application/json，application/x-www-form-urlencoded，multipart/form-data，text/plain 等（用 postman 可演示）

## response headers

- Content-Type 返回的数据类型，对应 Accept
- Content-Length 数据大小
- Content-Encoding 压缩算法，如 gzip ，对应 Accept-Encoding
- Set-Cookie

## 示例

看百度首页，html 请求，js 请求，图片请求等

用 postman ，演示 request headers 里的 Content-type

## 自定义 header

有些接口需要前端调用时，加一个自定义的 header 。
如 axios 中自定义 headers http://www.axios-js.com/docs/#Request-Config

## 其他

关于缓存的 header ，后面会统一讲

Response headers

- Cache-Control
- Etag
- Expires
- Last-Modified

Request headers

- If-Modified-Since
- If-None-Match

面试时，这些和缓存有关的 header 也可以单独说。不要和其他的混在一起，本来就挺乱的。


# 12-升级-http面试题\05-http缓存.md
# http 缓存

## 什么是缓存

（画图，http 请求过程）

缓存，即某些情况下，资源不是每次都去服务端获取，而是第一次获取之后缓存下来。
下次再请求时，直接读取本地缓存，而不再去服务端请求。

## 为什么需要缓存

核心需求，让网页更快的显示出来，即提高性能。

- 计算机执行计算，非常快
- 包括页面渲染，JS 执行等
- 加载资源却非常慢（相比于计算来说），而且受限于网络不可控。

解决好最关键的问题 —— 缓存网络资源

## 哪些资源需要缓存

对于一个网页来说

- html 页面不能缓存
- 业务数据不能缓存（例如一个博客项目，里面的博客信息）
- 静态资源可以缓存，js css 图片等（所有的静态资源累加起来，体积是很大的）

PS：讲 webpack 时讲过 `contentHash` ，就是给静态资源加上一个唯一的 hash 值，便于缓存。

## 缓存策略 —— 强制缓存，客户端缓存

**Cache-Control** (response headers 中) 表示该资源，被再次请求时的缓存情况。

- `max-age:31536000` 单位是 s ，该资源被强制缓存 1 年
- `no-cache` 不使用强制缓存，但不妨碍使用协商缓存（下文会讲）
- `no-store` 禁用一起缓存，每次都从服务器获取最新的资源
- `private` 私有缓存（浏览器级缓存）
- `public` 共享缓存（代理级缓存）

关于 Expires

- http 1.0 ，设置缓存过期时间的
- 由于本地时间和服务器时间可能不一致，会导致问题
- 已被 Cache-Control 的 max-age 代替

## 缓存策略 —— 协商缓存（对比缓存），服务端缓存

当强制缓存失效，请求会被发送到服务端。此时，服务端也不一定每次都要返回资源，如果客户端资源还有效的话。

第一，**Last-Modified**（Response Headers）和 **If-Modified-Since**（Request Headers）

- Last-Modified 服务端返回资源的最后修改时间
- If-Modified-Since 再次请求时带着最后修改时间
- 服务器根据时间判断资源是否被修改（如未被修改则返回 304，失败则返回新资源和新的缓存规则）

第二，**Etag**（Response Headers）和 **If-None-Match**（Request Headers）

- Etag 服务端返回的资源唯一标识（类似人的指纹，唯一，生成规则由服务器端决定，结果就是一个字符串）
- If-None-Match 再次请求时带着这个标识
- 服务端根据资源和这个标识是否 match （成功则返回 304，失败则返回新资源和新的缓存规则）

如果两者一起使用，则**优先使用 Etag** 规则。因为 Last-Modified 只能精确到秒级别。

## 缓存策略 - 综述

画图，参考视频

## 刷新操作对应不同的缓存策略

三种操作

- 正常操作：地址栏输入 url ，点击链接，前进后退等
- 手动刷新：F5 或者点击刷新按钮
- 强制刷新：ctrl + F5

对应的缓存策略

- 正常操作：强制缓存有效，协商缓存有效
- 手动刷新：强制缓存*失效*，协商缓存有效
- 强制刷新，强制缓存*失效*，协商缓存*失效*

## 小结

关于 http 缓存的重点

- 强缓存和协商缓存
- 几个 http headers
- 流程图


# 12-升级-http面试题\06-https.md
# https

http 是明文传输，传输的所有内容（如登录的用户名和密码），都会被中间的代理商（无论合法还是非法）获取到。

http + TLS/SSL = https ，即加密传输信息。只有客户端和服务端可以解密为明文，中间的过程无法解密。

## 关于信息加密

### 对称加密

一个密钥，既负责加密，又符合揭秘

- 浏览器访问服务端，服务端生成密钥，并传递给浏览器
- 浏览器和服务端，通过这个密钥来加密、解密信息

但这有一个很严重的问题：密钥也会被劫持

### 非对称加密

生成一对密钥，一个公钥，一个私钥。
- 公钥加密的信息，只有私钥能解密
- 私钥加密的信息，只有公钥能解密

- 浏览器访问服务端，服务端生成公钥、私钥，并把公钥传递给浏览器
- 浏览器生成一个 key（随机字符串），并用公钥加密，传递给服务端
- 服务端用私钥解密 key 。这样浏览器和服务端，就都得到了 key ，而且 key 还是加密传输的
- 然后，浏览器和服务端使用 key 为密钥，做对称加密传输

思考：如果公钥和 key 被劫持，黑客能解密 key 吗？—— 不能，因为解密 key 要使用私钥，而私钥一只在服务端，没有传输。

### 证书

公钥劫持了不行，那替换行不行呢？<br>
黑客直接劫持请求，替换为自己的公钥（当然他自己有私钥），你的所有请求他劫持到，就都可以解密了。<br>
这叫做“中间人攻击”

这个问题，不好从技术上规避，那就从标准规范上解决 —— CA 证书。
- 由正规的第三方结构，颁发证书（如去阿里云申请，但要花钱）
- 证书包括：公钥，域名，申请人信息，过期时间等 —— 这些都是绑定的
- 浏览器识别到正规的证书，才使用。否则会交给用户确认。

这样，当黑客使用中间人攻击时，浏览器就会识别到它的证书不合规范，就会提示用户。

所以，尽量使用正规渠道申请的证书，花点钱，保证安全和稳定性。

## https 加密原理

图示

# 12-升级-http面试题\07-问题解答和总结.md
# 问题解答 & 总结

- http 常见的状态码有哪些
- http 常见的 header 有哪些
- 什么是 Restful API
- 请描述 http 缓存机制


# x1-教学互动\练习环节\01-项目任务.md
# 项目任务

> 浅层学习看输入，深度学习看输出

## 第2章 面试前的准备

**【任务】写一个自己的简历**

试着写一下自己当前的简历，无论你是否正在打算找工作。

写简历可以让你总结、复盘当前自己的技术水平，看看自己有多少能拿的出手的技能和项目经验。
如果感觉目前还有不足，可即使学习补充，下次面试就能用得上。

## 第3章 CSS 面试题

**【任务】总结 CSS 面试题**

写一篇博客，总结本章的学习成果，记录常见的 CSS 面试题。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第4章 JS基础-变量类型和计算

**【任务】默写 JS 深拷贝**

学完本章之后，不参考任何资料，默写 JS 深拷贝。

以博客形式输出，即写一篇博客记录 JS 深拷贝的实现过程，和代码解读。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第5章 JS基础-原型和原型链

**【任务】画图解释原型链**

学完本章之后，不参考任何资料，自己画一个原型链的图示，并配合代码。

以博客形式输出，即写一篇博客讲解图和代码。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第6章 JS基础-作用域和闭包

**【任务】总结闭包的使用场景**

写一篇博客，总结闭包的使用场景，并写 demo 解释。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第7章 JS基础-异步

**【任务】初识 Promise**

如果你是 JS 新手，可写一篇博客来记录你对 Promise 的任务。如果你对 Promise 比较熟悉，可忽略。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第8章 JS 异步进阶

**【任务】画图解释 event loop**

学完本章，自己画图（不要截课程的图）解释 event loop 过程。

以博客形式输出，即写一篇博客解释 event loop 的过程，结合你画的图。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

**【任务】总结宏任务和微任务**

写一篇博客，总结宏任务和微任务，作为学习笔记。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第9章 JS-Web-API-DOM

暂无（内容少，而且很简单）

## 第10章 JS-Web-API-BOM

暂无（内容少，而且很简单）

## 第11章 JS-Web-API-事件

暂无（内容少，而且很简单）

## 第12章 JS-Web-API-Ajax

**【任务】介绍跨域请求**

写一篇博客，介绍跨域请求的前生今世，包括浏览器同源策略，和跨域的实现方式。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第13章 JS-Web-API-存储

暂无（内容少，而且很简单）

## 第14章 http 面试题

**【任务】总结 http 缓存策略**

写一篇博客，总结你对 http 缓存策略的学习成果，作为学习笔记。尽量详细写，图文并茂的解释清楚。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第15章 开发环境

**【任务】总结 linux 常用命令**

写一篇博客，总结 linux 常用命令，作为学习笔记。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第16章 运行环境

**【任务】手写 debounce 和 throttle**

学完本章之后，自己默写 debounce 和 throttle ，不要照抄。

以博客形似输出，即写一篇博客，分析 debounce 和 throttle 的源码和使用。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第17章 课程总结

无

## 第18章 真题模拟

无


# x1-教学互动\练习环节\02-互动话题.md
# 互动话题

## 第2章 面试前的准备

【话题】你都通过什么方式投递简历？

## 第3章 CSS 面试题

【话题】你在面试时，都遇到过哪些 CSS 面试题？

## 第4章 JS基础-变量类型和计算

【话题】你在日常工作中，遇到过哪些 js 变量类型的坑？

## 第5章 JS基础-原型和原型链

【话题】你的日常工作中，有哪些场景用到了 class 继承？

## 第6章 JS基础-作用域和闭包

【话题】你的日常工作中，会用到闭包吗？

## 第7章 JS基础-异步

【话题】你在面试时，都遇到过哪些 js 异步面试题？

## 第8章 JS 异步进阶

【话题】你的日常工作中，是否全面使用 async/await 写异步代码？

## 第9章 JS-Web-API-DOM

【话题】你的日常工作中，是否会本能的考虑 DOM 操作的优化？

## 第10章 JS-Web-API-BOM

暂无（内容少，而且很简单）

## 第11章 JS-Web-API-事件

【话题】你的日常工作中，是否会本能的考虑事件代理，来做性能优化？

## 第12章 JS-Web-API-Ajax

【话题】你的日常工作中，用什么方式实现跨域？

## 第13章 JS-Web-API-存储

暂无（内容少，而且很简单）

## 第14章 http 面试题

【话题】你的日常工作中，是否用 Restful API ？

## 第15章 开发环境

【话题】你的日常工作中，用什么代码管理服务（github，gitlab 等）？

## 第16章 运行环境

【话题】你的日常工作中，都用到了哪些性能优化？

## 第17章 课程总结

无

## 第18章 真题模拟

【话题】你之前面试时，还遇到过哪些没答出来的面试？


# x2-学习过程\后续学习建议.md
# 后续学习建议

课程中也讲过，我们要有体系化的学习思维。后续学习可以参考双越老师亲手制作的 Web 前端知识体系 https://what-is-fe.gitee.io/ ，通过这个知识体系，可以纵观 Web 前端开发的全貌。

知识体系包括：
- 数学英语等基础科目
- 计算机基础
- 数据结构、算法
- 编程模式和设计模式
- html css
- ES 语法
- JS Web API
- 网络
- 研发流程
- 工程化、CI/CD
- 运行和监控
- 前端框架
- ……

还有很多，大家可以亲自去看。

看过之后，你也可以试着自己去总结一份前端知识体系。自己写出来的，才真正是自己的。


# x2-学习过程\扩展学习.md
# 扩展学习

学完前端基础知识，接下来最重要的就是学习前端框架。

对于面试来说，就是框架和项目的知识点和面试题，这里推荐双越老师录制的课程《[前端框架及项目面试－聚焦Vue3/React/Webpack](https://coding.imooc.com/class/419.html)》。

如果想单独了解框架，可以直接去官网网站：
- Vue https://cn.vuejs.org/
- React https://react.docschina.org/
- webpack https://webpack.docschina.org/

对于 3 年工作经验以上的同学，你还需要开始关注学习设计模式，推荐双越老师录制的《[Javascript 设计模式系统讲解与应用](https://coding.imooc.com/class/255.html)》


# x2-学习过程\课前必读.md
# 课前必读

本课程是初级课程，但不是 0 基础入门课程，学习本课程之前需要掌握：
- 了解 javascript 和 ES6 基本语法
- 了解 html 和 css 基础语法
- 有自我查询知识的能力，有获取知识的欲望

其中技术相关的内容，大家可以去慕课网的[慕课教程](http://www.imooc.com/wiki/)里学习，里面包含了前端开发常用的技术和知识。

如遇到问题可以通过网络搜索引擎就行查找，也可以通过提问网站进行提问。当然课程的学员也可以直接像讲师提问。

另外，我们这是一门针对面试的课程，会讲到一些面试技巧和简历的写法。这部分虽然不是技术内容，但对于我们找工作来说非常有帮助，希望大家学以致用。

预祝各位学习愉快，收获满满～


# x2-学习过程\01-面试介绍\章介绍.md
# 章介绍

本章会出几个面试题，分析每道题目设计的知识点，然后总结出一个完整的知识体系。让我们开始 “题目->知识点->解题” 的快乐之旅吧。

## 本章产出

- 学习体系化的思维方式
- 学习如何搞定所有面试题
- 画出前端基础知识的思维导图

## 主要内容

- 看了这节课你就知道该怎么准备面试了
- 先来体验几个面试题
- 如何搞定所有面试题
- 前端知识体系图

## 关键词

- 体系化
- 知识体系

## 学习方法

- 逐渐培养体系化的思维方式

## 注意事项

- 课程刚开始，看不懂的题目不要着急


# x2-学习过程\01-面试介绍\章回顾.md
# 章回顾

## 本章产出

- 学习体系化的思维方式
- 学习如何搞定所有面试题
- 画出前端基础知识的思维导图

## 主要内容

- 看了这节课你就知道该怎么准备面试了
- 先来体验几个面试题
- 如何搞定所有面试题
- 前端知识体系图

## 知识点

本章没有讲到技术的知识，所以暂无知识点。

## 注意事项

- 课程刚开始，看不懂的题目不要着急


# x2-学习过程\02-面试前的准备\章介绍.md
# 章介绍

本章介绍面试之前你需要准备什么，以及如何解读 JD ，如何写好简历，还有些面试的注意事项。帮大家规避一些非技术的风险和问题。

## 本章产出

- 学会解读 JD
- 学会正确的简历格式
- 学会正确投递简历的方式

## 主要内容

- 面试之前你需要准备什么？
- 投递简历的几种方式
- 面试的主要环节
- JD分析-知己知彼（上）
- JD分析-知己知彼（下）
- 如何写简历
- 简历案例分析
- 面试前的准备工作和注意事项

## 关键词

- 面试
- 简历
- JD
- 猎头
- hr

## 学习方法

- 学以致用，学完就试着写一份自己的简历，无论找不找工作

## 注意事项

- 虽然不是讲技术，但这些比技术更重要


# x2-学习过程\02-面试前的准备\章回顾.md
# 章回顾

## 本章产出

- 学会解读 JD
- 学会正确的简历格式
- 学会正确投递简历的方式

## 主要内容

- 面试之前你需要准备什么？
- 投递简历的几种方式
- 面试的主要环节
- JD分析-知己知彼（上）
- JD分析-知己知彼（下）
- 如何写简历
- 简历案例分析
- 面试前的准备工作和注意事项

## 知识点

本章没有讲技术，暂无知识点

## 注意事项

- 虽然不是讲技术，但这些比技术更重要


# x2-学习过程\03-CSS面试题\章介绍.md
# 章介绍

本章讲解 CSS 中常考和必考的知识点，包括布局、定位、响应式等。其中会讲到很多常考问题，如 BFC、居中对齐、flex 布局等。前端一面中，CSS 一般最先考察，不过关则直接宣告失败。

## 产出

- 学会 HTML CSS 常见的考点和面试题

## 主要内容

- HTML 考点和面试题
- CSS 考点和面试题
    - 布局
    - 定位
    - 图文样式
    - 响应式

## 关键词

- HTML
- CSS

## 学习方法

- 边学边练，课程示例都亲自写一遍
- 记录学习笔记

## 注意事项

暂无


# x2-学习过程\03-CSS面试题\章回顾.md
# 章回顾

## 产出

- 学会 HTML CSS 常见的考点和面试题

## 主要内容

- HTML 考点和面试题
- CSS 考点和面试题
    - 布局
    - 定位
    - 图文样式
    - 响应式


## 知识点

- 盒模型
- BFC
- float
- flex
- position
- line-height
- rem
- media query
- vw/wh


# x2-学习过程\04-JS变量类型和计算\章介绍.md
# 章介绍

本章介绍变量的类型和计算的知识点和题目，包括值类型和引用类型区别，类型判断，深拷贝等。变量和类型是一个任何一门语言的基础，不了解的话，会被认为是 JS 语法不过关。

## 产出

- 认识值类型和引用类型
- 学会深拷贝

## 主要内容

- JS 值类型和引用类型的区别
- 手写 JS 深拷贝
- 变量计算 - 注意某些类型转换的坑
- 变量类型相关的面试题

## 关键字

- 值类型
- 引用类型
- 深拷贝
- 类型转换

## 学习方法

- 深拷贝，要亲自手写一遍，熟练掌握递归

## 注意事项

- 注意类型转换的坑


# x2-学习过程\04-JS变量类型和计算\章回顾.md
# 章回顾

## 产出

- 认识值类型和引用类型
- 学会深拷贝

## 主要内容

- JS 值类型和引用类型的区别
- 手写 JS 深拷贝
- 变量计算 - 注意某些类型转换的坑
- 变量类型相关的面试题

## 知识点

- 值类型
- 引用类型
- 类型判断
- 类型转换
- 深拷贝

## 注意事项

- 注意类型转换的坑


# x2-学习过程\05-JS原型和原型链\章介绍.md
# 章介绍

本章介绍原型、原型链和 class 相关的知识点和题目。包括 class ，继承，原型，原型链，instanceof。原型是“JS 三座大山”之一，原型和原型链也是必考知识点。

## 产出

- 学会原型和原型链
- 学会 class 和继承

## 主要内容

- JS 原型的考点和面试题
- 如何用 class 实现继承
- 如何理解 JS 原型（隐式原型和显示原型）
- instanceof 是基于原型链实现的
- JS 原型本章相关的面试题

## 关键词

- 原型
- 原型链
- instanceof
- class
- 继承

## 学习方法

- 原型链图，自己要亲自画一遍

## 注意事项

- 如今 ES6 已经普及，用 class 继承即可，不用再关注其他继承方式


# x2-学习过程\05-JS原型和原型链\章回顾.md
# 章回顾

## 产出

- 学会原型和原型链
- 学会 class 和继承

## 主要内容

- JS 原型的考点和面试题
- 如何用 class 实现继承
- 如何理解 JS 原型（隐式原型和显示原型）
- instanceof 是基于原型链实现的
- JS 原型本章相关的面试题

## 知识点

- class
- 继承
- 原型
- 原型链
- instanceof

## 注意事项

- 如今 ES6 已经普及，用 class 继承即可，不用再关注其他继承方式


# x2-学习过程\06-JS作用域和闭包\章介绍.md
# 章介绍

本章介绍作用域和闭包的知识点和题目。包括作用域，自由变量，闭包，this 等部分。作用域是“JS 三座大山”之二，不知道闭包的话，面试通过概率不大。

## 产出

- 学会作用域和闭包
- 学会 this 的所有用法

## 主要内容

- 什么是作用域？什么是自由变量？ 
- 什么是闭包？闭包会用在哪里？
- this 有几种赋值情况 
- 作用域相关的面试题

## 关键字

- 作用域
- 闭包
- this

## 学习方法

- 把课程示例都亲自手写一遍

## 注意事项

- 闭包，不要纠结于概念，要多注意它的使用场景


# x2-学习过程\06-JS作用域和闭包\章回顾.md
# 章回顾

## 产出

- 学会作用域和闭包
- 学会 this 的所有用法

## 主要内容

- 什么是作用域？什么是自由变量？ 
- 什么是闭包？闭包会用在哪里？
- this 有几种赋值情况 
- 作用域相关的面试题

## 知识点

- 作用域
- 闭包
- 自由变量
- this

## 注意事项

- 闭包，不要纠结于概念，要多注意它的使用场景

# x2-学习过程\07-异步基础\章介绍.md
# 章介绍

本章介绍异步的知识点和题目。包括异步和同步的区别，异步应用场景，以及 Promise 。异步是“JS 三座大山”之三，所有公司的 JS 面试，100% 会考察异步和 Promise 。

## 产出

- 知道什么是异步，和同步的区别
- 异步的应用场景
- Promise 的基本使用

## 主要内容

- 同步和异步有何不同
- 异步的应用场景有哪些
- Promise的基本使用
- JS 异步相关的面试题
- JS基础部分的考点总结

## 关键字

- 同步
- 异步
- Promise

## 学习方法

- 课程示例要亲自练习一遍

## 注意事项

- 本章只是“异步基础”，后面还有“异步进阶”内容


# x2-学习过程\07-异步基础\章回顾.md
# 章回顾

## 产出

- 知道什么是异步，和同步的区别
- 异步的应用场景
- Promise 的基本使用

## 主要内容

- 同步和异步有何不同
- 异步的应用场景有哪些
- Promise的基本使用
- JS 异步相关的面试题
- JS基础部分的考点总结

## 知识点

- 单线程
- callback
- Promise

## 注意事项

- 本章只是“异步基础”，后面还有“异步进阶”内容

# x2-学习过程\08-异步进阶\章介绍.md
# 章介绍

JS 的特色就是异步编程，所有有很多关于异步的考点，本章都会讲解。如 event loop、promise、async-await、微任务和宏任务。学不会这些，就不算是精通 JS ，也无法进大厂。

## 产出

- 全面使用 Promise
- 学会 async await 语法
- 学会 event loop 流程
- 认识微任务和宏任务

## 主要内容

- event loop 执行过程
- Promise 全面使用
- async await 全面使用
- 微任务和宏任务
- 面试题讲解

## 关键字

- Promise
- async await
- event loop
- 微任务和宏任务

## 学习方法

- event loop 图示，自己亲自画一遍
- 课程示例自己亲自写一遍

## 注意事项

- event loop 用最简单的 demo 能理解即可，不要用它来解释过于复杂的代码，自己会蒙的


# x2-学习过程\08-异步进阶\章回顾.md
# 章回顾

## 产出

- 全面使用 Promise
- 学会 async await 语法
- 学会 event loop 流程
- 认识微任务和宏任务

## 主要内容

- event loop 执行过程
- Promise 全面使用
- async await 全面使用
- 微任务和宏任务
- 面试题讲解

## 知识点

- Promise
- async await
- event loop
- for ... of
- 微任务和宏任务

## 注意事项

- event loop 用最简单的 demo 能理解即可，不要用它来解释过于复杂的代码，自己会蒙的

# x2-学习过程\09-JS-Web-API-DOM\章介绍.md
# 章介绍

本章介绍 DOM 操作的知识点和题目。包括 DOM 结构，常用 DOM 操作，DOM 性能优化等。DOM 是网页结构的基础，学会 DOM 操作才可以做网页开发。

## 产出

- 学会常见 DOM 操作

## 主要内容

- 从JS基础到JS-Web-API
- DOM的本质是什么
- DOM节点操作
- DOM结构操作
- 如何优化 DOM 操作的性能
- DOM 操作相关的面试题

## 关键字

- DOM
- 节点
- DOM 树

## 学习方法

- 课程示例，要亲自练习

## 注意事项

- DOM 操作非常耗费性能，要注意性能优化


# x2-学习过程\09-JS-Web-API-DOM\章回顾.md
# 章回顾

## 产出

- 学会常见 DOM 操作

## 主要内容

- 从JS基础到JS-Web-API
- DOM的本质是什么
- DOM节点操作
- DOM结构操作
- 如何优化 DOM 操作的性能
- DOM 操作相关的面试题

## 知识点

- DOM 树
- DOM 节点操作
- DOM 属性
- DOM 性能

## 注意事项

- DOM 操作非常耗费性能，要注意性能优化


# x2-学习过程\10-JS-Web-API-BOM\章介绍.md
# 章介绍

本章介绍 BOM 操作的知识点和题目。本章内容虽然不多，但不可不会。

## 产出

- 基础的 BOM 操作

## 内容

- BOM 操作相关的面试题 

## 关键字

- BOM

## 学习方法

- 课程示例要亲自练习

## 注意事项

暂无

# x2-学习过程\10-JS-Web-API-BOM\章回顾.md
# 章回顾

## 产出

- 基础的 BOM 操作

## 内容

- BOM 操作相关的面试题 

## 知识点

- navigator
- screen
- location
- history


# x2-学习过程\11-JS-Web-API-事件\章介绍.md
# 章介绍

本章介绍事件绑定的知识点和题目。包括事件绑定，事件冒泡机制，事件代理。事件能让网页和鼠标、键盘进行交互，初级 JS 面试必考。

## 产出

- DOM 事件相关知识

## 主要内容

- 事件绑定和事件冒泡
- 什么是事件代理（面试必考）
- DOM 事件相关的面试题

## 关键字

- DOM 事件
- 事件冒泡
- 事件代理

## 学习方法

- 课程示例，要亲自练习

## 注意事项

- 暂无


# x2-学习过程\11-JS-Web-API-事件\章回顾.md
# 章回顾

## 产出

- DOM 事件相关知识

## 主要内容

- 事件绑定和事件冒泡
- 什么是事件代理（面试必考）
- DOM 事件相关的面试题

## 知识点

- 事件绑定
- 事件冒泡
- 事件代理


# x2-学习过程\12-JS-Web-API-Ajax\章介绍.md
# 章介绍

本章介绍 ajax 相关的知识点和题目。包括 XMLHttpRequest ，同源策略，跨域方式，以及常用插件介绍。我们早就进入了动态网页时代，而当下的前后端分离开发方式，更加要求每个工程师必须熟练掌握 ajax 。

## 产出

- 学会 ajax 使用
- 学会跨域解决方法

## 主要内容

- ajax 的核心API - XMLHttpRequest
- 什么是浏览器的同源策略
- 实现跨域的常见方式 - jsonp 和 CORS
- ajax 相关的面试题
- 实际项目中 ajax 的常用插件

## 关键字

- ajax
- 同源策略
- 跨域

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 跨域要前后端结合练习，只有前端实现不了跨域


# x2-学习过程\12-JS-Web-API-Ajax\章回顾.md
# 章回顾

## 产出

- 学会 ajax 使用
- 学会跨域解决方法

## 主要内容

- ajax 的核心API - XMLHttpRequest
- 什么是浏览器的同源策略
- 实现跨域的常见方式 - jsonp 和 CORS
- ajax 相关的面试题
- 实际项目中 ajax 的常用插件

## 知识点

- XMLHttpRequest
- 状态码
- 跨域
- CORS
- JSONP

## 注意事项

- 跨域要前后端结合练习，只有前端实现不了跨域


# x2-学习过程\13-JS-Web-API-存储\章介绍.md
# 章介绍

本章介绍存储的知识点和题目。包括 cookie、localStorage 和 sessionStorage 。本章内容虽然不多，但不可不会。

## 产出

- 学会 cookie
- 学会浏览器本地存储

## 主要内容

- 如何理解 cookie
- localStorage SessionStorage 和 cookie 的区别

## 关键字

- cookie
- localStorage
- sessionStorage

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 注意 cookie 要跟随着 http 请求被发送出去


# x2-学习过程\13-JS-Web-API-存储\章回顾.md
# 章回顾

## 产出

- 学会 cookie
- 学会浏览器本地存储

## 主要内容

- 如何理解 cookie
- localStorage SessionStorage 和 cookie 的区别

## 知识点

- cookie
- localStorage
- sessionStorage

## 注意事项

- 注意 cookie 要跟随着 http 请求被发送出去



# x2-学习过程\14-http\章介绍.md
# 章介绍

前端工程师做出网页，需要通过网络请求向后端获取数据，因此 http 协议是前端面试的必考内容。本章讲解 http 协议常考的知识点，如状态码、header、method、缓存等。特别是 http 缓存策略，非常重要。

## 产出

- 学会 http 基础只是
- 学会 http 缓存机制

## 主要内容

- http的几个面试题
- http常见的状态码有哪些-part1
- http常见的状态码有哪些-part2
- 什么是Restful-API
- http哪些常见header
- http为何需要缓存
- cache-control是什么意思-http强制缓存
- Etag和Last-Modified是什么意思-http协商缓存
- 刷新页面对http缓存的影响
- http考点总结

## 关键词

- http
- Restful-API
- 缓存

## 学习方法

- 记录学习笔记

## 注意事项

- 学习 http 没法像代码演示那样方便的练习，要注意跟随课程示例，理解学习


# x2-学习过程\14-http\章回顾.md
# 章回顾

## 产出

- 学会 http 基础只是
- 学会 http 缓存机制

## 主要内容

- http的几个面试题
- http常见的状态码有哪些-part1
- http常见的状态码有哪些-part2
- 什么是Restful-API
- http哪些常见header
- http为何需要缓存
- cache-control是什么意思-http强制缓存
- Etag和Last-Modified是什么意思-http协商缓存
- 刷新页面对http缓存的影响
- http考点总结

## 知识点

- http 状态码
- http Method
- Restful API
- http headers
- http 缓存策略

## 注意事项

- 学习 http 没法像代码演示那样方便的练习，要注意跟随课程示例，理解学习

# x2-学习过程\15-开发环境\章介绍.md
# 章介绍

本章介绍开发环境相关的知识点和题目。包括 git ，调试工具，抓包工具，webpack 和 babel ，以及 linux 常用命令。熟练使用开发环境的各个工具，才能证明你真的做过前端开发，真的有项目经验，否则只能被认定为菜鸟小白。

## 产出

- 熟悉前端开发环境
- 学习 webpack 的基本配置
- 学习 linux 常用命令

## 内容

- 前端开发常用的开发工具
- 什么是 git
- git 的常用命令有哪些
- git 常用命令演示
- 如何用 chrome 调试 js 代码
- 移动端 h5 如何抓包网络请求
- 如何配置 webpack
- 如何配置 babel
- ES6 模块化规范是什么
- 如何配置 webpack 生产环境
- 前端用到的 linux 常用命令有哪些
- 开发环境的考点总结

## 关键字

- git
- 调试
- 抓包
- webpack
- babel
- ES Module
- linux 命令

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 开发环境非常重要，会影响生产效率，要注意学习掌握


# x2-学习过程\15-开发环境\章回顾.md
# 章回顾

## 产出

- 熟悉前端开发环境
- 学习 webpack 的基本配置
- 学习 linux 常用命令

## 内容

- 前端开发常用的开发工具
- 什么是 git
- git 的常用命令有哪些
- git 常用命令演示
- 如何用 chrome 调试 js 代码
- 移动端 h5 如何抓包网络请求
- 如何配置 webpack
- 如何配置 babel
- ES6 模块化规范是什么
- 如何配置 webpack 生产环境
- 前端用到的 linux 常用命令有哪些
- 开发环境的考点总结

## 知识点

- git
- 调试
- 抓包
- webpack
- babel
- ES Module
- linux 命令

## 注意事项

- 开发环境非常重要，会影响生产效率，要注意学习掌握


# x2-学习过程\16-运行环境\章介绍.md
# 章介绍

本章介绍运行环境相关的知识点和题目。包括浏览器加载和渲染机制，性能优化，web 安全。网页在浏览器加载和运行，这些内容必须掌握，也是面试常考。

## 产出

- 学会网页加载过程
- 学会常见的性能优化
- 学会基本的前端安全预防

## 内容

- JS 上线之后在什么哪里运行？
- 网页是如何加载并渲染出来的
- 网页加载和渲染的示例
- 网页加载和渲染相关的面试题
- 前端性能优化有哪些方式
- 前端性能优化的示例
- 手写防抖 debounce
- 手写节流 throttle
- 如何预防 xss 攻击
- 如何预防 xsrf 攻击
- 运行环境的考点总结

## 关键字

- 渲染
- 性能优化
- 安全

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 运行环境是直接和用户接触的，所以对于产品体验直观重要，要重视起来


# x2-学习过程\16-运行环境\章回顾.md
# 章回顾

## 产出

- 学会网页加载过程
- 学会常见的性能优化
- 学会基本的前端安全预防

## 内容

- JS 上线之后在什么哪里运行？
- 网页是如何加载并渲染出来的
- 网页加载和渲染的示例
- 网页加载和渲染相关的面试题
- 前端性能优化有哪些方式
- 前端性能优化的示例
- 手写防抖 debounce
- 手写节流 throttle
- 如何预防 xss 攻击
- 如何预防 xsrf 攻击
- 运行环境的考点总结

## 知识点

- 页面加载
- 页面渲染
- 资源加载优化
- 渲染优化
- XSS
- XSRF

## 注意事项

- 运行环境是直接和用户接触的，所以对于产品体验直观重要，要重视起来


# x2-学习过程\17-课程总结\章介绍.md
# 章介绍

本章回顾所有题目和知识点，总结课程内容。还会介绍一些实用的面试技巧，避免你在面试中犯一些低级错误。

## 产出

- 课程总结

## 内容

- 课程总结

## 关键字

暂无

## 学习方法

暂无

## 注意事项

暂无


# x2-学习过程\17-课程总结\章回顾.md
# 章回顾

## 产出

- 课程总结

## 内容

- 课程总结

## 知识点

暂无

## 注意事项

暂无


# x2-学习过程\18-真题模拟\章介绍.md
# 章介绍

本章节，通过一部分高频面试真题，带大家分析面试，以及如何解答。

## 产出

- 讲解一些面试真题

## 内容

- 讲解一些面试真题（会不定期更新）

## 关键字

- 面试真题

## 学习方法

- 通过题目，看到它背后的知识点

## 注意事项

暂无


# x2-学习过程\18-真题模拟\章回顾.md
# 章回顾

## 产出

- 讲解一些面试真题

## 内容

- 讲解一些面试真题（会不定期更新）

## 知识点

暂无

## 注意事项

暂无

