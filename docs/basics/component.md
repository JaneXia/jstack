# 界面组件

React是一个基于JavaScript的UI框架，Mantra使用React实现UI表现层。

我们目前很少使用React组件的状态，而是通过props获取数据，React的[无状态组件](https://medium.com/@joshblack/stateless-components-in-react-0-14-f9798f8b992d)使这项工作非常容易。

UI组件不依赖程序，也不能读取程序状态，用来渲染UI组件的数据和事件处理函数是通过props传入的。有时在UI组件里会使用临时本地状态，但是这样的状态永远不会被外部的内容引用。

当编写UI组件时，可以使用任意其它React组件。下面这些地方可以导入React组件

* 应用程序其它地方定义的UI组件
* 来自NPM的UI组件（比如 material-ui).
* 应用程序中任何的容器

您可以直接从NPM组件中导入任何库函数，并在UI组件中使用。这些函数应该是[纯函数](https://en.wikipedia.org/wiki/Pure_function).

下面是一个简单的UI组件：

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
