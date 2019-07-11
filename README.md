# 中惠科技 通用方法类库 zhby-app.js

收录了从 `2018年年初` 开始至今的项目中，使用频率较高的方法

## 快速开始

开发过程中请从 `234服务器` 上进行 `引用` ，项目部署上线后推荐将使用的文件进行 `下载` ，冻结使用的版本号

引用时可以直接引用dist文件夹中的 `最新` 文件，代码默认跟随版本升级

或引用lib中 `某个版本号` 的文件，保证兼容性

```外网引用
<script type="text/javascript" src="http://121.28.5.194:10001/js/dist/zhby-app.js"></script>
```
```内网引用
<script type="text/javascript" src="http://192.168.1.234:10001/js/dist/zhby-app.js"></script>
```

## 历史版本

所有发布过的历史版本都存放在 `/js/lib` 路径下

!> 本类库的版本号未使用Semantic Versioning 2.0.0 语义化版本控制规范

版本号分为4部分： `a.y.m.w`

`a`：代表大版本号，如果a出现更替，说明最新版本与之前的大版本 `不再兼容`，否则为兼容之前版本的修复、维护、升级

`y`：代表年分版本号，每年进行一次更新，2018年为第0版本，向后一次累加

`m`：代表月份版本号

`w`：代表每个月的周目版本号

```外网引用
<script type="text/javascript" src="http://121.28.5.194:10001/js/lib/zhby-app-0.0.0.0.js"></script>
```

```内网引用
<script type="text/javascript" src="http://192.168.1.234:10001/js/lib/zhby-app-0.0.0.0.js"></script>
```
