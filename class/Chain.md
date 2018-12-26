# Chain类

责任链式调用类

## 方法link(fun)

在责任链上加入运行的单元

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
fun | Function | - | 要运行的单元函数 | *

### 返回值

`this` 当前Chain的实例

### 示例

```js

(new Chain()).link(function(obj, next) {
    if(obj > 0) {
        alert('正数')
    } else {
        next()
    }
}).link(function(obj, next) {
    if(obj < -5) {
        alert('负数，小于-5')
    } else {
        next()
    }
}).link(function(obj, next) {
    if(obj < -1) {
        alert('负数，大于-5，小于-1')
    }
})

```

## 方法run(obj)

执行Chain实例中链接好的责任链 `如果只link，不run，则责任链不会执行`

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | 任意 | - | 责任链中通用的参数 |

### 返回值

-

### 示例

```js

setTimeout(function() {
    console.log(1)
}, 2000);
setTimeout(function() {
    console.log(2)
}, 1000);
setTimeout(function() {
    console.log(3)
}, 3000);

===> 2 1 3 总共耗时三秒

(new Chain()).link(function(obj, next) {
    setTimeout(function() {
        console.log(1);
        next();
    }, 2000);
}).link(function(obj, next) {
    setTimeout(function() {
        console.log(2);
        next();
    }, 1000);
}).link(function(obj, next) {
    setTimeout(function() {
        console.log(3);
        next();
    }, 3000);
}).run()

===> （运行2s后）1（又运行1s后）2（又运行3s后）3

```
