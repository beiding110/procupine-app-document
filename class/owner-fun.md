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

## setLocal(key, value)

设置当前页面的 `localStorage` 值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | - | 想要设置的键，如果为对象格式，则将对象转为字符串后设置 | *
value | String | - | 键对应的value |

### 返回值

`Object` 将设置完的localStorage对象返回

### 示例

```js

setLocal('name', 'yang');

setLocal({
    name: 'yang'
});

```

## getSession(key)

获取当前页面 `sessionStorage` 中对应的值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String | - | 想获取的值对应的key |

### 返回值

`String/Object` 如果传入key，则返回相应字段，不存在则返回false，如果不传入，则会将sessionStorage转为对象返回

### 示例

```js

getSession('user') ===> false

getSession() ===> {}

```

## setSession(key, value)

设置当前页面的 `sessionStorage` 值

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
key | String/Object | - | 想要设置的键，如果为对象格式，则将对象转为字符串后设置 | *
value | String | - | 键对应的value |

### 返回值

`Object` 将设置完的sessionStorage对象返回

### 示例

```js

setSession('name', 'yang');

setSession({
    name: 'yang'
});

```

## timeToDate(time)

取日期字符串的年月日部分

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
time | String | - | 待处理的字符串 | *

### 返回值

`String` 切分后的日期

### 示例

```js

timeToDate('2018-12-25 18:38') ===> '2018-12-25'

```

## getRandom(length)

生成某个长度的随机数字符串

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
length | Number | - | 随机字符串的长度 | *

### 返回值

`String` 随机数字符串

### 示例

```js

getRandom(3) ===> '703'

```

## getTimeStrmp()

生成一个当前时间的时间戳

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
- | - | - | - |

### 返回值

`Number` 生成的时间戳

### 示例

```js

getTimeStrmp() ===> 1545734596266

```

## floatToPercent(num, length, range)

浮点小数转为百分比字符串

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
num | Number | - | 待转换的浮点小数 | *
length | Number | 0 | 小数点后保留的位数 |
range | Boolean | false | 是否最大不能超过100% |

### 返回值

`String` 生成的百分比字符串

### 示例

```js

floatToPercent(0.533, 2) ===> '53.30%'

floatToPercent(1.53, 2, true) ===> '100.00%'

```

## wxPay(obj, callback, errcallback)

在`微信服务器中`调起微信支付

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 调起支付的参数,应包含示例中的参数 | *
callback | Function | - | 支付成功的回调函数 | *
errcallback | Function | - | 未支付成功的回调函数 |

### 返回值

-

### 示例

```js

wxPay({
    appId: '',
    timeStamp: '',
    nonceStr: '',
    package: '',
    signType: 'MD5',
	paySign: ''
}, function() {
    alert('支付成功')
}, function() {
    alert('支付未成功')
})

```

## downloader(path)

下载方法

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
path | String | - | 文件存放路径，应确保能在浏览器中打开 | *

### 返回值

`Boolean` 下载方法调用成功则返回true

### 示例

```js

downloader('http://121.28.5.194:10001/js/dist/zhby-app.js')

```

## imgToBase64(url, callback, outputFormat)

将路径内的文件转换成base64编码

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
url | String | - | 文件路径，确保浏览器内能打开，并保证同源策略，不能跨域 | *
callback | Function | - | 成功后的回调函数，结果会议参数形式传入回调函数 | *
outputFormat | String | 'image/png' | 图片编码类型 | *

### 返回值

-

### 示例

```js

imgToBase64('http://test.hgchzj.com:12000/images/logo.png', function(res) {
    console.log(res)
});

===> data:image/png;base64,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

```

## inheritPrototype(subType, superType)

继承原型链

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
subType | Object | - | 子类 | *
superType | Object | - | 父类 | *

### 返回值

-

### 示例

```js

var num = {};
inheritPrototype(num, Number);

```

## loadScript(src)

异步加载js文件

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
src | String | - | js文件路径，确保能够在浏览器中打开 | *

### 返回值

`Boolean` 成功加载则返回true

### 示例

```js

loadScript('http://121.28.5.194:10001/js/dist/zhby-app.js')

```

## Arabia_to_Chinese(n)

将数字金额转换为中文大写金额

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
n | Number | - | 带转换的金额 | *

### 返回值

`String` 转换完成的大写金额

### 示例

```js

Arabia_to_Chinese(1.25) ===> "壹元贰角伍分"

```

## mixin(obj, target, state)

混合对象

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
obj | Object | - | 待混入的对象 | *
target | Object | - | 混入的目标对象 | *
state | Boolean | false | 是否覆盖混入 |

### 返回值

`Object` 混合完毕的对象

### 示例

```js

var a = {
    name: 'yang',
    age: 23
}, b = {
    age: 18
};
var c = clone(b);

mixin(a, b) ===> {age: 18, name: "yang"}

mixin(a, c, true) ===> {age: 23, name: "yang"}

```
