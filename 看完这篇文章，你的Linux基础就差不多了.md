
# 一、Linux介绍

## 1、操作系统的发展

![](https://upload-images.jianshu.io/upload_images/6767178-4922dd72fc41e408.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/668)

## 2、Linux的不同版本

<1>Linux内核版本：内核(kernel)是系统的心脏，是运行程序和管理像磁盘和打印机等硬件设备的核心程序，它提供了一个在裸设备与应用程序间的抽象层。
 <2>Linux发行版本：也被叫做 GNU， 通常包含了包括桌面环境、办公套件、媒体播放器、数据库等应用软件。

# 二、文件和目录

## 1、Windows和Linux文件系统区别

在 windows 平台下，打开“计算机”，我们看到的是一个个的驱动器盘符：

![](https://upload-images.jianshu.io/upload_images/6767178-d58feffa17177fdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/741)

每个驱动器都有自己的根目录结构，这样形成了多个树并列的情形，如图所示：

![](https://upload-images.jianshu.io/upload_images/6767178-732382babbbdd15c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/346)

在 Linux 下，我们是看不到这些驱动器盘符，我们看到的是文件夹（目录）：
![](https://upload-images.jianshu.io/upload_images/6767178-e965bee0a4c28b0a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/701)

就比如我们用的Ubuntu没有盘符这个概念，只有一个根目录/，所有文件都在它下面：

![](https://upload-images.jianshu.io/upload_images/6767178-0dbb1d189b38987b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/673)

> /：根目录，一般根目录下只存放目录，在Linux下有且只有一个根目录。所有的东西都是从这里开始。当你在终端里输入“/home”，你其实是在告诉电脑，先从/（根目录）开始，再进入到home目录。
>  /bin: /usr/bin: 可执行二进制文件的目录，如常用的命令ls、tar、mv、cat等。
>  /boot：放置linux系统启动时用到的一些文件，如Linux的内核文件：/boot/vmlinuz，系统引导管理器：/boot/grub。
>  /dev：存放linux系统下的设备文件，访问该目录下某个文件，相当于访问某个设备，常用的是挂载光驱 mount /dev/cdrom /mnt。
>  /etc：系统配置文件存放的目录，不建议在此目录下存放可执行文件，重要的配置文件有 /etc/inittab、/etc/fstab、/etc/init.d、/etc/X11、/etc/sysconfig、/etc/xinetd.d。
>  /home：系统默认的用户家目录，新增用户账号时，用户的家目录都存放在此目录下，<sub>表示当前用户的家目录，</sub>edu 表示用户 edu 的家目录。
>  /lib: /usr/lib: /usr/local/lib：系统使用的函数库的目录，程序在执行过程中，需要调用一些额外的参数时需要函数库的协助。
>  /lost+fount：系统异常产生错误时，会将一些遗失的片段放置于此目录下。
>  /mnt: /media：光盘默认挂载点，通常光盘挂载于 /mnt/cdrom 下，也不一定，可以选择任意位置进行挂载。
>  /opt：给主机额外安装软件所摆放的目录。
>  /proc：此目录的数据都在内存中，如系统核心，外部设备，网络状态，由于数据都存放于内存中，所以不占用磁盘空间，比较重要的目录有 /proc/cpuinfo、/proc/interrupts、/proc/dma、/proc/ioports、/proc/net/* 等。
>  /root：系统管理员root的家目录。
>  /sbin: /usr/sbin: /usr/local/sbin：放置系统管理员使用的可执行命令，如fdisk、shutdown、mount 等。与 /bin 不同的是，这几个目录是给系统管理员 root使用的命令，一般用户只能"查看"而不能设置和使用。
>  /tmp：一般用户或正在执行的程序临时存放文件的目录，任何人都可以访问，重要数据不可放置在此目录下。
>  /srv：服务启动之后需要访问的数据目录，如 www 服务需要访问的网页数据存放在 /srv/www 内。
>  /usr：应用程序存放目录，/usr/bin 存放应用程序，/usr/share 存放共享数据，/usr/lib 存放不能直接运行的，却是许多程序运行所必需的一些函数库文件。/usr/local: 存放软件升级包。/usr/share/doc: 系统说明文件存放目录。/usr/share/man: 程序说明文件存放目录。
>  /var：放置系统执行过程中经常变化的文件，如随时更改的日志文件 /var/log，/var/log/message：所有的登录文件存放目录，/var/spool/mail：邮件存放的目录，/var/run:程序或服务启动后，其PID存放在该目录下。

## 2、用户目录

位于/home/user，称之为用户工作目录或家目录,表示方式：

> /home/user
>  ~

## 3、相对路径和绝对路径

绝对路径：从/目录开始描述的路径为绝对路径，如：/home
 相对路径：从当前位置开始描述的路径为相对路径，如：../../
 .和.. ：每个目录下都有.和..（可用`ls -a`查看）；. 表示当前目录；.. 表示上一级目录，即父目录；根目录下的.和..都表示当前目录

## 4、文件权限

文件权限就是文件的访问控制权限，即哪些用户和组群可以访问文件以及可以执行什么样的操作。
 在 Unix/Linux中的每一个文件或目录都包含有访问权限，这些访问权限决定了谁能访问和如何访问这些文件和目录。

### <1>访问用户

通过设定权限可以从以下三种访问方式限制访问权限：
 只允许用户自己访问（所有者） 所有者就是创建文件的用户，用户是所有用户所创建文件的所有者，用户可以允许所在的用户组能访问用户的文件。
 允许一个预先指定的用户组中的用户访问（用户组） 用户都组合成用户组，例如，某一类或某一项目中的所有用户都能够被系统管理员归为一个用户组，一个用户能够授予所在用户组的其他成员的文件访问权限。
 允许系统中的任何用户访问（其他用户） 用户也将自己的文件向系统内的所有用户开放，在这种情况下，系统内的所有用户都能够访问用户的目录或文件。在这种意义上，系统内的其他所有用户就是 other 用户类。

### <2>访问权限

用户能够控制一个给定的文件或目录的访问程度，一个文件或目录可能有读、写及执行权限：
 读权限（r） 对文件而言，具有读取文件内容的权限；对目录来说，具有浏览目录的权限。
 写权限（w） 对文件而言，具有新增、修改文件内容的权限；对目录来说，具有删除、移动目录内文件的权限。
 可执行权限（x） 对文件而言，具有执行文件的权限；对目录了来说该用户具有进入目录的权限。
 注意：通常，Unix/Linux系统只允许文件的属主(所有者)或超级用户改变文件的读写权限。

### <3>示例说明：利用`ls -lh`查看

![](https://upload-images.jianshu.io/upload_images/6767178-f70192f1488c6dc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/794)

第1个字母代表文件的类型：“d” 代表文件夹、“-” 代表普通文件、“c” 代表硬件字符设备、“b” 代表硬件块设备、“s”表示管道文件、“l” 代表软链接文件。 后 9 个字母分别代表三组权限：文件所有者、用户者、其他用户拥有的权限。

```
handy@ubuntu:~$ ls -l
total 44
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Desktop
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Documents
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Downloads
-rw-r--r-- 1 handy handy 8980 Aug 29 06:39 examples.desktop
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Music
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Pictures
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Public
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Templates
drwxr-xr-x 2 handy handy 4096 Aug 29 06:45 Videos
handy@ubuntu:~$ ls -lh
total 44K
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Desktop
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Documents
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Downloads
-rw-r--r-- 1 handy handy 8.8K Aug 29 06:39 examples.desktop
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Music
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Pictures
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Public
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Templates
drwxr-xr-x 2 handy handy 4.0K Aug 29 06:45 Videos
handy@ubuntu:~$ 

```

每一个用户都有它自身的读、写和执行权限。
 第一组权限控制访问自己的文件权限，即所有者权限。
 第二组权限控制用户组访问其中一个用户的文件的权限。
 第三组权限控制其他所有用户访问一个用户的文件的权限。
 这三组权限赋予用户不同类型（即所有者、用户组和其他用户）的读、写及执行权限就构成了一个有9种类型的权限组。

# 三、常用基本命令

Linux 提供了大量的命令，利用它可以有效地完成大量的工作，如磁盘操作、文件存取、目录操作、进程管理、文件权限设定等。Linux 发行版本最少的命令也有 200 多个，这里只介绍比较重要和使用频率最多的命令。

## 1、命令使用方法

Linux命令格式:
 `command [-options] [parameter1] …`
 命令 选项 参数
 说明：
 command: 命令名,相应功能的英文单词或单词的缩写 [-options]：选项,可用来对命令进行控制，也可以省略，[]代表可选 parameter1 …：传给命令的参数：可以是零个一个或多个.

## 2、查看帮助文档

### <1>--help

一般是linux命令自带的帮助信息，如：`ls --help`

### <2>man

man是linux提供的一个手册，包含了绝大部分的命令、函数使用说明
 该手册分成很多章节（section），使用man时可以指定不同的章节来浏览。
 例：`man ls` ; `man 2 printf`
 man中各个section意义如下：
 1: Standard commands（标准命令）
 2: System calls（系统调用，如open,write）
 3: Library functions（库函数，如printf,fopen）
 4:Special devices（设备文件的说明，/dev下各种设备）
 5: File formats（文件格式，如passwd）
 6:Games and toys（游戏和娱乐）
 7:Miscellaneous（杂项、惯例与协定等，例如Linux档案系统、网络协定、ASCII 码；environ全局变量）
 8: Administrative Commands（管理员命令，如ifconfig）
 man是按照手册的章节号的顺序进行搜索的。
 man设置了如下的功能键：

![](https://upload-images.jianshu.io/upload_images/6767178-dc8448b29709d19f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/975)

例如：
![](https://upload-images.jianshu.io/upload_images/6767178-9fc5865ede9a2c78.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/777)

## 3、自动补全

在敲出命令的前几个字母的同时，按下tab键，系统会自动帮我们补全命令

## 4、历史命令

当系统执行过一些命令后，可按上下键翻看以前的命令，`history`将执行过的命令列举出来。

# 四、文件、磁盘管理的常用命令

### <1>查看文件信息：ls

ls是英文单词list的简写，其功能为列出目录的内容，是用户最常用的命令之一，它类似于DOS下的dir命令。
 Linux文件或者目录名称最长可以有265个字符，“.”代表当前目录，“..”代表上一级目录，以“.”开头的文件为隐藏文件，需要用`-a`参数才能显示。

![](https://upload-images.jianshu.io/upload_images/6767178-ef96174e7d3b9641.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

ls常用参数

![](https://upload-images.jianshu.io/upload_images/6767178-8032ef9312c13c07.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/591)

ls -l

与DOS下的文件操作类似，在Unix/Linux系统中，也同样允许使用特殊字符来同时引用多个文件名，这些特殊字符被称为通配符。
![](https://upload-images.jianshu.io/upload_images/6767178-64415a6400925df5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

### <2>输出重定向命令：>

Linux允许将命令执行结果重定向到一个文件，本应显示在终端上的内容保存到指定文件中。
 如：`ls > test.txt` ( test.txt 如果不存在，则创建，存在则覆盖其内容 )
 注意： `>`输出重定向会覆盖原来的内容，`>>`输出重定向则会追加到文件的尾部。

### <3>分屏显示：more

查看内容时，在信息过长无法在一屏上显示时，会出现快速滚屏，使得用户无法看清文件的内容，此时可以使用more命令，每次只显示一页，按下空格键可以显示下一页，按下q键退出显示，按下h键可以获取帮助。

![](https://upload-images.jianshu.io/upload_images/6767178-783181afa65a9efd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/282)

![](https://upload-images.jianshu.io/upload_images/6767178-aee7f213f3e39545.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/707)

more 示例

### <4>管道：|

管道：一个命令的输出可以通过管道做为另一个命令的输入。
 管道我们可以理解现实生活中的管子，管子的一头塞东西进去，另一头取出来，这里“ | ”的左右分为两端，左端塞东西(写)，右端取东西(读)。

![](https://upload-images.jianshu.io/upload_images/6767178-010154863b9456ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/729)

管道示例

### <5>清屏：clear

`clear`作用为清除终端上的显示(类似于DOS的cls清屏功能)，也可使用快捷键：Ctrl + l ( “l” 为字母 )。

### <6>切换工作目录： cd

在使用Unix/Linux的时候，经常需要更换工作目录。`cd`命令可以帮助用户切换工作目录。Linux所有的目录和文件名大小写敏感。
 cd后面可跟绝对路径，也可以跟相对路径。如果省略目录，则默认切换到当前用户的主目录。

![](https://upload-images.jianshu.io/upload_images/6767178-f3473bcece7bd24a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

cd 示例

注意：如果路径是从根路径开始的，则路径的前面需要加上 “ / ”，如 “ /mnt ”，通常进入某个目录里的文件夹，前面不用加 “ / ”。

### <7>显示当前路径：pwd

使用pwd命令可以显示当前的工作目录，该命令很简单，直接输入pwd即可，后面不带参数。

### <8>创建目录：mkdir

通过`mkdir`命令可以创建一个新的目录。参数`-p`可递归创建目录。

![](https://upload-images.jianshu.io/upload_images/6767178-910722590b82260e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/824)

示例

需要注意的是新建目录的名称不能与当前目录中已有的目录或文件同名，并且目录创建者必须对当前目录具有写权限。

### <补>创建文件：touch

命令格式：`touch 文件名`
 如果文件**不存在**，可以创建一个空白文件。
 如果文件**存在**，可以修改文件的末次修改日期。

### <9>删除目录：rmdir

可使用`rmdir`命令删除一个目录。必须离开目录，并且目录必须为空目录，不然提示删除失败。

### <10>删除文件：rm

可通过rm删除文件或目录。使用rm命令要小心，因为文件删除后不能恢复。为了防止文件误删，可以在rm后使用-i参数以逐个确认要删除的文件。

![](https://upload-images.jianshu.io/upload_images/6767178-5f7e189d02869497.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用参数

注意递归删除文件夹要加`-r`，而删除文件可以不加。
![](https://upload-images.jianshu.io/upload_images/6767178-7d5f63b31c9991d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/438)

示例

### <11>建立链接文件：ln

Linux链接文件类似于Windows下的快捷方式。
 链接文件分为软链接（有`-s`）和硬链接。
 软链接：软链接不占用磁盘空间，源文件删除则软链接失效，源文件要用绝对路径。`ln -s 源文件 链接文件`
 硬链接：硬链接只能链接普通文件，不能链接目录，相当于文件“小名”，日常是不用的，只有文件的硬链接数（用`ls -l`查看）为0时，文件才被真正删除。 `ln 源文件 链接文件`

![](https://upload-images.jianshu.io/upload_images/6767178-c79291c375a616e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)

硬链接示例及软链接的tree示意

![](https://upload-images.jianshu.io/upload_images/6767178-8a0157aa17efde15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/744)

文件软硬链接示意图

> 在Linux中，文件数据和文件名是分开存储的。

### <12>查看或者合并文件内容：cat

对应英文是concatenate，用于查看文件内容（适合内容较少的，较多的用`more`）、创建文件、文件合并、追加文件内容等。

![](https://upload-images.jianshu.io/upload_images/6767178-0137c7fe49ff17b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/236)

常用参数

> Linux中还有一个`nl`命令，和`cat -b`效果等价。

![](https://upload-images.jianshu.io/upload_images/6767178-d1c32484806aee6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/556)

示例

### <13>文本搜索：grep

Linux系统中grep命令是一种强大的文本搜索工具，grep允许对文本文件进行模式查找。如果找到匹配模式， grep打印包含模式的所有行。
 grep一般格式为：`grep [-选项] ‘搜索内容串’文件名`
 在grep命令中输入字符串参数时，最好引号或双引号括起来。例如：grep‘a ’1.txt。

![](https://upload-images.jianshu.io/upload_images/6767178-e6bafab6edd6175c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用选项

grep搜索内容串可以是正则表达式，也就是模式查找。
 正则表达式是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个“规则字符串”，这个“规则字符串”用来表达对字符串的一种过滤逻辑。
![](https://upload-images.jianshu.io/upload_images/6767178-0205f065ce5bca9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

grep常用正则表达式

![](https://upload-images.jianshu.io/upload_images/6767178-78c03da90fa486b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/411)

grep示例

### <14>查找文件：find

find支持文件名的正则表达式查找，按文件修改时间查找，按文件大小查找，按文件权限查找，按文件类型查找等，查找到以后还支持直接对查找到的文件使用命令，功能非常强大。

典型的find命令的写法是：`find 查找路径 查找的标准 查找到之后的动作`。
 比如: `find /home -type d -ls`，意思是: 找出/home/下所有的目录,并显示目录的详细信息。

后继命令（查找到之后的动作）：

```
-print: 显示
-ls：类似ls -l的形式显示每一个文件的详细
-quit：查找到一个就退出
-delete：删除匹配到的行
-ok COMMAND {} \：每一次操作都需要用户确认，{}表示引用找到的文件，是占位符，对于（find等输出的一个列表的内容）依次循环每一个；\是表示 -exec 命令终结的的符号。
-exec COMMAND {} \：每次操作无需确认

```

![](https://upload-images.jianshu.io/upload_images/6767178-51470fc681c2c9aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用用法

### <15>拷贝文件：cp

cp命令的功能是将给出的文件或目录复制到另一个文件或目录中，相当于DOS下的copy命令。

![](https://upload-images.jianshu.io/upload_images/6767178-268f1883b7330fcb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用选项

### <16>移动文件：mv

用户可以使用mv命令来移动文件或目录，也可以给文件或目录重命名。

![](https://upload-images.jianshu.io/upload_images/6767178-97fa32769855be00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用选项

### <17>归档管理：tar

计算机中的数据经常需要备份，tar是Unix/Linux中最常用的备份工具，此命令可以把一系列文件归档到一个大文件中，也可以把档案文件解开以恢复数据。
 tar使用格式`tar [选项] 打包文件名 文件`
 tar命令很特殊，其选项前面可以使用“-”，也可以不使用。

![](https://upload-images.jianshu.io/upload_images/6767178-2644bf136496d061.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

常用选项

注意：除了f需要放在参数的最后，其它参数的顺序任意。
 一般来说，我们的选项主要要用cvf和xvf。

*   文件打包：`tar -cvf ***.tar 1.py 2.py 3.txt *.c`
*   文件解包：`tar -xvf ***.tar -C ~/Desktop`

### <18>文件压缩解压：gzip

tar与gzip命令结合使用实现文件打包、压缩。 tar只负责打包文件，但不压缩，用gzip压缩tar打包后的文件，其扩展名一般用xxxx.tar.gz。
 gzip使用格式：`gzip [选项] 被压缩文件`
 常用选项：`-d`解压、`-r`压缩所有子目录
 tar这个命令并没有压缩的功能，它只是一个打包的命令，但是在tar命令中增加一个选项(-z)可以调用gzip实现了一个压缩的功能，实行一个先打包后压缩的过程。

*   压缩用法：`tar -zcvf 压缩包包名 文件1 文件2 ...`
     -z ：指定压缩包的格式为：file.tar.gz
*   解压用法： `tar -zxvf 压缩包包名`
     解压到指定目录：-C （大写字母“C”）

### <19>文件压缩解压：bzip2

tar与bzip2命令结合使用实现文件打包、压缩(用法和gzip一样)。
 tar只负责打包文件，但不压缩，用bzip2压缩tar打包后的文件，其扩展名一般用xxxx.tar.gz2。
 在tar命令中增加一个选项(-j)可以调用bzip2实现了一个压缩的功能，实行一个先打包后压缩的过程。

*   压缩用法：`tar jcvf 压缩包包名 文件...(tar jcvf bk.tar.bz2 *.c)`
*   解压用法：`tar jxvf 压缩包包名 (tar jxvf bk.tar.bz2)`
    ![](https://upload-images.jianshu.io/upload_images/6767178-f982a26eed487865.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/725)

    示例

### <20>文件压缩解压：zip、unzip

通过zip压缩文件的目标文件不需要指定扩展名，默认扩展名为zip。

*   压缩文件：`zip [-r] 目标文件(没有扩展名) 源文件`
*   解压文件：`unzip -d 解压后目录文件 压缩文件`
    ![](https://upload-images.jianshu.io/upload_images/6767178-1ff82188bc77b848.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/568)

### <21>查看命令位置：which

![](https://upload-images.jianshu.io/upload_images/6767178-b4f8be87528ca12b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/795)

bin 和 sbin

![](https://upload-images.jianshu.io/upload_images/6767178-93a1cd2c8649e3ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/239)

示例

# 五、用户、权限管理的常用命令

用户是Unix/Linux系统工作中重要的一环，用户管理包括用户与组账号的管理。
 在Unix/Linux系统中，不论是由本机或是远程登录系统，每个系统都必须拥有一个账号，并且对于不同的系统资源拥有不同的使用权限。
 Unix/Linux系统中的root账号通常用于系统的维护和管理，它对Unix/Linux操作系统的所有部分具有不受限制的访问权限。
 在Unix/Linux安装的过程中，系统会自动创建许多用户账号，而这些默认的用户就称为“标准用户”。
 在大多数版本的Unix/Linux中，都不推荐直接使用root账号登录系统。

### <1>查看当前用户：whoami

`whoami`命令用户查看当前系统当前账号的用户名。可通过`cat /etc/passwd`查看系统用户信息。
 由于系统管理员通常需要使用多种身份登录系统，例如通常使用普通用户登录系统，然后再以su命令切换到root身份对传统进行管理。这时候就可以使用whoami来查看当前用户的身份。

![](https://upload-images.jianshu.io/upload_images/6767178-b96a3bc2867ea17e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/775)

### <2>查看登录用户：who

who命令用于查看当前所有登录系统的用户信息。

常用选项

示例

### <3>退出登录账户： exit

*   如果是图形界面，退出当前终端（Terminal）；
*   如果是使用ssh远程登录，退出登陆账户；
*   如果是切换后的登陆用户，退出则返回上一个登陆账号。

    ![](https://upload-images.jianshu.io/upload_images/6767178-a475c15b3ae3059c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/643)

    exit示意图

### <4>切换用户：su

可以通过`su`命令切换用户，`su`后面可以加“-”。`su`和`su –`命令不同之处在于，`su -`切换到对应的用户时会将当前的工作目录自动转换到切换后的用户主目录：

![](https://upload-images.jianshu.io/upload_images/6767178-6a00b454c840129e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/604)

示例

注意：如果是ubuntu平台，需要在命令前加`sudo`，如果在某些操作需要管理员才能操作，ubuntu无需切换到root用户即可操作，只需加`sudo`即可。sudo是ubuntu平台下允许系统管理员让普通用户执行一些或者全部的root命令的一个工具，减少了root 用户的登陆和管理时间，提高了安全性。
![](https://upload-images.jianshu.io/upload_images/6767178-eccc05fc14e32cfc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

su用法

![](https://upload-images.jianshu.io/upload_images/6767178-a6177bc7ee163ce6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/327)

Ubuntu下示例

### <5>添加、删除组账号：groupadd、groupdel

`groupadd 组名` 新建组账号 `groupdel 组名` 删除组账号 `cat /etc/group` 查看用户组信息

![](https://upload-images.jianshu.io/upload_images/6767178-077cc9fdc80e0c9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/423)

示例

### <6>修改用户所在组：usermod

*   主组：通常在新建用户时指定，在 `/etc/passwd` 的第四列GID对应的组。
*   附加组：在 `/etc/group` 的最后一列表示该组的用户列表，用于指定用户的附加权限。
     `usermod`可以用来设置用户的 **主组/附加组** 和 **登陆 Shell** ，命令格式如下：
    ![](https://upload-images.jianshu.io/upload_images/6767178-151470f4d8ca2903.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/908)

### <7>添加用户账号：useradd

在Unix/Linux中添加用户账号可以使用`adduser`或`useradd`命令，因为`adduser`命令是指向`useradd`命令的一个链接，因此，这两个命令的使用格式完全一样。
 `useradd`命令的使用格式如下： `useradd [选项及参数] 新建用户名`

创建用户、设置密码、删除用户、确认用户信息

useradd示例

注意：

*   创建用户时忘记加上`-m`的解决方法是：**删除用户，重新创建**（不必考虑设置权限问题）。
*   创建用户时会默认创建一个和 **用户名** 同名的组。
*   用户信息保存在`/etc/passwd`文件中。
*   默认使用`useradd`添加的用户没有`sudo`权限，需要用命令`sudo usermod -G sudo 用户名`，将用户添加到`sudo`附加组中。
    usermod修改附加组示例

### <8>设置用户密码：passwd

在Unix/Linux中，超级用户可以使用passwd命令为普通用户设置或修改用户口令。用户也可以直接使用该命令来修改自己的口令，而无需在命令后面使用用户名。

passwd示例

### <9>删除用户：userdel

userdel命令用法

### <补>查看用户UID和GID：id

命令格式：`id 用户名`

passwd文件说明

id示例

### <10>修改文件权限：chmod

chmod 修改文件权限有两种使用格式：字母法与数字法。
 **字母法**：chmod u/g/o/a +/-/= rwx 文件

ugoa

+-=

rwx

chmod o+w file 给文件file的其它用户增加写权限：

chmod u-r file 给文件file的拥有者减去读的权限：
![](https://upload-images.jianshu.io/upload_images/6767178-cf2c0bf43e9a9bb5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/721)

chmod g=x file设置文件file的同组用户的权限为可执行，同时去除读、写权限：
![](https://upload-images.jianshu.io/upload_images/6767178-243c9bb32eb91dac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/709)

**数字法**：“rwx” 这些权限也可以用数字来代替
![](https://upload-images.jianshu.io/upload_images/6767178-040fa8778fdfeded.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/416)

chmod数字表示法

例如，chmod 777 file：所有用户拥有读、写、执行权限
![](https://upload-images.jianshu.io/upload_images/6767178-c33233652cd1fdae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/707)

注意要递归修改权限的话，需要加上`-R`。
![](https://upload-images.jianshu.io/upload_images/6767178-21f76b482786f20f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/698)

chmod示例

以下是对修改文件的属主、属组、权限的总结：

### <11>修改文件所有者：chown

命令格式：`chown 用户名 文件名|目录名`

### <12>修改文件所属组：chgrp

命令格时：`chgrp 组名 文件名|目录名`

注意要递归修改的话，需要加上`-R`。

chown、chgrp示例

修改文件的命令总结

# 六、系统、远程管理的常用命令

### <1>查看当前日历：cal

`cal`（calendar）命令用于查看当前日历，`-y`显示整年日历：

cal示例

### <2>显示或设置时间：date

设置时间格式（需要管理员权限）：`date [MMDDhhmm[[CC]YY][.ss]] +format`
 CC为年前两位yy为年的后两位，前两位的MM为月，后两位的mm为分钟，dd为天，hh为小时，ss为秒。如： `date 010203042016.55`。
 显示时间格式（`date '+%y,%m,%d,%H,%M,%S'`）：

date示例

### <3>查看进程信息：ps

进程是一个具有一定独立功能的程序，它是操作系统动态执行的基本单元。
 `ps`（process status）命令可以查看进程的详细状况，常用选项(选项可以不加“-”)如下：

注意：`ps`默认只会显示当前用户通过终端启动的应用程序。
ps示例

### <4>动态显示进程：top

`top`命令用来动态显示运行中的进程。`top`命令能够在运行后，在指定的时间间隔更新显示信息。可以在使用`top`命令时加上`-d`来指定显示信息更新的时间间隔。
 在`top`命令执行后，可以按下按键得到对显示的结果进行排序：

![](https://upload-images.jianshu.io/upload_images/6767178-53a37fdec83ee1c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

![](https://upload-images.jianshu.io/upload_images/6767178-0f2f3add7346420d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/723)

top示例

### <5>终止进程：kill

kill命令指定进程号的进程，需要配合 `ps` 使用。
 使用格式：`kill [-signal] pid`
 信号值从0到15，其中9为绝对终止，可以处理一般信号无法终止的进程。

![](https://upload-images.jianshu.io/upload_images/6767178-3566a888fa56853c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/723)

kill示例

有些进程不能直接杀死，这时候我们需要加一个参数`-9`，“ -9 ” 代表强制结束。

### <6>关机重启：reboot、shutdown、init

`shutdown`命令格式：`shutdown -选项 时间`
 `shutdown`可以 安全关闭 或 重新启动系统
 注意：

*   当选项是`-r`时，表示**重新启动**。
*   当选项是`-c`时，表示取消操作。
*   不指定选项和参数时，默认**一分钟后关闭**电脑。
*   远程维护服务器时，最好不要关闭系统，而应该重新启动系统。
     常用命令示例：

![](https://upload-images.jianshu.io/upload_images/6767178-c67ea4eb8685a6d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

### <7>检测磁盘空间：df

`df`（disk free）命令用于检测文件系统的磁盘空间占用和空余情况，可以显示所有文件系统对节点和磁盘块的使用情况。

![](https://upload-images.jianshu.io/upload_images/6767178-9c4fe80a511ba095.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/963)

df常用选项

df示例

### <8>检测目录所占磁盘空间：du

`du`（disk usage）命令用于统计目录或文件所占磁盘空间的大小，该命令的执行结果与`df`类似，`du`更侧重于磁盘的使用状况。
 `du`命令的使用格式如下： `du [选项] 目录或文件名`

du常用选项

du示例

### <9>查看或配置网卡信息：ifconfig

如果，我们只是敲：`ifconfig`，它会显示所有网卡的信息：

可以通过管道快速查看IP地址：`ifconfig | grep 'inet'`。
 提示：一台计算机中可能有一个物理网卡和多个虚拟网卡，在Linux中物理网卡的名字通常以`ensXX`表示。`127.0.0.1`被称为本地回环/环回地址，一般用来测试本机网卡是否正常。

### <10>测试远程主机连通性：ping

> `ping`一般用于检测当前计算机到目标计算机之间的网络是否通畅，数值越大，速度越慢。
>  `ping`的工作原理与潜水艇的声纳相似，它就是取自声纳的声音。
>  网络管理员之间也通常将`ping`作为动词——ping一下计算机x，看它是否还开着。

提示：在Linux中，要想终止一个终端程序的执行，绝大多数都可以使用`ctrl c`。

### <补>SSH基础

通过**ssh客户端**可以连接到安装了**ssh服务器**的远程机器上。

> ssh客户端是一种使用`secure shell（SSH）`协议连接到远程计算机的程序。
>  利用SSH协议，可以防止信息泄露，防止DNS欺骗和IP欺骗（加密），并提高传输速度（压缩）。

#### 1）域名 和 端口号

域名：由一串用点分隔的名字组成，是IP地址的**别名**，方便用户记忆，例如[www.baidu.com](http://www.baidu.com)。
 IP地址：通过IP地址找到网络上的**计算机**。
 端口号：通过端口号找到计算机上**运行的应用程序**。

> SSH服务器的默认端口号是`22`，如果是默认端口号，在连接时可以省略。

常见服务器端口号

#### 2）SSH服务器的安装配置

> 安装ssh相关服务的客户端：openssh-client，服务端（Ubuntu自带）：openssh-server，可以用命令：`sudo apt-get install openssh-client openssh-server`。
> 
> *   Ubuntu中其实只需安装**SSH服务器**：`sudo apt-get install openssh-server`，启动服务`service sshd start`，查看服务状态：`service sshd status`，设置有root权限的用户的登陆应该修改配置文件：`vi /etc/ssh/sshd_config`，如下：
> 
> ```
> # Authentication:
> LoginGraceTime 120
> PermitRootLogin yes
> StrictModes yes
> 
> ```
> 
> 然后要记得重启服务：`service sshd restart`，也可以`sudo /etc/init.d/ssh stop` ， `sudo /etc/init.d/ssh start`。
> 
> > 可能需要：关闭Ubuntu的防火墙：
> > 
> > ```
> > sudo ufw disable #关闭防火墙
> > 
> > sudo ufw enable #开启防火墙
> > 
> > sudo ufw status #查看防火墙状态
> > 
> > ```
> > 
> > 还有可能的错误：/etc/passwd文件中用户的shell设置的不对。（我之前的错误在这里，下图是在Ubuntu中用`service sshd status`查看日志得到的）
> > 
> > ![](https://upload-images.jianshu.io/upload_images/6767178-4863553aad04883d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)
> 
> *   Ubuntu中配置openssh-server开机自动启动：打开`/etc/rc.local`文件，在exit 0语句前加入：`/etc/init.d/ssh start`

#### 3）SSH客户端的简单使用

![](https://upload-images.jianshu.io/upload_images/6767178-f8352ddd4336b0b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/901)

`ssh [-p port] user@remote`命令中有三个要素：

*   `user`是远程机器上的用户名，如果不指定的话默认为当前用户。
*   `remote`是远程机器的地址，可以是 **IP** 或 **域名** ，或者是后面会提到的 **别名**。
*   `port`是**SSH Server**监听的端口，如果不指定，就为默认值`22`。

> 提示：
> 
> *   使用`exit`退出当前用户的登陆。
> *   `ssh`这个终端命令只能在Unix或Linux中使用，在Windows中要安装客户端软件。

#### 4）Windows下SSH客户端软件的安装和使用

提示：建议从官网下载。
 `PuTTy`：[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
 
 `XShell`： [http://www.netsarang.com/download/main.html](http://www.netsarang.com/download/main.html)

![](https://upload-images.jianshu.io/upload_images/6767178-7c03ee370cfe8fa5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/536)

PuTTy

![](https://upload-images.jianshu.io/upload_images/6767178-d9951e6c54e2b6d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/857)

XShell

#### 5）SSH高级使用

> 有关ssh配置的信息都放在用户家目录下`.ssh`目录下。

**免密码登陆：**

![](https://upload-images.jianshu.io/upload_images/6767178-ed98c323192529bc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/916)

**配置别名：**

每次都输入`ssh -p port user@remote`，时间久了会觉得很麻烦，特别是当`user`, `remote`和`port`都得输入，而且还不好记忆，而** 配置别名 **可以让我们进一步偷懒，譬如用：`ssh mac`来替代上面这么一长串，那么就在`~/.ssh/config`里面追加以下内容：

```
Host mac
    HostName ip地址
    User itheima
    Port 22

```

保存之后，即可用`ssh mac`实现远程登录了，`scp`同样可以使用
 提示：`touch config` 之后 `gedit config`或者`vi config`，然后就可以追加了。

### <补>远程拷贝文件：scp

`scp` 就是 secure copy，是一个在Linux下来进行远程拷贝文件的命令。
 它的地址格式与ssh基本相同，需要注意的是，在指定端口时用的是大写的`-P`。

![](https://upload-images.jianshu.io/upload_images/6767178-c9c79634e7f2f564.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/902)

```
# 把本地当前目录下的 01.py 文件 复制到 远程 家目录下的 Desktop/01.py
# 注意：`:` 后面的路径如果不是绝对路径，则以用户的家目录作为参照路径
scp -P port 01.py user@remote:Desktop/01.py

# 把远程 家目录下的 Desktop/01.py 文件 复制到 本地当前目录下的 01.py
scp -P port user@remote:Desktop/01.py 01.py

# 加上 -r 选项可以传送文件夹
# 把当前目录下的 demo 文件夹 复制到 远程 家目录下的 Desktop
scp -r demo user@remote:Desktop

# 把远程 家目录下的 Desktop 复制到 当前目录下的 demo 文件夹
scp -r user@remote:Desktop demo

```

![](https://upload-images.jianshu.io/upload_images/6767178-f9cfe8ae1af7c8bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/900)

scp常用选项

注意：

*   `scp`这个终端命令只能在Unix或Linux系统中使用。
*   如果在Windows系统中，可以安装PuTTy使用`pscp`命令行工具，或者安装FileZilla（[https://filezilla-project.org/](https://filezilla-project.org/)）使用FTP进行文件传输。
    FileZilla

> *   除了用`scp`命令拷贝，还可以用ftp服务上传，安装ftp服务：`sudo apt-get install vsftpd`。
> *   ftp服务的配置：`sudo vi /etc/vsftpd.conf`，在配置文件中查找并修改以下信息
> 
> ```
> anonymous_enable=NO #不允许匿名用户登陆
> local_enable=YES  #允许本机登陆
> local_root=/home/handy/ftp #指定ftp上传下载目录  
> ####一般使用FileZilla时只需要更改###
> write_enable=YES #允许上传文件到ftp服务器！！！
> ###################################
> chroot_list_enable=YES 
> chroot_list_file=/etc/vsftpd.chroot_list  #允许vsftpd.chroot_list文件中的用户登陆ftp服务器
> 
> ```
> 
> 更改配置文件完成后，要重启服务：`service vsftpd restart`
> 
> 测试上传功能，登陆ftp服务器：`ftp IP`
>  上传命令，可以把文件上传到ftp服务器：`put somefile`
>  下载命令，可以把ftp服务器上的文件下载到本地：`get somefile`
>  也可用图形界面的FileZilla或Xftp。
> 
> > 解决上传的中文乱码文件的删除、改名等操作
> >  `ls -i`：显示文件索引节点号（inode）。一个索引节点代表一个文件；
> >  `find -inum 节点号 -delete`：查找符合指定的inode编号的文件并删除，不能删除非空目录；
> >  更名：`find . -inum 节点号 -exec mv {} 新名字 \`
> >  删除：`find ./ -inum 节点号 -exec rm -rf {} \`
> >  {}是占位符，find出来的，每一个文件，的意思。对于每一个文件，占座，等find出来后，放到对应的{}的位置。\是表示 -exec 命令终结的的符号。

# 七、Ubuntu软件安装的常用命令

### <1>安装/卸载软件：apt

`apt`是advanced packaging tool的缩写，是Linux下的一款安装包管理工具，可以在终端中安装/卸载/更新软件包。

apt常用命令

提示：apt的安装命令其实不用记忆，在终端中如果没有这个命令，系统会提示安装。

### <2>配置软件源

如果希望在Ubuntu中安装软件**更加快速**，可以通过**设置镜像源**，选择一个访问网速更快的服务器，来提供软件下载/安装服务。
 提示：更换服务器之后，需要一个相对比较长时间的更新过程，需要耐心等待。更新完成后，再安装软件就会从新设置的服务器下载安装了。

> 所谓**镜像源**，就是所有服务器的内容是相同的（镜像），但是其所在位置不同，国内的服务器一般会快些。
> 
> 软件和更新

# 八、vi编辑器的常用命令

### <1> vi简介

在工作中，要对 **服务器** 上的文件进行 **简单** 的修改，可以使用 `ssh` 远程登录到服务器上，并且使用 `vi` 进行快速的编辑即可
 常见需要修改的文件包括：**源程序**、**配置文件**，例如 `ssh` 的配置文件 `~/.ssh/config`

> 在没有图形界面的环境下，要编辑文件，`vi` 是最佳选择！
>  每一个要使用 Linux 的程序员，都应该或多或少的学习一些 `vi` 的常用命令

在很多 `Linux` 发行版中，直接把 `vi` 做成 `vim` 的软连接

#### vi

`vi` 是 `Visual interface` 的简称，是 `Linux` 中 **最经典** 的文本编辑器
 `vi` 的核心设计思想 —— **让程序员的手指始终保持在键盘的核心区域，就能完成所有的编辑操作**

![](https://upload-images.jianshu.io/upload_images/6767178-0b296c8e83d8afce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)

`vi` 的特点：**没有图形界面** 的 **功能强大** 的编辑器、只能是编辑 **文本内容**，不能对字体、段落进行排版、**不支持鼠标操作**、**没有菜单**、**只有命令**、`vi` 编辑器在 **系统管理**、**服务器管理** 编辑文件时，**其功能永远不是图形界面的编辑器能比拟的**。

#### vim

**vim = vi improved**
 `vim` 是从 `vi` 发展出来的一个文本编辑器，支持 **代码补全**、**编译** 及 **错误跳转** 等方便编程的功能特别丰富，在程序员中被广泛使用，被称为 **编辑器之神**

### <2> 打开和新建文件

```
$ vi 文件名

```

*   如果文件已经存在，会直接打开该文件
*   如果文件不存在，会新建一个文件

### <3>打开文件并且定位行

在日常工作中，有可能会遇到 **打开一个文件，并定位到指定行** 的情况
 例如：在开发时，**知道某一行代码有错误**，可以 **快速定位** 到出错代码的位置
 ，这个时候，可以使用以下命令打开文件

```
$ vi 文件名 +行数

```

提示：如果只带上 `+` 而不指定行号，会直接**定位到文件末尾**，如果不带`+`号，那么会直接**定位到文件开头**。

### <4>异常处理

如果 `vi` 异常退出，在磁盘上可能会保存有 **交换文件**

![](https://upload-images.jianshu.io/upload_images/6767178-65e3c2d826f4963a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/980)

下次再使用 `vi` 编辑该文件时，会看到以下屏幕信息，按下字母 `d` 可以 **删除交换文件** 即可，之前的异常退出涉及的修改消失。

![](https://upload-images.jianshu.io/upload_images/6767178-9d80557ac1301d40.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)

提示：按下键盘时，注意输入法为英文状态。

### <5> vi 的三种工作模式

`vi` 有三种基本工作模式：

*   **命令模式**
     **打开文件首先进入命令模式**，是使用 `vi` 的 **入口**
     通过 **命令** 对文件进行常规的编辑操作，例如：**定位**、**翻页**、**复制**、**粘贴**、**删除**……
     在其他图形编辑器下，通过 **快捷键** 或者 **鼠标** 实现的操作，都在 **命令模式** 下实现

*   **末行模式** —— 执行 **保存**、**退出** 等操作
     要退出 `vi` 返回到控制台，需要在末行模式下输入命令
     末行模式 是 `vi` 的 **出口**

*   **编辑模式** —— 正常的编辑文字

    ![](https://upload-images.jianshu.io/upload_images/6767178-3b7457511b982549.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/929)

    vi的模式

> 提示：在 `Touch Bar` 的 Mac 电脑上 ，按 `ESC` 不方便，可以使用 `CTRL + [` 替代

**末行模式命令：**

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| w | write | 保存 |
| q | quit | 退出，如果没有保存，不允许退出 |
| q! | quit | 强行退出，不保存退出 |
| wq | write & quit | 保存并退出 |
| x | 保存并退出 |

### <6> 常用命令

#### 命令学习线路图

> 1.  重复命令多次
>     *   在命令模式下，**先输入一个数字**，**再跟上一个命令**，可以让该命令 **重复执行指定次数**
> 2.  移动和选择（**多练**）
>     *   `vi` 之所以快，关键在于 **能够快速定位到要编辑的代码行**
>     *   **移动命令** 能够 和 **编辑操作** 命令 **组合使用**
> 3.  编辑操作
>     *   **删除**、**复制**、**粘贴**、**替换**、**缩排**
> 4.  撤销和重复
> 5.  查找替换

#### 1\. 移动（基本）

*   要熟练使用 `vi`，首先应该学会怎么在 **命令模式** 下样快速移动光标
*   **编辑操作命令**，能够和 **移动命令** 结合在一起使用

##### 1) 上、下、左、右

| 命令 | 功能 | 手指 |
| --- | --- | --- |
| h | 向左 | 食指 |
| j | 向下 | 食指 |
| k | 向上 | 中指 |
| l | 向右 | 无名指 |

![](https://upload-images.jianshu.io/upload_images/6767178-d7a0c2ccc5899177.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)

移动光标

##### 2) 行内移动

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| w | word | 向后移动一个单词 |
| b | back | 向前移动一个单词 |
| 0 | 行首 |
| ^ | 行首，第一个不是空白字符的位置 |
| $ | 行尾 |

##### 3) 行数移动

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| gg | go | 文件顶部 |
| G | go | 文件末尾 |
| 数字gg | go | 移动到 数字 对应行数 |
| 数字G | go | 移动到 数字 对应行数 |
| :数字 | 移动到 数字 对应行数 |

##### 4) 屏幕移动

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| Ctrl + b | back | 向上翻页 |
| Ctrl + f | forward | 向下翻页 |
| H | Head | 屏幕顶部 |
| M | Middle | 屏幕中间 |
| L | Low | 屏幕底部 |

#### 2\. 移动（程序）

##### 1) 段落移动

*   `vi` 中使用 空行 来区分段落
*   在程序开发时，通常 **一段功能相关的代码会写在一起** —— 之间没有空行

| 命令 | 功能 |
| --- | --- |
| { | 上一段 |
| } | 下一段 |

##### 2) 括号切换

*   在程序世界中，`()`、`[]`、`{}` 使用频率很高，而且 **都是成对出现的**

| 命令 | 功能 |
| --- | --- |
| % | 括号匹配及切换 |

##### 3) 标记

*   在开发时，某一块代码可能**需要稍后处理**，例如：编辑、查看
*   此时先使用 `m` 增加一个标记，这样可以 **在需要时快速地跳转回来** 或者 **执行其他编辑操作**
*   **标记名称** 可以是 `a~z` 或者 `A~Z` 之间的任意 **一个** 字母
*   添加了标记的 **行如果被删除**，**标记同时被删除**
*   如果 **在其他行添加了相同名称的标记**，**之前添加的标记也会被替换掉**

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| mx | mark | 添加标记 x，x 是 a~z 或者 A~Z 之间的任意一个字母 |
| 'x | 直接定位到标记 x 所在位置 |

#### 3\. 选中文本（可视模式）

*   在 `vi` 中要选择文本，需要先使用 `Visual` 命令切换到 **可视模式**
*   `vi` 中提供了 **三种** 可视模式，可以方便程序员选择 **选中文本的方式**
*   按 `ESC` 可以放弃选中，返回到 **命令模式**

| 命令 | 模式 | 功能 |
| --- | --- | --- |
| v | 可视模式 | 从光标位置开始按照正常模式选择文本 |
| V | 可视行模式 | 选中光标经过的完整行 |
| Ctrl + v | 可视块模式 | 垂直方向选中文本 |

注意：**可视模式**下，可以和 **移动命令** 连用，例如：`ggVG` 能够选中所有内容

#### 4\. 撤销和恢复撤销

*   在学习编辑命令之前，先要知道怎样撤销之前一次 **错误的** 编辑动作！

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| u | undo | 撤销上次命令 |
| CTRL + r | redo | 恢复撤销的命令 |

#### 5\. 删除文本

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| x | cut | 删除光标所在字符，或者选中文字 |
| d(移动命令) | delete | 删除移动命令对应的内容 |
| dd | delete | 删除光标所在行，可以 ndd 复制多行 |
| D | delete | 删除至行尾 |

> 提示：如果使用 **可视模式** 已经选中了一段文本，那么无论使用 `d` 还是 `x`，都可以删除选中文本

*   删除命令可以和 **移动命令** 连用，以下是常见的组合命令：
     dw # 从光标位置删除到单词末尾
     d0 # 从光标位置删除到一行的起始位置
     d} # 从光标位置删除到段落结尾
     ndd # 从光标位置向下连续删除 n 行
     d代码行G # 从光标所在行 删除到 指定代码行 之间的所有代码
     d'a # 从光标所在行 删除到 标记a 之间的所有代码

> 提示：可使用`:set nu`和`:set nonu`设置行号的显示与否。

#### 6\. 复制、粘贴

*   `vi` 中提供有一个 **被复制文本的缓冲区**
    *   **复制** 命令会将选中的文字保存在缓冲区
    *   **删除** 命令删除的文字会被保存在缓冲区
    *   在需要的位置，使用 **粘贴** 命令可以将缓冲区的文字插入到光标所在位置

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| y(移动命令) | copy | 复制 |
| yy | copy | 复制一行，可以 nyy 复制多行 |
| p | paste | 粘贴 |

**提示**

*   命令 `d`、`x` 类似于图形界面的 **剪切操作** —— `CTRL + X`
*   命令 `y` 类似于图形界面的 **复制操作** —— `CTRL + C`
*   命令 `p` 类似于图形界面的 **粘贴操作** —— `CTRL + V`
*   `vi` 中的 **文本缓冲区同样只有一个**，如果后续做过 **复制、剪切** 操作，之前缓冲区中的内容会被替换

**注意**

*   `vi` 中的 **文本缓冲区** 和系统的 **剪贴板** 不是同一个
*   所以在其他软件中使用 `CTRL + C` 复制的内容，不能在 `vi` 中通过 `P` 命令粘贴
*   可以在 **编辑模式** 下使用 **鼠标右键粘贴**

#### 7\. 替换

| 命令 | 英文 | 功能 | 工作模式 |
| --- | --- | --- | --- |
| r | replace | 替换当前字符 | 命令模式 |
| R | replace | 替换当前行光标后的字符 | 替换模式 |

*   `R` 命令可以进入 **替换模式**，替换完成后，按下 `ESC` 可以回到 **命令模式**
*   **替换命令** 的作用就是不用进入 **编辑模式**，对文件进行 **轻量级的修改**

#### 8\. 缩排和重复执行

| 命令 | 功能 |
| --- | --- |
| >> | 向右增加缩进 |
| << | 向左减少缩进 |
| . | 重复上次命令 |

*   **缩排命令** 在开发程序时，**统一增加代码的缩进** 比较有用！
    *   一次性 **在选中代码前增加 4 个空格**，就叫做 **增加缩进**
    *   一次性 **在选中代码前删除 4 个空格**，就叫做 **减少缩进**
*   在 **可视模式** 下，缩排命令只需要使用 **一个** `>` 或者 `<`

> 在程序中，**缩进** 通常用来表示代码的归属关系
> 
> *   前面空格越少，代码的级别越高
> *   前面空格越多，代码的级别越低

#### 9\. 查找

#### 常规查找

| 命令 | 功能 |
| --- | --- |
| /str | 查找 str |

*   查找到指定内容之后，使用 `Next` 查找下一个出现的位置：
    *   `n`: 查找下一个
    *   `N`: 查找上一个
*   如果不想看到高亮显示，可以随便查找一个文件中不存在的内容即可

##### 单词快速匹配

| 命令 | 功能 |
| --- | --- |
| * | 向后查找当前光标所在单词 |
| # | 向前查找当前光标所在单词 |

*   在开发中，通过单词快速匹配，可以快速看到这个单词在其他什么位置使用过

#### 10\. 查找并替换

*   在 `vi` 中查找和替换命令需要在 **末行模式** 下执行
*   记忆命令格式：

```
:%s///g

```

##### 1) 全局替换

*   **一次性**替换文件中的 **所有出现的旧文本**
*   命令格式如下：

```
:%s/旧文本/新文本/g

```

##### 2) 可视区域替换

*   **先选中** 要替换文字的 **范围**
*   命令格式如下：

```
:s/旧文本/新文本/g

```

##### 3) 确认替换

*   如果把末尾的 `g` 改成 `gc` 在替换的时候，会有提示！**推荐使用！**

> c表示conform。

```
:%s/旧文本/新文本/gc

```

1.  `y` - `yes` 替换
2.  `n` - `no` 不替换
3.  `a` - `all` 替换所有
4.  `q` - `quit` 退出替换
5.  `l` - `last` 最后一个，并把光标移动到行首
6.  `^E` 向下滚屏
7.  `^Y` 向上滚屏

#### 11\. 插入命令

*   在 `vi` 中除了常用的 `i` 进入 **编辑模式** 外，还提供了以下命令同样可以进入编辑模式：

| 命令 | 英文 | 功能 | 常用 |
| --- | --- | --- | --- |
| i | insert | 在当前字符前插入文本 | 常用 |
| I | insert | 在行首插入文本 | 较常用 |
| a | append | 在当前字符后添加文本 |
| A | append | 在行末添加文本 | 较常用 |
| o | 在当前行后面插入一空行 | 常用 |
| O | 在当前行前面插入一空行 | 常用 |

![](https://upload-images.jianshu.io/upload_images/6767178-9da04400e8edec1d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/484)

插入命令

> 要快速打出大写字母，使用：`shift 字母`。

##### 演练 1 —— 编辑命令和数字连用

*   在开发中，可能会遇到连续输入 `N` 个同样的字符

> 在 `Python` 中有简单的方法，但是其他语言中通常需要自己输入

*   例如：`**********` 连续 10 个星号

要实现这个效果可以在 **命令模式** 下

1.  输入 `10`，表示要重复 10 次
2.  输入 `i` 进入 **编辑模式**
3.  输入 `*` 也就是重复的文字
4.  按下 `ESC` 返回到 **命令模式**，返回之后 `vi` 就会把第 `2、3` 两步的操作重复 `10` 次

> 提示：正常开发时，在 **进入编辑模式之前，不要按数字**

##### 演练 2 —— 利用 可视块 给多行代码增加注释

*   在开发中，可能会遇到一次性给多行代码 **增加注释** 的情况

> 在 `Python` 中，要给代码增加注释，可以在代码前增加一个 `#`

要实现这个效果可以在 **命令模式** 下

1.  移动到要添加注释的 **第 1 行代码**，按 `^` 来到行首
2.  按 `CTRL + v` 进入 **可视块** 模式
3.  使用 `j` 向下连续选中要添加的代码行
4.  输入 `I` 进入 **编辑模式**，并在 **行首插入**，注意：一定要使用 **I**
5.  输入 `#` 也就是注释符号
6.  按下 `ESC` 返回到 **命令模式**，返回之后 `vi` 会在之前选中的每一行代码 **前** 插入 `#`

#### 12\. 分屏命令

*   属于 `vi` 的高级命令 —— 可以 **同时编辑和查看多个文件**

##### 末行命令扩展

**末行命令** 主要是针对文件进行操作的：**保存**、**退出**、**保存&退出**、**搜索&替换**、**另存**、**新建**、**浏览文件**

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| :e . | edit | 会打开内置的文件浏览器，浏览要当前目录下的文件 |
| :n 文件名 | new | 新建文件 |
| :w 文件名 | write | 另存为，但是仍然编辑当前文件，并不会切换文件 |

> 提示：切换文件之前，必须保证当前这个文件已经被保存！

*   已经学习过的 **末行命令**：

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| :w | write | 保存 |
| :q | quit | 退出，如果没有保存，不允许退出 |
| :q! | quit | 强行退出，不保存退出 |
| :wq | write & quit | 保存并退出 |
| :x | 保存并退出 |
| :%s///gc | 确认搜索并替换 |

> 在实际开发中，可以使用 `w` 命令 **阶段性的备份代码**

##### 分屏命令

*   使用 **分屏命令**，可以 **同时编辑和查看多个文件**

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| :sp [文件名] | split | 横向增加分屏 |
| :vsp [文件名] | vertical split | 纵向增加分屏 |

##### 1) 切换分屏窗口

> 分屏窗口都是基于 `CTRL + W` 这个快捷键的，`w` 对应的英文单词是 `window`

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| w | window | 切换到下一个窗口 |
| r | reverse | 互换窗口 |
| c | close | 关闭当前窗口，但是不能关闭最后一个窗口 |
| q | quit | 退出当前窗口，如果是最后一个窗口，则关闭 vi |
| o | other | 关闭其他窗口 |

##### 2) 调整窗口大小

> 分屏窗口都是基于 `CTRL + W` 这个快捷键的，`w` 对应的英文单词是 `window`

| 命令 | 英文 | 功能 |
| --- | --- | --- |
| + | 增加窗口高度 |
| - | 减少窗口高度 |
| > | 增加窗口宽度 |
| < | 减少窗口宽度 |
| = | 等分窗口大小 |

> 调整窗口宽高的命令可以和数字连用，例如：`5 CTRL + W +` 连续 5 次增加高度

#### 13\. 常用命令速查图

![](https://upload-images.jianshu.io/upload_images/6767178-c30cb17c897b7aa8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)

##### vimrc

*   `vimrc` 是 `vim` 的配置文件，可以设置 vim 的配置，包括：**热键**、**配色**、**语法高亮**、**插件** 等
*   `Linux` 中 `vimrc` 有两个位置，**家目录下的配置文件优先级更高**

```
/etc/vim/vimrc
~/.vimrc

```

*   常用的插件有：
    *   代码补全
    *   代码折叠
    *   搜索
    *   Git 集成
    *   ……
*   网上有很多高手已经配置好的针对 `python` 开发的 `vimrc` 文件，可以下载过来直接使用，或者等大家多 `Linux` 比较熟悉后，再行学习！

# Tips：

终端中的字体大小更改：放大是`ctrl shift +`，缩小是`ctrl -`。
 终端中退出某个程序：往往是`q`，可能是`ctrl c`或是`ctrl d`。
 以新标签页的形式打开一个终端：`ctrl alt T`。

# 全文思维导图

![](https://upload-images.jianshu.io/upload_images/6767178-d9227f824880f8eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)
Linux 基础.png
