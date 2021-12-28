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

#### Hosting provider will not immediately open up UDP.

These steps only apply for the standalone version of Geyser.

This usually has something to do on your host's end. Most commonly, it's because they do not open up ports over the UDP protocol, which is what Minecraft: Bedrock Edition uses, opposed to Minecraft: Java Edition using TCP. One way to get around this (if you're using an online host) is to shut down your server, and when asking for a server jar, select Nukkit (you won't actually be switching to Nukkit). Afterward, open up your FTP file manager and find the Nukkit jar. Then, replace this jar with the server software you're using. Upon starting up the server, it should open up ports over UDP whilst still allowing you to use the server jar you desire.

**PLEASE NOTE:** If your server automatically redownloads jars upon startup, such as with an autoupdate system, this workaround will not work. Please contact your host if this does not work for you as there is nothing we can do.

## 卡在 "正在连接服务器" 且后台没有报错

你或许需要升级你的 Java，如果确实是这样，请访问 [AdoptOpenJDK.net](https://adoptopenjdk.net)。

有时这会发生在网络较差的环境中。 Geyser 配置中有一个 `mtu` 选项； 慢慢降低这个数字（以 100 为基准），每次修改后重新启动，并重新测试加入。

如果您收到“无法连接到世界”而没有提示新的连接的控制台记录，则此选项很可能没有作用。

## 登录失败

_**如果你正在使用一个插件版本：**_ 在你的 Geyser 配置，将你的 bedrock 的 ip 设置为 `127.0.0.1`。 If that does not work, check your startup log for a message about Docker, and use that address in the remote address

#### Cannot reply to EncryptionRequestPacket without profile and access token

There are two causes of this message:

_Floodgate issue_:

This message can occur with a Floodgate setup. Usually, it means that a misconfiguration occurred, or another plugin is conflicting. If you copied the Floodgate key from its folder to the Geyser folder on the same server, this is now unnecessary and you can safely remove the Geyser copy, restart, and try again.

_Server is in Online Mode while Geyser is in Offline Mode_:

If you have your configuration set up like this, put simply, it won't work. If authentication for the Java server is set to online, it is expected Geyser is configured the same way. The server requires a valid Minecraft: Java Edition account, and if you aren't logging into one with Geyser, then you will be unable to join the server. If your configuration is set up properly and you're still getting this issue, it could be that your credentials are invalid.

#### Connection Refused: \<INSERT IP AND/OR DOMAIN>

Connection Refused usually means that a Java server could not be found on that port, or the server denied access to the connection on a network level. The latter can happen with anti-DDOS plugins such as TCPShield, but otherwise ensure that the server you're trying to connect to is spelled correctly in the config, is up and is port forwarded correctly.

If you're updating from an old build of Geyser, set your remote address to `auto` and try again.

#### Floodgate Misconfiguration

See [this page](https://github.com/GeyserMC/Floodgate/wiki/Issues) for more information.

#### Mojang Resetting Account Credentials

This is unfortunately something we have no control over, and is most likely the case when you're running Geyser as a plugin on a server host or joining a friend far away from your location. If you're running Geyser locally, this should not happen to you, but what we recommend for servers is a plugin we make called [Floodgate](https://github.com/GeyserMC/Floodgate), which allows for Bedrock clients to join your server without needing a Java Edition account. Take a look [here](https://github.com/GeyserMC/Geyser/wiki/Floodgate) for more information.

## "Invalid IP address!" from Bedrock

It's currently unknown why this happens even for valid domains. Try using the IPv4 address.

## 基岩版客户端在使用指令时出现卡顿或者崩溃

在你的 Geyser 配置文件中关闭 `command-suggestions` 选项。 your Geyser config. This will stop the freezing at the expense of removing command suggestions from Bedrock clients. If you're a dedicated server admin, you can have a list of commands players should be using. This will remove any unnecessary commands from tab completion as well for Java players. It has other benefits too. Here's a plugin that can just do that: [CommandWhitelist](https://www.spigotmc.org/resources/commandwhitelist-spigot-waterfall-velocity.81326/)

## BungeeCord 在基岩版玩家加入后卡顿或者崩溃

请确保你的 **BungeeCord** 的 `config.yml` 配置文件中将 `ip-forward` 设置为 `true` 并在你的所有子服的 `spigot.yml` 配置文件中将 `bungeecord` 设置为 `true`。

## Failed to load locale asset cache: Unrecognized token 'Cannot'

This or anything else related to failing to download a locale file on startup is usually caused by java trying to connect using IPv6 and Mojang only use IPv4, so start Geyser or the server up with this flag `-Djava.net.preferIPv4Stack=true`, EG: `java -Xms1024M -Djava.net.preferIPv4Stack=true -jar Geyser.jar`

## Outdated client! Please use 1.x.x

**Java** 版服务器太新，**Geyser** 对它来说有点旧了。请确保你的 **Geyser** 是最新版本，如果是，请耐心等待 **Geyser** 完成更新。

## Outdated server! I'm still on 1.x.x

更新你的 **Java** 版服务器或者使用 [ViaVersion](https://viaversion.com) 插件。 你也可以尝试 [VIAaaS](https://github.com/ViaVersion/VIAaaS)。

## Query: Incorrect Magic!

See here: [https://www.spigotmc.org/threads/query-incorrect-magic-and-high-cpu-usage.159386/#post-2709057](https://www.spigotmc.org/threads/query-incorrect-magic-and-high-cpu-usage.159386/#post-2709057)

* If you don't use a reverse proxy such as TCPShield make sure that `enable-proxy-protocol` is set to false.

## Only for BungeeCord with floodgate

If you use floodgate ensure that it is installed on all of your Spigot backend servers as following:

1. `Bungee: Geyser and Floodgate`
2. `Lobby: floodgate`
3. `Server-1: floodgate`
4. `Server-2: floodgate` And so on.

* Please also make sure that you have the same `key.pem` and `config.yml` on all of your servers.

If your players can't connect from the lobby to another backend server, check console.

#### Plugins that can cause issues

* `HamsterAPI`
