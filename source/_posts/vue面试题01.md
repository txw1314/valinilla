---
title: vue面试题01
author: 作者
tags: 标签
categories: 分类
description: 这是摘要
comments: true
music:
  server: netease
  type: song
  id: 1916550868
date: 2022-11-01 11:11:18
updated: 2022-11-01 11:11:18
index_img:
banner_img:
headimg:
img:
cover:
---

为了金三银四的跳槽季做准备，并且我是 `vue` 技术栈的，所以整理了若干个 `vue` 的面试题。

每次看别人的博客，都会不自主的去看答案，为了方便检验自己的掌握程度，我特意将答案折叠起来，大家可以先看题目，在脑海中想象一下如果你被问到会怎么回答，然后再展开答案看看和自己的答案有什么不同。

答案非官方，仁者见仁智者见智，仅供参考。

# 基础使用

## MVVM、MVC有什么区别

<details> 
<p><code>MVC</code> 通过分离 <code>Model</code>、<code>View</code> 和 <code>Controller</code> 的方式来组织代码结构。</p>
<ul>
<li>其中 <code>View</code> 负责页面的显示逻辑，</li>
<li><code>Model</code> 负责存储页面的业务数据，以及对相应数据的操作。</li>
<li><code>Controller</code> 层是 <code>View</code> 层和 <code>Model</code> 层的纽带，它主要负责用户与应用的响应操作，当用户与页面产生交互的时候，<code>Controller</code> 中的事件触发器就开始工作了，通过调用 <code>Model</code> 层，来完成对 <code>Model</code> 的修改，然后 <code>Model</code> 层再去通知 <code>View</code> 层更新。</li>
</ul>
<p><code>MVVM</code> 分为 <code>Model</code>、<code>View</code>、<code>ViewModel</code>。</p>
<ul>
<li><code>Model</code> 代表数据模型，数据和业务逻辑都在 <code>Model</code> 层中定义；</li>
<li><code>View</code> 代表 <code>UI</code> 视图，负责数据的展示；</li>
<li><code>ViewMode</code> 负责监听 <code>Model</code> 中数据的改变并且控制视图的更新，处理用户交互操作；</li>
</ul>
<p><code>Model</code> 和 <code>View</code> 并无直接关联，而是通过 <code>ViewModel</code> 来进行联系的，<code>Model</code> 和 <code>ViewModel</code> 之间有着双向数据绑定的联系。因此当 <code>Model</code> 中的数据改变时会触发 <code>View</code> 层的刷新，<code>View</code> 中由于用户交互操作而改变的数据也会在 <code>Model</code> 中同步。
这种模式实现了 <code>Model</code> 和 <code>View</code> 的数据自动同步，因此开发者只需要专注于数据的维护操作即可，而不需要自己操作 <code>DOM</code>。</p>
<p><code>Vue</code> 并没有完全遵循 <code>MVVM</code> 思想呢？</p>
<ul>
<li>严格的 <code>MVVM</code> 要求 <code>View</code> 不能和 <code>Model</code> 直接通信，而 <code>Vue</code> 提供了 <code>$refs</code> 这个属性，让 <code>Model</code> 可以直接操作 <code>View</code>，违反了这一规定，所以说 <code>Vue</code> 没有完全遵循 <code>MVVM</code>。</li>
</ul>
</details>

## Vue的优点

<details> 
<ul>
<li>
<p><strong>渐进式框架</strong>：可以在任何项目中轻易的引入；</p>
</li>
<li>
<p><strong>轻量级框架</strong>：只关注视图层，是一个构建数据的视图集合，大小只有几十 <code>kb</code> ；</p>
</li>
<li>
<p><strong>简单易学</strong>：国人开发，中文文档，不存在语言障碍 ，易于理解和学习；</p>
</li>
<li>
<p><strong>双向数据绑定</strong>：在数据操作方面更为简单；</p>
</li>
<li>
<p><strong>组件化</strong>：很大程度上实现了逻辑的封装和重用，在构建单页面应用方面有着独特的优势；</p>
</li>
<li>
<p><strong>视图，数据，结构分离</strong>：使数据的更改更为简单，不需要进行逻辑代码的修改，只需要操作数据就能完成相关操作；</p>
</li>
</ul>
</details>

## 对 SPA 单页面的理解，它的优缺点分别是什么？

<details> 
<p><code>SPA</code> 仅在 <code>Web</code> 页面初始化时加载相应的 <code>HTML</code>、<code>JavaScript</code> 和 <code>CSS</code>。一旦页面加载完成，<code>SPA</code> 不会因为用户的操作而进行页面的重新加载或跳转；取而代之的是利用路由机制实现 <code>HTML</code> 内容的变换，<code>UI</code> 与用户的交互，避免页面的重新加载。</p>
<p><strong>优点：</strong></p>
<ul>
<li>用户体验好、快，内容的改变不需要重新加载整个页面，避免了不必要的跳转和重复渲染；</li>
<li>有利于前后端职责分离，架构清晰，前端进行交互逻辑，后端负责数据处理；</li>
</ul>
<p><strong>缺点：</strong></p>
<ul>
<li>初次加载耗时多：为实现单页 <code>Web</code> 应用功能及显示效果，需要在加载页面的时候将 <code>JavaScript</code>、<code>CSS</code> 统一加载，部分页面按需加载；</li>
<li>不利于 <code>SEO</code>：由于所有的内容都在一个页面中动态替换显示，所以在 <code>SEO</code> 上其有着天然的弱势。</li>
</ul>
</details>

## 怎样理解 Vue 的单向数据流？

<details> 
<p>父级 <code>prop</code> 的更新会向下流动到子组件中，但是反过来则不行。这样会防止从子组件意外改变父级组件的状态，从而导致你的应用的数据流向难以理解。</p>
<p>每次父级组件发生更新时，子组件中所有的 <code>prop</code> 都将会刷新为最新的值。在子组件内部改变 <code>prop</code> 的时候 ， <code>Vue</code> 会在浏览器的控制台中发出警告。</p>
<p>子组件想修改时，只能通过 <code>$emit</code> 派发一个自定义事件，父组件接收到后，由父组件修改。</p>
<p>有两种常见的试图改变一个 <code>prop</code> 的情形 :</p>
<ul>
<li>
<p>这个 <code>prop</code> 用来传递一个初始值；这个子组件接下来希望将其作为一个本地的 <code>prop</code> 数据来使用。&nbsp;在这种情况下，最好定义一个本地的 <code>data</code> 属性并将这个 <code>prop</code> 用作其初始值：</p>
</li>
<li>
<p>这个 <code>prop</code> 以一种原始的值传入且需要进行转换。&nbsp;在这种情况下，最好使用这个 <code>prop</code> 的值来定义一个计算属性</p>
</li>
</ul>
</details>

## Data为什么是一个函数？

<details> 
<p>因为组件是用来复用的，且 <code>JS</code> 里对象是引用关系，如果组件中 <code>data</code> 是一个对象，那么这样作用域没有隔离，子组件中的 <code>data</code> 属性值会相互影响，如果组件中 <code>data</code> 选项是一个函数，那么每个实例可以维护一份被返回对象的独立的拷贝，组件实例之间的 <code>data</code> 属性值不会互相影响；而 <code>new Vue</code> 的实例，是不会被复用的，因此不存在引用对象的问题。</p>
</details>

## Computed和Watch 有什么区别？

<details> 
<p><strong>对于Computed：</strong></p>
<ul>
<li>它支持缓存，只有依赖的数据发生了变化，才会重新计算</li>
<li>不支持异步，当 <code>Computed</code> 中有异步操作时，无法监听数据的变化</li>
<li>如果一个属性是由其他属性计算而来的，这个属性依赖其他的属性，一般会使用 computed</li>
<li>如果 <code>computed</code> 属性的属性值是函数，那么默认使用 <code>get</code> 方法，函数的返回值就是属性的属性值；在 <code>computed</code> 中，属性有一个 <code>get</code> 方法和一个 <code>set</code> 方法，当数据发生变化时，会调用 <code>set</code> 方法。</li>
</ul>
<p><strong>对于Watch：</strong></p>
<ul>
<li>它不支持缓存，当一个属性发生变化时，它就会触发相应的操作</li>
<li>支持异步监听</li>
<li>监听的函数接收两个参数，第一个参数是最新的值，第二个是变化之前的值</li>
<li>监听数据必须是 <code>data</code> 中声明的或者父组件传递过来的 <code>props</code> 中的数据，当发生变化时，会触发其他操作</li>
<li>函数有两个的参数：
<ul>
<li><strong>immediate</strong>：组件加载立即触发回调函数</li>
<li><strong>deep</strong>：深度监听，发现数据内部的变化，在复杂数据类型中使用，例如数组中的对象发生变化。</li>
</ul>
</li>
</ul>
</details>

## Computed 和 Methods 的区别

<details> 
<p><strong>共同点：</strong></p>
<p>可以将同一函数定义为一个 <code>method</code> 或者一个计算属性。对于最终的结果，两种方式是相同的。</p>
<p><strong>不同点：</strong></p>
<ul>
<li><strong>computed</strong>: 计算属性是基于它们的依赖进行缓存的，只有在它的相关依赖发生改变时才会重新求值；</li>
<li><strong>method</strong>: 调用总会执行该函数。</li>
</ul>
</details>

## .Sync的作用是什么？

<details> 
<p><code>vue</code> 修饰符 <code>sync</code> 的功能是：当父组件提供了一个数据，而子组件想要去更改这个数据，但是 <code>Vue</code> 的规则不能让子组件去修改父组件的数据，就需要通过&nbsp;<code>this.$emit</code>&nbsp;和&nbsp;<code>$event</code>，来实现数据修改的目的。</p>
<pre><code class="hljs language-js copyable" lang="js">:money.<span class="hljs-property">sync</span>=<span class="hljs-string">"total"</span> 
<span class="hljs-comment">// 等价于 </span>
:money=<span class="hljs-string">"total"</span> v-<span class="hljs-attr">on</span>:<span class="hljs-attr">update</span>:money=<span class="hljs-string">"total = $event"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 绑定事件@click=handler 和@click=handler（） 那个正确？有什么区别？

<details> 
<p>都可以，不带括号会传进来一个事件对象，带括号的不会</p>
</details>

## 事件有哪些修饰符？

<details> 
<p><strong>「事件修饰符」</strong></p>
<ul>
<li><strong>.stop</strong> 阻止事件继续传播</li>
<li><strong>.prevent</strong> 阻止标签默认行为</li>
<li><strong>.capture</strong> 使用事件捕获模式,即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理</li>
<li><strong>.self</strong> 只当在 <code>event.target</code> 是当前元素自身时触发处理函数</li>
<li><strong>.once</strong> 事件将只会触发一次</li>
<li><strong>.passive</strong> 告诉浏览器你不想阻止事件的默认行为</li>
</ul>
<p><strong>「v-model 的修饰符」</strong></p>
<ul>
<li><strong>.lazy</strong> 通过这个修饰符，转变为在 <code>change</code> 事件再同步</li>
<li><strong>.number</strong> 自动将用户的输入值转化为数值类型</li>
<li><strong>.trim</strong> 自动过滤用户输入的首尾空格</li>
</ul>
<p><strong>「键盘事件的修饰符」</strong></p>
<ul>
<li><strong>.enter</strong></li>
<li><strong>.tab</strong></li>
<li><strong>.delete</strong> (捕获“删除”和“退格”键)</li>
<li><strong>.esc</strong></li>
<li><strong>.space</strong></li>
<li><strong>.up</strong></li>
<li><strong>.down</strong></li>
<li><strong>.left</strong></li>
<li><strong>.right</strong></li>
</ul>
<p><strong>「系统修饰键」</strong></p>
<ul>
<li><strong>.ctrl</strong></li>
<li><strong>.alt</strong></li>
<li><strong>.shift</strong></li>
<li><strong>.meta</strong></li>
</ul>
<p><strong>「鼠标按钮修饰符」</strong></p>
<ul>
<li><strong>.left</strong></li>
<li><strong>.right</strong></li>
<li><strong>.middle</strong></li>
</ul>
</details>

