# 功能

### 白名单指令

**Floodgate 2.0** 有一个白名单指令， `fwhitelist`，这用来将 **Floodgate** 玩家从 `whitelist.json` 文件中添加或移除，也就是添加或者移除他们的白名单。基岩版玩家的前缀不需要填写，你只需要输入他们的正常名字即可。例如： `fwhitelist add Tim203` `fwhitelist remove Tim203`

你也可以通过 UUID 形式使用此指令: `fwhitelist add 00000000-0000-0000-0009-01f64f65c7c3`

这个权限对应的权限节点是 `floodgate.command.whitelist`。

### 什么是 通用 API?

通用 API 是为每个服务器提供的一个 API。它目前包含：[通用连接](gong-neng.md#shen-me-shi-tong-yong-lian-jie)、[皮肤上传](gong-neng.md#shen-me-shi-pi-fu-shang-chuan)，通过游戏标签获得对于 xuid，通过 xuid 获得对应游戏标签。除了某些不可识别来源的数据外，我们不会通过 通用 API 获取您的任何内容。通用 API 的源代码可以 [在这里查看](https://github.com/GeyserMC/global\_api)，通用连接服务器的源代码可以 [在这里查看](https://github.com/GeyserMC/GlobalLinkServer)。

### 什么是 通用连接?

有关连接的指引和介绍，可以在这里查看: [https://link.geysermc.org/](https://link.geysermc.org)

在 通用连接 出现以前，您在访问每个拥有 Floodgate 的服务器时，必须一个个的手动将自己的 基岩版和Java版 账号进行绑定。通用连接就是用来解决这个问题的，您只需在这里绑定一次账号，在加入其他启用 通用连接 的 Floodgate 服务器时，将会自动绑定。\
通用连接也是 [通用 API](https://github.com/GeyserMC/Floodgate/wiki/Features#What-is-the-Global-Api) 的一部分，并且使用 GlobalLinkServer 来连接您的账号。要连接您的账号，您必须进行以下操作：

1. Join the GlobalLinkServer with both your Java and Bedrock account\
   (IP: `link.geysermc.org`, Java port: `25565`, Bedrock port: `19132`)
2. Start the linking process by typing `/linkaccount` on your Java **or** Bedrock account
3. You'll get a message with a random number that you have to enter on the account that you did not start the linking process on.
4. Enter the random number on the other account by typing `/linkaccount <code>`
5. You should get kicked from the server on both your Bedrock and Java account with the message that it had successfully linked your accounts.

Global Linking should be enabled by default on every server running Floodgate 2.0, but in the case that you disabled it, you can enable it again by opening your Floodgate config and make sure that the `player-link` section looks similar to this:

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

([see the default config](https://github.com/GeyserMC/Floodgate/blob/master/common/src/main/resources/config.yml))

Once you saved the config and restarted your server you should be using Global Linking.

If you don't want to use Global Linking, you can disable `enable-global-linking` in the Floodgate config.

#### 本地连接

You can also set up a local linking database on your server. Local linking can work with Global Linking at the same time. Link entries in your local database will override entries in the Global Linking Server.

Note that you only have to follow these steps on your proxy (BungeeCord or Velocity), if you have one.

1. Download one of the linking databases extensions [here](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/). If you need help picking the right one: choose `mysql` if you already have a database or want to have a multi-proxy setup. For anything else choose `sqlite`. The full name should be `floodgate-*type*-database.jar`.
2. Copy the database extension jar you just downloaded _into_ the floodgate 2.0 plugin folder (e.g. `/plugins/floodgate/`).
3. Enable `enable-own-linking` in the `player-link` section of Floodgate.
4. Set `type` in the `player-link` section to your database type (currently either `mysql` or `sqlite`). (If you used Floodgate 1.0 and had linking enabled back then; the database type was `sqlite`).
5. Restart your server

If you have selected `mysql` a new data folder for the database should be generated inside the Floodgate data folder. You can enter your database credentials in there. After you did that restart your server once more.

That should be it. You can then link your accounts by following the instructions you get when typing `/linkaccount`.

### 什么是皮肤上传?

如果你的 **Floodgate 2.0** 被正确安装，那么 **基岩版玩家的皮肤** 对于 **Java版** 玩家来说是可见的。\
如果没有，那么很有可能你的玩家太多，我们需要一个一个帮你的基岩版玩家的皮肤进行上传，然后展示给 **Java版玩家**，这需要一定的时间，过一会就好了。

皮肤上传也是 [通用API](gong-neng.md#shen-me-shi-tong-yong-api) 的一部分。它的职责是将基岩版的皮肤转换成Java版的皮肤，然后上传到 **Mojang** 的服务器，以使得 **Java版** 玩家可以看到 **基岩版** 玩家的皮肤。

我们当前使用 MineSkin 作为皮肤上传的站点。MineSkin 通过由社区捐赠给他们的正版账号来维持运营。所以你如果想支持 MineSkin 并且想让自己服务器的皮肤上传速度再快一点，请不妨 [查看这个页面](https://mineskin.org/account) 以获取更多信息。

![示例皮肤上传](https://camo.githubusercontent.com/7ef276852d8552edfa07a342bfefb6f9ce9a7bffb67c09cef448b65da7dfb915/68747470733a2f2f63646e2e646973636f72646170702e636f6d2f6174746163686d656e74732f3631333136383835303932353634393938312f3831353936393830313736333136303130342f756e6b6e6f776e2e706e67)
