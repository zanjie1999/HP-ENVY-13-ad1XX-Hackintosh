# HP-ENVY-13-ad1XX-Hackintosh
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
| Network | Dell Wireless ~~1820a~~ 1560 |

## 更新日志
-------
### 2020-01-11
1. 放弃驱动DW1820A；
2. 修复了之前电池百分比显示问题；
3. 驱动了原生亮度快捷键；
4. 更新`FakeSMC`套件至3.5.3；
5. 调整了待机功耗，现在待机时间应该更长了；
6. 将屏蔽或者禁用的设备合并到一个`SSDT`的`AML`文件中了；
7. 声卡ID换至`03`以获得更好的声音表现；
8. 还有什么其他乱七八糟的我想不起来的更新。

## 说明
-------

1. 目前10.15.2没有问题；
2. 该配置是最早[daliansky](https://github.com/daliansky/)维护的，我对其进行了大量的更新；
3. 显卡FakeID `56160000`，仿冒的`HD 620`；
4. 声卡LayoutID `03`，注入的ID `03`，驱动的是底面的扬声器；
5. 原生网卡Intel AC7265，用不了的，这里我用的网卡~~DW1820A~~ DW1560（只推荐这张，1820A问题很多，1830可能因大小问题不能安装）~~，仿冒的`14e4,4353`；注意：如果您使用的是DW1820A网卡，需要将`CLOVER/ACPI/patched`中的`SSDT-WIFI.aml`替换成`Post-Install/DW1820A`中的`SSDT-WIFI.aml`即可~~；
6. 触控板使用的白果手势，但四指捏合和张开并不能使用，为驱动本身限制，似乎无解；
7. 如果使用的是DW1820A，Airdrop和HandOff没有问题，但是Sidecar可能不能用。其他网卡没有数据，自行测试；
8. 亮度调节可用，~~但亮度快捷键部分有问题，可以外接键盘后在`系统偏好设置`修改快捷键为`Fn+F2`和`Fn+F3`拔掉外接键盘就可以正常使用了~~ 原生亮度快捷键可用，现在亮度档位存在疑点问题：调节档位间隔不是很大。大家自行体会，如果有人有更好的方案，欢迎提交；
9. 电池百分比正常；
10. 如果您有独显，并尝试驱动他，这边建议您直接放弃`Hackintosh`；
11. 如果您对SD卡口有刚需，请自备读卡器；


## 2. 安装
-------

1. 下载macOS原版镜像（或者其他人提供带引导的也可以），文件格式为`dmg`；
2. 使用[`etcher`](https://www.balena.io/etcher/)等工具刻录镜像至U盘；
3. 将提供的`CLOVER`文件夹通过各种手段（不一一列举）放在硬盘的`EFI`分区中的`EFI`文件夹下，并使用`bootice`等工具添加引导项；
4. 重启在HP logo还未出现时按`F10`进入`BIOS`，；
5. 在`CLOVER`中选择`macOS Install from XXX(表示移动设备名称)`进入安装界面~~。如果在这步出现问题，请参考下面的问题部分1~~；
6. 这步和白果一样，分区啊什么乱七八糟的。这里需要记下自己安装macOS的分区名称；
7. 安装中间会重启一次，重启后在`CLOVER`中选择`macOS Install from XXX(这次是你的分区名称)`，这步安装完成后会再次重启。如果在这步出现问题请参考下面的问题部分1；
8. 待第七步结束之后你的`CLOVER`中应该会出现一个`macOS`的选项，回车键进入就可以正常使用了~~，如果不能正常使用的话请参考问题部分2~~。

## 3. 问题
-------

~~1. 如果您使用的是`DW1820A`，那么您可能会遇到卡进度条的情况，这个时候需要带上启动参数`-v`，一般来说就可以直接进去了，如果还进不去就根据具体卡在哪里决定禁用哪个驱动，不过安装进度条本身也很慢，需要等一段时间；~~
~~2. 如果您使用的是`DW1820A`，那么您可能会遇到“冻结”的问题，即系统已开始用的还很流畅，后来突然网卡找不到、菜单栏不可操作、系统奇卡无比。这种情况的话不用怀疑网卡的锅并且我也没有解决方案，如果您有其他问题可以在issue里面提交；~~

1. 如果你尝试使用1820a，那么我祝你好运，但我本人因技术有限不再提供任何与1820a有关的技术支持，如果有需要，请移步[小兵的blog](https://blog.daliansky.net)查看对应问题的解决方案。
2. 全套配置已经由我本人亲自调试，并没有过多问题，安装按照上文提到的教程就不会有差错。如果还是不行，你可以问一下你的电脑为什么不行；
3. 目前PS2驱动存在大写灯不正常/禁用触控板有可能打不开的情况，大家先将就一下，等等VoodooPS2项目更新；
4. 如果有什么改进或者其他建议欢迎PR。

## 4.写在最后
-------

我是`XPS 15 9560`用户，这个配置写下来最主要还是为了我女朋友，`ENVY 13 ad1XX`是她的电脑，执笔时她刚刚买了一台`iPad Air 3`，本着折腾的精神以及更好的体验苹果生态，我决定为她做这么一份引导，驱动的更新不会太差，但是可能很多情况下对问题的修复会有些不及时。
2020-01-11续
这台机子奉劝大家千万不要用1820A，按照小兵的方法，原则上时不能驱动的，但是可以通过固件保留的方式（启动Windows后重启到Mac）使用网卡，但代价是不能睡眠，一睡网卡必定掉，整个系统直接卡死。

## 鸣谢
-------
以下排名不分先后：<br>
[Acidanthera](https://github.com/acidanthera)提供的各种驱动、[Daliansky（黑果小兵）](https://github.com/daliansky/)及其[博客](https://blog.daliansky.net/)提供的首版引导和DW1820A驱动方式及睡眠修复方法、[Bat.bat](https://github.com/williambj1)提供的Envy13亮度快捷键以及电池补丁、[Aris](https://ariser.cn)提供的10.14.5以及HDMI补丁、[JardenLiu](https://github.com/jardenliu)提供的XPS15教程以及一系列讲解以供深入学习Hackintosh、[Rehabman](https://bitbucket.org/%7Be26fb9ce-5cc2-4e36-8576-7a8faae8e194%7D/)提供的一系列补丁、以及很多朋友提供的问题反馈！


-------
请勿使用此项目用作商业目的<br>
惠普电脑装Mac交流群：543758684<br>
ENVY13(2017)交流群：247548827<br>
