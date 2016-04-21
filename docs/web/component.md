# 界面组件

我们希望通过构建 **可复用** 组件的方式来构建应用程序，不断提高生产效率。可复用组件是一种完全不依赖于它所在渲染环境的组件，它仅依赖于输入信息，对于特定的输入参数结果是确定的。

React目前最为流行的js前端框架，也是实现界面组件的最佳选择，我们在项目里面使用React的[无状态组件](https://medium.com/@joshblack/stateless-components-in-react-0-14-f9798f8b992d)，
它不依赖程序，也不能读取程序状态，用来渲染的数据和事件处理函数是通过props传入的。

当编写界面组件时，可以使用任意其它React组件，包括：

* 应用程序其它地方定义的界面组件
* 来自NPM的界面组件（比如 `material-ui`).
* 应用程序中任何的容器
* 可以直接从NPM组件中导入任何[纯函数](https://en.wikipedia.org/wiki/Pure_function)，并在界面组件中使用。

下面是一个简单的界面组件：

```html
import React from 'react';

const PostList = ({posts}) => (
  <div className='postlist'>
    <ul>
      {posts.map(post => (
        <li key={post._id}>
          <a href={`/post/${post._id}`}>{post.title}</a>
        </li>
      ))}
    </ul>
  </div>
);

export default PostList;
```