## 什么是插槽？具名插槽？作用域插槽？原理是什么？

<details> 
<p><code>slot</code> 又名插槽，是 <code>Vue</code> 的内容分发机制，插槽 <code>slot</code> 是子组件的一个模板标签元素，而这一个标签元素是否显示，以及怎么显示是由父组件决定的。<code>slot</code> 又分三类，默认插槽，具名插槽和作用域插槽。</p>
<ul>
<li><strong>默认插槽</strong>：又名匿名插槽，当 <code>slot</code> 没有指定 <code>name</code> 属性值的时候，默认显示的插槽，一个组件内只允许有一个匿名插槽。</li>
<li><strong>具名插槽</strong>：带有具体名字的插槽，也就是带有 <code>name</code> 属性的 <code>slot</code>，一个组件可以出现多个具名插槽。</li>
<li><strong>作用域插槽</strong>：可以是匿名插槽，也可以是具名插槽，该插槽在渲染时，父组件可以使用子组件内部的数据。</li>
</ul>
<p>实现原理：当子组件 <code>vm</code> 实例化时，获取到父组件传入的 <code>slot</code> 标签的内容，存放在 <code>vm.$slot</code> 中，默认插槽为 <code>vm.$slot.default</code>，具名插槽为 <code>vm.$slot.xxx</code>，<code>xxx</code> 为插槽名，当组件执行渲染函数时候，遇到 <code>slot</code> 标签，使用 <code>$slot</code> 中的内容进行替换，此时可以为插槽传递数据，若存在数据，则可称该插槽为作用域插槽。</p>
</details>

## Vue中如何实现过度效果？如何实现列表过度？

<details> 
<p>过渡效果，当然只有 <code>dom</code> 从显示到隐藏或隐藏到显示才能用</p>
<p><code>Vue.js</code> 为我们提供了内置的过渡组件 <code>transition</code> 和 <code>transition-group</code></p>
<p><code>Vue</code> 将元素的过渡分为四个阶段，进入前，进入后，消失前，消失后</p>
<p>支持 <code>mode</code> 属性，可选值：</p>
<ul>
<li><code>in-out</code>:要进入的先进入，然后要消失的再消失</li>
<li><code>out-in</code>:要消失的先消失，然后要进入的再进入</li>
</ul>
<p>多个元素需要加上过渡效果可以使用 <code>name</code> 属性进行区分。</p>
<p>可以配合 <code>animate.css</code> 实现更多的动画效果。</p>
</details>

## 过滤器的作用，如何实现一个过滤器

<details> 
<p>过滤器是用来过滤数据的，在 <code>Vue</code> 选项中声明 <code>filters</code> 来实现一个过滤器，<code>filters</code>不会修改数据，而是处理数据，改变用户看到的输出。</p>
<p><strong>使用场景：</strong></p>
<ul>
<li>需要格式化数据的情况，比如需要处理时间、价格等数据格式的输出 / 显示。</li>
<li>比如后端返回一个 <strong>年月日的日期字符串</strong>，前端需要展示为 <strong>多少天前</strong> 的数据格式，此时就可以用<code>fliters</code> 过滤器来处理数据。</li>
</ul>
<p>过滤器是一个函数，它会把表达式中的值始终当作函数的第一个参数。过滤器用在 <strong>插值表达式</strong> <code>{{ }}</code> 和 <code>v-bind</code> <strong>表达式</strong> 中，然后放在操作符 <code>|</code> 后面进行指示。</p>
<p>例如，在显示金额，给商品价格添加单位：</p>
<pre><code class="hljs language-js copyable" lang="js">&lt;li&gt;商品价格：{{item.<span class="hljs-property">price</span> | filterPrice}}&lt;/li&gt;

 <span class="hljs-attr">filters</span>: {
    filterPrice (price) {
      <span class="hljs-keyword">return</span> price ? (<span class="hljs-string">'￥'</span> + price) : <span class="hljs-string">'--'</span>
    }
  }
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## assets和static的区别

<details> 
<p><strong>相同点：</strong>&nbsp;<code>assets</code>&nbsp;和&nbsp;<code>static</code>&nbsp;两个都是存放静态资源文件。项目中所需要的资源文件图片，字体图标，样式文件等都可以放在这两个文件下，这是相同点</p>
<p><strong>不相同点：</strong> <code>assets</code>&nbsp;中存放的静态资源文件在项目打包时，也就是运行&nbsp;<code>npm run build</code>&nbsp;时会将&nbsp;<code>assets</code>&nbsp;中放置的静态资源文件进行打包上传，所谓打包简单点可以理解为压缩体积，代码格式化。而压缩后的静态资源文件最终也都会放置在&nbsp;<code>static</code>&nbsp;文件中跟着&nbsp;<code>index.html</code>&nbsp;一同上传至服务器。<code>static</code>&nbsp;中放置的静态资源文件就不会要走打包压缩格式化等流程，而是直接进入打包好的目录，直接上传至服务器。因为避免了压缩直接进行上传，在打包时会提高一定的效率，但是&nbsp;<code>static</code>&nbsp;中的资源文件由于没有进行压缩等操作，所以文件的体积也就相对于&nbsp;<code>assets</code>&nbsp;中打包后的文件提交较大点。在服务器中就会占据更大的空间。</p>
<p><strong>建议：</strong>&nbsp;将项目中&nbsp;<code>template</code>需要的样式文件js文件等都可以放置在&nbsp;<code>assets</code>&nbsp;中，走打包这一流程。减少体积。而项目中引入的第三方的资源文件如<code>iconfoont.css</code>&nbsp;等文件可以放置在&nbsp;<code>static</code>&nbsp;中，因为这些引入的第三方文件已经经过处理，我们不再需要处理，直接上传。</p>
</details>

## 对SSR的理解

<details> 
<p><code>SSR</code> 大致的意思就是 <code>vue</code> 在客户端将标签渲染成的整个 <code>html</code> 片段的工作在服务端完成，服务端形成的 <code>html</code> 片段直接返回给客户端，这个过程就叫做服务端渲染。</p>
<p><strong>（1）服务端渲染的优点：</strong></p>
<ul>
<li>更好的 <code>SEO</code>：<code>SSR</code> 是直接由服务端返回已经渲染好的页面（数据已经包含在页面中），所以搜索引擎爬取工具可以抓取渲染好的页面；</li>
<li>首屏加载更快：<code>SPA</code> 会等待所有 <code>Vue</code> 编译后的 <code>js</code> 文件都下载完成后，才开始进行页面的渲染，文件下载等需要一定的时间等，所以首屏渲染需要一定的时间；<code>SSR</code> 直接由服务端渲染好页面直接返回显示，无需等待下载 <code>js</code> 文件及再去渲染等，所以 <code>SSR</code> 有更快的内容到达时间；</li>
</ul>
<p><strong>（2) 服务端渲染的缺点：</strong></p>
<ul>
<li>更多的开发条件限制：例如服务端渲染只支持 <code>beforCreate</code> 和 <code>created</code> 两个钩子函数，</li>
<li>不能进行 <code>dom</code> 操作。</li>
</ul>
<p>这会导致一些外部扩展库需要特殊处理，才能在服务端渲染应用程序中运行。</p>
</details>

## Vue的性能优化有哪些

<details> 
<p><strong>（1）代码层面的优化</strong></p>
<ul>
<li><code>v-if</code> 和 <code>v-show</code> 区分使用场景</li>
<li><code>computed</code> 和 <code>watch</code> 区分使用场景</li>
<li><code>v-for</code> 遍历必须为 <code>item</code> 添加 <code>key</code>，且避免同时使用 <code>v-if</code></li>
<li>长列表性能优化</li>
<li>事件的销毁</li>
<li>图片资源懒加载</li>
<li>路由懒加载</li>
<li>第三方插件的按需引入</li>
<li>优化无限列表性能</li>
<li>服务端渲染</li>
</ul>
<p><strong>（2）Webpack 层面的优化</strong></p>
<ul>
<li><code>Webpack</code> 对图片进行压缩</li>
<li>减少 <code>ES6</code> 转为 <code>ES5</code> 的冗余代码</li>
<li>提取公共代码</li>
<li>模板预编译</li>
<li>提取组件的 <code>CSS</code></li>
<li>优化 <code>SourceMap</code></li>
<li>构建结果输出分析</li>
<li><code>Vue</code> 项目的编译优化</li>
</ul>
<p><strong>（3）基础的 Web 技术的优化</strong></p>
<ul>
<li>开启 <code>gzip</code> 压缩</li>
<li>浏览器缓存</li>
<li><code>CDN</code> 的使用</li>
<li>使用 <code>Chrome Performance</code> 查找性能瓶颈</li>
</ul>
</details>

## Vue的首屏加载性能优化有哪些

<details> 
<p>优化前的大小</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cffa135cb86240efb3f90f53e5c46c64~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
<p>1.图片优化</p>
<p>之前为了方便开法， 背景图片直接在 <code>assets</code> 里面扔了一个 <code>jpg</code> ， 导致加载这张图片的时候就用了十几秒， 于是乎我就把图片上传空间了， 然后改用网络地址。</p>
<p>2.禁止生成.map文件</p>
<p><code>build</code> 出来的 <code>dist</code> 文件夹里面有很多的 <code>.map</code> 文件,这些文件主要是帮助线上调试代码，禁止生成这些文件.</p>
<p>在 <code>vue.config.js</code> 里面加上这句。</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bd4c4766c76a4d22ba4d2e198df2a7b6~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
<p>3.路由懒加载</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9333ab755a304c378a9c22de47aa11a9~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
<p>4.cdn引入公共库</p>
<pre><code class="hljs language-js copyable" lang="js">    &lt;link rel=<span class="hljs-string">"stylesheet"</span> href=<span class="hljs-string">"https://unpkg.com/element-ui/lib/theme-chalk/index.css"</span>&gt;
    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"https://cdn.bootcss.com/vue/2.6.11/vue.min.js"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">script</span>&gt;</span></span>
    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"https://unpkg.com/element-ui/lib/index.js"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">script</span>&gt;</span></span>
    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"https://cdn.bootcss.com/vuex/3.0.1/vuex.min.js"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">script</span>&gt;</span></span>
    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"https://cdn.bootcss.com/vue-router/3.0.1/vue-router.min.js"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">script</span>&gt;</span></span>
    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"https://cdn.bootcss.com/axios/0.19.2/axios.min.js"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">script</span>&gt;</span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js">    <span class="hljs-comment">//cdn引入</span>
    <span class="hljs-attr">configureWebpack</span>: {
        <span class="hljs-attr">externals</span>: {
            <span class="hljs-string">'vue'</span>: <span class="hljs-string">'Vue'</span>,
            <span class="hljs-string">'element-ui'</span>: <span class="hljs-string">'ELEMENT'</span>,
            <span class="hljs-string">'vue-router'</span>: <span class="hljs-string">'VueRouter'</span>,
            <span class="hljs-string">'vuex'</span>: <span class="hljs-string">'Vuex'</span>,
            <span class="hljs-string">'axios'</span>: <span class="hljs-string">'axios'</span>
        }
    }
