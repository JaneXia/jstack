# 路由

路由的主要功能是将组件挂载到界面上，我们使用[Flow Router](https://github.com/kadirahq/flow-router/).

示例如下:

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
