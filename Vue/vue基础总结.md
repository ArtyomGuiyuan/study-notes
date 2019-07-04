## Vue 基础总结

### 1.Vue 介绍
> Vue.js是一个轻巧、高性能、可组件化的MVVM库，同时拥有非常容易上手的API；
Vue.js是一个构建数据驱动的Web界面的库。
Vue.js是一套构建用户界面的 渐进式框架。与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。Vue的核心库只关注视图层，并且非常容易学习，非常容易与其它库或已有项目整合。另一方面，Vue 完全有能力驱动采用单文件组件和 Vue生态系统支持的库开发的复杂单页应用。数据驱动+组件化的前端开发。
简而言之：Vue.js是一个构建数据驱动的 web 界面的渐进式框架。Vue.js 的目标是通过尽可能简单的 API实现响应的数据绑定和组合的视图组件。核心是一个响应的数据绑定系统。

### 2.MVVM
> MVVM 是 Model-View-ViewModel 的缩写。mvvm 是一种设计思想。Model 层代表数据模型，也可以在 Model 中定义数据修改和操作的业务逻辑；View 代表 UI 组件，它负责将数据模型转化成 UI 展现出来，ViewModel 是一个同步 View 和 Model 的对象。

### 3.Vue的响应式原理
> 当一个Vue实例创建时，vue会遍历data选项的属性，用 Object.defineProperty 将它们转为 getter/setter并且在内部追踪相关依赖，在属性被访问和修改时通知变化。
每个组件实例都有相应的 watcher 程序实例，它会在组件渲染的过程中把属性记录为依赖，之后当依赖项的 setter 被调用时，会通知 watcher 重新计算，从而致使它关联的组件得以更新。

### 4.Vue特点
#### 两个核心 数据驱动 组件系统
> 简洁：页面由HTML模板+Json数据+Vue实例组成
数据驱动：自动计算属性和追踪依赖的模板表达式
组件化：用可复用、解耦的组件来构造页面
轻量：代码量小，不依赖其他库
快速：精确有效批量DOM更新
模板友好：可通过npm，bower等多种方式安装，很容易融入

### 5.scss 
> 预处理css，把css当前函数编写，定义变量,嵌套.

### 6.vue生命周期函数
> 总共分为 8 个阶段创建前/后，载入前/后，更新前/后，销毁前/后。
创建前/后： 在 beforeCreate 阶段，vue 实例的挂载元素 el 还没有。
载入前/后：在 beforeMount 阶段，vue 实例的$el 和 data 都初始化了，但还是挂载之前为虚拟的 dom 节点，data.message 还未替换。在 mounted 阶段，vue 实例挂载完成，data.message 成功渲染。
更新前/后：当 data 变化时，会触发 beforeUpdate 和 updated 方法。
销毁前/后：在执行 destroy 方法后，对 data 的改变不会再触发周期函数，说明此时 vue 实例已经解除了事件监听以及和 dom 的绑定，但是 dom 结构依然存在。

### 7.为什么vue中的data必须是一个对象
> 对象为引用类型，当重用组件时，由于数据对象都指向同一个data对象，当在一个组件中修改data时，其他重用的组件中的data会同时被修改；而使用返回对象的函数，由于每次返回的都是一个新对象（Object的实例），引用地址不同，则不会出现这个问题。

### 8.vue-cli
> assets文件夹是放静态资源；
components是放组件；
router是定义路由相关的配置;
view视图；
app.vue是一个应用主组件；
main.js是入口文件

### 9.computed 和watch 的区别
> computed 计算属性是用来声明式的描述一个值依赖了其它的值。当你在模板里把数据绑定到一个计算属性上时，Vue 会在其依赖的任何值导致该计算属性改变时更新 DOM。这个功能非常强大，它可以让你的代码更加声明式、数据驱动并且易于维护。

>watch 监听的是你定义的变量,当你定义的变量的值发生变化时，调用对应的方法。就好在div写一个表达式name，data里写入num和lastname,firstname,在watch里当num的值发生变化时，就会调用num的方法，方法里面的形参对应的是num的新值和旧值，而计算属性computed,计算的是Name依赖的值,它不能计算在data中已经定义过的变量。


### 10.prop验证和默认值

