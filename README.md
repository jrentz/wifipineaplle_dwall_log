# wifipineaplle_dwall_log
wifipineapple dwall增加log功能


# 加入功能: 

- 原来的DWall版本其实已经很好用了，只是没有记录log，这就让我们不在的时候，没办法看到，所以我加入了记录log的功能.
- 虽然这个功能很简单，但我觉得还是比较实用的，以后只要每次启动就会自动进行记录，错过不了好东西。



# 主要修改的地方：

在运行命令的时候，api/module.php 加入：

        $time = time();
        $date = date("ymdHis",$time);
        $date = $date.".log";

        $this->execBackground("/usr/bin/python /pineapple/modules/DWall/assets/DWall.py > /pineapple/modules/DWall/log/".$date);
    

其实就是把分析的字符串，记录在了文件中,在assets/WebSocketsHandler.py 中加入print，让他打印屏幕。

	print dataDict;


## log后内容的格式：
		{'url': 'http://t.wg.360-api.cn/ap/tips/browse?mid=2ea1cddeb1140c584e2af3fdd9f70e22', 'to': 'xxx.xxx.xxx.xxx', 'from': '172.16.42.192
		{'url': 'http://s.360.cn/360game/stat.htm?pid=se&m=2ea1cddeb1140c584e2af3fdd9f70e22&ver=9.0.7.1033&s=loading&type=extyouxi&sever=9.1
		{'url': 'http://wan.360.cn/?src=se', 'to': 'xxx.xxx.xxx.xxx', 'from': 'xxx.xxx.xxx.xxx', 'cookie': '__huid=11K07bgNFwCnhAAu7BlaPTAx5Xov
		{'url': 'http://seupdate.360safe.com/bankmode4.ini?1842861343', 'to': '61.240.140.61', 'from': '172.16.42.192'}
		{'to': '42.236.102.95', 'image': 'http://p0.qhimg.com/t016d59f245a828b8e3.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t01321f78ebe6c390bf.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t01dfc19ebeec81e26f.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t01e46f85933f369ab6.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t0188118c4beb970f46.jpg', 'from': '172.16.42.192'}
		{'to': '120.52.32.31', 'image': 'http://p0.qhimg.com/t016d59f245a828b8e3.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t01cd2fd2aa60ffd533.jpg', 'from': '172.16.42.192'}
		{'to': 'xxx.xxx.xxx.xxx', 'image': 'http://p6.yx-s.com/t014f83608163d71015.jpg', 'from': '172.16.42.192'}
		{'url': 'http://js.passport.qihucdn.com/5.0.3.js', 'to': '42.236.102.95', 'from': '172.16.42.192'}


## 目录文件：
		root@gl_ar150:/sd/modules/DWall/log# ls -la
		drwxr-xr-x    2 root     root          4096 Mar 26 19:30 .
		drwxr-xr-x    6 111      118           4096 Mar 23 19:11 ..
		-rw-r--r--    1 root     root             0 Mar 23 20:17 180323121756.log
		-rw-r--r--    1 root     root       1568871 Mar 26 11:29 180323121836.log
		-rw-r--r--    1 root     root         16384 Mar 26 19:30 180326112942.log
		-rw-r--r--    1 root     root         28673 Mar 26 19:31 180326113030.log


# 使用方法:(两种方法) 

## 第一种：

- 在DWall下建立log目录（必须）；
- 覆盖api目录下的modulue.php
- 覆盖assets目录下的UDSHandler.py 

## 第二种：

直接下载我这个版本使用,替换原来的文件即可！


## [最佳实践](https://github.com/yearnwang/wifipineaplle_dwall_log/blob/master/my_wifipineapple.md)
