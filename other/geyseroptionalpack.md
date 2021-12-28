# GeyserOptionalPack

#### **下载:** [https://ci.opencollab.dev/job/GeyserMC/job/GeyserOptionalPack/job/master/lastSuccessfulBuild/artifact/GeyserOptionalPack.mcpack](https://ci.opencollab.dev/job/GeyserMC/job/GeyserOptionalPack/job/master/lastSuccessfulBuild/artifact/GeyserOptionalPack.mcpack)

**GeyserOptionalPack** 是 **Geyser** 为 **基岩版与Java版** 同步而为基岩版提供额外功能支持的资源包。该资源包为基岩版带来 **新的功能和错误修复**，包括：

* 自定义盔甲架姿势
* 幻术师
* 铁傀儡受伤后”裂开“纹理
* 击打粒子和其他基岩版原版不存在的粒子
* 副手动画
* 潜影贝隐形
* 光灵箭纹理

更详细的列表可见该资源包的 [README](https://github.com/GeyserMC/GeyserOptionalPack/blob/master/README.md) 页面。如果你对如何实现这些功能的细节方面感兴趣，你可以  [点击这里](https://github.com/GeyserMC/GeyserOptionalPack/blob/master/developer\_documentation.md) 查看。

虽然我们推荐您使用此资源包，但您不需要在 **Geyser** 服务器上安装此资源包 - 玩家可以自己安装到客户端中。此外，如果您使用 **WaterdogPE** 等代理端，则可以在服务器上安装该资源包，并且不会影响其他基岩版子服上的游戏。

#### 资源包冲突

如果你当前服务器资源包包含任何与本资源包系统的 [实体改动](https://github.com/GeyserMC/GeyserOptionalPack/tree/master/entity) 相同的部分，那么您需要将对这些实体改动的文件进行合并才能正常工作。否则，基于本资源包的关于实体方面的改动将会根据资源包的顺序来决定优先级，将有可能导致本资源包或者服务器的资源包作用失效。这个过程较为复杂，我们建议您人工操作，当然您也可以尝试使用 [脚本](https://gist.github.com/Kas-tle/89c6adc3e7901fbabd1b9f71d902d0a6) 来操作。
