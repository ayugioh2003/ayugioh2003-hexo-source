---
title: 目前電腦上所安裝的程式
date: 2016-10-26 01:36:56
categories: 軟體
tags:
- Software
- 整理
---

![來源:http://www.unitech.com.au/?p=4323](/images/20161026software.jpg)

本文將記錄我安裝的電腦軟體

<!-- more -->

---

<!-- toc -->

- [碎碎唸](#碎碎唸)
	- [先整理一些能查看安裝軟體的指令](#先整理一些能查看安裝軟體的指令)
	- [記錄神奇的指令](#記錄神奇的指令)
- [軟體：其他](#軟體其他)
	- [Atom](#atom)
	- [Chrome](#chrome)
- [時間快照](#時間快照)
	- [2016.10.26](#20161026)
- [參考連結](#參考連結)

<!-- tocstop -->
---


# 碎碎唸

工欲善其事，必先利其器。這邊簡單的記錄一些指令

## 先整理一些能查看安裝軟體的指令

要記錄安裝的軟體，用 cmd 來查看也是很合理的

- 用 cmd 的話

```sh
WMIC
product get name,version
```
- 用 PowerShell 的話

```bash
Get-WmiObject -Class Win32_Product | Select-Object -Property Name
```

## 記錄神奇的指令

既然用了 cmd 記錄安裝的軟體，那用 cmd 來安裝軟體也是很合理的

- 透過 cmd 安裝軟體

```bash
# 查看
clist Name

# 安裝
choco install Name
```

- 快速打開有管理員權限的 cmd or PowerShell
  - 方法一
    1. 按一下 `Win` 鍵
    2. 鍵入想開啟程式的前幾個字
    3. 出現目標程式後，鍵入 `Ctrl + Shift + Enter`
  - 方法二
    1. `Win + X`
    2. `A`

---

# 軟體：其他

暫時還沒有想到好的分類方式，所以全部的軟體都是 others XD

## Atom

Coding 碼字的好夥伴。前端的生活工具。已新增

- Atom Package 篇

## Chrome

居家旅行，必備好軟件。之後會再新增

- 附加元件篇
- Stylish 與 TemporMonkey 篇
---

# 時間快照
## 2016.10.26

Name                                                                                                        Version
Windows Installer Clean Up                                                                                  3.00.00.0000
中華郵政 TRUSTATM Plugin                                                                                    1.1.39
PxMergeModule                                                                                               1.00.0000
Microsoft Application Error Reporting                                                                       12.0.6015.5000
Microsoft Office Professional Plus 2010                                                                     14.0.7015.1000
Microsoft Office OneNote MUI (Chinese (Traditional)) 2010                                                   14.0.7015.1000
Microsoft Office Office 32-bit Components 2010                                                              14.0.7015.1000
Microsoft Office Shared 32-bit MUI (Chinese (Traditional)) 2010                                             14.0.7015.1000
Microsoft Office InfoPath MUI (Chinese (Traditional)) 2010                                                  14.0.7015.1000
Microsoft Office Access MUI (Chinese (Traditional)) 2010                                                    14.0.7015.1000
Microsoft Office Excel MUI (Chinese (Traditional)) 2010                                                     14.0.7015.1000
Microsoft Office PowerPoint MUI (Chinese (Traditional)) 2010                                                14.0.7015.1000
Microsoft Office IME (Chinese (Traditional)) 2010                                                           14.0.7015.1000
Microsoft Office IME (Chinese (Traditional)) 2010                                                           14.0.7015.1000
Microsoft Office Publisher MUI (Chinese (Traditional)) 2010                                                 14.0.7015.1000
Microsoft Office Outlook MUI (Chinese (Traditional)) 2010                                                   14.0.7015.1000
Microsoft Office Groove MUI (Chinese (Traditional)) 2010                                                    14.0.7015.1000
Microsoft Office Word MUI (Chinese (Traditional)) 2010                                                      14.0.7015.1000
Microsoft Office Proofing (Chinese (Traditional)) 2010                                                      14.0.7015.1000
Microsoft Office Shared MUI (Chinese (Traditional)) 2010                                                    14.0.7015.1000
Microsoft Office Proof (Chinese (Traditional)) 2010                                                         14.0.7015.1000
Microsoft Office Proof (English) 2010                                                                       14.0.7015.1000
Microsoft Office 2010                                                                                       14.0.4763.1000
Microsoft DCF MUI (Chinese (Traditional)) 2016                                                              16.0.4266.1001
Microsoft Office Professional Plus 2016                                                                     16.0.4266.1001
Microsoft OneNote MUI (Chinese (Traditional)) 2016                                                          16.0.4266.1001
Microsoft Office 32-bit Components 2016                                                                     16.0.4266.1001
Microsoft Office Shared 32-bit MUI (Chinese (Traditional)) 2016                                             16.0.4266.1001
Microsoft Office OSM MUI (Chinese (Traditional)) 2016                                                       16.0.4266.1001
Microsoft Office OSM UX MUI (Chinese (Traditional)) 2016                                                    16.0.4266.1001
Microsoft InfoPath MUI (Chinese (Traditional)) 2016                                                         16.0.4266.1001
Microsoft Access MUI (Chinese (Traditional)) 2016                                                           16.0.4266.1001
Microsoft Excel MUI (Chinese (Traditional)) 2016                                                            16.0.4266.1001
Microsoft PowerPoint MUI (Chinese (Traditional)) 2016                                                       16.0.4266.1001
Microsoft Publisher MUI (Chinese (Traditional)) 2016                                                        16.0.4266.1001
Microsoft Outlook MUI (Chinese (Traditional)) 2016                                                          16.0.4266.1001
Microsoft Groove MUI (Chinese (Traditional)) 2016                                                           16.0.4266.1001
Microsoft Word MUI (Chinese (Traditional)) 2016                                                             16.0.4266.1001
Microsoft Skype for Business MUI (Chinese (Traditional)) 2016                                               16.0.4266.1001
Microsoft Office Proofing (Chinese (Traditional)) 2016                                                      16.0.4266.1001
Microsoft Office Shared MUI (Chinese (Traditional)) 2016                                                    16.0.4266.1001
Microsoft Office 校訂工具 2016 - 繁體中文                                                                   16.0.4266.1001
Microsoft Office Proofing Tools 2016 - English                                                              16.0.4266.1001
Raccolta foto di Windows Live                                                                               15.4.3502.0922
MSXML 4.0 SP3 Parser (KB2758694)                                                                            4.30.2117.0
Microsoft Visual C++ 2008 Redistributable - x64 9.0.30729.4148                                              9.0.30729.4148
Microsoft_VC90_CRT_x86                                                                                      1.00.0000
Microsoft Visual C++ 2008 Redistributable - x64 9.0.21022                                                   9.0.21022
Microsoft Visual C++ 2010  x64 Redistributable - 10.0.40219                                                 10.0.40219
Microsoft_VC80_CRT_x86_x64                                                                                  8.0.50727.4053
Microsoft Visual Studio 2010 Tools for Office Runtime (x64) Language Pack - CHT                             10.0.50903
Microsoft SQL Server 2005 Compact Edition [ENU]                                                             3.1.0000
Microsoft Visual C++ 2010  x86 Redistributable - 10.0.40219                                                 10.0.40219
Microsoft_VC80_MFC_x86                                                                                      8.0.50727.4053
Python 2.7.8                                                                                                2.7.8150
Microsoft Visual C++ 2013 x86 Minimum Runtime - 12.0.21005                                                  12.0.21005
Intel(R) Chipset Device Software                                                                            10.0.24
Microsoft Visual C++ 2013 x86 Additional Runtime - 12.0.21005                                               12.0.21005
Microsoft_VC80_MFCLOC_x86                                                                                   8.0.50727.4053
Broadcom Gigabit NetLink Controller                                                                         14.6.1.2
Chrome Remote Desktop Host                                                                                  52.0.2743.48
IBM SPSS Statistics 21                                                                                      21.0.0.0
PDF Settings CS5                                                                                            10.0
Device Simulation Framework 1.0.1                                                                           1.0.1
Windows Live Communications Platform                                                                        15.4.3502.0922
Acrobat.com                                                                                                 1.6.65
Microsoft Visual Studio 2010 Tools for Office Runtime (x64)                                                 10.0.50908
Microsoft_VC90_MFC_x86_x64                                                                                  1.00.0000
Java 8 Update 31                                                                                            8.0.310
Java 8 Update 25                                                                                            8.0.250
Java 7 Update 71 (64-bit)                                                                                   7.0.710
Java 8 Update 25 (64-bit)                                                                                   8.0.250
Java SE Development Kit 7 Update 71 (64-bit)                                                                1.7.0.710
Bluetooth Win7 Suite (64)                                                                                   7.2.0.56
Windows Live Argazki Galeria                                                                                15.4.3502.0922
Adobe Media Player                                                                                          1.8
Microsoft_VC80_MFC_x86_x64                                                                                  8.0.50727.4053
Backup Manager V3                                                                                           3.0.0.85
Microsoft .NET Framework 4.5.2                                                                              4.5.51209
NVIDIA PhysX                                                                                                9.10.0514
Microsoft Visual C++ 2008 Redistributable - x64 9.0.30729.6161                                              9.0.30729.6161
Adobe Acrobat XI Pro                                                                                        11.0.00
G*Power 3.1.9.2                                                                                             3.1.92
EndNote X7                                                                                                  17.1.0.7705
Microsoft Visual C++ 2008 Redistributable - x86 9.0.30729.6161                                              9.0.30729.6161
MSXML 4.0 SP2 (KB973688)                                                                                    4.20.9876.0
Oracle VM VirtualBox 4.3.12_ZZZZ                                                                            4.3.12
tools-winPre2k                                                                                              9.6.1.1379776
tools-netware                                                                                               9.6.1.1379776
ChocolateyGUI 0.13.2.0                                                                                      0.13.2.0
D3DX10                                                                                                      15.4.2368.0902
Microsoft Visual C++ 2012 x64 Additional Runtime - 11.0.61030                                               11.0.61030
Evernote Sticky Notes                                                                                       1.5.9
Paragon Backup and Recovery? 14 Home                                                                       90.00.0003
Microsoft_VC80_MFCLOC_x86_x64                                                                               80.50727.4053
Node.js                                                                                                     4.4.3
Vedio WebCam                                                                                                4.00.0000
Renesas Electronics USB 3.0 Host Controller Driver                                                          2.0.26.0
PetWings                                                                                                    1.2.0
Microsoft_VC80_ATL_x86                                                                                      8.0.50727.4053
EverCamPPT                                                                                                  1.0.0
Google Drive                                                                                                1.31.2873.2758
Microsoft_VC80_CRT_x86                                                                                      8.0.50727.4053
Google Update Helper                                                                                        1.3.25.11
7-Zip 9.20 (x64 edition)                                                                                    9.20.00.0
EAP-GTC-x64                                                                                                 2.04.0000
Google Update Helper                                                                                        1.3.31.5
tools-linux                                                                                                 9.6.1.1379776
Python 2.7 pygame-1.9.1                                                                                     1.9.1
VMware Workstation                                                                                          10.0.1
MSVCRT                                                                                                      15.4.2862.0708
Dolby Advanced Audio v2                                                                                     7.2.7000.4
Adobe Community Help                                                                                        3.0.0
Microsoft DVD App Installation for Microsoft.WindowsDVDPlayer_2019.6.13291.0_neutral_~_ 8wekyb3d8bbwe (x64)  1.0.0.0
Podstawowe programy Windows Live                                                                            15.4.3502.0922
E-Prime 2.0 (2.0.8.22)                                                                                      2.0.08022
Microsoft_VC90_MFC_x86                                                                                      1.00.0000
Microsoft_VC80_ATL_x86_x64                                                                                  8.0.50727.4053
tools-solaris                                                                                               9.6.1.1379776
Intel(R) Driver Update Utility 2.0                                                                          2.0.0.29
Microsoft Visual C++ 2005 Redistributable                                                                   8.0.61001
Broadcom Card Reader Driver Installer                                                                       14.6.1.2
tools-windows                                                                                               9.6.1.1379776
Microsoft Visual C++ 2012 x64 Minimum Runtime - 11.0.61030                                                  11.0.61030
Microsoft_VC90_ATL_x86_x64                                                                                  1.00.0000
Microsoft Visual C++ 2008 Redistributable - x86 9.0.30729.4148                                              9.0.30729.4148
Microsoft_VC90_CRT_x86_x64                                                                                  1.00.0000
Microsoft Visual C++ 2008 Redistributable - x86 9.0.30729.17                                                9.0.30729
Microsoft Silverlight                                                                                       5.1.50428.0
tools-freebsd                                                                                               9.6.1.1379776
MSXML 4.0 SP2 (KB954430)                                                                                    4.20.9870.0
Adobe AIR                                                                                                   16.0.0.245
Evernote v. 6.0.6                                                                                           6.0.6.1769
Microsoft_VC90_ATL_x86                                                                                      1.00.0000
Microsoft Visual C++ 2008 Redistributable - x64 9.0.30729.17                                                9.0.30729
Experiment Builder 1.10.165                                                                                 1.10.165
Windows Live                                                                                                15.4.3502.0922
Java Auto Updater                                                                                           2.8.31.13
Python 3.4.4 (64-bit)                                                                                       3.4.4150
Costco Photo Batch Uploading Tool                                                                           1.0.11

---

# 參考連結

- [《電腦小技巧》如何將電腦中已安裝的軟體列出清單並儲存為文字檔 | 就是教不落 - 給你最豐富的 3C 資訊、教學網站](https://steachs.com/archives/3266)
- [用 wmic 建立已安裝軟體清單 | 簡睿隨筆 | 學習過程的紀錄與備忘](http://jdev.tw/blog/2487/wmic-product)
- [你是我的巧克力 - Chocolatey - 黑暗執行緒](http://blog.darkthread.net/post-2013-12-29-chocolatey.aspx)
- [使用管理者身分執行 cmd.exe - 黑暗執行緒](http://blog.darkthread.net/post-2015-04-17-cmdexe-runas-admin-in-win8.aspx)
