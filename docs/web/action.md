# Action

Action是在应用程序中处理 **业务逻辑** 的函数，它的第一个参数是上下文，其它传入参数支持具体的业务功能。Action的功能包括：

* 数据验证
* 状态管理
* 远端数据交互

注意事项：
* Action里所有操作都基于程序上下文和传入的参数
* 除了库以外，不能导入任何ES2015模块
* 需要避免在Action里面使用全局变量

举例如下：

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
