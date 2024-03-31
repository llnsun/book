
# README.md
# JS 高级面试题

## 目录

### 课程介绍

- 导学
- 先出几个面试题，引导思考

### vue 应用

- 先出几个面试题，引导思考
- 基本使用
- 组件使用
- 高级特性
- vuex 使用
- vue-router 使用
- 面试演练

### vue 原理

- 先出几个面试题，引导思考
- 组件化和 MVVM
- 2.x 响应式
- vdom 和 diff 算法
- 模板解析
- 渲染过程（包括异步渲染）
- 前端路由
- 面试演练

### vue3

- 开始（关于 vue3 的介绍）
- vue3 响应式（包括 Proxy Map Set）
- vue3 Composition API

## React 应用

- 先出几个面试题，引导思考
- 基本使用
- 高级特性
- redux 使用
- react-router 使用
- 面试演练

## React 原理

- 先出几个面试题，引导思考
- 纯函数和不可变值
- 回顾 vdom 和 diff
- JSX 本质
- 合成事件机制
- setState 和 batchUpdate
- 组件更新和 diff 算法
- 回顾前端路由
- 面试演练

## webpack 和 babel

- 先出几个面试题，引导思考
- 基本使用
- 高级特性
- 性能优化
- babel
- 面试演练

## 组件设计

- 先出几个面试题，引导思考
- 解答 todo-list 设计
- 解答购物车设计
- 总结解题思路

## 项目流程

- 依次讲解各个流程和遇到的问题
- 总结问题和解题思路


# 01-课程介绍\01-导学.md
# 导学

参考视频

# 01-课程介绍\02-几个面试题.md
# 几个面试题

## 题目

vue

- v-if 和 v-show 的区别
- 为何 v-for 中要用 `key`
- 描述 vue 组件生命周期（以及有父子组件，两者的生命周期）
- 组件间如何通讯
- 响应式原理
- 组件渲染和更新的过程
- 双向数据绑定 v-model 的原理

React

- 组件之间如何通讯
- JSX 本质是什么
- context 是什么，如何应用？
- shouldComponentUpdate 的用途
- redux 单向数据流过程
- setState 场景题

综合应用

- 用 React 设计一个 todo-list
- 说明组件结构
- 说明 redux state 数据结构

- 用 vue 设计一个购物车
- 说明组件结构
- 说明 vuex state 数据结构

webpack

- 前端代码为何要进行构架和打包？
- module chunk bundle 的区别
- loader 和 plugin 的区别
- webpack 如何实现懒加载？
- webpack 性能优化
- babel-runtime 是什么，如何应用？

## 如何应对？

老师看过很多面试题，对于框架面试题，总结出规律

使用

- 基本用法
- 高级特性
- 周边工具

原理

- 基本理念的理解（组件化， MVVM）
- 热门技术的深度（vdom， diff 算法）
- 框架原理的全面性，完整流程

综合应用

- 场景题，现场做项目设计
- 组件结构
- 数据结构

思考一下，为何面试会这样问：

- 保证候选人能正常干活，不拖后腿 —— 考察：基本用法，周边工具，高级特性
- 多候选人竞争时，选择有技术追求的 —— 考察：原理
- 看候选人是否能独立承担项目 —— 考察：综合应用、设计

```js
class Root extends React.Component {
  constructor(props) {
    super(props)
    this.state = { count: 0 }
  }
  componentDidMount() {
    this.setState({ count: this.state.count + 1 })
    console.log(this.state.count)    // 打印
    this.setState({ count: this.state.count + 1 })
    console.log(this.state.count)    // 打印
    setTimeout(function(){
      this.setState({ count: this.state.count + 1 })
      console.log(this.state.count)   // 打印
    }, 0)
    setTimeout(function(){
      this.setState({ count: this.state.count + 1 })
      console.log(this.state.count)   // 打印
    }, 0)
  }
  render() {
    return <h1>{this.state.count}</h1>
  }
}
```


# 02-vue使用\01-开始.md
# vue 使用

## 目录

- 基本使用
- 组件使用
- 高级特性
- vuex 使用
- vue-router 使用

## 先出几个面试题

- v-if 和 v-show 的区别
- 为何 v-for 中要用 `key`
- 描述 vue 组件生命周期（以及有父子组件，两者的生命周期）
- 组件间如何通讯
- 响应式原理
- 组件渲染和更新的过程
- 双向数据绑定 v-model 的原理

这对以上题目

- 先自己思考，要带着思考和疑问来继续学习
- 题目可能会涉及 vue 原理，后面会讲 —— 本来应用和原理是分不开的，但是内容太要分两章
- 这几道题是“开胃菜”，后面还有面试演练“大餐”

------

还没讲到：

- **vue render 函数**
- vue renderless 函数组件
- vue 高级组件


# 02-vue使用\02-基本使用.md
# vue 基本使用

## vue-cli 创建项目

安装最新版本 nodejs ，要求版本 >= 8.11
执行 `npm i @vue/cli -g` ，然后查看 `vue --version`

创建项目运行 `vue create xxx`

## 插值 指令

- 插值
- 表达式
- 指令（即 `v-` 开头的。后面的事件、循环、判断等也会用到指令，慢慢讲）
- 指令缩写

代码参考 vue-demo

## computed 和 watch

代码参考 vue-demo ，注意

- computed 是有缓存的，data 不变就不会重新计算
- watch
    - 如何深度监听
    - 引用类型无法拿到 oldVal

## class 和 style

代码参考 vue-demo

## 条件

代码参考 vue-demo

- v-if 和 v-show 的区别，以及使用场景 —— 频繁切换用 v-show ，否则用 v-if

## 循环

代码参考 vue-demo

- 遍历数组，遍历对象
- key
- v-for 和 v-if 不要一起用
    - v-for 会优先于 v-if 执行
    - 因此 v-if 会在每一个 v-for 中都计算一遍
    - v-if 和 v-for 拆开使用

## 事件

代码参考 vue-demo
【注意】vue 事件是被注册到当前 DOM 元素的，和 React 不一样

- 传参
- event 参数
- 事件修饰符
- 按键修饰符
- 【注意】用 vue 绑定的事件，组建销毁时会自动被解绑。自己绑定的事件，需要自己销毁。

事件修饰符

```html
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即内部元素触发的事件先在此处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
```

按键修饰符

```html
<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button @click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button @click.exact="onClick">A</button>
```

## 表单

- textarea 要用 v-model

修饰符 lazy number trim


# 02-vue使用\03-组件使用.md
# vue 组件使用

代码参考 vue-demo ComponentsDemo

- props 类型和默认值
- $emit 执行父组件的事件
- vue 自带 eventBus 功能

单个组件生命周期

vue 生命周期

- 挂载过程
- 更新过程
- 销毁过程

考虑父子组件的生命周期，参考代码中 index 和 List 组件。

创建阶段

- index created
- list created
- list mounted
- index mounted

更新阶段

- index before update
- list before update
- list updated
- index updated

销毁阶段

- index before destroy
- list before destroy
- list destroyed
- index destroyed


# 02-vue使用\04-高级特性.md
# vue 高级特性

## 自定义 v-model

代码参考 vue-demo

## $nextTick

代码参考 vue-demo

顺便用了 ref 获取一个 DOM 节点。
另外，ref 也可以被用于获取一个组件的实例。

## slot

代码参考 vue-demo

**作用域插槽**

代码参考 vue-demo

即子组件管理数据，父组件通过插槽的作用域来获取。

**具名插槽**，参考以下代码示例

```html
<!-- NamedSlot 组件 -->
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
```

```html
<NamedSlot>
  <template v-slot:header> <!-- 缩写 <template #header> -->
    <h1>将插入 header slot 中</h1>
  </template>

  <p>将插入到 main slot 中，即未命名的 slot</p>

  <template v-slot:footer>
    <p>将插入到 footer slot 中</p>
  </template>
</NamedSlot>
```

## 动态组件

关键代码如下，其中 `TplDemoName` 要有定义

```html
<component v-bind:is="TplDemoName"></component>
```

```js
import TplDemo from '../BaseUse/TplDemo'

export default {
    components: {
        TplDemo
    },
    data() {
        return {
            TplDemoName: 'TplDemo'
        }
    }
}
```

## 异步组件

代码参考 vue-demo

## keep-alive

代码参考 vue-demo

## mixin

代码参考 vue-demo

【注意】mixin 不是完美的解决方案，**它的变量作用域不明确** 。
vue3 的 composition API 也是想解决这问题。

React mixins 的缺点
Vue mixins 也同样适用


# 02-vue使用\05-vuex使用.md
# vuex 使用

安装 `npm i vuex --save` ，在入口文件中 `Vue.use(vuex)`

vuex 的操作流程 https://vuex.vuejs.org/zh/ 示意图 https://vuex.vuejs.org/vuex.png

- state
- getters
- action
- mutation
- 用于 vue
    - dispatch
    - commit
    - mapState
    - mapGetters
    - mapActions
    - mapMutations

vuex 主要是理解概念，API 不难，也就不再代码演示了。


# 02-vue使用\06-vue-router使用.md
# vue router 使用

- vue-router
- 动态路由
- to 和 push
- hash 和 history
- 懒加载（配合动态组件）

```js
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)

export default new VueRouter({
    routes: [
        {
            path: '/',
            component: () => import(
                /* webpackChunkName: "navigator" */
                './../components/Navigator'
            )
        },
        {
            path: '/feedback',
            component: () => import(
                /* webpackChunkName: "feedback" */
                './../components/FeedBack'
            )
        }
    ]
})
```

```js
const User = {
  // 获取参数如 10 20
  template: '<div>User {{ $route.params.id }}</div>'
}

const router = new VueRouter({
  routes: [
    // 动态路径参数 以冒号开头。能命中 `/user/10` `/user/20` 等格式的路由
    { path: '/user/:id', component: User }
  ]
})
```

```js
const router = new VueRouter({
  mode: 'history', // 使用 h5 history 模式
  routes: [...]
})
```


# 02-vue使用\07-总结.md
# vue 使用 - 总结

- 基本使用
- 组件使用
- 高级特性
- vuex 使用
- vue-router 使用

PS：待讲完原理之后，统一进行面试演练。因为很多问题需要结合使用和原理，统一解决。


# 03-vue原理\01-开始.md
# vue 原理

## 目录

- 组件化
- 2.x 响应式
- vdom 和 diff
- 模板解析
- 渲染过程（包括异步渲染）
- 前端路由

## 题目

- v-if 和 v-show 的区别
- 为何 v-for 中要用 `key`
- 描述 vue 组件生命周期（以及有父子组件，两者的生命周期）
- 组件间如何通讯
- 响应式原理
- 组件渲染和更新的过程
- 双向数据绑定 v-model 的原理

针对以上题目：

- 有些已经了解
- 有些知道，但不了解原理
- 学完原理之后，会有大量题目做面试演练


# 03-vue原理\02-组件化.md
# 组件化

## 组件化基础

web 开发的历史中，组件化其实很早就有了，在 jsp asp 就有了。

**ejs 组件** —— 可以看《koa2 微博》课程的示例

vue 组件

```html
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>
```

React 组件

```js
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <HelloWorld msg="Welcome to Your React App"/>
      </header>
    </div>
  );
}
```

## 数据驱动视图

### ejs 组件

可以看《koa2 微博》课程的示例
【注意】ejs 这种服务端渲染，有一个问题：**不能动态改变，只能根据 props 静态渲染**。
因此需要 vue 和 React

### vue —— MVVM 模型

（参考 vue 的 MVVM 模型图）

```html
<template>
  <div id="app">
    <p @click="changeName">{{name}}</p>
    <ul>
        <li v-for="(item, index) in list" :key="index">
            {{item}}
        </li>
    </ul>
    <button @click="addItem">添加一项</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
      return {
        name: 'vue',
        list: ['a', 'b', 'c']
      }
  },
  methods: {
    changeName() {
        this.name = '双越'
    },
    addItem() {
        this.list.push(`${Date.now()}`)
    }
  }
}
</script>
```

### React —— setState 方式

```js
class List extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            name: 'React',
            list: ['a', 'b', 'c']
        }
    }
    render() {
        return <div>
            <p onClick={this.changeName.bind(this)}>{this.state.name}</p>
            <ul>{
                this.state.list.map((item, index) => {
                    return <li key={index}>{item}</li>
                })
            }</ul>
            <button onClick={this.addItem.bind(this)}>添加一项</button>
        </div>
    }
    changeName() {
        this.setState({
            name: '双越'
        })
    }
    addItem() {
        this.setState({
            list: this.state.list.concat(`${Date.now()}`) // 使用不可变值
        })
    }
}
```

### vue 和 React 对比

都支持组件化，没有啥区别。（在这一点和 ejs 也没啥区别）

数据驱动视图

- vue 声明式
- React 函数式


# 03-vue原理\03-vue2.x响应式.md
# vue 2.x 响应式

Object.defineProperty 

## 基本用法

```js
// Object.defineProperty 的基本用法
const data = {}
const name = 'zhangsan'
Object.defineProperty(data, "name", {
    get: function () {
        console.log('get')
        return name  
    },
    set: function (newVal) {
        console.log('set')
        name = newVal
    }
});

// 测试
console.log(data.name)  // get zhangsan
data.name = 'lisi'      // set
```

## 演示

监听数据变化，参考 `code-1.js`

## 缺点

总结 Object.defineProperty 缺点：

- 深度监听，需要递归到底
- 无法监听新增属性/删除属性（Vue.set Vue.delete）
- 无法监听数组，需要特殊处理

3.0 的响应式就解决了这些问题，后面会讲。


# 03-vue原理\04-vdom和diff.md
# vdom 和 diff

## 背景

基于组件化，数据驱动视图。只需关心数据，无需关系 DOM ，好事儿。

但是，JS 运行非常快，DOM 操作却非常慢，如何让“数据驱动视图”能快速响应？

------

## 引入 vdom

用 vnode 表示真实 DOM 结构

```html
<div id="div1" class="container">
    <p>vdom</p>
    <ul style="font-size: 20px">
        <li>a</li>
    </ul>
</div>
```

```js
{
    tag: 'div',
    props: {
        className: 'container',
        id: 'div1'
    }
    children: [
        {
            tag: 'p',
            children: 'vdom'
        },
        {
            tag: 'ul',
            props: { style: 'font-size: 20px' }
            children: [
                {
                    tag: 'li',
                    children: 'a'
                }
                // ....
            ]
        }
    ]
}
```

演示 vdom 的使用（对比不用 vdom 的情况）—— snabbdom 和 jquery

------

## 使用 vdom 能快速操作 DOM

- JS 执行很快
- DOM 操作很慢

如何让 DOM 操作最快？—— 尽可能减少 DOM 操作，只操作需要更新的，不做多余操作。

如何尽量减少 DOM 操作？—— 两个 vnode 进行 diff ，找出不同。diff 是 JS 执行，会很快。
（画图示例，两棵 vnode ，找出不同）

------

## diff 算法概述

diff 算法是一个很广泛的，前端常见的例如文本 diff ，json 对象 diff ，还有这里的“树 diff”。

- 文本 diff ，例如 linux 的 diff 命令
- json diff ，例如 https://github.com/cujojs/jiff
- 树 diff ，如 vdom diff

**diff 两棵树的时间复杂度是 `O(n^3)`**（不可用的复杂度），例如 `diff(Tree1, Tree2)`

- 遍历 Tree1 ，每个节点都要和 Tree2 对比
- 针对 Tree1 的节点，遍历 Tree2 每个节点和它对比
- 重新排序

但是，vdom diff 算法做了几个改进，**让复杂度变为 `O(n)`** 

- 只比较同一层级
- tag 或组件不相同的，直接删掉重建，不再继续深入比较
- tag 或组件 & key ，两个都相同的，即认为是相同节点

------

## diff 算法过程详解

snabbdom https://github.com/snabbdom/snabbdom 是一款比较简洁、高性能的 vdom lib
vue2.x 的 diff 算法完全参考它。
即了解 snabbdom 的 diff 算法，也就了解 vue2.x 的 diff 算法。**应该面试的 diff 算法问题足够了**。

基本流程

- 回顾一下它的基本使用，找出核心的 API `h` `patch`
- 下载 snabbdom 源码
- 查看源码

注意

- 解读源码，只看主干和要点，不要去扣细节
- 源码是 ts ，但不妨碍我们阅读，不要关注语法细节

### h 函数

【功能】h 函数是一个工厂函数，根据传入的参数，生成 vnode 结构。

源码在 `src/h.ts`

输入和输出 `function h(sel: string, data: VNodeData, children: VNodeChildren): VNode;`

返回 `return vnode(sel, data, children, text, undefined);`

### vnode 函数

源码在 `src/vnode.ts`

返回 `return {sel, data, children, text, elm, key};`

这里可以结合 demo 中的断点来看数据结构。此时的 `elem` 应该是 `undefined`

### text 和 children

一个元素或者有 contentText ，后者有 children ，两者不能共存
demo 中有示例

### patch 函数

【功能】patch 函数将 newVnode 更新到 vnode 或者 elem 上，patch 的过程也就是 diff 的过程。

源码 `src/snabbdom.ts` ，找到其中的 `init` 函数，最后返回的就是 `patch` 函数。

输入输出 `function patch(oldVnode: VNode | Element, vnode: VNode): VNode`

（画图：elem 和 oldVnode vnode 的关系）
（要考虑第一个参数是 VNode 和 Element 两种情况）

### patchVnode 函数

源码在 `src/snabbdom.ts`

先看 `addVnodes` 和 `removeVnodes` ，最后看 `updateChildren`

### updateChildren 函数

