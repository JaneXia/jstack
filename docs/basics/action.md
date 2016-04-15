# Action

Actions是在应用程序中写 **业务逻辑** 的地方，包括：

* 验证
* 状态管理
* 远端数据交互

Action是一个函数，它的第一个参数是应用程序上下文，其它参数是基于调用场景的。

注意：
* 您在action里所有的操作都需要基于程序上下文和传入的参数
* 除了库以外，您不能导入任何ES2015模块
* 您需要避免在Action里面使用全局变量

下面是一个action的例子：

```js
export default {
  create({Meteor, LocalState, FlowRouter}, title, content) {
    if (!title || !content) {
      return LocalState.set('SAVING_ERROR', 'Title & Content are required!');
    }

    LocalState.set('SAVING_ERROR', null);

    const id = Meteor.uuid();
    // There is a method stub for this in the config/method_stubs
    // That's how we are doing latency compensation
    Meteor.call('posts.create', id, title, content, (err) => {
      if (err) {
        return LocalState.set('SAVING_ERROR', err.message);
      }
    });
    FlowRouter.go(`/post/${id}`);
  },

  clearErrors({LocalState}) {
    return LocalState.set('SAVING_ERROR', null);
  }
};
```
