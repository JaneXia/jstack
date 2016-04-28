# ESLint

```
{
 "plugins":[
    "react"
 ],
 "parseOptions": {
    "ecmaVersion": 6, // ECMAScript 6
     /*
      * 默认值为script 
      * 如果你的代码使用的ECMAScript的modules,改成module
     */
    "sourceType": "module",
    "ecmaFeatures":{
        "experimentalObjectRestSpread": true, // 使用rest参数,扩展运算符
        "globalReturn": true, // 全局return
        "jsx": true // 支持jsx
    }
 },
 "rules":{
    ...
 }
}
```
## rules


**表示含义**

| 值 | 含义 |
| -- | -- |
| "off" or 0 | 不校验此规则 |
| "warn" or 1 | 如不符合规则，显示警告 |
| "error" or 2 | 如不符合规则，显示错误|

** 具体规则**
* **array-bracket-spacing **定义数组格式间距

    * `"never"` 默认值
    * `"always"` 使用间隔    
          样例："array-bracket-spacing": [2, "always"]
          var arr = [ 'foo', 'bar' ];  // √ 
          var arr = ['foo', 'bar'];  // x          
* **arrow-spacing** 箭头间距,箭头函数前后是否有间距

      样例："arrow-spacing": 2
      (a) => {} // √
      (a)=>{} // x      
* **block-scoped-var** 

      样例："block-scoped-var": 0  // 不校验此规则
      function doIf() { // √
        var build;
        if (true) {
          build = true;
        }
        console.log(build);
      }
      
      function doIf() { // x
        if (true) {
          var build = true;
        }
        console.log(build);
      }
     
* **brace-style** 

      样例："brace-style": [2, "1tbs", {"allowSingleLine": true}]
        if (foo) { // √
          bar();
        }
        if （foo） // x
        {
          bar();
        }
        if (foo) {
          bar();
        } else {
          baz();
        }

        if (foo) { bar(); }       // 单行
        // when there are no braces, there are no problems
        if (foo) bar();
        else if (baz) boom();
            
* **callback-return**

      样例： "callback-return": 2
      默认值：["callback", "cb", "next"]
      function doSomething(err, callback) { // √
        if (err) {
            return callback(err);
        }
        callback();
      }
      
* **camelcase**  驼峰命名

      样例："camelcase": [2, {"properties": "always"}],

      ---- 通过 ----
      var myFavoriteColor   = "#112C85"; // √      
      var _myFavoriteColor  = "#112C85"; // √
      var myFavoriteColor_  = "#112C85"; // √
      var MY_FAVORITE_COLOR = "#112C85"; // √
      var foo = bar.baz_boom;  // √
      var foo = { qux: bar.baz_boom };  // √
      var { category_id: category } = query;  // √
      obj.do_something();  // √
      
      ---- 不通过 ----
      var my_favorite_color = "#112C85"; // x
      obj.do_something = function() { // x
        // ...
      };
      var obj = { // x
        my_pref: 1
      };
      
      
* **comma-dangle**  使用变量后是否加 `,`

      样例："comma-dangle": [2,"always"]
      
      ---- 通过 ----
      var foo = { 
          bar: "baz",
          qux: "quux",
      };
      var arr = [1,2,]; 
      foo({  
        bar: "baz",
        qux: "quux",
      });
      
      ---- 不通过 ----
      var foo = { 
          bar: "baz",
          qux: "quux"
      };
      var arr = [1,2];  
      foo({  
        bar: "baz",
        qux: "quux"
      });
      
  

* **comma-spacing** 使用变量是否加空格 

      样例：comma-spacing: ["error", { "before": false, "after": true }]
      ---- 不通过 ----
      var foo = 1 ,bar = 2;
      var arr = [1 , 2];
      var obj = {"foo": "bar" ,"baz": "qur"};
      foo(a ,b);
      new Foo(a ,b);
      function foo(a ,b){}
      a ,b
      
      ---- 通过 ----
        var foo = 1, bar = 2
          , baz = 3;
      var arr = [1, 2];
      var arr = [1,, 3]
      var obj = {"foo": "bar", "baz": "qur"};
      foo(a, b);
      new Foo(a, b);
      function foo(a, b){}
      a, b
      
* **comma-style**
        
        样例：eslint comma-style: ["error", "last"]
        ---- 通过 ----
        var foo = 1, bar = 2;
        var foo = 1,
            bar = 2;
        var foo = ["apples",
                   "oranges"];
        function bar() {
            return {
                "a": 1,
                "b:": 2
            };
        }
        
        ---- 不通过 ----
        var foo = 1
        ,
        bar = 2;
        var foo = 1
          , bar = 2;
        var foo = ["apples"
                   , "oranges"];
        function bar() {
            return {
                "a": 1
                ,"b:": 2
            };
        }
* **complexity**

      样例：eslint complexity: ["error", 2]
         
        ---- 通过 ----
        function a(x) {
            if (true) {
                return x;
            } else {
                return 4;
            }
        }
        
        ---- 不通过 ---- 
        function a(x) {
            if (true) {
                return x;
            } else if (false) {
                return x+1;
            } else {
                return 4; // 3rd path
            }
        }
* **computed-property-spacing **   
      样例：computed-property-spacing: ["error", "never"]
      ---- 通过 ----
      obj[foo]
      obj['foo']
      var x = {[b]: a}
      obj[foo[bar]]
      
      ---- 不通过 ----
      obj[foo ]
      obj[ 'foo']
      var x = {[ b ]: a}
      obj[foo[ bar ]]
        
* **consistent-return **
      样例：eslint consistent-return: 2
      ---- 通过 ----
      function doSomething(condition) {

          if (condition) {
              return true;
          } else {
              return false;
          }
      }

      function Foo() {
          if (!(this instanceof Foo)) {
              return new Foo();
          }

          this.a = 0;
      }
      ---- 不通过 ----
      function doSomething(condition) {

          if (condition) {
              return true;
          } else {
              return;
          }
      }

      function doSomething(condition) {

          if (condition) {
              return;
          } else {
              return true;
          }
      }

      function doSomething(condition) {

          if (condition) {
              return true;
          }
      }
        
* consistent-this
* curly
* default-case
* dot-location
* dot-notation
* eol-last
* eqeqeq
* func-names
* func-style
* 
  
  
        
    
