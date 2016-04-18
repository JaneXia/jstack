# 依赖注入

Mantra使用依赖注入来区分应用程序的不同部分，包括界面组件和action。可以使用[`react-simple-di`](https://github.com/kadirahq/react-simple-di)来实现依赖注入。

一旦配置完成，应用程序上下文会被自动注入到每个action里。

另外，应用程序上下文也可以在容器里访问。

依赖会被注入到应用程序最高层的组件里，比如布局(Layout)组件，您可以在路由里面实现注入:

```js
import React from 'react';
export default function (injectDeps) {
  // See: Injecting Deps
  const MainLayoutCtx = injectDeps(MainLayout);

  // Routes related code
}
```