源码在 `src/snabbdom.ts`

以 todo list 的 items 变化，为例，图解演示即可

------

## 总结

diff 算法中，细节不是关键例如“头头 头尾 对比”等，核心概念才是关键，如 h vnode patch key 等。
所有的 diff 算法，以及无论如何做优化，都离不开这些核心概念


# 03-vue原理\05-原理.md
# vue 原理

- 响应式
- vdom
- 模板解析
- 渲染过程
- 异步渲染

------

## 响应式

响应式的作用：**监听 data 数据变化**，仅此而已。所以，不要掺杂进其他功能进来。

回顾 Object.defineProperty 方式

## vdom

回顾 vdom

- h 函数
- vnode 结构
- patch 函数

------

## 模板解析

### with 语法

- 改变 {} 内自由变量，当做 obj 属性来查找
- 如果找不到会报错
- with 要慎用，因为它打破了作用域的规则

```js
const obj = {a: 100, b: 200}

console.log(obj.a)
console.log(obj.b)
console.log(obj.c) // undefined

// 使用 with ，能改变 {} 内自由变量的查找方式
// 将 {} 内自由变量，当做 obj 的属性来查找
with(obj) {
    console.log(a)
    console.log(b)
    console.log(c) // 会报错 ！！！
}
```

### 编译 render 函数

- 原生 html 不识别指令
- html 是静态标记语言，不具备运算能力（不是图灵完备的语言，不能顺序、判断、循环运算）
- 将 html 模板转换为 js 函数（render 函数）
- 执行 render 函数，生成 vnode。重要！！！

如何转换，参考 vue-template-compiler 示例

### vue 函数式组件

https://cn.vuejs.org/v2/guide/render-function.html#%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BB%84%E4%BB%B6

使用 render 函数代替 template

```js
Vue.component('heading', {
  // template: `xxxx`,
  render: function (createElement) {
    return createElement(
      'h' + this.level,
      [
        createElement('a', {
          attrs: {
            name: 'headerId',
            href: '#' + 'headerId'
          }
        }, 'this is a tag')
      ]
    )
  }
})
```

------

## 渲染过程

### 回顾 3 个要点

- 响应式 监听数据 get set
- 模板解析 生成 render 函数，执行则返回 vnode
- vdom 根据 vnode 渲染/更新 DOM

### 初次渲染过程

- 对 data 进行响应式处理，监听 get set
- 解析模板为 render 函数（**这一步可能在开发环境打包时就已经完成，重要！！！**）
- 执行 render 函数，生成 vnode
    - 这一步会触发 data getter ，收集依赖，重要！！！
    - 将该数据 “观察”起来
    - 注意，不一定所有的 data 都会被观察，得看模板中是否用到了，如下图。
- 将 vnode 渲染到页面上

```html
<p>{{message}}</p>

<script>
export default {
    data() {
        return {
            message: 'hello', // 会触发 get
            city: '北京' // 不会触发 get ，因为模板没用到，即和视图没关系
        }
    }
}
</script>
```

### 数据更新过程

- 修改“被观察的”数据，触发 data setter
- 重新执行 render 函数，生成 newVnode
- patch(vnode, newVnode)

### 图示

vue 官网的流程图 https://cn.vuejs.org/images/data.png

------

## 异步渲染

回顾 nextTick

- 异步渲染
- 汇总 data 变化，一次性渲染
- 尽量减少渲染次数，提高性能


# 03-vue原理\06-前端路由.md
# 前端路由

- hash
- history API

## hash

hash 是什么

```js
// http://127.0.0.1:8881/01-hash.html?a=100&b=20#/aaa/bbb
location.protocol // 'http:'
location.hostname // '127.0.0.1'
location.host // '127.0.0.1:8881'
location.port // '8881'
location.pathname // '/01-hash.html'
location.search // '?a=100&b=20'
location.hash // '#/aaa/bbb'
```

hash 的特点，重要！！！

- 会触发页面跳转，即可后退、前进
- 但不会刷新页面，支持 SPA 必须的特性
- hash 不会被提交到 server 端（因此刷新页面也会命中当前页面，让前端根据 hash 处理路由）

url 中的 hash ，是不会发送给 server 端的。前端 `onhashchange` 拿到自行处理。

onhashchange 监听 hash 变化

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

## history API

常用的两个 API

- history.pushState
- window.onpopstate

页面刷新时，**服务端要做处理**。即无论什么 url 访问 server ，都要返回该页面。

需要 server 端配合，可参考 https://router.vuejs.org/zh/guide/essentials/history-mode.html#%E5%90%8E%E7%AB%AF%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90

按照 url 规范，不同的 url 对应不同的资源，例如：

- https://github.com/ 首页
- https://github.com/username/ 用户页
- https://github.com/username/xxx/ 项目页

但是用了 SPA 的前端路由，就改变了这一规则，假如 github 用了的话：

- https://github.com/ 首页
- https://github.com/username/ 首页（前端处理路由）
- https://github.com/username/xxx/ 首页（前端处理路由）

所以，从开发者的实现角度来看，前端路由是一个违反规则的形式。
但是从不关心后端，只关心前端页面的用户，或者浏览器来看，更喜欢 pushState 这种方式。

## 如何选择？

- 内部系统或 to B 的管理系统，用 hash 。简单易用，对 url 规范没有要求。
- to C 的页面，用 history API ，对 url 规范和 SEO 要求较高。—— 但需要服务端配合

## 结合 vue-router

vue-router 和 react-router 的路由原理


# 03-vue原理\07-总结.md
# vue 原理 - 总结

- 组件化
- 2.x 响应式
- vdom 和 diff
- 模板解析
- 渲染过程（包括异步渲染）
- 前端路由


# 03-vue原理\08-面试演练.md
# vue 原理 - 面试演练

前面出的几个面试题

- v-if 和 v-show 的区别
- 为何 v-for 中要用 `key`
- 描述 vue 组件生命周期（以及有父子组件，两者的生命周期）
- 组件间如何通讯
- 组件渲染和更新的过程
- 双向数据绑定 v-model 的原理

补充面试题 —— 待补充

- 说一下对 MVVM 的理解
- computed 和 method 的区别？
- 为何组件 data 必须是一个函数？
- ajax 请求应该放在哪个生命周期？
- 如何将父组件的所有 props 传递给子组件？—— $props
- 如何自己实现一个 v-model ？
- 多组件有相同的逻辑，如何抽离？
- 何时需要使用异步组件？
- 何时需要使用 keep-alive
- 何时需要使用 beforeDestroy ？
- 什么是作用域插槽？为何需要它
- vuex 的 action 和 mutation 有何区别？
- vue-router 路由模式有几种？ —— 三种 "hash" | "history" | "abstract" ？？？
- 如何配置 vue-router 异步加载？
- 场景题：用虚拟 DOM 描述一个 html 结构
- vue 如何监听 data 变化？
- vue 如何监听数组变化？
- 响应式原理
- 简述 diff 算法过程
- diff 算法时间复杂度是多少
- vue 为何是异步渲染？
- nextTick 有何作用？
- vue-router 如何实现路由变化？
- vue 性能优化
（开发环境编译模板）


# 04-vue3\01-开始.md
# vue 3

Proxy 兼容性问题，不可 polyfill —— 不好解决，只能等所有平台的升级。

使用 `Object.defineProperty` 支持 IE11

vue 3 升级内容？？？

## 概述

- vue3 会在 2020 年第一季度发布
- vue3 使用 ts 重写（响应式，vdom，模板解析等）
- vue3 增加了新玩法 —— Composition API

## vue3 发布后 vue2 会过时吗

Vue3.0 会在 2020 年第一季度发布，**Vue2.x 是否已经过时了**？—— 近期不会过时

- Vue 3.0 的全面推广使用，需要持续一段时间（预计大概一年的时间）。这段时间还会继续用 2.x
- Vue 2.x 已经普及，且用于很多项目，这些项目还需要维护
- Vue 是平滑升级，不是断崖式升级，2.x 的功能在 3.x 照样适用。

另外，当 3.0 发布且推广开来之后，课程会及时更新 3.0 的面试题。

PS：只要 vue 还是基于 MVVM 和 html 模板的设计方式，那这些内容就不会过时。就像，只要有 DOM 操作 jquery 就依然有价值。

## 重要内容

- Proxy 实现响应式
- Composition API
- 其他内容，后续会继续更新


# 04-vue3\04-Proxy.md
# Proxy Reflect 语法

## 代理对象

get set deleteProperty

```js
const obj = {
    a: 100,
    b: 200
}

const objProxy = new Proxy(obj, {
    get(target, key, receiver) {
        // 原型属性（如 toString ），不希望被监听到
        const ownKeys = Reflect.ownKeys(target)
        if (ownKeys.includes(key) === true) {
            // console.log('get', target, key, receiver)
            console.log('get', key)
        }

        // 返回结果
        return Reflect.get(target, key, receiver)
    },
    set(target, key, value, receiver) {
        console.log('set', key, value)
        const res = Reflect.set(target, key, value, receiver) // 如果属性只读，则返回 false。如 object.defineProperty writable false
        console.log('set res', res)
        return res
    },
    // has(target, key) {
    //     console.log('has', key)
    //     const res = Reflect.has(target, key) // 可以用 key in target ，但并不是函数式的规范写法
    //     console.log('has res', res)
    //     return res
    // },
    deleteProperty(target, key) {
        console.log('deleteProperty', key)
        const res = Reflect.deleteProperty(target, key) // 如果用 delete target[key] ，但返回结果永远都是 true ，而且不是规范的函数式写法
        console.log('deleteProperty res', res)
        return res
    }
})

// 测试
objProxy.a
objProxy.b
objProxy.a = 101
delete objProxy.a
```

## 代理数组

```js
const arr = [10, 20, 30]
const arrProxy = new Proxy(arr, {
    get(target, key, receiver) {
        // 原型属性(如 toString push pop 等)，不希望被监听到
        const ownKeys = Reflect.ownKeys(target)
        if (ownKeys.includes(key) === true) {
            // 获取 arrProxy[0] 应该触发
            // 获取 arrProxy.length 应该触发，可能需要将 length 显示到视图中
            console.log('get', key)
        }

        // 返回结果
        return Reflect.get(target, key, receiver)
    },
    set(target, key, value, receiver) {
        // arrProxy.push(40) 时，会先设置 3:40 ，然后设置 length:4，即 set 两次。
        // 而 length:4 这次 set 是没必要监听到的。因为当设置 3:40 的时候，length 就已经是 4 了
        const curVal = Reflect.get(target, key, receiver)
        if (value === curVal) {
            // 值已相等，如上述 length 的情况
            return true
        }

        console.log('set', key, value)
        const res = Reflect.set(target, key, value, receiver)
        console.log('set res', res)
        return res
    },
    deleteProperty(target, key) {
        console.log('deleteProperty', key)
        const res = Reflect.deleteProperty(target, key)
        console.log('deleteProperty res', res)
        return res
    }
})

// 测试
arrProxy[1]
arrProxy.length
arrProxy.push(40)
```

## 思考 Proxy Reflect 的作用

Proxy 作用

- 代理属性和方法
- 监听变化
- 针对对象、数组，全方位

Reflect 作用

- API 和 Proxy 对应
- Reflect 能让编程规范化、标准化、函数式
- Reflect 会替代掉 Object 上的工具函数

```js
Reflect.has(target, key)
key in target

Reflect.deleteProperty(target, key)
delete target[key]

Reflect.ownKeys({a: 100})
Object.getOwnPropertyNames({a: 100})
```


# 04-vue3\05-vue3响应式.md
# vue3 响应式

## 回顾 Object.defineProperty

基本用法

```js
// Object.defineProperty 的基本用法
const data = {}
const name = 'zhangsan'
Object.defineProperty(data, "name", {
    get: function () {
        console.log('get')
        return name  
    },
    set: function (newVal) {
        console.log('set')
        name = newVal
    }
});

// 测试
console.log(data.name)  // 可以监听到
data.name = 'lisi'      // 可以监听到
```

监听数据变化，参考 `code-1.js`

总结 Object.defineProperty 缺点：

- 深度监听，需要递归到底
- 无法监听新增属性/删除属性（Vue.set Vue.delete）
- 无法监听数组，需要特殊处理

## 使用 Proxy

我们已知：

- Proxy 可以原生监听 新增/删除属性
- Proxy 原生支持监听数组变化

接下来看看 Proxy 如何实现深度监听。参考 `code-2.js`

## 两者对比

- 深度监听，都用递归。但前者是一次性递归，后者是访问时再递归。
- Proxy 原生能监听 新增/删除属性
- Proxy 原生支持监听数组变化

但 —— **Proxy 兼容性不好** ，我见过，oppo vivo 的某些机型，某些 app 的 webview 还没有支持 ES6 。

## vue3 响应式实现

响应式的作用：**监听 data 数据变化**，仅此而已。所以，不要掺杂进其他功能进来。

### 回顾

- 回顾 Object.defineProperty 方式
- 回归 Proxy 语法
- 回顾 Map 和 Set 语法

### Proxy 实现

用 Proxy 模仿 Vue 3.0 的响应式

学习用法

- 下载 vue-next ，然后查看测试用例，看 `packages/reactivity/__tests__/effect.spec.ts`
- 找 `basic properties` ，找到使用方式

源码编写，步骤如下

- `reactivity-1.js` 实现简单的 Proxy 监听
- `reactivity-2.js` 深度监听，修改 `get` 的代码
- `reactivity-3.js` 监听数组，修改 `get` 去掉原型方法，修改 `set` 区分新增属性和修改属性，不重复修改属性
- `reactivity-4.js` 避免重复代理
    - 新建 `toProxyMap` 和 `toRawMap`
    - `createReactiveObject` 中
        - 创建 proxy 之前，判断 `toProxyMap` 是否有对应的 proxy
        - 创建 Proxy 之前，判断 `toRawMap` 是否已有对应的 proxy
        - 生成 proxy 之后，设置 `toProxyMap`
        - 生成 proxy 之后，设置 `toRawMap`
- `reactivity-5.js` 接收副作用，**先初始化时能执行一次**。创建 `effect` `createReactiveEffect` `run` 和 `activeEffectStacks`
- `reactivity-6.js` 响应式副作用
    - 新建 `targetsMap`
    - 新建 `track` 函数，并在 `get` 时执行
    - 新建 `trigger` 函数，并在 `set` 时执行

总结 Proxy 比 Object.defineProperty 的优点？

- 深度监听时，Proxy 延迟递归，而不是一上来就全部递归，性能好
- 原生支持监听数组
- 原生支持新增和删除属性


# 05-React使用\01-开始.md
# React 使用

- 基本使用
- 高级特性
- redux 使用
- react-router 使用

## 题目

- 组件之间如何通讯
- JSX 本质是什么
- context 是什么，如何应用？
- shouldComponentUpdate 的用途
- redux 单向数据流过程
- setState 场景题

这对以上题目

- 先自己思考，要带着思考和疑问来继续学习
- 题目可能会涉及 React 原理，后面会讲 —— 本来应用和原理是分不开的，但是内容太要分两章
- 这几道题是“开胃菜”，后面还有面试演练“大餐”


# 05-React使用\02-基本使用.md
# React 基本使用

**【注意】代码演示时，和 vue 相关的知识对比一下 —— 重要！！！**

## 创建项目

安装最新版本 nodejs ，要求版本 >= 8.10。
安装 `npm i -g create-react-app` ，然后执行 `create-react-app xxx` 创建项目

## JSX 基本语法

查看代码

- 变量和表达式
- class 和 style
- 子元素和组件

另外还有原生 html （未过滤 xss）的加载方式

## 条件

查看代码

- if else
- 逻辑运算符 && ||
- 三元表达式

## 列表

查看代码

- map 函数
- key（作用和 vue 的相同）

## 事件

查看代码

- this
- event 对象（真实的 event 和 currentTarget）
- 传递参数

## 表单

- 受控组件 （非受控组件后面讲）
- input textarea select - 用 value
- checkbox radio - 用 checked

## 组件和 props (和类型检查)

- props 传递数据
- props 传递函数
- props 类型检查 （安装 `npm i prop-types --save`）

## setState

- 用不可变值（对象、数组）或者用 immutable.js
- 可能是异步更新（什么情况下同步更新？）
- 可能会被合并（什么情况下不合并？）

```js
// 不可变值 - 数组
const list5Copy = this.state.list5.slice()
list5Copy.splice(2, 0, 'a') // 中间插入/删除
this.setState({
    list1: this.state.list1.concat(100), // 追加
    list2: [...this.state.list2, 100], // 追加
    list3: this.state.list3.slice(0, 3), // 截取
    list4: this.state.list4.filter(item => item > 100) // 筛选
    list5: list5Copy // 其他操作
})
// 注意，不能直接对 this.state.list 进行 push pop splice 等，这样违反不可变值
```

```js
// 不可变值 - 对象
this.setState({
    obj1: Object.assign({}, this.state.obj1, {a: 100}),
    obj2: {...this.state.obj2, a: 100}
})
// 注意，不能直接对 this.state.obj 进行属性设置，这样违反不可变值
```

## 生命周期

图示

- componentDidMount 可获取 ajax 数据
- shouldComponentUpdate 可做性能优化
- componentWillUnmount 可销毁事件绑定，避免内存泄露
- shouldComponentUpdate 和 componentWillUpdate 中，不要 setState ，可能会死循环

- 挂载过程
- 更新过程
- 销毁过程


# 05-React使用\03-1-高级用法-1.md
# React 高级用法

## 函数组件

函数组件没有实例，也不能监听各个生命周期，也无法扩展属性和方法。只是输入 props ，输出 jsx ，纯函数。

