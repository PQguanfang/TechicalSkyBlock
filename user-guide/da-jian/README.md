# 搭建

基岩版客户端将通过 **Geyser** 连接到 **Java版服务器**，**Geyser** 的工作就是将两个版本之间的数据包进行转换。截止到目前，有 **6** 个版本的 Geyser 可供使用：**Geyser Spigot版（当然在 Paper 一类的服务端也可以正常使用）、Geyser BungeeCord版（同理，在 Waterfall 一类的服务端也可以正常使用）、Geyser Velocity版、Geyser Sponge版，Geyser Farbic版（不支持客户端Mod，更多信息请见这里=========）和Geyser 独立版**。前面 **5** 个版本以 插件或者Mod 的形式安装到服务端内。而独立版是一个独立的服务端，它需要独立运行。

## 准备

* 你所要连接的 **Java** 版服务器必须支持最新版本 **客户端** (截至目前，是 Minecraft 1.18.1)。这代表服务器本身不一定必须是最新版本，但它必须支持最新版本客户端加入。你可以安装 [ViaVersion](https://www.spigotmc.org/resources/viaversion.19254/) 插件以实现低版本服务端支持高版本客户端，但请注意 **官方只支持1.12.2以上版本的服务端**。
* 你运行 **Geyser** 的设备必须搭载了 **Java 16** 或更高版本。如果你对升级 Java 存有疑惑，请访问 [https://paper.readthedocs.io/en/latest/java-update/index.html](https://paper.readthedocs.io/en/latest/java-update/index.html) 以查看帮助。如果你使用的服务端核心并不支持 **Java 16**，请在 **启动参数** 添加 `-DPaper.ignoreJavaVersion=true` 来使得你的服务端能够正常运行。如果你的服务端核心实在无法在 **Java 16** 上运行，请考虑使用 **独立版**。
* 如果你所要连接的服务器是一个 **正版服务器**，那么你必须拥有一个 **正版Java账号**。如果你是该服务器的服主，那么你可以考虑使用 [Floodgate](https://1686965528.gitbook.io/geyser-wiki/floodgate-wiki/) 以绕过这一要求。
* 你的基岩版客户端必须支持 **Geyser** 当前支持的版本，目前是 **1.17.30 - 1.18.2**。
* 你需要在 **Geyser** 运行的端口上放行 **UDP** 协议，详情见下。

## 各插件版的搭建

1. 从 [构建服务器](https://ci.opencollab.dev/job/Geyser/job/master/) 上下载 **你所需要的对应服务端的插件版**。如果你对此感到疑惑，请查看 [常见问题](https://1686965528.gitbook.io/geyser-wiki/user-guide/chang-jian-wen-ti) 页面。
2. 将下载好的 **Geyser-xxx.jar** 文件放置到服务端的 **plugins** 文件夹，并启动服务端。
3. 在 `config.yml` 修改配置。如果你不懂各个配置文件是干什么的，请 [点击这里](../li-jie-pei-zhi.md) 查看。
4. 如果你修改了配置，你需要 **重启** 你的服务器。
5. 默认情况下，**Geyser** 开启的是端口是 **19132**，这也是 **基岩版添加服务器时的默认端口**。

如果 **Geyser** 和你的基岩版客户端在同一个局域网内，那么你可以通过基岩版客户端中的 **好友** 选项卡加入服务器。

### BungeeCord/Velocity 搭建

如果你正在使用一个 **BungeeCord，Waterfall 或者 Velocity** 代理服务端，那么你只需要将 **Geyser (还有 Floodgate, 如果你需要的话)** 安装到代理服务端上即可，无需在子服上安装。

你可以在各个子服上安装 **Floodgate (但 Geyser 真的没必要)** 来增强玩家的皮肤显示功能和在子服上使用 **Floodgate API**。如果你要这么做，你 _**必须**_ 保证你将代理服务端内 **Floodgate** 文件夹内的 `key.pem` 文件放置到了 **所有子服的 Floodgate 文件夹内的相同位置**，否则，基岩版客户端无法加入服务器。详细的教程，请查看 [Floodgate Wiki](broken-reference)。

基岩版客户端加入你的代理服务端的时，和 **Java** 客户端一样，也是先进入代理服务端，再进入代理服务端下的子服，所以你无需担心任何安全漏洞。

## 独立版的搭建

请务必注意，你只能在你的 **电脑或者云主机上** 使用 **Geyser** 独立版。类似**Termux** 的软件虽然在安卓上也能够运行 Geyser 独立版，但很遗憾的是，你需要保证你的手机有足够的性能，一句话，**后果自负**！ 有关 **Termux** 使用 Geyser 的教程，请 点击 ===========这里查看。

1. 从 [构建服务器](https://ci.opencollab.dev/job/Geyser/job/master/) 上下载 **独立版**。
2. 创建一个专门给 **Geyser** 准备的文件夹，然后把独立版的 **.jar** 文件放置在那。

### 图形化搭建（推荐）

1. 双击 **.jar** 文件，**Geyser** 会生成它运行所需的所有文件。
2. 在 `config.yml` 修改配置。如果你不懂各个配置文件是干什么的，请 [点击这里](../li-jie-pei-zhi.md) 查看。
3. 重启 **Geyser** 独立版本。

### 命令行搭建

1. 像打开一个 Spigot/Paper 服务器一样，创建一个 **.bat 或者 脚本** 文件。如果你不知道如何编写，请 [点击这里](bian-xie-qi-dong-jiao-ben.md) 查看。
2. 运行 **.bat 或者 脚本** 文件，**Geyser** 会生成它运行所需的所有文件。
3. 在 `config.yml` 修改配置。如果你不懂各个配置文件是干什么的，请 [点击这里](../li-jie-pei-zhi.md) 查看。
4. 重启 **Geyser** 独立版本。

### 独立搭建 (Geyser 和 Floodgate 不在同一个主机上)

请见 [这个](broken-reference) 页面查看帮助。

### 端口转发

不像 **Minecraft Java版本**，基岩版的端口默认是 **UDP** 协议的 **19132**。当你设置 **端口转发** 时，必须保证你分配了 **19132 UDP** 或者其他 **UDP** 端口。

### Termux (安卓)

在此之前，请确保你已阅读过 [这里](./#du-li-ban-de-da-jian)。

1. 下载并安装 [Termux](https://termux.com)
2. 运行 `pkg install openjdk-17`
3. 运行 `wget https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/lastSuccessfulBuild/artifact/bootstrap/standalone/target/Geyser.jar`
4. 执行 `java -jar Geyser.jar`

或者

我们有一个用于 **Termux** 的自动安装脚本，可能不适用于所有用户。如果上面的指南不起作用，请尝试此操作。运行此命令以开始下载/安装：

```
curl https://gist.githubusercontent.com/rtm516/e3e07d6595ee41e05a38b03c0f4d7a80/raw/install.sh | bash
```

### NewTerm 2 (iOS)

**注意:** 你需要事先进行越狱。

1. 安装 [Filza File Manager](http://cydia.saurik.com/package/com.tigisoftware.filza/)
2. 安装 [NewTerm 2](https://chariz.com/get/newterm)
3. 下载 [这里](https://github.com/PojavLauncherTeam/PojavLauncher\_iOS/releases/download/v16-openjdk/openjdk-16-jre\_16.0.0+git20201217.8383f41-2\_iphoneos-arm.deb) 的 **jre-16 iOS** 版并通过 Filza 进行安装
4. 下载 [这里](https://cdn.discordapp.com/attachments/558829512633090048/834014323755319306/com.letschill.java\_0.1\_iphoneos-arm.deb) 的 **修改后的 java 指令集** 并通过 Filza 进行安装
5. 打开 NewTerm 2 并运行 `wget https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/lastSuccessfulBuild/artifact/bootstrap/standalone/target/Geyser.jar`
6. 运行 `java -jar Geyser.jar`
7. 你现在可以在基岩版使用 Geyser 了！

**注意:** 由于 iOS 的环境，如果您的设备性能不足，iOS 可能会在您玩游戏时杀死 NewTerm 2 的进程。

你或许遇到了一些错误。如果是的话，运行 `su` 然后输入 root 密码 (默认是 `alpine`) 以获得 root 权限。再跟正常一样开启服务器，你有可能发现正常了。
