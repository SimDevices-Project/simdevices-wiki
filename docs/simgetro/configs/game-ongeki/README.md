# 连接到「オンゲキ」

您的设备需要经过配置才能连接到「オンゲキ」，如果您希望这么做，请遵循以下步骤操作。

## 手工修改配置文件

1. 找到并打开您的配置文件，这个文件名对于大多数环境下是`segatools.ini`；如果您修改了相关配置，请打开对应的文件
2. 编辑您的`[aime]`段落，找到`enable`项目，将其值修改为`0`
3. 编辑您的`[aimeio]`段落，删除该段落下所有内容，如果不存在该段落请直接跳过此步骤
4. 编辑您的`[io4]`段落，找到`enable`项目，将其值修改为`0`
5. 编辑您的`[mu3io]`段落，删除该段落下所有内容，如果不存在该段落请直接跳过此步骤
6. 编辑您的`[led15093]`段落，找到`enable`项目，将其值修改为`0`
7. 保存您的配置文件

## 使用示例配置文件

或者您也可以找到您的配置文件，然后根据以下范例修改您的配置文件。

```ini
[vfs]
amfs=amfs
option=option
appdata=appdata

[aime]
enable=0

[dns]
default=aqua.naominet.live

[netenv]
enable=1

[keychip]
gameId=SDDT

[gpio]
enable=1
freeplay=0
dipsw1=1

[gfx]
enable=1

[led15093]
enable=0

[io4]
enable=0
```

以上配置设置了您的游戏连接到[RinNET](https://portal.naominet.live/)服务器，并为您的控制器配置了基本的设置项，您可以参考以上配置修改您的配置项。