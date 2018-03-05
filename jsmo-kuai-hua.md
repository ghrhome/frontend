# 模块模式

采用"宽放大模式"。

```
var module1 = ( function (mod){

　　　　//...

　　　　return mod;

　　})(window.module1 || {});
```