<span class="copy-code-btn">复制代码</span></code></pre>
<p>网上说可以把 <code>import</code> 注释掉，亲自操作会报错，也有资料说不用注释也不会打包。</p>
<p>一顿操作最后的文件,效果显著，app.js还是很大</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e46843b470dc4b4d9d7b7a82e577031a~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
<p>5.终极法宝 GZIP压缩</p>
<p>做完这个感觉前四步都是小菜一碟，直接把 <code>1.4m</code> 的 <code>app.js</code> 干成一百多 <code>kb</code> ,其他的都不足挂齿了。</p>
<pre><code class="hljs language-js copyable" lang="js"> <span class="hljs-attr">configureWebpack</span>: <span class="hljs-function"><span class="hljs-params">config</span> =&gt;</span> {
        <span class="hljs-keyword">return</span> {
            <span class="hljs-comment">//配置cdn</span>
            <span class="hljs-attr">externals</span>: {
                <span class="hljs-string">'vue'</span>: <span class="hljs-string">'Vue'</span>,
                <span class="hljs-string">'element-ui'</span>: <span class="hljs-string">'ELEMENT'</span>,
                <span class="hljs-string">'vue-router'</span>: <span class="hljs-string">'VueRouter'</span>,
                <span class="hljs-string">'vuex'</span>: <span class="hljs-string">'Vuex'</span>,
                <span class="hljs-string">'axios'</span>: <span class="hljs-string">'axios'</span>
            },
            <span class="hljs-comment">//配置gzip压缩</span>
            <span class="hljs-attr">plugins</span>: [
                <span class="hljs-keyword">new</span> <span class="hljs-title class_">CompressionWebpackPlugin</span>({

                    <span class="hljs-attr">test</span>: <span class="hljs-keyword">new</span> <span class="hljs-title class_">RegExp</span>(<span class="hljs-string">'\.(js|css)$'</span>),
                    <span class="hljs-attr">threshold</span>: <span class="hljs-number">10240</span>,
                    <span class="hljs-attr">minRatio</span>: <span class="hljs-number">0.8</span>
                })
            ],
        }
    }
<span class="copy-code-btn">复制代码</span></code></pre>
<p>服务端也要配，不然不认识 <code>GZIP</code> 文件。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//配置GZIP压缩模块</span>
<span class="hljs-keyword">const</span> compression = <span class="hljs-built_in">require</span>(<span class="hljs-string">'compression'</span>);
<span class="hljs-comment">//在所有中间件之前引入</span>
app.<span class="hljs-title function_">use</span>(<span class="hljs-title function_">compression</span>());
<span class="copy-code-btn">复制代码</span></code></pre>
<p>最垃圾的服务器通过以上几个优化,一样飞起来了!!!</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9434af0d30cc4201b299aac3898a2539~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
</details>

## vue初始化页面闪动问题

<details> 
<p>使用 <code>vue</code> 开发时，在 <code>vue</code> 初始化之前，由于&nbsp;<code>div</code>&nbsp;是不归&nbsp;<code>vue</code>&nbsp;管的，所以我们写的代码在还没有解析的情况下会容易出现花屏现象，看到类似于&nbsp;<code>{{message}}</code>&nbsp;的字样，虽然一般情况下这个时间很短暂，但是我们还是有必要让解决这个问题的。</p>
<p>首先：在 <code>css</code> 里加上&nbsp;<code>[v-cloak] { display: none; }</code>&nbsp;。如果没有彻底解决问题，则在根元素加上 <code>style="display: none;" :style="{display: &nbsp;block }"</code></p>
</details>

## Class 与 Style 如何动态绑定？

<details> 
<p><code>Class</code> 可以通过对象语法和数组语法进行动态绑定：</p>
<ul>
<li>对象语法：</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">&lt;div&nbsp;v-<span class="hljs-attr">bind</span>:<span class="hljs-keyword">class</span>=<span class="hljs-string">"{&nbsp;active:&nbsp;isActive,&nbsp;'text-danger':&nbsp;hasError&nbsp;}"</span>&gt;&lt;/div&gt;

<span class="hljs-attr">data</span>:&nbsp;{
&nbsp;&nbsp;<span class="hljs-attr">isActive</span>:&nbsp;<span class="hljs-literal">true</span>,
&nbsp;&nbsp;<span class="hljs-attr">hasError</span>:&nbsp;<span class="hljs-literal">false</span>
}
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>数组语法：</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">&lt;div&nbsp;v-<span class="hljs-attr">bind</span>:<span class="hljs-keyword">class</span>=<span class="hljs-string">"[isActive&nbsp;?&nbsp;activeClass&nbsp;:&nbsp;'',&nbsp;errorClass]"</span>&gt;&lt;/div&gt;

<span class="hljs-attr">data</span>:&nbsp;{
&nbsp;&nbsp;<span class="hljs-attr">activeClass</span>:&nbsp;<span class="hljs-string">'active'</span>,
&nbsp;&nbsp;<span class="hljs-attr">errorClass</span>:&nbsp;<span class="hljs-string">'text-danger'</span>
}
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>Style</code> 也可以通过对象语法和数组语法进行动态绑定：</p>
<ul>
<li>对象语法：</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">&lt;div&nbsp;v-<span class="hljs-attr">bind</span>:style=<span class="hljs-string">"{&nbsp;color:&nbsp;activeColor,&nbsp;fontSize:&nbsp;fontSize&nbsp;+&nbsp;'px'&nbsp;}"</span>&gt;&lt;/div&gt;

<span class="hljs-attr">data</span>:&nbsp;{
&nbsp;&nbsp;<span class="hljs-attr">activeColor</span>:&nbsp;<span class="hljs-string">'red'</span>,
&nbsp;&nbsp;<span class="hljs-attr">fontSize</span>:&nbsp;<span class="hljs-number">30</span>
}
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>数组语法：</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">&lt;div&nbsp;v-<span class="hljs-attr">bind</span>:style=<span class="hljs-string">"[styleColor,&nbsp;styleSize]"</span>&gt;&lt;/div&gt;

<span class="hljs-attr">data</span>:&nbsp;{
&nbsp;&nbsp;<span class="hljs-attr">styleColor</span>:&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-attr">color</span>:&nbsp;<span class="hljs-string">'red'</span>
&nbsp;&nbsp;&nbsp;},
&nbsp;&nbsp;<span class="hljs-attr">styleSize</span>:{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-attr">fontSize</span>:<span class="hljs-string">'23px'</span>
&nbsp;&nbsp;}
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 如何让CSS只在当前组件中起作用?

<details> 
<p>在组件中的&nbsp;<code>style</code>&nbsp;标签中加上&nbsp;<code>scoped</code></p>
</details>

## 如何获取dom

<details> 
<p><code>ref="domName"</code>&nbsp;用法：<code>this.$refs.domName</code></p>
</details>

## vue-loader是什么？使用它的用途有哪些？

<details> 
<p><code>vue</code> 文件的一个加载器，把 <code>template/js/style</code>转换成 <code>js</code> 模块。</p>
</details>

# 生命周期

## Vue有哪些生命周期钩子?

<details> 
<p><code>Vue</code> 的生命周期钩子核心实现是利用发布订阅模式先把用户传入的的生命周期钩子订阅好（内部采用数组的方式存储）然后在创建组件实例的过程中会一次执行对应的钩子方法（发布）。</p>
<ul>
<li><code>beforeCreate</code>：是 <code>new Vue()</code> 之后触发的第一个钩子，在当前阶段 <code>data</code>、<code>methods</code>、<code>computed</code> 以及 <code>watch</code> 上的数据和方法都不能被访问。</li>
<li><code>created</code>：在实例创建完成后发生，当前阶段已经完成了数据观测，也就是可以使用数据，更改数据，在这里更改数据不会触发 <code>updated</code> 函数。可以做一些初始数据的获取，在当前阶段无法与 <code>Dom</code> 进行交互，如果非要想，可以通过 <code>vm.$nextTick</code> 来访问 <code>Dom</code>。</li>
<li><code>beforeMount</code>：发生在挂载之前，在这之前 <code>template</code> 模板已导入渲染函数编译。而当前阶段虚拟 <code>Dom</code> 已经创建完成，即将开始渲染。在此时也可以对数据进行更改，不会触发 <code>updated</code>。</li>
<li><code>mounted</code>：在挂载完成后发生，在当前阶段，真实的 <code>Dom</code> 挂载完毕，数据完成双向绑定，可以访问到 <code>Dom</code> 节点，使用 <code>$refs</code> 属性对 <code>Dom</code> 进行操作。</li>
<li><code>beforeUpdate</code>：发生在更新之前，也就是响应式数据发生更新，虚拟 <code>dom</code> 重新渲染之前被触发，你可以在当前阶段进行更改数据，不会造成重渲染。</li>
<li><code>updated</code>：发生在更新完成之后，当前阶段组件 <code>Dom</code> 已完成更新。要注意的是避免在此期间更改数据，因为这可能会导致无限循环的更新。</li>
<li><code>beforeDestroy</code>：发生在实例销毁之前，在当前阶段实例完全可以被使用，我们可以在这时进行善后收尾工作，比如清除计时器。</li>
<li><code>destroyed</code>：发生在实例销毁之后，这个时候只剩下了 <code>dom</code> 空壳。组件已被拆解，数据绑定被卸除，监听被移出，子实例也统统被销毁。</li>
</ul>
</details>

## 如果需要发送异步请求，最好放在哪个钩子内？

<details>
<p>可以在钩子函数 <code>created</code>、<code>beforeMount</code>、<code>mounted</code> 中进行调用，因为在这三个钩子函数中，<code>data</code> 已经创建，可以将服务端端返回的数据进行赋值。</p>
<p>推荐在 <code>created</code> 钩子函数中调用异步请求，有以下优点：</p>
<ul>
<li>能更快获取到服务端数据，减少页面 <code>loading</code> 时间；</li>
<li><code>ssr</code> 不支持 <code>beforeMount</code> 、<code>mounted</code> 钩子函数，所以放在 <code>created</code> 中有助于一致性；</li>
</ul>
</details>

## 第一次页面加载会触发哪几个钩子？

<details> 
<p><code>beforeCreate</code>，<code>created</code>，<code>beforeMount</code>，<code>mounted</code></p>
</details>

## 哪个钩子可以进行dom操作？

<details> 
<p>在钩子函数 <code>mounted</code> 被调用前，<code>Vue</code> 已经将编译好的模板挂载到页面上，所以在 <code>mounted</code> 中可以访问操作 <code>DOM</code>。</p>
</details>

## 父子组件嵌套时，父组件和子组件生命周期钩子执行顺序是什么？

<details> 
<p><code>Vue</code> 的父组件和子组件生命周期钩子函数执行顺序可以归类为以下 <strong>4</strong> 部分：</p>
<ul>
<li>加载渲染过程 <code>父beforeCreate</code> -&gt; <code>父created</code> -&gt; <code>父beforeMount</code> -&gt; <code>子beforeCreate</code> -&gt; <code>子created</code> -&gt; <code>子beforeMount</code> -&gt; <code>子mounted</code> -&gt; <code>父mounted</code></li>
<li>子组件更新过程 <code>父beforeUpdate</code> -&gt; <code>子beforeUpdate</code> -&gt; <code>子updated</code> -&gt; <code>父updated</code></li>
<li>父组件更新过程 <code>父beforeUpdate</code> -&gt; <code>父updated</code></li>
<li>销毁过程 <code>父beforeDestroy</code> -&gt; <code>子beforeDestroy</code> -&gt; <code>子destroyed</code> -&gt; <code>父destroyed</code></li>
</ul>
</details>

## 父子组件嵌套时，父组件视图和子组件视图谁先完成渲染？

<details> 
<ul>
<li>加载渲染过程 <code>父beforeCreate</code> -&gt; <code>父created</code> -&gt; <code>父beforeMount</code> -&gt; <code>子beforeCreate</code> -&gt; <code>子created</code> -&gt; <code>子beforeMount</code> -&gt; <code>子mounted</code> -&gt; <code>父mounted</code></li>
</ul>
<p>可知子组件先完成渲染</p>
</details>

## keep-alive 中的生命周期哪些

<details> 
<ul>
<li>对应两个钩子函数 <code>activated</code> 和 <code>deactivated</code> ，当组件被激活时，触发钩子函数 <code>activated</code>，当组件被移除时，触发钩子函数 <code>deactivated</code>。</li>
</ul>
</details>

# 指令相关

## 说说 vue 内置指令

<details> 
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a9905a8c13994556bd06c00a89f3eca5~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp?" alt="640.webp" loading="lazy" class="medium-zoom-image"></p>
</details>

## 什么是自定义指令？有哪些生命周期？

