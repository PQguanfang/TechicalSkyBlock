# Geyser-Farbic

## [点击这里下载](https://ci.opencollab.dev/job/GeyserMC/job/Geyser-Fabric/job/java-1.18/lastSuccessfulBuild/artifact/build/libs/Geyser-Fabric-2.0.0-SNAPSHOT.jar)

就大部分方面而言，Geyser-Farbic和其他平台的版本一致。下面是几个区别：

* Geyser-Fabric 安装在 `mods` 文件夹，它的配置文件应当在你的服务器的根目录下的 `config/Geyser-Fabric/config.yml` 被找到。
* 服务器要求使用任何 **客户端Mod** 都会导致基岩版玩家无法进入服务器。
* Floodgate-Fabric 可以在 [这里](https://github.com/GeyserMC/Floodgate-Fabric) 被找到。
* 你必须安装 Fabric API Mod。

该项目的源代码可以在 [这里查看](https://github.com/GeyserMC/Geyser-Fabric)。

#### permissions.yml

位于 `config/Geyser-Fabric` 目录下的文件控制哪些指令可以被非 OP 玩家使用（基岩版和Java版玩家都是）。您可以将您想要让玩家使用的指令取消注释以使得非OP玩家正常使用。

#### 为什么要单独分开一个源代码库？

* 通过分开源代码库，我们可以更轻松的支持多个 Minecraft 版本。
* **Fabric** 通过 **Gradle** 工具构建，而 **Geyser** 通过 **Maven** 工具构建。
