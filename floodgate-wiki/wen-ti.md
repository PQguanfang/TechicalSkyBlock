# 问题

## 已知问题和注意事项

如果您遇到的问题没有在这里列出，请考虑加入 Geyser 的 [Discord频道](http://discord.geysermc.org)。

### 运行指令时出错

在某些情况下，例如，如果您将 Floodgate 的配置的 `username-prefix` 选项设置为 `*`，则可能在运行指令时需要将基岩版玩家的用户名用引号括起来；例如：`/tp "*homo114514"`。将基岩版玩家的前缀设置为 `.` 也许能解决这个问题。

### If you wish to use IP forwarding, please enable it in your BungeeCord config as well!

很可能您在 **Floodgate** 配置中启用了 `send-floodgate-data`，但是您没有将 **Floodgate** 生成的密钥文件复制到所有子服的 **Floodgate** 文件夹中，或者您的 **各个子服的密钥文件不一致**（请一次性复制它们，以便它们都使用相同的密钥）。

### `java.lang.IllegalStateException: Cannot reply to EncryptionRequestPacket without profile and access token.`

确保服务器正确安装了 **Floodgate** 并启动，如果这不能解决你的问题，请查看下面报错的解决方案。

### `javax.crypto.AEADBadTagException: Tag mismatch!`

如果 **Geyser** 和 **Floodgate** 在同一个服务器上，请关闭您的服务器，删除服务器中的 `floodgate` 插件文件夹并删除服务器中的 `Geyser` 文件夹中的所有密钥文件，然后重新启动您的服务器。 如果 Geyser 和 Floodgate 不在同一台服务器上，并且您必须复制 **Floodgate** 的密钥文件到 **Geyser** 文件夹内，如果你已上传，这也可能是与 **通过FTP上传** 相关的错误。使用ASCII在这里不起作用，并且您需要确保在上传时使用二进制文件。如果您使用 **FTP** 进行文件传输，我们建议使用 [WinSCP](https://winscp.net/eng/index.php)。

### java.lang.NumberFormatException: For input string: ""

您尝试在没有 **Xbox帐户** 的情况下登录。**Floodgate** 需要一个 **Xbox帐户** 来验证基岩玩家。如果您已登录，则重新启动客户端再试。

### Geyser-Floodgate:51777 lost connection: Internal Exception: java.lang.NumberFormatException: For input string: "SfqdXv36" (or a similar error)

将 **BungeeCord** 配置中的`ip-forwarding` 设置为 `true`。

### 在连接时提示 "请从官方Geyser连接"

请确保 **Floodgate** 和 **Geyser** 的版本都是最新的。

### 即使修改了配置，前缀也没加到基岩版玩家名字中

在 **Paper** 的 **1.15.2-355** 和 **1.16.5-505** 的构建之间，有一个错误，即已经连接到服务器的 **Floodgate** 玩家不会修改他们的前缀。**Paper build1.16.5-506** 及更高版本修复了此问题。

同时确保您删除了服务端根目录下的 `usercache.json` 文件并重新启动您的服务器。

### 使用 LuckPerms 时玩家的前缀出现错误

在 **LuckPerms** 的配置中设置 `allow-invalid-usernames` 为 `true`。

### 在混合 Forge 或者 Farbic 的 Bukkit 系服务端上出现错误

目前，没有办法在混合Forge和Bukkit或Fabric和Bukkit的服务器上运行Floodgate（例如：Magma，Mohist和Cardboard/Bukkit4Fabric）-大多数混合端不支持我们需要做的复杂程序，以便让基岩版玩家连接 (对于有技术头脑的人来说：这些服务器软件通常不支持NMS)。

如果您希望将Floodgate与混合服务器结合使用，我们建议将这些服务器放在BungeeCord或Velocity代理后面，并在代理上运行Floodgate。