<details> 
<p>是 <code>vue</code> 对 <code>HTML</code> 元素的扩展，给 <code>HTML</code> 元素增加自定义功能。<code>vue</code> 编译 <code>DOM</code> 时，会找到指令对象，执行指令的相关方法。</p>
<p>自定义指令有五个生命周期</p>
<ul>
<li><strong>bind</strong>：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。</li>
<li><strong>inserted</strong>：被绑定元素插入父节点时调用&nbsp;(仅保证父节点存在，但不一定已被插入文档中)。</li>
<li><strong>update</strong>：被绑定于元素所在的模板更新时调用，而无论绑定值是否变化。通过比较更新前后的绑定值，可以忽略不必要的模板更新。</li>
<li><strong>componentUpdated</strong>：被绑定元素所在模板完成一次更新周期时调用。</li>
<li><strong>unbind</strong>：只调用一次，指令与元素解绑时调用。</li>
</ul>
</details>

## v-text和v-html 有什么区别？

<details> 
<ul>
<li><code>v-text</code> 和 <code>{{}}</code> 表达式渲染数据，不解析标签。</li>
<li><code>v-html</code> 不仅可以渲染数据，而且可以解析标签。</li>
</ul>
</details>

## v-if和v-for的优先级

<details> 
<p>当&nbsp;<code>v-if</code>&nbsp;与&nbsp;<code>v-for</code>&nbsp;一起使用时，<code>v-for</code>&nbsp;具有比&nbsp;<code>v-if</code>&nbsp;更高的优先级，这意味着&nbsp;<code>v-if</code>&nbsp;将分别重复运行于每个&nbsp;<code>v-for</code>&nbsp;循环中。所以，不推荐&nbsp;<code>v-if</code>&nbsp;和&nbsp;<code>v-for</code>&nbsp;同时使用。如果&nbsp;<code>v-if</code>&nbsp;和&nbsp;<code>v-for</code>&nbsp;一起用的话，<code>vue</code> 中的的会自动提示&nbsp;<code>v-if</code>&nbsp;应该放到外层去。</p>
</details>

## V-if和v-show有什么区别？

<details> 
<ul>
<li>
<p><strong>手段</strong>：<code>v-if</code> 是动态的向 <code>DOM</code> 树内添加或者删除 <code>DOM</code> 元素；<code>v-show</code> 是通过设置 <code>DOM</code> 元素的 <code>display</code> 样式属性控制显隐；</p>
</li>
<li>
<p><strong>编译过程</strong>：<code>v-if</code> 切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件；<code>v-show</code> 只是简单的基于 <code>css</code> 切换；</p>
</li>
<li>
<p><strong>编译条件</strong>：<code>v-if</code> 是惰性的，如果初始条件为假，则什么也不做；只有在条件第一次变为真时才开始局部编译; <code>v-show</code> 是在任何条件下，无论首次条件是否为真，都被编译，然后被缓存，而且 <code>DOM</code> 元素保留；</p>
</li>
<li>
<p><strong>性能消耗</strong>：<code>v-if</code> 有更高的切换消耗；<code>v-show</code> 有更高的初始渲染消耗；</p>
</li>
<li>
<p><strong>使用场景</strong>：<code>v-if</code> 适合运营条件不大可能改变；<code>v-show</code> 适合频繁切换。</p>
</li>
</ul>
</details>

## 组件的v-model是如何实现的？

<details> 
<p>我们在 <code>vue</code> 项目中主要使用 <code>v-model</code> 指令在表单 <code>input</code>、<code>textarea</code>、<code>select</code> 等元素上创建双向数据绑定，我们知道 <code>v-model</code> 本质上不过是语法糖，<code>v-model</code> 在内部为不同的输入元素使用不同的属性并抛出不同的事件：</p>
<ul>
<li><code>text</code> 和 <code>textarea</code> 元素使用 <code>value</code> 属性和 <code>input</code> 事件；</li>
<li><code>checkbox</code> 和 <code>radio</code> 使用 <code>checked</code> 属性和 <code>change</code> 事件；</li>
<li><code>select</code> 字段将 <code>value</code> 作为 <code>prop</code> 并将 <code>change</code> 作为事件。</li>
</ul>
<p>以 <code>input</code> 表单元素为例：</p>
<pre><code class="hljs language-js copyable" lang="js">&lt;input&nbsp;v-model=<span class="hljs-string">'something'</span>&gt;
&nbsp;&nbsp;&nbsp;&nbsp;
<span class="hljs-comment">// 相当于</span>

<span class="xml"><span class="hljs-tag">&lt;<span class="hljs-name">input</span>&nbsp;<span class="hljs-attr">v-bind:value</span>=<span class="hljs-string">"something"</span>&nbsp;<span class="hljs-attr">v-on:input</span>=<span class="hljs-string">"something&nbsp;=&nbsp;$event.target.value"</span>&gt;</span>
</span><span class="copy-code-btn">复制代码</span></code></pre>
</details>

## v-model 可以被用在自定义组件上吗？如果可以，如何使用？

<details> 
<p>如果在自定义组件中，<code>v-model</code> 默认会利用名为 <code>value</code> 的 <code>prop</code> 和名为 <code>input</code> 的事件，如下所示：</p>
<pre><code class="hljs language-js copyable" lang="js">父组件：
&lt;<span class="hljs-title class_">ModelChild</span>&nbsp;v-model=<span class="hljs-string">"message"</span>&gt;&lt;/<span class="hljs-title class_">ModelChild</span>&gt;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js">子组件：
&lt;div&gt;{{value}}&lt;/div&gt;

<span class="hljs-attr">props</span>:{
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-attr">value</span>:&nbsp;<span class="hljs-title class_">String</span>
},
<span class="hljs-attr">methods</span>:&nbsp;{
&nbsp;&nbsp;<span class="hljs-title function_">test1</span>(<span class="hljs-params"></span>){
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-variable language_">this</span>.$emit(<span class="hljs-string">'input'</span>,&nbsp;<span class="hljs-string">'小红'</span>)
&nbsp;&nbsp;},
},
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## v-on可以监听多个方法吗？

<details> 
可以
<pre><code class="hljs language-js copyable" lang="js">&lt;input type=<span class="hljs-string">"text"</span> v-on=<span class="hljs-string">"{ input:onInput,focus:onFocus,blur:onBlur, }"</span>&gt;
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

# 组件相关

## 组件通信的N种方式

<details> 
<p><strong>（1）<code>props / $emit</code>&nbsp;适用 父子组件通信</strong></p>
<p><strong>（2）<code>ref</code>&nbsp;适用 父子组件通信</strong></p>
<ul>
<li><code>ref</code>：如果在普通的 <code>DOM</code> 元素上使用，引用指向的就是 <code>DOM</code> 元素；如果用在子组件上，引用就指向组件实例</li>
</ul>
<p><strong>（3）<code>$parent</code>&nbsp;/&nbsp;<code>$children</code> /&nbsp;<code>$root</code>：访问父 / 子实例 / 根实例</strong></p>
<p><strong>（4）<code>EventBus （$emit / $on）</code>&nbsp;适用于 父子、隔代、兄弟组件通信</strong></p>
<p>这种方法通过一个空的 <code>Vue</code> 实例作为中央事件总线（事件中心），用它来触发事件和监听事件，从而实现任何组件间的通信，包括父子、隔代、兄弟组件。</p>
<p><strong>（5）<code>$attrs</code>/<code>$listeners</code>&nbsp;适用于 隔代组件通信</strong></p>
<ul>
<li><code>$attrs</code>：包含了父作用域中不被 <code>prop</code> 所识别 (且获取) 的特性绑定 ( <code>class</code> 和 <code>style</code> 除外 )。当一个组件没有声明任何 <code>prop</code> 时，这里会包含所有父作用域的绑定 ( <code>class</code> 和 <code>style</code> 除外 )，并且可以通过&nbsp;<code>v-bind="$attrs"</code>&nbsp;传入内部组件。通常配合 <code>inheritAttrs</code> 选项一起使用。</li>
<li><code>$listeners</code>：包含了父作用域中的 (不含 <code>.native</code> 修饰器的) <code>v-on</code> 事件监听器。它可以通过&nbsp;<code>v-on="$listeners"</code>&nbsp;传入内部组件</li>
</ul>
<p><strong>（6）<code>provide / inject</code>&nbsp;适用于 隔代组件通信</strong></p>
<p>祖先组件中通过 <code>provide</code> 来提供变量，然后在子孙组件中通过 <code>inject</code> 来注入变量。<code>provide / inject API</code> 主要解决了跨级组件间的通信问题，不过它的使用场景，主要是子组件获取上级组件的状态，跨级组件间建立了一种主动提供与依赖注入的关系。</p>
<p><strong>（7）<code>Vuex</code> 适用于 父子、隔代、兄弟组件通信</strong></p>
<p><code>Vuex</code> 是一个专为 <code>Vue.js</code> 应用程序开发的状态管理模式。每一个 <code>Vuex</code> 应用的核心就是 <code>store</code>（仓库）。<code>store</code> 基本上就是一个容器，它包含着你的应用中大部分的状态 ( <code>state</code> )。</p>
<ul>
<li><code>Vuex</code> 的状态存储是响应式的。当 <code>Vue</code> 组件从 <code>store</code> 中读取状态的时候，若 <code>store</code> 中的状态发生变化，那么相应的组件也会相应地得到高效更新。</li>
<li>改变 <code>store</code> 中的状态的唯一途径就是显式地提交 <code>(commit) mutation</code>。这样使得我们可以方便地跟踪每一个状态的变化。</li>
</ul>
<p><strong>（8）插槽</strong></p>
<p><code>Vue3</code> 可以通过 <code>usesolt</code> 获取插槽数据。</p>
<p><strong>（9）<code>mitt.js</code> 适用于任意组件通信</strong></p>
<p><code>Vue3</code> 中移除了 <code>$on</code>，<code>$off</code>等方法，所以 <code>EventBus</code> 不再使用，相应的替换方案就是 <code>mitt.js</code></p>
</details>

## Vue3和vue2 全局组件和局部组件注册的方式？

<details> 
<ul>
<li><strong>Vue2</strong>：<code>Vue.component()</code></li>
<li><strong>Vue3</strong>：<code>app.component()</code></li>
</ul>
</details>

## 什么是动态组件？动态组件的钩子如何执行？

<details> 
<p>让多个组件使用同一个挂载点，并动态切换，这就是动态组件</p>
<p>简单的说，动态组件就是将几个组件放在一个挂载点下，这个挂载点就是标签，其需要绑定 <code>is</code> 属性，属性值为父组件中的变量，变量对应的值为要挂载的组件的组件名，然后根据父组件里某个变量来动态显示哪个，也可以都不显示。</p>
<p>缓存 <code>&lt;keep-alive&gt;</code></p>
<ul>
<li>包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。</li>
<li>可以将动态组件放到组件内对动态组件进行缓存，这样动态组件进行切换的时候，就不会每次都重新创建了。</li>
</ul>
</details>

## Keep-alive的作用？使用keep-alive的组件如何监控组件切换？

<details> 
<p><code>keep-alive</code> 是 <code>Vue</code> 内置的一个组件，可以使被包含的组件保留状态，避免重新渲染 ，其有以下特性：</p>
<ul>
<li>一般结合路由和动态组件一起使用，用于缓存组件；</li>
<li>提供 <code>include</code> 和 <code>exclude</code> 属性，两者都支持字符串或正则表达式， <code>include</code> 表示只有名称匹配的组件会被缓存，<code>exclude</code> 表示任何名称匹配的组件都不会被缓存 ，其中 <code>exclude</code> 的优先级比 <code>include</code> 高；</li>
<li>对应两个钩子函数 <code>activated</code> 和 <code>deactivated</code> ，当组件被激活时，触发钩子函数 <code>activated</code>，当组件被移除时，触发钩子函数 <code>deactivated</code>。</li>
</ul>
</details>

## 父组件如何监听子组件的生命周期？

