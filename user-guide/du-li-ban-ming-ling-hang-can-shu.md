# 独立版命令行参数

## 通用命令行参数

#### `--config [文件路径]`

**简写: `-c`**

指定一个路径下的 **config.yml** 文件使用。

#### `--gui` / `--nogui`

**简写: `gui` / `nogui`**

强制使用图形化页面启动/强制不使用图形化页面启动。

## 重写特定配置选项

通过重写特定配置选项，**Geyser** 直接优先读取参数内的配置，无视 **config.yml** 内对应的配置。

重写一个标准配置选项 (例如 `command-suggestions`):

`--command-suggestions=false`

重写一个嵌套配置选项(例如 `remote` 下的 `address`):

`--remote.address=test.geysermc.org`
