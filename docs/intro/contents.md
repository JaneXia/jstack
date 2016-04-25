# 内容梗概

本文分为三大部分

**PART I: 横向讨论单个技术的最佳实践**

* **界面组件** UI Components，通过React Dumb Components可复用的组件构建应用
* **状态管理** 应用程序状态管理机制，目前以Redux为主
* **组合容器** 通过容器将状态和action集成到界面组件中的方法
* **业务逻辑** 通过Action来定义业务逻辑，并充分考虑程序解耦问题
* **代码规范** 通过ESLint等工具构建适用于JS技术栈的统一代码规范、命名规范
* **自动测试** 尽量做到代码每一部分代码都是可测试的
* **持续集成** 持续集成系统的构建方案及相关策略
* **数据建模** 采用以MongoDB为主的数据库建模方式


**PART II: 纵向讨论每个应用的构建方式**

* **Web前端** Web前端应用的目录架构以及模块化构建方式，参考[Mantra](https://kadirahq.github.io/mantra/)
* **微信前端** 微信应用的构建方式，类似于Web，不过有一些特殊的地方需要特殊考虑
* **App前端** 通过[ReactNative](http://facebook.github.io/react-native/)构建安卓和iOS应用的方式
* **桌面前端** 通过[Electron](http://electron.atom.io/)构建桌面应用的方式
* **ApiServer**：通过参考[KOA](http://koajs.com/)和[Loopback](http://loopback.io/)等框架构建ApiServer的方式


**PART III: 结合部署实践，讨论高可用大并发互联网平台的构建方式**
