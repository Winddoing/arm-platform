## 配置NFS

1. 安装

    #sudo apt-get install nfs-kernel-server

2. 配置文件/etc/exports （默认为空文件）
添加

    /work/embedded/rootfs *(rw,sync,no_root_squash)

	书写格式：
	共享目录 共享的目标名或 IP（共享参数列表）
	每行都是一个共享目录的配置
	rw — 读写 sync — C/S 数据，同步更新
	no_root_squash — 不压制 root 权限
	注：参数之间用逗号分隔，并且逗号两端不能有空格

3. 重启服务

    #service portmap start
    #service nfs restart

4. 测试服务

i. 挂载共享文件系统

    #mount 192.168.11.11:/work/embedded/rootfs/ /media/

ii. 查看共享目录与挂载目录中，文件是否同步