<details> 
<p>比如有父组件 <code>Parent</code> 和子组件 <code>Child</code>，如果父组件监听到子组件挂载 <code>mounted</code> 就做一些逻辑处理，可以通过以下写法实现：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//&nbsp;Parent.vue</span>
&lt;<span class="hljs-title class_">Child</span>&nbsp;@mounted=<span class="hljs-string">"doSomething"</span>/&gt;
&nbsp;&nbsp;&nbsp;&nbsp;
<span class="hljs-comment">//&nbsp;Child.vue</span>
<span class="hljs-title function_">mounted</span>(<span class="hljs-params"></span>)&nbsp;{
&nbsp;&nbsp;<span class="hljs-variable language_">this</span>.$emit(<span class="hljs-string">"mounted"</span>);
}
<span class="copy-code-btn">复制代码</span></code></pre>
<p>以上需要手动通过 <code>$emit</code> 触发父组件的事件，更简单的方式可以在父组件引用子组件时通过 <code>@hook</code> 来监听即可，如下所示：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//&nbsp;&nbsp;Parent.vue</span>
&lt;<span class="hljs-title class_">Child</span>&nbsp;@<span class="hljs-attr">hook</span>:mounted=<span class="hljs-string">"doSomething"</span>&nbsp;&gt;&lt;/<span class="hljs-title class_">Child</span>&gt;

<span class="hljs-title function_">doSomething</span>(<span class="hljs-params"></span>)&nbsp;{
&nbsp;&nbsp;&nbsp;<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(<span class="hljs-string">'父组件监听到&nbsp;mounted&nbsp;钩子函数&nbsp;...'</span>);
},
&nbsp;&nbsp;&nbsp;&nbsp;
<span class="hljs-comment">//&nbsp;&nbsp;Child.vue</span>
<span class="hljs-title function_">mounted</span>(<span class="hljs-params"></span>){
&nbsp;&nbsp;&nbsp;<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(<span class="hljs-string">'子组件触发&nbsp;mounted&nbsp;钩子函数&nbsp;...'</span>);
},&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;
<span class="hljs-comment">//&nbsp;以上输出顺序为：</span>
<span class="hljs-comment">//&nbsp;子组件触发&nbsp;mounted&nbsp;钩子函数&nbsp;...</span>
<span class="hljs-comment">//&nbsp;父组件监听到&nbsp;mounted&nbsp;钩子函数&nbsp;...&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>当然 <code>@hook</code> 方法不仅仅是可以监听 <code>mounted</code>，其它的生命周期事件，例如：<code>created</code>，<code>updated</code> 等都可以监听。</p>
</details>

# 原理相关

## Vue初始化时都做了什么？

<details> 
<p><a href="https://juejin.cn/post/6984589942840098829" target="_blank" title="https://juejin.cn/post/6984589942840098829">【源码学习】Vue 初始化过程 (附思维导图)</a></p>
<h3 data-id="heading-49">第一部分</h3>
<p>⭐ 每个 <code>vue</code> 实例都有一个 <code>_uid</code>，并且是依次递增的，确保唯一性。</p>
<p>⭐ <code>vue</code> 实例不应该是一个响应式的，做个标记。</p>
<h3 data-id="heading-50">第二部分</h3>
<p>⭐ 如果是子组件,将组件配置对象上的一些深层次属性放到<code> vm.$options</code> 选项中，以提高代码的执行效率。</p>
<p>⭐ 如果是根组件，对 <code>options</code> 进行合并，<code>vue</code> 会将相关的属性和方法都统一放到 <code>vm.$options</code> 中。<code>vm.$options</code> 的属性来自两个方面，一个是 <code>Vue</code> 的构造函数 <code>vm.constructor</code> 预先定义的，一个是 <code>new Vue</code> 时传入的入参对象。</p>
<h3 data-id="heading-51">第三部分</h3>
<p>⭐ <strong>initProxy / vm._renderProxy</strong> 在非生产环境下执行了 <code>initProxy</code> 函数,参数是实例;在生产环境下设置了实例的 <code>_renderProxy</code> 属性为实例自身。</p>
<p>⭐ 设置了实例的 <code>_self</code> 属性为实例自身。</p>
<p>⭐ <strong>initLifecycle</strong> 初始化组件实例关系属性 , 比如 <code>$parent</code>、<code>$children</code>、<code>$root</code>、<code>$refs</code> 等 （不是组件生命周期 <code>mounted</code> , <code>created</code>...）</p>
<p>⭐ <strong>initEvents</strong> 初始化自定义事件。</p>
<p>⭐ <strong>initRender</strong> 初始化插槽 , 获取 <code>this.slots</code> , 定义 <code>this._c</code> , 也就是 <code>createElement</code> 方法 , 平时使用的 <code>h</code> 函数。</p>
<p>⭐ <strong>callHook</strong> 执行 <code>beforeCreate</code> 生命周期函数。</p>
<p>⭐ <strong>initInjections</strong> 初始化 <code>inject</code> 选项</p>
<p>⭐ <strong>initState</strong> 响应式原理的核心 , 处理 <code>props</code>、<code>methods</code>、<code>computed</code>、<code>data</code>、<code>watch</code> 等。</p>
<p>⭐ <strong>initProvide</strong> 解析组件配置项上的 <code>provide</code> 对象，将其挂载到 <code>vm._provided</code> 属性上。</p>
<p>⭐ <strong>callHook</strong> 执行 <code>created</code> 生命周期函数。</p>
<h3 data-id="heading-52">第四部分</h3>
<p>⭐ 如果有 <code>el</code> 属性，则调用 <code>vm.$mount</code> 方法挂载 <code>vm</code> ，挂载的目标就是把模板渲染成最终的 <code>DOM</code>。</p>
<p>⭐ 不存在 <code>el</code> 的时候不挂载 , 需要手动挂载。</p>
</details>

## 数据响应式的原理

<details> 
<p><code>Vue.js</code> 是采用 <strong>数据劫持</strong> 结合 <strong>发布者-订阅者模式</strong> 的方式，通过 <code>Object.defineProperty()</code> 来劫持各个属性的 <code>setter</code>，<code>getter</code>，在数据变动时发布消息给订阅者，触发相应的监听回调。主要分为以下几个步骤：</p>
<ol>
<li>使用 <code>observe</code> 对需要响应式的数据进行递归，将对像的所有属性及其子属性，都加上 <code>setter</code> 和 <code>getter</code> 这样的话，给这个对象的某个属性赋值的时候，就会触发 <code>setter</code>，那么就能监听到了数据变化。</li>
<li><code>compile</code> 解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图。</li>
<li><code>Watcher</code> 订阅者是 <code>Observer</code> 和 <code>Compile</code> 之间通信的桥梁，主要做的事情是:</li>
</ol>
<ul>
<li>在自身实例化时往属性订阅器(<code>dep</code>)里面添加自己</li>
<li>自身必须有一个 <code>update()</code> 方法</li>
<li>待属性变动触发 <code>dep.notice()</code> 通知时，能调用自身的 <code>update()</code> 方法，并触发 <code>Compile</code> 中绑定的回调，完成视图更新。
总结：通过 <code>Observer</code> 来监听自己的 <code>model</code> 数据变化，通过 <code>Compile</code> 来解析编译模板指令，最终利用 <code>Watcher</code> 搭起 <code>Observer</code> 和 <code>Compile</code> 之间的通信桥梁，达到一个数据响应式的效果。</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/475e0835adb7431d8360486372aa70c8~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="" loading="lazy" class="medium-zoom-image"></p>
</details>

## 使用 Object.defineProperty() 来进行数据劫持有什么缺点？

<details> 
<p>无法劫持以下操作</p>
<ul>
<li>给对象新增属性</li>
<li>给对象删除属性</li>
<li>大部分的操作数组</li>
</ul>
</details>

## Vue 框架怎么实现对象和数组的监听？

<details> 
<p><code>Vue</code> 框架是通过 <strong>遍历数组</strong> 和 <strong>递归遍历对象</strong>，从而达到利用 <code>Object.defineProperty()</code> 对对象和数组的部分方法的操作进行监听。</p>
</details>

## Vue 中给 data 中的对象属性添加一个新的属性或删除一个属性时会发生什么？如何解决？

<details> 
<p>什么都不会发生，因为 <code>Object.defineProperty()</code> 监听不到这类变化。</p>
<p>可以使用 <code>vm.$set</code> 和 <code>Vue.set</code> 方法去添加一个属性。</p>
<p>可以使用 <code>vm.$delete</code> 和 <code>Vue.delete</code> 方法去删除一个属性。</p>
</details>

## 如何解决索引赋值或者修改数组长度无法改变视图？

<details> 
<p>由于 <code>Vue</code> 只改写了 7 种修改数组的方法，所以 <code>Vue</code> 不能检测到以下数组的变动：</p>
<ul>
<li>当你利用索引直接设置一个数组项时，例如：<code>vm.items[indexOfItem] = newValue</code></li>
<li>当你修改数组的长度时，例如：<code>vm.items.length = newLength</code></li>
</ul>
<p>为了解决第一个问题，<code>Vue</code> 提供了以下操作方法：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//&nbsp;Vue.set</span>
<span class="hljs-title class_">Vue</span>.<span class="hljs-title function_">set</span>(vm.<span class="hljs-property">items</span>,&nbsp;indexOfItem,&nbsp;newValue)
<span class="hljs-comment">//&nbsp;vm.$set，Vue.set的一个别名</span>
vm.$set(vm.<span class="hljs-property">items</span>,&nbsp;indexOfItem,&nbsp;newValue)
<span class="hljs-comment">//&nbsp;Array.prototype.splice</span>
vm.<span class="hljs-property">items</span>.<span class="hljs-title function_">splice</span>(indexOfItem,&nbsp;<span class="hljs-number">1</span>,&nbsp;newValue)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>为了解决第二个问题，<code>Vue</code> 提供了以下操作方法：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//&nbsp;Array.prototype.splice</span>
vm.<span class="hljs-property">items</span>.<span class="hljs-title function_">splice</span>(newLength)
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 数组的响应式是怎么实现的？

<details> 
<p>择对 <strong>7</strong> 种数组（<strong>push,shift,pop,splice,unshift,sort,reverse</strong>）方法进行重写</p>
<p>所以在 <code>Vue</code> 中修改数组的索引和长度是无法监控到的。需要通过以上 <strong>7</strong> 种变异方法修改数组才会触发数组对应的 <code>watcher</code> 进行更新</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//&nbsp;src/obserber/array.js\</span>
<span class="hljs-comment">//&nbsp;先保留数组原型\</span>
<span class="hljs-keyword">const</span>&nbsp;arrayProto&nbsp;=&nbsp;<span class="hljs-title class_">Array</span>.<span class="hljs-property"><span class="hljs-keyword">prototype</span></span>;\
<span class="hljs-comment">//&nbsp;然后将arrayMethods继承自数组原型\</span>
<span class="hljs-comment">//&nbsp;这里是面向切片编程思想（AOP）--不破坏封装的前提下，动态的扩展功能\</span>
<span class="hljs-keyword">export</span>&nbsp;<span class="hljs-keyword">const</span>&nbsp;arrayMethods&nbsp;=&nbsp;<span class="hljs-title class_">Object</span>.<span class="hljs-title function_">create</span>(arrayProto);\
<span class="hljs-keyword">let</span>&nbsp;methodsToPatch&nbsp;=&nbsp;[\
&nbsp;&nbsp;<span class="hljs-string">"push"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"pop"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"shift"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"unshift"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"splice"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"reverse"</span>,\
&nbsp;&nbsp;<span class="hljs-string">"sort"</span>,\
];\
methodsToPatch.<span class="hljs-title function_">forEach</span>(<span class="hljs-function">(<span class="hljs-params">method</span>)&nbsp;=&gt;</span>&nbsp;{\
&nbsp;&nbsp;arrayMethods[method]&nbsp;=&nbsp;<span class="hljs-keyword">function</span>&nbsp;(<span class="hljs-params">...args</span>)&nbsp;{\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;&nbsp;&nbsp;这里保留原型方法的执行结果\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">const</span>&nbsp;result&nbsp;=&nbsp;arrayProto[method].<span class="hljs-title function_">apply</span>(<span class="hljs-variable language_">this</span>,&nbsp;args);\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;这句话是关键\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;this代表的就是数据本身&nbsp;比如数据是{a:[1,2,3]}&nbsp;那么我们使用a.push(4)&nbsp;&nbsp;this就是a&nbsp;&nbsp;ob就是a.__ob__&nbsp;这个属性就是上段代码增加的&nbsp;代表的是该数据已经被响应式观察过了指向Observer实例\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">const</span>&nbsp;ob&nbsp;=&nbsp;<span class="hljs-variable language_">this</span>.<span class="hljs-property">__ob__</span>;\
\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;这里的标志就是代表数组有新增操作\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">let</span>&nbsp;inserted;\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">switch</span>&nbsp;(method)&nbsp;{\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">case</span>&nbsp;<span class="hljs-string">"push"</span>:\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">case</span>&nbsp;<span class="hljs-string">"unshift"</span>:\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inserted&nbsp;=&nbsp;args;\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">break</span>;\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">case</span>&nbsp;<span class="hljs-string">"splice"</span>:\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inserted&nbsp;=&nbsp;args.<span class="hljs-title function_">slice</span>(<span class="hljs-number">2</span>);\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-attr">default</span>:\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">break</span>;\
&nbsp;&nbsp;&nbsp;&nbsp;}\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;如果有新增的元素&nbsp;inserted是一个数组&nbsp;调用Observer实例的observeArray对数组每一项进行观测\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">if</span>&nbsp;(inserted)&nbsp;ob.<span class="hljs-title function_">observeArray</span>(inserted);\
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-comment">//&nbsp;之后咱们还可以在这里检测到数组改变了之后从而触发视图更新的操作--后续源码会揭晓\</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">return</span>&nbsp;result;\
&nbsp;&nbsp;};\
});
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## $nextTick的原理是什么？

