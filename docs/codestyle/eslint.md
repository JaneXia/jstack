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
        "experimentalObjectRestSpread": true, // 允许使用rest参数,扩展运算符
        "globalReturn": true, // 全局return
        "jsx": true // 支持jsx
    }
 },
 "rules":{
    ...
 }
}
```
### rules
* 数组间隔,默认值为default,即数组前后没有间隔
    
    `"array-bracket-spacing": [2, "always"]` 

    `var arr = [ 'foo', 'bar' ];  // always`

    `var [ x, y ] = z;  // never `
    
