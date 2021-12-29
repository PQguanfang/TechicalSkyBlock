# 问题

## 已知问题和注意事项

如果您遇到的问题没有在这里列出，请考虑加入geyser的[Discord频道]（http://discord.geysermc.org)。

### Running commands

在某些情况下，例如，如果您将`username-prefix'设置为'*`，则可能需要将基岩版玩家的用户名用引号括起来;例如：`/tp"*homo114514"`。 将前缀设置为`。'也许能解决这个问题。

### If you wish to use IP forwarding, please enable it in your BungeeCord config as well!

很可能您在Floodgate配置中启用了"send-floodgate-data"，但是Floodgate没有安装在目标服务器上，或者您的floodgate密钥在插件的安装之间不同（请复制它们，以便它们都使用相同的密钥）。

### `java.lang.IllegalStateException: Cannot reply to EncryptionRequestPacket without profile and access token.`

确保服务器安装了Floodgate并正确启动. 否则，请查看下一行是否修复了您的错误。

### `javax.crypto.AEADBadTagException: Tag mismatch!`

如果Geyser和Floodgate在同一台服务端上，请关闭您的服务端，删除`floodgate`插件文件夹，删除Geyser文件夹中的任何密钥文件，然后重新启动您的服务端。 如果Geyser和Floodgate不在同一台服务器上，并且您必须复制密钥文件，这也可能是与通过FTP上传相关的错误。 使用ASCII在这里不起作用，并且您需要确保在上传时使用二进制文件。 我们建议使用[WinSCP](https://winscp.net/eng/index.php）如果您需要使用FTP。

### java.lang.NumberFormatException: For input string: ""

您尝试在没有Xbox帐户的情况下登录。 Floodgate需要一个Xbox帐户来验证基岩玩家.

### Geyser-Floodgate:51777 lost connection: Internal Exception: java.lang.NumberFormatException: For input string: "SfqdXv36" (or a similar error)

将BungeeCord中的`ip-forwarding`设置为`true`。

### "Please connect through the official Geyser" disconnect message

确保Floodgate和Geyser的版本都是最新的.

### Prefix is not changing on the server after changing it in the config.

在1.15.2-355和1.16.5-505的文件构建之间，有一个错误，即已经连接到服务器的Floodgate玩家不会改变他们的前缀。 Paper build1.16.5-506及更高版本修复了此问题。

确保您删除了'usercache。json'文件从服务端根目录并重新启动您的服务端。

### Issues with LuckPerms and prefixes

在LuckPerms的配置中设置'allow-invalid-usernames'为'true'。

### Error with Forge or Fabric Bukkit Hybrid

目前，没有办法在混合Forge和Bukkit或Fabric和Bukkit的服务器上运行Floodgate（例如：Magma，Mohist和Cardboard/Bukkit4Fabric）-大多数混合端不支持我们需要做的复杂程序，以便让基岩版玩家连接 (对于有技术头脑的人来说：这些服务器软件通常不支持NMS).

如果您希望将Floodgate与混合服务器结合使用，我们建议将这些服务器放在BungeeCord或Velocity代理后面，并在代理上运行Floodgate。
