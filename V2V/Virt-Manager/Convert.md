# 转换
Try running qemu directly without libvirt using this environment variable:
export LIBGUESTFS_BACKEND=direct
* 首先需要关闭即将被准换的虚拟机。

* 前提
  * 准备一台 virt-manager 虚拟机。
  * 在虚拟机所属的主机（也就是运行 `virt-v2v` 的主机）上安装如下软件包：
    ~~~ bash
    yum -y install virt-v2v
    ~~~
  * 如果您想要导出的虚拟机的操作系统是 `Windows` 的话，还需要在运行 `virt-v2v` 的主机上安装以下安装包：
    ~~~ bash
    yum -y install libguestfs-winsupport
    yum -y install virtio-win
    ~~~


> **注意**：
> 目前 virt-manager 虚拟机转换成 EayunOS 虚拟机的情况，只支持本地转换。

* Windows
  > **注意**：
  > 如果即将被转换的虚拟机的操作系统是 `Windows`，那么需要安装下面两个包：
    ~~~ bash
    yum -y install libguestfs-winsupport
    yum -y install virtio-win
    ~~~

  1. Win 7
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win7
     ~~~
  2. Win 8
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win8
     ~~~
  3. Win Server 2008 R2
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win2k8_R2
     ~~~
  4. Win Server 2008
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct
     virt-v2v -v -x -ic qemu+ssh://root@192.168.9.64/system -o ovirt -os 192.168.9.72:/exports/export --network eayunosmgmt win2k8
     ~~~
  5. Win Server 2003 R2
     ~~~ bash
     virt-v2v -v -x -ic qemu+ssh://root@192.168.9.64/system -o ovirt -os 192.168.9.72:/exports/export --network eayunosmgmt win2k3r2
     ~~~
  6. Win Server 2003
     ~~~ bash
     virt-v2v -v -x -ic qemu+ssh://root@192.168.9.64/system -o ovirt -os 192.168.9.72:/exports/export --network eayunosmgmt wink2k3
     ~~~

* Linux
  1. Suse
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt opensuse13.1
     ~~~
  2. CentOS
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt centos7.0
     ~~~
