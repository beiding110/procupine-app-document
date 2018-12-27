# mainVue类

基于Vue再度封装的类，方便平时（在多页面项目开发中）使用

## 功能说明

* 相比较于原生的Vue，该类直接将 `el` 属性规定为 `#main_con` 因此，不同页面内使用时必须使用 `id="main_con"` 的容器。

* 同时，在使用mainVue类后，会生成一个全局变量 `$vue` ，不但可以方便调试，并且可以从某种程度上 `代替this指针`，不太理解this指针的人可以直接用此变量代替。

* 在mainVue实例化后，还会 `自动初始化` 一些页面内 `常用的变量`，如：`loadingController`（Boolean，加载控制变量）、`dialogVisible`（Boolean，弹框控制变量）、`searchKey`（String，搜索字段变量）、`tableData`（Array，表格列表变量）。

* 除上述功能外，mainVue还会自动将你在element-ui中的表单组件进行部分重写，减少表单验证的配置步骤，如：

```el-form-item预处理

<el-form-item label="label" required mobile></el-form-item>

===>

<el-form-item label="label" :rules="[{required:true,message:'请输入label',trigger:['blur','change']},{ "validator":validatorObj.mobile,"trigger": ["blur", "change"]}]"></el-form-item>

```

!> 在封装 `Vue组件` 时，应使用 `原生Vue` 类，而不应使用本类。

!> 相比原生Vue，由于mainVue是为 `多页面项目` 封装的，所以mainVue的生命周期仅包含 `created` 和 `mounted`，页面切换/关闭时会自动结束生命周期。

## 示例

```js

new mainVue({
	data:{

	},
	computed: {

    },
    methods: {

    },
	mounted:function(){

	}
})

```
