# 上下文

上下文是保存应用程序共享变量的地方，action和容器都可以通过上下文放在这些变量，它们包括：

* Meteor 命名空间
* Meteor Collection
* LocalState
* FlowRouter
* Meteor Package
* Redux存储
* Rest客户端
* DDP客户端

下面例子创建并导出了整个应用程序客户端的上下文：

```js
import * as Collections from '/lib/collections';
import {Meteor} from 'meteor/meteor';
import {FlowRouter} from 'meteor/kadira:flow-router';
import {ReactiveDict} from 'meteor/reactive-dict';
import {Tracker} from 'meteor/tracker';

export default function () {
  return {
    Meteor,
    FlowRouter,
    Collections,
    LocalState: new ReactiveDict(),
    Tracker
  };
}
```
