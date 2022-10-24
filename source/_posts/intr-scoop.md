---
title: scoop，一条命令安装windows软件
date: 2022-07-28 08:48:22
tags: [windows软件,实用工具]
cover: https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0e266d1ebdb744f88e852fa07355bc3c~tplv-k3u1fbpfcp-no-mark:480:480:0:0.awebp?
---
下载软件带了病毒？环境变量没配好？软件缺少相关依赖导致无法运行？那就试试scoop吧，一条命令搞定你所有问题！

<!-- more -->

- 你是否在为无法找到合适的软件资源苦恼着？（高速下载、\*\*之家，XX安装器）
- 你是否在为环境变量的配置抓狂着？（JAVA_HOME，NGINX_HOME）
- 你是否羡慕着linux，mac上一行命令直接安装软件？（apt-get,brew）
- 你是否需要经常切换软件的版本？（JAVA8，JAVA11 Python2，Python3）
- 你是否被某些软件的依赖搞到抓狂？（tomcat-JRE）

那适合你的工具来了！
那就是：<br>
    
<p align=center><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5d3c8a474179462b849d99cef2448be3~tplv-k3u1fbpfcp-watermark.image?"/></p>

**<p align=center> Scoop </p>**

想安装Python？一条：

```
scoop install python
```
想查找不同版本的JAVA安装？先搜索：

```
scoop search jdk
```
得到：

```
'java' bucket:
    ...太多了不放出来了
    openjdk (18.0.1.1-2)
    openjdk10 (10.0.2-13)
    openjdk11 (11.0.2-9)
    openjdk12 (12.0.2-10)
    openjdk13 (13.0.2-8)
    openjdk14 (14.0.2-12)
    openjdk15 (15.0.2-7)
    openjdk16 (16.0.2-7)
    openjdk17 (17.0.2-8)
    openjdk18 (18.0.1.1-2)
    openjdk19 (19-28-ea)
    ...
```
选择JAVA18进行安装:

```
scoop install openjdk18
```
安装完成后直接运行，环境变量也帮你配好了：
```
java -version
```
```
java version "18.0.1.1" 2022-04-22
Java(TM) SE Runtime Environment (build 18.0.1.1+2-6)
Java HotSpot(TM) 64-Bit Server VM (build 18.0.1.1+2-6, mixed mode, sharing)
```

那么，开始吧：
# 系统要求
- Windows 7 SP1+ / Windows Server 2008+
- PowerShell 3（或更高版本）和 .NET Framework 4.5+
- 启用PowerShell，并且`executionpolicy`可以设置成`remotesigned`(参考之后的步骤)

确保已安装 PowerShell 3 或更高版本。 如果使用的是 Windows 10 或 Windows Server 2012 就可以直接用，但 Windows 7 和 Windows Server 2008 估计需要去升级PowerShell，powerShell的官方下载地址：
https://docs.microsoft.com/en-us/powershell/scripting/windows-powershell/install/installing-windows-powershell?view=powershell-7.2#upgrading-existing-windows-powershell

可以使用以下命令检查powershell版本：
```
$psversiontable.psversion.major
```
如果返回的数字大于3，就再次输入这个命令（否则先通过上面的链接升级）：
```
set-executionpolicy remotesigned -scope currentuser
```
# 安装
## 设置安装位置（可跳过）
scoop默认是安装在`C:\Users\[你的账户名]\scoop`下的，如果不想安装在这里，要首先指定安装目录（下面的例子安装在`D:\Applications\Scoop`）：

```
[environment]::setEnvironmentVariable('SCOOP', 'D:\Applications\Scoop', 'User')
$env:SCOOP='D:\Applications\Scoop'
```
## 安装scoop
继续在Powershell中输入：
```
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```
等待命令执行完毕，就安装成功了
## 设置全局软件安装位置（可跳过）
软件安装时可以加入一个global参数，安装在全局位置，否则就会安装到用户目录下，这个全局安装位置默认在`C:\GlobalScoopApps`下，可以通过如下命令进行修改（下面的例子中安装在`F:\GlobalScoopApps`）:
```
[environment]::setEnvironmentVariable('SCOOP_GLOBAL','F:\GlobalScoopApps','Machine')
$env:SCOOP_GLOBAL='F:\GlobalScoopApps'
```
# 使用Scoop
## 常用命令
输入`scoop help`可以查看所有scoop命令
```
alias       Manage scoop aliases
bucket      Manage Scoop buckets
cache       Show or clear the download cache
cat         Show content of specified manifest. If available, `bat` will be used to pretty-print the JSON.
checkup     Check for potential problems
cleanup     Cleanup apps by removing old versions
config      Get or set configuration values
create      Create a custom app manifest
depends     List dependencies for an app
download    Download apps in the cache folder and verify hashes
export      Exports (an importable) list of installed apps
help        Show help for a command
hold        Hold an app to disable updates
home        Opens the app homepage
info        Display information about an app
install     Install apps
list        List installed apps
prefix      Returns the path to the specified app
reset       Reset an app to resolve conflicts
search      Search available apps
shim        Manipulate Scoop shims
status      Show status and check for new app versions
unhold      Unhold an app to enable updates
uninstall   Uninstall an app
update      Update apps, or Scoop itself
virustotal  Look for app’s hash or url on virustotal.com
which       Locate a shim/executable (similar to ‘which’ on Linux)
```
其中比较常用的是：

