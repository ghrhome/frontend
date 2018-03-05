# 模块模式

采用"宽放大模式"。

```
var module1 = ( function (mod){

　　　　//...

　　　　return mod;

　　})(window.module1 || {});
```

```
(function (factory) {
    "use strict";
    if (typeof define === 'function' && define.amd) {
        define(['jquery'], factory);
    }
    else if(typeof module !== 'undefined' && module.exports) {
        module.exports = factory(require('jquery'));
    }
    else {
        factory(jQuery);
    }
})(function ($, undefined) {
    "use strict";、
    var module1 = ( function (mod){

　　　　//...

　　　　return mod;

　　})(window.module1 || {});

    return module1;
    
})
```



