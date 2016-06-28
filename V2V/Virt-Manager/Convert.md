# 转换
> **注意**：
> 目前 virt-manager 虚拟机转换成 EayunOS 虚拟机的情况，只支持本地转换。

* 开始转换：
  首先需要关闭即将被准换的虚拟机。支持转换的虚拟机操作系统：
  * Windows 7 / 8
  * Windows 2003 R2 / 2008 R2
  * Windows 2003 / 2008
  * CentOS / RedHat
  * Suse

  > **注意**：
  > 由于当前 libvirt 还无法处理 json，所以请您在转换之前务必执行 `export LIBGUESTFS_BACKEND=direct`，不然会提示如下
    ~~~ bash
    [zhangyaqi@localhost VMware]$ virt-v2v -v -x -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/
    virt-v2v: libguestfs 1.30.6 (x86_64)
    [   0.0] Opening the source -i libvirt -ic vpx://administrator%40vsphere.local@192.168.9.91/Datacenter/192.16
    input_libvirt_vcenter_https: source: scheme vpx server 192.168.9.91
    virt-v2v: error: because of libvirt bug
    https://bugzilla.redhat.com/show_bug.cgi?id=1134592 you must set this
    environment variable:

    export LIBGUESTFS_BACKEND=direct

    and then rerun the virt-v2v command.
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
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win2k8
     ~~~
  5. Win Server 2003 R2
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt win2k3r2
     ~~~
  6. Win Server 2003
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt wink2k3
     ~~~

  7. Suse
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt opensuse13.1
     ~~~
  8. CentOS
     ~~~ bash
     virt-v2v -v -x -o ovirt -os 192.168.2.56:/home/ply/workspace/storage/Export --network eayunosmgmt centos7.0
     ~~~

* 参数说明：
  * '-v(--verbose)'：可以看到 bebug 的信息。
  * '-x'：追踪 libguestfs API 调用。
  * '-o ovirt'：设置输出方法为 ovirt。
  * '-os'：在该参数的后面指明导出域的地址，该导出域必须是初始化过的（即曾被添加到 EayunOS 管理平台上过）。
  * '--network'：在该参数后面指明您的 EayunOS 管理平台的虚拟网络名称。
  * 最后一个参数是虚拟机的名称。
