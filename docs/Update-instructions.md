# 版本&更新内容说明

### v1.0.12.4

* mixin函数加入了待混入对象防错机制；

* ajaxResCheck加入的error的中英文对照；

### v1.0.12.3

* Hasher对象中，如果hash值没有改变，则手动调用一次对应值的watch方法；

* formValidateTrans自动表单验证加入require全空格验证；

### v1.0.11.4

* 加入win对象，包含g和r方法，对应location.href和location.replace;

### v1.0.11.3

* Hasher类中gethash方法重写，配适hash地址中带?的情况；

### v1.0.10.5

* ajaxResCheck加入通用抛出code，以“throw-”开头的code将不在js内处理，直接抛出；

### v1.0.10.3

* 调整Hasher类初始化时$data属性赋值及初始化变量监听的位置；

* 修改Hasher类中判断onhashchange是否存在的条件为document.documentMode>=8；

* Hasher类将$path设为关键字;

* hasher类生命周期加入mounted钩子；丰富html方法编码解码的内容；

* 追加getTimeStrmp生成时间戳方法；

* formValidateTrans方法自带类型加入中文映射；

### v1.0.10.2

* 新增ShadeBox遮罩层类；

* ShowMsg加入关闭回调;

* 新增ShowConfirm确认弹框;

### v1.0.9.4

* 新增mixin混入函数；

* getStorage取不到东西时会默认返回false；

* 新增treeBreakArr 树拆数组；

* toSearch加入字段防空；

### v1.0.9.3

* 修改toSearch方法中匹配中文的正则表达式；

* floatToPercent加入最大值为100%的限制；

### v1.0.9.2

* toSearch和getSearch方法加入中文自动转码机制；

* 修改ajaxResCheck的code为‘jumpurl’时的提示框类型；

* 追加Arabia_to_Chinese方法，数字转中文金额；

* 新增get/setStorage基方法供get/setSession/local调用；

### v1.0.9.1

* 修复inheritPrototype的bug;

* inAttr方法回滚；

* toSearch方法深度遍历加入对象是否为null的判断；

* 追加loadScript方法，加入导航栏hash值监听反馈类Hasher，ShowMsgBox关闭了关闭按钮（ie兼容）；

### v1.0.8.5

* ajaxResCheck传入ajax设置相关参数（非必填），修改inAttr判断逻辑

### v1.0.8.4

* 修正了setHash方法，并加入参数为对象时的解析方法，给getSearch，getHash加入了参数为空的，

* 追加get/setLocal、get/setSession方法，

* 将bus中转站移入，

* session加入escape编码，

* getSession函数修正了获取结果为undefined时，返回为'undefined'的错误，

* 追加string的html方法，

* 追加imgToBase64方法，

* 新增inheritPrototype方法

### v1.0.8.3

* 追加了toSearch、getHash、sethash、floatToPercent

### v1.0.8.2
