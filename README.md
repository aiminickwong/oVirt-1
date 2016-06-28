# V2V

## 说明
   * virt-v2v 可以对其他 Hypervisor 上运行的虚拟机（例如：VMware ESX(i)，KVM 或 Xen 虚拟化环境中的虚拟机）进行转换，进而运行在 EayunOS 虚拟化管理平台上。

## 前提条件
   * 在 EayunOS 上附加 NFS [导出域](http://docs.eayun.cn/zh-CN/EayunOS/4.1/html/administration-guide/EayunOS%20%E5%AD%98%E5%82%A8%E5%9F%9F/%E5%87%86%E5%A4%87_NFS_%E5%AD%98%E5%82%A8.html)。
   * Virt-Manager 平台
     1. 一台需要被转换的 `Virt-Manager` 中的虚拟机。
     2. 在**该虚拟机所属的主机**中安装以下包：
        * 虚拟机 OS 为 Windows：
          ~~~ bash
          yum -y install libguestfs-winsupport
          yum -y install virtio-win
          ~~~
 
        * 虚拟机 OS 为 Linux：
          ~~~ bash
          yum -y install virt-v2v
          ~~~
  
   * VMware ESX(i) 平台
     1. 一台需要被转换的 `ESX(i)` 中创建的虚拟机。
     2. 在**任意一台可以正常使用的机器**中安装以下包：
        * 虚拟机 OS 为 Windows：
          ~~~ bash
          yum -y install libguestfs-winsupport
          yum -y install virtio-win
          ~~~
 
        * 虚拟机 OS 为 Linux：
          ~~~ bash
          yum -y install virt-v2v
          ~~~
  
   

## 转换虚拟机
`virt-v2v` 命令可以对其他虚拟机监控程序（hypervisor）上运行的虚拟机进行转换，从而在 EayunOS 虚拟化管理平台上运行起来。想要在 EayunOS 管理平台上使用其他 Hypervisor 的虚拟机，分为一下两个步骤：
   1. `virt-v2v` 会自动打包虚拟机的磁盘文件和元数据，然后将它们上传到 EayunOS 管理平台的导出域中。
   2. 导入虚拟机到 EayunOS，详细过程参见：[http://docs.eayun.cn/zh-CN/EayunOS/4.1/html/administration-guide/%E8%99%9A%E6%8B%9F%E6%9C%BA/%E5%AF%BC%E5%85%A5%E5%92%8C%E5%AF%BC%E5%87%BA%E8%99%9A%E6%8B%9F%E6%9C%BA_t.html](http://docs.eayun.cn/zh-CN/EayunOS/4.1/html/administration-guide/%E8%99%9A%E6%8B%9F%E6%9C%BA/%E5%AF%BC%E5%85%A5%E5%92%8C%E5%AF%BC%E5%87%BA%E8%99%9A%E6%8B%9F%E6%9C%BA_t.html)。



