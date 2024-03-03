---
title: "面试必备 Vue React Webpack 全掌握"
datePublished: Sun Mar 03 2024 16:33:21 GMT+0000 (Coordinated Universal Time)
cuid: cltbqecgu00040al8anfl16id
slug: vue-react-webpack

---

# **Vue 基本使用**

## **指令、插值**

* 插值、表达式
    
* 指令、动态属性
    
* v-html 会有 xss 风险，会覆盖子组件
    

​

## **computed 和 watch**

* computed 有缓存，data 不变则不会重新计算
    
* watch 如何深度监听
    
* watch 监听引用类型，拿不到 oldVal
    

```javascript
watch : {
    handler (oldVal, val) {
        console.log('watch info', oldVal, val)
    },
    deep: true
}
```

## **class style**

* 使用动态属性
    
* 使用驼峰式写法
    

​

## **条件渲染**

* v-if v-else 的用法，可以使用变量，也可以使用 === 表达式
    
* v-if 和 v-show 的区别
    
* v-if 和 v-show 的使用场景
    

​

## **循环列表的渲染**

* 如何遍历对象——也可以使用 v-for
    
* key 的重要性，key 不能乱写，如 random 或者 index
    
* v-for 和 v-if 是不能一起使用的
    

​

## **事件**

* event 参数，自定义参数（$event,原生 event）
    
* 事件修饰符，按键修饰符
    
* 【观察】事件被绑定到哪里（写在哪，挂载在哪）
    

