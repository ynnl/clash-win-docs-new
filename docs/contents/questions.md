# 常见问题

[[toc]]

### General 加载失败，显示“failed to clash core, logs are not available.”

<question-answer>

将安装目录添加到杀毒软件白名单。

如 Windows Defender 开启，则需要将安装目录添加到[排除项](https://support.microsoft.com/zh-cn/windows/%E5%B0%86%E6%8E%92%E9%99%A4%E9%A1%B9%E6%B7%BB%E5%8A%A0%E5%88%B0-windows-%E5%AE%89%E5%85%A8%E4%B8%AD%E5%BF%83-811816c0-4dfd-af4a-47e4-c301afe13b26#:~:text=%E4%BE%9D%E6%AC%A1%E8%BD%AC%E5%88%B0%E2%80%9C%E5%BC%80%E5%A7%8B%E2%80%9D%E8%8F%9C%E5%8D%95,%E7%9A%84%E6%89%80%E6%9C%89%E5%AD%90%E6%96%87%E4%BB%B6%E5%A4%B9%E3%80%82)中

</question-answer>

### macOS 无法设置 System Proxy，系统代理项目灰色无法更改

<question-answer>

1. 进入**设置**
2. 选择**安全与隐私**
3. 选择**通用**
4. 点击**解锁按钮**，输入密码
5. 点击**高级...**
6. 取消**访问系统范围的偏好设置需要输入管理员密码**选项

</question-answer>

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

请在系统防火墙中将 clash core 放行。方法参考 [TUN 模式说明](https://docs.cfw.lbyczf.com/contents/tun.html#windows)

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
     auto-detect-interface: true
   ```
3. 重启 CFW

</question-answer>

### 为什么更新到最新版本后 Service Mode 后面的地球变红了？

<question-answer>

在更新到 `v0.20.0` 后， `Service Mode` 的安全性有所提高，因此在从 `v0.19.29` 及以下版本更新到此版本时, `Service Mode` 后面的地球图标可能会显示为红色，请在 Manage 中选择 `Update` 或重新安装 TUN 网卡来消除此问题

</question-answer>
