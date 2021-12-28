# 理解配置

这个页面主要为你介绍 **Geyser** 配置各个选项的作用，尽管配置文件中已经介绍，我们还在这里为你带来更详细的讲解。

### 基岩版部分

这些选项适用于 **Geyser** 基岩端方面。

**`address`**: **Geyser** 所开启的地址。一般情况下，你不需要修改这里，**保持原样即可**。

**`port`**: **Geyser** 所开启的端口。默认和基岩版的默认端口一样，为 `19132`。

**`clone-remote-port`**: 服务器每次开启时，Geyser 所开启的端口和 **Java版**服务器是否保持一致。**独立版无法使用此选项**。

**`motd1`**: **Geyser** 所开启的服务器显示的 **MOTD** 的第一行。

**`motd2`**: **Geyser** 所开启的服务器显示的 **MOTD** 的第二行。**请务必注意该选项只在基岩版客户端 好友 选项卡显示 Geyser 服务器时有效。**

**`server-name`**: 基岩版客户端在 **暂停页面** 所显示的世界名称。

**`compression-level`**: 一个数字值，表示压缩传出流量的程度。 可以是 **-1** 到 **9** 之间的任意数字；任何其他值都将替换为最接近的可接受值。数字越大，使用的 **CPU** 处理越多，但使用的 **带宽** 越少。

### 远程服务器部分 (Java版 部分)

这些选项适用于 **Java** 版服务器。

**`address`**: 你所要连接的 **Minecraft:Java** 版服务器的地址。默认情况下，这个选项被设置为 `auto`。如果一直设置为 `auto`，那么 **Geyser** 会自动同步 **Java版服务器** 的 **IP、端口和Floodgate配置信息**。在独立版，将其设置为 `auto` 将代表设置成 `127.0.0.1`。

**`port`**: 你在 `address` 选项所要连接的 **Minecraft:Java** 版服务器的端口。

**`auth-type`**: 登录到 **Minecraft:Java** 版服务器的方式，包括 `online`, `offline`和 `floodgate`。

**请务必注意您的 `auth-type` 选项必须和对应 Java 版服务器保持一致 (除了你的 Java 版服务器是盗版服务器，而你在这里设置为正版)。尝试不用正版登录方式进入正版服务器是行不通的。如果你希望你的正版服务器的基岩版玩家无需使用 Java正版账号 登录，请查看 Floodgate Wiki。**

**`use-proxy-protocol`**: 是否在连接到服务器时使用 PROXY/HAProxy 协议，这一般在以下情况有用：

* 你的服务器支持 PROXY 协议（大多数情况下是不支持的）。
* 你的 **Java** 版服务器使用 **Velocity** 或者 **BungeeCord** 代理端并且其对应配置也是开启的。

**`forward-hostname`**: 是否将 **Geyser** 服务器的 **IP/端口** 和 **Java版服务器** 保持一致。

### 通用选项

通用选项一般适用于 **Geyser** 本身的修改。

