# 转换

* 在转换 Xen 虚拟机之前，需要确保如下几点已经实现：                                                     
  1. 首先需要关闭即将被准换的虚拟机。
     ~~~ bash
     # 安装了 Xen 的机器，`ip` 为 `172.16.1.35`。
     root@debian:/var/lib/libvirt/images# virsh list --all
     Id    Name                           State
     ----------------------------------------------------
     19    win2k3                         running
     -     win7                           shut off  # 转换前一定要确保关机了。
     ~~~

* 转换
  * **本地转换**：
    1. 获取 Xen 虚拟机的 XML：
       ~~~ bash
       root@debian:/home/helen/workspace# virsh list --all
       id    Name                           State
       ---------------------------------------------------
       20    rhel7                          running
       -     win2k3                         shut off
       -     win7                           shut off

       root@debian:/home/helen/workspace# ls
       firmware-amd-graphics_20160110-1_all.deb   libguestfs
       firmware-linux-nonfree_20160110-1_all.deb  firmware-misc-nonfree_20160110-1_all.deb
       root@debian:/home/helen/workspace# virsh dumpxml win7 > win7.xml # 注意名称要同要转换的虚拟机名称相同。
       root@debian:/home/helen/workspace# ls
       firmware-amd-graphics_20160110-1_all.deb   libguestfs
       firmware-linux-nonfree_20160110-1_all.deb  win7.xml # 多出一个 xml 文件
       firmware-misc-nonfree_20160110-1_all.deb
       ~~~

    2. 开始转换：
       ~~~ bash
       virt-v2v -i libvirtxml -o rhev -os 172.16.1.35:/home/nfs/yaqi --network eayunosmgmt /tmp/win7.xml
       ~~~
       在虚拟机转换的过程中，`virt-v2v` 会去寻找 `/var/lib/libvirt/images/` 目录下的 `win7.img` 这个磁盘文件。

    3. 参数说明：
       * `-i`：指定要使用的输入方法来获取到将要被转换的虚拟机。支持的选项有：`libvirt`，`libvirtxml` 和 `ova`。
       * `-o`：设置输出方法为 rhev。
       * `-os`：在该参数的后面指明导出域的地址，该导出域必须是初始化过的（即曾被添加到 EayunOS 管理平台上过）。
       * '--network'：在该参数后面指明您的 EayunOS 管理平台的虚拟网络名称。
       * 最后一个参数是虚拟机 xml 文件的路径。

  * **远程转换**：
    1. 前提：
       已经有一台用于虚拟机转换的机器，`machine1`。

    2. 开始转换：
       ~~~ bash
       # 在 `machine1` 执行如下命令：
       [root@zhangyingyun helen]# virt-v2v -o rhev -ic xen+ssh://root@172.16.1.66 -os 172.16.1.35:/home/nfs/yaqi --network eayunosmgmt win7
       Smartmatch is experimental at /usr/share/perl5/vendor_perl/Sys/VirtConvert/Connection/LibVirtTarget.pm line 572.
       Smartmatch is experimental at /usr/share/perl5/vendor_perl/Sys/VirtConvert/Connection/LibVirtTarget.pm line 578.
       root@172.16.1.66's password:
       root@172.16.1.66's password:
       win7.img: 100% [===============================================================================================================]D 0h19m50s
       virt-v2v: 配置中没有 app 匹配 os='windows' name='virtio' distro='windows' major='6' minor='1' arch='i386'
       ~~~

    3. 参数说明：
       * `-o`：设置输出方法为 rhev。
       * `-ic libvirtURI`：为读取虚拟机，指定 libvirt 连接 URI。
       * `libvirtURI` 格式：`xen+ssh://root@xen.example.com`
         * `xen.example.com`：Xen 虚拟机所在的机器。
       * '-os'：在该参数的后面指明导出域的地址，该导出域必须是初始化过的（即曾被添加到 EayunOS 管理平台上过）。
       * '--network'：在该参数后面指明您的 EayunOS 管理平台的虚拟网络名称。
       * 最后一个参数是虚拟机的名称。



    
