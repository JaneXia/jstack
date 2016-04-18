# 上下文

应用程序上下文对所有action和容器都是可见的，所以可以将应用程序共享变量放在这个地方，包括

* Meteor命名空间
* Meteor数据集
* LocalState
* FlowRouter
* 其它Meteor包
* Redux存储
* Rest客户端
* DDP客户端

下面是一个简单的例子：

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
