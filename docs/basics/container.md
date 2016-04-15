# 容器

容器是Mantra里的集成层，它主要执行如下操作:

* 使用状态修改变量并将它们通过props传递到UI组件里
* 将action传递到UI组件里
* 将应用程序上下文内容传递到UI组件里

容器也是一个React组件，它通过[react-komposer](https://github.com/kadirahq/react-komposer)进行集成，支持不同的数据源，包括Meteor/Tracker, Promises, Rx.js Observable等。它使得React容器从不同的数据源获取数据并加载到UI组件更加容易，具体内容可以参考[Let’s Compose Some React Containers](https://voice.kadira.io/let-s-compose-some-react-containers-3b91b6d9b7c8#.my9ynz9e2)。

容器内需要写如下这些函数：

* 从状态管理模块获取数据的composer函数
* 从依赖注入层获取数据的mapper函数

创建一个容器时需要遵循如下规则：

* 每个文件仅能有一个容器，而且需要被默认导出(default export)
* composer函数和mapper函数需要从容器模块里面导出
* composer函数只能使用从props获得的变量
* mapper函数应该是[纯函数](https://en.wikipedia.org/wiki/Pure_function).

注意：如果您需要将应用程序上下文传递给一个组件，要使用mapper通过props传递。

下面是一个容器的例子:

```js
import PostList from '../components/postlist.jsx';
import {useDeps, composeWithTracker, composeAll} from 'mantra-core';

export const composer = ({context}, onData) => {
  const {Meteor, Collections} = context();
  if (Meteor.subscribe('posts.list').ready()) {
    const posts = Collections.Posts.find().fetch();
    onData(null, {posts});
  }
};

export default composeAll(
  composeWithTracker(composer),
  useDeps()
)(PostList);
```





我们使用React容器从不同的数据源获取数据并加载到UI组件时，[react-komposer](https://github.com/kadirahq/react-komposer)使这项工作更加容易，下面这篇文章可以让您获取更多知识。

* [Let’s Compose Some React Containers](https://voice.kadira.io/let-s-compose-some-react-containers-3b91b6d9b7c8#.my9ynz9e2)
