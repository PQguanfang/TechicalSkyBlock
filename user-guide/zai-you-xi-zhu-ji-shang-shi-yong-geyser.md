# 在游戏主机上使用 Geyser

所有的游戏主机版本客户端都可以加入第三方服务器 - 包括 Geyser 的服务器。像 **Xbox One，Nintendo Switch 和 PS4** 系统的玩家可以通过一个名为 BedrockConnect 的第三方软件进入第三方服务器。要获取该项目的技术信息或者如何搭建该软件，请查看 [他们的 GitHub 页面](https://github.com/Pugmatt/BedrockConnect) (_这个项目不隶属于 GeyserMC_)。没有其他替代的方法。

**注意：The main IP used for BedrockConnect is often blocked on consoles, if you run into issues with internet connection or joining servers after changing your DNS, consider using either one of the other BedrockConnect servers on the** [**BedrockConnect Github Page**](https://github.com/Pugmatt/BedrockConnect)**, or the** [**Public GeyserConnect**](https://www.geyserconnect.net) **which allows connecting to both Java and Bedrock servers.**

## Xbox One

(请参考下面的视频)

[![Xbox One BedrockConnect](https://camo.githubusercontent.com/16b2e654c48fe537827fc702d90960c0804c77e9be5bfc44badd0bf66d472053/68747470733a2f2f696d672e796f75747562652e636f6d2f76692f67386d4876617356484d732f302e6a7067)](https://www.youtube.com/watch?v=g8mHvasVHMs)

## Nintendo Switch

(请参考下面的视频)

[![Nintendo Switch BedrockConnect](https://camo.githubusercontent.com/6c5e8959ec0c85e7a9cd1e1f8a5bf97fc4011eee4660313596105895190a8fea/68747470733a2f2f696d672e796f75747562652e636f6d2f76692f7a616c545f6f52316e504d2f302e6a7067)](https://www.youtube.com/watch?v=zalT\_oR1nPM)

## PlayStation 4

1. 前往你的 PS4 主页。
2. 前往设置。
3. 前往网络。
4. 选择你的网络，并连接。
5. If you are using wired internet, select "Use LAN Cable", otherwise choose "Use Wi-Fi".
6. Select the Custom network creation mode.
7. Select Automatic IP Address.
8. For DHCP Host Name, make sure you select Do Not Specify.
9. Under DNS Settings, select Manual.
10. Enter the BedrockConnect IP for the preferred Primary DNS (Multiple options depending on region can be found on the [BedrockConnect Github Page](https://github.com/Pugmatt/BedrockConnect)) and something like Google or Cloudfare's IP for the Secondary DNS (8.8.8.8 or 1.1.1.1).

### Alternative Methods

If you'd rather try emulating a LAN game on your network on another device, here's how you'd do that.

_Note that this method will not work with the Nintendo Switch._

#### Using a PC

If you have a PC, you can use [Phantom](https://github.com/jhead/phantom).

#### Using an Android Device

If you have an Android device, you have several options:

* [~~Geyser Android app~~](https://github.com/GeyserMC/GeyserAndroid) (Currently out of date)
* [MC Lan Proxy (Trial)](https://discord.com/channels/613163671870242838/613194762249437245/770699493482037310)
* [MC Lan Proxy (Paid)](https://play.google.com/store/apps/details?id=com.luzenna.mineproxydroid)
* [MC Server Connector](https://play.google.com/store/apps/details?id=com.smokiem.mcserverconnector)

#### Using an iOS device

If you have an iOS 14+ device, you can use [BedrockTogether](https://apps.apple.com/app/bedrocktogether/id1534593376).
