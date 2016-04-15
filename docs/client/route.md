# 路由和组件挂载

在Mantra里，路由唯一的功能就是将组件挂载(mount)到UI上。可以有多种选择，比如[Flow Router](https://github.com/kadirahq/flow-router/)和[React Router](https://github.com/rackt/react-router)。

下面例子使用FlowRouter作为路由:

```js
import React from 'react';
import {FlowRouter} from 'meteor/kadira:flow-router';
import {mount} from 'react-mounter';

import MainLayout from '/client/modules/core/components/main_layout.jsx';
import PostList from '/client/modules/core/containers/postlist';

export default function (injectDeps) {
  const MainLayoutCtx = injectDeps(MainLayout);

  FlowRouter.route('/', {
    name: 'posts.list',
    action() {
      mount(MainLayoutCtx, {
        content: () => (<PostList />)
      });
    }
  });
}
```