![image.png](https://static.ziying.site/yuque_img_upload/27b54711-1267-36a2-8e4c-2c5fe7bd416f.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/5f038f99-496f-3e12-81f6-7168ce58d4a5.png align="left")

## **表单**

* v-model
    
* 常见的表单项， textarea，checkbox，radio，select
    
* 修饰符 lazy number trim
    

![image.png](https://static.ziying.site/yuque_img_upload/df7bb609-7a1e-3169-89d1-ff1305cfa4ce.png align="left")

## **vue 组件使用**

* props 和 $emit
    
* 组件间通讯-自定义事件
    
* 组件生命周期
    

​

单个组件

* 挂载阶段
    
* 更新阶段
    
* 销毁阶段
    

​

created vue 实例化完成 mounted 元素挂载完成​

父子组件

![image.png](https://static.ziying.site/yuque_img_upload/60bcb8e1-4d74-3d6d-bc0e-86b8475f74d5.png align="left")

创建从外到内，渲染从内到外

![image.png](https://static.ziying.site/yuque_img_upload/8095b887-1919-3972-b0b9-9f4bc5b57d52.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/0f15a2e0-237c-3376-90e3-4c8e14ea9d53.png align="left")

## **Vue 高级特性**

* 自定义 v-model
    
* $nextick
    
* slot
    
* 动态、异步组件
    
* keep-alive
    
* mixin
    

v-model

```html
<intput :value="text" @input="$emit('change', $event.target.value)" />
```

```javascript
export default {
  model: {
    prop: "text",
    event: "change",
  },
  props: {
    text: String,
    default: "",
  },
};
```

​

$nextTick

* Vue 是异步渲染
    
* data 改变之后，DOM 不会立刻渲染
    
* $nextTick 会在 DOM 渲染之后被触发，以获取最新的 DOM 节点
    

​

![image.png](https://static.ziying.site/yuque_img_upload/679e0c11-a494-386d-8a7f-84860af854d0.png align="left")

slot

* 基本使用
    
* 作用域插槽
    
* 具名插槽
    

​

动态组件

* :is="component-name" 用法 `<component :is="NextTick" />`
    
* 需要根据数据，动态渲染的场景。即组件类型不确定
    

​

Vue 如何加载异步组件

* import() 函数
    
* 按需加载，异步加载大组件
    

​

keep-alive

* 缓存组件
    
* 频繁切换，不需要重复渲染
    
* Vue 常见的性能优化
    

​

mixins

* 多个组件有相同的逻辑，抽离出来
    
* mixin 并不是最完美的解决方案，会有一些问题
    
* Vue3 提出的 CompositionAPI 旨在解决这些问题
    

mixin 缺点

* 变量来源不明确，不利于阅读
    
* 多个 mixin 可能会造成命名冲突
    
* mixin 和组件可能会出现多对多的关系，复杂度高
    

​

## **Vuex 使用**

基本概念

* state
    
* getters
    
* action
    
* mutation
    

用于 vue 组件

* dispatch
    
* commit
    
* mapState
    
* mapGetters
    
* mapActions
    
* mapMutations
    

​

![image.png](https://static.ziying.site/yuque_img_upload/19b5c6a6-5346-309c-927f-e2c4539b783b.png align="left")

## **VueRouter**

* 路由模式，（hash，H5 history）
    
* 路由配置，（动态路由，懒加载）
    

​

# **Vue 原理**

* 组件化
    
* 响应式
    
* vdom 和 diff
    
* 模板编译
    
* 渲染过程
    
* 前端路由
    

​

## **组件化基础**

* “很久以前”就有组件化
    
* 数据驱动视图（MVVM，setState）
    

​

* 传统组件，只是静态渲染，更新还是要依赖于操作 DOM
    
* 数据驱动视图 - Vue MVVM
    
* 数据驱动视图 - React setState
    

​

## **Vue MVVM**

![image.png](https://static.ziying.site/yuque_img_upload/d743d1e5-725f-30be-b436-198c6def1f99.png align="left")

## **Vue 响应式**

* 核心 API Object.defineProperty
    
* proxy 有兼容性的问题，且无法 polyfill
    
* 监听对象，监听数组
    
* 复杂对象，深度监听
    
* 几个缺点
    

​

* Object.defineProperty 深度监听，需要递归到底，一次性计算量大
    
* 无法监听新增属性，删除属性
    
* 无法监听原生数组，需要做特殊处理
    

​

## **虚拟 DOM 和 diff**

* vdom 是实现 vue 和 React 的重要基石
    
* diff 算法是 vdom 中最核心最关键的部分
    
* vdom 是一个热门话题，也是面试中最热门的话题
    

​

* DOM 的操作非常耗费性能
    
* 以前使用 jQuery，可以自行控制 DOM 操作的时机，手动调整
    
* Vue 和 React 是数据驱动视图，如何有效的控制 DOM 操作
    

​

* 有了一定复杂度，想减少计算次数比较难
    
* 能不能把计算，更多的转移为 JS 计算，因为 JS 执行速度很快
    
* vdom - 用 js 模拟 DOM 结构，计算出最小的变更，操作 DOM
    

​

* vue3 重写了 vdom 的代码，优化了性能
    
* 但是 vdom 的基本里边不变，面试考点也不变
    

​

## **snabbdom 使用**

* 用 JS 模拟 DOM 结构（vnode）
    
* 新旧 vnode 对比，得出最小的更新范围，最后更新 DOM
    
* 数据驱动视图的模式下，有效控制 DOM 的操作
    

​

## **diff 算法**

树 diff 的时间复杂度是 O(n^3)——算法不可用的 优化时间复杂度到 O(n)​

* 只比较同一层级，不跨级比较
    
* tag 不相同，则直接删掉重建，不再深度比较
    
* tag 和 key， 两者都相同，则认为是相同节点，不在深度比较
    

​

![image.png](https://static.ziying.site/yuque_img_upload/db84a17e-9dda-3743-a724-757f0c169f01.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/9309a393-d9ec-352f-8205-6395c77ee432.png align="left")

h 函数： 返回一个 vnode​

* patchNode
    
* addVnodes removeVNodes
    
* updateChildren
    

​

* 细节不重要，updateChildren 的过程也不重要，不要深究
    
* vdom 的核心概念很重要，h，vnode，patch、diff、key
    
* vdom 存在的价值更加重要：数据驱动视图，控制 DOM 操作
    

​

## **模板编译**

* 模板是 vue 开发中最常用的部分，即与使用相关联的原理
    
* 他不是 html，有指令、插值、JS 表达式到底是什么
    
* 面试不会直接问，但是会通过“组件渲染和更新过程”考察
    

​

* v-if 三元表达式
    
* v-for \_l renderList
    
* 事件
    
* v-model
    

​

vue-template-compiler​

## **组件 渲染/更新 过程**

* 响应式：监听 data 属性的 getter 和 setter （包括数组）
    
* 模板编译：模板到 render 函数，再到 vnode
    
* vdom ：patch(ele, vnode) patch(vnode, newVNode)
    

初次渲染的过程

* 解析模板为 render 函数，（或者在开发环境中已经完成，vue-loader）
    
* 触发响应式，监听 data 属性 getter setter
    
* 执行 render 函数，生成 vnode，patch(ele, vnode)
    

​

更新过程

* 修改 data， 触发 setter（此前在 getter 中已被监听）
    
* 重新执行 render 函数，生成 newVNode
    
* patch(vnode, newVnode)
    

​

![image.png](https://static.ziying.site/yuque_img_upload/7c8b976c-2056-3f7b-8f59-a06c4ae8af58.png align="left")

​

​

异步渲染

* 回顾$nexttick
    
* 汇总 data 的修改，一次性更新视图
    
* 减少 DOM 的操作次数，提高性能
    

​

## **前端路由的原理**

路由模式

* hash
    
* history
    

​

hash 的特点

* hash 变化会触发网页的跳转，即浏览器的前进后退
    
* hash 变化不会刷新页面，SPA 必备特点
    
* hash 永远不会提交到 server 端
    

​

window.onhashchange = () =&gt; {}​

H5 history

* 用 url 规范的路由，但跳转时不刷新页面
    
* history.pushState
    
* window.onpopstate
    
* 需要后端配合
    

​

# **Vue 面试真题**

## **v-show v-if 区别**

## **为何在 v-for 中使用 key**

* 必须用 key，且不能是 index 和 random
    
* diff 算法中通过 tag 和 key 来判断，是否是 sameNode
    
* 减少渲染次数提升渲染性能
    

​

## **描述 Vue 组件的生命周期**

* 单组件的生命周期图
    
* 父子组件生命周期关系
    

## **Vue 组件如何通讯**

* 父子组件 props 和 this.$emit
    
* 自定义事件，event.$on event.$off event.$emit
    
* vuex
    

​

## **描述组件渲染和更新的过程**

![image.png](https://static.ziying.site/yuque_img_upload/1bb1a69d-d720-3597-b7a8-bf3e9f419b70.png align="left")

## **双向数据绑定 v-model 的实现原理**

* ipnut 元素的 value = this.name
    
* 绑定 input 事件 this.name = $event.target.value
    
* data 更新触发 re-render
    

​

## **对 mvvm 的理解**

## **computed 有何特点**

* 缓存，data 不变不会重新计算
    
* 提高性能
    

​

## **为何组件 data 必须是一个函数**

## **ajax 请求应该放在那个生命周期中**

* mounted
    
* js 是单线程的，ajax 异步获取数据
    
* 放在 mounted 之前没有用只会让逻辑更加复杂
    

​

## **如何将组件所有 props 传递给子组件**

* v-bind="$props"
    

​

## **如何自己实现一个 v-model**

## **多个组件有相同的逻辑，怎么抽离**

mixin​

## **何时要使用 异步组件**

* 加载大组件
    
* 路由
    

​

## **何时需要使用 keep-alive**

* 缓存组件，不需要重复渲染
    
* 性能优化
    

## **何时需要使用 beforeDestory**

* 解绑自定义事件 event.$off
    
* 清除定时器
    
* 解绑自定义的 DOM 事件
    

​

## **什么是作用域插槽**

## **Vuex 中 action 和 mutation 有什么区别**

![image.png](https://static.ziying.site/yuque_img_upload/0f5de666-28f2-3115-921a-0ee3a804c0f3.png align="left")

## **vue-router 常用的路由模式**

## **vue-router 异步加载**

## **请用 vnode 描述一个 DOM 结构**

## **监听 data 变化的核心 API 是什么**

## **Vue 如何监听数组变化**

## **请描述响应式原理**

## **Diff 算法的时间复杂度**

## **简述 diff 算法的过程**

![image.png](https://static.ziying.site/yuque_img_upload/c4fdbb01-1a77-3cdd-a5f6-a5021ffd7e0d.png align="left")

## **Vue 为何是异步渲染，$nextTick 何用**

## **Vue 性能优化**

* 合理使用 v-show 和 v-if
    
* 合理使用 computed
    
* v-for 时加 key ，避免和 v-if 同时使用
    
* 自定义事件，以及 DOM 事件要及时销毁
    
* 合理使用 异步组件
    
* 合理使用 keep-alive
    
* data 层级不要太深
    
* 使用 vue-loader 在开发环境做模板预编译
    
* webpack 层的优化
    
* 前端通用的优化，图片懒加载
    
* 使用 SSR
    

# **Vue3**

## **Vue3 对 Vue2 有什么优势**

* 性能更小
    
* 体积更小
    
* 更好的 TS 开发的
    
* 更好的代码组织
    
* 更好的逻辑抽离
    

​

## **Composition API 和 Options API**

* 不建议共用，会引起混乱
    
* 小型项目业务逻辑简单，用 Options API
    
* 中大型项目、复杂逻辑，用 Composition API
    

## **ref**

* 生成值类型的响应式数据
    
* 可用于模板和 reactive
    
* 通过 .value 修改值
    

​

## **toRef**

* 针对一个响应式对象（reactive 封装）的 prop
    
* 创建一个 ref，具有响应式
    
* 两者保持引用关系
    

​

## **toRefs**

* 将响应式对象（reactive 封装）转换为普通对象
    
* 对象的每一个 prop 都是对应的 ref
    
* 两者保持引用关系
    

​

## **toRef 和 toRefs 的最佳使用方式**

* 用 reactive 做对象的响应式，用 ref 做值类型的响应式
    
* setup 中返回 toRefs(state) 或者 toRef(state, 'xxx')
    
* ref 的变量命名都用 xxxRef
    
* 合成函数返回响应式对象时，使用 toRefs
    

​

​

## **深入理解 ref**

为什么使用 ref

* 返回值类型，会丢失响应式
    
* 如 setup, computed，合成函数，都有可能返回值类型
    
* Vue 如不定义 ref，用户会自造 ref，反而混乱
    

​

为什么需要.value

* ref 是一个对象（不丢失响应式），value 存储值
    
* 通过 .value 属性的 get 和 set 实现响应式
    
* 用于模板、reactive 时，不需要.value，其他情况下都需要
    

​

## **为什么需要 toRef 和 toRefs**

初衷：不丢失响应式的情况下，把数据对象 分解/扩散 前提：针对的是响应式对象（reactive 封装的）非普通对象 注意：不创造响应式，而是延续响应式​

## **vue 升级了哪些重要的功能**

* createApp
    
* emit 属性
    
* 生命周期
    
* 多事件
    
* Fragment
    
* 移除 .sync
    
* 异步组件的写法
    
* 移除 filter
    
* suspense
    
* composition API
    

​

## **Vue2 如何实现响应式**

Object.defineProperty 的缺点

* 深度监听需要一次性递归
    
* 无法监听新增属性和删除属性
    
* 无法监听数组，需要特殊处理
    

![image.png](https://static.ziying.site/yuque_img_upload/c777b75f-28b1-333b-83bd-43e48f711b6a.png align="left")

​

Reflect 作用

* 和 Proxyu 能力一一对应
    
* 规范化、标准化、函数式
    
* 代替 object 的工具函数
    

​

Proxy 实现响应式

* 深度监听，性能更好
    
* 可监听 新增、删除属性
    
* 可监听数组变化
    

​

![image.png](https://static.ziying.site/yuque_img_upload/e2c8d619-2f22-302b-8259-aac909c98edd.png align="left")

## **watch 和 watchEffect 区别**

* 两者都可以监听 data 属性变化
    
* watch 需要明确监听哪个属性
    
* watchEffect 会根据其中的属性，自动监听其变化
    

​

![image.png](https://static.ziying.site/yuque_img_upload/2a8ac94b-6162-3216-b6af-fddc8b8df928.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/c75fbfbe-b100-3d0a-a1cf-1cab92165990.png align="left")

​

​

## **setup 中如何获取组件的实例**

* 在 setup 和其他 compositionAPI 中没有 this
    
* 可以通过 getCurrentInstance 获取当前实例
    
* 若使用 options API 可照常使用 this
    

​

## **Vue3 为何比 Vue2 快**

* Proxy 响应式
    
* PatchFlag
    
* hoistStatic
    
* cacheHandler
    
* SSR 优化
    
* tree-shaking
    

​

PatchFlag

* 编译模板时，动态节点做标记
    
* 标记，分为不同类型，如 TEXT，PROPS
    
* diff 算法时，可以区分静态节点，以及不同类型的动态节点
    

​

![image.png](https://static.ziying.site/yuque_img_upload/ff745ad0-6005-30da-a26c-b94442b6a8fc.png align="left")

## **hoistStatic**

* 将静态节点的定义，提升到父作用域，缓存起来
    
* 多个相邻的静态节点会被合并起来
    
* 典型的那空间换时间的优化策略
    

​

## **cacheHandler**

* 缓存事件
    

​

## **SSR 优化**

* 静态节点直接输出，绕过了 vdom
    
* 动态节点，还是需要动态渲染
    

​

## **vite 是什么**

* 一个前端的打包工具，Vue 作者发起的项目
    
* 借助 Vue 的影响力，发展较快，和 webpack 竞争
    
* 优势： 开发环境下无需打包，启动快
    

​

Vite 为何启动快

* 开发环境使用 ES Module，无需打包——非常快
    
* 生产环境下使用 rollup，并不会快很多
    

es module： type='module'​

## **Composition API 和 react hooks 对比**

* 前者 setup 只会调用一次，而后者函数会被调用很多次
    
* 前者无需调用 useMemo，useCallback 因为 setup 只会调用一次
    
* 前者无需顾虑调用的顺序，而后者需要保证 hooks 的顺序一致
    
* 前者 reactive 和 ref 比后者 useState，要更加难以理解
    

​

## **Vue3 和 JSX**

![image.png](https://static.ziying.site/yuque_img_upload/23c97ed5-2fcc-3257-b110-b2c4a93545ef.png align="left")

jsx 和 template 区别

* 语法上是有很大的区别的
    
* 本质是相同的
    
* 具体示例，插值，自定义组件，属性和事件，条件和循环
    
* jsx 的本质就是 js 代码，可以使用 js 的任何能力
    
* template 只能嵌入简单的 js 表达式，其他需要指令，如 v-if
    
* jsx 已经成为 es 规范，template 还是 Vue 自家的规范
    

​

​

## **Vue3 script setup**

# **React**

## **关于 react 17**

* 没有明显的新特性，使用是和 react 16 是一致的
    
* 面试时也不会被重点考察
    

## **React 基本使用**

​

## **事件**

* bind this
    
* 关于 event 参数
    
* 传递自定义参数
    

​

react 中的 event 不是原生的 event ，而是 syntheticEvent（组合事件）

## **react 事件和 DOM 事件的区别**

* event 是 SyntheticEvent ，模拟出原生事件所有的能力
    
* event.nativeEvent 是原生事件对象
    
* 多有的时间都被挂载到 document 上
    
* 和 DOM 时间不一样，和 Vue 事件也不一样
    

​

![image.png](https://static.ziying.site/yuque_img_upload/907f72ea-161e-3edc-86d1-b6d77607c75e.png align="left")

React 16 绑定到 document 上 react 17 绑定在 root 组件上 有利于多个 react 版本并存，例如微前端​

![image.png](https://static.ziying.site/yuque_img_upload/8cad46b0-5d08-34a3-8fbf-3d5d9c16202f.png align="left")

## **表单**

* 受控组件
    
* input textarea select 用 value
    
* checkbox radio 用 checked
    

​

​

## **setState**

* 不可变值
    
* 可能是异步更新
    
* 可能会被合并
    

​

setState 是同步还是异步的

* 正常情况下是异步的
    
* setTimeout 中 setState 是同步的
    
* 自定义 DOM 事件中也是同步的
    

​

setState 可能会被合并

* 传入对象会被合并
    
* 传入函数不会被合并
    

​

## **单组件生命周期**

![image.png](https://static.ziying.site/yuque_img_upload/4b068451-2ac2-32e9-8d5a-6e49b0b228a8.png align="left")

[生命周期](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## **React 高级特性**

* 函数组件
    
* 非受控组件
    
* Portals
    
* context
    
* 异步组件
    
* 性能优化
    
* 高阶组件 HOC
    
* Render Props
    

​

### **函数组件**

* 输入 props 输出 jsx
    
* 没有实例，没有生命周期，没有 state
    
* 不能扩展其他方法
    

​

### **什么是非受控组件**

* ref
    
* defaultValue defaultChecked
    
* 手动操作 DOM 元素
    

​

使用场景

* 必须手动操作 DOM 元素，setState 实现不了
    
* 文件上传，input type='file'
    
* 某些富文本编辑器，需要传入 DOM 元素
    

受控组件 vs 非受控组件

* 优先使用受控组件，符合 React 设计原则
    
* 必须操作 DOM 时，再使用非受控组件
    

​

### **Portals**

* 组件默认会按照既定的层级嵌套渲染
    
* 如何让组件渲染到父组件外
    

​

ReactDOM.createPortals​

![image.png](https://static.ziying.site/yuque_img_upload/14a177fe-bbd3-3d33-bb65-2483ed87dccb.png align="left")

### **context**

* 公共信息（语言，主题）如何传递给每个组件
    
* 用 props 太繁琐
    
* 用 redux 小题大做
    

​

### **react 如何加载异步组件**

![image.png](https://static.ziying.site/yuque_img_upload/83816d3b-5eb1-3836-958d-170d313eefa4.png align="left")

### **性能优化**

* shouldComponentUpdate
    
* PureComponent 和 React.memo
    
* 不可变值 immutable.js
    

![image.png](https://static.ziying.site/yuque_img_upload/6bfc22e9-ff5d-3ad5-b0a6-f22ddeb05fce.png align="left")

React 默认：父组件更新，子组件则默认无条件更新 性能优化对于 React 更加重要！​

​

SCU 一定每次都要用吗——需要的时候才会优化​

shouldComponentUpdate 在做深层比较的时候，如果使用 isEqual 会对数组或者对象做深层比较，（一次性递归到底）​

* SCU 默认返回 true，即 React 默认重新渲染所有子组件
    
* 必须配合不可变值一起使用
    
* 可先不使用 shouldComponentUpdate ，有性能问题时在考虑使用
    

### **PureComponent 和 memo**

* PureComponent，scu 中实现了浅比较
    
* React.memo. 函数组件中的 PureComponent
    
* 浅比较已经适用大部分情况（尽量不要做深度比较）
    

​

### **immutable.js**

* 彻底拥抱“不可变值”
    
* 基于共享数据（不是深拷贝），速度好
    
* 有一定学习和迁移成本，按需使用
    

![image.png](https://static.ziying.site/yuque_img_upload/58a8a9bf-1afb-3893-83d9-2c16e53ba9ef.png align="left")

## **关于组件公共逻辑的抽离**

* mixin 已经被 React 废弃
    
* 高阶组件 HOC
    
* render props
    

​

高阶组件不是一种功能，而是一种模式

* 透传所有 props（Vue 中 v-bind $props）
    
* 增加 mouse 属性
    

​

redux connect 是高阶组件​

向组件属性中传入 render 函数

​

​

## **Redux 使用**

* 基本概念
    
* 单向数据流
    
* react-redux
    
* 异步 action
    
* 中间件
    

基本概念

* store state
    
* action
    
* reducer
    

​

流程

* dispatch(action)
    
* reducer -&gt; newState
    
* subscribe 触发通知
    

​

react-redux

* connect
    
* mapStateToProps mapDispatchToProps
    

​

![image.png](https://static.ziying.site/yuque_img_upload/4f6977ff-f400-3d78-a1d1-84cff2c8e00b.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/c445d1e5-29f9-30cc-accd-91ff3bc71795.png align="left")

* redux-thunk
    
* redux-promise
    
* redux-saga
    

​

![image.png](https://static.ziying.site/yuque_img_upload/32baa8ec-7864-3c57-a56d-e3f76ef3285a.png align="left")

## **react router**

* 路由模式（hash ，H5 history）
    
* 路由配置（动态路由，懒加载）
    
* 掌握基本使用
    

​

# **React 原理**

* 大厂使用 React 概率更高
    
* react 对开发人员要求更高
    
* 大厂更偏爱考察原理
    

​

* 函数式编程
    
* vdom 和 diff 算法
    
* JSX 的本质
    
* 合成事件
    
* setState batchUpdate
    
* 组件渲染过程
    

​

## **函数式编程**

* 一种编程范式，概念比较多
    
* 纯函数
    
* 不可变值
    

​

vdom 和 diff

* h 函数
    
* 返回 vnode 数据结构
    
* patch 函数
    

​

diff 算法的改造

* 只比较同一层级，不跨级比较
    
* tag 相同，则之间删掉重建，不再深度比较
    
* tag 和 key ，两者都相同，则认为是相同节点，不在深度比较
    

​

* Vue2 Vue3 React 三者实现 vdom 细节均不相同
    
* 核心概念和实现思路都一样
    
* 面试主要考察后者，不用全部掌握细节
    

​

JSX 的本质

* JSX 等同于 Vue 的模板
    
* Vue 模板不是 HTML
    
* JSX 也不是 JS
    

​

* React.createElement 即 h 函数，返回 vnode
    
* 第一个参数，可能是组件，也可能是 html tag
    
* 组件名，首字母必须大写（React 规定）
    

​

## **react 合成事件机制**

![image.png](https://static.ziying.site/yuque_img_upload/6b784461-5c17-3119-9b90-f1384a03bc0b.png align="left")

​

## **为什么要合成事件机制**

* 更好的兼容性和跨平台
    
* 挂载到 document 上，减少内存消耗，避免频繁解绑
    
* 方便事件的统一管理
    

​

![image.png](https://static.ziying.site/yuque_img_upload/b39f62b5-870f-3894-9c81-e2a0eb4b0af9.png align="left")

## **React 的 batchUpdate 机制**

* 有的时候是异步的（普通使用），有时同步（setTimeout，DOM 事件）
    
* 有时合并（对象形式），有时不合并（函数形式）
    
* 后者比较好理解，向 Object.assign ，主要讲解后者
    

​

* setState 主流程
    
* batchUpdate 机制
    
* transaction （事物）机制
    

​

![image.png](https://static.ziying.site/yuque_img_upload/59888bb1-d570-3f5e-a8e0-05dfc1ca5a8c.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/a6f7c455-2925-38be-affb-e33794a0f084.png align="left")

* setState 无所谓异步还是同步
    
* 看是否可以命中 batchUpdate 机制
    
* 判断 isBatchingUpdates
    

​

那些可以命中 batchUpdate 机制

* 生命周期（和它调用的函数）
    
* React 中注册的时间（和它调用的函数）
    
* React 可以“管理”的入口
    

​

* setTimeout setInterval 等（和它调用的函数）
    
* 自定义的 DOM 事件（和它调用的函数）
    
* React “管不到”的入口
    

​

## **简述 transaction 事务机制**

![image.png](https://static.ziying.site/yuque_img_upload/ee6404fd-735c-3477-89b2-456f599b0f83.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/df736e9c-2f41-3508-a43c-f892c09edc10.png align="left")

## **组件渲染和更新过程**

* JSX 如何渲染为页面
    
* setState 之后如何更新页面
    
* 面试考察全流程
    

​

* props state
    
* render() 生成 vnode
    
* patch(elem, vnode)
    

​

* setState(newState) --&gt; dirtyComponents(可能有子组件)
    
* render() 生成 newVnode
    
* patch(vnode, newVnode)
    

​

## **更新的两个阶段**

* 上述 patch 被拆分成了两个阶段
    
* reconciliation 阶段 - 执行 diff 算法，纯 JS 计算
    
* commit 阶段 - 将 diff 结果渲染 DOM
    

​

如果不拆分成两个阶段，可能会有性能问题

* js 是单线程，且和 DOM 渲染公用一个线程
    
* 当组件足够复杂，组件更新时计算和渲染都压力大
    
* 同时再有 DOM 操作需求，（动画，鼠标拖拽），将卡顿
    

​

解决方案 fiber

* 将 reconciliation 阶段进行任务拆分，（commit 无法拆分）
    
* DOM 需要渲染时暂停，空闲时恢复
    
* window.requestIdleCallback
    

​

# **React 面试真题**

## **组件间如何通讯**

## **JSX 的本质是什么**

## **context 是什么如何应用**

## **shouldComponentUpdate 的用途**

## **redux 单向数据流**

## **setState 场景题**

![image.png](https://static.ziying.site/yuque_img_upload/738e0e9d-11b0-388d-933a-50837eb582f5.png align="left")

## **什么是纯函数**

## **React 组件证明周期（单组件，父子组件）**

## **ajax 应该在那个生命周期上**

## **渲染列表，为何使用 key**

## **函数组件和 class 组件的区别**

## **什么是受控组件**

## **何时使用异步组件**

## **多个组件有公共逻辑，如何抽离**

## **redux 如何进行异步请求**

## **react-router 如何配置懒加载**

![image.png](https://static.ziying.site/yuque_img_upload/64c84e3b-5adc-3c0b-9ce8-451ae484e3bb.png align="left")

## **PureComponent 有何区别**

## **React 事件和 DOM 事件的区别**

## **React 性能优化**

* 渲染列表时使用 key
    
* 自定义事件 DOM 事件及时销毁
    
* 合理使用异步组件
    
* 减少函数 bind this 的次数
    
* 合理使用 shouldComponentUpdate PureComponent 和 memo
    
* 合理使用 Immuta.js
    
* webpack 层面的优化
    
* 前端通用的性能优化，如图片懒加载
    
* 使用 SSR
    

​

## **React 和 Vue 的区别**

共同点

* 都支持组件化
    
* 都是数据驱动视图
    
* 都使用 vdom 操作 DOM
    

​

不同点

* React 使用 jsx 拥抱 js ，vue 使用模板拥抱 html
    
* React 函数式编程，Vue 声明式编程
    
* React 更多的需要自力更生，Vue 把想要的都给你
    

​

# **Webpack**

* webpack 已经是前端打包构建的不二选择
    
* 每日必用，面试必考
    
* 成熟的工具，重点在于配置和使用，原理并不高优
    

​

## **webpack 5**

* webpack 5 主要是内部效率的优化
    
* 对于 webpack4 ，没有太多使用上的改动
    
* 你可以直接使用 webpack5
    

​

## **webpack 基本配置**

* 拆分配置 和 merge
    
* 启动本地服务
    
* 处理 es6
    
* 处理样式
    
* 处理图片
    
* （模块化）
    

​

​

postcss 兼容性处理​

## **webpack 高级配置**

* 多入口
    

![image.png](https://static.ziying.site/yuque_img_upload/2a71770d-85d3-3ed4-9c26-7ef8d0970a4a.png align="left")

* 抽离 css 文件
    

![image.png](https://static.ziying.site/yuque_img_upload/1db35e9d-f721-3317-a045-0d88d379349f.png align="left")

* 抽离公共代码
    

![image.png](https://static.ziying.site/yuque_img_upload/f4a30d70-3a76-347c-9488-626ef8a8830e.png align="left")

* 懒加载
    
* 处理 jsx 处理 vue
    

​

## **module chunk bundle 的区别**

* module - 各个源码文件，webpack 中一切皆模块
    
* chunk - 多模块合成的 如 entry import() splitChunk
    
* bundle - 最终输出的文件
    

![image.png](https://static.ziying.site/yuque_img_upload/f270bbc8-ea78-3af9-9ddc-f75a093366d6.png align="left")

## **webpack 性能优化**

webpack 怎么优化打包构建速度，开发体验和效率 优化产出代码 - 产品性能​

​

优化 babel-loader

![image.png](https://static.ziying.site/yuque_img_upload/a330c6d5-80fb-3db7-bb0a-6f8d5743bf3a.png align="left")

ignorePlugin 避免引用无用模块

![image.png](https://static.ziying.site/yuque_img_upload/c2c2390b-5f18-37f8-9ea5-6f315d64e0c9.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/4af3266e-5486-32c1-bf09-51a7749c0380.png align="left")

noParse 避免重复打包

![image.png](https://static.ziying.site/yuque_img_upload/380ef094-47e2-3775-8928-132bfd1b5ecc.png align="left")

ignorePlugin vs noParse

* IgnorePlugin 直接不引入，代码中没有
    
* noParse 引入，但不打包
    

​

happyPack 多进程打包

* JS 单线程，开启多进程打包
    
* 提高构建速度，特别是多核 CPU
    

![image.png](https://static.ziying.site/yuque_img_upload/da43e101-57d1-380d-987d-9d54ec3a22b2.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/94a6d419-46f1-3046-870d-79faad5f5eab.png align="left")

parallelUglifyPlugin 多进程压缩 JS

* webpack 内置 uglify 工具压缩 JS
    
* JS 单线程，开启多进程压缩更快
    
* 和 happyPack 同理
    

![image.png](https://static.ziying.site/yuque_img_upload/bef75ae9-82d2-326a-b648-0c577ccbbd2c.png align="left")

关于开启多线程

* 项目较大，打包较慢，开启多线程能提升速度
    
* 项目较小，打包较快，开启多进程会降低速度
    
* 按需使用
    

​

自动刷新

![image.png](https://static.ziying.site/yuque_img_upload/268cf8ae-f7ee-323d-83a5-0c6227e6d230.png align="left")

热更新

* 自动刷新：整个网页全部刷新，速度较慢
    
* 自动刷新网页的状态会丢失
    
* 热更新就是新代码生效，网页不刷新，状态不丢失
    

​

![image.png](https://static.ziying.site/yuque_img_upload/15c7d37d-257b-35df-877e-e5e7bbe870b1.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/7275c44a-ad19-3ae1-b3c1-a86945337995.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/1f23e4cd-d03d-3deb-99bc-72d6ac568737.png align="left")

dllPlugin 动态链接库插件

* 前端框架如 vue react 体积大，构建慢
    
* 较稳定，不常更新版本
    
* 同一个版本只构建一次即可，不用每次都重新构建
    

​

* webpack 已经内置了 DllPlugin 支持
    
* DllPlugin - 打包出 dll 文件
    
* DllReferencePlugin - 使用 dll 文件
    

​

```javascript
const path = require("path");
const DllPlugin = require("webpack/lib/DllPlugin");
const { srcPath, distPath } = require("./paths");

module.exports = {
  mode: "development",
  // JS 执行入口文件
  entry: {
    // 把 React 相关模块的放到一个单独的动态链接库
    react: ["react", "react-dom"],
  },
  output: {
    // 输出的动态链接库的文件名称，[name] 代表当前动态链接库的名称，
    // 也就是 entry 中配置的 react 和 polyfill
    filename: "[name].dll.js",
    // 输出的文件都放到 dist 目录下
    path: distPath,
    // 存放动态链接库的全局变量名称，例如对应 react 来说就是 _dll_react
    // 之所以在前面加上 _dll_ 是为了防止全局变量冲突
    library: "_dll_[name]",
  },
  plugins: [
    // 接入 DllPlugin
    new DllPlugin({
      // 动态链接库的全局变量名称，需要和 output.library 中保持一致
      // 该字段的值也就是输出的 manifest.json 文件 中 name 字段的值
      // 例如 react.manifest.json 中就有 "name": "_dll_react"
      name: "_dll_[name]",
      // 描述动态链接库的 manifest.json 文件输出时的文件名称
      path: path.join(distPath, "[name].manifest.json"),
    }),
  ],
};
```

![image.png](https://static.ziying.site/yuque_img_upload/bacc9ee8-2cbf-3f6d-b1bb-396840ed0e2f.png align="left")

webpack 优化构建速度（可以用于生产环境）

* 优化 babel-loader include exclude
    
* IgnorePlugins
    
* noParse
    
* happyPack
    
* ParallelUglifyPlugin
    

webpack 优化构建速度（不可用于生产环境）

* 自动刷新
    
* 热更新
    
* DllPlugin
    

​

webpack 性能优化 - 产出代码

* 体积更小
    
* 合理分包，不重复加载
    
* 速度更快，内存使用更小
    

​

* 小图片 base64 编码
    
* bundle 加 hash
    
* 懒加载
    
* 提取公共代码
    
* IgnorePlugin
    
* 使用 CDN 加速
    
* 使用 production
    
* Scope Hosting
    

​

## **使用 Production**

* 开启代码压缩
    
* vue react 等会删掉调试代码（如开发环境下的 warning）
    
* 启用 tree shaking
    

​

必须使用 ES6 Module 才能让 tree-shaking 生效 commonjs 就不行​

​

ES Module 和 Commonjs 的区别

* ES module 静态引入，编译时引入
    
* commonjs 动态引入，执行时引入
    
* 只有 ES6 Module 才能静态分析，实现 Tree-shaking
    

​

## **Scope Hosting**

* 代码体积会更小
    
* 创建函数作用域更少
    
* 代码的可读性更好
    

![image.png](https://static.ziying.site/yuque_img_upload/d37b5b04-5d93-329d-a7d5-15503509f40e.png align="left")

## **babel**

* 环境搭建
    
* .babelrc 配置
    
* preset 和 plugins
    

​

preset 是 plugins 的集合​

​

什么是 babel-polyfill

* 什么是 polyfill
    
* core-js 和 regenerator
    
* babel-polyfill 就是上面两者的集合
    

​

* babel-polyfill 在 babel 7.4 之后被弃用
    
* 推荐直接使用 core-js 和 regenerator
    

​

core-js： polyfill 集合​

​

babel-polyfill 如何按需引入

* 文件较大
    
* 只有一部分功能，无需全部引入
    
* 配置按需引入
    

​

```json
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "useBuiltIns": "usage",
        "corejs": 3
      }
    ]
  ],
  "plugins": [
    [
      "@babel/plugin-transform-runtime",
      {
        "absoluteRuntime": false,
        "corejs": 3,
        "helpers": true,
        "regenerator": true,
        "useESModules": false
      }
    ]
  ]
}
```

问题

* 污染了全局环境
    
* 如果做一个 web 系统，则无碍
    
* 如果是一个第三方的 lib，会有问题
    

​

## **babel-runtime**

​

​

# **Webpack 面试题**

## **前端为什么要进行打包构建**

* 体积更小（tree-shaking、压缩、合并），加载更快
    
* 编译高级语言或语法（TS，ES6+，模块化，scss）
    
* 兼容性和错误检查（Polyfill，postcss，eslint）
    

​

* 统一高校的开发环境
    
* 统一的构建流程和产出标准
    
* 继承公司构建规范（提测、上线）
    

​

## **module chunk bundle 的区别**

## **loader 和 plugins 的区别**

## **常见 loader 和 plugins**

## **babel 和 webpack 的区别**

## **如何产出一个 lib**

## **babel-polyfill 和 babel-runtime 的区别**

## **webpack 如何实现懒加载**

## **为何 Proxy 不能被 polyfill**

## **webpack 优化构建速度**

## **webpack 优化产出代码**

# **组件设计**

* 从功能上拆分层次
    
* 尽量让组件原子化
    
* 容器组件（只管理数据） UI 组件（只显示视图）
    

​

# **React Hooks**

* 可选功能
    
* 100% 向后兼容，没有破坏性改动
    
* 不会取代 class 组件，尚无计划要移除 class 组件
    

​

## **函数组件的特点**

* 没有组件实例
    
* 没有生命周期
    
* 没有 state 和 setState，只能接受 props
    

​

​

class 组件的问题

* 大型组件很难拆分和重构，很难测试（即 class 不易拆分）
    
* 相同业务逻辑，分散到各个方法中逻辑混乱
    
* 复用逻辑复杂，Mixins，HOC，Render Props
    

​

react 组件更易用函数表达

* react 倡导函数式编程
    
* 函数更灵活更易拆分，更易测试
    
* 但函数组件太简单，需要增强能力——hooks
    

​

## **state hook**

* 默认组件没有 state
    
* 函数组件是一个纯函数，执行完就销毁，无法储存 state
    
* 需要 state hook ，即把 state 功能“钩”到纯函数中
    

​

## **Effect**

* didMount didUpdate - useEffect
    
* didMount - useEffect(()=&gt;{},\[\])
    

​

![image.png](https://static.ziying.site/yuque_img_upload/913a870e-3b93-3379-9791-720d539247a9.png align="left")

## **模拟 unmount 的时候注意事项**

![image.png](https://static.ziying.site/yuque_img_upload/9ca97e58-966c-3561-974e-70972f53668e.png align="left")

## **其他 hooks**

* useRef
    
* useContext
    
* usereducer
    
* useMemo
    
* useCallback
    

​

![image.png](https://static.ziying.site/yuque_img_upload/f67f37b4-2fc5-374e-b581-f787380a939a.png align="left")

## **自定义 hooks**

* 封装通用的功能
    
* 开发和使用第三方 hooks
    
* 自定义 hook 带来无线的扩展性，解耦代码
    

​

## **Hooks 使用规范**

* 只能用于 react 组件和自定义 hook 中，其他地方不可以
    
* 只能用于顶层代码，不能用于循环判断中使用 hooks
    
* eslint 插件 eslint-plugin-react-hooks
    

​

## **为何 Hooks 要依赖于调用顺序**

* 函数组件，纯函数，执行完即销毁
    
* 所以，无论组件初始化，还是组件更新
    
* 都会执行过一次这个函数，获取最新的组件
    
* render： 初始化 state 的值 “张三”
    
* re-render：读取 state 的值 “张三”
    

​

* render： 添加 effect 函数
    
* re-render：替换 effect 函数，内部的函数也会重新定义
    

​

## **class 组件逻辑复用**

* mixin 早已废弃
    
* 高阶组件 HOC
    
* render props
    

​

mixin 问题

* 变量作用域来源不清楚
    
* 属性重名
    
* mixin 引入过多会导致顺序冲突
    

​

HOC

* 组件层级嵌套过多，不易渲染，不一调试
    
* HOC 会劫持 props，必须严格遵守规范，容易出现疏漏
    

​

render props

* 学习成本较高，不易理解
    
* 只能传递纯函数，默认情况下纯函数功能有限
    

​

## **Hooks 组件逻辑复用有什么好处**

* 完全符合 Hooks 原有规则，没有其他要求，易理解记忆
    
* 变量作用域很明确
    
* 不会产生组件嵌套
    

​

## **React Hooks 注意事项**

* useState 初始化值，只有第一次有效
    
* useEffect 不能修改 state
    
* useEffect 可能出现死循环