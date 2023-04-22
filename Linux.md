# Linux

# 1:Linux简介

## 1.1:介绍

Linux 内核最初只是由芬兰人林纳斯·托瓦兹在赫尔辛基大学上学时出于个人爱好而编写的。

Linux 是一套免费使用和自由传播的类 Unix 操作系统

是一个基于 POSIX 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统

Linux 能运行主要的 UNIX 工具软件、应用程序和网络协议。它支持 32 位和 64 位硬件

Linux 继承了 Unix 以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统



## 1.2:Linux的目录结构

![image-20230422151553169](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422151553169.png)

- /，根目录是最顶级的目录了
- Linux 只有一个顶级目录：/
- 路径描述的层次关系同样适用/来表示
- /home/zzx/a.txt，表示根目录下的home文件夹内有 zzx 文件夹，内有 a.txt 文件

## 1.3:Linux的发行版

目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS等

无论是哪个版本，其内核都是Linux内核，主要是各个版本在上层封装的函数不同



# 2:Linux前置知识

## 2.1:隐藏标识

在Linux中以.开头的，均是隐藏的

默认不显示出来，需要 -a 选项才可查看到





## 2.2:相对路径、绝对路径

相对路径，非 / 开头的称之为相对路径

相对路径表示以当前目录作为起点，去描述路径

如 test/a.txt，表示当前工作目录内的 test 文件夹内的a.txt文件



绝对路径，以 / 开头的称之为绝对路径

绝对路径从根开始描述路径



## 2.3:特殊路径符

.   表示当前，比如 ./a.txt ，表示当前文件夹内的 a.txt 文件

..  表示上级目录，比如 ../ 表示上级目录，../../ 表示上级的上级目录

~  表示用户的 HOME 目录，比如 cd ~，即可切回用户HOME目录



## 2.4:Home目录

每一个用户在Linux系统中都有自己的专属工作目录，称之为HOME目录

- 普通用户的HOME目录，默认在：/home/用户名

- root用户的HOME目录，在：/root

在我们使用账号密码登陆终端后，默认的工作目录就是用户的HOME目录

## 2.5:VI编辑器

Linux通常都已经默认安装好了 vi 或 Vim 文本编辑器，我们只需要通过vim命令就可以直接打开vim编辑器了

VI/VIM 编辑器共分为三种模式，下面是他们的关系

![image-20230422161459228](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422161459228.png)

# 3:Linux的常用命令

## 3.1:帮助命令

可以通过：命令 --help 查看命令的帮助手册

例如查看 ls 的帮助命令：ls --help



可以通过：man 命令查看某命令的详细手册

录入查看 ls 的详细手册：man ls



一般使用 help 指令就够了



## 3.2:ls命令

功能：列出文件夹信息

语法：ls [-l -a] [参数]

- 参数：被查看的文件夹，不提供参数，表示查看当前工作目录
- -l，以列表形式查看
- -a，显示隐藏文件

使用 ll 等效于 ls -l

至于参数一般我们都不用，因为一般就在当前的工作目录内使用



## 3.3:pwd命令

功能：展示当前工作目录

语法：pwd



## 3.4:cd命令

功能：切换工作目录

语法：cd  [目标目录]

参数：目标目录，要切换去的地方，不提供默认切换到当前登录用户HOME目录



## 3.5:mkdir命令

功能：创建文件夹

语法：mkdir [-p] 参数

- 参数：被创建文件夹的路径
- 选项：-p，可选，表示创建前置路径

例如 mkdir -p a1/a2/a3，就是创建了三个目录，分别是 a1 下面有 a2、a2 下面有 a3 目录



## 3.6:touch命令

功能：创建文件

语法：touch 参数

参数：被创建的文件路径

至于参数一般我们都不写路径，因为一般就在当前的工作目录内使用，默认就创建在工作目录下



## 3.7:cat命令

功能：查看文件内容

语法：cat 参数

参数：被查看的文件路径



## 3.8:more命令

