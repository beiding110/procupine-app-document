# window下的方法

作用域直接在window下的方法

## ajaxResCheck(obj, settings, callback)

根据前端规范，对返回值中的code进行分类，根据不同的code约定不同的结果操作

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 接口返回的json对象 | *
settings | Object | - | ajax中的功能设置对象 |
callback | Function | - | code为 `v/pglist/throw-xxx` 时的回调函数 | *

### 返回值

-

### 示例

```js

$.ajax('', {

}, function(data) {
    var obj;
    if(typeof(data) === 'string') {
        obj = JSON.parse(data);
    };
    ajaxResCheck(obj, function(res, response) {
        console.log(res, response)
    })
})

```

### 附录-ajax中返回的code及含义

code | 说明 | json示例
- | - | -
`v` | 成功，obj.tdata和obj作为参数传给callback | { "code": "v", "msg": null, "errors": {}, "tdata": {} }
`pglist` | 列表 json 成功，obj作为参数传给callback | { "total": 4,//总条数 "startRow": 0, //开始行 "code": "pglist",  "pageIndex": 1, //当前页 "pageSize": 1000, //每页条数 "rows": [], //数据项 "end": 1000, //终止项 "start": 0 //起始项 }
`valerror` | 字段验证失败（前端传值错误）弹框展示obj.msg | { code: 'valerror', msg：'' //错误信息 }
`login-index` | 超时或未登录，跳转至前台写死的登录页面 | { code: 'login-index' }
`error` | 后台报错，弹框展示obj.msg | { code: 'error', msg：' ' //错误信息 }
`jump-url` | 后台控制跳转页面至obj.url | { code: 'jump-url', url：' ' //跳转路径 }
`throw-xxx` | 多功能code，方法会将该整个返回的对象obj以参数的形式传给callback，其中code为xxx（去掉了throw-） | { "code": "throw-xxx", "msg": null, "errors": {}, "tdata": {} }

## ShowMsgBox(msg, type, callback)

提示框

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
msg | String | '' | 提示内容 | *
type | String | "warning" | 提示框类型success / info / warning / error |
callback | Function | - | 点击确定后的回调函数 |

### 返回值

-

### 示例

```js

ShowMsgBox('操作成功', 'success', function() {
    window.location.back();
})

ShowMsgBox('错误', null, function() {
    window.location.reload();
})

```

## ShowMsg(msg, type, callback)

提示消息（无操作）

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
msg | String | '' | 提示内容 | *
type | String | "warning" | 提示框类型success / info / warning / error |
callback | Function | - | 自动关闭的回调函数 |

### 返回值

-

### 示例

```js

ShowMsg('操作成功', 'success', function() {
    window.location.back();
})

ShowMsg('错误', null, function() {
    window.location.reload();
})

```

## ShowConfirm(msg, type, cb1, cb2)

确认操作弹框

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
msg | String | '' | 提示内容 | *
type | String | "warning" | 提示框类型success / info / warning / error |
cb1 | Function | - | 点击确定的回调函数 |
cb2 | Function | - | 点击取消的回调函数 |

### 返回值

-

### 示例

```js

ShowConfirm('操作成功', 'success', function() {
    window.location.back();
}, function() {
    alert('取消操作')
})

ShowConfirm('错误', null, function() {
    window.location.reload();
})

```
