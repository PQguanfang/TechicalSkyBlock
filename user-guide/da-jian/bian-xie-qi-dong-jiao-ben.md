# 编写启动脚本

**要使用启动脚本，你必须安装了 Java8 或者更高版本！**

一旦你下载并放置好 **Geyser** 到它的独立文件夹，那么你需要编写一个启动脚本来启动它，就像启动一个 **Bukkit** 服务器那样！

#### Windows

* 在 **Geyser jar** 文件相同的目录创建一个文本文件，并将其命名 `run.bat`。以文本管理软件为打开方式编辑它（推荐使用Notepad++），并按照如下内容填写:

```
@echo off
java -Xms1024M -jar Geyser.jar
pause
```

* 双击 **run.bat**，Geyser将会启动并生成它所需的所有文件。

#### macOS

* 同样，创建命名为 **run.command** 的文件，然后使用像 **TextEdit** 或者 **TextMate** 的 **文本编辑软件** 编辑 **run.command** 文件:

```
#!/bin/bash 
cd "$( dirname "$0" )" 
java -Xms1024M -jar Geyser.jar
```

* 打开 **Terminal**，输入 `chmod a+x` **(不要按回车！)**，然后将你的 _run.command_ 文件放置到 **Terminal**。
* 按下键盘的回车键，Geyser将会启动并生成它所需的所有文件。

#### Linux

* 同样，创建名为 _run.sh_ 的文件，然后使用 **文本编辑软件** 编辑 **run.sh** 文件:

```
#!/bin/sh 
cd "$( dirname "$0" )" 
java -Xms1024M -jar Geyser.jar
```

* 在你的默认终端软件中，输入命令 `chmod +x ~(dir)/run.sh` 其中 `dir` 指的是 **Geyser** 文件所在的路径或者通过其他方式给予最高权限。
* 在你的默认终端软件中，使用命令 `./run.sh` 来启动Geyser，Geyser将会生成它所需的所有文件。
