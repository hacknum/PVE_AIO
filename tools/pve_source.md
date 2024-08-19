**功能介绍：**

1、更换PVE软件源、Debian源、LXC CT源、Ceph源及一键换源并更新系统等。源包括中科大源、清华大学源、南京大学源、阿里云源、腾讯源、华为源等；

2、设置设备的直通直通功能、虚拟机的核显及高清音频直通功能；

3、自定义虚拟机的扩展参数配置向导；

4、群晖虚拟机虚拟 USB 引导配置向导；

5、修改 PVE 概要信息栏，增加 CPU及线程频率、CPU及核心、主板等工作状态及温度，风扇转速，NVME及机械硬盘的型号、容量、温度、通电时间、IO状态等信息显示。其中NVME支持0E故障监测。UPS 信息

6、支持安装PVE暗黑主题(感谢Weilbyte)；

7、支持删除其他内核及头文件，也支持一键删除其他内核及头文件；

8、支持修改 CPU 工作模式；

9、支持自定义 CPU 主频限制区间或锁定主频。



P.S.

①个人编写的小工具，适用于特定机型个别场景，因此请勿与其他类似功能工具比较；

②不定期更新。个人较繁忙，有事留言，请勿急催；

③感谢支持。



其他

6.x内核，AMD 平台 CPU 频率限制无效，需要更新到6.5内核。非脚本BUG。Intel 平台无问题。



**pve_source 更新日志：**

2023.12.21 开发版

①更新核显直通方案参数，AMD 7840HS 等系列兼容 PVE 8.1.3 内核 6.5.11-7 实现一键核显直通。



2023.12.2 开发版

①增加 P-States 模式切换功能，可解决 6.x 内核 AMD 平台频率限制及 6.5 内核 CPU 工作模式较少的问题。

注：该功能在系统 IOMMU 定制向导菜单中列为可选项，同时提供独立功能选项；

②支持 ZFS 系统盘禁止网卡更名，使用原始 eth0~ethN 。



2023.12.1 开发版

①PVE 概要信息支持 AMD 780M 760M 核显温度显示；



2023.11.30 开发版

①PVE 系统配置 IOMMU、核显直通、核显 SR-IOV 调整为定制向导+推荐方案；

②更新设备 ID 及 更新 Intel 核显固件调整为独立选项菜单。



2023.11.24

①PVE 概要信息 IO 增加磁盘读写速度统计；

②PVE 概要信息区别硬盘和闪存信息。



2023.11.20

①PVE 概要信息增加预设方案条目。



2023.11.19.002-fix

①PVE 概要信息定制菜单修复当 CPU 核心超过 4 个时， CPU 核心温度不显示的 BUG ；

②PVE 概要信息定制菜单硬盘通电时间调整为可选项；

③PVE 概要信息定制菜单 NVME 硬盘寿命调整为剩余百分比；

④PVE 概要信息定制菜单修复 IO 信息导致界面无响应的 BUG ；

⑤PVE 概要信息定制菜单其他界面的改善或修复；



2023.11.19

①PVE 概要信息调整为定制菜单，自由定制显示条目。



2023.11.16

①一些 AMD 核显直通方面的兼容性改善。



2023.11.13.002

①修复 CPU 功率采样率过高导致 AMD 霄龙平台读数异常的BUG。



2023.11.13