| 命令 | 描述 | 示例 |
| --- | --- | --- |
| install | 安装指定名称的软件 | scoop install tomcat |
| uninstall | 卸载指定名称的软件 | scoop uninstall mongodb |
| update | 更新指定名称的软件 | scoop update vscode |
| search | 搜索包含指定名称的软件 | scoop search jdk |
| list | 列出所有已经安装的软件 | scoop list |
| reset | 将指定版本的软件添加到环境变量 | scoop reset oraclejdk|
| bucket | 软件仓库管理(下文详谈） | scoop bucket add extra |

所以最简单的安装方法就是`scoop intall`了，一个`scoop install vscode`，文本编辑器就安装好了！
## 增加软件仓库
输入`scoop bucket list`命令，可以看到类似这样的返回值：
```powershell
Name   Source                                   Updated            Manifests
----   ------                                   -------            ---------
extras https://github.com/ScoopInstaller/Extras 2022/6/30 17:41:19      1580
java   https://github.com/ScoopInstaller/Java   2022/6/30 17:50:23       224
main   https://github.com/ScoopInstaller/Main   2022/6/30 12:32:29      1053
```
如果你是第一次安装的话，这里应该只会显示一行`name`为`main`的数据，也就是说当前你只有一个默认仓库，有可能并没有收录你需要的软件，因此需要增加新的仓库。<br>
一些官方默认仓库可以直接使用仓库名称，比如：
```
scoop bucket add extras #强烈推荐使用这个仓库，扩充了大量软件
```
而其他的第三方仓库则需要设定别名之后填写地址：
```
scoop bucket add dorado https://github.com/chawyehsu/dorado
```
scoop官网推荐了如下的软件仓库：
仓库名 (30)                                                                              | 描述+我的吐槽                                                                                                                                                      | Star数 |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| [extras ](https://github.com/ScoopInstaller/Extras)                                      | 📦 Scoop官方的补充仓库.                                                                                                                                  | 1345  |
| [main ](https://github.com/ScoopInstaller/Main)                                          | 📦 Scoop官方的默认仓库.                                                                                                                                 | 977   |
| [chawyehsu/dorado ](https://github.com/chawyehsu/dorado)                                 | 🐟 也是另一个Scoop的补充仓库                                                                                                                           | 698   |
| [nerd-fonts ](https://github.com/matthewjberger/scoop-nerd-fonts)                        |  nerd字体仓库                                                                                                                         | 225   |
| [java ](https://github.com/ScoopInstaller/Java)                                          | 📦 Scoop的Java仓库，包括以下厂商的版本：Oracle Java, OpenJDK, Eclipse Temurin, IBM Semeru, Zulu, ojdkbuild, Amazon Corretto, BellSoft Liberica, SapMachine 和 Microsoft JDK. | 163   |
| [TheRandomLabs/Scoop-Spotify ](https://github.com/TheRandomLabs/Scoop-Spotify)           | Spotify, Spicetify及其相关软件的仓库                                                                                                      | 156   |
| [games ](https://github.com/Calinou/scoop-games)                                         | 开源和免费软件及其相关工具的仓库                                                                                               | 147   |
| [kkzzhizhou/scoop-apps ](https://github.com/kkzzhizhou/scoop-apps)                       | 使用Github Action每天自动合并其他scoop仓库的更新，仓库地址：https://github.com/kkzzhizhou/scoop-apps                                                                                  | 146   |
| [ivaquero/scoopet ](https://github.com/ivaquero/scoopet)                                 | 🚀 一个偏向学术研究的仓库.                                                                                                            | 134   |
| [TheRandomLabs/scoop-nonportable ](https://github.com/TheRandomLabs/scoop-nonportable)   | 里面有一些非绿色版的软件                                                                                                                     | 130   |
| [borger/scoop-galaxy-integrations ](https://github.com/borger/scoop-galaxy-integrations) | 游戏平台的仓库，比如Steam、Uplay、战网之类的，甚至还包含一些模拟器（3DS,Wii）以及最终幻想14（为什么只有这么一个游戏啊，我猜作者可能是个狒狒人）                                                                              | 131   |
| [TheCjw/scoop-retools ](https://github.com/TheCjw/scoop-retools)                         | 逆向工程工具仓库                                                                                                                       | 115   |
| [versions ](https://github.com/ScoopInstaller/Versions)                                  | 📦 包含了多个版本软件的仓库（Python2就可以在里面找到）.                                                                                                              | 106   |
| [littleli/scoop-clojure ](https://github.com/littleli/scoop-clojure)                     | 在windows上安装clojure的仓库（查了下这好像是Java的方言？）                                                                                                                            | 73    |
| [kidonng/sushi ](https://github.com/kidonng/sushi)                                       | [已停止维护] 🍣 “一个美味而包容的仓库”（原文就是这么写的……看了下也是个有各种类型软件的丰富仓库，但是可惜作者因为换了mac电脑而没有动力和条件继续维护了……）                                                                                                            | 72    |
| [rasa/scoops ](https://github.com/rasa/scoops)                                           | 📦 “一个包含鲜美软件的Scoop味仓库”（同上……）.                                                                                                                        | 66    |
| [Ash258/GenericBucket ](https://github.com/Ash258/GenericBucket)                         | 已废弃. 用 https://github.com/shovel-org/GenericBucket 替代                                                                                                     | 62    |
| [kkzzhizhou/scoop-zapps ](https://github.com/kkzzhizhou/scoop-zapps)                     | 自用Scoop仓库，使用Github Action自动更新                                                                                                                                    | 49    |
| [MCOfficer/scoop-nirsoft ](https://github.com/MCOfficer/scoop-nirsoft)                   | My 作者自己维护的一些便利小程序，有250多个.                                                                                                 | 45    |
| [KNOXDEV/wsl ](https://github.com/KNOXDEV/wsl)                                           |  WSL（windows的Linux子系统）的仓库，就不需要windows商店了.                                                                               | 35    |
| [cderv/r-bucket ](https://github.com/cderv/r-bucket)                                     | R语言相关的仓库                                                                                                  | 29    |
| [tetradice/scoop-iyokan-jp ](https://github.com/tetradice/scoop-iyokan-jp)               | 日针对日语环境进行了优化的仓库                                                                                                                                         | 30    |
| [TheRandomLabs/Scoop-Bucket ](https://github.com/TheRandomLabs/Scoop-Bucket)             | 一个个人仓库（其实自己维护一个仓库托管在github上很方便，有空做个教程）                                                                                                                                        | 26    |
| [hoilc/scoop-lemon ](https://github.com/hoilc/scoop-lemon)                               | 🍋也是个个人仓库（居然贴心的提供了中国镜像）                                                                                                                   | 26    |
| [Paxxs/Cluttered-bucket ](https://github.com/Paxxs/Cluttered-bucket)                     | 🍺一个（尽量) 绿色干净，带有惊喜的 scoop bucket 软件仓库（Windows 绿色软件收录/优秀软件/独立开发者）                                                                                                 | 26    |
| [Qv2ray/mochi ](https://github.com/Qv2ray/mochi)                                         | 🍡Mochi: 中国用户的美味解决方案（为啥都喜欢用美味来形容啊……）                                                                                                                | 23    |
| [php ](https://github.com/ScoopInstaller/PHP)                                            | 📦 PHP仓库                                                                                                                                          | 21    |
| [zhoujin7/tomato ](https://github.com/zhoujin7/tomato)                                   | 一个个人仓库.                                                                                                                                        | 20    |
| [ZvonimirSun/scoop-iszy ](https://github.com/ZvonimirSun/scoop-iszy)                     | 依然是个个人仓库                                                                                                                                     | 20    |
| [wzv5/ScoopBucket ](https://github.com/wzv5/ScoopBucket)                                 | 又双叒叕是个个人仓库.                                                                                                                                              | 18

**好了，接下来在你的软件海洋中遨游吧！再也不怕下到奇奇怪怪的东西了！**