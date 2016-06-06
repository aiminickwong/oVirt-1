# 转换
* Windows
  1. Win 7
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
