## web随身记1

### 非负浮点数正则表达式
```javaScript
let rNum = /^\d+(\.\d+)?$/;
```
[查看全部](http://lives.iteye.com/blog/1397939)

### css正片叠底效果
```css
mix-blend-mode: darken;  
```

### 重载console.log
```javaScript
// 1. 普通的重载
console.log = (function (oriFun) {
  return function (s) {
    oriFun.call(console, 1);
  }
})(console.log);

// 或者
console.log = ((oriFun) => (s) => {
  oriFun.call(console, 1);
})(console.log);

// 2. 重载为logger.info的功能
const util = require('util');
// 重载console.log
console.log = function () {
    logger.info.apply(logger, formatArgs(arguments));
};

// 把多个参数如 ('test', 'test') => 'test test'
function formatArgs(args) {
    return [util.format.apply(util.format, Array.prototype.slice.call(args))];
}
```

### `Object.is()`
是ES6引入的来弥补全等运算符的不准确运算。

### 正则表达式 /g
js 正则 global会影响lastindex出现这种情况  
  
![](https://i.loli.net/2018/04/09/5acace911f18f.jpg
)

解决方法，去掉/g
