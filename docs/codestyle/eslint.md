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
* 
      样例： "callback-return": 2
      默认值：["callback", "cb", "next"]
      
* camelcase
* comma-dangle
* comma-spacing
* comma-style
* complexity
      
   
        
    
