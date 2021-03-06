# 单元测试

测试是Mantra和核心内容，可以对程序的每部分进行测试。具体实现时可以使用诸如[Mocha](https://mochajs.org/), [Chai](http://chaijs.com/), 和 [Sinon](http://sinonjs.org/)这样的常见工具。

## 为什么需要测试

## 什么是Behavior-driven Development (BDD)

## Stub, mock, fake分别适用于怎样的测试场合

## mantra中的测试实战

在mantra里，您可以对应用程序的三个核心部分进行单元测试，示例如下：

### UI组件

我们使用[enzyme](https://github.com/airbnb/enzyme)进行UI测试。通过[这个例子](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/components/tests/post.js)来看一些测试样例。


[示例](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/components/tests/post.js)


### Actions

[示例](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/actions/tests/posts.js)

### 容器

[示例](https://github.com/mantrajs/mantra-sample-blog-app/blob/master/client/modules/core/containers/tests/post.js)