> 我们在父组件给子组件传值得时候，为了避免不必要的错误，可以给prop的值进行类型设定，让父组件给子组件传值得时候，更加准确，prop可以传一个数字，一个布尔值，一个数组，一个对象，以及一个对象的所有属性。组件可以为 props 指定验证要求。如果未指定验证要求，Vue 会发出警告比如传一个number类型的数据，用defalt设置它的默认值，如果验证失败的话就会发出警告。

```js
props: {
    visible: {
        default: true,
        type: Boolean,
        required: true
    },
},
```

### 11.vue组件通信
+ 父传递子
父：自定义属性名 + 数据（要传递）=> :value="数据"
子：props ["父组件上的自定义属性名“] =>进行数据接收)
+ 子传递父
在父组件中注册子组件并在子组件标签上绑定自定义事件的监听。
子：this.$emit('自定义事件名称', 数据) 子组件标签上绑定@自定义事件名称='回调函数'
父：methods: {自定义事件() {//逻辑处理} }
+ 兄弟组件
通过中央通信 let bus = new Vue()
A：methods :{ 函数{bus.$emit('自定义事件名'，数据)} 发送
B：created （）{bus.$on('A发送过来的自定义事件名'，函数)} 进行数据接收

### 12.路由传参
> 1.使用query方法传入的参数使用this.$route.query接受
2.使用params方式传入的参数使用this.$route.params接受

### 13.vuex
> Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。
有 5 种，分别是 state、getter、mutation、action、module
+ store 
vuex 就是一个仓库，仓库里放了很多对象。其中 state 就是数据源存放地，对应于一般 vue 对象里面的 datastate 里面存放的数据是响应式的，vue 组件从 store 读取数据，若是 store 中的数据发生改变，依赖这相数据的组件也会发生更新它通过 mapState 把全局的 state 和 getters 映射到当前组件的 computed 计算属性
+  getter
getter 可以对 state 进行计算操作，它就是 store 的计算属性虽然在组件内也可以做计算属性，但是 getters 可以在多给件之间复用如果一个状态只在一个组件内使用，是可以不用 getters
+  mutation 
更改Vuex的store中的状态的唯一方法是提交mutation
+ action 
action 类似于 muation, 不同在于：action 提交的是 mutation,而不是直接变更状态action 可以包含任意异步操作
vue 中 ajax 请求代码应该写在组件的 methods 中还是 vuex 的 action 中
+  module 
面对复杂的应用程序，当管理的状态比较多时；我们需要将vuex的store对象分割成模块(modules)。

### 14.v-show 和v-if
> v-show指令是通过修改元素的displayCSS属性让其显示或者隐藏(频率高的采用)
v-if指令是直接销毁和重建DOM达到让元素显示和隐藏的效果(频率低的采用)

### 15.让CSS只在当前组件中起作用
> 将当前组件的style修改为style scoped

### 16.<keep-alive></keep-alive>的作用
> 会缓存不活动的组件实例,主要用于保留组件状态或避免重新渲染。

### 17.delete和Vue.delete删除数组
> delete只是被删除的元素变成了 empty/undefined 其他的元素的键值还是不变。 
> Vue.delete直接删除了数组 改变了数组的键值。

### 18.$nextTick
> vue实现响应式并不是数据发生变化后dom立即变化，而是按照一定的策略来进行dom更新。
$nextTick 是在下次 DOM 更新循环结束之后执行延迟回调，在修改数据之后使用 $nextTick，则可以在回调中获取更新后的 DOM

### 19. v-on 
> 可以监听多个方法

> 常用修饰符
> .stop 该修饰符将阻止事件向上冒泡。同理于调用 event.stopPropagation() 方法
.prevent 该修饰符会阻止当前事件的默认行为。同理于调用 event.preventDefault() 方法
.self 该指令只当事件是从事件绑定的元素本身触发时才触发回调
.once 该修饰符表示绑定的事件只会被触发一次

### 20.v-for key的作用
> 当Vue用 v-for 正在更新已渲染过的元素列表是，它默认用“就地复用”策略。如果数据项的顺序被改变，Vue将不是移动DOM元素来匹配数据项的改变，而是简单复用此处每个元素，并且确保它在特定索引下显示已被渲染过的每个元素。
为了给Vue一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 key 属性。key属性的类型只能为 string或者number类型。
key 的特殊属性主要用在 Vue 的虚拟 DOM 算法，在新旧 nodes 对比时辨识 VNodes。如果不使用 key，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试修复/再利用相同类型元素的算法。使用 key，它会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。

### 21.v-for 与 v-if 的优先级
> v-for比v-if优先，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候。

### 22.Promise对象
> 1.Promise是异步编程的一种解决方案，它是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。promise对象是一个构造函数，用来生成Promise实例；
2.promise的两个特点   对象状态不受外界影响 && 一旦状态改变，就不会再变，任何时候都可以得到结果（pending状态-->fulfilled || pending-->rejected）

### 23.axios
> 1、axios是一个基于promise的HTTP库，支持promise的所有API；
2、它可以拦截请求和响应；
3、它可以转换请求数据和响应数据，并对响应回来的内容自动转换为json类型的数据；
4、它安全性更高，客户端支持防御XSRF；

### 24.vue中的 ref
>ref 被用来给元素或子组件注册引用信息。引用信息将会注册在父组件的 $refs 对象上。如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例。

### 25.vue的路由模式
>hash模式 和 history模式

+ hash模式：在浏览器中符号“#”，#以及#后面的字符称之为hash，用window.location.hash读取；
特点：hash虽然在URL中，但不被包括在HTTP请求中；用来指导浏览器动作，对服务端安全无用，hash不会重加载页面。
hash 模式下:仅 hash 符号之前的内容会被包含在请求中，如 http://www.xxx.com，因此对于后端来说，即使没有做到对路由的全覆盖，也不会返回 404 错误。
+ history模式：history采用HTML5的新特性；且提供了两个新方法：pushState（），replaceState（）可以对浏览器历史记录栈进行修改，以及popState事件的监听到状态变更。
history 模式:前端的 URL 必须和实际向后端发起请求的 URL 一致，如 http://www.xxx.com/items/id。后端如果缺少对 /items/id 的路由处理，将返回 404 错误。Vue-Router 官网里如此描述：“不过这种模式要玩好，还需要后台配置支持……所以呢，你要在服务端增加一个覆盖所有情况的候选资源：如果 URL 匹配不到任何静态资源，则应该返回同一个 index.html 页面，这个页面就是你 app 依赖的页面。”

### 26.$route和$router的区别
> $route是“路由信息对象”，包括path，params，hash，query，fullPath，matched，name等路由信息参数。
$router是'路由实例'对象包括了路由的跳转方法，钩子函数等。

### 27.页面刷新vuex被清空解决方法
> 1.localStorage 存储到本地再回去
2.重新获取接口获取数据

### 28.Vue 改变数组触发视图更新
> 以下方法调用会改变原始数组：

+ push() 数组尾添加元素并返回新的长度 
+ pop() 删除并返回数组最后一个元素
+ shift() 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。
+ unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。
+ splice() 方法向/从数组中添加/删除项目，然后返回被删除的项目。（该方法会改变原始数组）
+ sort() 排序
+ reverse() 翻转数组
+ Vue.set( target, key, value )
> 调用方法：Vue.set( target, key, value )
target：要更改的数据源(可以是对象或者数组)
key：要更改的具体数据
value ：重新赋的值

### 29.DOM 渲染在哪个周期中就已经完成？
> mounted
注意 mounted 不会承诺所有的子组件也都一起被挂载。如果你希望等到整个视图都渲染完毕，可以用 vm.$nextTick 替换掉 mounted
```js
mounted: function () {
  this.$nextTick(function () {
    // Code that will run only after the
    // entire view has been rendered
  })
}
```

### 30.每个周期具体适合哪些场景
> beforecreate : 可以在这加个loading事件，在加载实例时触发
created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用
mounted : 挂载元素，获取到DOM节点 updated : 如果对数据统一处理，在这里写上相应函数
beforeDestroy : 可以做一个确认停止事件的确认框 

### 31.第一次加载会触发哪几个钩子
> beforeCreate , created ,beforeMount ,mounted

### 32.动态绑定class
> active classname， isActive 变量
```js
<div v-bind:class="{ active: isActive }"></div>
```


















