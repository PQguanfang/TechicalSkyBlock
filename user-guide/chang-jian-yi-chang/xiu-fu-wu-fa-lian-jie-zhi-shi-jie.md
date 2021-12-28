# 修复 “无法连接至世界”

_无法连接至世界_ 是许多人在使用 Geyser 时遇到的共同问题，下面我们将一步一步教你如何解决这一问题。

## 在我们开始之前...

### ...Java 玩家同样也无法加入！

这 **肯定不是** Geyser的问题。**Geyser** 不会对 **Java版服务器** 进行任何改动。**Floodgate** 也只对 **基岩版玩家** 修改登录流程。所以，请联系你的服务商，向他们寻求解决服务器连接的问题。

### ...我刚刚更新了Geyser，现在它没法正常工作了！

如果这在你更新了插件版的Geyser后出现，请确保你是关闭了你的服务器，然后替换了 Geyser jar 文件，然后重新开启你的服务器。

### ...控制台有一堆报错！

请阅读 [常见异常](./)。如果你的问题并不在那个页面出现，请加入我们的 [Discord](https://discord.geysermc.org) 以寻求帮助。

### ...你被无限的重启困扰了吗？

特别是手机用户，有时，你只需要重启你的游戏客户端就可以解决这个问题了。

## 是服务器的问题还是客户端的问题？

将你的 **Java** 版服务器 **IP** 和基岩版的 **IP** 放在 [https://mcsrvstat.us/](https://mcsrvstat.us) 网站查询。这是首先确定服务器是否正常工作的好办法。

## 一般排除步骤

### 确保你使用正确的 IP 连接

You should be connecting with the Java server IP and the Bedrock port. If you port forwarded 19132, for example, you should specify port 19132 when connecting from Bedrock.

### 我正在使用一个云主机 或者 VPS！

请向你的服务商寻求帮助。

### 端口转发

Your server does need to be port forwarded. Generally, you can follow any Minecraft: Java Edition port forwarding guide; however, you need to replace any mention of TCP with UDP and, by default, any mention of 25565 with 19132.

### Using TCP in DNS options/port forwarding Instead of UDP

Minecraft: Java Edition uses TCP for connecting; Minecraft: Bedrock Edition uses UDP. Port forwarding your Bedrock Edition port with only TCP will not work, it has to be UDP. Forwarding your Bedrock Edition port with `TCP/UDP` (both protocols) should also work but is not recommended unless Java Edition and Bedrock Edition is sharing the same port.

### Bedrock port is less than 10000

Historically, having a Bedrock port that is a lower number will cause issues. Setting it to 10000 or above seems safe.

### Bedrock players can connect _after_ hitting the server on a TCP port (e.g. on Java or a website on the same server), OR only people who also play on Java Edition can join from Geyser

This is likely a firewall issue on your server. Try the following workaround:

Attempt to connect to the Bedrock IP and port through a web browser - for example, `http://test.geysermc.org:19132`. It won't work, but then try connecting through Bedrock, and it should work.

Specific host fixes:

SoYouStart (a subsidiary of OVH):

In the SoYouStart control panel:

1. Click the IP tab.
2. Click the gear at the right of the public IP address; select "Game mitigation".
3. Pick "Add a rule".
4. Select "minecraftPocketEdition" in the dropdown list and enter the target UDP ports.
5. Save and wait a few seconds for the changes to come into effect.

### Issues connecting with OVH or a subsidiary

If you're running into issues with some Bedrock players being unable to connect on OVH, navigate through the following settings:

* Navigate to `Network interfaces`
* Click on the `...` button on the table for your IP -> then `...` and `Configure the GAME firewall` -> `Add rule` -> `Other protocol` (or `minecraftPocketEdition` if available)
* Add your Geyser port into `outgoing port`

### Changing the `bedrock` `address` in the Geyser config.

Except for a few specific hosting providers, you generally do not need to change this part of the Geyser config. However, in rare instances, it does fix issues

## Using a hosting provider or other location

### Pterodactyl

If you get this error while using the Pterodactyl Panel, try editing the Geyser config and changing the port to something besides `19132` (e.g. `25566`).

### Hosting Geyser on another computer on the same network

#### Can only connect from the same computer and not anywhere else

Your firewall is likely in the way. Try adding an exception to Java, or disable the firewall for testing purposes.

## Using Geyser on the same computer

### Windows 10

_This only affects people trying to join Geyser from Windows 10 Edition with Geyser hosted on the same computer._

This is an issue caused by Loopback restrictions not being lifted. By default, Microsoft Apps have this restriction on all their apps for local connections. Geyser will attempt to resolve this automatically; however, if you're still having connection problems, you can lift it by typing the following in Windows PowerShell in administrator mode: (it should return `OK.` if it worked)

```
CheckNetIsolation LoopbackExempt -a -n="Microsoft.MinecraftUWP_8wekyb3d8bbwe"
```

Should this not work, you can try this set of steps:

1. Hold down Windows Key + R
2. In the prompt, type `hdwwiz.exe`, then press Enter then Next
3. Install the Hardware Manually
4. Choose Network Adapter > Next > Microsoft > "Microsoft KM-TEST Loopback Adapter" then hit Next until it's done.
