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
     ~~~ shell
     
     ~~~
  2. Win 8
  3. Win Server 2008 R2
     ~~~ shell
     virt-v2v -v -x -ic vpx://administrator%40eayunos.com@192.168.9.77/Datacenter0/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt Win2008_R2
     ~~~
  4. Win Server 2008
  5. Win Server 2003 R2
  6. Win Server 2003

* Linux
  1. Suse
  2. RedHat
  3. CentOS
     ~~~ shell
     virt-v2v -v -x -ic vpx://administrator%40eayunos.com@192.168.9.77/Datacenter0/192.168.9.55?no_verify=1 -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt CentOS7
     ~~~
