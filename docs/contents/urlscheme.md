# URL Scheme

## 下载配置

CFW 支持使用 URL Scheme 快速导入配置文件：

```
clash://install-config?url=<encoded URI>
```

### 响应头

#### content-disposition

如果响应头中存在`content-disposition`字段，则使用`filename`对应的值作为配置文件名（例如)，否则使用 URL 最后一部分作为配置文件名

```
content-disposition: attachment; filename="abc.yaml"
```

#### profile-update-interval

如果响应头中存在`profile-update-interval`字段，则配置文件自动更新间隔设置为对应的值，以小时为单位

```
profile-update-interval: 12
```

#### subscription-userinfo

如果响应头中存在`subscription-userinfo`字段，则其对应的流量及到期信息会显示在 Profiles 模块中，[规范参考此处](https://github.com/crossutility/Quantumult/blob/master/extra-subscription-feature.md)

```
subscription-userinfo: upload=455727941; download=6174315083; total=1073741824000; expire=1671815872.8
```

## 退出软件

```
clash://quit
```
