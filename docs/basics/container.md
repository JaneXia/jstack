# 容器

容器(Container)又被称作React Smart Component，它也是一个React组件，通过[react-komposer](https://github.com/kadirahq/react-komposer)集成不同的数据源，而
`react-komposer`相关内容可以参考[Let’s Compose Some React Containers](https://voice.kadira.io/let-s-compose-some-react-containers-3b91b6d9b7c8#.my9ynz9e2)

容器主要执行如下操作:

* 通过props给界面组件传递变量
* 通过props给界面组件传递action
* 通过props给界面组件传递上下文context

需要为容器提高如下函数：

* 从状态管理模块获取数据的composer函数
* 从依赖注入层获取数据的mapper函数

创建容器需遵循如下规则：

* 每个文件仅有一个容器，并被默认导出
* composer函数和mapper函数需从容器模块导出
* composer函数只能使用从props获得的变量
* mapper函数应该是[纯函数](https://en.wikipedia.org/wiki/Pure_function).

注意：如果需要将上下文传递给组件，要使用mapper通过props传递。

示例：

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