<details> 
<p><code>nextTick</code> 中的回调是在下次 <code>DOM</code> 更新循环结束之后执行的延迟回调。在修改数据之后立即使用这个方法，获取更新后的 <code>DOM</code>。主要思路就是采用微任务优先的方式调用异步方法去执行 <code>nextTick</code> 包装的方法。</p>
<p>简单的理解是：当数据更新了，在 <code>dom</code> 中渲染后， 自动执行该函数。<code>Vue</code> 实现响应式并不是数据发生变化之后 <code>DOM</code> 立即变化，<code>Vue</code> 是异步执行 <code>DOM</code> 更新的。<code>created</code> 钩子函数进行的 <code>DOM</code> 操作一定要放在<code>Vue.nextTick()</code> 的回调函数中，原因是在函数执行的时候 <code>DOM</code> 其实并未进行任何渲染。常用的场景是在进行获取数据后，需要对新视图进行下一步操作或者其他操作时，发现获取不到 <code>dom</code>。因为赋值操作只完成了数据模型的改变并没有完成视图更新。</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;有一个 <code>timerFunc</code> 这个函数用来执行 <code>callbacks</code> 里存储的所有回调函数</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;先判断是否原生支持 <code>promise</code>，如果支持，则利用 <code>promise</code> 来触发执行回调函数；</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;否则，如果支持 <code>MutationObserver</code>，则实例化一个观察者对象，观察文本节点发生变化时，触发执行所有回调函数。
&nbsp;&nbsp;&nbsp;如果都不支持，则利用 <code>setTimeout</code> 设置延时为 <strong>0</strong>。</p>
</details>

## 列表循环时 key 有什么作用？

<details> 
<p><code>key</code> 是为 <code>Vue</code> 中 <code>vnode</code> 的唯一标记，通过这个 <code>key</code>，我们的 <code>diff</code> 操作可以更准确、更快速。<code>Vue</code> 的 <code>diff</code> 过程可以概括为：<code>oldCh</code> 和 <code>newCh</code> 各有两个头尾的变量 <code>oldStartIndex</code>、<code>oldEndIndex</code> 和 <code>newStartIndex</code>、<code>newEndIndex</code>，它们会新节点和旧节点会进行两两对比，即一共有 <strong>4</strong> 种比较方式：<code>newStartIndex</code> 和 <code>oldStartIndex</code> 、<code>newEndIndex</code> 和 <code>oldEndIndex</code> 、<code>newStartIndex</code> 和 <code>oldEndIndex</code> 、<code>newEndIndex</code> 和 <code>oldStartIndex</code>，如果以上 <strong>4</strong> 种比较都没匹配，如果设置了 <code>key</code>，就会用 <code>key</code> 再进行比较，在比较的过程中，遍历会往中间靠，一旦 <code>StartIdx &gt; EndIdx</code> 表明 <code>oldCh</code> 和 <code>newCh</code> 至少有一个已经遍历完了，就会结束比较。</p>
<p>所以 <code>Vue</code> 中 <code>key</code> 的作用是：<code>key</code> 是为 <code>Vue</code> 中 <code>vnode</code> 的唯一标记，通过这个 <code>key</code>，我们的 <code>diff</code> 操作可以更准确、更快速，因为带 <code>key</code> 就不是就地复用了，在 <code>sameNode</code> 函数&nbsp;<code>a.key === b.key</code>&nbsp;对比中可以避免就地复用的情况。利用 <code>key</code> 的唯一性生成 <code>map</code> 对象来获取对应节点，比遍历方式更快，源码如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">function</span>&nbsp;<span class="hljs-title function_">createKeyToOldIdx</span>&nbsp;(children,&nbsp;beginIdx,&nbsp;endIdx)&nbsp;{
&nbsp;&nbsp;<span class="hljs-keyword">let</span>&nbsp;i,&nbsp;key
&nbsp;&nbsp;<span class="hljs-keyword">const</span>&nbsp;map&nbsp;=&nbsp;{}
&nbsp;&nbsp;<span class="hljs-keyword">for</span>&nbsp;(i&nbsp;=&nbsp;beginIdx;&nbsp;i&nbsp;&lt;=&nbsp;endIdx;&nbsp;++i)&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;key&nbsp;=&nbsp;children[i].<span class="hljs-property">key</span>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="hljs-keyword">if</span>&nbsp;(<span class="hljs-title function_">isDef</span>(key))&nbsp;map[key]&nbsp;=&nbsp;i
&nbsp;&nbsp;}
&nbsp;&nbsp;<span class="hljs-keyword">return</span>&nbsp;map
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 为什么不建议用index作为key?

<details> 
<p>使用 <code>index</code> 作为 <code>key</code> 和没写基本上没区别，因为不管数组的顺序怎么颠倒，<code>index</code> 都是<code> 0, 1, 2...</code> 这样排列，导致 <code>Vue</code> 会复用错误的旧子节点，做很多额外的工作。</p>
</details>

## v-if、v-show、v-html 的原理

<details> 
<ul>
<li>
<p><strong>v-if</strong> 会调用 <code>addIfCondition</code> 方法，生成 <code>vnode</code> 的时候会忽略对应节点，<code>render</code> 的时候就不会渲染；</p>
</li>
<li>
<p><strong>v-show</strong> 会生成 <code>vnode</code>，<code>render</code> 的时候也会渲染成真实节点，只是在 <code>render</code> 过程中会在节点的属性中修改 <code>show</code> 属性值，也就是常说的 <code>display</code>；</p>
</li>
<li>
<p><strong>v-html</strong> 会先移除节点下的所有节点，设置 <code>innerHTML</code> 为 <code>v-html</code> 的值。</p>
</li>
</ul>
</details>

## Vue中封装的数组方法有哪些，其如何实现页面更新

<details> 
<p>数组就是使用 <code>object.defineProperty</code> 重新定义数组的每一项，那能引起数组变化的方法我们都是知道的，</p>
<ul>
<li><code> pop</code> 、</li>
<li><code> push</code> 、</li>
<li><code> shift</code> 、</li>
<li><code> unshift</code> 、</li>
<li><code> splice</code> 、</li>
<li><code> sort</code> 、</li>
<li><code> reverse</code>
这七种，只要这些方法执行改了数组内容，我就更新内容就好了，是不是很好理解。</li>
</ul>
<ol>
<li>是用来函数劫持的方式，重写了数组方法，具体呢就是更改了数组的原型，更改成自己的，用户调数组的一些方法的时候，走的就是自己的方法，然后通知视图去更新。</li>
<li>数组里每一项可能是对象，那么我就是会对数组的每一项进行观测，（且只有数组里的对象才能进行观测，观测过的也不会进行观测）</li>
</ol>
<p><strong>vue3</strong>：改用 <code>proxy</code> ，可直接监听对象数组的变化。</p>
</details>

## Vue模板渲染的原理是什么？

<details> 
<p><code>vue</code> 中的模板 <code>template</code> 无法被浏览器解析并渲染，因为这不属于浏览器的标准，不是正确的 <code>HTML</code> 语法，所有需要将 <code>template</code> 转化成一个 <code>JavaScript</code> 函数，这样浏览器就可以执行这一个函数并渲染出对应的 <code>HTML</code> 元素，就可以让视图跑起来了，这一个转化的过程，就成为模板编译。</p>
<p>模板编译又分三个阶段，解析 <code>parse</code>，优化 <code>optimize</code>，生成 <code>generate</code>，最终生成可执行函数 <code>render</code>。</p>
<ul>
<li><strong>parse阶段</strong>：使用大量的正则表达式对 <code>template</code> 字符串进行解析，将标签、指令、属性等转化为抽象语法树 <code>AST</code>。</li>
<li><strong>optimize阶段</strong>：遍历 <code>AST</code>，找到其中的一些静态节点并进行标记，方便在页面重渲染的时候进行 <code>diff</code> 比较时，直接跳过这一些静态节点，优化 <code>runtime</code> 的性能。</li>
<li><strong>generate阶段</strong>：将最终的 <code>AST</code> 转化为 <code>render</code> 函数字符串。</li>
</ul>
</details>

## 说一下什么是Virtual DOM

<details> 
<p><code>Virtual DOM</code> 是 <code>DOM</code> 节点在 <code>JavaScript</code> 中的一种抽象数据结构，之所以需要虚拟 <code>DOM</code>，是因为浏览器中操作 <code>DOM</code> 的代价比较昂贵，频繁操作 <code>DOM</code> 会产生性能问题。虚拟 <code>DOM</code> 的作用是在每一次响应式数据发生变化引起页面重渲染时，<code>Vue</code> 对比更新前后的虚拟 <code>DOM</code>，匹配找出尽可能少的需要更新的真实 <code>DOM</code>，从而达到提升性能的目的。</p>
</details>

## Vue data 中某一个属性的值发生改变后，视图会立即同步执行重新渲染吗？

<details> 
<ul>
<li><code>Vue</code> 是异步执行 <code>DOM</code> 更新。</li>
<li>只要观察到数据变化，<code>Vue</code> 将开启一个队列，并缓冲在同一事件循环中发生的所有数据改变。</li>
<li>如果同一个 <code>watcher</code> 被多次触发，只会被推入到队列中一次。这种在缓冲时去除重复数据对于避免不必要的计算和 <code>DOM</code> 操作上非常重要。</li>
<li>然后，在下一个的事件循环&nbsp;<code>tick</code>&nbsp;中，<code>Vue</code> 刷新队列并执行实际 (已去重的) 工作。<code>Vue</code> 在内部尝试对异步队列使用原生的 <code>Promise.then</code> 和 <code>MessageChannel</code>，如果执行环境不支持，会采用 <code>setTimeout(fn, 0)</code> 代替。</li>
</ul>
<p>例如，当你设置 <code>vm.someData = 'new value'</code> ，该组件不会立即重新渲染。</p>
<ul>
<li>当刷新队列时，组件会在事件循环队列清空时的下一个&nbsp;<code>tick</code>&nbsp;更新。</li>
<li>多数情况我们不需要关心这个过程，但是如果你想在 <code>DOM</code> 状态更新后做点什么，这就可能会有些棘手。</li>
<li>虽然 <code>Vue.js</code> 通常鼓励开发人员沿着 “数据驱动” 的方式思考，避免直接接触 <code>DOM</code>，但是有时我们确实要这么做。为了在数据变化之后等待 <code>Vue</code> 完成更新 <code>DOM</code> ，可以在数据变化之后立即使用 <code>Vue.nextTick(callback) </code>。这样回调函数在 <code>DOM</code> 更新完成后就会调用。</li>
</ul>
</details>