功能：查看文件，可以支持翻页查看

语法：more 参数

参数：被查看的文件路径

在查看过程中：

- 使用空格键翻页
- 使用 q 退出查看



## 3.9:cp命令

功能：复制文件、文件夹

语法：cp [-r] 参数1 参数2

- 参数1，被复制的
- 参数2，要复制去的地方
- 选项：-r，可选，表示递归复制，复制文件夹使用

示例：

- cp a.txt b.txt，复制当前目录下 a.txt 为 b.txt
- cp a.txt test/，复制当前目录 a.txt 到 test 文件夹内
- cp -r test test2，复制文件夹 test 到当前文件夹内为 test2 存在



## 3.10:mv命令

功能：移动文件、文件夹

语法：mv 参数1 参数2

- 参数1：被移动的
- 参数2：要移动去的地方，参数 2 如果不存在，则会进行改名



## 3.11:rm命令

功能：删除文件、文件夹

语法：rm [-r -f] 参数...参数

- 参数：支持多个，每一个表示被删除的，空格进行分隔
- 选项：-r，删除文件夹使用
- 选项：-f，强制删除，不会给出确认提示，一般 root 用户会用到



## 3.12:which命令

功能：查看命令的程序本体文件路径

语法：which 参数

参数：被查看的命令

示例：which cat        得到的结果======>          /usr/bin/cat       

表明  cat  命令在   /usr/bin/cat     

## 3.13:find命令

功能：搜索文件

语法：find 路径 -name 参数

路径，搜索的起始路径

参数，搜索的关键字，支持通配符， 比如：*conf 表示搜索任意以 conf 结尾的文件



示例：查找 /etc 目录下面所有 .conf 结尾的文件

命令：find /etc/ -name "*.conf"

## 3.14:grep命令

功能：把前面的结构进行关键字过滤

语法：grep [-n] 关键字 文件路径

选项 -n，可选，表示在结果中显示匹配的行的行号

参数，关键字，必填，表示过滤的关键字，带有空格或其它特殊符号，建议使用””将关键字包围起来

参数，文件路径，必填，表示要过滤内容的文件路径，可作为内容输入端口



参数文件路径，也可以作为管道符的输入

例如我们有一个文件 my.log

![image-20230422155534462](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422155534462.png)

我们要查看里面含有 ERROR 的部分：grep ERROR my.log

![image-20230422155650410](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422155650410.png)



## 3.15:管道符 | 命令

写法：|

功能：将符号左边的结果，作为符号右边的输入

示例：cat my.log | grep ERROR

![image-20230422155650410](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422155650410.png)

其实就是将 cat my.log 的结果，作为 grep 命令的输入，过滤条件为含有 ERROR 的字符



管道符 grep 可以支持嵌套：



## 3.16:ps命令

功能：查看进程信息

语法：ps -ef，查看全部进程信息，可以搭配 grep 做过滤：ps -ef | grep xxx

## 3.17:echo命令

功能：输出内容

语法：echo 参数

参数：被输出的内容

例如：查看环境变量 PATH：echo $PATH 



## 3.18:tail命令

功能：查看文件尾部内容

语法：tail [-f] 参数

参数：被查看的文件

选项：-f，持续跟踪文件修改

这个常被用于查看日志文件

![image-20230422160332830](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422160332830.png)

左下角的红色会一直闪动，表明一直在监视



这个时候我们新开一个窗口写入一些文本：ps -ef | grep tomcat >> my.log

![image-20230422160450588](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422160450588.png)

这个时候就会立刻监视到数据到变化，常用于查看日志

## 3.19:head命令

功能：查看文件头部内容

语法：head [-n] 参数

参数：被查看的文件

选项：-n，查看的行数

使用跟 tail 的语法类似



## 3.20:重定向符

功能：将符号左边的结果，输出到右边指定的文件中去

使用 **>** 表示覆盖输出

使用 **>>** 表示追加输出



# 4:Linux常用操作

## 4.1:systemctl

