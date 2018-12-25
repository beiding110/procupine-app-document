# Date对象拓展

对原生Date对象拓展的一些方法

## pattern(fmtstr)

日期格式化

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
fmtstr | String | '' | 希望转换成的格式字符串 | *

### 返回值

`String` 格式化后的日期字符串

### 示例

```js

(new Date()).pattern("yyyy-MM-dd hh:mm:ss.S") ==> 2018-12-25 01:57:03.660
(new Date()).pattern("yyyy-MM-dd E HH:mm:ss") ==> 2018-12-25 二 13:57:26
(new Date()).pattern("yyyy-MM-dd EE hh:mm:ss") ==> 2018-12-25 周二 13:57:26
(new Date()).pattern("yyyy-MM-dd EEE hh:mm:ss") ==> 2018-12-25 星期二 13:57:26
(new Date()).pattern("yyyy-M-d h:m:s.S") ==> 2018-12-25 2:5:44.497

```

## Format(fmtstr)

日期格式化方法

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
fmtstr | String | '' | 希望转换成的格式字符串 | *

### 返回值

`String` 格式化后的日期字符串

### 示例

```js

(new Date()).Format("yyyy-MM-dd HH:mm:ss.S") ===> 2018-12-25 14:08:56.522
(new Date()).Format("yyyy-MM-dd q HH:mm:ss") ===> 2018-12-25 4 14:08:56.522(q为季度)

```