## Vue.mixin 的使用场景和原理

<details> 
<p>在日常的开发中，我们经常会遇到在不同的组件中经常会需要用到一些相同或者相似的代码，这些代码的功能相对独立，可以通过 <code>Vue</code> 的 <code>mixin</code> 功能抽离公共的业务逻辑，原理类似“对象的继承”，当组件初始化时会调用 <code>mergeOptions</code> 方法进行合并，采用策略模式针对不同的属性进行合并。当组件和混入对象含有同名选项时，这些选项将以恰当的方式进行“合并”。</p>
</details>

## Vue.extend 作用和原理

<details> 
<p>其实就是一个子类构造器 ，是 <code>Vue</code> 组件的核心 <code>api</code> 实现思路就是使用原型继承的方法返回了 <code>Vue</code> 的子类 并且利用 <code>mergeOptions</code> 把传入组件的 <code>options</code> 和父类的 <code>options</code> 进行了合并。</p>
</details>

## Vue 事件绑定原理

<details> 
<p>原生事件绑定是通过 <code>addEventListener</code> 绑定给真实元素的，组件事件绑定是通过 <code>Vue</code> 自定义的 <code>$on</code> 实现的。如果要在组件上使用原生事件，需要加 <code>.native</code> 修饰符，这样就相当于在父组件中把子组件当做普通 <code>html</code> 标签，然后加上原生事件。</p>
<p><code>on、emit</code> 是基于发布订阅模式的，维护一个事件中心，<code>on</code> 的时候将事件按名称存在事件中心里，称之为订阅者，然后 <code>emit</code> 将对应的事件进行发布，去执行事件中心里的对应的监听器。</p>
</details>

## 虚拟 DOM 实现原理？

<details> 
<p>虚拟 <code>DOM</code> 的实现原理主要包括以下 <strong>3</strong> 部分：</p>
<ul>
<li>用 <code>JavaScript</code> 对象模拟真实 <code>DOM</code> 树，对真实 <code>DOM</code> 进行抽象；</li>
<li><code>diff</code> 算法 — 比较两棵虚拟 <code>DOM</code> 树的差异；</li>
<li><code>pach</code> 算法 — 将两个虚拟 <code>DOM</code> 对象的差异应用到真正的 <code>DOM</code> 树。</li>
</ul>
</details>

## 虚拟 dom 和真实 dom 的区别

<details> 
<ul>
<li>虚拟 <code>DOM</code> 不会进行排版与重绘操作&nbsp;</li>
<li>虚拟 <code>DOM</code> 就是把真实 <code>DOM</code> 转换为 <code>Javascript</code> 代码</li>
<li>虚拟 <code>DOM</code> 进行频繁修改，然后一次性比较并修改真实 <code>DOM</code> 中需要改的部分，最后并在真实 <code>DOM</code> 中进行排版与重绘，减少过多 <code>DOM</code> 节点排版与重绘损耗</li>
</ul>
</details>

# 生态相关

## vue-router 路由模式有几种？

<details> 
<p><code>vue-router</code> 有 3 种路由模式：<code>hash</code>、<code>history</code>、<code>abstract</code>：</p>
<ul>
<li><strong>hash</strong>: 使用 <code>URL hash</code> 值来作路由。支持所有浏览器，包括不支持 <code>HTML5 History Api</code> 的浏览器；</li>
<li><strong>history</strong> : 依赖 <code>HTML5 History API</code> 和服务器配置。</li>
<li><strong>abstract</strong> : 支持所有 <code>JavaScript</code> 运行环境，如 <code>Node.js</code> 服务器端。如果发现没有浏览器的 <code>API</code>，路由会自动强制进入这个模式.</li>
</ul>
</details>

## 路由的hash和history模式的区别

<details> 
<p><strong>（1）hash 模式的实现原理</strong></p>
<p>早期的前端路由的实现就是基于 <code>location.hash</code> 来实现的。其实现原理很简单，<code>location.hash</code> 的值就是 <code>URL</code> 中 <code>#</code> 后面的内容。比如下面这个网站，它的 <code>location.hash</code> 的值为 <code>#search</code>：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-attr">https</span>:<span class="hljs-comment">//www.word.com#search</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>hash</code> 路由模式的实现主要是基于下面几个特性：</p>
<ul>
<li><code>URL</code> 中 <code>hash</code> 值只是客户端的一种状态，也就是说当向服务器端发出请求时，<code>hash</code> 部分不会被发送；</li>
<li><code>hash</code> 值的改变，都会在浏览器的访问历史中增加一个记录。因此我们能通过浏览器的回退、前进按钮控制 <code>hash</code> 的切换；</li>
<li>可以通过 <code>a</code> 标签，并设置 <code>href</code> 属性，当用户点击这个标签后，<code>URL</code> 的 <code>hash</code> 值会发生改变；或者使用 <code>JavaScript</code> 来对 <code>loaction.hash</code> 进行赋值，改变 <code>URL</code> 的 <code>hash</code> 值；</li>
<li>我们可以使用 <code>hashchange</code> 事件来监听 <code>hash</code> 值的变化，从而对页面进行跳转（渲染）。</li>
</ul>
<p><strong>（2）history 模式的实现原理</strong></p>
<p><code>HTML5</code> 提供了 <code>History API</code> 来实现 <code>URL</code> 的变化。其中做最主要的 <code>API</code> 有以下两个：<code>history.pushState()</code> 和 <code>history.repalceState()</code>。这两个 <code>API</code> 可以在不进行刷新的情况下，操作浏览器的历史纪录。唯一不同的是，前者是新增一个历史记录，后者是直接替换当前的历史记录，如下所示：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-variable language_">window</span>.<span class="hljs-property">history</span>.<span class="hljs-title function_">pushState</span>(<span class="hljs-literal">null</span>,&nbsp;<span class="hljs-literal">null</span>,&nbsp;path);
<span class="hljs-variable language_">window</span>.<span class="hljs-property">history</span>.<span class="hljs-title function_">replaceState</span>(<span class="hljs-literal">null</span>,&nbsp;<span class="hljs-literal">null</span>,&nbsp;path);
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>history</code> 路由模式的实现主要基于存在下面几个特性：</p>
<ul>
<li><code>pushState</code> 和 <code>repalceState</code> 两个 <code>API</code> 来操作实现 <code>URL</code> 的变化 ；</li>
<li>我们可以使用 <code>popstate</code> 事件来监听 <code>url</code> 的变化，从而对页面进行跳转（渲染）；</li>
<li><code>history.pushState()</code> 或 <code>history.replaceState()</code> 不会触发 <code>popstate</code> 事件，这时我们需要手动触发页面跳转（渲染）。</li>
</ul>
</details>

## 如何获取页面的hash变化

