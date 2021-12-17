# 常见问题

[[toc]]

### Service Mode 无法安装

<question-answer>

#### Windows

先确定系统安装了`.NET framework runtime`

然后尝试手动安装：

1. 点击 General 中的 Home Directory 打开文件夹，进入 service 子目录中
2. 打开 CMD，执行以下命令：

```
service.exe install
service.exe start
```

如安装出现错误，参考[这个 issue](https://github.com/Fndroid/clash_for_windows_pkg/issues/1627)

#### macOS

1. 打开终端
2. 运行以下命令：
   ```sh
   curl https://gist.githubusercontent.com/Fndroid/2119fcb5ccb5a543a8f6a609418ae43f/raw/ff63615309a9b3f3e1d682fc29bc73284816422e/mac.sh > cfw-tun.sh && chmod +x cfw-tun.sh && sudo ./cfw-tun.sh install && rm cfw-tun.sh
   ```
   如要卸载则将 install 改为 uninstall

#### linux

1. 打开终端
2. 运行以下命令：

   ```sh
   curl https://gist.githubusercontent.com/Fndroid/2119fcb5ccb5a543a8f6a609418ae43f/raw/592eba4f480c7ccb4f29c9b8e80d24bfd5dda8cf/linux.sh > cfw-tun.sh && chmod +x cfw-tun.sh && sudo ./cfw-tun.sh install <cfw安装目录>
   ```

   如要卸载则将 install 改为 uninstall，最后一部分位 CFW 安装目录

</question-answer>

### macOS 版本启动要求授权

<question-answer >

在第一次或更新 APP 后打开软件会提示用户授权，这是因为需要安装/更新用于设置系统代理的工具，如果不进行授权，General 中的 System Proxy 开关将无法打开。一般情况下，除非工具更新，否则除了第一次启动外不会重复需要授权。

</question-answer>

### macOS DMG 安装后无法打开，提示损坏

<question-answer>

网络下载应用被 Apple 添加隔离标识，终端输入命令解除即可：

```
sudo xattr -r -d com.apple.quarantine /Applications/Clash\ for\ Windows.app
```

</question-answer>

### 系统代理自动关闭或打开

<question-answer>

[参考](https://github.com/Fndroid/clash_for_windows_pkg/issues/312)

</question-answer>

### General 端口显示为 0

<question-answer>

[参考](https://github.com/Fndroid/clash_for_windows_pkg/issues/671)

</question-answer>

### Killer 系列网卡无法开启 TAP/TUN 模式

<question-answer>

[参考](https://github.com/Fndroid/clash_for_windows_pkg/issues/1243#issuecomment-751165537)

</question-answer>

### 在 Windows 系统中，使用 system 作为 TUN stack 时，Clash 网卡无法正常工作

<question-answer>

当前版本下，使用`system`作为 TUN stack 时，需要在系统防火墙中将 Clash core 放行。[参考](https://github.com/Fndroid/clash_for_windows_pkg/issues/1936#issuecomment-853226838)

</question-answer>

### 在 Windows 系统中，TUN 模式下无法使用热点分享功能

<question-answer>

1. 开启热点分享功能，此时系统网络设置中会生成一个网卡
2. 开启 TUN 模式
3. 进入系统网络设置，在 Clash 网卡右键选择属性，选择共享标签页
4. 勾选“允许其他网络用户通过此计算机的 Internet 连接来连接”
5. 在“家庭网络连接”选择框中选择第 1 步生成的网卡

</question-answer>

### 软件启动时，TUN 创建网卡失败，提示 Start Tun interface error: error creating interface: Cannot create a file when that file already exists.（Windows）

<question-answer>

临时解决方法：

1. 进入 Home Directory
2. 编辑 config.yaml，添加如下配置：
   ```yaml
   port: 7890
   # ...
   # 添加下面这段👇
   tun:
     enable: true
     stack: gvisor
     auto-route: false
     auto-detect-interface: false
   ```
3. 重启 CFW

</question-answer>
