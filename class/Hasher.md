# Hasher类

生成一个hash监听器

## 方法Hasher.push(key, value)

将当前页面的hash值跳转至参数路径

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | - | String时代表要修改的key，Object时代表整个要修改的hash对象 | *
value | String | - | 要修改的对应value |

### 返回值

生成的新地址

### 示例

```js

var hasher = new Hasher({
    data: {
        $path: '', //特殊变量用于监听hash后不带key的参数，如#/home/index
        id: '' //声明后进行变量劫持监听，直接改变该变量，可以改变地址栏中hash
    },
    watch: { //在此处声明的变量可以在地址栏中的相应变量变化后进行监听并处罚回调
        $path: function(n, o) {
            alert(n)
        }
    },
    mounted: function() {
        this.id = 1;
        this.push('sub', '1');
        this.push({
            '$path': '/home'
        });
    }
})

```

## 方法Hasher.replace(key, value)

将当前页面的hash值跳转至参数路径，且不可返回跳转前的路径

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | - | String时代表要修改的key，Object时代表整个要修改的hash对象 | *
value | String | - | 要修改的对应value |

### 返回值

生成的新地址

### 示例

```js

var hasher = new Hasher({
    data: {
        $path: '',
        sub: ''
    },
    watch: {
        $path: function(n, o) {
            alert(n)
        }
    },
    mounted: function() {
        this.replace('id', '1');
        this.replace({
            '$path': '/home'
        });
    }
})

```