```js
// class 组件
class List extends React.Component {
    constructor(props) {
        super(props)
    }
    render() {
        const { list } = this.props

        return <ul>{list.map((item, index) => {
            return <li key={item.id}>
                <span>{item.title}</span>
            </li>
        })}</ul>
    }
}

// 函数组件
function List(props) {
    const { list } = this.props

    return <ul>{list.map((item, index) => {
        return <li key={item.id}>
            <span>{item.title}</span>
        </li>
    })}</ul>
}
```

## 非受控组件

先回顾受控组件

要点：

- ref
- defaultValue defaultChecked
- 手动操作 DOM 元素

使用场景，必须通过 DOM 节点才能操作的：

- 文件上传 `<input type="file">`
- 有些富文本编辑器，要求通过 DOM 节点渲染

受控 vs 非受控

- 优先使用受控组件，符合 React 的设计思路
- 必须操作 DOM 的才考虑非受控组件

## Portals

Portal 提供了一种将子节点渲染到存在于父组件以外的 DOM 节点的优秀的方案。

以下情况可能要考虑使用 Portal

- 组件有 overflow: hidden （其他命中 BFC 的情况），导致了渲染问题
- 父组件有 z-index 导致了渲染问题
- 用到 fixed 等需要跳出父组件

## context

Context 提供了一个无需为每层组件手动添加 props，就能在组件树间进行数据传递的方法。
例如：地区偏好，UI 主题。这些属性是应用程序中许多组件都需要的。Context 提供了一种在组件之间共享此类值的方式，而不必显式地通过组件树的逐层传递 props。

- React.createContext(defaultValue) 创建 Context
- Context.Provider 最外层父组件
- Class.contextType 和 this.context - 用于类组件
- Context.Consumer - 用于函数组件

## 异步组件 懒加载

- import() 语法，可回顾 vue 动态组件
- React.lazy 动态引入 React 组件
- React.Suspense 实现 loading 效果

```js
import("./math").then(math => {
  console.log(math.add(10, 20))
})
```


# 05-React使用\03-2-高级用法-2.md
# React 高级用法

## 性能优化

React 性能优化方案，说出来可能有很多，但是那些是所有前端项目、框架都需要做的。如

- 代码分割，代码压缩，使用生产版本的代码等（前端框架都需要，通用方案）
- 渲染列表时合理使用 key （vue 也有）
- 缓存组件（vue 也有）

只有一点是 React 特色的：**如何避免无效渲染？**（vue 就没有这个困扰，后面再说）

- shouldComponentUpdate
- PureComponent 和 memo
- 不可变数据 immutable.js

### 解释 shouldComponentUpdate

- 复杂项目中，React 会出现一些无效的渲染（有些可能并不影响性能，不是所有的都需要优化）
- React 提供了 SCU 来让用户自己选择是否优化
- SCU 返回 true 则渲染，返回 false 则不渲染。默认返回 true —— 演示一下

那么问题来了 —— **既然这样，能否将 SCU 都做一个判断，props 和 state 一样，就返回 true 呢？**

答案是不能 —— 做演示：1. 借助 propsDemo 改造；2. 使用 `push` 操作数组；3. 使用 `_.isEqual` 对比 list ；4. 再分别注释掉 `push` 和 `SCU` 做对比。

- 回顾之前 setState 的使用，纯函数，不可变值
- push 会改变 nextState 的值，因此被 SCU 拦截
- SCU 必须配合不可变值一起使用

### 解释 PureComponent

- 自带 shouldComponentUpdate 比较
- 只有浅比较（只比较函数或数组第一层属性，深层次不管）—— 深度比较太消耗性能
- 演示 demo （List 使用 PureComponent，使用不可变值）

### 合理使用 shouldComponentUpdate 和 PureComponent

- 一定要用不可变值，否则会留坑（这是 React 的基本里面）
- 推荐使用 PureComponent
- 同时，state 设计尽量扁平

### React.memo

- 用于函数组件（Class 组件用 SCU）
- 对于相同的 props ，会缓存渲染结果
- 默认只进浅层比较（和 PureComponent 一样）

```js
const MyComponent = React.memo(function MyComponent(props) {
  /* 使用 props 渲染 */
})
```

### 不可变值 immutable.js

https://github.com/immutable-js/immutable-js

```js
const map1 = Immutable.Map({ a: 1, b: 2, c: 3 })
const map2 = map1.set('b', 50)
map1.get('b') // 2
map2.get('b') // 50
```

- 专门为 React 设计的“不可变值”工具
- 使用共享数据（不是深拷贝），速度很快
- 有一定学习成本和迁移成本，因此仅推荐复杂、大型的项目使用

### 总结一下 React 性能优化

如何避免 React 组件重复渲染

- SCU 和不可变值
- PureComponent 和 React.memo
- immutable.js


# 05-React使用\03-3-高级用法-3.md
# React 高级用法

React 组件逻辑的复用

- mixin 已经弃用（具体参考 vue mixin ，一样的）
- 高阶组件
- render prop

## 高阶组件 HOC

高阶组件不是一种功能，而是一种模式。

```js
// 高阶组件不是一种功能，而是一种模式
const HOCFactory = (Component) => {
  class HOC extends React.Component {
    // 在此定义多个组件的公共逻辑
    render(){
      return <Component {...this.props} /> // 返回拼装的结果
    }
  }
  return HOC
}
const EnhancedComponent1 = HOCFactory(WrappedComponent1)
const EnhancedComponent2 = HOCFactory(WrappedComponent2)
```

示例参考 HOCDemo

redux 的 connect 就是一个高阶组件，应用如下

```js
import { connect } from 'react-redux'

// connect 是高阶组件
const VisibleTodoList = connect(
    mapStateToProps,
    mapDispatchToProps
)(TodoList)

export default VisibleTodoList
```

connect 源码结构如下

- connect 接收 mapStateToProps 和 mapDispatchToProps ，返回一个函数
- 该函数是一个高阶组件，接收 WrappedComponent ，返回新组件

```js
export const connect = (mapStateToProps, mapDispatchToProps) => (WrappedComponent) => {
  class Connect extends Component {
    constructor () {
      super()
      this.state = {
        allProps: {}
      }
    }

    /* 中间省略 N 行代码 */

    render () {
      return <WrappedComponent {...this.state.allProps} />
    }
  }
  return Connect
}
```

## render prop

Render Props 的核心思想是，通过一个函数将 class 组件的 state 作为 props 传递给纯函数组件。

```js
// Render Props 的核心思想
// 通过一个函数将 class 组件的 state 作为 props 传递给纯函数组件
class Factory extends React.Component {
  constructor() {
    this.state = {
      /* state 即多个组件的公共逻辑的数据 */
    }
  }
  /* 修改 state */
  render(){
    return <div>{this.props.render(this.state)}</div>
  }
}
const App = () => (
    <Factory render={
        /* render 是一个函数组件 */
        (props)) => <p>{props.a} {props.b} ...</p>
    }/>
)
```

查看代码 demo

**HOC 和 render prop 的对比**

- HOC
    - 会增加层级关系，使结构变的复杂。但 HOC 可通过扩展参数实现更复杂的功能。（如 `withMouse(App, a, b)` 等这样扩展参数）
    - 需透传 props 给 wrapperComponent ，规范做不好的话，容易混乱
    - 比较好理解，易上手
- render props
    - 代码简洁 层级简洁
    - 不需要透传 props
    - 有一定学习成本 （render 和 prop 本来就是 React 的两个关键字，现在又组合起来，作为一个新的技术点，比较绕）

具体用哪个，自己根据实际情况判断


# 05-React使用\03-4-高级应用-4.md
# React 高级应用

## hook

最后看面试题中 hook 的占比，再决定否是要讲解。或者后续更新升级。

------

react hook 要和 vue 组合 API 对应起来，所以 vue 组合 API 也要介绍一下。
而且，两者结合着来看，会更加好理解。

React 深入：从 Mixin 到 HOC 再到 Hooks


# 05-React使用\04-redux.md
# redux

redux 一般用于大型项目的数据管理。
组件较多，数据较多，就把数据集中存储到一个地方，供所有组件共享访问。

## 基本概念和用法

- store state
- action
- reducer

看文档 https://www.redux.org.cn/ 中的示例（在 redux-demo.js 中）

## 单项数据流模型

redux 数据流和 redux-thunk 数据流

## react-redux

- Provider connect
- mapStateToProps
- mapDispatchToProps

查看代码 redux-demo
注意，这里只需要关心 redux 的使用。数据结构和 react 组件结构，后面再讲。

## 异步 action

action 是创造新数据的来源。异步获取新数据，是前端很常见的方式。

### 使用 redux-thunk

```js
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers/index';

// 创建 store 时，作为中间件引入 redux-thunk
const store = createStore(rootReducer, applyMiddleware(thunk));
```

```js
// 同步 action
export const addTodo = text => {
  // 返回 action 对象
  return {
    type: 'ADD_TODO',
    id: nextTodoId++,
    text
  }
}

// 异步 action
export const addTodoAsync = text => {
  // 返回函数，其中有 dispatch 参数
  return (dispatch) => {
    // ajax 异步获取数据
    fetch(url).then(res => {
      // 执行异步 action
      dispatch(addTodo(res.text))
    })
  }
}
```

### 其他库

- redux-promise
- redux-saga

## 中间件

想要在 redux 的每一次 action 中都增加一段业务逻辑（如增加一个打印当前 action 的 logger 功能）

- reducer 是纯函数，只承担计算 state 的功能，不能在这里加
- View 是 state 的视觉层，根据 state 渲染，不能在这里加
- Action 是存放数据的对象，即消息的载体，只能被别人操作，自己不能进行任何操作

想来想去，只能在 dispatch 上搞搞事情。

```js
// 自己修改 dispatch ，增加 logger
let next = store.dispatch;
store.dispatch = function dispatchAndLog(action) {
  console.log('dispatching', action);
  next(action);
  console.log('next state', store.getState());
}
```

```js
// 将这个能力拆分出来，作为中间件
import { applyMiddleware, createStore } from 'redux';
import createLogger from 'redux-logger';
import thunk from 'redux-thunk';
const logger = createLogger();

const store = createStore(
  reducer,
  applyMiddleware(thunk, logger) // 会按顺序执行
  //（此处，也可以想一下 redux-thunk 是如何实现的）
);
```

总结。说白了，redux 中间件，就是对 dispatch 的二次封装，就是 redux 允许用户自定义 dispatch 。


# 05-React使用\05-react-router.md
# React router

React router 不是 React 面试题部分的重要考点。

## 基本的使用

- 路由配置（router route path 动态路由）
- 路由跳转（Link to， history.push）
- 钩子（onEnter onUpdate onLeave）—— 也可以使用 route 对应的生命周期来替代这三个（componentDidMount替代onEnter，使用componentDidUpdate替代onUpdate，使用componentWillUnmount替换onLeave。）

```js
// 配置路由
import React from 'react'
import { Router, Route, Link, browserHistory } from 'react-router'

/* 定义 App About Inbox Message 组件，省略 */

React.render((
  <Router history={browserHistory}>
    <Route path="/" component={App}>
      <Route path="about" component={About} />
      <Route path="inbox" component={Inbox}>
        {/* 动态路由*/}
        <Route path="messages/:id" component={Message} />
      </Route>
    </Route>
  </Router>
), document.body)
```

```js
// 路由跳转 使用 <Link to="/xxx">
const App = React.createClass({
  render() {
    return (
      <div>
        <h1>App</h1>
        <ul>
          <li><Link to="/about">About</Link></li>
          <li><Link to="/inbox">Inbox</Link></li>
        </ul>
        {this.props.children}
      </div>
    )
  }
})
```

## 常见的考点

第一，回顾前端路由实现方案： hash 和 pushState

```js
// 使用 history API
import { Router, Route, Link, browserHistory } from 'react-router'
/* 定义 routes ，省略 */
render(
  <Router history={browserHistory} routes={routes} />,
  document.getElementById('app')
)

// 使用 hash
import { Router, Route, Link, hashHistory } from 'react-router'
/* 定义 routes ，省略*/
render(
  <Router history={hashHistory} routes={routes} />,
  document.getElementById('app')
)
```

第二，基于路由的代码分割，使用 lazy 和 Suspense

```js
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import React, { Suspense, lazy } from 'react';

const Home = lazy(() => import('./routes/Home'));
const About = lazy(() => import('./routes/About'));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home}/>
        <Route path="/about" component={About}/>
      </Switch>
    </Suspense>
  </Router>
);
```


# 05-React使用\06-总结.md
# 总结

- 基本使用
- 高级特性
- redux 使用
- react-router 使用

PS：待讲完原理之后，统一进行面试演练。因为很多问题需要结合使用和原理，统一解决。


# 06-React原理\01-开始.md
# React 原理

目录

- 纯函数和不可变值 —— 前面应该讲过，回顾即可
- 回顾 vdom 和 diff
- JSX 本质
- 合成事件机制
- setState 和 batchUpdate
- 组件更新和 diff 算法
- 回顾前端路由

题目

- 组件之间如何通讯
- JSX 本质是什么
- context 是什么，如何应用？
- shouldComponentUpdate 的用途
- redux 单向数据流过程
- setState 场景题

针对以上题目：

- 有些已经了解
- 有些知道，但不了解原理
- 学完原理之后，会有大量题目做面试演练


# 06-React原理\02-原理.md
# React 原理

回顾 vue 渲染和更新过程

- 要点
    - 响应式
    - 模板解析
    - vdom
- 过程
    - 初次渲染时
    - 更新时
    - 示意图

------

## React 原理的要点

- JSX 渲染出页面（JSX 的本质是什么）
- 事件如何被绑定（之前说过，事件都挂载到了 document 上）
- setState 过程（为何有时同步，有时异步？）
- 组件更新和 diff 算法

------

## JSX 的本质

首先，回顾一下 vodm 的知识

- vnode 结构
- h 函数
- patch 函数

到 `https://www.babeljs.cn/` 做一个测试，将以下 jsx 编译为 js

```js
// JSX 基本用法
const imgElem = <div>
    <p>some text</p>
    <img src={imgUrl}/>
</div>

// JSX style
const styleData = { fontSize: '30px',  color: 'blue' }
const styleElem = <p style={styleData}>设置 style</p>

// JSX 加载组件
const app = <div>
    <Input submitTitle={onSubmitTitle}/>
    <List list={list}/>
</div>

// JSX 事件
const eventList = <p onClick={this.clickHandler}>
    some text
</p>

// JSX list
const listElem = <ul>{this.state.list.map((item, index) => {
    return <li key={item.id}>index {index}; title {item.title}</li>
})}</ul>

```

以上可见，`React.createElement` 就相当于 `h` 函数，执行则会返回一个 vnode 结构。

```js
{
    tag: 'div', // 或是一个组件名 Input List 等
    props: {...},
    children: [...] // 或 '...' 其中只有文本
}
```

看 React.createElement 的第一个参数

- 渲染 html 标签时，就是一个字符串， div p img 等
- 渲染组件时，就是一个组件，Input List 等
- React 规定，所有的组件必须大写字母开头，因为 html 标签都是小写字母开头 —— 这样就很好识别 jsx 标签是一个 html tag 还是自定义组件。

如果第一个参数是组件，那就继续去寻找该组件的 render 函数中的 jsx 结构，直到找到最底层，即 html tag 。

```js
// 第一个参数是 List 组件
React.createElement(List, {
  list: list
})

// 找到 List 组件 jsx 结构，继续拆分
React.createElement("ul", null, list.map(
        function (item, index) {
            return React.createElement("li", {
                key: item.id
            }, "title ", item.title)
        }
    )
)
```

总结一下

- JSX 是 React.createElement 的语法糖
- React.createElement 最终返回 vnode
- 其中遇到自定义组件，会继续找其 jsx 结构，继续渲染

最后，将 vnode 结构渲染为 elem ，之前已经讲过，React 这里的过程也是一样的。
React 将组件分为四个类型，分别进行渲染。

- ReactEmptyComponent - 空组件 null undefined
- ReactDOMComponent - html 节点
- ReactTextComponent - 文本组件
- ReactCompositeComponent - 自定义组件

------

## 事件机制

```js
clickHandler = (event) => {
    event.preventDefault()
    event.stopPropagation()

    console.log('target', event.target) // 指向当前元素，即当前元素触发
    console.log('current target', event.currentTarget) // 指向当前元素，假象！！！

    // 注意，event 其实是 React 封装的。可以看 __proto__.constructor 是 SyntheticEvent
    console.log('event', event)

    // 原生 event 如下。其 __proto__.constructor 是 MouseEvent
    console.log('nativeEvent', event.nativeEvent)
    // 指向当前元素，即当前元素触发
    console.log('nativeEvent target', event.nativeEvent.target)
    // 指向 document ！！！
    console.log('nativeEvent current target', event.nativeEvent.currentTarget)
}
```

通过之前的使用，可以得出

- React 将所有时间都挂载到 document 上
- event 不是原生的，是 SyntheticEvent 合成事件

React 自己实现了一套事件机制 —— 合成事件机制

- 事件的绑定和销毁
- 事件的触发和冒泡
- 和 DOM 事件不一样

React 事件机制的实现流程

- 示意图
- diapatchEvent
- JSX 渲染时，能知道每个事件和组件的关系，也就能触发到该组件的事件函数

为什么要这样做？

- 为了兼容性和跨平台（仅仅是将事件挂载到 document ，其他都不依赖于 DOM 事件，很独立）
- 挂载到 document ，减少内存消耗，方便事件绑定和解绑（不用再用 removeListener）
- 方便对事件的统一管理，如事务机制 —— 下文介绍

