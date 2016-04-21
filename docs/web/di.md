# 依赖注入DI

依赖注入是面向对象编程的设计原则中常用的解耦方法，可以将程序分解为相互独立的部分。[`react-simple-di`](https://github.com/kadirahq/react-simple-di)是Mantra里面常用的DI方法，可以将上下文会注入到action、组件和容器里。

具体而言，依赖会被注入到应用程序最高层的组件里，比如布局组件，可以在路由里面实现注入:

```js
import React from 'react';
export default function (injectDeps) {
  // See: Injecting Deps
  const MainLayoutCtx = injectDeps(MainLayout);

  // Routes related code
}
```
