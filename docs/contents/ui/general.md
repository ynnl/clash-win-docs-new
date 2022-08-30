# 常规 General

![](~@imgs/ui-general.png)

在常规页面下可以清楚了解当前配置文件的设置，譬如常规的 http 和 socks5 代理端口等，方便对某些应用单独进行配置代理。部分含删除线功能说明在新版本后弃用。

## 选项说明

- Port：Mixed(Http+Socks) 代理端口
- ~~Socks Port：Socks5 代理端口~~
- Allow LAN：是否允许局域网代理
- Log Level：Clash 核心日志等级
- IPV6: 是否启用IPV6
- Home Directory：Clash 配置文件目录（不建议修改此目录下文件内容）
- GeoIP Database：GeoIP 数据库更新
- UWP Loopback：UWP 应用联网限制解除工具
- TUN Mode: 是否启用TUN模式
- Service Mode: 虚拟网卡安装(TUN模式)
- TAP Device：虚拟网卡安装(TAP模式)
- ~~General YAML：文本模式编辑基础配置~~
- ~~Theme：切换`亮`/`暗`主题~~
- Mixin: 是否启用Minxin模式
- System Proxy：系统代理开关
- Start with Windows：开机自启动开关

## 点击行为

- Random Mixed Port(循环按钮): 随机设置Mixed端口
- 端口: 设置Mixed端口号
- info(Log Level): 设置日志类型
- Clash Core
  - 盾牌: 添加Allow LAN与System Stack的防火墙规则
  - 内核版本号: 打开Clash内核控制页面
- Connected to Clash core：快速打开 logs 文件夹
- Clash for Windows（标题）：快速重启软件
- v x.x.x: 当显示`new`提示时可以直接点击下载新版安装包 (每隔 6 小时检查一次更新)
- Home Directory：快速打开配置文件目录
- GeoIP Database：点击更新 GeoIP 库
- UWP Loopback：快速打开回环代理限制器
- TAP Device(Manage)：打开TAP模式虚拟网卡控制面板
- Service Mode(Manage): 打开TUN模式虚拟网卡控制面板
- 小齿轮图标: 打开TUN Mode/Mixin的配置文件
- Allow LAN: 显示当前所有网卡IPV4 & IPV6地址

## 悬停行为

- ~~Allow LAN：显示当前所有网卡 IPv4 地址~~
