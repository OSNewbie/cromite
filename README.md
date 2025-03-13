<a href="https://github.com/uazo/cromite/releases/latest">
  <img src="https://img.shields.io/github/v/release/uazo/cromite" alt="current Cromite release" title="current Cromite release" />
</a>
<br>

[![Build Cromite](https://github.com/uazo/cromite/actions/workflows/build_cromite.yaml/badge.svg)](https://github.com/uazo/cromite/actions/workflows/build_cromite.yaml)

# Cromite (一个Bromite的分支) - 夺回你的浏览器

<a href="https://www.cromite.org">
  <img title="Cromite - take back your browser!" src="https://www.cromite.org/app_icon.png" width="96" alt="Bromite" />
</a>
<br>

Cromite是一个 [Chromium](https://www.chromium.org/Home) 基于的分支 [Bromite](https://github.com/bromite/bromite) 内置支持广告拦截，并关注隐私。

Cromite适用于Android arm64-v8a、arm32-v7a和x86_64，Oreo及以上版本（最低v8.0，API级别26），Windows和Linux 64位。
# Goals
Cromite的目标是：
- 限制浏览器内置的可用于跟踪用户习惯的平台功能，如果技术上不可行，则禁用这些功能，并由用户选择是否重新启用它们。
- 限制浏览器与其制造商之间的紧密集成。
- 不让csagan5在Bromite上所做的优秀研究工作被遗忘。

此外，Cromite希望促进与其他非营利、开源浏览器的更大集成，鼓励与他人的更紧密合作，并尝试在它们达到适当的成熟度后直接将其集成到Chromium中。

# 隐私限制

Cromite的隐私功能，包括反指纹缓解（并不全面）， **不应被视为对记者和生活在自由受限国家的人们有用。**, 请查看 [Tor Browser](https://www.torproject.org/download/) 在这种情况下（最好使用桌面版本）。
请注意，该项目并非没有错误，改变浏览器的行为可能是有风险的，并且并非没有问题。

# 文档
- [隐私政策](https://github.com/uazo/cromite/blob/master/docs/PRIVACY_POLICY.md)
- [功能](https://github.com/uazo/cromite/blob/master/docs/FEATURES.md)
- [常见问题](https://github.com/uazo/cromite/blob/master/docs/FAQ.md)
- [如何构建](https://github.com/uazo/cromite/blob/master/docs/HOW_TO_BUILD.md)
- [补丁列表](https://github.com/uazo/cromite/blob/master/docs/PATCHES.md)

# 发布

所有构建版本可作为 [releases](https://github.com/uazo/cromite/releases).

Cromite目前为ARM、ARM64、Android x86、Windows x64和Linux构建。

每个发布将包含以下文件：

#### Android的Cromite apk:
- [arm64_ChromePublic.apk](https://github.com/uazo/cromite/releases/latest/download/arm64_ChromePublic.apk)
- [arm_ChromePublic.apk](https://github.com/uazo/cromite/releases/latest/download/arm_ChromePublic.apk)
- [x64_ChromePublic.apk](https://github.com/uazo/cromite/releases/latest/download/x64_ChromePublic.apk)

#### Linux包:
- [chrome-lin64.tar.gz](https://github.com/uazo/cromite/releases/latest/download/chrome-lin64.tar.gz)

#### Windows 安装包:
- [chrome-win.zip](https://github.com/uazo/cromite/releases/latest/download/chrome-win.zip)

#### 用于Java堆栈跟踪去混淆的调试符号和proguard文件
- x64_ChromePublic.apk.mapping
- arm64_ChromePublic.apk.mapping
- arm64_symbols.zip

#### 构建时间分析文件：
- arm64_ninja_log_trace.html

#### Chrlauncher自动更新文件：
- updateurl.txt

还提供其他文件：请注意，这些文件是由一个[附加构建](https://github.com/uazo/cromite/actions/workflows/build_additional_targets.yaml) 与发布过程分开创建的，因此可能不会立即可用。

#### Android的Cromite系统WebView apk：
- arm64_SystemWebView.apk
- x64_SystemWebView.apk

#### Android的Vanilla Chromium（用于测试）：
- arm64_VanillaChromium.apk
- arm_VanillaChromium.apk
- x64_VanillaChromium.apk

#### SystemWebView Shell（用于测试）
- arm64_SystemWebViewShell.apk
- x64_SystemWebViewShell.apk

### F-droid

Official F-droid repo url:
https://www.cromite.org/fdroid/repo/?fingerprint=49F37E74DEE483DCA2B991334FB5A0200787430D0B5F9A783DD5F13695E9517B

### Android中的自动更新
您将通过自动更新功能自动收到有关新更新的通知（并能够安装它们）。在第一次启动时，系统会询问您是否要激活该功能。


### Windows的自动更新设置

1. 下载 https://github.com/henrypp/chrlauncher/releases
2. 创建一个 `chrlauncher.ini`

```
[chrlauncher]

# 自定义Chromium更新URL（字符串）：
ChromiumUpdateUrl=https://github.com/uazo/cromite/releases/latest/download/updateurl.txt

# Chromium 的命令行（字符串）：
# 注意 --user-data-dir= 使用绝对路径效果更好
# 参见这里：http://peter.sh/experiments/chromium-command-line-switches/
ChromiumCommandLine=--user-data-dir="C:\Users\<my user>\AppData\Local\Cromite\User Data" --no-default-browser-check
k

# 在 c:\temp\log.txt 中启用完整日志记录（每日轮换，无自动删除）
# ChromiumCommandLine=--enable-logging --v=0 --log-file=C:\temp\log.txt --user-data-dir=".\User Data" --no-default-browser-check

# Chromium 可执行文件名（字符串）：
ChromiumBinary=chrome.exe

# Chromium 二进制文件目录（字符串）：
# 相对路径（相对于 chrlauncher 目录）或完整路径（支持环境变量）。
ChromiumDirectory=.\bin

```
为了防止每次浏览器更新时被 Microsoft Defender 删除，请通过相应地修改 `user-data-dir` 文件夹进行检查。

### 在 Windows 中启用网络进程沙箱

我不包括任何设置，因为我不喜欢不知道它们的作用的体验，因此您必须在首次安装时手动运行此命令：
```
cd <where_is_the_exe>
icacls . /grant "*S-1-15-2-2:(OI)(CI)(RX)"
```
请参阅 https://github.com/uazo/bromite-buildtools/issues/51

### 在 Windows 中启用渲染进程的 AppContainer  
您可以通过命令行激活（强烈推荐）'RendererAppContainer' 标志，使用：
```
  --enable-features=RendererAppContainer
```

### Linux 的自动更新设置  
正在进行中，详细信息请参见 https://github.com/uazo/cromite/issues/771

### 在 Ubuntu 24.04 及其衍生版（如 Kubuntu 等）中使 Cromite 工作  
这发生的原因是，从 Ubuntu 24.04 开始，AppArmor 限制了对非特权用户命名空间的使用。要解决此问题，您有几个选项：
#### 1. 为 Cromite 创建一个 AppArmor 配置文件  
创建 `/etc/apparmor.d/chrome`，并写入：
```
abi <abi/4.0>,
```
include <tunables/global>

profile cromite /home/user/cromite/chrome-lin/chrome flags=(unconfined) {
  userns,

  include if exists <local/chrome>
}
```
将 Cromite 二进制文件路径替换为您放置 Cromite 的位置。

现在，运行 `sudo apparmor_parser -r /etc/apparmor.d/cromite` 以应用更改。

#### 2. 在下次重启之前禁用限制
`sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0`

#### 3. 永久禁用限制
将 `kernel.apparmor_restrict_unprivileged_userns=0` 添加到文件 `/etc/sysctl.d/60-apparmor-namespace.conf` 中。如果文件不存在，请创建它。

# 贡献

请按照问题模板提交问题；请注意，GitHub 在移动设备上不显示模板。

欢迎并接受与项目目标相符的补丁。

如果您想帮助我，[这里](https://github.com/uazo/cromite/blob/master/docs/HELP_ME_PLEASE.md) 是我需要的事项列表。

有关任何使用或开发讨论，请使用 GitHub 讨论区：https://github.com/uazo/cromite/discussions

# 致谢

* [Chromium 项目](https://www.chromium.org/Home) 和开发者
* [Bromite](https://github.com/bromite/bromite)
  * [Iridium 项目](https://github.com/iridium-browser) 提供的一些补丁
  * [ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium) 提供的一些补丁
  * [ungoogled-chromium-android](https://github.com/ungoogled-software/ungoogled-chromium-android) 提供的一些补丁
  * [GrapheneOS](https://github.com/GrapheneOS) 提供的一些安全补丁
  * [Inox 补丁集](https://github.com/gcarq/inox-patchset) 提供的一些补丁（通过 ungoogled-chromium）
  * [Brave 浏览器](https://github.com/brave/brave-core) 提供的一些补丁

感谢 [austinhuang0131](https://github.com/austinhuang0131) 提供的 SVG 图标。
# 捐赠

如果您愿意，可以通过 [paypal](https://www.paypal.com/pools/c/9cwNgAQhRL) 捐赠以支持 Cromite 的开发。

# 许可证

Cromite 以 [GNU GPL v3](./LICENSE) 许可证发布。  
作为 Bromite 项目一部分发布的补丁仅在 GNU GPL v3 许可证下发布。  
Cromite 特定的补丁则在 GNU GPL-2+ 许可证下发布。  
每个单独的补丁包含有关所使用许可证的具体信息。
