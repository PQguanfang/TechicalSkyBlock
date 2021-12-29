# 常见问题

### Geyser 是如何工作的？

**Geyser** 像一个翻译官那样工作，将传入和传出的数据包翻译为客户端和服务端（服务器） 都能理解的格式。这样说来，它模拟了 **Minecraft Java版** 客户端，因此服务器实际上认为您是从 **Java版本** 加入的。无论是什么服务器以及它安装了什么插件，您都可以将其与 **Geyser** 连接（只要服务器支持最新的Minecraft版本）。

### 红石是按照哪个版本工作的？

**红石**，还有 **指令、农场** 等各种机制都是按照 **Java版** 工作的。因为你加入的服务器是一个 **Java版** 服务器。

### Geyser 是付费的吗?

不，**Geyser** 和 **它的相关一切作品** 都是 **免费且开源的**，且遵循 **MIT** 协议。

### 哪些插件不兼容 Geyser？

**Geyser** 应当和大部分 **服务端插件** 兼容，但总有例外，例如：

* [TCPShield](https://tcpshield.com) 如果你没有购买付费计划，需要关闭该插件的 `only-allow-proxy-connections` 选项。然而，如果你购买了付费计划，则无需担心，因为他们的付费计划有对 **Geyse**r 添加额外支持。

**Floodgate** 与修改登录流程的插件不兼容。_请务必注意以下各个支持离线登录的插件只是为了 Wiki 编写，Geyser 官方不对离线服务器提供帮助支持。_

* [DynamicBungeeAuth](https://www.spigotmc.org/resources/dynamicbungeeauth-premium-command-semi-premium-system-sessions.27480/) 使得基岩版玩家生成无效的登录请求。
* [FastLogin](https://www.spigotmc.org/resources/fastlogin.14153/) 不让 Floodgate 为基岩版玩家添加前缀。
* [ExploitFixer](https://www.spigotmc.org/resources/2ls-exploitfixer-the-ultimate-antiexploit-plugin.62842/) 认为 Floodgate 玩家使用 恶意UUID - 请关闭该插件的 `uuidspoof` 配置。
* [JPremium](https://www.spigotmc.org/resources/27766/) 改变 Floodgate 玩家的 UUID，导致 Floodgate API 等可能存在异常。
* [LibHatesMods](https://www.spigotmc.org/resources/78202/) 造成玩家无法登录，且报错： `com.github.steveice10.mc.auth.exception.request.InvalidCredentialsException`
* [ProtocolSupport](https://www.spigotmc.org/resources/7201/) 虽然和 Floodgate兼容，但我们推荐使用 [ViaBackwards](https://www.spigotmc.org/resources/viabackwards.27448/)。
* [ProtocolSupportBungee](https://www.spigotmc.org/resources/8733/) 破坏 Floodgate 玩家登录流程，导致 Floodgate API 等可能存在异常。
* [SayNoToMcLeaks](https://www.spigotmc.org/resources/40906/) 使得 Floodgate 玩家无法完成登录。

如果你发现其他不兼容情况，可通过 [Discord](http://discord.geysermc.org) 联系我们。

### 我应该使用哪个版本的 插件版Geyser？

* Geyser-Spigot 支持:
  * [Spigot](https://www.spigotmc.org)
  * [Paper](https://papermc.io/downloads) (推荐)
  * 其他分支
* Geyser-Bungee 支持:
  * [BungeeCord](https://www.spigotmc.org/wiki/bungeecord/)
  * [Waterfall](https://papermc.io/downloads#Waterfall)
  * 其他分支
* Geyser-Velocity 支持 [Velocity](https://www.velocitypowered.com)
* Geyser-Sponge 支持 [SpongeVanilla 或者 SpongeForge](https://www.spongepowered.org)

### Geyser-Spigot 支持什么版本?

支持 **1.12.2** 及更高版本。如果你的服务器比这个版本还低，请使用独立版。

### 如果我使用 BungeeCord，那么 Geyser/Floodgate 应该放置到哪?

你只需要在你的 **BungeeCord** 服务器安装 **Geyser/Floodgate**，这是在你的服务器不使用 **Floodgate API** 的情况下。如果不是这种情况，你还需要在每个子服都正确安装 **Floodgate**。

### 我应该给基岩版玩家什么 IP？

一般来说，如果你没有自己修改过，那么你的基岩版玩家连接你的服务器的IP应该和你的 **Java版玩家** 一样。至于端口，则根据你的 Geyser 配置下的 `bedrock` 下的 `port` 选项来决定。

### 我如何让基岩版玩家加载资源包？

你可以在 **Geyser** 下的 `packs` 文件夹放置资源包。基岩版客户端在加入服务器时会自动下载资源包。目前没有 **Java-基岩 资源包自动转换** 的功能，如果你需要转换资源包格式，请前往 [https://rtm516.github.io/ConvertJavaTextureToBedrock/](https://rtm516.github.io/ConvertJavaTextureToBedrock/) 并把转换好的资源包放置在 **Geyser** 内。

### 基岩版玩家如何副手拿物品？

你可以使用指令 `/geyser offhand`  来进行 **主手和副手** 的切换。你也可以通过修改 Geyser 下的配置 (`emote-offhand-workaround`) 来使得基岩版通过游戏里的 **表情** 按钮来进行 **主手和副手** 的切换。

### 在使用 Floodgate 时，执行指令的玩家变量是什么？

如果基岩版玩家有前缀，所有指令的 **必须** 在名称中 **包含该前缀** 。Floodgate 还将名称中的所有 **空格** 替换为 **下划线** ，因此在执行命令时请务必将所有空格替换为下划线。 如果这不起作用，请在名称周围加上双引号。\
\
示例: /tp ".<基岩版玩家>"。

### 在使用 Floodgate 时，我该如何添加基岩版玩家到白名单内？

您可以通过三种方式执行此操作。 第一种方法是使用 Floodgate 的内置白名单命令，`/fwhitelist add .<基岩版玩家>`。 第二种方法是使用 /whitelist off 关闭白名单，然后让基岩版玩家加入，然后运行 `/whitelist add ".<基岩版>"`，然后使用 `/whitelist on` 打开白名单。 ( 如果将这种方法用于关联到现有的、已列入白名单的 Java 帐户的基岩帐户，则无需将基岩帐户也列入白名单；您可以关联帐户然后立即重新打开白名单 ) 第三种方法是添加基岩玩家的 UUID ( 由 Floodgate 提供 ) 添加到 whitelist.json 文件，然后运行 `/whitelist reload`。

### 当使用 Floodgate 时，如何实现在玩家没有加入服务器的情况下查看他们的 UUID？

请尝试使用 [此页面](https://floodgate-uuid.heathmitchell1.repl.co)，如果这不起作用，请尝试下面这个方法：

首先，您需要获取基岩玩家的 **XUID**。 有几个第三方网站可以找到这个，例如 [这个](https://cxkes.me/xbox/xuid)（与 Geyser 无关）。确保选择“十六进制”。 您需要输入玩家的 **Xbox** 名，并且一旦提交，它应该以 **xxxxxxxxxxxxxxxx** 的格式显示 **XUID**。 要把XUID变成Java版可以识别的UUID，需要把XUID写成这样的格式：**00000000-0000-0000-xxxx-xxxxxxxxxxxx**。如果格式正确，**Java** 版应该可以识别它并作为 **UUID**。

### 在使用 Floodgate 时，我能删除基岩玩家的前缀吗?​&#x20;

虽然您可以删除基岩版玩家前缀，但通常建议 **不要删除** 它，因为这可以防止出现两个版本中 **玩家名称相同** 的情况（例如：基岩版玩家名称：`DJelly4K`，Java 版玩家名称：`DJelly4K`）。由于 **Floodgate** 与 **Java版服务端** 的 **UUID** 生成规则不同，这导致虽然他们具有不同的 **UUID**，但是他们都有相同的游戏名称名，这可能会导致与涉及玩家名称的指令发生 **冲突**。如果尝试删除基岩版玩家前缀只是为了使用指令，请尝试在游戏名称两边添加引号。示例：`/tp ".<基岩版玩家>"`。如果你执意要删除，那么基岩版玩家前缀的配置在 Floodgate 文件夹内的 **config.yml** 文件中的 `username-prefix:` 下，你可以将其修改为 `""` 以删除。

### 要使用 Geyser 就必须安装 Floodgate 吗？

不。当你的服务器是 **正版服务器** 但你不希望基岩版玩家也需要 **Java版正版账号** 登录，那么这时你可以通过安装 **Floodgate** 实现这一愿望。但是如果你是正版服务器且也想要让基岩版玩家必须使用 **Java** 版正版账号或者你是盗版服务器，那么 **Floodgate** 不是强制需要你去安装的。

### 有时，世界跑的很远以后客户端会很卡.

这是 **基岩版** 客户端的问题。具体请 [点击](https://minecraft.fandom.com/zh/wiki/%E5%9F%BA%E5%B2%A9%E7%89%88%E4%B8%AD%E7%9A%84%E8%B7%9D%E7%A6%BB%E7%8E%B0%E8%B1%A1) 这里查看。

### 我可以使用 Geyser 使得 Java 版玩家进入基岩版服务器吗?

不，**Geyser** 只是一个使得 **基岩版玩家加入Java版服务器** 的工具，你是怎么想到反着来也可以的？

### 我可以通过 Geyser 连接一个旧版本的服务器吗？

如果这个服务器安装了 **ViaVersion 或**者通过其他方法支持最新的 **Minecraft** 版本，那么，是的，**你可以**！但是，我们 **不推荐** 这么做！

### 我可以通过 Geyser 连接一个 Mod (Forge/Fabric) 服务器吗？

简单来说，如果你的服务器没有安装任何 **客户端Mod**，那么是可以的。

换句话说，如果你的服务器有 **客户端Mod**，那么 **Geyser** 目前无法翻译 Mod 所新增的 **一切物品、方块等**，因此，也就不受支持了。

### 如何实现自动更新 Geyser？

[Geyser MC Auto Updater](https://github.com/michaelwatne/geysermcupdater) 是一个通过 **命令行** 更新 **Geyser** 的一个不错的方法，但你需要注意这不是 **Geyser官方的项目**。

GeyserUpdater ([GitHub 页面](https://github.com/YHDiamond/GeyserUpdater)/[Spigot 页面](https://www.spigotmc.org/resources/geyserupdater.88555/)) 是一个 Spigot/BungeeCord 插件，通过 **插件** 更新 **Geyser** 也是一个不错的方法。请注意这个插件同样不是 **Geyser官方的项目**，如果你需要支持，请联系他们的 [Discord](https://discord.gg/U5MC2tcCz9)。

### Geyser 支持哪些语言？

我们支持所有 **基岩版** 本身支持的语言。 [点击](https://translate.geysermc.org) 这里以查看我们的 **Crowdin** 页面。下面是所有语言和其对应的代码。我们同时也对基岩版本身不提供支持的语言提供额外支持，你可以在下面查看。 (客户端语言调整请查看 [https://www.curseforge.com/minecraft/mc-addons/translations-for-minecraft](https://www.curseforge.com/minecraft/mc-addons/translations-for-minecraft))

#### 基岩版支持的语言

| 语言名称                         | 代码     |
| ---------------------------- | ------ |
| Bulgarian                    | bg\_bg |
| Czech                        | cs\_cz |
| Danish                       | da\_dk |
| German                       | de\_de |
| Greek                        | el\_gr |
| British English              | en\_gb |
| American English             | en\_us |
| Spanish                      | es\_es |
| Mexican Spanish              | es\_mx |
| Finnish                      | fi\_fi |
| Canadian French              | fr\_ca |
| French                       | fr\_fr |
| Hungarian                    | hu\_hu |
| Indonesian                   | id\_id |
| Italian                      | it\_it |
| Japanese                     | ja\_jp |
| Korean                       | ko\_kr |
| Dutch                        | nl\_nl |
| Norwegian Bokmål             | nb\_no |
| Polish                       | pl\_pl |
| Brazilian Portuguese         | pt\_br |
| Portuguese                   | pt\_pt |
| Russian                      | ru\_ru |
| Slovak                       | sk\_sk |
| Swedish                      | sv\_se |
| Turkish                      | tr\_tr |
| Ukrainian                    | uk\_ua |
| Chinese Simplified (China)   | zh\_cn |
| Chinese Traditional (Taiwan) | zh\_tw |

#### 额外提供支持的语言：

| 语言名称       | 代码     |
| ---------- | ------ |
| Afrikaans  | af\_za |
| Belarusian | be\_by |
| Hebrew     | he\_il |
| Hindi      | hi\_in |

## 和游戏方面无关的问题

### CubeCraft 和 Geyser 是什么关系？

**Redned** 最早在 **2019年7月** 开始 **Geyser** 的开发。在 2020年5月，**CubeCraft** 收购了 Geyser，这意味着他们有时也会参与 **Geyser** 的开发，并赞助 **Geyser** 团队。但他们不拥有 **Geyser** 代码。

### CubeCraft 使用 Geyser 吗？

并不。**CubeCraft** 的双通是自己研发的。
