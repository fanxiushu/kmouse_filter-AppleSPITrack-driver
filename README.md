
kmdf_driver是驱动源代码目录， 使用WDK7编译。

bin目录里边的两个子目录：过期签名的驱动， 未签名驱动

未签名驱动：
    是完整的驱动包，
    如果你拥有驱动签名证书，可以自己签名，签名之后。
    打开”设备管理器“，找到 “Apple SPI Trackpad”，右击点“卸载设备”，弹出框中，选中“删除此设备的驱动程序软件”，然后卸载。
    卸载之后，重启系统，然后再次打开设备管理器，会看到一个打问号的未知设备，点击它，更新驱动，然后选择签名了之后的驱动安装即可。

过期签名的驱动：
    这个是使用网上的一个过期证书签名的，如果你没有自己的签名证书，安装方法需要你自己手动安装。
    首先把kmouse_filter.sys复制到一个固定目录（最好是全英文目录），
    然后运行 InstDrv.exe，打开kmouse_filter.sys路径，点“安装”，成功之后关闭InstDrv.exe。
    打开注册表 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\SPI\VID_05ac&PID_0277&MI_02 ，
    找到 LowerFilters 字段，看到里边有AppleSPITrackpad，把它替换成 kmouse_filter
    之后重启电脑即可。

不管哪种方式，希望你是熟悉windows的，而不是windows小白。
能在安装前做好系统备份，同时备份Bootcamp驱动，这样出错时候可以恢复。
出问题则由你自己负责。
 
本驱动在 macbook pro 2017版13寸带bar的机器测试成功，
bootcamp版本是 6.1.6183.0， Apple SPI Device 总线驱动日期 2016/5/26， 版本 6.1.6500.0
其他型号的mac机器没有测试过。


如果熟悉windows驱动开发，可以修改本驱动源代码以达到你平时熟悉的手势操作，
也可以制作更好使用的安装程序，
但并不意味着，可以使用本驱动作为生财工具。

fanxiushu  2017

