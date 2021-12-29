# 搭建和用法

## 下载

Floodgate 2.0: [https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/)\
Geyser: [https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/](https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/)

## 准备

* 你必须拥有一个服务器或者拥有一个服务器的管理权限才能使用 **Floodgate**。_如果你不是该服务器的服主或者管理者，那么 **Floodgate** 对你来说是没用的，因为它不会帮助你尝试绕过 **Java版服务器** 的正版验证。_
* 你必须使用 **Geyser** 的 [插件版](../user-guide/da-jian/#ge-cha-jian-ban-de-da-jian) 或者 [独立版](../user-guide/da-jian/#du-li-ban-de-da-jian)。**Floodgate** 无法取代 **Geyser** 的功能。
* 你必须保证你正在使用最新版本的 **Geyser**。（旧版本的 **Geyser** 只和 **Floodgate 1.0** 适配而不支持 **Floodgate 2.0**）
* `floodgate-spigot.jar` 不能安装到 **CraftBukkit/Bukkit** 服务器上。

## 搭建

_以下提及有关 Spigot 的内容，在类似 Paper 的基于 Spigot 的fork上也通用。_

对于 **BungeeCord/Velocity**: 你只需要将 **Floodgate** 安装到 **BungeeCord 或者 Velocity** 代理端上，除非你想在子服使用 **Floodgate API** - 具体操作请查看下面的安装步骤\
&#x20;      _注意:_ 在子服安装 **Floodgate** 将允许基岩版玩家可以直接显示他们的皮肤。

* 在 [这里下载](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/) Floodgate 插件并放置到你的服务器的 plugins 文件夹。
  * `floodgate-spigot.jar` 适配 Spigot, Paper 等等
  * `floodgate-bungee.jar` 适配 BungeeCord, Waterfall 等等
  * `floodgate-velocity.jar` 适配 Velocity
* 将 **Geyser** 配置内的 `auth-type` 选项设置为 `floodgate`。
* 重启你的服务器。

**你只需在使用独立版上进行此步骤：**

* _复制_ **Floodgate** 配置所在的目录下的 `key.pem` 文件到 **Geyser独立版** 的文件夹内。**不要尝试将这个文件分享给其他人！**这个密钥文件允许基岩版账号绕过 Java 版身份验证，如果有人拿到了它，他们可能会对您的服务器造成严重破坏。

#### 在 BungeeCord 或者 Velocity 代理端下的每个子服也安装 Floodgate

这只在你想要使用 **Floodgate API** 时需要进行此步骤：

* 在你的 **代理端和** _**所有子服**_ 都安装 Floodgate，相关教程请见上
* 如果你使用 BungeeCord，启用你的 BungeeCord 的 `config.yml` 内的 `ip_forward` 选项
* 将 `spigot.yml` 配置内的  `bungeecord` 选项为 `true`&#x20;
* 开启你的代理服务端
* 编辑代理服内的 **Floodgate** 配置内的 `send-floodgate-data` 选项为 `true`.
* _Copy_ the `key.pem` file in the proxy Floodgate config folder to all Spi_复制_ **Floodgate** 配置所在的目录下的 `key.pem` 文件到 **Geyser独立版** 的文件夹内。**不要尝试将这个文件分享给其他人！**这个密钥文件允许基岩版账号绕过 Java 版身份验证，如果有人拿到了它，他们可能会对您的服务器造成严重破坏。
* 重启子服代理服

## 修改/关闭基岩版玩家前缀

_**请注意: 除非您能保证您的玩家没有一个 Java 和 基岩 玩家同名，否则我们不建议您移除基岩版玩家前缀。Floodgate 给玩家生成 UUID 的规则和Java 版本身不同，即使玩家名称相同，但他们的 UUID 依然不同。因此，重复的玩家名称会导致奇怪的情况，例如你永远无法传送到其中一名玩家。**_

在你的 **Floodgate** 配置中，将 `username-prefix` 设置为你需要的前缀 - 你可以设置为 `""` 以关闭基岩版前缀功能。

在一些旧版本的 Paper 服务器（或者 Paper 的一些分支），你或许需要关闭你的服务器并删除你的 **服务端 jar** 文件同目录下的的`usercache.json` 文件以避免出现你的老的 **Floodgate** 玩家的前缀没有更新的问题。

## 获取 Floodgate 玩家的 UUID

你可以检查服务器日志或者 [这个](https://floodgate-uuid.heathmitchell1.repl.co) 页面以获取。如果这两个办法没用，试试下面这个方法：&#x20;

首先，您需要获取基岩玩家的 **XUID**。 有几个第三方网站可以找到这个，例如 [这个](https://cxkes.me/xbox/xuid)（与 Geyser 无关）。确保选择“十六进制”。 您需要输入玩家的 **Xbox** 名，并且一旦提交，它应该以 **xxxxxxxxxxxxxxxx** 的格式显示 **XUID**。 要把XUID变成Java版可以识别的UUID，需要把XUID写成这样的格式：**00000000-0000-0000-xxxx-xxxxxxxxxxxx**。如果格式正确，**Java** 版应该可以接受它作为 **UUID**。

## 使用 PlaceholderAPI

如果你使用 Floodgate 的 Bukkit 版本，在 [这里 ](https://github.com/rtm516/FloodgatePlaceholders/)下载 **PlaceholderAPI** 插件。 你只需安装好 [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) 插件即可使用 Floodgate 的变量符，无需其他操作。如果你想在 BungeeCord 使用，那么你需要将 Floodgate 安装到所有子服上，具体步骤见上。

## 使用 Skript

如果你使用 Floodgate 的 Bukkit 版本，这里有一个非官方支持的 Skript 脚本支持 [在这里](https://github.com/Camotoy/floodgate-skript)。
