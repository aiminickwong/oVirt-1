# 转换
* 首先需要关闭即将被准换的虚拟机。

* Windows
  > **注意**：
  > 如果即将被转换的虚拟机的操作系统是 `Windows`，那么需要安装下面两个包：
    ~~~ bash
    yum -y install libguestfs-winsupport
    yum -y install virtio-win
    ~~~

  1. Win 7
     ~~~ bash

     ~~~
  2. Win 8
     ~~~ bash

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
     ~~~
  6. Win Server 2003
     ~~~ bash
     ~~~

* Linux
  1. Suse
  2. RedHat
  3. CentOS
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt centos7.0
     ~~~
