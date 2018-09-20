1.file  xxxx.so: 查看该so包的位数（32or64）

2.vim ctrl+s 假死: 在vim下ctrl+s整个putty终端就死了,原来ctrl+s在LINUX里是锁定屏幕的快捷键，解锁ctrl+q就可以了

3.top  获取CPU使用情况
```
-m num：最大显示条数
-n num：更新次数
-d num：两次更新时间
-s col：按哪列排序（cpu vss rss thr）
-t：显示线程信息而不是进程   (这个option可能无效)
-h：显示帮助文档
```

4.tar  压缩和解压文件（后缀.tar.gz）
```
tar cvfz 压缩文件名 源文件
tar xvfz 目标文件          //在当前目录下将压缩包文件解压
```

5.linux ssh 连接另一台linux
```
$ ssh -l liu 10.71.84.145   默认22端口  liu为用户名
```

6.使用rar 命令进行分卷压缩
```
rar a -v1m 目标文件名 源文件目录
```
a 代表添加  -v表示设置分卷的大小后面跟上1m 表示每个分卷最大为1M，单位可以是k,m,g。。。分别表示千字节，兆字节，千兆字节
6.linux ssh 挂载远程目录
```
$sshfs -o allow_other peisaiasi@172.18.102.106:/data2/peisaisai/
```
