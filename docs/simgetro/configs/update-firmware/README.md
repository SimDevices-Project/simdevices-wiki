# 更新固件

遵循以下步骤，可以为您的SimGETRO更新固件

## 在线更新

> TODO

## 临时手动更新方案

!> 请只有在确定必须的情况下才进行手动更新

要为您的设备更新固件，请先从售后群文件中下载测试固件包。

1. 解压`index.zip`
2. 使用现代浏览器打开`index.html`
3. 按住Coin按钮同时连接手台到计算机
4. 在网页中选择`请求设备`
5. 在网页中选择`连接设备`
6. 在网页中选择`初始化IAP`
7. 在网页中选择`选择文件`，选取固件二进制文件，如`测试固件-20250204.bin`
8. 在网页中选择`烧入固件`，并等待Log窗口显示`Firmeware write done`字样
9. 在网页中选择`验证固件`，并等待Log窗口显示`Firmeware verify OK`字样
10. 在网页中选择`跳转程序`，如果跳转出现错误，请手动重新连接设备，然后继续下一步
11. 将设备的摇杆摆放至正中间
12. 打开`SimpleHIDWrite.exe`，找到`SimGEKI Config`字样开头的项目，选中
13. `ReportID`填写`AA`，在下面第一个空格填写任意内容，第二个空格内填写`A0`
14. 点选`Write`
15. 修改`segatools.ini`，`[aime]`下的`enable`配置为`0`
16. 修改设备的COM端口号为对应端口号
17. 进入游戏，重新校正摇杆

## 开发版固件

处于开发状态中的固件您暂时只能通过自行下载源代码并编译的方式取得，您可以参考以下两个项目来操作。

[SimGEKI固件主仓库](https://github.com/SimDevices-Project/SimGEKI)

[SimGEKI-IAP程序仓库](https://github.com/SimDevices-Project/SimGEKI-IAP)