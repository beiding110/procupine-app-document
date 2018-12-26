# win对象

封装了常用的地址跳转和不记录历史记录跳转方法

## win.g(path, callback)

进行路径跳转，跳转地址后加入跳转时的时间戳（可防缓存）

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
path | String/Object | - | 应传入String类型的url地址或包含path和query属性的Object | *
callback | Function | - | 跳转成功的回调 |

### 返回值

-

### 示例

```js

win.g('http://www.baidu.com');

win.g({
    path: 'http://www.baidu.com',
    query: {
        id: 'id123',
        name: 'yang'
    }
});

```

## win.r(path, callback)

进行路径跳转（不可返回跳转前页面），跳转地址后加入跳转时的时间戳（可防缓存）

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
path | String/Object | - | 应传入String类型的url地址或包含path和query属性的Object | *
callback | Function | - | 跳转成功的回调 |

### 返回值

-

### 示例

```js

win.r('http://www.baidu.com');

win.r({
    path: 'http://www.baidu.com',
    query: {
        id: 'id123',
        name: 'yang'
    }
});

```