**`floodgate-key-file`**: **Floodgate** 生成的 k**ey** 文件的路径。你必须安装 [Floodgate](https://github.com/GeyserMC/Floodgate/wiki/) 且 `auth-type` 选项设置成  `floodgate`。

**`userAuths`**: 一个放置你自己的 **Minecraft:Java版** 正版账号的选项，这样你每次登录 **Geyser** 服务器将会自动进入服务器，不需要输入你的正版账号信息。 **我只建议你在个人使用 Geyser 时配置此选项，我想没人会愿意把自己的正版账号共享给其他人使用。**

如果你的 **Xbox** 账号名称是 **Notch**，你的 **Java版正版账号** 的邮箱地址是s`foobar2000@gmail.com` 然后你的密码是 `hunter2` ，那么你就需要按下面这样的格式填写配置:

```
userAuths:
  Notch: # MCPE/Xbox 账号名称
    email: foobar2000@gmail.com
    password: "hunter2"
    microsoft-account: true
```

账号名称前面是两个空格，**email** 等前面是四个空格。

**`command-suggestions`**: 如果你的服务器指令提示太多，基岩版客户端在玩家首次打开聊天框并输入指令时会出现卡顿或者崩溃。这个配置选项可以根本指令提示功能，以解决卡顿问题。自从 **1.16.100** 版本更新后**: 指令提示造成的崩溃问题已经大幅度解决，在大多数情况下你不需要关闭这个选项。**

**`passthrough-motd`**: 是否直接显示 **Java** 版服务器的 **MOTD**。如果设置为是，那么 `motd1` 和 `motd2` 选项在 **基岩版客户端** 的 **MOTD不会显示**。

**`passthrough-protocol-name`**: 是否直接显示自定义的 **Java** 版自定义版本信息。 (例如 BungeeCord \[X.X], Paper 1.X) - 这通常在你的Java版服务器使用自定义版本信息功能情况下才有用，如果你不知道你的服务器是否有使用相关功能，你可以前往 **MCSrvStatus** 查看你的服务器版本信息以确认。\<mcsrvstat.us>

**`passthrough-players`**: 是否直接显示 **Java** 版服务器的人数。

**`legacy-ping-passthrough`**: If enabled, manually pings the server by impersonating a Minecraft client instead of using the server's API. **This option should **_**only**_** be enabled if your MOTD or player count is not accurate,** as it can cause errors especially on BungeeCord. This option does nothing on standalone.

**`ping-passthrough-interval`**: How often the fake Minecraft client should attempt to ping the remote server to update information, in seconds (a setting of 1 will ping the server every second; a setting of 3 will ping the server every three seconds). Only relevant for standalone and legacy ping passthrough. Increase the number if you're getting timeout or BrokenPipe exceptions.

**`max-players`**: The maximum amount of players shown when pinging the server. This does not actually cap how many players can join the Geyser instance at this time. The number will visually increase when pinging if the amount of players is greater, as Bedrock clients will not even attempt to join a full server.

**`debug-mode`**: If debug messages should be printed in console. Useful if you run into an error and need more context.

**`general-thread-pool`**: The amount of threads Geyser will be able to use. Higher is not always better :P.

**`allow-third-party-capes`**: If third party (Optifine, 5zig, LabyMod, etc.) capes should be displayed to the bedrock player.

**`allow-third-party-ears`**: If third party Deadmau5-style ears should be enabled. Currently only supports MinecraftCapes.

**`show-cooldown`**: Bedrock Edition currently does not have Java Edition 1.9+ combat mechanics. In order to get around this, Geyser sends a fake cooldown by sending a title message. This cooldown should not show if 1.8 combat mechanics are in use. The options available for this setting are `false` (no cooldown is sent), `title`/`true` (a cooldown indication is shown in the title), or `actionbar` (a cooldown indication is shown in the action bar). All other options default to `false`.

**`show-coordinates`**: Bedrock Edition has an option to show coordinates in the top-left part of your screen. This setting enables or disables this.

**`emote-offhand-workaround`**: Since Java Edition 1.9, clients have had the ability to switch the item in their mainhand and offhand with a keybind. Bedrock Edition does not have this ability, so this config option makes up for it, If set, when a Bedrock player performs any emote, it will swap the offhand and mainhand items, just like the Java Edition keybind. There are three options this can be set to:

* `disabled` - the default/fallback, which doesn't apply this workaround
* `no-emotes` - emotes will NOT be sent to other Bedrock clients and offhand will be swapped. This effectively disables all emotes from being seen.
* `emotes-and-offhand` - emotes will be sent to Bedrock clients and offhand will be swapped

**`default-locale`**: The default locale to send to players if their locale could not be found. Check [this](https://github.com/GeyserMC/Geyser/wiki/FAQ#what-languages-does-geyser-support) page to find the code corresponding to your language.

**`chunk-caching`**: Cache chunks for each Bedrock player, adds support for additional sounds and fixing movement issues at the expense of slightly more RAM usage. This option is always on for Spigot as we can use the server's API to get block information at no expense. _Geyser does not recommend disabling this option._

**`cache-images`**: Specify how many days images will be cached to disk to save downloading them from the internet. A value of 0 is disabled. (Default: 0)

**`allow-custom-skulls`**: 允许 **Geyser** 翻译自定义头颅皮肤。这会在一些低端/老的设备上造成严重的卡顿问题。

**`above-nether-bedrock-building`**: 基岩版的下界最高高度是127，玩家无法在 **128** 格以上高度放置方块 - 开启这个选项以后，Geyser 会把下界维度翻译成末地维度，虽然这么做会导致下界的天空是末地的样子，但目前只能通过这种方法解决你在下界放置 **128** 格以上高度放置方块的问题。

**`force-resource-packs`**: Force clients to load all resource packs if there are any. If set to false, it allows the user to disconnect from the server if they don't want to download the resource packs.

**`xbox-achievements-enabled`**: Allows Xbox achievements to be unlocked. **This disables certain commands so the Bedrock client can't "cheat" to get them; this cannot be worked around if you want to enable this**. Commands such as /gamemode and /give will not work from Bedrock with this enabled.

### 高级选项

**`scoreboard-packet-threshold`**: Geyser updates the Scoreboard after every Scoreboard packet, but when Geyser tries to handle a lot of scoreboard packets per second can cause serious lag. This option allows you to specify after how many Scoreboard packets per seconds the Scoreboard updates will be then limited to four updates per second.

**`enable-proxy-connections`**: Allow connections from ProxyPass and Waterdog. See [https://www.spigotmc.org/wiki/firewall-guide/](https://www.spigotmc.org/wiki/firewall-guide/) for assistance - use UDP instead of TCP. **This option does not need to be enabled in instances like BungeeCord or Velocity**.

**`mtu`**: [https://en.wikipedia.org/wiki/Maximum\_transmission\_unit](https://en.wikipedia.org/wiki/Maximum\_transmission\_unit) - The internet supports a maximum MTU of 1492 but could cause issues with packet fragmentation. 1400 is the default.

**`use-direct-connection`**: Whether to connect directly into the Java server without creating a TCP connection. This should only be disabled if a plugin that interfaces with packets or the network does not work correctly with Geyser. If enabled on plugin versions, the remote address and port sections are ignored. If disabled on plugin versions, expect performance decrease and latency increase.

默认 Geyser 配置：

```
# --------------------------------
# Geyser Configuration File
#
# A bridge between Minecraft: Bedrock Edition and Minecraft: Java Edition.
#
# GitHub: https://github.com/GeyserMC/Geyser
# Discord: https://discord.geysermc.org/
# --------------------------------

bedrock:
  # The IP address that will listen for connections.
  # There is no reason to change this unless you want to limit what IPs can connect to your server.
  address: 0.0.0.0
  # The port that will listen for connections
  port: 19132
  # Some hosting services change your Java port everytime you start the server and require the same port to be used for Bedrock.
  # This option makes the Bedrock port the same as the Java port every time you start the server.
  # This option is for the plugin version only.
  clone-remote-port: false
  # The MOTD that will be broadcasted to Minecraft: Bedrock Edition clients. This is irrelevant if "passthrough-motd" is set to true
  # If either of these are empty, the respective string will default to "Geyser"
  motd1: "Geyser"
  motd2: "Another Geyser server."
  # The Server Name that will be sent to Minecraft: Bedrock Edition clients. This is visible in both the pause menu and the settings menu.
  server-name: "Geyser"
  # How much to compress network traffic to the Bedrock client. The higher the number, the more CPU usage used, but
  # the smaller the bandwidth used. Does not have any effect below -1 or above 9. Set to -1 to disable.
  compression-level: 6
  # Whether to enable PROXY protocol or not for clients. You DO NOT WANT this feature unless you run UDP reverse proxy
  # in front of your Geyser instance.
  enable-proxy-protocol: false
  # A list of allowed PROXY protocol speaking proxy IP addresses/subnets. Only effective when "enable-proxy-protocol" is enabled, and
  # should really only be used when you are not able to use a proper firewall (usually true with shared hosting providers etc.).
  # Keeping this list empty means there is no IP address whitelist.
  # Both IP addresses and subnets are supported.
  #proxy-protocol-whitelisted-ips: [ "127.0.0.1", "172.18.0.0/16" ]
remote:
  # The IP address of the remote (Java Edition) server
  # If it is "auto", for standalone version the remote address will be set to 127.0.0.1,
  # for plugin versions, it is recommended to keep this as "auto" so Geyser will automatically configure address, port, and auth-type.
  address: auto
  # The port of the remote (Java Edition) server
  # For plugin versions, if address has been set to "auto", the port will also follow the server's listening port.
  port: 25565
  # Authentication type. Can be offline, online, or floodgate (see https://github.com/GeyserMC/Geyser/wiki/Floodgate).
  # For plugin versions, it's recommended to keep the `address` field to "auto" so Floodgate support is automatically configured.
  auth-type: online
  # Allow for password-based authentication methods through Geyser. Only useful in online mode.
  # If this is false, users must authenticate to Microsoft using a code provided by Geyser on their desktop.
  allow-password-authentication: true
  # Whether to enable PROXY protocol or not while connecting to the server.
  # This is useful only when:
  # 1) Your server supports PROXY protocol (it probably doesn't)
  # 2) You run Velocity or BungeeCord with the option enabled in the proxy's main config.
  # IF YOU DON'T KNOW WHAT THIS IS, DON'T TOUCH IT!
  use-proxy-protocol: false
  # Forward the hostname that the Bedrock client used to connect over to the Java server
  # This is designed to be used for forced hosts on proxies
  forward-hostname: false

# Allows the overworld world height to be extended from 0 - 255 to -64 - 319. This option cannot be changed during a reload.
# 1.17.0-1.17.2 Bedrock clients cannot connect with this option enabled.
# Performance issues and/or additional bugs may occur for Bedrock clients as this is an experimental toggle on their end.
extended-world-height: false

# Floodgate uses encryption to ensure use from authorised sources.
# This should point to the public key generated by Floodgate (BungeeCord, Spigot or Velocity)
# You can ignore this when not using Floodgate.
# If you're using a plugin version of Floodgate on the same server, the key will automatically be picked up from Floodgate.
floodgate-key-file: key.pem

# The Xbox/Minecraft Bedrock username is the key for the Java server auth-info.
# This allows automatic configuration/login to the remote Java server.
# If you are brave enough to put your Mojang account info into a config file.
# Uncomment the lines below to enable this feature.
#userAuths:
#  BedrockAccountUsername: # Your Minecraft: Bedrock Edition username
#    email: javaccountemail@example.com # Your Minecraft: Java Edition email
#    password: javaccountpassword123 # Your Minecraft: Java Edition password
#    microsoft-account: true # Whether the account is a Mojang or Microsoft account.
#
#  bluerkelp2: 
#    email: not_really_my_email_address_mr_minecrafter53267@gmail.com 
#    password: "this isn't really my password"
#    microsoft-account: false

# Bedrock clients can freeze when opening up the command prompt for the first time if given a lot of commands.
# Disabling this will prevent command suggestions from being sent and solve freezing for Bedrock clients.
command-suggestions: true

# The following three options enable "ping passthrough" - the MOTD, player count and/or protocol name gets retrieved from the Java server.
# Relay the MOTD from the remote server to Bedrock players.
passthrough-motd: false
# Relay the protocol name (e.g. BungeeCord [X.X], Paper 1.X) - only really useful when using a custom protocol name!
# This will also show up on sites like MCSrvStatus. <mcsrvstat.us>
passthrough-protocol-name: false
# Relay the player count and max players from the remote server to Bedrock players.
passthrough-player-counts: false
# Enable LEGACY ping passthrough. There is no need to enable this unless your MOTD or player count does not appear properly.
# This option does nothing on standalone.
legacy-ping-passthrough: false
# How often to ping the remote server, in seconds. Only relevant for standalone or legacy ping passthrough.
# Increase if you are getting BrokenPipe errors.
ping-passthrough-interval: 3

# Whether to forward player ping to the server. While enabling this will allow Bedrock players to have more accurate
# ping, it may also cause players to time out more easily.
forward-player-ping: false

# Maximum amount of players that can connect. This is only visual at this time and does not actually limit player count.
max-players: 100

# If debug messages should be sent through console
debug-mode: false

# Thread pool size
general-thread-pool: 32

# Allow third party capes to be visible. Currently allowing:
# OptiFine capes, LabyMod capes, 5Zig capes and MinecraftCapes
allow-third-party-capes: true

# Allow third party deadmau5 ears to be visible. Currently allowing:
# MinecraftCapes
allow-third-party-ears: false

# Allow a fake cooldown indicator to be sent. Bedrock players do not see a cooldown as they still use 1.8 combat
# Can be title, actionbar or false
show-cooldown: title

# Controls if coordinates are shown to players.
show-coordinates: true

# If set, when a Bedrock player performs any emote, it will swap the offhand and mainhand items, just like the Java Edition keybind
# There are three options this can be set to:
# disabled - the default/fallback, which doesn't apply this workaround
# no-emotes - emotes will NOT be sent to other Bedrock clients and offhand will be swapped. This effectively disables all emotes from being seen.
# emotes-and-offhand - emotes will be sent to Bedrock clients and offhand will be swapped
emote-offhand-workaround: "disabled"

# The default locale if we dont have the one the client requested. Uncomment to not use the default system language.
# default-locale: en_us

# Specify how many days images will be cached to disk to save downloading them from the internet.
# A value of 0 is disabled. (Default: 0)
cache-images: 0

# Allows custom skulls to be displayed. Keeping them enabled may cause a performance decrease on older/weaker devices.
allow-custom-skulls: true

# Whether to add (at this time, only) the furnace minecart as a separate item in the game, which normally does not exist in Bedrock Edition.
# This should only need to be disabled if using a proxy that does not use the "transfer packet" style of server switching.
# If this is disabled, furnace minecart items will be mapped to hopper minecart items.
# This option requires a restart of Geyser in order to change its setting.
add-non-bedrock-items: true

# Bedrock prevents building and displaying blocks above Y127 in the Nether -
# enabling this config option works around that by changing the Nether dimension ID
# to the End ID. The main downside to this is that the sky will resemble that of
# the end sky in the nether, but ultimately it's the only way for this feature to work.
above-bedrock-nether-building: false

# Force clients to load all resource packs if there are any.
# If set to false, it allows the user to connect to the server even if they don't
# want to download the resource packs.
force-resource-packs: true

# Allows Xbox achievements to be unlocked.
# THIS DISABLES ALL COMMANDS FROM SUCCESSFULLY RUNNING FOR BEDROCK IN-GAME, as otherwise Bedrock thinks you are cheating.
xbox-achievements-enabled: false

# bStats is a stat tracker that is entirely anonymous and tracks only basic information
# about Geyser, such as how many people are online, how many servers are using Geyser,
# what OS is being used, etc. You can learn more about bStats here: https://bstats.org/.
# https://bstats.org/plugin/server-implementation/GeyserMC
metrics:
  # If metrics should be enabled
  enabled: true
  # UUID of server, don't change!
  uuid: generateduuid

# ADVANCED OPTIONS - DO NOT TOUCH UNLESS YOU KNOW WHAT YOU ARE DOING!

# Geyser updates the Scoreboard after every Scoreboard packet, but when Geyser tries to handle
# a lot of scoreboard packets per second can cause serious lag.
# This option allows you to specify after how many Scoreboard packets per seconds
# the Scoreboard updates will be limited to four updates per second.
scoreboard-packet-threshold: 20

# Allow connections from ProxyPass and Waterdog.
# See https://www.spigotmc.org/wiki/firewall-guide/ for assistance - use UDP instead of TCP.
enable-proxy-connections: false

# The internet supports a maximum MTU of 1492 but could cause issues with packet fragmentation.
# 1400 is the default.
# mtu: 1400

# Whether to connect directly into the Java server without creating a TCP connection.
# This should only be disabled if a plugin that interfaces with packets or the network does not work correctly with Geyser.
# If enabled on plugin versions, the remote address and port sections are ignored
# If disabled on plugin versions, expect performance decrease and latency increase
use-direct-connection: true

config-version: 4
```