①解决CPU 实时功率无法自启的 BUG。(P.S. 感谢网友[**yk**](https://bbs.x86pi.cn/user/control/home?userName=7RFV0qIJWttTROD9gFI))



2023.11.12

①概要信息新增 CPU 实时功率显示。



2023.11.10

①新增设置 Proxmox 系统通过 SLAAC 获取 IPv6 功能。



2023.11.07.002

①新增更新 PVE 的 Intel 核显固件的功能(在开启 Intel 核显 SR-IOV 功能最后一步)，以解决 N100 等设备 SR-IOV 开启失败的问题。

注：需自行处理 GitHub 连通性。



2023.11.07

①更新虚拟机核显直通向导，兼容市面多种主流方案；

②工具主页增加网络连通性判断和提示。



2023.11.02

①兼容PVE 8。支持旧版本升级固件；

②新增 UPS 信息显示。

③新增 CPU 工作模式显示；

④新增设置启动内核功能；

⑤新增 Intel 核显 SR-IOV 配置功能，(仅支持部分 Intel CPU，最高支持到 6.2.16-15 内核)，需配合安装 i915-sriov-dkms-dkms_6.1_all.deb 驱动；

⑥兼容 11 代以上核显直通配置。



2022.10.15

①增加 NTP 自动校时服务器设置;

②增加 移除 local-lvm 存储空间功能(具有危险性);

③增加 禁止 Proxmox 修改网卡名称功能(具有危险性)。



2022.10.12-002

①增加0E故障提示时，显示可用备用空间百分比；

②改善部分主机上的概要信息显示。

2022.10.12

①增加CPU主频限制功能。



2022.10.11

①论坛首发。



**示意图：**

![img](https://bbs.x86pi.cn/file/topic/2023-12-22/image/ccba370abce04d6c801d9df9463f6d38b2.png)



**Q&A**

**案例一 it87-dkms 依赖的 dksm 版本过低，如下图：**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/e33084df74394b46acca94be62c308d4b2.png)

原因分析：因为安装dkms前没有更新软件数据库。

解决办法：

①卸载 it87-dkms。命令：

```bash
apt purge it87-dkms
```

复制

或

```bash
dpkg -P it87-dkms
```

复制

②更新数据库和软件包，包括dkms会自动更新到最新。命令：

```bash
apt update && apt upgrade -y
```

复制

**案例二 apt 和 dpkg 安装工具故障。提示需要用 dpkg --configure -a 命令修复问题，如下图：**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/b1ba6c6e97e94d39bf4f8c08cf830230b2.png)

原因分析：CW 56-58 部分设备因 12V 5A 电源功率不够，在首次运行更新数据库、更新软件包、更新系统等任务时掉电关机，导致工具故障。此故障也会导致其他安装或卸载工具命令运行失败。

解决办法：换个高功率的好电源，开机修复后再进行其他任务。命令：

```bash
dpkg --configure -a
```

复制

**同理，基础工具安装失败也可能是由以上原因导致的，分别根据症状排查修复。**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/5ef35474892c48a99c4136d8b1893273b2.png)



**案例三 概要信息栏中，CPU温度信息空栏。如下图：**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/8dace039137c434ebc1debf27d008398b2.png)

原因分析：未按要求将 conf 文件上传至 /etc/sensors.d 路径且拷贝错了文件。

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/1a2f074ab8934942a0387a2154b6988cb2.png)

解决办法：将正确的 conf 文件上传至 /etc/sensors.d 路径，并删除无用文件。

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/c36f8217396c4060bd775cab9d0f6df8b2.jpg)



**案例四 vbios、群晖img等文件填写报错。如下图：**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/c34a322a2f0d4158aba1fd34ae6f9a7cb2.png)

原因分析：填写内容与实际文件路径、名称不一致

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/8a358d9027944a9fb2079e91a551e77ab2.png)

解决办法：按要求填写



**案例五 直通核显的虚拟机启动报错类型如下图：**

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/e43b9a2ecbd648c8b14e3c75bae12f72b2.png)

原因分析：未提前安装系统就直通核显。

解决办法：删除已直通的核显及高清音频PCI设备，再将显示改成默认，先安装好Windows 10及以下系统(不支持Windows 11等无法传统引导的系统)后。再通过 pve_source 添加直通核显，安装核显驱动，且将显示调整为none。重启PVE后通过 HDMI 或 DP 输出显示器。

