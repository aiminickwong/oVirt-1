# virt-v2v —— 将其他 hypervisor 上的虚拟机转换为基于 hypervisor 为 KVM 的虚拟机。
## 概要
   ~~~ bash
   # VMware ESXi 虚拟机
   virt-v2v -ic vpx://vcenter.example.com/Datacenter/ESXi_IP VMware_vm
   virt-v2v -ic vpx://vcenter.example.com/Datacenter/ESXi_IP VMware_vm -o ovirt -os Eayun.nfs:/storage_domain.example/exportdomain --network eayunosmgmt
   virt-v2v -i libvirtxml guest-domain.xml -o local -os /var/tmp
   virt-v2v -i disk disk.img -o local -os /var/tmp
   virt-v2v -i disk disk.img -o glance
   virt-v2v -ic qemu:///system qemu_guest --in-place
   ~~~
## 描述
## 输入输出模式
## 实例
### 将 VMware vCenter server 的虚拟机转换为本地 libvirt 虚拟机
### 将 VMware vCenter server 的虚拟机转换为 oVirt 的虚拟机
### 将磁盘镜像转换为 OpenStack 中的 glance
### Convert disk image to disk image
## 支持的母体？
### Hypervisors（Input）
### Hypervisors（Output）
### 虚拟管理系统（Output）
### Guests
### Guest firmware
## 选项
## Xen 半虚拟化虚拟机
## 开启 virtio
## RHEL4
### SELinux relabel appears to hang forever
## Windows
### Windows >= 8 Fast Startupis incompatible with virt-v2v
### Boot failure: 0x0000007B
### OpenStack and Windows reactivation
## UEFI
## 网络和网桥
## Input from vmware vcenter server
##
