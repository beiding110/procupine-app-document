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
