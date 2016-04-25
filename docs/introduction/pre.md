# 预备知识

作为JavaScript技术栈的最佳实践，主要给出的是相关技术搭建的规范规则，原则上不会过多的介绍各种基础知识本身。
也就是说，在阅读这份文档，以及使用这份文档指导工作的时候，我们假设你是具备比较扎实的相关基础的。

下面各个小节列举了整个技术栈涉及到的相关知识以及必要的学习指南。


## 语言：ES6配合Babel

JavaScript是互联网领域最流行的语言，有一桶江湖的趋势，ES6是目前最新的JavaScript语言标准，它的大部分特性在最新的主流浏览器中已经被实现，Babel是个可插拔ES6编译器。

不用再用CoffeeScript了，因为它的大部分好的特性在ES6都有了，而且CoffeeScript的工具很弱，它的社区也在快速的衰落。


相关学习资源：

* ES6新特性快速入门： [Learn ES6: Say Hello to ES6](https://tutor.mantrajs.com/say-hello-to-ES6/introduction)
* 系统学习ES6：阮一峰的[ECMAScript 6入门](http://es6.ruanyifeng.com/)。


## React

React是一个基于JavaScript的UI框架，也是文本唯一推荐使用的前端框架。

* 从顶到底都是组件，你的应用程序代码非常容易理解
* 学习曲线非常平缓，要知道罗列它所有关键的API都不会超过一页A4纸张。
* JSX非常棒，你可以用获得JavaScript编程语言的能力和工具链来描述页面
* 使用Flux和Redux这种单向数据流非常直白来表达业务逻辑
* React的社区生态圈非常不错，产出了很多高质量的开发工具如Redux
* 在React写的大型项目中，利用Flux管理起数据流/内部状态非常容易（而不像在双向数据绑定中， 例如Angular1.x/Knockout中
* 如果你需要类似于服务端渲染，那么选React没错了

相关学习资源：

* [官方教程](https://facebook.github.io/react/docs/tutorial.html)
* [Scotch.io的入门教程](https://scotch.io/tutorials/learning-react-getting-started-and-concepts)
* [React Components, Elements, and Instances](https://medium.com/@dan_abramov/react-components-elements-and-instances-90800811f8ca)
* React容器： 使得React容器从不同的数据源获取数据并加载到UI组件更加容易，具体内容可以参考[Let’s Compose Some React Containers](https://voice.kadira.io/let-s-compose-some-react-containers-3b91b6d9b7c8#.my9ynz9e2)。

## Meteor

Meteor提供了一种快速构建实时应用程序MVP的方法，对于大多数ToB系统来说，Meteor已经足够好了。


## 应用生命周期：Redux

应用程序需要管理数据状态和生命周期，Redux是毋容置疑的优胜者。

它的作者，Dan Abranmov是一位非常棒的老师（他的教学视频非常易懂好学）。通过那些视频你很容易成为Redux的专家。

* 入门视频：[Getting Started with Redux](https://egghead.io/series/getting-started-with-redux)


## 格式和风格：ESlint配合Airbnb指南


使用ESLint的React插件和良好的es6的支持，几乎非常完美完成lint的工作。JSLint是过时了，ESLint这个软件可以单独完成原本需要 JSHint 和 JSCS 联合起来做的事。

你需要配置他用你的风格约定。强烈建议使用Airbnb的风格指南，大部分可以被 ESLint airbnb config 来严格约束实现。如果团队会在代码风格上产生分歧和争超，那么拿出这份指南来终结所有的不服！它也不是完美的，但保持统一一致的代码风格是要高度推荐的。

一旦开始熟悉它，就建议开启更多的规则。在编辑撰写代码时候越多的捕获不规范（配置你的编辑器IDE使用上这个ESLint插件），就会避免分歧和在决定费神，从而让你和团队更加高效！


## 依赖管理：仅考虑NPM，CommonJS 和ES6模块

忘记之前的bower, 就用NPM。类似 Browserify 和 Webpack 的构建工具把npm的强大功能引到了web上。版本处理变得很简单，你也获得了node生态的大部分模块提供的功能。

你可能会考虑的一件事：如何在开发服务器构建应用。不想Ruby社区的Bundler，npm 常使用通配符来指定版本号，导致你开始书写代码到最后部署时候版本号很可能已经变化了。使用 shrinkwrap 文件来锁定你的依赖（我建议使用 Uber的 shrinkwrap 来获得更见一致性的输入）。同时考虑使用利用类似于 Sinopia 来构建自己的私有npm服务器。

Babel可以把 ES6 模块语法编译到CommonJS。意味着你可面向未来的语法，和在使用构建工具（如Webpack 2.0）时获得它支持的一些静态代码分析工具如 tree shaking 的优势

## 构建工具：Webpack

不想在你的页面文件中加入非常多的外链Script引用，那你就需要一个构建工具来打包你的依赖。如果你也需要允许npm包在浏览器运行工作的工具，那么Webpack就是你需要的。

一年前，关于这块还有不少选择。根据你的开发环境，你可以利用Rails的sprockets来解决类似问题。RequireJS，Browserify和Webpack都是以JavaScript基础的工具，现在RollupJS声称自己在ES6模块上处理的更好。

在一个个尝试使用后，最终还是高度推荐Webpack：

* 它有自己独特的写法，不过即使是最少见的场景也能找到解决的方法
* 主流的模块格式都支持（如AMD，CommonJS，Globals写法）
* 它有处理有问题模块的能力（不是标准的模块写法
* 它能处理CSS文件
* 它有最完善的cache busting/hashing 系统（如果你需要把你的资源发布到CDN）
* 它内置热加载功能
* 它能加载几乎你需要的一切
* 它一套令人惊叹的优化列表

Webpack目前也是处理大型SPA应用项目的最好方案，利用它的代码切割（code splitting）和懒加载特性。


## 测试：Mocha + Chai + Sinon

目前在 JavaScript 单元测试上，我们有众多选择，你选择任何一个都不会错太多。因为你开始做单元测试，你就走对一大步了。

我对一个测试框架的的选择标准是：

* 它应该可以在浏览器中运行从而方便调试
* 它应该运行的足够快
* 它可以很好的处理解决异步测试
* 它可以在命令行就能很方便的使用
* 它应该允许我使用任意断言库，而不会约束限制


对于React而言，Airbnb的Enzyme和Teaspoon是不错的相关工具选择。


## 客户端软件：Electron

Electron 是Atom这个优秀编辑器的背后基石。你可以用它来构建自己的应用程序。它的核心，就是一个特殊版本的Node可以来打开Chrome窗口来渲染GUI页面，并且能够获取到操作系统底层的API（不用借助浏览器的安全沙箱等措施）。你可以打包你的应用程序像其他的桌面客户端软件那样分发安装包，并且辅以自动更新机制。

这就是用来构建横跨OSX，WIndows和Linux这多个桌面环境的应用软件的最简单的方式，利用起上面提到的所有好用的工具。它也有不错的文档和活跃的社区支持。

你也许也听过nw.js（之前叫node-webkit）它年事已高，Electron比它更稳健，更容易上手使用。

来使用这个模板项目来开搞自己的Electron，React和热更新项目吧，你可以看看这些东西是怎么相互配合工作的~
