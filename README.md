# HP-ENVY-13-ad1XX-Hackintosh
-------

我基于下面的内容进行了修改，使用底部的扬声器，音质更好

-------
惠普 ENVY 13 黑苹果

## 配置
-------

| Specs | Model |
| --- | --- |
| Board | HP 83A8 |
| CPU | Intel Core i5-8250U |
| GPU | Intel Graphics UHD 620 |
| Audio | Realtec ALC298 |
| Network | Dell Wireless 1560 （缺点是贵）|

## 1. 说明
-------

1. 目前兼容10.15；
2. 该配置是最早[daliansky](https://github.com/daliansky/)维护的，我对其进行了一定的更新；
3. 显卡FakeID `56160000`，仿冒的`HD 620`；
4. 声卡LayoutID `1c`，注入的ID `28`，驱动的是前面板的扬声器；
5. 原生网卡Intel AC7265，用不了的，这里我用的网卡DW1820A（DW1830、DW1560也可以），仿冒的`14e4,4353`；注意：如果您使用的是DW1820A网卡，需要将`CLOVER/ACPI/patched`中的`SSDT-WIFI.aml`替换成`Post-Install/DW1820A`中的`SSDT-WIFI.aml`即可；
6. 触控板使用的白果手势，但四指捏合和张开并不能使用，为驱动本身限制，似乎无解；
7. 如果使用的是DW1820A，Airdrop和HandOff没有问题，但是Sidecar可能不能用。其他网卡没有数据，自行测试；
8. 亮度调节可用，但亮度快捷键部分有问题，可以外接键盘后在`系统偏好设置`修改快捷键为`Fn+F2`和`Fn+F3`拔掉外接键盘就可以正常使用了；
9. 如果您有独显，并尝试驱动他，这边建议您直接放弃`Hackintosh`；
10. 如果您对SD卡口有刚需，请自备读卡器；


## 2. 安装
-------

1. 下载macOS原版镜像（或者其他人提供带引导的也可以），文件格式为`dmg`；
2. 使用[`etcher`](https://www.balena.io/etcher/)等工具刻录镜像至U盘；
3. 将提供的`CLOVER`文件夹通过各种手段（不一一列举）放在硬盘的`EFI`分区中的`EFI`文件夹下，并使用`bootice`添加引导项；
4. 重启在HP logo出现时按`F10`进入`BIOS`，……；
5. 在`CLOVER`中选择`macOS Install from XXX(表示移动设备名称)`进入安装界面。如果在这步出现问题，请参考下面的问题部分1；
6. 这步和白果一样，分区啊什么乱七八糟的。这里需要记下自己安装macOS的分区名称；
7. 安装中间会重启一次，重启后在`CLOVER`中选择`macOS Install from XXX(这次是你的分区名称)`，这步安装完成后会再次重启。如果在这步出现问题请参考下面的问题部分1；
8. 待第七步结束之后你的`CLOVER`中应该会出现一个`macOS`的选项，回车键进入就可以正常使用了，如果不能正常使用的话请参考问题部分2。

## 3. 问题
-------

1. 如果您使用的是`DW1820A`，那么您可能会遇到卡进度条的情况，这个时候需要带上启动参数`-v`，一般来说就可以直接进去了，如果还进不去就根据具体卡在哪里决定禁用哪个驱动，不过安装进度条本身也很慢，需要等一段时间；
2. 如果您使用的是`DW1820A`，那么您可能会遇到“冻结”的问题，即系统已开始用的还很流畅，后来突然网卡找不到、菜单栏不可操作、系统奇卡无比。这种情况的话不用怀疑网卡的锅并且我也没有解决方案，如果您的`DW1820`有其他问题请去`SilentSliver`的issue里面提交；
3. 以上“冻结”大概也是固态的锅，可以稳定，似乎容易造成Windows系统损坏（哪怕只读挂载）

## 鸣谢
-------
以下排名不分先后：<br>
[Acidanthera](https://github.com/acidanthera)提供的各种驱动、[Daliansky（黑果小兵）](https://github.com/daliansky/)及其[博客](https://blog.daliansky.net/)提供的首版引导和DW1820A驱动方式及睡眠修复方法、[JardenLiu](https://github.com/jardenliu)提供的XPS15教程以及一系列讲解、[Rehabman](https://bitbucket.org/%7Be26fb9ce-5cc2-4e36-8576-7a8faae8e194%7D/)提供的一系列补丁、以及很多朋友提供的问题反馈！


-------
请勿使用此项目用作商业目的<br>
惠普电脑装Mac交流群：543758684<br>
ENVY13(2017)交流群：247548827<br>
