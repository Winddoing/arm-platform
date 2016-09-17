## 配置tftp

1. 安装

    $sudo apt-get install xinetd tftpd tftp

2. 修改配置文件/etc/xinetd.d/tftp

    service tftp
    {
	    socket_type = dgram #网络类型
		    protocol = udp
		    wait = yes
		    user = root
		    server = /usr/sbin/in.tftpd
		    server_args = -s /tftpboot #-s 路径 用于指定服务器共享目录
		    disable = no #是否禁用此服务
		    per_source = 11
		    cps = 100 2
		    flags = IPv4
    }

3. 重启服务：

    #service xinetd.d restart

4. 测试是否成功：
i. 安装 tftp 客户端，通过系统光盘安装

    #mount /dev/cdrom /media/
    #rpm -ivh /media/Server/tftp-0.49-2.i386.rpm

ii. 使用 tftp 命令下载文件测试

    #tftp 192.168.11.11
    tftp> get test

注：所有用于 tftp 下载的文件对所有用户都必须至少有可读权限（即 444），
否则无法下载。