------

## setState 和 batchUpdate

根据之前对 setState 的应用，发现

- 有时异步，有时同步（不受 React 控制的函数中，是同步）
- 连续执行多次 setState ，只会更新一次（异步情况下）
- 传入对象时，会被合并

这部分过程非常复杂，如果从源码入手，反而不太容易讲清楚。另外，由于细节过于复杂，所以再难的面试也不可能考察到那么细致的源码。**所以，我们只需要了解这部分的流程和重点，应对面试应该没有问题**。

这部分的重要知识点：

- batchUpdate 机制
- transaction 机制

（解释什么是“事务”，例如数据库的事务操作。即将一组操作当做一个原子操作，例如银行转账）

```js
transaction.initialize = function () {
    console.log('initialize')
}
transaction.close = function () {
    console.log('close')
}

function method(){
    console.log('abc')
}
transaction.perform(method)

// 输出 'initialize'
// 输出 'abc'
// 输出 'close'
```

哪些场景会命中 batchUpdate 机制？

- 生命周期
- React 事件

哪些不会命中 batchUpdate 机制？

- setTimeout 等全局函数
- 自己定义的 DOM 事件

总结 setState 的特点

- 单独看 setState 本身，无所谓同步和异步
- 同步还是异步，取决于是否命中 batchUpdate 机制
- 通过事务机制，控制 isBatchingUpdates

------

## 组件更新和 diff 算法

回顾 vdom 的重点知识。

遍历 dirtyComponents 进行更新，组件更新依赖于 vdom 和 diff 算法。

- 根据 newProps 和 newState 执行 render 函数
- 生成 newVnode
- patch(vnode, newVnode) —— 这里并不是一步完成，React 会有更详细的优化，但最终结果和 patch 一样。

更新是分位两个阶段

- reconciliation 阶段。对 dirtyComponent 以及子组件进行 diff ，找出变化部分。这个阶段可以拆分为多个子任务，可以随时暂停和恢复。—— 至于为何要拆分，继续往下看。
- commit 阶段。对当前 diff 获取的变化部分，进行 DOM 操作。一次性执行完成，不能拆分。

暴露性能问题 —— **注意，是在某些复杂的情况下，你不一定能遇到！**

- JS 是单线程，而且和 DOM 渲染共用一个线程
- 当前项目复杂、组件数量多时，组件更新将占据大量 JS 计算
- 此时，如果再有其他的 DOM 渲染需求（如动画、频繁的鼠标键盘操作），将会导致卡顿

解决方案 —— fiber （React 16 之后引入 fiber 架构）

- 对 reconciliation 阶段进行任务拆分，可暂停，可恢复
- 当有 DOM 渲染需求时暂停，空闲时再恢复
- 如何判断浏览器空闲？—— window.requestIdleCallback https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestIdleCallback

注意，fiber 是 React 内部的运行机制，作为使用者体会不到，甚至有些情况都触发不到 fiber 机制。但是我们得知道它的基本情况：what why how


# 06-React原理\03-面试演练.md
# React 面试演练

前面提到

- 组件之间如何通讯
- JSX 本质是什么
- context 是什么，如何应用？
- shouldComponentUpdate 的用途
- redux 单向数据流过程
- setState 场景题

补充的

- 什么是纯函数？
- 组件生命周期
- React 发起 ajax 应该在哪个生命周期？
- 渲染列表时，为何用 key ？
- 函数组件和 class 组件的区别？
- 什么是受控组件？
- 何时将使用异步组件？
- 多个组件有公共的功能，如何抽离？
- setState 是同步还是异步？—— 场景题，代码如下
- redux 如何进行异步请求？
- react-router 如何异步加载？
- PureComponent 相比于普通组件有何不同
- React 事件和 DOM 事件有何不同？
- React 如何性能优化？

```js
// setState 同步还是异步？场景题
class Example extends React.Component {
  constructor() {
    super();
    this.state = {
      val: 0
    };
  }
  
  componentDidMount() {
    this.setState({val: this.state.val + 1});
    console.log(this.state.val);    // 第 1 次 log

    this.setState({val: this.state.val + 1});
    console.log(this.state.val);    // 第 2 次 log

    setTimeout(() => {
      this.setState({val: this.state.val + 1});
      console.log(this.state.val);  // 第 3 次 log

      this.setState({val: this.state.val + 1});
      console.log(this.state.val);  // 第 4 次 log
    }, 0);
  }

  render() {
    return null;
  }
};
```


# 06-React原理\04-react和vue的区别.md
# React 和 vue 区别

React 使用 jsx 去拥抱 js ，vue 使用模板去拥抱 html 。两个方向。

React 和 vue 做一个对比！！！细节一些
如 vue 的 slot 和 React 的 props.children
如 React 需要 SCU 优化，而 vue 就不需要，这是为何？
其他的再想，相同点 & 不同点


# 07-webpack\01-题目.md
# webpack 题目

webpack 面试题

- 前端代码为何要进行构架和打包？
- module chunk bundle 的区别
- loader 和 plugin 的区别
- 常用的 loader 和 plugin 有哪些
- webpack 性能优化（如上）
- webpack 构建流程简述
- 如何产出多页，如何产出 lib

babel 面试题

- babel 和 webpack 的区别
- babel-runtime 和 babel-polyfill 区别
- 为何 Proxy 无法 polyfill


# 07-webpack\02-基本应用.md
# webpack 基本应用

【注意】只过一遍知识点，不再详细代码演示了。

## 安装和配置 —— 拆分 dev prod 配置，然后 merge

- 安装 nodejs
- 初始化 `npm init -y`
- 安装插件 `npm i webpack webpack-cli webpack-merge --save-dev`

- 新建 `src` 及其测试 js 代码（包含 ES6 模块化）
- 创建配置文件
- 增加 `scripts` ，运行

- 安装 `npm i clean-webpack-plugin --save-dev`
- 配置 prod

## 本地服务和代理

- 新建 `index.html`
- 安装 `npm i html-webpack-plugin --save-dev` ，并配置
- 安装 `npm i webpack-dev-server --save-dev` ，并配置
- 修改 `scripts` 的 `dev` ，运行

## 处理 ES6

先引入简单的 babel ，polyfill 以后会单独讲

- 安装 `npm i @babel/core @babel/preset-env babel-loader --save-dev`
- 配置 webpack module
- 配置 `.babelrc`
- 运行 dev

## 处理样式

基本使用

- 安装 `npm i style-loader css-loader less-loader less --save-dev` （注意要安装 less）
- 配置 webpack module
- 新建 css less 文件，引入 index.js
- 运行 dev

postcss

- 安装 `npm i postcss-loader autoprefixer -D`
- 新建 `postcss.config.js`
- 配置  webpack module ，增加 `postcss-loader`
- 增加 css `transform: rotate(-45deg);`
- 运行 dev

## 处理图片

考虑 base64 格式

- 安装 `npm i file-loader url-loader --save-dev`
- 分别配置 webpack.dev 和 webpack.prod
- 新建图片文件，并引入到 js 中，插入页面
- 运行 dev
- 运行 build


# 07-webpack\03-高级应用.md
# webpack 高级应用

## 多入口

- 新建 `other.html` 和 `other.js`
- 修改 entry
- 修改 output
- 修改 HtmlWebpackPlugin

- 运行 dev
- 运行 build

## 抽离 & 压缩 css 文件

抽离

- 安装 `npm i mini-css-extract-plugin -D`
- 将之前 common 中的 css 处理，移动到 dev 配置中
- 配置 prod （配置 module ，配置 plugin）
- 运行 build

压缩

- 安装 `npm i terser-webpack-plugin optimize-css-assets-webpack-plugin -D`
- 配置 prod

## 抽离公共代码

- 配置 `splitChunks`
- 修改 HtmlWebpackPlugin 中的 chunks 。重要！！！
- 安装 lodash `npm i lodash --save` 做第三方模块的测试，引用 lodash
- 运行 build

## 懒加载

- 增加 `dynamic-data.js` 并动态引入
- 运行 dev 查看效果（看加载 js）
- 运行 build 看打包效果

至此，可以总结一下：

- module：就是js的模块化webpack支持commonJS、ES6等模块化规范，简单来说就是你通过import语句引入的代码。
- chunk: chunk是webpack根据功能拆分出来的，包含三种情况：
    - 你的项目入口（entry）
    - 通过import()动态引入的代码
    - 通过splitChunks拆分出来的代码
    - （chunk包含着module，可能是一对多也可能是一对一）
- bundle：bundle是webpack打包之后的各个文件，一般就是和chunk是一对一的关系，bundle就是对chunk进行编译压缩打包等处理之后的产出。

## 处理 React 和 vue

- vue-loader
- jsx 的编译，babel 已经支持，配置 `@babel/preset-react`

## 常见 loader 和 plugin

- https://www.webpackjs.com/loaders/
- https://www.webpackjs.com/plugins/


# 07-webpack\04-1-性能优化-part1.md
# webpack 性能优化

注意：

- 以下知识点不再一行一行演示
- 面试的时候也不会问到很细节
- 但不要死记硬背一个概念，一定要知道它的基本原理和配置方式

------

## 打包效率

### 优化 babel-loader

- babel-loader cache 未修改的不重新编译
- babel-loader include 明确范围

```js
{
    test: /\.js$/,
    use: ['babel-loader?cacheDirectory'], // 开启缓存
    include: path.resolve(__dirname, 'src'), // 明确范围
    // // 排除范围，include 和 exclude 两者选一个即可
    // exclude: path.resolve(__dirname, 'node_modules')
},
```

### IgnorePlugin 避免引入哪些模块

以常用的 moment 为例。安装 `npm i moment -d` 并且 `import moment from 'moment'` 之后，monent 默认将所有语言的 js 都加载进来，使得打包文件过大。可以通过 ignorePlugin 插件忽略 locale 下的语言文件，不打包进来。

```js
plugins: [
    // 忽略 moment 下的 /locale 目录
    new webpack.IgnorePlugin(/\.\/locale/, /moment/)
]
```

```js
import moment from 'moment'
import 'moment/locale/zh-cn' // 手动引入中文语言包
moment.locale('zh-cn')
```

### noParse 避免重复打包

`module.noParse` 配置项可以让 Webpack 忽略对部分没采用模块化的文件的递归解析处理，这样做的好处是能提高构建性能。 原因是一些库，例如 jQuery 、ChartJS， 它们庞大又没有采用模块化标准，让 Webpack 去解析这些文件耗时又没有意义。

```js
module.exports = {
  module: {
    // 独完整的 `react.min.js` 文件就没有采用模块化
    // 忽略对 `react.min.js` 文件的递归解析处理
    noParse: [/react\.min\.js$/],
  },
};
```

两者对比一下：

- `IgnorePlugin` 直接不引入，代码中不存在
- `noParse` 引入，但不再打包编译

### happyPack 多进程打包

【注意】大型项目，构建速度明显变慢时，作用才能明显。否则，反而会有副作用。

webpack 是基于 nodejs 运行，nodejs 是**单线程**的，happyPack 可以开启多个**进程**来进行构建，发挥多核 CPU 的优势。

```js
const path = require('path')
const HappyPack = require('happypack')

module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        // 把对 .js 文件的处理转交给 id 为 babel 的 HappyPack 实例
        use: ['happypack/loader?id=babel'],
        exclude: path.resolve(__dirname, 'node_modules')
      }
    ]
  },
  plugins: [
    new HappyPack({
      // 用唯一的标识符 id 来代表当前的 HappyPack 是用来处理一类特定的文件
      id: 'babel',
      // 如何处理 .js 文件，用法和 Loader 配置中一样
      loaders: ['babel-loader?cacheDirectory'],
      // ... 其它配置项
    })
  ]
}
```

### ParallelUglifyPlugin 多进程压缩 js

webpack 默认用内置的 uglifyJS 压缩 js 代码。
大型项目压缩 js 代码时，也可能会慢。可以开启多进程压缩，和 happyPack 同理。

```js
const path = require('path')
const ParallelUglifyPlugin = require('webpack-parallel-uglify-plugin')

module.exports = {
  plugins: [
    // 使用 ParallelUglifyPlugin 并行压缩输出的 JS 代码
    new ParallelUglifyPlugin({
      // 传递给 UglifyJS 的参数
      // （还是使用 UglifyJS 压缩，只不过帮助开启了多进程）
      uglifyJS: {
        output: {
          beautify: false, // 最紧凑的输出
          comments: false, // 删除所有的注释
        },
        compress: {
          // 在UglifyJs删除没有用到的代码时不输出警告
          warnings: false,
          // 删除所有的 `console` 语句，可以兼容ie浏览器
          drop_console: true,
          // 内嵌定义了但是只用到一次的变量
          collapse_vars: true,
          // 提取出出现多次但是没有定义成变量去引用的静态值
          reduce_vars: true,
        }
      },
    }),
  ],
};
```

### 自动刷新

watch 默认关闭。但 webpack-dev-server 和 webpack-dev-middleware 里 Watch 模式默认开启。

先验证下 webpack 是否能默认自动刷新页面 ？？？

```js
module.export = {
  watch: true, // 开启监听，默认为 false
  // 注意，开启监听之后，webpack-dev-server 会自动开启刷新浏览器！！！

  // 监听配置
  watchOptions: {
    ignored: /node_modules/, // 忽略哪些
    // 监听到变化发生后会等300ms再去执行动作，防止文件更新太快导致重新编译频率太高
    // 默认为 300ms
    aggregateTimeout: 300,
    // 判断文件是否发生变化是通过不停的去询问系统指定文件有没有变化实现的
    // 默认每隔1000毫秒询问一次
    poll: 1000
  }
}
```

### 热更新

上文的自动刷新，会刷新整个网页。

- 速度更慢
- 网页当前的状态会丢失，如 input 输入的文字，图片要重新加载，vuex 和 redux 中的数据

操作步骤

- 把现有的 watch 注释掉
- 增加以下代码
- 修改 css less 实验 —— 热替换生效
- 修改 js 实验 —— 热替换**不生效**

```js
const HotModuleReplacementPlugin = require('webpack/lib/HotModuleReplacementPlugin');

module.exports = {
  entry:{
    // 为每个入口都注入代理客户端
    index:[
        'webpack-dev-server/client?http://localhost:8080/',
        'webpack/hot/dev-server',
        path.join(srcPath, 'index.js')
    ],
    // other 先不改了
  },
  plugins: [
    // 该插件的作用就是实现模块热替换，实际上当启动时带上 `--hot` 参数，会注入该插件，生成 .hot-update.json 文件。
    new HotModuleReplacementPlugin(),
  ],
  devServer:{
    // 告诉 DevServer 要开启模块热替换模式
    hot: true,
  }  
};
```

js 热替换不生效，是因为我们要自己增加代码逻辑。

```js
// 增加，开启热更新之后的代码逻辑
if (module.hot) {
    module.hot.accept(['./math'], () => {
        const sumRes = sum(10, 20)
        console.log('sumRes in hot', sumRes)
    })
}
```

最后，热替换切勿用于 prod 环境！！！

### DllPlugin

Dll 动态链接库，其中可以包含给其他模块调用的函数和数据。

要给 Web 项目构建接入动态链接库的思想，需要完成以下事情：

- 把网页依赖的基础模块抽离出来，打包到一个个单独的动态链接库中去。一个动态链接库中可以包含多个模块。
- 当需要导入的模块存在于某个动态链接库中时，这个模块不能被再次被打包，而是去动态链接库中获取。
- 页面依赖的所有动态链接库需要被加载。

为什么给 Web 项目构建接入动态链接库的思想后，会大大提升构建速度呢？

- 前端依赖于第三方库 `vue` `react` 等
- 其特点是：体积大，构建速度慢，版本升级慢
- 同一个版本，只需要编译一次，之后直接引用即可 —— 不用每次重复构建，提高构建速度

Webpack 已经内置了对动态链接库的支持，需要通过2个内置的插件接入，它们分别是：

- DllPlugin 插件：打包出 dll 文件
- DllReferencePlugin 插件：使用 dll 文件

打包出 dll 的过程

- 增加 webpack.dll.js
- 修改 package.json scripts `"dll": "webpack --config build/webpack.dll.js"`
- `npm run dll` 并查看输出结果

使用 dll

- 引入 `DllReferencePlugin`
- babel-loader 中排除 `node_modules`
- 配置 `new DllReferencePlugin({...})`
- index.html 中引入 `react.dll.js`
- 运行 dev

### 总结 - 提高构建效率的方法

哪些可用于线上，哪些用于线下

- 优化 babel-loader（可用于线上）
- IgnorePlugin 避免引入哪些模块（可用于线上）
- noParse 避免重复打包（可用于线上）
- happyPack 多进程打包（可用于线上）
- ParallelUglifyPlugin 多进程压缩 js（可用于线上）
- 自动刷新（仅开发环境）
- 热更新（仅开发环境）
- DllPlugin（仅开发环境）



# 07-webpack\04-2-性能优化-part2.md
# webpack 性能优化

## 产出代码优化

### 使用 production

- 开启压缩代码
- 开启 tree shaking（必须是 ES6 Module 语法才行）

ES6 Module 和 commonjs 的区别

- ES6 Module 是静态引入，编译时引入
- commonjs 是动态引入，执行时引入

```js
// commonjs
let apiList = require('../config/api.js')
if (isDev) {
    // 可以动态引入，执行时引入
    apiList = require('../config/api_dev.js')
}
```

```js
import apiList from '../config/api.js'
if (isDev) {
    // 编译时报错，只能静态引入
    import apiList from '../config/api_dev.js'
}
```

