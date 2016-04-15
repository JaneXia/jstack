# 客户端

基于如下几点考虑，客户端是应用程序的重点：

* 客户端是代码最多的地方，需要投入的工作量也最多，服务端则相对容易管理和组织。
* 未来客户端程序将会通过schema与服务端交互，客户端程序对于服务端的实现机制是一无所知的。
* Mantra不相信[万能应用](https://voice.kadira.io/say-no-to-isomorphic-apps-b7b7c419c634#.hogcs5r24)，
它鼓励单个服务器和多个客户端应用程序交互，并在最大程度实现代码共享。

基于上述的事实，将客户端和服务端代码混合不是一个好主意。**这个规范里面讨论的内容主要是针对客户端的**，服务端内容可以参考附录B。


* [ES6](es6.md)
* [UI使用React](ui.md)
* [Action](action.md)
* [状态管理](state.md)
* [容器](container.md)
* [应用程序上下文](context.md)
* [依赖注入](di.md)
* [路由和组件挂载](route.md)
* [库](lib.md)
* [测试](test.md)
* [模块](module.md)
* [单入口点](entry.md)
