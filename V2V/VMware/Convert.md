# 转换
* 首先需要关闭即将被准换的虚拟机。

* Windows
  > **注意**：
  > 如果即将被转换的虚拟机的操作系统是 `Windows`，那么需要安装下面两个包：
    ~~~ bash
    yum -y install libguestfs-winsupport
    yum -y install virtio-win
    ~~~
  > 由于当前 libvirt 还无法处理 json，所以请您在转换之前务必执行 export LIBGUESTFS_BACKEND=direct，不然会提示如下内容：
    ~~~ bash
    [zhangyaqi@localhost VMware]$ virt-v2v -v -x -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt Win2k3
    virt-v2v: libguestfs 1.30.6 (x86_64)
    [   0.0] Opening the source -i libvirt -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 Win2k3
    input_libvirt_vcenter_https: source: scheme vpx server 192.168.9.91
    virt-v2v: error: because of libvirt bug 
    https://bugzilla.redhat.com/show_bug.cgi?id=1134592 you must set this 
    environment variable:

    export LIBGUESTFS_BACKEND=direct

    and then rerun the virt-v2v command.
    ~~~
  1. Win 2003
     ~~~ bash
     # 注意: V2V 必须要在 root 下执行
     [root@localhost ~]# virt-v2v -v -x -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt Win2k3
     virt-v2v: libguestfs 1.30.6 (x86_64)
     [   0.0] Opening the source -i libvirt -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 Win2k3
     input_libvirt_vcenter_https: source: scheme vpx server 192.168.9.91
     为 administrator@vsphere.local 输入 192.168.9.91's 密码: # 输入 vSphere Web Client 的密码
     Enter host password for user 'administrator@vsphere.local': # 还要再输入一次
     ... # 漫长的执行过程，注意这里的 -v -x 是进入 debug 模式，所以输出较多。当然您也可以不加 -v -x 选项。
     ~~~
  2. Win Server 2008 R2
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct
     virt-v2v -v -x -ic vpx://administrator%40eayunos.com@192.168.9.77/Datacenter0/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt Win2008_R2
     ~~~
  3. Win Server 2008
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct

     ~~~
  4. Win Server 2003 R2
  5. Win Server 2003
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct
     virt-v2v -v -x -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt Win2k3
     ~~~
  6. Win 7
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct
     virt-v2v -v -x -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win7
     ~~~
  7. Win 8
     ~~~ bash
     ~~~


* Linux
  1. Suse
     ~~~ bash

     ~~~
  2. CentOS
     ~~~ bash
     export LIBGUESTFS_BACKEND=direct
     virt-v2v -v -x -ic vpx://administrator%40eayunos.com@192.168.9.77/Datacenter0/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt CentOS7
     ~~~