### 小图片 base64 编码

### bundle 加 hash

### 使用 CDN

配置 publicPath

### 提取公共改代码

### 懒加载

### scope hosting 将 module 合并到一个函数中

使用前后的对比，使用的好处

配置如下

```js
const ModuleConcatenationPlugin = require('webpack/lib/optimize/ModuleConcatenationPlugin')

module.exports = {
  resolve: {
    // 针对 Npm 中的第三方模块优先采用 jsnext:main 中指向的 ES6 模块化语法的文件
    mainFields: ['jsnext:main', 'browser', 'main']
  },
  plugins: [
    // 开启 Scope Hoisting
    new ModuleConcatenationPlugin(),
  ]
}
```

同时，考虑到 Scope Hoisting 依赖源码需采用 ES6 模块化语法，还需要配置 `mainFields`。因为大部分 Npm 中的第三方库采用了 CommonJS 语法，但部分库会同时提供 ES6 模块化的代码，为了充分发挥 Scope Hoisting 的作用。


# 07-webpack\05-原理和二次开发.md
# webpack 原理和二次开发

这部分是面试的加分项，大家不要深究细节。即便面试被问到，实际工作中应用的概率也非常小。
webpack 本身就是一个工具，只是用来打包构建。而且发展多年已经成熟完善，日常的开发场景都能满足。

------

## webpack 构建流程

几个核心概念

- Entry：入口，Webpack 执行构建的第一步将从 Entry 开始，可抽象成输入。
- Module：模块，在 Webpack 里一切皆模块，一个模块对应着一个文件。Webpack 会从配置的 Entry 开始递归找出所有依赖的模块。
- Chunk：代码块，一个 Chunk 由多个模块组合而成，用于代码合并与分割。
- Loader：模块转换器，用于把模块原内容按照需求转换成新内容。
- Plugin：扩展插件，在 Webpack 构建流程中的特定时机会广播出对应的事件，插件可以监听这些事件的发生，在特定时机做对应的事情。

Webpack 的构建流程可以分为以下三大阶段：

- 初始化：启动构建，读取与合并配置参数，加载 Plugin，实例化 Compiler。
- 编译：从 Entry 发出，针对每个 Module 串行调用对应的 Loader 去翻译文件内容，再找到该 Module 依赖的 Module，递归地进行编译处理。
- 输出：对编译后的 Module 组合成 Chunk，把 Chunk 转换成文件，输出到文件系统。

------

## 开发 loader

以 `less-loader` 为例，回顾一下使用规则

```js
{
    test: /\.less$/,
    // 注意顺序
    loader: ['style-loader', 'css-loader', 'less-loader']
}
```

所以，loader 的作用：

- 一个代码转换器，将 less 代码转换为 css 代码
- 再例如 vue-template-compiler
- 再例如 babel 编译 jsx

所以一个 loader 的基本开发模式：

```js
const less = require('node-less')
module.exports = function(source) {
  // source 即 less 代码，需要返回 css 代码
  return less(source)
}
```

以上是 loader 的基本开发方式，实际开发中可能还会有更多要求

- 支持 options ，如 `url-loader` 的使用
- 支持异步 loader
- 缓存策略

```js
// options
const loaderUtils = require('loader-utils')
module.exports = function(source) {
  // 获取 loader 的 options
  const options = loaderUtils.getOptions(this)
  return source // 示例，直接返回 source 了
}
```

```js
// 异步 loader
module.exports = function(source) {
    // 使用异步 loader
    const callback = this.async()
    // 执行异步函数，如读取文件
    someAsyncFn(source, function(err, result, sourceMaps, ast) {
        // 通过 callback 返回异步执行后的结果
        callback(err, result, sourceMaps, ast)
    })
}
```

```js
// 缓存
module.exports = function(source) {
  // 关闭该 Loader 的缓存功能（webpack 默认开启缓存）
  this.cacheable(false)
  return source
}
```


# 07-webpack\06-babel.md
# babel

本节主要解决以下问题，相信很多同学都很懵

- babel-polyfill —— **7.4 之后弃用，推荐直接使用 corejs 和 regenerator ？？**
- babel-runtime

## 初始化环境

- 安装 babel 插件 `npm i @babel/cli @babel/core @babel/preset-env -D`
- 新建 `.babelrc`，配置 preset-env
- 新建 `src/index.js` ，写一个箭头函数
- 运行 `npx babel src/index.js` ，看结果

## 使用 polyfill

什么是 babel-polyfill

- 什么是 polyfill ？—— 即一个补丁，引入以兼容新 API（注意**不是新语法**，如箭头函数），如搜索“Object.keys polyfill” 和 “Promise polyfill”
- core-js 集合了所有新 API 的 polyfill 。https://github.com/zloirock/core-js
- regenerator 是 generator 的 polyfill 。 https://github.com/facebook/regenerator
- babel-polyfill 即 core-js 和 regenerator 的集合，它只做了一层封装而已。

基本使用

- `src/index.js` 中写一个 Promise，打包看结果
- `npm install --save @babel/polyfill` 【注意】要 `--save`
- 然后引入 `import '@babel/polyfill'`
- 再打包，看结果
    - 解释：babel 仅仅是处理 ES6 语法，并不关心模模块化的事情。模块化归 webpack 管理
    - 全部引入 polyfill ，体积很大

按需加载

- 新增 `"useBuiltIns": "usage"` （注意要改写 preset 的 json 结构）
- 删掉入口的 `import '@babel/polyfill'`
- 再打包，看结果
    - 提示选择 core-js 的版本，增加 `"corejs": 3`
    - 只引入了 promise 的 polyfill

## 使用 runtime

babel-polyfill 的问题 —— 会污染全局变量

- 如果是一个网站或者系统，无碍
- 如果是做一个第三方工具，给其他系统使用，则会有问题
- 不能保证其他系统会用 Promise 和 includes 做什么，即便他们用错了，那你也不能偷偷的给更改了

```js
// 源代码
Promise.resolve(100).then(data => data);
[10, 20, 30].includes(20);

// 结果 —— 可以看到，Promise 和 includes 都未改动，因为以注入全局变量了
"use strict";
require("core-js/modules/es.array.includes.js");
require("core-js/modules/es.object.to-string.js");
require("core-js/modules/es.promise.js");

Promise.resolve(100).then(function (data) {
  return data;
});
[10, 20, 30].includes(20);
```

使用 babel-runtime

- `npm install --save-dev @babel/plugin-transform-runtime`
- `npm install --save @babel/runtime`，注意是 `--save`
- 配置 `"plugins": ["@babel/plugin-transform-runtime"]`
    - 其中 `"corejs": 3,` v3 支持 API 如数组 includes ，v2.x 不支持
- 删掉 `"useBuiltIns": "usage"`
- 运行代码

## 总结

- babel-polyfill 是什么，core-js 是什么
- babel-polyfill 按需加载的配置
- babel-polyfill 和 babel-runtime 的不同应用场景


# 08-组件设计\01-题目.md
# 组件设计 - 题目

- todo-list 设计
- 购物车设计

------

组件设计也是面试考察的重点，毕竟招聘进来是要做项目的，而做项目就少不了做技术方案设计。
所以，如果面试过程中遇到问设计的问题，你应该很庆幸，他们不是在招一个纯搬砖的，至少有设计工作。
反过来说，如果你不懂设计，那基本也就只能做一个纯搬砖的码农。

- 组件拆分
- 组件间的数据传递
- 状态数据设计


# 08-组件设计\02-todo-list设计.md
# todo list 设计

## 简单的（常考）

- 画原型图
- 组件设计
- 数据结构设计

代码参考 `react-demo` 中 `baseUse/PropsDemo` ，只是需要再把 Item 组件单独拆分一下。

## 复杂的，结合状态管理

回顾之前 `react-demo` 中 `reduxUse` 的代码，以及系统演示

可以先不看 Footer 过滤功能

- 运行演示功能
- 查看代码文件结构
- `app.js`
- `reducers`
    - `todos.js`
    - `visibilityFilter.js`
- `actions/index.js`
- `components/App.js` - 查看组件结构
- `containers/AddTodo.js`
- `containers/VisibleTodoList.js`
- `components/TodoList`
- `components/Footer.js`
- `containers/FilterLink.js`
- `components/Link`
- 总结：组件拆分，数据结构，数据操作（actions reducer 等）


# 08-组件设计\03-购物车设计.md
# 购物车组件设计

简单版本的 —— 不再代码演示了，只做一下分析：

- 画原型图（结合外卖 app 的订单界面，考虑每个商品的数量）
- 组件设计
- 数据结构设计

复杂版本的，代码示例 `~/Learn/vuex/example/shopping-cart` （vuex 中的 example）

可以先不看**结算**功能

- 先把 demo 运行起来，看看效果
- 看代码结构 `app.js` `components` `api`
- `app.js`
- `api/shop.js`
- `store/modules/products.js`
- `store/modules/cart.js`
- `components/App.vue` - 查看组件结构
- `components/ProductList.vue`
- `components/ShoppingCart.vue`
- 总结：组件拆分，数据结构，数据操作（actions mutations）


# 08-组件设计\04-总结.md
# 组件设计 总结

为何面试要考察组件设计？
如何拆分组件、组件通讯？
如何定义数据结构？


# 09-项目流程\01-start.md
# 项目流程

正统的软件开发流程中，编码只占用 1/6 的时间，所以程序猿上班工作并不仅仅是编码。

先出几个题目，引导思考

- PM 在项目过程中想新增需求，怎么办？
- 项目即将延期了，该怎么办？
- 你将如何保证项目质量？

## 什么是项目流程

- 项目分多人员、多角色参与
- 项目分多阶段
- 把项目从无到有按照计划做出来的过程

标准、规范的项目流程，一般都在中大型公司中实行。小公司，或者学校组织的开发团队，一般都不会规范且完整。
这也是大厂出来的人，有竞争力的原因。

## 面试为何会考察项目流程

- 确定你真正参与过实际项目（而不仅仅是个人项目、毕业设计等）
- 确定你能真正解决项目中的常见问题
- 看你是否能独立承担一个项目？—— 对应工作经验比较多的候选人

## 考察方式

- 第一，根据你简历中的项目经历，提问问题
    - 先了解你的项目经历（项目多少人？如何与后端协作？项目 pv qps 多少？项目提测流程 ……）
    - 再了解过程中去顺带着提问
- 第二，直接提问

## 讲解过程

- 一个项目的全流程
- 其中会遇到的问题


# 09-项目流程\02-项目流程.md
# 项目流程

完成流程参考 参考 https://www.imooc.com/article/289377

会遇到的各个项目角色

- PM 产品经理 - 提需求，一般也是项目的推动者
- FE 前端开发
- RD 后端开发
- CRD 客户端开发
- UE 视觉设计师 - 切图仔
- QA 测试
- OP 运维人员 - 管理服务器的

## 需求分析

- 了解项目背景，即为啥要做这件事儿，解决的问题是什么。别一上来就说功能
- 需求是否合理？从用户角度来考虑
- 需求是否闭环（如缺少统计）
- 是否可实现？（如在 h5 中做点赞的动画）—— 此时应该建议修改续期，而不是硬撑着做
- 是否需要其他支持？如图片放大需要客户端支持，用户信息可能需要服务端支持。
- 不要着急给出排期，一般话术是：“今天下班之前给排期”

## 技术方案设计

在此回顾一下之前讲的“组件设计”

- 尽量以最简单的设计来解决问题，不要为了设计而设计
- 要写出设计文档，画图、写伪代码。—— 不要觉得写文档很麻烦，它是检验你是否真正理解的一个过程
    - 如果你真理解了，写文档画图不会花费你过多时间；
    - 如果你不理解，那你写不出文档，到时候你也一定写不出代码。
- 前端设计的重点：组件设计、数据结构设计、接口设计
- 要通过全组评审，或者你的导师、组内高工评审。
    - 第一，他们技术好、工作经验丰富能看出你设计的是否合理，是否有破坏性，是否可扩展，是否有性能问题、安全问题、或者其他坑；
    - 第二，他们对公司环境熟悉，知道公司中很多线程的工具，有些你可以直接用。
- 要和服务端、客户端对好接口和调用协议，确定好联调时间，以邮件的形式发出来，抄送他们的领导。

## 开发

反馈排期

- 预留 buffer ，应对风险
- 考虑自己是否有并行的其他工作
- 关注 UE RD CRD 的排期 —— 大家协作，可能会因为上游、或协同人员的延期，而导致你延期

开发规范

- git 规范：分支规范、commit 规范
- 注释规范 jsdoc ，注释是代码的一部分
- 及时写开发文档 README.md ，文档是代码的一部分 —— 例如你做了一个公共的 API 或者 UI 模块，写清楚如何调用、注意事项等。

单元测试

- 代码和单测并行，单测是代码的一部分 —— 前端开发，不用要求对所有部分写单测（例如 UI 写单测挺麻烦的），但是一些公用的方法和函数，还是要有的
- 及时开发，及时单测
- 常用工具 jest ，以及 React vue 的单测

mock API

- 此时，服务端在还开发中，没有后端接口
- 需要自己构建假数据，模拟后端接口
- webpack proxy 或 mockjs

及时 cr code review

- 将 cr 归入研发流程
- cr 的内容 merge request
- cr 必须留有记录

## 联调

- 后端、客户端联调
- 视觉联调 —— 这一步很麻烦，UE 的像素眼可能会给你调出很多问题，特别是不同尺寸的手机上
- 产品确认 —— 这一步特别重要！！！确定最后做出来的产品，一定是 PM 需要的，否则就不能提测。

此时 PM 可能还会让你加需求，怎么办？？？

- 不能拒绝（你也无权拒绝），走需求变更流程
- 如果公司有现成的流程，则按照这个来
- 如果没有，可以发邮件或开发周知项目组和 leader （重要！！！），重新评估技术方案和排期

## 测试

“我这里没问题呀！” —— 自己复现不了，怎么办？

- 不要说这句话！！！—— 显得自己很不会沟通
- 当面讨论，让 QA 帮你复现问题 —— 如果是偶尔复现的，就尝试找一找必然复现的路径
- 如果需要特定设备才能复现，则让 QA 提供设备 —— 总之，要抱着一起解决问题的心态，而不是推卸

## 上线

暂无问题，每个公司的上线流程都不一样

## 回滚（如果需要）

- 遇到问题先回滚，止损，再排查
- 回滚之后，要立刻周知 PM 和项目组
- 解决之后，记得写复盘报告 —— 无论公司有没有规定，对自己的总结和反省，是进步的最好方式

## 沟通和变更

- 每日站会，周会 —— PM 或者项目经理组织
- 有问题（如要延期）及时汇报
- 如上游或写同人导致的延期，也要及时汇报 —— 但说话不要用甩锅的语气，就事论事即可

## 项目总结

- 项目结束之后，要记得写个总结
- 总结项目遇到的各种问题和风险，以及解决方案
- 总结自己做下来的感想


# 10-升级-React-Hooks\01-题目.md
# 题目

- 为什么要使用 React Hooks？解决了什么问题
- React Hooks 如何模拟组件生命周期
- 如何自定义 Hook
- React Hooks 性能优化
- React Hooks 有哪些坑？ —— 看你是否在实战中用过 Hooks ，还是仅仅看了一些文档

------

React Hooks v16.8 发布的新 API

- 完全可选的（class 组件 vs Hooks）
- 100% 向后兼容（Hooks 不包含任何破坏性改动，只是新功能的增加）
- 不会取代 class 组件 （React 也从没有计划要移除 class 组件）

因此，面试官如果要问 React 面试题，只会拿出一部分时间问 Hooks 。
所以对于 React 初学者，还是以学习 React class 组件和基本使用为主，不用过多学 Hooks 。
熟悉了 React class 组件和基本使用之后，再来学习 Hooks 。

即，Hooks 是 React 的加分项，要考虑好轻重。

（列一下本章学习的所有知识点）


# 10-升级-React-Hooks\02-认识Hooks.md
# 认识 Hooks

为了照顾对 Hooks 不了解的同学，我们先来花点时间认识一下 React Hooks

先不要管 Hooks 的动机，即为何要使用。等学会了基本使用之后，后面再讲，现在讲估计也效果不好。

## 回顾函数组件

函数组件没有实例，也不能监听各个生命周期，也无法扩展属性和方法。只是输入 props ，输出 jsx ，纯函数。
也没有 state

```js
// class 组件
class List extends React.Component {
    constructor(props) {
        super(props)
    }
    render() {
        const { list } = this.props

        return <ul>{list.map((item, index) => {
            return <li key={item.id}>
                <span>{item.title}</span>
            </li>
        })}</ul>
    }
}

// 函数组件
function List(props) {
    const { list } = this.props

    return <ul>{list.map((item, index) => {
        return <li key={item.id}>
            <span>{item.title}</span>
        </li>
    })}</ul>
}
```

## class 组件 vs 函数组件

class 组件有如下问题

- 大型组件很难拆分和重构，也很难测试。
- 业务逻辑分散在组件的各个方法之中，导致重复逻辑或关联逻辑。
- 组件类引入了复杂的编程模式，比如 render props 和高阶组件。

按照 React 函数式编程的思维来说，一个组件更像一个函数，而不像一个 class ，即 `view = fn(props)`
所以，函数组件会看起来更简洁、符合逻辑。

但函数组件没有 state ，没有生命周期，还无法取代 class 组件。所以，才有了 React Hooks 。

## state hook

函数组件，要求必需是**纯函数**，不能有副作用。因此，要在函数组件使用 state ，不能直接使用，而是要“钩”进来，这就是 Hooks

