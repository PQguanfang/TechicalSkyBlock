# 常见异常

通常，人们在使用 **Geyser** 时会遇到无法连接到服务器类似的错误，这个页面帮助你尝试解决这些异常。如果你仍然没有解决，请不妨加入 [我们的 Discord](https://discord.geysermc.org) 以获得支持。

## Floodgate

有关 Floodgate 的帮助，请见: [这里](../../floodgate-wiki/wen-ti.md)。

## 我无法连接到服务器! (服务器在好友选项卡没有显示或者在连接服务器时出现 "无法连接到世界")

* 如果你不使用像 **TCPShield** 的反向代理，请保证你的 `enable-proxy-protocol` 选项是设置为 **false** 的。

### 如果服务器没有在好友选项卡显示

* _如果你使用的是 Windows 10, iOS, 或者 Android_: 尝试以添加服务器形式连接。
* _如果你使用的是 Xbox One_: 尝试使用 [BedrockConnect](https://github.com/GeyserMC/Geyser/wiki/Using-Geyser-with-Consoles) 连接。
* _如果你使用的是 PS4_: [请使用使用一个 LAN 代理](https://github.com/GeyserMC/Geyser/wiki/Using-Geyser-with-Consoles#playstation-4)
* _如果你使用的是 Nintendo Switch_: 目前没有方法可以使用好友选修课连接，但你仍然可以使用 [BedrockConnect](https://github.com/GeyserMC/Geyser/wiki/Using-Geyser-with-Consoles) 以添加服务器形式连接。

_如果 Geyser 服务器就在本地：_尝试将 `localhost` 或者 `0.0.0.0` 作为IP，以添加服务器形式进行连接。_如果这没有效果，或者你的 Geyser 服务器不在同一个电脑，那么请使用：_你 **本地** 的 IPv4 地址。

### [点击这里](xiu-fu-wu-fa-lian-jie-zhi-shi-jie.md) 以修复 "无法连接至世界" 且后台无报错

#### `java.net.BindException: Address already in use: bind` on startup.

这代表 **Geyser** 服务器所开设的端口已被占用，请确保你关闭了所有占用该端口的软件，然后再试。如果这没有起作用，通常重启你的电脑即可解决该问题。

#### \[...] `has been compiled by a more recent version of the Java Runtime (class file version 60.0)`

点击这个链接以了解如何升级到 **Java 16**: [https://paper.readthedocs.io/en/latest/java-update/index.html](https://paper.readthedocs.io/en/latest/java-update/index.html).

#### 您的服务商可能不会及时打开UDP端口

这些步骤仅适用于 Geyser 的独立版本。

这和你的主机端口有关，通常来说，他们没有通过UDP协议来开放端口（对于基岩版来说，服务端会使用UDP协议的端口，而Java端MC所使用的端口是TCP协议）。解决这个问题的一个办法（如果你是腐竹），那就是关服。当机子询问核心文件的时候，选择NK（补充:你当然不一定会选择NK，NK也有分支）。然后，打开你的FTP文件管理器找到Nukkit.jar,然后替换你服务器软件所使用的Nukkit.jar。当开服的时候，它应该会打开使用UDP协议的端口。并且依然允许你使用你所要的服务端核心

**PLEASE NOTE:** If your server automatically redownloads jars upon startup, such as with an autoupdate system, this workaround will not work.如果上述方案没有解决你的问题，那么也没有什么我们能做的了。请联系你的服务器供应商，让他们开放相应的UDP端口。

## 卡在 "正在连接服务器" 且后台没有报错

你或许需要升级你的 Java，如果确实是这样，请访问 [AdoptOpenJDK.net](https://adoptopenjdk.net)。

有时这会发生在网络较差的环境中。 Geyser 配置中有一个 `mtu` 选项； 慢慢降低这个数字（以 100 为基准），每次修改后重新启动，并重新测试加入。

如果您收到“无法连接到世界”而没有提示新的连接的控制台记录，则此选项很可能没有作用。

## 登录失败

_**如果你正在使用一个插件版本：**_ 在你的 Geyser 配置，将你的 bedrock 的 ip 设置为 `127.0.0.1`。 如果这不起作用，请检查您的启动日志以获取有关 Docker 的消息，并在该地址配置中使用远程地址配置。

#### Cannot reply to EncryptionRequestPacket without profile and access token

出现这个消息一般有两个原因:

_Floodgate 问题_:

如果您设置种启用了 Floodgate 可能会出现此消息。 通常，这意味着您的配置是错误的，或与其他插件冲突。 如果您将 Floodgate 密钥从其文件夹复制到同一服务器上的 Geyser 文件夹，那么 Geyser 文件夹内的密钥就不是必要的。您可以安全的删除掉复制到 Geyser 文件夹中的密钥文件，重新启动，然后重试。

_服务器是正版认证模式而你的Geyser设置的是离线模式_:

如果你的配置如上所述，那么简单来说，Geyser自然不会正常运作。 如果你将服务器的认证方式设置为正版认证，那么你的 Geyser 配置也应该是相同的。 正版认证的服务器将会要求您使用 Java正版账户 进行登录认证，如果你再登陆Geyser的时候没有使用正版账户认证那么你将无法加入服务器。如果你的配置没有问题却仍然遇到这个报错，那么有可能是您的登录凭据无效或者是连接正版认证服务器进行认证时超时。

#### Connection Refused: <INSERT IP AND/OR DOMAIN>

连接被拒绝通常意味着请求该端口时无法连接 Java 服务器，或者服务器拒绝访问网络级别的外部连接。 后者可能会发生在类似 TCPShield 等 DDOS 防护插件上，如果您没有类似的 DDOS 防护插件，请确保您尝试连接的服务器连接IP或域名在配置中拼写正确，已启动且端口转发正确。

如果您从旧版本的 Geyser 进行更新，请将您的远程地址设置为`auto`，然后重试。

#### Floodgate Misconfiguration

请查看 [这个页面](https://github.com/GeyserMC/Floodgate/wiki/Issues) 查看更多信息

#### Mojang Resetting Account Credentials

不幸的是，这是我们无法控制的事情，当您在服务器上将 Geyser 作为插件运行或加入远离您所在位置的朋友时，很可能就是这种情况，异地登陆会让Mojang判定您的账户可能被盗号，并因此重置登录凭据。 如果您在本地运行 Geyser，这不应该发生在您身上，但是我们为服务器推荐的是我们制作的插件 [Floodgate](https://github.com/GeyserMC/Floodgate), 它允许基岩客户端在不需要 Java 版帐户的情况下加入您的服务器。  [点击了解这个插件](https://github.com/GeyserMC/Geyser/wiki/Floodgate) 以获得更多帮助。

## "Invalid IP address!" from Bedrock

目前尚不清楚为什么，即使对于有效IP域名也会发生这种情况。 尝试使用 IPv4 地址。

## 基岩版客户端在使用指令时出现卡顿或者崩溃

在你的 Geyser 配置文件中关闭 `command-suggestions` 选项。 关闭这个设置后基岩版玩家将无法进行命令补全，但是可以防止因此造成的游戏卡顿或崩溃。 如果你是服务器的管理员，你可以准备一份命令白名单让玩家使用， 这将会把非必要的命令从TAB补全中移除，对于Java版玩家来说也是一样。他还有其他好处。这是一个可以做到此功能的插件： [CommandWhitelist](https://www.spigotmc.org/resources/commandwhitelist-spigot-waterfall-velocity.81326/)

## BungeeCord 在基岩版玩家加入后卡顿或者崩溃

请确保你的 **BungeeCord** 的 `config.yml` 配置文件中将 `ip-forward` 设置为 `true` 并在你的所有子服的 `spigot.yml` 配置文件中将 `bungeecord` 设置为 `true`。

## Failed to load locale asset cache: Unrecognized token 'Cannot'

这与启动时无法下载区域设置文件相关的任何其他内容通常是由 java 尝试使用 IPv6 连接而 Mojang 仅使用 IPv4 引起的，因此使用在启动命令添加此标识来固定使用ipv4： `-Djava.net.preferIPv4Stack=true`, 就像这样: `java -Xms1024M -Djava.net.preferIPv4Stack=true -jar Geyser.jar`

## Outdated client! Please use 1.x.x

**Java** 版服务器太新，**Geyser** 对它来说有点旧了。请确保你的 **Geyser** 是最新版本，如果是，请耐心等待 **Geyser** 完成更新。

## Outdated server! I'm still on 1.x.x

更新你的 **Java** 版服务器或者使用 [ViaVersion](https://viaversion.com) 插件。 你也可以尝试 [VIAaaS](https://github.com/ViaVersion/VIAaaS)。

## Query: Incorrect Magic!

看这里： [https://www.spigotmc.org/threads/query-incorrect-magic-and-high-cpu-usage.159386/#post-2709057](https://www.spigotmc.org/threads/query-incorrect-magic-and-high-cpu-usage.159386/#post-2709057)

*如果您不使用 TCPShield 等反向代理，请确保将 `enable-proxy-protocol` 设置为 false.

## Only for BungeeCord with floodgate

如果您使用 floodgate，请确保将其安装在所有 Spigot 后端服务器上，如下所示：

1. `Bungee: Geyser 和 Floodgate`
2. `大厅: floodgate`
3. `子服-1: floodgate`
4. `子服-2: floodgate` 
   其他的同理。

* 请保证你的 `key.pem` 和 `config.yml` 在所有的服务器上使用的是相同的配置。

如果您的玩家无法从大厅连接到另一个后端服务器，请检查控制台。

#### Plugins that can cause issues

* `HamsterAPI`
