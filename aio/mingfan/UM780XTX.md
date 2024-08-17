# UM780XTX AIO方案 BY Gr4v8l

以下内容分享仅为个人方案，**仅供参考**！且作者还处于学习阶段，如有**设计缺陷**或**操作错误**之处，**欢迎[联系作者](https://github.com/gr4v8l)指正**！

## 后选配置

- 内存：64G
- 主硬盘：三星970EVO Plus 1T
- 副硬盘：致态Ti600 4T

## 方案用途

- iKuai（主路由）
- iStoreOS（提供科学分流）
- AdGuard Home（提供高效的DNS解析）
- TrueNAS Core（统一管理，提供所有Docker服务的存储）
- Docker（LXC踩坑中，待补充）
- HomeAssistant（智能家居聚合，提供米家等设备桥接进HomeKit家庭的能力）

## 网络规划

- iKuai（10.0.0.1）
- iStoreOS（10.0.0.2）
- PVE（10.0.0.3）
- AdGuard Home（10.0.0.4）
- Docker（10.0.0.5）
- TrueNAS Core（10.0.0.6）

- HomeAssistant（10.0.0.7）

## iKuai部署

### 配置参数

- 方式：虚拟机
- 镜像：[官方下载](https://www.ikuai8.com/component/download)
- CPU：4核
- 内存：4G
- 磁盘：10G

## iStoreOS部署

### 配置参数

- 方式：虚拟机
- 镜像：[官方下载](https://fw.koolcenter.com/iStoreOS/)
- CPU：4核
- 内存：2G
- 磁盘：img镜像直接加载

## AdGuard Home部署

### 配置参数

- 方式：LXC容器
- CT模板：centos-9
- CPU：2核
- 内存：2G / 交换内存：1G
- 磁盘：5G

## TrueNAS Core部署

### 配置参数

- 方式：虚拟机
- 镜像：[官方下载](https://www.truenas.com/download-truenas-core/)
- CPU：8核
- 内存：16G
- 磁盘：32G

## Docker部署

### 配置参数

- 方式：LXC容器
- CT模板：debian-12
- CPU：8核
- 内存：32G / 交换内存：16G
- 磁盘：128G

