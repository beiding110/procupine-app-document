# ShadeBox类

快速创建遮罩层类

## show()

显示ShadeBox实例

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
- | - | - | - |

### 返回值

-

### 示例

```js

var sb = new ShadeBox({
    style: {
        background: 'red'
    },
    animate: 400, //或'0.4s'，动画持续时间，默认0.3s
    innerHTML: '<h1>我是ShadeBox实例</h1>'
});

sb.show();

```

## hide()

隐藏ShadeBox实例

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
- | - | - | - |

### 返回值

-

### 示例

```js

var sb = new ShadeBox({
    style: {
        background: 'red'
    },
    animate: 400, //或'0.4s'，动画持续时间，默认0.3s
    innerHTML: '<h1>我是ShadeBox实例</h1>'
});

sb.show();

setTimeout(function() {
    sb.hide();
}, 2000);

```
