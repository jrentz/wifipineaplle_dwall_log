# wifipineaplle_dwall_log
wifipineapple dwall增加log功能


#加入功能:#
原来的DWall版本其实已经很好用了，只是没有记录log，这就让我们不在的时候，没办法看到，所以我加入了记录log的功能.

#主要修改的地方：#

在运行命令的时候，加入：

        $time = time();
        $date = date("ymdHis",$time);
        $date = $date.".log";

        $this->execBackground("/usr/bin/python /pineapple/modules/DWall/assets/DWall.py > /pineapple/modules/DWall/log/".$date);
    

其实就是把分析的字符串，记录在了文件中：
      
        print dataDict;



#使用方法:(两种方法)#

##第一种：##
- 在DWall下建立log目录（必须）；
- 覆盖api目录下的modulue.php
- 覆盖assets目录下的UDSHandler.py 

##第二种：##
直接下载我这个版本使用。