那如何把 state “钩”到函数组件呢？ —— `ClickCounter.js` 代码演示
（可以再对比一下 `ClickCounterClass.js` ，体会和 class 组件的区别）

代码总结

- useState(0) 传入初始值，返回一个数组
- 数组第一个元素，state 值
- 数组第二个元素，setState 函数

注意命名规范

- 规定所有 Hook 命名必须是 use 开头，如 useXxx
- 自定义的 Hook ，也要 use 开头
- 其他地方，不要乱用 useXxx 名字

## effect hook

有了 state 之后，还差一个常用的功能 —— 组件声明周期。例如，组件经常会在 didMount 里发请求

`LifeCycles.js` 代码演示

- 模拟 ComponentDidMount
- 模拟 ComponentDidUpdate
- 模拟 ComponentWillUnMount

effect 实现的是**副作用**，解释一下这个词

- 纯函数，输入参数，返回结果，不应该有副作用
- 副作用：对函数之外的干扰，如设置一个定时任务
- 而组件却需要副作用，所以用 effect hook 实现

继续讲一个知识点，其实上述“模拟 ComponentWillUnMount” 和 class 组件的 WillUnMount 还不一样。
以一个“监听好友在线状态”的组件为例子说明 —— `FriendStatusClass.js` 和 `FriendStatus.js` ，对比着看。

- 先用 class 组件演示，光有 WillUnmount 满足不了需求，需要结合 Update 声明周期
- 而用 effect Hook 一步就可以解决问题
- 所以这里的 “模拟 ComponentWillUnMount” 和 class 组件的 WillUnMount 不一样

## 小结

有了 state ，有了最基本的 3 个生命周期，日常见的功能也就都能做了


# 10-升级-React-Hooks\03-其他Hooks.md
# 其他 Hooks

下面这些 hooks 优先级并不高，不是那么常用。但是你至少要知道它是干嘛的，以便后面用到时再详细查询。
所以，下面我们就依次看看，这些 hooks 的介绍和基本使用，做一个大概的了解即可。

## useRef

可用于获取 DOM 元素，参考 `UseRefDemo.js` 中的代码

## useContext

（先回顾一下之前的 Context 知识，借用之前 ppt 和源码）

Hooks 中使用 `useContext` 来获取 context 的值

参考 `UseContextDemo.js` 代码。

## useReducer

（先回顾一下 redux 的流程，和各个概念）

参考 `UseReducerDemo.js` 代码

useReducer 和 redux 不同

- useReducer 是 useState 的代替方案，用于更复杂的 state 变化逻辑
- useReducer 还是单组件的状态管理，多组件通讯还是需要 props 传递数据
- redux 是全局的状态管理，多组件可共享数据

## useMemo

（先回顾一下之前的性能优化部分的知识，借用之前 ppt 和源码）

- React 默认更新所有子组件
- Class 组件使用 SCU 或者 PureComponent 进行优化
- Hooks 里使用 useMemo（但道理是一样的）

参考 `UseMemoDemo.js` 代码演示

## useCallback

在 useMemo 的基础上继续，如果是函数传递给子组件，怎么办？

- useMemo 封装数据
- useCallback 封装函数

参考 `UseCallbackDemo.js` 代码演示


# 10-升级-React-Hooks\04-自定义Hook.md
# 自定义 Hook

实际开发中，一些公共的功能，需要自己封装起来，这就是自定义 Hook 。
接下来，借用 axios 封装一个自定义 Hook —— useAxios 。

首先，要安装 axios `npm i axios --save`

代码参考 `customHooks/useAxios.js`（注意，名字以 `use` 开头，重要！！！）
和 `CustomHookUsage.js` 组件

总结一下

- 本质是一个函数
- 文件名称以 use 开头，重要！
- 内部正常使用 useState useEffect
- 返回想要的结果即可

------

最后，有很多第三方的 hook 可以直接使用
如 https://nikgraf.github.io/react-hooks/
再如 https://github.com/umijs/hooks


# 10-升级-React-Hooks\05-Hooks使用规范.md
# Hooks 使用规范

已经初步认识了 React Hooks ，在继续深入学习之前，我们要说两个重要的规范。请大家一定要遵守。

## 规则

- 只在代码最顶层使用 Hook ，不要在循环、判断和嵌套函数中使用。（以及不要在 Hook 之前 return 掉）
- 只在 React 函数组件，或自定义 Hook 中使用
    - 不在 class 组件中使用
    - 不在普通函数中使用
- eslint 插件 eslint-plugin-react-hooks 可以帮你解决以上问题

安装 `npm install eslint-plugin-react-hooks --save-dev` ，然后修改 eslint 配置文件

```json
// ESLint 配置文件
{
  "plugins": [
    // ...此处省略 N 行...
    "react-hooks"
  ],
  "rules": {
    // ...此处省略 N 行...
    "react-hooks/rules-of-hooks": "error", // 检查 Hook 的规则
    "react-hooks/exhaustive-deps": "warn" // 检查 effect 的依赖
  }
}
```

## 关于 Hook 的调用顺序

第二条规则应该不难理解：Hooks 就是给 React 函数组件使用的，不能用在其他地方。

- 是一个函数
- import React from 'react' （普通函数，编译时不用引入 React ，也就不具备 Hooks 功能）
- 返回 JSX

那么第一条规则，为何必须放在顶层？我们需要一探究竟。如果面试时候问到，你也能从容作答。
（参考 `Teach.js` 代码演示）

- 无论 render 和 re-render ，所有 Hook （包括 useState useEffect 还有其他）都必须保证顺序一致，才能对应起来
- 如果某一个 Hook 出现在判断或者循环中，则无法保证顺序一致 （此处可代码展示一下，但不能运行）
- React Hook 严重依赖于 Hook 的调用顺序！重要！！！


# 10-升级-React-Hooks\06-Hooks组件逻辑复用.md
# Hooks 组件逻辑复用

------

## 回顾之前 class 组件的逻辑复用

### mixin 已被废弃

相互依赖，相互耦合

- 变量作用域不明确
- 属性重名
- mixin 过多时的顺序冲突问题

### 高阶组件 HOC

（回顾之前的 ppt 和代码）

HOC 的缺点：

- 使用多了，导致组件层级嵌套过多，不易渲染，更不易调试
- HOC 可以劫持 props ，需要严格遵守约定 （即，如果 HOC 没传或者传错了 props ，将会给子组件带来很大困扰）

### render props

（回顾之前的 ppt 和代码）

缺点：

- 有一定学习和理解成本 （这种方式，感觉很绕，并不是那么直白，而且一不小心就忘）
- 只能传函数组件 （而函数组件如果没有 hooks ，功能有限）

------

## 使用 Hooks 做组件逻辑复用

无论是 mixin HOC 还是 render prop ，他们不是完美的解决方案，多少都会有一些令人费解或者困惑的地方。

其实用 Hooks 做组件逻辑复用，本质上就是自定义 Hook 。可先回顾自定义 Hook 的内容。

再对比之前的 HOC 和 render prop ，自定义 Hook 做一个鼠标位置的 demo 。参考 `useMousePosition.js` 代码。

- 完全符合自定义 Hook 规则，没有其他要求，很好理解和记忆
- 变量作用域非常明确
- 不会产生组件嵌套

（Vue3 Composition API 也是参照 Hooks 来设计的）


# 10-升级-React-Hooks\07-Hooks注意事项.md
# React Hooks 的坑

## useState 的值，只有第一次有效

useState 初始化值

- 只在 render 时执行
- re-render 时不会重新初始化
- 只能通过 setState 来修改

参考 `UseStateTrap.js` 代码

## useEffect 内部不能修改 state

useEffect 里面使用到的 state 的值, 固定在了 useEffect 内部， 不会被改变，除非 useEffect 刷新，重新固定state的值

参考 `UseEffectChangeState.js`

## useEffect 死循环

如果依赖项（即第二个参数）里有对象、数组，就会出现死循环。所以，依赖项里都要是值类型。
可以用 useAxios 进行演示，加一个 config 依赖项

因为 React Hooks 是通过 `Object.is` 进行依赖项的前后比较。
如果是值类型，则不妨碍。
如果是引用类型，前后的值是不一样的（纯函数，每次新建值），就类似 `{x:100} !== {x:100}`


# 10-升级-React-Hooks\08-答题.md
# 答题

（可以先回顾一下本章学习的所有知识点）

- 为什么要使用 React Hooks？解决了什么问题
- React Hooks 如何模拟组件生命周期
- 如何自定义 Hook
- React Hooks 性能优化
- React Hooks 有哪些坑？

## 为何要使用 Hooks

- 组件公共逻辑复用，Hooks 更好
- 完善函数组件的能力（class 写组件是一个很费解的事情，以及 class 里的 this 也是初学者捉摸不透）
- class 复杂组件正在变的难以理解

class 组件变的复杂是，相同的逻辑，分散到各个地方：

- DidMount 和 DidUpdate 中获取数据
- DidMount 绑定事件， WillUnMount 解绑
- 使用 Hooks ，可以把相同逻辑放在一个 useEffect 中 （这样就按照逻辑拆分出一个一个的小模块，甚至是一个一个自定义的 Hook）

## React Hooks 如何模拟组件生命周期

主要的几个生命周期

- ComponentDidMount - useEffect 依赖是 []
- ComponentDidUpdate - useEffect 依赖是 [a, b]
- ComponentDid - useEffect 返回一个函数

## 如何自定义 Hook

参考之前 ppt

## React Hooks 性能优化

- useMemo 缓存数据
- useCallback 缓存函数
- 配合 memo（相当于 SCU 和 PureComponent）

## React Hooks 有哪些坑

看你是否在实战中用过 Hooks ，还是仅仅看了一些文档

- useState 的值，只有第一次有效
- useEffect 内部不能修改 state
- useEffect 死循环

【注意】坑可能还有其他的很多，但你说出这三个，至少证明你只真正用过 Hooks 的，面试官也不会过于为难你


# 11-升级Vue3.0\00-开始.md
# 开始

学 vue2 之前，先加一节视频
- 明确范围：第 3 4 5 章是讲解 vue2 的，第 6 章是讲解 vue3 的。但请一定不要跳过 vue2 直接看 vue3 ，因为两者有前后的继承关系。
- vue2 并不会立马过时，面试肯定会继续考察
- vue2 的语法，绝大部分都可继续在 vue3 中使用。vue3 的升级是很平滑的。如果不适应，我们会在视频中单独指出来。所以，放心学。



**熟悉 vue2 的，可以选择跳过**

React 从 class 到 Hooks ，Vue 从 Option API 到 Composition API。
这都是**面向对象**向**函数式编程**的一个转变，方向是统一的。
说明，面向对象思维，已经无法满足当前前端开发的需求。而需要更加灵活的模式。—— 这里可以好好思考一下，看怎么讲解？？？

不要再就纠结哪个好，哪个不好\
（技术永远都是为业务服务的，低成本、稳定、易维护的技术方案就是最优解，大家不要做技术的奴隶、框架的奴隶）

---

现有第 6 章，全部放 vue3 的内容

删掉 6-1

6-2 6-3 6-4 可以回答 vue3 的响应式原理


# 11-升级Vue3.0\01-题目.md
# 题目

- Vue3.0 比 Vue2.x 的优势 —— 即，设计初衷
- Vue3.0 生命周期
- 你如何看待 Composition API 和 Options API
- 如何理解 `ref` `toRef` `toRefs`
- Vue3.0 有哪些重要的新功能
- Composition API 如何实现代码逻辑复用
- Vue3.0 如何实现响应式？
- watch 和 watchEffect 的区别
- setup 中如何获取组件实例？
- Vue3.0 为什么这么快？
- Vite 是什么？
- 和 React Hooks 对比

注意事项
- 不是从 0 入门，所以要去看一看 vue3 的文档


# 11-升级Vue3.0\02-解答-1.md
# 解答-1

## Vue3.0 比 Vue2.x 的优势

- 性能更好
- 体积更小
- 更好的 ts 支持
- 更好的代码组织
- 利于复杂逻辑抽离 - Composition API
- 增加了新功能 `Fragment` `Teleport` `Suspense`

虽然有很多更具体的数据，但不用可以去记录这些数据，跟我们日常开发也没有太多关系，了解即可。

![](./img/性能提升.png)

## Vue3.0 生命周期

v2.x 的生命周期依然支持，需要注意的是：
- beforeDestroy 改名为 beforeUnmount
- destroyed 改名为 unmounted

新的 Composition API 有了新的生命周期。

看代码演示。

## 你如何看待 Composition API 和 Options API

Composition API 是 vue3 的重要更新，也是使用者们最关注的部分。
- 更好的代码组织
- 更好的逻辑复用 —— 这是两码事儿，后者依赖于前者
- 更好的类型推导

### 代码组织参考例子
- 实际的代码例子
    - v2 https://github.com/vuejs/vue-cli/blob/a09407dd5b9f18ace7501ddb603b95e31d6d93c0/packages/@vue/cli-ui/src/components/folder/FolderExplorer.vue#L198-L404
    - v3 这里有 https://vue-composition-api-rfc.netlify.app/zh/#%E4%BB%A3%E7%A0%81%E7%BB%84%E7%BB%87

### 关于 vue2 中的类型推导
- vue2 中的 this 的方式是比较微妙的。（比如 methods 选项下的函数的 this 是指向组件实例的，而不是这个 methods 对象）
- vue2 设计时，是没有考虑 ts 的类型推导的

### Composition API 和 Options API 如何选择？？
- 不建议共用，会很混乱
- 普通情况下（之前用 vue2.x 也觉得挺好），建议还是继续用 Options API
- 如果系统复杂度比较高，则考虑使用 Composition API ，毕竟需要抽离很多逻辑

### 关于 Composition API 的误解，重要！！！
- 从 vue3 的文档来看，Composition API 隐藏很深，在“高阶指南”里。如果从 0 学习 vue3 你是不太容易接触到它的，普通场景下你甚至都用不到它。它属于一个附加或者高级的额功能。所以，不要把它看的那么重要。
- vue3 也支持 vue2 的 options API ，而且入门文档就是用的 Options API 。这其实就跟 React 的 class 组件和 Hooks 一样了。所以，Composition API 就像是 React Hooks ，是可选的，是为了解决特殊问题的，而不是必须的。


# 11-升级Vue3.0\03-解答-2.md
# 解答-2

## 如何理解 `ref` `toRef` `toRefs`

细节的知识点，在整个 Composition API 中算是比较难理解的。
甚至出现了 ref sugar 的讨论。

ref 和 reactive 结合起来使用，更是难以理解。
既然有 reactive ，为何还要 ref 呢？？？

https://v3.cn.vuejs.org/api/refs-api.html

### ref

创建响应式对象一般用 reactive

第一，响应式 （代码参考 `RefBasic.vue`）
- 生成值类型的响应式数据
- 可直接用于模板和 reactive
- 可通过 `.value` 修改值

第二，模板引用（代码参考 `RefTemplate.vue`）

### toRef

代码参考 `ToRef.vue`

可以用来为源响应式对象上的 property 新创建一个 ref。然后可以将 ref 传递出去，从而保持对其源 property 的响应式连接。

- 针对一个**响应式对象**的 property
- 创建一个 ref 具有响应式
- 保持**引用**关系

【注意】必须是响应式对象，普通对象不具有响应式。

### toRefs

代码参考 `ToRefs.vue`

将响应式对象转换为普通对象，其中结果对象的每个 property 都是指向原始对象相应 property 的 ref 。

- 将**响应式对象**转换为普通对象 obj
- obj 的每个属性都是对应的 ref
- 保持**引用**关系

【注意】必须是响应式对象，普通对象不具有响应式。


当从合成函数返回响应式对象时，toRefs 非常有用。
这样消费组件就可以在不丢失响应性的情况下对返回的对象进行分解/扩散：

```js
function useFeatureX() {
  const state = reactive({
    x: 1,
    y: 2
  })

  // 逻辑运行状态，省略 N 行

  // 返回时转换为ref
  return toRefs(state)
}

export default {
  setup() {
    // 可以在不失去响应性的情况下破坏结构
    const { x, y } = useFeatureX()

    return {
      x,
      y
    }
  }
}
```

### ref 和 reactive

既然有 reactive ，为何还要 ref 呢？

- 返回值类型，会丢失响应式
- 如在 setup、computed、合成函数，都有可能返回值类型
- Vue 如不定义 ref ，用户将自造 ref ，反而混乱

代码参考 `ref/WhyRef.vue`

### 为何需要 `.value`

- 因为要保证响应式，需要把值类型封装成一个对象形式，所以用 `.value` 表示这个值
- 模板，reactive 使用时，不需要 `.value`
- 其他情况都需要 `.value`

结合 computed 的内部实现，可如下解释：

```js
// 伪代码：不具有响应式，即改变值不会触发渲染
function computed(getter) {
  let value
  watchEffect(() => {
    value = getter() // value 是值类型，值拷贝，value 的变化不会传递到下游
  })
  return value
}

// 伪代码：具有响应式
function computed(getter) {
  const ref = {
    value: null,
  }
  watchEffect(() => {
    ref.value = getter() // ref 是引用类型，指针拷贝，ref 的变化会传递到下游
  })
  return ref
}
```

上述代码，可以把 `watchEffect` 改为 `setTimeout` 模拟一下

### 再聊 toRef 和 toRefs

- 设计初衷：不丢失响应性的情况下对返回的对象进行**分解/扩散**
- 必须存在：因为直接 property 或者 `...state` ，会直接拿到属性的值。如果属性是**值类型**，则会丢失响应式 ！！！（响应式是 Proxy 实现的）
- 注意事项：不创造响应式，而是**延续**响应式 （所以针对普通对象不行，必须是响应式对象）

