# virt-v2v —— 将其他 hypervisor 上的虚拟机转换为基于 hypervisor 为 KVM 的虚拟机。
## 概要
~~~ bash
# VMware ESXi 虚拟机
virt-v2v -ic vpx://vcenter.example.com/Datacenter/ESXi_IP VMware_vm
virt-v2v -ic vpx://vcenter.example.com/Datacenter/ESXi_IP VMware_vm -o ovirt -os Eayun.nfs:/storage_domain.example/exportdomain --network eayunosmgmt
~~~
