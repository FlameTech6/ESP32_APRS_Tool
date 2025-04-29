# 语言 / Languages

[简体中文](README-ZH-CN.md) | 
[English](../README.md)

---

# ESP32 APRS Tool 项目

ESP32 APRS Tool 是一个为乐鑫ESP32微处理器实现的互联网网关(IGate)/数字中继(DiGi)/追踪器(Tracker)/气象站(WX)/遥测(TLM)设备，内置TNC功能。Fork自[ESP32APRS](https://github.com/nakhonthai/ESP32APRS_Audio)项目

## 功能特性

* 支持硬件: ESP32DR简易版, ESP32DR标准版, 其他DIY设备
* 支持射频模块: SA8x8/FRS VHF/UHF/350型号
* 支持APRS互联网网关(IGATE)
* 支持APRS数字中继(DIGI)
* 支持APRS追踪器(TRACKER)
* 支持外置GNSS模块（可选UART0-2或TCP客户端）
* 支持外置TNC模块（可选UART0-2或八重洲数据包协议）
* 支持固定位置的APRS IGATE/DIGI/WX功能（可通过GNSS获取移动位置）
* 基于Visual Studio Code + Platform IO的ESP-Arduino开发环境
* 支持AFSK 1600/1800Hz 300bps（用于HF电台）
* 支持Bell202 1200bps AFSK（用于VHF/UHF电台）
* 实现软件调制解调器，支持编解码
* 支持信息监控显示与统计
* 支持多站Wi-Fi或Wi-Fi接入点模式
* 支持网页服务配置与系统控制
* 支持IGATE/DIGI/显示界面的数据包收发过滤
* 支持音频滤波器（BPF, HPF）
* 支持WireGuard VPN
* 支持全球时区设置
* 支持网页服务登录认证
* 通过LED和OLED显示屏显示收发数据包状态
* 多制式调制解调器（代码源自[vp-digi](https://github.com/sq8vps/vp-digi)项目）:
  * 1200波特 Bell202 AFSK（VHF标准）
  * 300波特 Bell103 AFSK（HF标准）
  * 9600波特 G3RUH GFSK（UHF标准）
  * 1200波特 V.23 AFSK
* 模拟-数字忙闲信道检测（载波侦听）
* AX.25编解码器
* FX.25（带纠错的AX.25）编解码器，完全兼容[Direwolf](https://github.com/wb2osz/direwolf)和[UZ7HO Soundmodem](http://uz7.ho.ua/packetradio.htm)

## 硬件截图
![esp32dr简易版](../image/ESP32DR_Simple_Test.png) ![esp32dr_sa868](../image/ESP32DR_SA868_2.png)
![esp32dr_sa868电路板](../doc/ESP32DR_SA868/ESP32DR_SA868_Block.png)

## 硬件改装
![esp32dr_sql](../image/ESP32IGate_SQL.jpg)

## 网页服务截图
![仪表盘界面](../image/ESP32IGate_Screen_dashboard.png) ![iGate界面](../image/ESP32IGate_Screen_igate.png) \
![无线电界面](../image/ESP32IGate_Screen_radio.png) ![调制模式界面](../image/ESP32IGate_Screen_mod.png)

## ESP32DR_SA868模块
共享项目[链接](https://oshwlab.com/APRSTH/esp32sa818) \
原理图[下载](../doc/ESP32DR_SA868/ESP32DR_SA868_sch.pdf) \
PCB Gerber文件[下载](../doc/ESP32DR_SA868/ESP32DR_SA868_Gerber.zip)

## ESP32DR简易版

![esp32dr简易版3D模型](../image/ESP32DR_Simple_Model.png)

ESP32DR简易版是连接电台的小型接口板。

* PCB尺寸64x58mm
* 单面PCB设计
* RJ11六针接口连接电台

### 原理图

[![原理图](../image/ESP32DR_SimpleCircuit.png)](../image/ESP32DR_SimpleCircuit.png)

### CAD资料

Gerber文件[下载](../doc/Gerber_ESP32DR_Simple.zip)

PCB正片文件[下载](../doc/PCB_Bottom.pdf)

PCB负片文件[下载](../doc/PCB_Bottom_Invert.pdf)

PCB布局图[下载](../doc/PCB_Layout.pdf)

原理图PDF[下载](../doc/ESP32DR_Simple_Schematic.pdf)

### 物料清单

|元件编号|参数|描述|
|---|:---:|---|
|U1|ESP32开发板|DOIT ESP32 DEVKIT（ESP32模块）|
|RP2|1K|3362W可调电阻（调节输出音量）|
|RP1|10K|3362W可调电阻（调节输入音量）|
|RJ11|RJ11-6P6C|6针RJ11模块插座|
|R13,R12,R11,R5,R3,R9|1K|1/4W 1K电阻（色环：棕黑红）|
|R7,R18,R19|100Ω|1/4W 100Ω电阻（色环：棕黑黑）|
|R6,R2,R1|10K|1/4W 10k电阻（色环：棕黑橙）|
|R4|3K|1/4W 3k电阻（色环：橙黑红）|
|R10|33K|1/4W 33K电阻（色环：橙橙橙）|
|Q1|2N3904|NPN晶体管（TO-92封装）|
|LED3|3.5mm LED|黄色LED（发射TX指示灯）|
|LED2|3.5mm LED|绿色LED（接收RX指示灯）|
|LED1|3.5mm LED|红色LED（电源指示灯）|
|L1|电感或跳线|隔离电感或跳线|
|C11|100uF/6.3V|电解电容|
|C4,C5|100nF|多层陶瓷电容|
|C6|470uF/10V|电解电容|
|C1,C3,C10|100nF或0.1uF|聚丙烯电容|
|C2|10nF或0.01uF|聚丙烯电容|
|D2,D1|1N4148|二极管（可用0.01uF电容替代）|

*R18和R19可不安装  
*D2,D1可用10nF多层陶瓷电容替代  
*若连接外接麦克风输入的电台，需将R4改为100K

可通过Shopee购买套件[点击](https://shopee.co.th/product/45191268/13373396785)

### 安装示意图

![安装图](../image/ESP32DR_SimpleLayout.png)

### 电台连接方式

根据电台型号需要焊接跳线。

![ESP32DR接口定义](../image/RJ12Pinout.png)

|制造商|RJ11-1 (+VIN)|RJ11-2 (SPK)|RJ11-3 (PTT)|RJ11-4 (GND)|RJ11-5 (MIC)|RJ11-6 (SQL)|
|---|---|---|---|---|---|---|
|Alinco DR-135(DB9)|-|2|7|5|9|1|
|IC2200(RJ45)|-|SP|4|5|6|-|
|FT-2800(RJ11)|-|SP|1|3|2|-|
|手持台麦克风线|-|SPK|PTT|GND|MIC|-|

Alinco DR-135(DB9)连接方式:

![Alinco](../image/ESP32DR_DR135.png)

ICOM IC2200(RJ45)连接方式:

![IC2200](../image/ESP32DR_IC2200.png)

Yaesu FT-2800(RJ11)连接方式:

![FT2800](../image/ESP32DR_FT2800.png)

手持电台连接方式:

![手持电台](../image/ESP32DR_HT.png)

![手持电台接收](../image/ESP32DR_RxOnly.png)

## ESP32IGate固件安装（首次操作所需，后续可通过网页升级）
1. 将USB线连接至ESP32模块
2. 下载固件并打开ESP32下载工具，设置固件路径：ESP32IGate_Vxx.bin（地址0x10000）、partitions.bin（地址0x8000）、bootloader.bin（地址0x1000）和boot.bin（地址0xe000）。如无法连接，请将GPIO0短接GND，点击START按钮完成后，按电源键或复位键（红色）
3. 连接WiFi热点SSID: ESP32IGate，浏览器访问http://192.168.4.1 密码: aprsthnetwork 可进行设置或连接路由器
4. 长按BOOT按钮>100ms进入TX模式，>10秒恢复出厂设置

![ESP32工具](../image/ESP32Tool.png)

## ESP32 Flash下载工具
https://www.espressif.com/en/support/download/other-tools

## PlatformIO快速入门

1. 安装[Visual Studio Code](https://code.visualstudio.com/)和[Python](https://www.python.org/)
2. 在VS Code扩展中搜索安装`PlatformIO`插件
3. 安装完成后需重启VS Code
4. 重启后选择左上角`文件`→`打开文件夹`→选择`ESP32APRS`目录
5. 点击`platformio.ini`文件，在platformio栏取消注释需要使用的示例行（确保只有一行有效）
6. 点击左下角(✔)符号编译
7. 通过USB连接开发板
8. 点击(→)上传固件并重新启动
9. 重启后显示监控界面并重新配置

## APRS服务器服务

- T2THAI的APRS服务器[aprs.dprns.com:14580](http://aprs.dprns.com:14501)，CBAPRS服务器[aprs.dprns.com:24580](http://aprs.dprns.com:24501)
- T2THAI的ampr主机[aprs.hs5tqa.ampr.org:14580](http://aprs.hs5tqa.ampr.org:14501)
- APRS地图服务[http://aprs.dprns.com](http://aprs.dprns.com)

## ESP32 Flash下载工具
https://www.espressif.com/en/support/download/other-tools

## 特别说明
本项目仅实现APRS文本(TNC2原始格式)，不支持数据包中的空字符(0x00)。

---

以下为原项目的相关信息

---

## 原项目开发者信息

- 作者: Somkiat Nakhonthai
- 呼号: HS5TQA,Atten,Nakhonthai
- 国家: 泰国,曼谷
- Github: [https://github.com/nakhonthai](https://github.com/nakhonthai)
- Youtube: [https://www.youtube.com/@HS5TQA](https://www.youtube.com/@HS5TQA)
- TikTok: [https://www.tiktok.com/@hs5tqa](https://www.tiktok.com/@hs5tqa)
- Facebook: [https://www.facebook.com/atten](https://www.facebook.com/atten)
- Telegram: [https://t.me/APRSTH](https://t.me/APRSTH)
- TelegramID: @HS5TQA
- 微信ID: HS5TQA

## 原项目作者捐赠与支持链接

可通过[github赞助](https://github.com/sponsors/nakhonthai)支持原项目ESP32APRS的开发。\
如需捐赠硬件支持APRS移植开发，请[联系我们](https://www.facebook.com/atten)。\
<a href="https://www.paypal.me/0hs5tqa0"><img src="https://github.com/nakhonthai/ESP32IGate/raw/master/blue.svg" height="40"></a>

## 致谢与参考

- nakhonthai的ESP32APRS项目[ESP32APRS](https://github.com/nakhonthai/ESP32APRS_Audio)(此为本项目的原项目)

- amedes的ESP32TNC项目[ESP32TNC](https://github.com/amedes/ESP32TNC)
- markqvist的LibAPRS库[LibAPRS](https://github.com/markqvist/LibAPRS)
