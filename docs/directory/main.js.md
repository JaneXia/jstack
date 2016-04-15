# main.js

这里是Mantra应用程序的入口，初始化程序上下文并加载模块，这些工作是由一个被称作`mantra-core`的库完成的。

下面是一个例子：

```js
import {createApp} from 'mantra-core';
import initContext from './configs/context';

// modules
import coreModule from './modules/core';
import commentsModule from './modules/comments';

// init context
const context = initContext();

// create app
const app = createApp(context);
app.loadModule(coreModule);
app.loadModule(commentsModule);
app.init();
```