<details> 
<p>监听 <code>$route</code> 对象</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 监听,当路由发生变化的时候执行</span>
<span class="hljs-attr">watch</span>: {
 <span class="hljs-attr">$route</span>: {
 <span class="hljs-attr">handler</span>: <span class="hljs-keyword">function</span>(<span class="hljs-params">val, oldVal</span>){
  <span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(val);
 },
  <span class="hljs-comment">// 深度观察监听</span>
 <span class="hljs-attr">deep</span>: <span class="hljs-literal">true</span>
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## route 和 router 的区别

<details> 
<p><code>$router</code>&nbsp;是 <code>VueRouter</code> 的实例，在 <code>script</code> 标签中想要导航到不同的 <code>URL</code>,使用&nbsp;<code>$router.push</code>&nbsp;方法。返回上一个历史 <code>history</code> 用&nbsp;<code>$router.to(-1)</code></p>
<p><code>$route</code>&nbsp;为当前 <code>router</code> 跳转对象。里面可以获取当前路由的 <code>name</code>,<code>path</code>,<code>query</code>,<code>parmas</code> 等。</p>
</details>

## 如何定义动态路由？如何获取传过来的动态参数？

<details> 
<p>可以通过<code>query</code>，<code>param</code>两种方式</p>
<p>区别：<code>query</code>通过<code>url</code>传参，刷新页面还在；<code>params</code>属性页面不在</p>
<p><code>params</code>的类型：</p>
<ul>
<li>配置路由格式: <code>/router/:id</code></li>
<li>传递的方式：在 <code>path</code> 后面跟上对应的值</li>
<li>传递后形成的路径：<code>/router/123</code></li>
<li>通过 <code>$route.params.id</code> 获取传递的值</li>
</ul>
<p><code>query</code> 的类类型</p>
<ul>
<li>配置路由格式 <code>:/router</code> 也就是普通配置</li>
<li>传递的方式:对象中使用 <code>query</code> 的 <code>key</code> 作为传递方式</li>
<li>传递后形成的路径 <code>:/route?id=123</code></li>
<li>通过 <code>$route.query</code> 获取传递的值</li>
</ul>
</details>

## Vue-router 导航守卫有哪些

<details> 
<p><a href="https://juejin.cn/post/6987267852575195143" target="_blank" title="https://juejin.cn/post/6987267852575195143">【面试题解】vue-router有几种钩子函数？具体是什么及执行流程是怎样的？</a></p>
</details>

## Vue-router跳转和location.href有什么区别

<details> 
<p>使用&nbsp;<code>location.href= /url&nbsp;</code>来跳转，简单方便，但是刷新了页面；</p>
<p>使用&nbsp;<code>history.pushState( /url )</code>&nbsp;，无刷新页面，静态跳转；</p>
<p>引进 <code>router</code> ，然后使用&nbsp;<code>router.push( /url )</code>&nbsp;来跳转，使用了&nbsp;<code>diff</code>&nbsp;算法，实现了按需加载，减少了 <code>dom</code> 的消耗。</p>
<p>其实使用 <code>router</code> 跳转和使用&nbsp;<code>history.pushState()</code>&nbsp;没什么差别的，因为 <code>vue-router</code> 就是用了&nbsp;<code>history.pushState()</code>&nbsp;，尤其是在 <code>history</code> 模式下。</p>
</details>

## params和query的区别

<details> 
<p><strong>用法</strong>：<code>query</code> 要用 <code>path</code> 来引入，<code>params</code> 要用 <code>name</code> 来引入，接收参数都是类似的，分别是&nbsp;<code>this.$route.query.name</code>&nbsp;和&nbsp;<code>this.$route.params.name</code>&nbsp;。</p>
<p><strong>url 地址显示</strong>：<code>query</code> 更加类似于我们 <code>ajax</code> 中 <code>get</code> 传参，<code>params</code> 则类似于 <code>post</code>，说的再简单一点，前者在浏览器地址栏中显示参数，后者则不显示。</p>
<p><strong>注意点</strong>：<code>query</code> 刷新不会丢失 <code>query</code> 里面的数据， <code>params</code> 刷新会丢失 <code>params</code> 里面的数据。</p>
</details>

## Vuex 的原理

<details> 
<ul>
<li>
<p><code>Vue</code> 组件会触发 <code>（dispatch）</code>一些事件或动作，也就是 <code>Actions</code>;</p>
</li>
<li>
<p>在组件中发出的动作，肯定是想获取或者改变数据的，但是在 <code>vuex</code> 中，数据是集中管理的，不能直接去更改数据，所以会把这个动作提交<code>（Commit）</code>到 <code>Mutations</code> 中;</p>
</li>
<li>
<p>然后 <code>Mutations</code> 就去改变 <code>State</code> 中的数据;</p>
</li>
<li>
<p>当 <code>State</code> 中的数据被改变之后，就会重新渲染<code>（Render）</code>到 <code>Vue Components</code> 中去，组件展示更新后的数据，完成一个流程。</p>
</li>
</ul>
</details>

## Vuex有哪几种属性

<details> 
<p>有五种，分别</p>
<ul>
<li><strong>State</strong>：定义了应用状态的数据结构，可以在这里设置默认的初始状态。</li>
<li><strong>Getter</strong>：允许组件从 <code>Store</code> 中获取数据，<code>mapGetters</code> 辅助函数仅仅是将 <code>store</code> 中的 <code>getter</code> 映射到局部计算属性。</li>
<li><strong>Mutation</strong>：是唯一更改 <code>store</code> 中状态的方法，且必须是同步函数。</li>
<li><strong>Action</strong>：用于提交 <code>mutation</code>，而不是直接变更状态，可以包含任意异步操作。</li>
<li><strong>Module</strong>：允许将单一的 <code>Store</code> 拆分为多个 <code>store</code> 且同时保存在单一的状态树中。</li>
</ul>
</details>

## Vuex和单纯的全局对象有什么区别？

<details> 
<ul>
<li>
<p><code>Vuex</code> 的状态存储是响应式的。当 <code>Vue</code> 组件从 <code>store</code> 中读取状态的时候，若 <code>store</code> 中的状态发生变化，那么相应的组件也会相应地得到高效更新。</p>
</li>
<li>
<p>不能直接改变 <code>store</code> 中的状态。改变 <code>store</code> 中的状态的唯一途径就是显式地提交  <code>mutation</code>。</p>
</li>
</ul>
</details>

## Vuex中action和mutation的区别

<details> 
<ul>
<li>
<p><code>Mutation</code> 专注于修改 <code>State</code>，理论上是修改 <code>State</code> 的唯一途径；<code>Action</code> 业务代码、异步请求。</p>
</li>
<li>
<p><code>Mutation</code>：必须同步执行；<code>Action</code>：可以异步，但不能直接操作 <code>State</code>。</p>
</li>
<li>
<p>在视图更新时，先触发 <code>actions</code>，<code>actions</code> 再触发 <code>mutation</code></p>
</li>
<li>
<p><code>mutation</code> 的参数是 <code>state</code>，它包含 <code>store</code> 中的数据；<code>action</code> 的参数是 <code>context</code>，它是 <code>state</code> 的父级，包含 <code>state</code>、<code>getters</code>等。</p>
</li>
</ul>
</details>

## 为什么 Vuex 的 mutation 中不能做异步操作？

<details> 
<ul>
<li>
<p><code>Vuex</code> 中所有的状态更新的唯一途径都是 <code>mutation</code>，异步操作通过 <code>Action</code> 来提交 <code>mutation</code> 实现，这样可以方便地跟踪每一个状态的变化，从而能够实现一些工具帮助更好地了解我们的应用。</p>
</li>
<li>
<p>每个 <code>mutation</code> 执行完成后都会对应到一个新的状态变更，这样 <code>devtools</code> 就可以打个快照存下来。如果 <code>mutation</code> 支持异步操作，就没有办法知道状态是何时更新的，无法很好的进行状态的追踪，给调试带来困难。</p>
</li>
</ul>
</details>

## Vuex 和 localStorage 的区别

<details> 
<p><strong>（1）最重要的区别</strong></p>
<ul>
<li><code>vuex</code> 存储在内存中</li>
<li><code>localstorage</code> 则以文件的方式存储在本地，只能存储字符串类型的数据，存储对象需要 <code>JSON</code> 的 <code>stringify</code> 和 <code>parse</code> 方法进行处理。 读取内存比读取硬盘速度要快</li>
</ul>
<p><strong>（2）应用场景</strong></p>
<ul>
<li><code>Vuex</code> 是一个专为 <code>Vue.js</code> 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。<code>vuex</code> 用于组件之间的传值。</li>
<li><code>localstorage</code> 是本地存储，是将数据存储到浏览器的方法，一般是在跨页面传递数据时使用 。</li>
<li><code>Vuex</code> 能做到数据的响应式，<code>localstorage</code> 不能</li>
</ul>
<p><strong>（3）永久性</strong></p>
<p>刷新页面时 <code>vuex</code> 存储的值会丢失，<code>localstorage</code> 不会，对于不变的数据可以用 <code>localstorage</code> 可以代替 <code>vuex</code>。</p>
</details>

## Vuex的严格模式是什么,有什么作用，如何开启？

<details> 
<p>在严格模式下，无论何时发生了状态变更且不是由 <code>mutation</code> 函数引起的，将会抛出错误。这能保证所有的状态变更都能被调试工具跟踪到。</p>
<p>在 <code>Vuex.Store</code> 构造器选项中开启,如下</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> store = <span class="hljs-keyword">new</span> <span class="hljs-title class_">Vuex</span>.<span class="hljs-title class_">Store</span>({
    <span class="hljs-attr">strict</span>:<span class="hljs-literal">true</span>,
})
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 如何在组件中批量使用Vuex的getter属性

<details> 
<p>使用 <code>mapGetters</code> 辅助函数, 利用对象展开运算符将 <code>getter</code> 混入 <code>computed</code> 对象中</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> {mapGetters} <span class="hljs-keyword">from</span> <span class="hljs-string">'vuex'</span>
<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span>{
    <span class="hljs-attr">computed</span>:{
        ...<span class="hljs-title function_">mapGetters</span>([<span class="hljs-string">'total'</span>,<span class="hljs-string">'discountTotal'</span>])
    }
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## 如何在组件中重复使用Vuex的mutation

<details> 
<p>使用 <code>mapMutations</code> 辅助函数,在组件中这么使用</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> { mapMutations } <span class="hljs-keyword">from</span> <span class="hljs-string">'vuex'</span>
<span class="hljs-attr">methods</span>:{
    ...<span class="hljs-title function_">mapMutations</span>({
        <span class="hljs-attr">setNumber</span>:<span class="hljs-string">'SET_NUMBER'</span>,
    })
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

## Vuex 页面刷新数据丢失怎么解决

<details> 
<ol>
<li>
<p>在 <code>created</code> 周期中读取 <code>sessionstorage</code> 中的数据存储在 <code>store</code> 中，此时用 <code>vuex.store</code> 的 <code>replaceState</code> 方法，替换 <code>store</code> 的根状态</p>
</li>
<li>
<p>在 <code>beforeunload</code> 方法中将 <code>store.state</code> 存储到 <code>sessionstorage</code> 中。</p>
</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> {
  <span class="hljs-attr">name</span>: <span class="hljs-string">'App'</span>,
  <span class="hljs-title function_">created</span>(<span class="hljs-params"></span>) {
    <span class="hljs-comment">//在页面加载时读取sessionStorage里的状态信息</span>
    <span class="hljs-keyword">if</span> (sessionStorage.<span class="hljs-title function_">getItem</span>(<span class="hljs-string">"store"</span>)) {
      <span class="hljs-variable language_">this</span>.<span class="hljs-property">$store</span>.<span class="hljs-title function_">replaceState</span>(<span class="hljs-title class_">Object</span>.<span class="hljs-title function_">assign</span>({},
        <span class="hljs-variable language_">this</span>.<span class="hljs-property">$store</span>.<span class="hljs-property">state</span>, <span class="hljs-title class_">JSON</span>.<span class="hljs-title function_">parse</span>(sessionStorage.<span class="hljs-title function_">getItem</span>(<span class="hljs-string">"store"</span>))))
    }
    <span class="hljs-comment">//在页面刷新时将vuex里的信息保存到sessionStorage里</span>
    <span class="hljs-variable language_">window</span>.<span class="hljs-title function_">addEventListener</span>(<span class="hljs-string">"beforeunload"</span>, <span class="hljs-function">() =&gt;</span> {
      sessionStorage.<span class="hljs-title function_">setItem</span>(<span class="hljs-string">"store"</span>, <span class="hljs-title class_">JSON</span>.<span class="hljs-title function_">stringify</span>(<span class="hljs-variable language_">this</span>.<span class="hljs-property">$store</span>.<span class="hljs-property">state</span>))
    })
  }
}
<span class="copy-code-btn">复制代码</span></code></pre>
</details>

# 3.0相关

## Vue3.0 有什么更新

<details> 
<p><code>Vue3</code> 的大多都在这里了。
<a href="https://juejin.cn/post/6977004323742220319#heading-9" target="_blank" title="https://juejin.cn/post/6977004323742220319#heading-9">【初学者笔记】整理的一些Vue3知识点</a></p>
</details>

## Vue3.0 defineProperty和proxy的区别

<details> 
<p><code>Vue3.x</code> 改用 <code>Proxy</code> 替代 <code>Object.defineProperty</code>。因为 <code>Proxy</code> 可以直接监听对象和数组的变化，并且有多达 <strong>13</strong> 种拦截方法。</p>
</details>

## Proxy 与 Object.defineProperty 优劣对比

<details> 
<p><strong>Proxy 的优势如下:</strong></p>
<ul>
<li><code>Proxy</code> 可以直接监听对象而非属性；</li>
<li><code>Proxy</code> 可以直接监听数组的变化；</li>
<li><code>Proxy</code> 返回的是一个新对象,我们可以只操作新的对象达到目的,而 <code>Object.defineProperty</code> 只能遍历对象属性直接修改；</li>
<li><code>Proxy</code> 作为新标准将受到浏览器厂商重点持续的性能优化，也就是传说中的新标准的性能红利；</li>
</ul>
<p><strong>Object.defineProperty 的优势如下:</strong></p>
<ul>
<li>兼容性好，支持 <code>IE9</code>。</li>
</ul>
</details>

## Vue 3.0 生命周期有哪些变化？

<details> 
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a8f719bf10544f109cd10e5ba6adbcda~tplv-k3u1fbpfcp-zoom-in-crop-mark:4536:0:0:0.awebp" alt="微信截图_20210623104108.png" loading="lazy" class="medium-zoom-image"></p>
<p><strong>注意</strong>:<code>3.0</code>中的生命周期钩子要比<code>2.X</code>中相同生命周期的钩子要快</p>
<p><code>Composition API</code>还新增了以下调试钩子函数：但是不怎么常用</p>
<ul>
<li>onRenderTracked</li>
<li>onRenderTriggered</li>
</ul>
</details>

## Vue 3.0 自定义指令有哪些变化？

<details> 
<p>先看看<code>Vue2</code>自定义指令的钩子</p>
<ul>
<li><strong>bind</strong>：当指令绑定在对应元素时触发。只会触发一次。</li>
<li><strong>inserted</strong>：当对应元素被插入到 <code>DOM</code> 的父元素时触发。</li>
<li><strong>update</strong>：当元素更新时，这个钩子会被触发（此时元素的后代元素还没有触发更新）。</li>
<li><strong>componentUpdated</strong>：当整个组件（包括子组件）完成更新后，这个钩子触发。</li>
<li><strong>unbind</strong>：当指令被从元素上移除时，这个钩子会被触发。也只触发一次。</li>
</ul>
<p>在<code> Vue3</code> 中，官方为了更有助于代码的可读性和风格统一，把自定义指令的钩子名称改的更像是组件生命周期，尽管他们是两回事</p>
<ul>
<li><strong>bind</strong> =&gt; <strong>beforeMount</strong></li>
<li><strong>inserted</strong> =&gt; <strong>mounted</strong></li>
<li><strong>beforeUpdate</strong>: <strong>新的钩子，会在元素自身更新前触发</strong></li>
<li><strong>update</strong> =&gt; <strong>移除</strong>！</li>
<li><strong>componentUpdated</strong> =&gt; <strong>updated</strong></li>
<li><strong>beforeUnmount</strong>: <strong>新的钩子，当元素自身被卸载前触发</strong></li>
<li><strong>unbind</strong> =&gt; <strong>unmounted</strong></li>
</ul>
</details>

# 后语

最后祝大家在新的一年里，都能找到满意的工作，升职加薪，赚的盆满钵满！



作者：一尾流莺
链接：https://juejin.cn/post/7064368176846340132
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
