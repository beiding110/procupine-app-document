# Vue追加方法

将常用方法以vue原型链的形式嵌入到vue对象中，调用时一般使用 `this.functionName` 的形式调用

## $ajax(settings)

jquery中 $.ajax 的 vue 封装版

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
settings | Object | undefined | 请求的配置参数 | *

### 返回值

-

### 示例

```js

new Vue({
    el: '#app',
    methods: {
        query: functoin() {
            this.$ajax({
                type: 'post', //默认为get
                url: '/ajax/a',
                data: {
                    name: '1'
                },
                fztype: true, //是否以字符串的形式发送复杂对象，默认为false
                callback: function(data, res) {
                    //请求成功回调
                },
                complete: function(data, res) {
                    //请求完成回调
                },
                error:  function(data, res) {
                    //请求错误回调
                },
            })
        }
    }
})

```

## $get(url, data, callback, sendstring)

jquery中 $.get 的 vue 封装版

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
url | String | '' | 请求的地址 | *
data | Object/String | - | 请求中向后人发送的数据 |
callback | Function | - | 请求成功后的回调函数 |
sendstring | Boolean | false | 是否以字符串的形式发送复杂对象 |

### 返回值

-

### 示例

```js

new Vue({
    el: '#app',
    methods: {
        query: functoin() {
            this.$get('/api/a', {
                name: 'yang'
            }, function(data, res) {
                console.log(data, res)
            })
        }
    }
})

```

## $post(url, data, callback, sendstring)

jquery中 $.post 的 vue 封装版

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
url | String | '' | 请求的地址 | *
data | Object/String | - | 请求中向后人发送的数据 |
callback | Function | - | 请求成功后的回调函数 |
sendstring | Boolean | false | 是否以字符串的形式发送复杂对象 |

### 返回值

-

### 示例

```js

new Vue({
    el: '#app',
    methods: {
        query: functoin() {
            this.$post('/api/a', {
                name: 'yang'
            }, function(data, res) {
                console.log(data, res)
            })
        }
    }
})

```

# app-supply中追加的Vue方法

## getRoute(key)

获取vue-router中的params

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | undefined | 需要获取的params名称 | *

### 返回值

- 对应的params

### 示例

```js

new Vue({
    el: '#app',
    mounted() {
        var id = this.getRoute('id')
    }
})

```

## getQuery(key)

获取vue-router中的query

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | undefined | 需要获取的query名称 | 

### 返回值

- 对应的query

### 示例

```js

new Vue({
    el: '#app',
    mounted() {
        var id = this.getQuery('id')
    }
})

```

## getStore(key)

获取vuex中的state

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | undefined | 需要获取的state名称 | *

### 返回值

- 对应的state

### 示例

```js

new Vue({
    el: '#app',
    mounted() {
        var id = this.getStore('id')
    }
})

```

## getGetters(key)

获取vuex中的getters

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | undefined | 需要获取的getters名称 | *

### 返回值

- 对应的getters

### 示例

```js

new Vue({
    el: '#app',
    mounted() {
        var id = this.getGetters('id')
    }
})

```

## goto(obj)

使用vue-router跳转页面

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | undefined | 需要跳转的路由参数，同router.push | *

### 返回值

- 

### 示例

```js

new Vue({
    el: '#app',
    mounted() {
        // this.goto('/login');

        this.goto({
            path: '/login',
            query: {
                id: 123
            }
        });
    }
})

```

## newRule(arg)

获取vue-router中的params

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
arg[0] | String | undefined | 错误提示中的label名称 | *
arg[1,2,3...] | String | undefined | 下方对应的可选内容 | *

```

required: '必填',
max10: '最长10位（可自定义）',
min10: '最长10位（可自定义）',
mobile: '手机号',
string: '字符串',
number: '数字',
boolean: '布尔',
method: '方法',
regexp: '正则',
integer: 'integer',
float: '浮点数',
array: '数组',
object: '对象',
enum: 'enum',
date: '日期',
url: 'url地址',
hex: '哈希',
email: '电子邮件',
ucc: '统一信用代码',

```

### 返回值

- 对应的el-form-item使用的规则

### 示例

```html

<el-form-item
    label="手机号"
    prop="form.mobile"
    :rules="newRule('手机号', 'required', 'mobile')"
></el-form-item>

```