功能：控制系统服务的启动关闭等

语法：systemctl start | stop | restart | disable | enable | status 服务名

- start，启动
- stop，停止
- status，查看状态
- disable，关闭开机自启
- enable，开启开机自启
- restart，重启

## 4.2:软链接

功能：创建文件、文件夹软链接（快捷方式）

语法：ln -s 参数1 参数2

- 参数1：被链接的
- 参数2：要链接去的地方（快捷方式的名称和存放位置）

比如：我们为我们的一个日志文件创建一个软连接【快捷方式】

命令：ln -s my.log link

查看 my.log 文件的时候则可以直接使用 cat link  <==>  cat my.log



## 4.3:查看ip地址

使用 ifconfig 即可查看到 Linux 的 IP 地址

![image-20230422162033685](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422162033685.png)



## 4.4:主机名

功能：查看Linux系统的名称

查看：hostname

设置：hostnamectl set-hostname 主机名



## 4.5:kill命令

语法：kill -9 进程ID

怎么查看进程ID：ps -ef | grep xxx



## 4.6:netstat命令

功能：查看端口占用

用法：netstat -anp | grep xxx

例如：查看 6379 的占用情况：netstat -anp | grep 6379



## 4.7:wget命令

语法：wget url

例如：下载tomcat：wget https://mirrors.cnnic.cn/apache/tomcat/tomcat-9/v9.0.7/bin/apache-tomcat-9.0.7.tar.gz



## 4.8:top命令

功能：查看主机运行状态

语法：top，查看基础信息

常用可选项：top -p pid，仅仅查看这一个 pid 的情况



## 4.9:df命令

命令：df -h  查看磁盘占用，使用 -h 是为了更加人性化的显示内容

![image-20230422164142666](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422164142666.png)



## 4.10:环境变量

临时设置：export 变量名 = 变量值

永久设置：

- 针对单个用户，设置用户 HOME 目录内：.bashrc文件
- 针对全局，设置/etc/profile【常用】

![image-20230422164435323](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422164435323.png)



## 4.11:$符号

可以取出指定的环境变量的值

语法：$变量名

示例：

echo $PATH，输出PATH环境变量的值

## 4.12:su命令

切换用户

语法：su 用户



## 4.13:sudo命令

可以让一条普通的命令带有 root 权限



## 4.14:chmod命令

修改文件、文件夹权限

语法：chmod [-R] 权限 参数

权限，要设置的权限，比如755，表示：rwxr-xr-x【最前面的不是权限，而是文件的类型】

文件调用权限分为三级 : 文件所有者、用户组、其它用户

![image-20230422165321518](https://zzx-note.oss-cn-beijing.aliyuncs.com/linux/image-20230422165321518.png)

参数，被修改的文件、文件夹

选项 -R，设置文件夹和其内部全部内容一样生效



- 

  ![image-20221027222512274](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/27/20221027222512.png)



## 4.15:env命令

查看系统全部的环境变量

语法：env



## 4.16:用户组管理

创建用户组：group add 用户组名

删除用户组：groupdel 用户组名



## 4.17:用户管理

以下命令需要在 root 用户下执行

创建用户
useradd[-g -d]用户名

选项： -g指定用户的组，不指定-g，会创建同名组并自动加入


选项： -d指定用户HOME路径，不指定，HOME 目录默认在: /home/用户名



删除用户

userdel[-r]用户名

选项：-r，删除用户的HOME目录，不使用-r，删除用户时，HOME目录保留



查看用户所属组

id [用户名]

参数：用户名，被查看的用户，如果不提供则查看自身



## 4.18:genenv命令

getenv group，查看系统全部的用户组

getenv passwd，查看系统全部的用户



# 5:Linux安装常用软件

我们一般会使用Docker来安装我们的常见软件，具体见我的这篇笔记内容：

Gitee笔记链接：https://gitee.com/jxlzzx/docker-software

Github笔记链接：https://github.com/ZZX9599/Docker-Software







