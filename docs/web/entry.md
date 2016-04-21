# 程序入口

程序里唯一的程序入口`client/main.js`可以让程序行为可预期，通常在这里初始化程序上下文并加载程序中所有的模块。

下面是客户端程序入口的示例：

```js
import {createApp} from 'mantra-core';
import {initContext} from './configs/context';

// 导入模块
import coreModule from './modules/core';
import commentsModule from './modules/comments';

// 初始化上下文
const context = initContext();

// 创建应用并加载模块
const app = createApp(context);
app.loadModule(coreModule);
app.loadModule(commentsModule);
app.init();
```
