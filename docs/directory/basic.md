# 基本约定

目前Meteor没有对项目目录结构做出类似Rails那样严格的要求和限制，不过不同的目录有着不同的含义。

## 特殊目录

不做出特殊约定的情况下，一般的Meteor文件都会在client与server端同时加载。不过下面这些目录有一些特殊的限制。

* **client** 任何在client目录下的文件仅在client端加载。
* **server** 任何在server目录下的文件仅在server端加载。
* **public** 所有public下的文件可以在client访问，访问这些文件时将public目录是为根目录。比如访问`public/bg.png`的url是`/bg.png`。
* **private** 仅server端可访问，通过Assets的API访问。
* **tests** 这个目录并不在任何地方加载，它只用于测试代码。
* **node_modules**  这个目录下放置nodejs的包，它并不被meteor直接加载，需要通过特定方式使用。
* **packages** 本地的包，不直接加载。
* **.** 以.开头的目录或文件，不加载，比如.meteor和.git。


## 加载顺序

从Meteor1.3开始，我们可以通过import来定义加载优先级，不过在更早的版本里会按照如下优先级进行加载:

1. HTML模板文件总是最先加载
1. 以main.开头的文件最后加载
1. 接着加载lib目录下的文件
1. 深层次目录的文件先加载
1. 剩下的文件按照字母顺序加载
