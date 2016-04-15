# 状态管理

在应用程序中，我们需要处理不同类型的状态，这些状态可以分为两大类型：

1. **本地状态** - 仅存在于客户端的状态，不与服务端同步，比如错误信息，验证消息和当前页面等。
2. **远端状态** - 需要从服务端获取并进行同步的状态。

应用程序里有多种管理状态的方法，包括：

* Meteor/MiniMongo (远端状态)
* Tracker/ReactiveDict (本地状态)
* FlowRouter (本地状态)
* Redux (本地状态)
* GraphQL (远端状态)
* Falcor (远端状态)

JavaScript社区很多的关于状态管理的新方法，Mantra是很灵活的，您可以使用任何需要的方法。

比如，程序启动时您可以使用如下方法

* Meteor/MiniMongo (远端状态)
* Tracker/ReactiveDict (本地状态)
* FlowRouter (本地状态)

然后，您可以使用其它方法

注意：Mantra有一些管理状态的强制规则

* 任何针对状态的写操作应该在action里完成
* 可以在action和容器里面读取状态
* 不应该在UI组件里直接读写状态，UI组件需要完全不了解程序的状态

下面是一些状态管理的例子：

* [读本地状态 - 在容器里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/containers/newpost.js#L6)
* [写本地状态 - 在action里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/actions/posts.js#L4)
* [读远端状态 - 在容器里](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/containers/postlist.js#L7)
