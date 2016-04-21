# 状态管理

应用程序状态可以分为两大类：

1. **本地状态** - 仅存在于客户端的状态，不与服务端同步，比如错误信息，验证消息和当前页面等。
2. **远端状态** - 需要从服务端获取并进行同步的状态。

应用程序里有多种管理状态的方法，包括：

* Meteor/MiniMongo (远端状态)
* Tracker/ReactiveDict (本地状态)
* FlowRouter (本地状态)
* Redux (本地状态)
* GraphQL (远端状态)
* Falcor (远端状态)

下面是一些主要遵循的规则：

* 写状态：任何写状态操作应该在action里完成
* 读状态：可以在action和容器里面读取状态
* **严禁在界面组件里直接读写状态**

最后是一些状态管理的例子：

* [读本地状态 - 在容器里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/containers/newpost.js#L6)
* [写本地状态 - 在action里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/actions/posts.js#L4)
* [读远端状态 - 在容器里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/containers/postlist.js#L7)
