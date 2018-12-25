# String对象追加

js原生String对象的拓展方法

## html(encode)

对字符串中的字符进行（反）编码

### 参数

参数名 | 类型 | 默认值 | 含义 | 必填
- | - | - | - | -
encode | Boolean | false | 类型true为转义false为反转义 | *

### 返回值

`String` （反）转义后的的字符串

### 示例

```js

var code = "&#39;&quot;&nbsp;&gt;&lt;&amp;&yen;&lsquo;&rsquo;&hellip;&ldquo;&rdquo;&mdash;";
var decode = code.html();
    ===> "'" ><&¥‘’…“”—"
decode.html(true);
    ===> "&#39;&quot;&nbsp;&gt;&lt;&amp;&yen;&lsquo;&rsquo;&hellip;&ldquo;&rdquo;&mdash;"

```
