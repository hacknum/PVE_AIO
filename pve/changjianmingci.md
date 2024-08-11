## 常见名词

- **KVM (Kernel-based Virtual Machine)**：基于Linux内核的虚拟化技术，用于运行虚拟机。
- **LXC (Linux Containers)**：Linux容器技术，提供轻量级的虚拟化，允许多个隔离的Linux系统在同一台主机上运行。
- **pmxcfs (Proxmox Cluster File System)**：PVE特有的数据库驱动文件系统，用于在集群节点间同步配置文件。
- **HA (High Availability)**：高可用性，PVE支持基于Linux HA技术的多节点集群，提供资源监控和自动故障转移。
- **API (Application Programming Interface)**：PVE提供REST API，允许用户通过编程方式管理虚拟化环境。
- **Spice**：一种开源的远程桌面协议，用于连接虚拟机的图形界面。
- **Ceph**：一种分布式存储系统，PVE从5.x版本开始支持Ceph作为存储后端。
- **QinQ**：一种网络技术，允许在VLAN标签内嵌套另一个VLAN标签，PVE支持QinQ配置。
- **VXLAN (Virtual Extensible Local Area Network)**：一种覆盖网络技术，用于在不同网络中传输VLAN信息。
- **EVPN (Ethernet VPN)**：一种用于实现虚拟私有网络的以太网技术，PVE支持EVPN设置。