![img](https://bbs.x86pi.cn/file/topic/2022-10-16/image/706d2f656f2041429e53193b7dc0657fb2.png)



**一、pve_source 下载地址及使用方法**

[附件一①：稳定版pve_source.tar.gz](https://bbs.x86pi.cn/file/topic/2023-11-28/file/01ac88d7d2b840cb88c15cb5e19d4305b2.gz)

[附件一②：开发版pve_source.tar.gz](https://bbs.x86pi.cn/file/topic/2024-01-06/file/24f723efc6ab4913b1f99c97a1d1a472b2.gz)

**使用方法：**

①下载后改名为 pve_source.tar.gz

②上传到 /root

③解压压缩包 tar zxvf pve_source.tar.gz

④执行程序./pve_source

或

**快速使用：**

稳定版

```bash
wget -q -O /root/pve_source.tar.gz 'https://bbs.x86pi.cn/file/topic/2023-11-28/file/01ac88d7d2b840cb88c15cb5e19d4305b2.gz' && tar zxvf /root/pve_source.tar.gz && /root/./pve_source
```

复制

开发版 (PVE 系统配置 IOMMU、核显直通、核显 SR-IOV 调整为定制向导+推荐方案)

```bash
wget -q -O /root/pve_source.tar.gz 'https://bbs.x86pi.cn/file/topic/2024-01-06/file/24f723efc6ab4913b1f99c97a1d1a472b2.gz' && tar zxvf /root/pve_source.tar.gz && /root/./pve_source
```

复制

![img](https://bbs.x86pi.cn/file/topic/2023-12-22/image/93bc7414e17e4d859ef83fb71902f2a7b2.png)



**二、传感器驱动下载地址及使用方法**

[附件二①(it87 系列传感器驱动，显示 PVE 风扇转速)：IT87传感器驱动_it87-dkms_1.0.63-1_all.deb](https://bbs.x86pi.cn/file/topic/2023-12-03/file/5434427fbfde4da7a71e654c3d178d17b2.deb)

[附件二②(nct 系列传感器驱动，显示 PVE 风扇转速)：NCT6687D传感器驱动_nct6687d-dkms_20231128-212556_all.deb](https://bbs.x86pi.cn/file/topic/2023-12-03/file/f0759a0dc7764194a62824e0b464c582b2.deb)

```bash
使用方法：
apt update && apt install -y pve-headers proxmox-headers-$(uname -r) dkms  ## PVE 8 安装 dkms 及头文件
apt update && apt install -y pve-headers pve-headers-$(uname -r) dkms      ## PVE 7 安装 dkms 及头文件
dpkg -i xxx.deb                                                            ## 安装 deb 驱动包，xxx.deb 改为包名称
reboot                                                                     ## 重启系统
```

复制



**三、核显直通文件下载地址及使用方法**

[附件三①(用于Intel 10代~14代核显直通)：Intel_10-14_Gop_Igd_vbios.rom](https://bbs.x86pi.cn/file/topic/2024-01-12/file/f9aacc8ac9694ed59d18a58a32aa6671b2.rom)

```bash
GitHub 1：https://github.com/tianocore/edk2
GitHub 2：https://github.com/cmd2001/build-edk2-gvtd
初编译：李晓流
重编译：Jazz，解决J4125花屏的 BUG

J4125 使用 OVMF+vbios_gvt_uefi.rom 或者合成单 rom 方案 HDMI 完美输出画面 BIOS 必选项(有些设备出厂已经预设，不用手调)：
Advanced - CSM Configuration - CSM Support - Enabled, Video - Legacy
J4125 核显直通必须同时黑名单 blacklist i915 与 blacklist snd_hda_intel 或将 VGA 与 Audio 的设备 ID 强行绑定到 vfio-pci 模块，否则高清音频设备会丢失且画面高宽比异常。
可使用Intel® 第 7 代至第 10 代处理器显示芯片 - Windows* 驱动
官方地址：https://www.intel.cn/content/www/cn/zh/download/776137/intel-7th-10th-gen-processor-graphics-windows.html
```

复制

[附件三②：J4125高清音频驱动包.zip](https://bbs.x86pi.cn/file/topic/2023-12-18/file/f585e4eac97a46ad9be5777b80e83ad6b2.zip)

```bash
说明：
①用于 J4125 核显直通后，解决高清音频设备无法通过 Intel 核显驱动安装音频驱动以致无法输出声音的问题(多见于虚拟 Win11 系统);
②包含三个驱动，全部都要安装才能解决问题;
③如未遇到上述问题，可不用安装本驱动包。
```

复制

[附件三③-1：AMD_Lucienne_Cezanne_Barcelo_Gop_vbios.rom](https://bbs.x86pi.cn/file/topic/2024-06-20/file/1c140cfeb9d046119e3ab0504e3397d3b2.rom)

```bash
说明：
用于 AMD 5500U 等 CPU 的 Lucienne 核显[1002:164c] 、5600U及5800U 等 CPU 的 Cezanne 核显[1002:1638] 、5825U 等 CPU 的 Barcelo 核显[1002:15e7]直通

更新日志：
2024.06.19
①更新 GOP Rev 2.23.0.17.10 Build Jan 14 2024.21:54:38。

2023.12.26
①更新 GOP Rev 2.20.0.17.10 Build Jul 12 2022 04:37:17；
②提高核显直通稳定性：黑屏、掉核显驱动、主机死机的情况有明显改善；响应速度有改善。
```

复制

[附件三③-2：AMD_Phoenix_Gop_vbios.rom](https://bbs.x86pi.cn/file/topic/2024-06-19/file/0f41a0e2143b4c83b4356ba1d1daf166b2.rom)

```bash
说明：
用于 AMD 7640 7840 7940 8845 等 CPU 的 Phoenix 780M 核显[1002:15bf]直通

更新日志：
2024.06.19
①更新 GOP Rev 3.8.8 Build Jan 11 2024.23:33:30。

2023.12.25
①更新 GOP Rev 3.8.5 Build Sep 15 2023 04:53:42；
②更新 vbios VER022.012.000.027.000001 Build 09/15/23,12:20:39；
③提高 GPU 游戏性能。
```

复制

[附件三③-3：AMD_Raphael_Gop_vbios.rom](https://bbs.x86pi.cn/file/topic/2024-06-19/file/0b30d69e217c4e7e8a8b8c8b608e3b81b2.rom)

```bash
说明：
用于 AMD 7950x 等 CPU 的 Raphael 核显[1002:164e]直通

更新日志：
2024.06.19
①更新 GOP Rev 3.8.8 Build Jan 11 2024.23:33:30。
```

复制

[附件三④：RadeonResetBugFixService v0.1.7.zip](https://bbs.x86pi.cn/file/topic/2023-12-22/file/26745696f47e4d2fae4b4cf139798e9fb2.zip)

```bash
GitHub：https://github.com/inga-lovinde/RadeonResetBugFix
原作者：inga-lovinde
Repack：Jazz，重新打包加入管理员权限批处理 bat 文件，便于一键安装
说明：
①用于改善 AMD 核显直通虚拟 Windows 系统 vendor reset BUG；
②原理：每次虚拟机内 Windows 系统重启或关机时，该服务会将核显及高清音频设备停用，下次启动虚拟机，进入系统后几十秒，该服务再启动核显及高清音频设备。
使用方法：
解压缩 RadeonResetBugFixService 文件夹到虚拟机 Windows 系统中任意路径；
双击 RadeonResetBugFixService.bat 批处理文件即可以管理员权限安装 Radeon Reset Bug Fix 服务并启动服务。
```

复制





**四、Intel 11 代及以上核显 SR-IOV 驱动下载地址及使用方法**

注意事项：之前用GitHub源码给PVE 6.2.16-15及以下内核安装过驱动的需要卸载老版本驱动，避免冲突。

a) 查看 dkms 状态；

```bash
dkms status
```

复制

b) 若有 i915-sriov-dkms/6.1，或者按第三方博主改过版本号的，如：i915-sriov-dkms/6.2；

c) 其中 i915-sriov-dkms 是模块名称，6.1 是模块版本。则卸载命令为：

```bash
dkms remove -m i915-sriov-dkms -v 6.1 --all
或
dkms remove i915-sriov-dkms/6.1 --all
```

复制

[附件四①：i915-sriov-dkms_6.1.11_all.deb](https://bbs.x86pi.cn/file/topic/2024-05-13/file/7f12279527104fb288c2383d4e141e0cb2.deb)

```bash
GitHub：https://github.com/strongtz/i915-sriov-dkms
用于 Gen 11 (如 i5-1135G7 的 Iris Xe 核显)、Gen12 (如 i7-1270p 的 Iris Xe 核显)及 Gen 13 (如 i5-13400 的 UHD 730 核显) SR-IOV
* 部分 Gen 11 核显 SR-IOV 失败可尝试使用 intel-i915-dkms 驱动
内核要求：适用于 PVE 6.2.16-16 及以上且 6.8 以下的内核
使用方法：
首次安装需安装两次。
安装过程中动态编译时间较长，需耐心等待，安装完成后需重启系统。
wget -q -O '/root/i915-sriov-dkms_6.1.11_all(PVE_6.2.16-16+).deb' 'https://bbs.x86pi.cn/file/topic/2024-05-13/file/7f12279527104fb288c2383d4e141e0cb2.deb' && dpkg -i '/root/i915-sriov-dkms_6.1.11_all(PVE_6.2.16-16+).deb'
```

复制

[附件四②：i915-sriov-dkms_6.1.11_all.deb](https://bbs.x86pi.cn/file/topic/2023-11-14/file/b14f8d40f19f4ec5a8878653950e3b24b2.deb)

```bash
GitHub：https://github.com/strongtz/i915-sriov-dkms
用于 Gen 11 (如 i5-1135G7 的 Iris Xe 核显)、Gen12 (如 i7-1270p 的 Iris Xe 核显)及 Gen 13 (如 i5-13400 的 UHD 730 核显) SR-IOV
* 部分 Gen 11 核显 SR-IOV 失败可尝试使用 intel-i915-dkms 驱动
内核要求：适用于 PVE 6.2.16-15 及以下内核
使用方法：
首次安装需安装两次。
安装过程中动态编译时间较长，需耐心等待，安装完成后需重启系统。
wget -q -O '/root/i915-sriov-dkms_6.1.11_all(PVE_6.2.16-15-).deb' 'https://bbs.x86pi.cn/file/topic/2023-11-14/file/b14f8d40f19f4ec5a8878653950e3b24b2.deb' && dpkg -i '/root/i915-sriov-dkms_6.1.11_all(PVE_6.2.16-15-).deb'
```

复制

[附件四③：intel-i915-dkms_1.24.1.19.240119.1.nodrm+i3-1_all.deb](https://bbs.x86pi.cn/file/topic/2024-05-13/file/594f60a1e29745a68d3c2f43626268dab2.deb)

```bash
GitHub(Intel 官方)：https://github.com/intel-gpu/intel-gpu-i915-backports
GitHub(适配及重打包)：https://github.com/MoetaYuko/intel-gpu-i915-backports
* 用于 Intel 11 代及以后各代核显直接使用 PVE 硬件解码、转码
* 用于 Intel 11 代及以后各代核显 SR-IOV 后分配 VFs 给虚拟群晖并在虚拟系统中调用 VF 实现硬件转码及解码；
* 用于部分 Gen 11 核显 SR-IOV 后分配 VFs 给虚拟 Windows 并在虚拟系统中调用 VF 实现硬件转码及解码；
* 不能用于 Gen12，如 i7-1270p 的 Iris Xe 核显或 Gen 13，如 i5-13400 的 UHD 730 核显 SR-IOV 后分配 VFs 给虚拟 Windows 并在虚拟系统中调用 VF 实现硬件转码及解码；
内核要求：待数据反馈
使用方法：
首次安装需安装两次。
安装过程中动态编译时间较长，需耐心等待，安装完成后需重启系统。
① 先安装基础依赖、头文件并更新核显固件后再安装本驱动 deb ：apt install -y flex bison
② wget -q -O '/root/intel-i915-dkms_1.24.1.19.240119.1.nodrm+i3-1_all.deb' 'https://bbs.x86pi.cn/file/topic/2024-05-13/file/594f60a1e29745a68d3c2f43626268dab2.deb' && dpkg -i '/root/intel-i915-dkms_1.24.1.19.240119.1.nodrm+i3-1_all.deb'
```

复制



**五、PVE 系统 Intel 核显固件下载地址及使用方法**

[附件五：intel-gpu-firmware_20231108_001.tar.gz](https://bbs.x86pi.cn/file/topic/2023-11-08/file/bb05958d54484ffbb6cb0be85b7dc46fb2.gz)

```bash
GitHub：https://github.com/intel-gpu/intel-gpu-firmware
用于更新 PVE 系统 Intel 平台的核显固件
使用方法：
pve_source 已集成通过 GitHub 地址在线更新。若网络连接不佳，可使用本方法更新
wget -q -O /root/intel-gpu-firmware.tar.gz 'https://bbs.x86pi.cn/file/topic/2023-11-08/file/bb05958d54484ffbb6cb0be85b7dc46fb2.gz' && mkdir -p /lib/firmware/updates/i915/ && tar -zxvf /root/intel-gpu-firmware.tar.gz -C /lib/firmware/updates/i915/
```

复制



**六、Intel 11代及以后核显 SR-IOV 使用方法**

①开启 BIOS 相关选项

```bash
Advanced - CPU Configuration - Intel (VMX) Virtualization Technology - Enabled
Chipset - System Agent (SA) Configuration - VT-d - Enabled
Chipset - System Agent (SA) Configuration - Above 4GB MMIO BIOS assignment - Enabled
```

复制

②使用 pve_source 开启 Intel 核显 SR-IOV 的 PVE 系统基础配置

③更新到最新系统内核 PVE 8.0 proxmox-kernel-6.2.16-16-pve 及以上版本，重启后确保当前运行内核是最新内核

```bash
apt update && apt dist-upgrade -y
```

复制

④查看当前内核

```bash
uname -r
```

复制

⑤更新 PVE 系统的 Intel 核显固件

⑥安装 dkms 及头文件

```bash
apt update && apt install -y pve-headers proxmox-headers-$(uname -r) dkms  ## PVE 8 安装 dkms 及头文件
apt update && apt install -y pve-headers pve-headers-$(uname -r) dkms      ## PVE 7 安装 dkms 及头文件
```

复制

⑦重启系统(非常重要！！！)

```bash
reboot
```

复制

⑧安装 SR-IOV 的 dkms deb 驱动包(安装过程中动态编译时间较长，需耐心等待)，安装完成后重启系统

⑨使用 pve_source 的就目标虚拟机进行 SR-IOV 配置向导



**七、其他文件**

[附件六：r8125-dkms_9.013.02-1_all.deb](https://bbs.x86pi.cn/file/topic/2024-05-13/file/66999143c76144bd989c711d1dd16853b2.deb)

```bash
Realtek RTL8125 2.5GbE 网卡驱动
原作者：Gzxhwq
Repack：Jazz，根据 2.5G/5G Ethernet LINUX driver r8125 for kernel up to 6.4 源码重新打包且降低 dkms 版本要求，以兼容 PVE 7

更新日志：
2024.05.13
①更新 9.013.02 。

安装驱动并重启系统
本驱动通过 alias 地址自动适配 r8125 网卡，通常无需手动屏蔽 r8169 模块。具体可通过 lspci -Dnnk 观察驱动的依赖模块
如依赖模块仍是 r8169，则手动将 /etc/modprobe.d/r8125-dkms.conf 中 #blacklist r8169 左侧的注释符 #删除并执行 update-initramfs -u -k all，再重启系统即可
①
apt update && apt install -y pve-headers proxmox-headers-$(uname -r) dkms  ## PVE 8 安装 dkms 及头文件
apt update && apt install -y pve-headers pve-headers-$(uname -r) dkms      ## PVE 7 安装 dkms 及头文件
②
dpkg -i r8125-dkms_9.013.02-1_all.deb
```

复制

![img](https://bbs.x86pi.cn/file/topic/2023-12-03/image/8df40fd1ff624858a167fd68b05c022db2.png)