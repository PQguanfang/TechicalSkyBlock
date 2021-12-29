# 功能

### 白名单指令

**Floodgate 2.0** 有一个白名单指令， `fwhitelist`，这用来将 **Floodgate** 玩家从 `whitelist.json` 文件中添加或移除，也就是添加或者移除他们的白名单。基岩版玩家的前缀不需要填写，你只需要输入他们的正常名字即可。例如： `fwhitelist add Tim203` `fwhitelist remove Tim203`

你也可以通过 UUID 形式使用此指令: `fwhitelist add 00000000-0000-0000-0009-01f64f65c7c3`

这个权限对应的权限节点是 `floodgate.command.whitelist`。

### 什么是 通用 API?

通用 API 是为每个服务器提供的一个 API。它目前包含：[通用连接](gong-neng.md#shen-me-shi-tong-yong-lian-jie)、[皮肤上传](gong-neng.md#shen-me-shi-pi-fu-shang-chuan)，通过游戏标签获得对于 xuid，通过 xuid 获得对应游戏标签。除了某些不可识别来源的数据外，我们不会通过 通用 API 获取您的任何内容。通用 API 的源代码可以 [在这里查看](https://github.com/GeyserMC/global\_api)，通用连接服务器的源代码可以 [在这里查看](https://github.com/GeyserMC/GlobalLinkServer)。

### 什么是 通用连接?

有关连接的指引和介绍，可以在这里查看: [https://link.geysermc.org/](https://link.geysermc.org)

在 通用连接 出现以前，您在访问每个拥有 **Floodgate** 的服务器时，必须一个个的手动将自己的 **基岩版和Java版** 账号进行绑定（这里称为连接）。通用连接就是用来解决这个问题的，您只需在这里绑定一次账号，在加入其他启用 **通用连接** 的使用 **Floodgate** 服务器时，将会自动绑定。\
通用连接也是 [通用 API](https://github.com/GeyserMC/Floodgate/wiki/Features#What-is-the-Global-Api) 的一部分，并且使用 **GlobalLinkServer** 来连接您的账号。要连接您的账号，您必须进行以下操作：

1. 同时使用你的 **Java版客户端和基岩版客户端** 加入 **GlobalLinkServer** \
   (IP: `link.geysermc.org`, Java 端口: `25565`, 基岩版端口: `19132`)
2. 在 Java版 **或者** 基岩版客户端中 输入指令 `/linkaccount` 来开始连接。
3. 你将会获得需要另外一个没有输入上诉指令的一端需要使用的随机代码。
4. 在另外一端输入指令`/linkaccount <随机代码>`。
5. 如果连接成功，你的 **Java版和基岩版** 会被同时踢出服务器。

通用连接在每个使用 Floodgate 2.0 的服务器上默认是开启的，但如果你关闭了它，那么你随时可以通过修改 Floodgate 的配置来重新打开它，这时请确保你的 `player-link` 选项像下面这样:

```
# Configuration for player linking
player-link:
  # Whether to enable the linking system. Turning this off will prevent
  # players from using the linking feature even if they are already linked.
  enabled: true
  # Whether to use global linking. Global linking uses a central server to request link
  # accounts, allowing people to link once, join everywhere (on servers with global linking).
  use-global-linking: true
```

([点击以查看默认配置](https://github.com/GeyserMC/Floodgate/blob/master/common/src/main/resources/config.yml))

一旦你修改并保存了配置，再次重启服务器以后，通用连接应该就能正常工作了。

如果你不想使用通用连接功能，那么你可以关闭 **Floodgate** 配置内的 `enable-global-linking` 选项。

#### 本地连接

你也可也在本地设立连接（绑定）数据库。本地连接和通用连接可以同时工作。如果你的玩家使用了本地连接（绑定），那么本地连接的数据将会在你的服务器上覆盖通用连接的数据。

如果你有代理端 (BungeeCord 或者 Velocity)，那么你只需做以下几个步骤即可：

1. [从这里](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/) 下载其中一个的数据库拓展。如果你已经有了一个 MySQL 数据库或者想要多个服的连接数据同步，那么请选择 `mysql` 。如果是其他情况，请选择 `sqlite`。完整的数据库拓展文件名称应当是 `floodgate-*类型名称*-database.jar`.
2. 将下载好的数据库拓展 _放置到_ Floodgate 2.0 的插件文件夹 (例如 `/plugins/floodgate/`)。
3. 在 Floodgate 配置中启用 `player-link` 下的 `enable-own-linking` 。
4. 在 Floodgate 配置中启用 `player-link` 下的 `type` 改为你的数据库类型 (当前是 `mysql` 或者 `sqlite`)。 (如果你曾经使用过 Floodgate 1.0 并且启用过玩家连接，那么它的数据库类型肯定是 `sqlite`).
5. 重启你的服务器。

如果你选择了 `mysql` ，一个新的数据库信息将会在 Floodgate 下的 data 文件夹生成。您可以在其中输入您的数据库凭据。在你这样做之后，你需要再次重启你的服务器。

如果你做好了，可以通过发送指令 `/linkaccount` 来连接你的两端账号。

### 什么是皮肤上传?

如果你的 **Floodgate 2.0** 被正确安装，那么 **基岩版玩家的皮肤** 对于 **Java版** 玩家来说是可见的。\
如果没有，那么很有可能你的玩家太多，我们需要一个一个帮你的基岩版玩家的皮肤进行上传，然后展示给 **Java版玩家**，这需要一定的时间，过一会就好了。

皮肤上传也是 [通用API](gong-neng.md#shen-me-shi-tong-yong-api) 的一部分。它的职责是将基岩版的皮肤转换成Java版的皮肤，然后上传到 **Mojang** 的服务器，以使得 **Java版** 玩家可以看到 **基岩版** 玩家的皮肤。

我们当前使用 MineSkin 作为皮肤上传的站点。MineSkin 通过由社区捐赠给他们的正版账号来维持运营。所以你如果想支持 MineSkin 并且想让自己服务器的皮肤上传速度再快一点，请不妨 [查看这个页面](https://mineskin.org/account) 以获取更多信息。

![示例皮肤上传](https://camo.githubusercontent.com/7ef276852d8552edfa07a342bfefb6f9ce9a7bffb67c09cef448b65da7dfb915/68747470733a2f2f63646e2e646973636f72646170702e636f6d2f6174746163686d656e74732f3631333136383835303932353634393938312f3831353936393830313736333136303130342f756e6b6e6f776e2e706e67)
