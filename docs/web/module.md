# 模块化架构

Mantra是一个百分之百模块化的应用程序架构，至少应该有一个模块。

程序应该遵循模块化架构，将相关内容定义在特定模块里，并通过import来集成。而所有模块都应该可以通过依赖关系访问上下文，但不能更新上下文。

## 模块定义

每个模块都需要一个定义文件'index.js'，用以导出action路由并接收上下文。而一些简单模块可以省略定义文件，它们也没有action或者路由，也不需要做任何初始化操作。

一个正常的模块定义如下：

```js
export default {
  // 可选
  load(context, actions) {
    // 模块初始化
  },
  // 可选
  actions: {
    myNamespace: {
      doSomething: (context, arg1) => {}
    }
  },
  // 可选
  routes(injectDeps) {
    const InjectedComp = injectDeps(MyComp);
    // load routes and put `InjectedComp` to the screen.
  }
};
```


**Actions**

一个模块可以通过命名空间暴露action，这些命名空间对于应用程序而言是全局的，模块需要确保命名空间的唯一性。

最后，每个模块的所有命名空间都会被合并，并可以在action和容器里面访问。

**路由**

在Mantra里，可以使用任何路由库，如果需要的话，可以在多个模块里面定义路由。



**避免子模块**

在一个模块内**不可以**有子模块。这个决定是为了不必要的复杂性，因为多层嵌套的模块结构是非常难以维护的。

## 核心模块(Core Module)

Mantra是百分之百模块化的，每个应用程序里至少有一个核心模块(core module)。
它仅是一个简单的模块，您需要在加载其它任何模块之前加载这个模块。核心模块是应用程序相关内容的最佳实现位置，包括：

* 核心路由
* 应用程序配置
* 公共库
* 公共action

## 模块组织方式

我们已经讨论了如何在模块里面组织代码以及如何使用它们，但是我并没有讨论过如何组织模块。下面是一些常见的组织模块的方式。

### 单核心模块

简单程序可以将所有代码放到一个模块里，并命名为 `core`，这比较适用于客户端代码比较少的简单程序。



### 核心模块加特性模块

这是在上述“单个核心模块”模式的扩充:

* 有一个具备所有客户端核心代码的core模块，包括所有的路由。
* 针对应用程序的不同特性，具有不同的模块，而这些模块没有路由。

### 多模块

在多模块方式下，没有单个核心模块。

* 针对程序的每个特性都有多个模块。
* 每个模块具有自己的路由。

### 页面模块

注意: 这种方式可以与上述任何方式一起使用。

有时候，我们需要显示一些UI页面。但是它们并没有action，路由和配置。它们只包含UI代码，可能是界面组件或者其它容器，这时可以使用隐含模块。
