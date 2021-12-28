# Geyser-Farbic

## [点击这里下载](https://ci.opencollab.dev/job/GeyserMC/job/Geyser-Fabric/job/java-1.18/lastSuccessfulBuild/artifact/build/libs/Geyser-Fabric-2.0.0-SNAPSHOT.jar)

就大部分方面而言，Geyser-Farbic和其他平台的版本一致。下面是几个区别：

* Geyser-Fabric 安装在 `mods` 文件夹，它的配置文件应当在你的服务器的根目录下的 `config/Geyser-Fabric/config.yml` 被找到。
* 服务器要求使用任何 **客户端Mod** 都会导致基岩版玩家无法进入服务器。
* Floodgate-Fabric 可以在 [这里](https://github.com/GeyserMC/Floodgate-Fabric) 被找到
* 你必须安装 Fabric API Mod，你可以在 。 下载。

该项目的源代码可以在 [这里查看](https://github.com/GeyserMC/Geyser-Fabric)。

#### permissions.yml

This file located in `config/Geyser-Fabric` controls what commands non-opped players (both Bedrock and Java) are able to run. Uncomment the commands you want any player to run.

#### Why a separate repository?

* By maintaining a separate repository, we can support multiple Minecraft versions easier.
* Fabric is built around the Gradle build tool, while Geyser is built around the Maven build tool.
