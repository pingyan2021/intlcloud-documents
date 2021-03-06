## 操作场景

腾讯云云服务器 Window Server 2008 R2 企业版 SP1 和 Windows Server 2012 R2 通过安装 Virtio 网卡驱动程序来优化虚拟化硬件的网络性能。腾讯云会持续改进网卡驱动，用于提升性能和解决故障。本文档将指导您如何更新 Virtio 网卡驱动，以及查看驱动版本。

## 前提条件

已登录腾讯云云服务器。

## 操作步骤

### 查看系统版本信息

您的系统版本信息可通过以下方法进行查看：
1. 登录云服务器，并对应实际使用的操作系统进行以下操作，打开“系统”窗口：
 - **Window Server 2008 R2 企业版 SP1**：在桌面右键单击【计算机】>【属性】。
 - **Windows Server 2012 R2**：打开“控制面板”窗口，并选择【系统】。
2. 在“系统”的【查看有关计算机的基本信息】中，即可查看到系统版本信息。   

### 更新 Virtio 网卡驱动方法
>! 更新过程中网络会闪断，更新前请检查是否会影响业务，更新后需要重启计算机。
>
1. 通过云服务器中的浏览器下载适用于 Window Server 2008 R2 和 Windows Server 2012 R2 的 VirtIO 网卡驱动安装文件。 
VirtIO 网卡驱动下载地址如下，请对应实际网络环境进行下载：
 - 公网下载地址：`http://mirrors.tencent.com/install/windows/virtio_64_10003.msi`
 - 内网下载地址：`http://mirrors.tencentyun.com/install/windows/virtio_64_10003.msi`
2. 下载完成后，双击启动安装程序，选择【典型】安装模式，单击【下一步】。
3. 在弹出的安全提示中，勾选【始终信任来自 “Tencent Technology（Shenzhen）Company Limited” 的软件】，单击【安装】。 
安装过程中，如果出现如下的弹出框，请选择【始终安装此驱动程序软件】。      
4. 根据提示，重新启动计算机，即可完成更新。


### 查看驱动版本

1. 单击<img src="https://main.qcloudimg.com/raw/87d894e564b7e837d9f478298cf2e292.png"  style="margin:0;"> ，在“运行”框中输入**ncpa.cpl**，并按 **Enter**。
2. 在打开的“网络连接”窗口中，右键单击“以太网”图标，选择【属性】。
3. 在弹出的“以太网 属性”窗口中，单击【配置】。
4. 在 “Tencent VirtIO Ethernet Adapter 属性”窗口中，选择【驱动程序】页签，即可查看当前驱动程序版本。


