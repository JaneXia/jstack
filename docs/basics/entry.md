# 单入口点

我们希望Mantra程序的运行是可预期的，这样我们会在程序里放置唯一的入口点`client/main.js`。它会初始化程序上下文并加载程序中所有的模块，下面是一个示例：

```js
import {createApp} from 'mantra-core';
import {initContext} from './configs/context';

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
