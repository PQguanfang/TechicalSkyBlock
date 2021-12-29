# 搭建和用法

## 下载

Floodgate 2.0: [https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/)\
Geyser: [https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/](https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/)

## 准备

* 你必须拥有或者拥有一个服务器的管理权限才能使用 **Floodgate**。_如果你不是该服务器的服主或者管理者，那么 **Floodgate** 是无效的，因为它不会帮助你尝试绕过 **Java版服务器** 的正版验证。_
* 你必须使用 **Geyser** 的 [插件版](../user-guide/da-jian/#ge-cha-jian-ban-de-da-jian) 或者 [独立版](../user-guide/da-jian/#du-li-ban-de-da-jian)。**Floodgate** 无法取代 **Geyser** 的功能。
* 你必须保证你正在使用最新版本的 Geyser。（旧版本的 **Geyser** 只和 **Floodgate 1.0** 适配而不支持 **Floodgate 2.0**）
* `floodgate-spigot.jar` 不能安装到 **CraftBukkit/Bukkit** 服务器上。

## 搭建

_以下提及有关 Spigot 的内容，在类似 Paper 的基于 Spigot 的fork上也通用。_

For BungeeCord/Velocity setups: you only are required to install Floodgate on the BungeeCord or Velocity proxy unless you want to use the Floodgate API on the backend servers - see [below](https://github.com/GeyserMC/Floodgate/wiki/installing-floodgate-also-on-spigot-servers-behind-bungeecord-or-velocity) for the installation process.\
&#x20;      _Note:_ Installing Floodgate on the backend servers will allow Bedrock player skins to display without the Bedrock player having to switch backend servers.

* Download the Floodgate plugin from [here](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/) and add it to your plugins folder on your frontend server.
  * `floodgate-spigot.jar` for Spigot, Paper, etc
  * `floodgate-bungee.jar` for BungeeCord, Waterfall, etc
  * `floodgate-velocity.jar` for Velocity
* Change the `auth-type` in the Geyser config to `floodgate`.
* Restart/start up the server.

**你只需在使用独立版上进行此步骤：**

* _Copy_ the `key.pem` file in the Floodgate config folder to the same directory as Geyser Standalone. **DO NOT DISTRIBUTE THIS KEY TO ANYBODY!** This key is what allows for Bedrock accounts to bypass the Java Edition authentication, and if anyone gets ahold of this, they can wreak havoc on your server.

#### Installing Floodgate also on Spigot servers behind BungeeCord or Velocity

This is only needed when you want to use the Floodgate API on your Spigot server(s) behind a proxy.

* Install Floodgate on the proxy and on _all_ backend servers as per the [previous insructions](https://github.com/GeyserMC/Floodgate/wiki/Setup-and-Usage#setting-up)
* Enable `ip_forward` in your BungeeCord `config.yml` if using BungeeCord
* Set `bungeecord` to `true` in your `spigot.yml`
* Start the proxy server.
* Edit the Floodgate config on your proxy server and set `send-floodgate-data` to `true`.
* _Copy_ the `key.pem` file in the proxy Floodgate config folder to all Spigot servers' Floodgate config folder. **DO NOT DISTRIBUTE THIS KEY TO ANYBODY!** This key is what allows for Bedrock accounts to bypass the Java Edition authentication, and if anyone gets ahold of this, they can wreak havoc on your server.
* Restart the Spigot servers and proxy server.

## 我如何将 Floodgate 1.0 升级到 Floodgate 2.0？

Floodgate 2.0 is not compatible with Floodgate 1.0 and Floodgate 1.0 is not compatible with Floodgate 2.0, which means there may be some manual upgrading required. When Floodgate 2.0 is loaded for the first time (on your server), it will try to convert the Floodgate 1.0 config to a Floodgate 2.0 config and it will generate a new key (the old one can be found under `old-key.pem`). Floodgate 2.0 uses a different algorithm for the key and because of that, you now only have one key (called `key.pem`) instead of two. You will have to copy the new Floodgate key (like you had to do in the initial startup) to all the servers that use Floodgate, including Geyser-Standalone.\


Probably not everyone will understand what has been said, so here is a step-by-step guide:

1. Replace Geyser with the [latest version](https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/) (builds of Geyser that worked with floodgate 1.0, don't work) and replace every server that uses Floodgate with the [latest version](https://ci.opencollab.dev/job/GeyserMC/job/Floodgate/job/master/).
2. Restart **one** server that uses Floodgate and let Floodgate update the config and generate a new `key.pem` file.
3. Look at the Floodgate configuration of that server and check if `config-version` is present in the Floodgate config. If it isn't, you have not installed Floodgate 2.0. While you are there, please decide if you want to continue using the legacy player name prefix `*` or use one of the recommended prefixes: `.` (the new default), `+` or `-`. All those new prefixes are easier to use for commands since you don't have to wrap the player's name in quotes.
4. Copy the files: `config.yml` and `key.pem` to all your servers that use Floodgate.
5. If you are using Geyser-Standalone, only copy `key.pem` to the Geyser-Standalone folder.
6. Make sure that you edit the Geyser config to point to `key.pem` instead of `public-key.pem` (the setting is`floodgate-key-file`).
7. Restart the other servers and check for errors.
8. Try to join Geyser with one account to check if everything works as expected. If it doesn't, please make sure that you followed every step correctly. If you did everything correctly and it still doesn't work, join our Discord to get support.

Depending on if you want to keep using [Global Linking](https://github.com/GeyserMC/Floodgate/wiki/Features#What-is-Global-Linking), which is enabled by default, you should be ready to go.

To migrate your Floodgate 1.0 local account linking database, follow [these](https://github.com/GeyserMC/Floodgate/wiki/Features#Local-Linking) steps.

## 修改/关闭基岩版玩家前缀

_**Please note: we do not recommend removing the prefix unless you are certain that no one will share a username between a Java and Bedrock player. Duplicated usernames will cause weird situations, like being unable to teleport to one of the players.**_

In your Floodgate config, change `username-prefix` to whichever prefix you desire - you can set it to `""` and there will be no prefix.

On some older Paper servers (or any forks that use them), you may need to also shut down your server and delete your `usercache.json` file located in the same folder as your server jar to prevent users who already joined from having the old prefix. See \[this issue]\(Issues#Prefix-is not-changing-on-the-server-after-changing-it in-the-config.) for more information.

## 获取 Floodgate 玩家的 UUID

Check your server logs, or use [this](https://floodgate-uuid.heathmitchell1.repl.co) page. If this doesn't work, then try this method:

First, you'll need to get the XUID of the player. There are several third-party websites to find this, for example, this one (unaffiliated with Geyser). Make sure to choose "Hexidecimal." You'll need to enter the player's Xbox Gamertag, and, once submitted, and it should display the XUID in the format of `xxxxxxxxxxxxxxxx`. To turn the XUID into a UUID that Java Edition can recognize, you need to put the XUID in this format: `00000000-0000-0000-xxxx-xxxxxxxxxxxx`. If formatted right, Java Edition should accept it as a UUID.

## 使用 PlaceholderAPI

If you're using the Bukkit version of Floodgate, download the Placeholder plugin [here](https://github.com/rtm516/FloodgatePlaceholders/). Using the placeholders shouldn't require additional setup other than having [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) installed. See the section above on installing Floodgate on backend servers if you wish to use this on BungeeCord.

## 使用 Skript

If you're using the Bukkit version of Floodgate, there is an unofficial plugin that adds Skript support [here](https://github.com/Camotoy/floodgate-skript).
