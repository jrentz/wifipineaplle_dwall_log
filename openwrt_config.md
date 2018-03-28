
# wifi pineapple #

---------

## 打开远程ssh访问: 打开22端口##

    uci add firewall rule
    uci set firewall.@rule[-1].src=wan
    uci set firewall.@rule[-1].target=ACCEPT
    uci set firewall.@rule[-1].proto=tcp
    uci set firewall.@rule[-1].dest_port=22
    uci commit firewall
    /etc/init.d/firewall restart

## 打开远程web访问: 打开1471端口##

    uci add firewall rule
    uci set firewall.@rule[-1].src=wan
    uci set firewall.@rule[-1].target=ACCEPT
    uci set firewall.@rule[-1].proto=tcp
    uci set firewall.@rule[-1].dest_port=1471
    uci commit firewall
    /etc/init.d/firewall restart


## USB扩充： ##

	u盘必须是ex4格式的，需要用linux格式化u盘
	
	config global
		option anon_swap '0'
		option anon_mount '0'
		option auto_swap '1'
		option auto_mount '1'
		option delay_root '5'
		option check_fs '0'

	config mount
		option target '/sd'
		option device '/dev/sda1'
		option fstype 'auto'
		option options 'rw,sync'
		option enabled '1'

	以后所有的程序就都可以安装到sd卡中了

## 修改IP与连接方式: ##

	Proto Recv-Q Send-Q Local Address   Foreign Address State   PID/Program name
	tcp0  0 0.0.0.0:80  0.0.0.0:*   LISTEN  1514/nginx.conf -g
	tcp0  0 0.0.0.0:53  0.0.0.0:*   LISTEN  6366/dnsmasq
	tcp0  0 0.0.0.0:22  0.0.0.0:*   LISTEN  1299/dropbear
	tcp0  0 0.0.0.0:14710.0.0.0:*   LISTEN  1514/nginx.conf -g
	tcp0  0 ::1:80  :::*LISTEN  9723/dropbear
	tcp0  0 :::22   :::*LISTEN  1299/dropbear
	udp0  0 0.0.0.0:53  0.0.0.0:*   6366/dnsmasq
	udp0  0 0.0.0.0:67  0.0.0.0:*   6366/dnsmasq


	Proto Recv-Q Send-Q Local Address           Foreign Address         State
	tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
	tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN
	tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
	tcp        0      0 0.0.0.0:1471            0.0.0.0:*               LISTEN
	tcp        0      0 :::22                   :::*                    LISTEN