toRef toRefs 必须针对一个响应式对象，普通对象是无法变成响应式的。
它俩的设计初衷，本来也是针对响应式对象的 https://vue-composition-api-rfc.netlify.app/zh/api.html#toref
即，想要实现响应式，只有两个方法：`ref` `reactive`

- `ref` **创造**响应式
- `toRef` 和 `toRefs` **延续**响应式

为何必须使用 `toRef(state, 'name')` 和 `toRefs(state)` ？？？
因为直接 property 或者 `...state` ，会直接拿到属性的值。如果属性是**值类型**，则会丢失响应式。（响应式是 Proxy 实现的）
这也是引入 `ref` 的根源！！！
也是引入 Composition API ，抛弃 this ，带来的结果。

### 从使用角度

理解和应用要分开总结，这很重要。即便你听不懂原理，也要知道如何使用。

- ref 值类型响应式
- ref 模板引用
- setup 返回时用 `toRefs(state)`
- 用于第三方的逻辑函数，如 demo 中的 `useMousePosition`
- 为所有的 ref 名加类似 `xxxRef` 的后缀

---

ref 和 reactive 混合起来，真的非常乱。
相比之下，React Hooks 只有 `useState` ，反而简单很多。—— 当然它也有其他的一些理解成本。


# 11-升级Vue3.0\04-解答-3.md
# 解答-3 

## Vue3.0 有哪些重要的新功能

（切记，不要像背诵课文似的）

我花了 3 个晚上的业余时间，详细对比了 v2 和 v3 的文档目录，找出了以下比较重要的改动。
只说**重点**改动，足够回复面试题了。要看详细的，需要去查阅文档。

另外，只说使用上的，不说原理上的。

### 可使用 vite 安装

（后面会讲 vite）

### createApp

```js
// vue2.x
const app = new Vue({ /* 选项 */ })

// vue3
const app = Vue.createApp({ /* 选项 */ })
```

全局 API

```js
// vue2.x
Vue.use(/* ... */)
Vue.mixin(/* ... */)
Vue.component(/* ... */)
Vue.directive(/* ... */)

// vue3
app.use(/* ... */)
app.mixin(/* ... */)
app.component(/* ... */)
app.directive(/* ... */)
```

### emits

组件中 `emits: ['fnName']` ，否则有警告 `Extraneous non-emits event listeners`

### 生命周期

已讲过

### 多事件处理

```html
<!-- 在 methods 里定义 one two 两个函数 -->
<button @click="one($event), two($event)">
  Submit
</button>
```

### Fragment

取消了 v2.x 的“一个组件必须有一个根元素”

```html
<!-- vue2.x 组件模板 -->
<template>
  <div class="blog-post">
    <h3>{{ title }}</h3>
    <div v-html="content"></div>
  </div>
</template>

<!-- vue3 组件模板 -->
<template>
  <h3>{{ title }}</h3>
  <div v-html="content"></div>
</template>
```

### 去掉了 `.sync`

```html
<!-- vue 2.x -->
<MyComponent v-bind:title.sync="title" />

<!-- vue 3.x -->
<MyComponent v-model:title="title" />
```

文档
- vue2.x https://cn.vuejs.org/v2/guide/components-custom-events.html#sync-%E4%BF%AE%E9%A5%B0%E7%AC%A6
- vue3 https://v3.cn.vuejs.org/guide/component-custom-events.html#v-model-%E5%8F%82%E6%95%B0

demo 代码参考 `VModel/index.vue`

### 异步组件

新增 `defineAsyncComponent` 方法。

```js
import { createApp, defineAsyncComponent } from 'vue'

createApp({
  // ...
  components: {
    AsyncComponent: defineAsyncComponent(() =>
      import('./components/AsyncComponent.vue')
    )
  }
})
```

vue2.x 写法如下

```js
new Vue({
  // ...
  components: {
    'my-component': () => import('./my-async-component.vue')
  }
})
```

### vue3 移除了过滤器 filter

```html
<!-- 以下 filter 在 vue3 中不可用了！！！ -->

<!-- 在双花括号中 -->
{{ message | capitalize }}

<!-- 在 `v-bind` 中 -->
<div v-bind:id="rawId | formatId"></div>
```

### Teleport

```html
<!-- data 中设置 modalOpen: false -->

<button @click="modalOpen = true">
    Open full screen modal! (With teleport!)
</button>

<teleport to="body">
    <div v-if="modalOpen" class="modal">
        <div>
            telePort 弹窗 (父元素是 body)
            <button @click="modalOpen = false">Close</button>
        </div>
    </div>
</teleport>
```

### Suspense

【注意】Suspense 是一个实验性的 API ，后面可能会改变 —— `v3.0.2`

当内容组件未加载完成时，先显示 loading 的内容。

```html
<Suspense>
    <template>
        <Test1/> <!-- 是一个异步组件 -->
    </template>

    <!-- #fallback 就是一个具名插槽。即：
      Suspense 组件内部，有两个 slot ，
      其中一个具名为 fallback -->
    <template #fallback>
        Loading...
    </template>
</Suspense>
```

demo 代码参考 `SuspenseTest/index.vue`

### Composition API

主要的功能有：
- reactive
- ref 相关
- readonly
- computed
- watch
- watchEffect
- setup
- 各生命周期钩子函数

-----

上述仅仅是比较重要改动，足够应对面试题了。
全面的改动，可以查看 v2 升级 v3 的指南 https://v3.cn.vuejs.org/guide/migration/introduction.html


# 11-升级Vue3.0\05-解答-4.md
# 解答-4

## Composition API 如何实现代码逻辑复用

参考 demo `MousePosition` 目录

## Vue3.0 如何实现响应式？

Proxy 实现，现有视频

## watch 和 watchEffect 的区别

- 两者都可以监听 data 变化
- watch 需要手动确认监听哪个属性
- watchEffect 会根据其中的属性，自动监听其变化

代码参考 demo `WatchEffect.vue` `Reactive.vue` `Ref.vue`

## setup 中如何获取组件实例？

该问题主要针对 `this`

- 若使用 `setup` 和组合式 API 时，没有 this
- 使用 `getCurrentInstance` 获取当前组件实例 —— 不过，使用组合式 API 一般也无需获取组件实例
- 若使用 Options API 的语法，照常有 `this`

这一点和 react 一样。class 组件有 this ，Hooks 函数组件没有 this 。

代码参考 `GetInstance.vue`


# 11-升级Vue3.0\06-解答-5.md
# 解答-5

## Vue3.0 为什么这么快？

- Proxy 实现响应式，初始化时更快。之前已经讲过
- 模板编译优化：静态内容直接输出、数据缓存 —— 所有的算法优化，都是**拿空间换时间**
- diff 算法优化，让组件渲染更快。diff 算法和模板是相关的。PS：其实 diff 算法本身的对比逻辑，跟之前时一样的。可优化的是一些细节和条件分支。
- tree-shaking

