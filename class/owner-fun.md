# owner作用域下的方法

作用域默认为window，可自行设置，如将owner设置为 `var app={}` 则该作用域下的方法调用方法为app.xxx。

应注意，本节下的方法实际上都是挂有 `owner.` 的前缀的，文档以其为默认情况 `window.` 编写。

## IsNullOrEmpty(val)

验证是否存在

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
val | 任意 | - | 待验证的变量 | *

### 返回值

`Boolean` true：变量undefined/null/空字符串；false：存在

### 示例

```js

var a = undefined,
    b = null,
    c = '',
    d = true,
    e = false,
    f = function() {alert(1)},
    g = 0,
    h = 1,
    i = 'string',
    j = [1, 2],
    k = {name: 'yang'};

IsNullOrEmpty(a) ===> true *
IsNullOrEmpty(b) ===> true *
IsNullOrEmpty(c) ===> true *
IsNullOrEmpty(d) ===> false
IsNullOrEmpty(e) ===> true *
IsNullOrEmpty(f) ===> false
IsNullOrEmpty(g) ===> true *
IsNullOrEmpty(h) ===> false
IsNullOrEmpty(i) ===> false
IsNullOrEmpty(j) ===> false
IsNullOrEmpty(k) ===> false

```

## enpty_obj(obj)

清空obj对象中的value值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 待清空对象 | *

### 返回值

`Object` value值均为null的对象

### 示例

```js

var obj = {
    name: 'yang',
    friend: [
        'd', 'z', 'l', 'p', 'w', 'j', 'c'
    ],
    year: 23
};

enpty_obj(obj);

    ===> {
        name: null,
        friend: null,
        year: null
    }

```

## IsNumber(value)

变量是否为number类型

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
value | 任意类型 | - | 待验证的变量 | *

### 返回值

`Number` 如果value为number类型，则返回value本身，否则返回0；

### 示例

```js

IsNumber(250) ===> 250
IsNumber('str') ===> 0
IsNumber(false) ===> 0
IsNumber(['str']) ===> 0
IsNumber({name: 'str'}) ===> 0

```

## clone(obj)

对象深度拷贝

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 待拷贝的对象 | *

### 返回值

`Object` 拷贝出来的新对象

### 示例

```js

//非深度复制
var old_obj = {
    name: 'yang'
};
var new_obj = obl_obj;
new_obj.name = 'yzh';
    ===> old_obj === new_obj === {
        name: 'yzh'
    }

//深度复制
var deep_old = {
    name: 'yang'
};
var deep_new = clone(deep_old);
deep_new.name = 'yzh';
    ===> deep_old === {
        name: 'yang'
    };
    ===> deep_new === {
        name: 'yzh'
    };

```

## arrBuildTree(targetArr, parentKeyWord, selfKeyWord)

p2

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
targetArr | Array | - | 待拼接的数组 | *
url | String | - | 标明上级的关键字 | *
url | String | - | 自身关键字 | *

### 返回值

`Array` 拼接后的树形数组

### 示例

```js

var arr = [
    {name: 'yang', id: 1, parentid: 0},
    {name: 'zi', id: 2, parentid: 1},
    {name: 'hao', id: 3, parentid: 1},
    {name: 'tai', id: 4, parentid: 3},
    {name: 'shuai', id: 5, parentid: 3},
    {name: 'le', id: 6, parentid: 3},
];

var tree = arrBuildTree(arr, 'parentid', 'id')

    ===> [{"name":"yang","id":1,"parentid":0,"children":[
            {"name":"zi","id":2,"parentid":1},
            {"name":"hao","id":3,"parentid":1,"children":[
                {"name":"tai","id":4,"parentid":3},
                {"name":"shuai","id":5,"parentid":3},
                {"name":"le","id":6,"parentid":3}
            ]}
        ]}]

```

## treeBreakArr(targetTree, childKey)

将树形对象/数组拆分为数组list

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
targetTree | Array/Object | - | 待拆分的树结构 | *
childKey | String | '' | ??? | *

### 返回值

`Object` 拆分后的结果，包含两个key，arr为拆分后的数组，depth为树的深度

### 示例

```js

var tree = [{"name":"yang","id":1,"parentid":0,"children":[
            {"name":"zi","id":2,"parentid":1},
            {"name":"hao","id":3,"parentid":1,"children":[
                {"name":"tai","id":4,"parentid":3},
                {"name":"shuai","id":5,"parentid":3},
                {"name":"le","id":6,"parentid":3}
            ]}
        ]}]

var arr = treeBreakArr(tree, 'children');

    ===>

{"array":[
    {"name":"yang","id":1,"parentid":0,"children":[{"name":"zi","id":2,"parentid":1},{"name":"hao","id":3,"parentid":1,"children":[{"name":"tai","id":4,"parentid":3},{"name":"shuai","id":5,"parentid":3},{"name":"le","id":6,"parentid":3}]}]},
    {"name":"zi","id":2,"parentid":1},
    {"name":"hao","id":3,"parentid":1,"children":[{"name":"tai","id":4,"parentid":3},{"name":"shuai","id":5,"parentid":3},{"name":"le","id":6,"parentid":3}]},
    {"name":"tai","id":4,"parentid":3},
    {"name":"shuai","id":5,"parentid":3},
    {"name":"le","id":6,"parentid":3}
], "depth":3}

```

## getSearch(key)

获取当前地址栏中的 `location.search` 中对应的值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | - | 想获取的值对应的key |

### 返回值

`String/Object` 如果传入key，则返回相应字段，不存在则返回undefined，如果不传入，则会将location.search转为对象返回

### 示例

```js

getSearch() ===> {}

getSearch('id') ===> undefined

```

## toSearch(obj, flag)

将对象转化为 `location.search` 字符串的形式

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 待转换的对象 | *
flag | Boolean | false | 不携带“?” |

### 返回值

`String` 转换后的字符串

### 示例

```js

toSearch({guid: '123', id: 'abc'}) ===> '?guid=123&id=abc'

toSearch({guid: '123', id: 'abc'}, true) ===> 'guid=123&id=abc'

```

## setHash(key, value, callback)

设置当前页面的 `hash` 值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | - | 想要设置的键，如果为对象格式，则将对象转为字符串后设置 | *
value | String | - | 键对应的value |
callback | Function | - | 设置完成后的回调 |

### 返回值

-

### 示例

```js

setHash('name', 'yang', function() {
    alert(1)
});

setHash({
    name: 'yang'
}, function() {
    alert(2)
});

```

## getHash(key)

获取当前地址栏中的 `location.hash` 中对应的值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | - | 想获取的值对应的key |

### 返回值

`String/Object` 如果传入key，则返回相应字段，不存在则返回undefined，如果不传入，则会将location.hash转为对象返回

### 示例

```js

getHash() ===> {}

getHash('id') ===> undefined

```

## getLocal(key)

获取当前页面 `localStorage` 中对应的值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | - | 想获取的值对应的key |

### 返回值

`String/Object` 如果传入key，则返回相应字段，不存在则返回false，如果不传入，则会将localStorage转为对象返回

### 示例

```js

getLocal('user') ===> false

getLocal() ===> {}

```