*PS：通过 [vue3 template explorer](https://vue-next-template-explorer.netlify.app/) 来体验下面的内容。*

### PatchFlag 静态标记

【案例 1】生成 PatchFlag 是 `1 /* TEXT */`

```html
<div>
  <p>静态文字</p>
  <p>{{ msg }}</p>
</div>
```

```js
import { createVNode as _createVNode, toDisplayString as _toDisplayString, openBlock as _openBlock, createBlock as _createBlock } from "vue"

export function render(_ctx, _cache, $props, $setup, $data, $options) {
  return (_openBlock(), _createBlock("div", null, [
    _createVNode("p", null, "静态文字"),
    _createVNode("p", null, _toDisplayString(_ctx.msg), 1 /* TEXT */)
  ]))
}
```

【案例 2 】生成 PatchFlag 是 `9 /* TEXT, PROPS */`

```html
<div>
  <span>静态文字</span>
  <span :id="hello" class="bar">{{ msg }}</span>
</div>
```

```js
import { createVNode as _createVNode, toDisplayString as _toDisplayString, openBlock as _openBlock, createBlock as _createBlock } from "vue"

export function render(_ctx, _cache, $props, $setup, $data, $options) {
  return (_openBlock(), _createBlock("div", null, [
    _createVNode("span", null, "静态文字"),
    _createVNode("span", {
      id: _ctx.hello,
      class: "bar"
    }, _toDisplayString(_ctx.msg), 9 /* TEXT, PROPS */, ["id"])
  ]))
}
```

即，所有的静态内容都没有 PatchFlag 标记，动态内容都会有。
这个 PatchFlag 到底有什么作用呢？

有了 PatchFlag 就可以区分出来动态节点和静态节点，只对比动态节点即可。

![](./img/diff.png)

### hoistStatic 静态提升

编译如下模板

```html
<div>
  <span>静态文字1</span>
  <span>静态文字2</span>
  <span>静态文字3</span>
  <span>{{ msg }}</span>
</div>
```

开启 `HoistStatic` 选项，可以看到静态节点全部提升到父作用域去定义，并缓存起来。

典型的“拿空间换时间”的优化方法，缓存就不用重复生成。

还有，如果多个静态节点挨着在一起，超过一定的数量，会被合并起来。
例如编译如下模板

```html
<div>
  <span>静态文字1</span>
  <span>静态文字2</span>
  <span>静态文字3</span>
  <span>静态文字4</span>
  <span>静态文字5</span>
  <span>静态文字6</span>
  <span>静态文字7</span>
  <span>静态文字8</span>
  <span>静态文字9</span>
  <span>静态文字10</span>
  <span>{{ msg }}</span>
</div>
```

到的结果

```js
import { createVNode as _createVNode, toDisplayString as _toDisplayString, createStaticVNode as _createStaticVNode, openBlock as _openBlock, createBlock as _createBlock } from "vue"

const _hoisted_1 = /*#__PURE__*/_createStaticVNode("<span>静态文字1</span><span>静态文字2</span><span>静态文字3</span><span>静态文字4</span><span>静态文字5</span><span>静态文字6</span><span>静态文字7</span><span>静态文字8</span><span>静态文字9</span><span>静态文字10</span>", 10)

export function render(_ctx, _cache, $props, $setup, $data, $options) {
  return (_openBlock(), _createBlock("div", null, [
    _hoisted_1,
    _createVNode("span", null, _toDisplayString(_ctx.msg), 1 /* TEXT */)
  ]))
}
```

### cacheHandler 缓存事件

渲染如下模板

```html
<div>
  <span @click="onClick">
    静态文本
  </span>
</div>
```

开启 `cacheHandlers` 开关，可以看到 onClick 事件会被缓存到 `_cache[1]` 中。

### SSR 时的优化

编译如下模板，输出 SSR

```html
<div>
  <span>静态文字1</span>
  <span>静态文字2</span>
  <span>静态文字3</span>
  <span>{{ msg }}</span>
</div>
```

静态文件直接输出，绕过了 vdom 到 dom 的过程。
这跟 PatchFlag 有点类似。

### tree-shaking

编译以下几段模板，可以看到 `import` 的内容不一样。

```html
<!-- 模板1 -->
<div>
  <span>静态文字</span>
</div>

<!-- 模板2 -->
<div>
  <span>静态文字</span>
  <span>{{ msg }}</span>
</div>

<!-- 模板3 -->
<div>
  <span>静态文字</span>
  <input v-model="msg">
</div>
```

即，针对不通情况，vue 会自动引入所需要的功能，而不会全部引入。
这样就让使用者可以压缩他们项目打包的体积，即 tree-shaking


# 11-升级Vue3.0\07-解答-6.md
# 解答-6

## Vite 是什么？

https://v3.cn.vuejs.org/guide/installation.html#vite

- 一个打包工具，Vue 作者发起的
- 借助 Vue 的影响力，和 webpack 竞争
- 优势：开发环境启动快，无需打包

- 开发环境基于 ES6 module https://www.caniuse.com/?search=module
- 生产环境打包时使用 rollup

```html
<script type="module">
    import add from './src/add.js'

    const res = add(1, 2)
    console.log('add res', res)
</script>
```

## 和 React Hooks 对比

PS：这个题目需要你了解 React Hooks ，不了解的，可以先去看看（课程里有讲解），再回来学习。

- 组件生命周期中 `setup` 只调用一次，而 React Hooks 在组件 render 和每次 update 时都会被调用
- 无需使用 `useMemo` `useCallback`
- “不需要顾虑调用顺序，也可以用在条件语句中” （React Hooks 的 `useXXX` 则有严格规定，这一点是 React Hooks 不太简单的地方）
- （后两个，都是依赖于第一个特性的）

另外，reactive ref 这俩概念，和 react Hooks 的 useState 相比，还是后者好理解


# 11-升级Vue3.0\升级01-vue3-jsx.md
# vue3 JSX

【注意】如果对 JSX 语法不熟悉，可以先去学习 React 部分。

## 开始

- vue3 中 JSX 的基本使用
- JSX 和 template 的区别
- JSX 和 slot
- JSX 和 作用域 slot

## vue3 中 JSX 的基本使用

- 基本使用
- 使用 `.jsx` 格式的文件，使用 `defineComponent` 
    - 可以传入一个配置
    - 也可以传入一个 `setup` 函数
- 引入子组件，传递属性

## JSX 和 template 的区别

语法的区别：
- JSX 就是 js 代码，它可以使用任何 js 的能力。
- template 是模板语法，目前只能插入一些简单的 js 表达式。逻辑则需要指令，如 `v-for` `v-if` 等。
- JSX 已经成为了 ES 规范语法，babel 支持。而 template 只是 vue 自家的语法规范。

但本质是相同的：他们都会被编译成 render 函数，用于渲染 vnode<br>
在 vue React 原理都讲过，这里不再重复

### 插值
- template 用 `{{xxx}}`
- JSX 用 `{xxx}`

### 自定义组件
- template 可用 `<custom-component></custom-component>` 或者 `<CustomComponent></CustomComponent>`
- JSX 必须使用 `<CustomComponent></CustomComponent>`

### 传递属性和事件
- template 中使用 `a="xx"` 或 `:a="xx"` ，`@xx="xx"`
- JSX 中全部使用 `a={xx}`

### 条件，循环
- template 使用指令 `v-for` `v-if` 等
- JSX 中使用 js 表达式

## JSX 和 slot

因为 template 只能内嵌简单的 js 表达式，无法内嵌组件，所以 vue 只能自造一个 `<slot>` 语法。

vue3 setup 中可以使用 `context.slots.default()` 获取子组件

使用 tabs 组件演示 JSX 如何操作 slot

## JSX 和作用域 slot

回顾作用域 slot ，就是：父组件想要获取子组件的信息，并渲染到 slot 中

作用域 slot 很难理解，一直是 vue 初学者的噩梦。但用 JSX 将会变的很好理解，因为它就是 js 代码逻辑。

代码的方式，在 react 中叫做“renderProps”


# 11-升级Vue3.0\升级02-vue3-script-setup.md
# vue3 script setup

vscode 插件 禁用 `Vetur` 下载 `Volar`

## 准备环境

vue-cli 创建项目之后，升级到 3.2 版本，重新安装即可 `yarn add vue@next`

## 基本使用

- 顶级变量，可以直接用于模板中
- 引入的组件，可以直接用于模板中
- 使用 ref reactive 等 vue3 功能

和其他 script 使用

- 没有 return 和 exports ，需要适应
- script 和 template 位置调换，这样更易阅读

## 属性和事件

- defineProps
- defineEmits

## defineExpose

向父组件暴露数据

------

setup script 中不能使用 jsx


# x1-学习过程\后续学习建议.md
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

学完了本课程的框架和项目，大家可以参照这个知识体系的方式，来写一个 Vue 或者 React 详细的知识体系图。<br>
写出来的，才是自己的。


# x1-学习过程\扩展学习.md
# 扩展学习

Vue React 等框架现在是前端必备的技能，即便是迎接毕业生也得会使用。

如果你是 3 年工作经验的同学，还需要去学习设计模式，慢慢的从“搬砖人员”到设计人员。推荐双越老师录制的《[Javascript 设计模式系统讲解与应用](https://coding.imooc.com/class/255.html)》。

另外，随着工作经验的增长，对业务的理解，你可能慢慢的会承担前端 leader 或者架构师角色。需要及早做准备，机会留给有准备的人。<br>
有兴趣的同学可以学习双越老师主讲的《[Web 前端架构师](https://class.imooc.com/sale/fearchitect)》课程，干货满满。


# x1-学习过程\课前必读.md
# 学前必读

本课程是中级课程，学习本课程之前需要掌握：
- 了解 javascript 和 ES6 基本语法
- 了解 React Vue 和 webpack ，至少看过文档，做过 demo
- 有自我查询知识的能力，有获取知识的欲望

前端基础知识，大家可以去慕课网的[慕课教程](http://www.imooc.com/wiki/)里学习，里面包含了前端开发常用的技术和知识。

了解框架，可以直接去官网网站：
- Vue https://cn.vuejs.org/
- React https://react.docschina.org/
- webpack https://webpack.docschina.org/

如遇到问题可以通过网络搜索引擎就行查找，也可以通过提问网站进行提问。当然课程的学员也可以直接像讲师提问。

预祝各位学习愉快，收获满满～


# x1-学习过程\03-vue使用\章介绍.md
# 章介绍

Vue 是前端面试必考内容，首先要保证自己要会使用 Vue 。本章讲解 Vue 基本使用、组件使用、高级特性和 Vuex Vue-router ，这些部分的知识点和面试题。

## 产出

- Vue 知识点和面试题

## 主要内容

- Vue 基本使用的知识点和面试题
- Vue 组件的知识点和面试题
- Vue 高级使用的知识点和面试题
- Vuex 和 Vue-router 相关面试题

## 关键字

- Vue
- Vuex
- Vue-router

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- Vue 高级用法不一定常用，但你一定要知道它们的存在


# x1-学习过程\03-vue使用\章回顾.md
# 章回顾

## 产出

- Vue 知识点和面试题

## 主要内容

- Vue 基本使用的知识点和面试题
- Vue 组件的知识点和面试题
- Vue 高级使用的知识点和面试题
- Vuex 和 Vue-router 相关面试题

## 知识点

- vue-cli
- 基本使用
    - 模板：指令 插值
    - computed 和 watch
    - class 和 style
    - 条件
    - 循环
    - 表单
    - 事件
- 组件
    - 生命周期
    - props
    - $emit
    - 自定义事件
- 高级特性
    - 自定义 v-model
    - $nextTick
    - refs
    - slot
    - 动态组件
    - 异步组件
    - keep-alive
    - mixin
- Vuex
- Vue-router

## 注意事项

- Vue 高级用法不一定常用，但你一定要知道它们的存在


# x1-学习过程\04-vue原理\章介绍.md
# 章介绍

要保证自己的面试竞争力，必须掌握 Vue 原理，前端高级面试或者大厂面试中常考。本章讲解虚拟DOM，diff 算法，响应式，模板编译，组件渲染等 Vue 原理常考的知识点和面试题。

## 产出

- 学会 Vue 相关原理，包括：响应式、虚拟 DOM、组件渲染等

## 主要内容

- Vue 响应式原理
- Vue 虚拟 DOM 相关原理
- Vue 模板编译原理
- Vue 组件渲染过程

## 关键字

- Vue
- 响应式
- 虚拟 DOM
- diff 算法
- 模板

## 学习方法

- 学习原理要关注重点、核心的部分，关注主流程，不要关注细节

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习


# x1-学习过程\04-vue原理\章回顾.md
# 章回顾

## 产出

- 学会 Vue 相关原理，包括：响应式、虚拟 DOM、组件渲染等

## 主要内容

- Vue 响应式原理
- Vue 虚拟 DOM 相关原理
- Vue 模板编译原理
- Vue 组件渲染过程

## 知识点

- 组件化和 MVVM
- 响应式原理
- 虚拟 DOM
- diff 算法
- 模板编译
- 组件渲染过程
- 前端路由

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习


# x1-学习过程\05-vue真题演练\章介绍.md
# 章介绍

## 产出

- Vue 面试真题演练

## 主要内容

- Vue 面试真题演练（会不定期更新）

## 关键字

暂无

## 学习方法

暂无

## 注意事项

- 自己面试时遇到 Vue 的面试题，可以提交问题，告知双越老师


# x1-学习过程\05-vue真题演练\章回顾.md
# 章回顾

## 产出

- Vue 面试真题演练

## 主要内容

- Vue 面试真题演练（会不定期更新）

## 知识点

暂无

## 注意事项

- 自己面试时遇到 Vue 的面试题，可以提交问题，告知双越老师


# x1-学习过程\06-vue3学习\章介绍.md
# 章介绍

对 vue3 进行全面讲解。包括 Vue3 升级的变动，Vue3 核心知识点，Composition API 如何使用，以及 Vue3 一些基础的原理。

## 产出

- Vue3 常考知识点和面试题

## 主要内容

- Vue3 基本使用
- Vue3 相比于 Vue2 的升级
- ref 相关的知识点（比较难理解）
- Composition API
- Vue3 原理讲解

## 关键字

- Vue3
- ref
- Composition API
- Proxy

## 学习方法

- Vue3 的课程示例，一定要亲自动手练习
- 学习原理要关注重点、核心的部分，关注主流程，不要关注细节

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习


# x1-学习过程\06-vue3学习\章回顾.md
# 章回顾

## 产出

- Vue3 常考知识点和面试题

## 主要内容

- Vue3 基本使用
- Vue3 相比于 Vue2 的升级
- ref 相关的知识点（比较难理解）
- Composition API
- Vue3 原理讲解

## 关键字

- Vue3 新功能
    - createApp
    - emits 属性
    - 多事件处理
    - Fragment
    - .sync 改为 v-model 参数
    - 异步组件的引用方式
    - 移除 filter
    - Teleport
    - Suspense
- Composition API
    - reactive
    - ref toRef toRefs
    - readonly
    - computed
    - watch watchEffect
    - 钩子函数生命周期
- Vue3 原理
    - Proxy 响应式
    - PatchFlag
    - hoistStatic
    - cacheHandler
    - SSR 优化
    - Tree shaking
- Vite 和 ES Module

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习


# x1-学习过程\07-React使用\章介绍.md
# 章介绍

和 Vue 一样，React 也是面试必备技能，而且大厂的考察概率更高。本章讲解 React 基本使用，高级特性，性能优化，redux 等内容的知识点和面试题。

## 产出

- React 基本使用的知识点和面试题
- React 高级使用的知识点和面试题

## 内容

- React 基本使用
- React state 和 setState （重要）
- React 高级使用
- React 性能优化
- Redux 和 React-router

## 关键字

- React
- JSX
- state
- Redux
- React-router

## 学习方法

- 课程示例需要亲自动手练习

## 注意事项

- React 性能优化要考虑使用场景，不要过早优化


# x1-学习过程\07-React使用\章回顾.md
# 章回顾

## 产出

- React 基本使用的知识点和面试题
- React 高级使用的知识点和面试题

## 内容

- React 基本使用
- React state 和 setState （重要）
- React 高级使用
- React 性能优化
- Redux 和 React-router

## 知识点

- React 基本使用
    - JSX
    - 条件
    - 列表
    - 事件
    - 组件和 props
    - state 和 setState
    - 组件生命周期
- React 高级特性
    - 函数组件
    - 受控和非受控组件
    - refs
    - Portals
    - 异步组件（懒加载）
    - 性能优化
    - SCU
    - 纯组件
    - 不可变值 immutable.js
    - 高阶组件 HOC
    - render prop
- Redux
    - store
    - reducer
    - action
    - dispatch
- React-router

## 注意事项

- React 性能优化要考虑使用场景，不要过早优化


# x1-学习过程\08-React原理\章介绍.md
# 章介绍

和 Vue 相比，使用 React 时更需要开发人员了解其原理，面试也会重点考察。本章讲解 JSX 编译、事件机制、batchUpdate ，组件更新渲染过程等 React 原理常考的知识点和面试题。

## 产出

- React 原理相关的知识点和面试题

## 内容

- JSX 本质
- 合成事件机制
- batchUpdate 机制
- 事务机制
- 组件渲染和更新的过程

## 关键字

- React
- JSX
- batchUpdate
- 事务
- 合成事件

## 学习方法

- 学习原理要关注重点、核心的部分，关注主流程，不要关注细节

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习



# x1-学习过程\08-React原理\章回顾.md
# 章回顾

## 产出

- React 原理相关的知识点和面试题

## 内容

- JSX 本质
- 合成事件机制
- batchUpdate 机制
- 事务机制
- 组件渲染和更新的过程

## 知识点

- 函数式编程
- vdom 和 diff 算法
- JSX 本质
- 合成事件
- setState 和 batchUpdate
- 组件渲染过程
- 前端路由

## 注意事项

- 原理不等于源码，用 2/8 原则高效学习


# x1-学习过程\09-React真题演练\章介绍.md
# 章介绍

## 产出

- react 面试真题演练

## 主要内容

- react 面试真题演练（会不定期更新）

## 关键字

暂无

## 学习方法

暂无

## 注意事项

- 自己面试时遇到 react 的面试题，可以提交问题，告知双越老师


# x1-学习过程\09-React真题演练\章回顾.md
# 章回顾

## 产出

- React 面试真题演练

## 主要内容

- React 面试真题演练（会不定期更新）

## 知识点

暂无

## 注意事项

- 自己面试时遇到 React 的面试题，可以提交问题，告知双越老师


# x1-学习过程\10-webpack和babel\章介绍.md
# 章介绍

webpack 是前端必备工具，面试必考内容，特别是性能优化。本章讲解 webpack 常用配置，详细的性能优化手段，已经 babel 。最后会给出常考面试题，做面试真题演练。

## 产出

- webpack 常见知识点和面试题

## 内容

- webpack 基本使用
- webpack 高级特性
- webpack 性能优化
- babel 使用和配置

## 关键字

- webpack
- babel

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 性能优化要考虑实际情况，不要过早优化


# x1-学习过程\10-webpack和babel\章回顾.md
# 章回顾

## 产出

- webpack 常见知识点和面试题

## 内容

- webpack 基本使用
- webpack 高级特性
- webpack 性能优化
- babel 使用和配置

## 知识点

- webpack 基本使用
    - 安装配置
    - dev-server
    - 解析 ES6
    - 解析样式
    - 解析图片文件
    - 常见 loader 和 plugin
- webpack 高级特性
    - 多入口
    - 压缩和抽离 css
    - 抽离公共代码
    - 懒加载
    - 处理 React 和 Vue
- webpack 性能优化
    - 优化打包速度
    - 优化产出代码
- babel
    - polyfill
    - runtime

## 注意事项

- 性能优化要考虑实际情况，不要过早优化


# x1-学习过程\11-项目设计\章介绍.md
# 章介绍

掌握了 Vue 和 React 的使用和原理，是否能设计出一个项目功能呢？面试会考察项目设计能力。本章讲解项目设计的常见考察方式，以及解题思路和方法。

## 产出

- 解答面试中如何考察项目设计

## 内容

- 项目设计的要点和思路
- React 设计 todo list
- Vue 设计购物车

## 关键字

- 设计
- 状态

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- 重点关注设计思路，此时不要再过于关注代码细节


# x1-学习过程\11-项目设计\章回顾.md
# 章回顾

## 产出

- 解答面试中如何考察项目设计

## 内容

- 项目设计的要点和思路
- React 设计 todo list
- Vue 设计购物车

## 知识点

暂无

## 注意事项

- 重点关注设计思路，此时不要再过于关注代码细节



# x1-学习过程\12-项目流程\章介绍.md
# 章介绍

本章讲解一个标准前端项目的开发流程，项目角色，以及项目进行中将会遇到的问题和解决方案。帮你提炼自己的项目经验，成为职场“老司机”。

## 产出

- 学会规范的前端项目研发流程

## 内容

- 前端项目研发流程的各个阶段，从需求评审、到设计、到研发、到测试、最后上线

## 关键字

- 研发流程
- 项目管理

## 学习方法

- 结合自己的实际工作经验来学习

## 注意事项

- 如果没有工作经验，或者工作中用不到流程，那就学习之后记录下来，以后遇到了再回顾。


# x1-学习过程\12-项目流程\章回顾.md
# 章回顾

## 产出

- 学会规范的前端项目研发流程

## 内容

- 前端项目研发流程的各个阶段，从需求评审、到设计、到研发、到测试、最后上线

## 知识点

暂无

## 注意事项

- 如果没有工作经验，或者工作中用不到流程，那就学习之后记录下来，以后遇到了再回顾。


# x1-学习过程\14-react-hooks\章回顾.md
# 章回顾

## 产出

- React Hooks 常考的知识点和面试题

## 内容

- useState
- useEffect
- useRef 和 useContext
- React Hooks 性能优化
- 自定义 Hooks
- 使用 React Hooks 的规则

## 知识点

- useState
- useEffect
- useRef
- useContext
- useReducer
- useMemo
- useCallback
- 自定义 Hooks

## 注意事项

- React Hooks 目前不会取代 class 组件，所以不用所有的项目都用 Hooks 来做，提前设计好


# x1-学习过程\14-react-hooks\章开始.md
# 章介绍

本章节，介绍了hooks的 核心考点，和class的对比，面试过程中要注意的一些点，以及面试解答分析。

## 产出

- React Hooks 常考的知识点和面试题

## 内容

- useState
- useEffect
- useRef 和 useContext
- React Hooks 性能优化
- 自定义 Hooks
- 使用 React Hooks 的规则

## 关键字

- React
- Hooks
- useState
- useEffect

## 学习方法

- 课程示例要亲自动手练习

## 注意事项

- React Hooks 目前不会取代 class 组件，所以不用所有的项目都用 Hooks 来做，提前设计好


# xx-教学互动\练习环节\01-项目任务.md
# 项目任务

> 浅层学习看输入，深度学习看输出

前两章是导学和介绍。

## 第三章 - Vue 使用

**【任务】总结 vue 高级特性**

写一篇博客，总结一下 vue 的所有高级特性。每个高级特性的考点，和应用场景，最好每一个都附上 demo 代码和截图。

把自己学习的结果都详细记录下来，写写画画记得牢固，也方便以后自己复习时查阅。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第四章 - Vue 原理

**【任务】vnode 之于 Vue 的作用**

写一篇博客，总结一下你对 vnode 的理解。这是一个开放性题目，内容不受限制，可以根据 vnode 继续联想其他知识点。

学习完本章，对于 vnode 这样重要的知识点，一定要有自己的思考，并且有思考结果。
证明自己有思考结果的最好方式，就是把结果写出来。这不仅仅是给老师证明，也是给自己证明。

可以参考老师的讲课思路来写，但更加建议有自己特立独行的思考方式，独立思考。
老师写博客、做课程从来都是特立独行，会去参考别的资料，但绝对不会模仿别人。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第五章 - Vue 面试真题演练

暂无

## 第六章 - Vue3
（按升级 2021.02 的升级内容）

**【任务】Composition API 给 Vue 带来了什么？**

写一篇博客，写出你对 Composition API 的理解。这是一个开放性题目，内容不受限制，围绕 Composition API 来写即可。

学习完本章，对于 Composition API 这样重要的知识点，一定要有自己的思考，并且有思考结果。
证明自己有思考结果的最好方式，就是把结果写出来。这不仅仅是给老师证明，也是给自己证明。

可以参考老师的讲课思路来写，但更加建议有自己特立独行的思考方式，独立思考。
老师写博客、做课程从来都是特立独行，会去参考别的资料，但绝对不会模仿别人。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。
## 第七章 - React 使用

**【任务】React 为何需要 SCU ？**

写一篇博客，写出你对 SCU 的理解，以及 SCU 相关的内容，这是理解 React 使用的关键。

注意，不要简单写几条总结，而是要详细写明，并附上必要的 demo 代码。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第八章 - React 原理

**【任务】介绍 React 的 batchUpdate 机制**

写一篇博客，介绍一下你所理解的 batchUpdate 机制，尽量详细完整、图文并茂。

batchUpdate 机制是理解 React 组件更新流程的重点，一定要搞清楚主要流程。写博客总结一下，会让你记忆更加牢固。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。

## 第九章 - React 面试真题演练

暂无

## 第十章 - webpack 和 babel

**【任务】从 0 配置 webpack5 开发环境**

从 0 自己搭建一个 webpack5 的开发环境，每一项都自己手动搭建，体验一下这个过程。不要直接用老师现成的代码。

产出的代码提交到自己的 github 仓库。并写一篇博客记录搭建的过程，也方便自己复习。

可以将 github 项目链接发到课程 QQ 群，分享给其他同学。相互学习，相互 star。

## 第十一章 - 项目设计

**【任务】用 Vue 实现 todo-list ，用 React 实现购物车**

课程里是 React 实现 todo list ，Vue 实现购物车。你可以换过来，用 Vue 实现 todo-list ，用 React 实现购物车。

产出的代码提交到自己的 github 仓库。并写一篇博客记录搭建的过程，也方便自己复习。

可以将 github 项目链接发到课程 QQ 群，分享给其他同学。相互学习，相互 star。

## 第十二章 - 项目流程

**【任务】自己画一个项目研发流程图**

按照自己的理解，画一个项目研发流程图。可参考课程的内容，但更鼓励自己独立思考。

画图工具可以使用 [processon.com](https://processon.com/) 。

画完之后到处图片，发到课程 QQ 群，分享给其他同学，相互学习。

## 第十四章 - React Hooks

**【任务】对比 React Hooks 和 Vue3 Composition API**

首先复习一下 Vue3 Composition API 。之前布置的任务里，有让你写过关于 Composition API 的博客，翻出来看一遍。

然后再写一篇博客，对比一下 React Hooks 和 Vue3 Composition API 。对于每一个对比结果，都附上 demo 和源码。

博客写完后，将链接发到课程 QQ 群，分享给其他同学。相互学习，相互评论，相互点赞。


# xx-教学互动\练习环节\02-互动话题.md
# 互动话题

前两章是导学和介绍。

## 第三章 - Vue 使用

【话题】Vue 的 slot 是不是很难理解？

## 第四章 - Vue 原理

暂无

## 第五章 - Vue 面试真题演练

【话题】你去面试时，都遇到过哪些 Vue 面试题？

## 第六章 - Vue3
（按升级 2021.02 的升级内容）

【话题】ref 有没有给你造成心智负担？

## 第七章 - React 使用

【话题】更喜欢 JSX 还是 Vue template ？

## 第八章 - React 原理

暂无
## 第九章 - React 面试真题演练

【话题】你去面试时，都遇到过哪些 React 面试题？

## 第十章 - webpack 和 babel

【话题】你公司里的项目，都用到了哪些 webpack 优化功能？

## 第十一章 - 项目设计

【话题】你们在做开发之前，以什么形式讨论确定设计方案？

## 第十二章 - 项目流程

【话题】你们公司，有专门负责项目研发流程的角色吗？他一般做哪些工作？

## 第十四章 - React Hooks

【话题】更喜欢 React Hooks 还是 Vue Composition API ？

