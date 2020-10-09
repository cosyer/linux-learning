# linux-learning
记录学习linux命令

注：这里只列出常用命令, 基本上能满足日常工作所需, 如果想要更系统的可能需要翻阅[Linux命令大全](https://man.linuxde.net/)。
---

# 目录
- 文件管理
  - [head](#head)
  - [tail](#tail)
  - [ls](#ls)
  - [pwd](#pwd)
  - [wc](#wc)
  - [find](#find)
  - [mkdir](#mkdir)
  - [chattr](#chattr)
  - [more](#more)
  - [paste](#paste)
  - [stat](#stat)
  - [grep](#grep)
  - [touch](#touch)
  - [cd](#cd)
  - [rm](#rm)
  - [rmdir](#rmdir)
  - [cp](#cp)
  - [cat](#cat)
  - [mv](#mv)
  - [locate](#locate)
  - [open](#open)
  - [source](#source)
  - [tree](#tree)
  - [ln](#ln)
  - [file](#file)
- 系统管理
  - [top](#top)
  - [whoami](#whoami)
  - [nohup](#nohup)
  - [watch](#watch)
  - [ping](#ping)
  - [which](#which)
  - [last](#last)
  - [shutdown](#shutdown)
  - [reboot](#reboot)
  - [ps](#ps)
  - [uptime](#uptime)
  - [crontab](#crontab)
  - [su](#su)
  - [uname](#uname)
  - [ifconfig](#ifconfig)
  - [who](#who)
  - [whereis](#whereis)
  - [kill](#kill)
  - [killall](#killall)
  - [chmod](#chmod)
  - [lsof](#lsof)
  - [netstat](#netstat)
  - [w](#w)
  - [chown](#chown)
  - [systemctl](#systemctl)
  - [service](#service)
  - [free](#free)
  - [jobs](#jobs)
  - [type](#type)
  - [printenv](#printenv)
  - [set](#set)
  - [export](#export)
  - [unset](#unset)
  - [alias](#alias)
  - [time](#time)
  - [clear](#clear)
- 压缩、解压
  - [zip](#zip)
  - [unzip](#unzip)
  - [gzip](#gzip)
  - [bzip2](#bzip2)
  - [tar](#tar)
- 加解密
  - [md5sum](#md5sum)
  - [base64](#base64)
- 网络
  - [wget](#wget)
  - [curl](#curl)
  - [scp](#scp)
- 磁盘
  - [df](#df)
  - [du](#du)
- 包管理
  - [yum](#yum)
  - [apt-get](#apt-get)
- 其他
  - [目录名称含义](#目录名称含义)
  - [echo](#echo)
  - [date](#date)
  - [man](#man)
  - [sleep](#sleep)
  - [history](#history)
  - [xargs](#xargs)
  - [cal](#cal)

## 目录名称含义
- / - 虚拟目录的根目录，通常不会在这里存储文件
- /bin - 二进制目录，存放许多用户级的GNU工具
- /boot - 启动目录，存放启动文件
- /dev - 设备目录，Linux在这里创建设备节点
- /etc - 系统配置文件目录
- /home - 主目录，Linux在这里创建用户目录
- /lib - 库目录，存放系统和应用程序的库文件
- /media - 媒体目录，可移动媒体设备的常用挂载点
- /mnt - 挂载目录，另一个可移动媒体设备的常用挂载点
- /opt - 可选目录，常用于存放第三方软件包和数据文件
- /proc - 进程目录，存放现有硬件及当期进程的相关信息
- /root - ROOT用户的主目录
- /sbin - 系统二进制目录，存放许多GNU管理员级工具
- /run - 运行目录，存放系统运作时的运行时数据
- /srv - 服务目录，存放本地服务的相关文件
- /sys - 系统目录，存放系统硬件信息的相关文件
- /tmp - 临时目录，可以在该目录中创建和删除临时工作文件
- /usr - 用户二进制目录，大量用户级的GNU工具和数据文件都存储在这里
- /var - 可变目录，用以存放经常变化的文件，比如日志文件

## head
显示某个文件的前十行
```bash
# 查看 README.md 前10行
head README.md
# 或者指定多个文件
head README.md package.json
# 指定行数, 覆盖默认的10行
head -n 100 README.md
```

## tail
显示指定文件的末尾部分
```bash
# 默认为显示末尾10行
tail README.md

# 显示末尾20行
tail -n 20 README.md

# 实时监听README.md文件变化
tail -f README.md

# 根据文件名进行追踪, 如果删除后创建相同的文件名会继续追踪
tail -F README.md

# 显示文件的最后10个字符
tail -c README.md
```

## top
实时查看系统执行中的程序
```bash
# 实时监听进程变化
top

# 显示2条
top -n 2

# 显示指定的进程信息
top -p 620
```

## ls
显示目录列表
```bash
# 只显示目录列表
ls

# 显示目录列表的详细信息
ls -l

# 显示指定目录
ls ./src

# 显示目录列表详细信息和大小
ls -lh

# 列出所有文件包括隐藏
ls -a
```


## pwd
显示当前工作目录
```bash
# 没有太多有用的参数，用法很简单
pwd
```


## wc
统计文件的行数、字数、字节数, 常见用于统计代码行数
```bash
# 统计字节数
wc -c README.md

# 统计行数
wc -l README.md

# 统计字数
wc -w README.md

# 统计字符数
wc -m README.md
```

## whoami
显示自身的用户名称, 此命令等价于 `id -un`
```bash
cosyer@192 golang % whoami
cosyer  # 输出
```



## alias
用于简化较长的命令
```bash
# 列出所有已设置的别名
alias

# 删除所有别名
unalias -a

# 设置别名
alias ll='ls -l'
```


## wget
用于从网络下载文件到本地
```bash
# 下载某个文件
wget https://mydearest.cn/robots.txt

# 指定下载后文件名
wget -O ro.txt https://mydearest.cn/robots.txt

# 断开续传，一般用于大文件，防止重新下载
wget -c https://mydearest.cn/robots.txt

# 使用后台下载, 对于大文件非常有用
wget -c https://mydearest.cn/robots.txt
tail -f wget-log   # 查看后台下载进度
```
curl和wget基础功能有诸多重叠，如下载等。非要说区别的话，curl由于可自定义各种请求参数所以在模拟web请求方面更擅长；wget由于支持ftp和Recursive所以
在下载文件方面更擅长。类比的话curl是浏览器，而wget是迅雷9。

1.下载文件
```bash
curl -O http://man.linuxde.net/text.iso                    #O大写，不用O只是打印内容不会下载
wget http://www.linuxde.net/text.iso                       #不用参数，直接下载文件
``` 

2.下载文件并重命名
```bash
curl -o rename.iso http://man.linuxde.net/text.iso         #o小写
wget -O rename.zip http://www.linuxde.net/text.iso         #O大写
```

3.断点续传
```bash
curl -O -C - http://man.linuxde.net/text.iso               #O大写，C大写
wget -c http://www.linuxde.net/text.iso                    #c小写
```

4.限速下载
```bash
curl --limit-rate 50k -O http://man.linuxde.net/text.iso
wget --limit-rate=50k http://www.linuxde.net/text.iso
```

5.显示响应头部信息
```bash
curl -I http://man.linuxde.net/text.iso
wget --server-response http://www.linuxde.net/test.iso
```

6.wget利器--打包下载网站
```bash
wget --mirror -p --convert-links -P /var/www/html http://man.linuxde.net/
```

## df
显示磁盘信息
```bash
# 显示系统磁盘信息
df

# 格式化大小，以kb以上进行显示
df -h

# 查看全部文件系统信息
df -a
```

## du
显示文件或目录所占用的磁盘空间
```bash
# 查看指定文件所占用磁盘空间
du README.md

# 查看指定目录所占用磁盘空间, 输出的最后一行是累计总大小
du src

# -h 以K，M，G为单位，提高信息的可读性。
du -h src  # 20K    src

# -s 只显示总大小，列出最后累计的值
du -s src
```

## find
指定某个目录下查找文件
```bash
# 在当前目录递归搜索文件名为 README.md 文件
find . -name README.md

# 通过通配符进行查找, 必须用引号括着, 这里查找所有后缀为 .md 文件
find . -name "*.md"
find . -iname "*.md"  # 忽略文件大小写

# 排除文件，只要加 ! , 排除掉所有 .md 后缀的文件
find . ! -name "*.md"

# 根据类型进行过滤搜索
# f 普通文件, l 符号连接
# d 目录, c 字符设备
# b 块设备, s 套接字, p Fifo
find . -type f

# 限定目录递归深度
find . -maxdepth 3  # 最大为3个目录
find . -mindepth 3  # 最小为3个目录

# 可以利用find命令进行代码统计，如下
# 统计所有后缀为 .js 文件，忽略掉 node_modules test dist 相关文件
find . -path "*.js" ! -path "*node_modules*" ! -path "*test*" ! -path "*dist*" | xargs wc -l
```

## mkdir
创建目录
```bash
# 在当前目录下创建 temp 目录
mkdir temp

# 创建多层目录
mkdir -p temp/temp2/temp3

# 基于权限创建
mkdir -m 777 temp
```

## touch
创建新的文件
```bash
# 创建一个空文件, 如果文件存在只会修改文件的创建时间
touch README.md
```


## ssh
远程连接服务器工具
```bash
# 简单的连接, 省略了端口号,默认为22
ssh root@192.168.0.0

# 指定端口号连接
ssh -p 23 root@192.168.0.0
```




## nohup
程序以挂起方式运行, 不会影响终端交互

因为程序会以后台的方式运行，所以终端不会输出, 默认情况下会在当前目录生成一个叫 `nohup.out` 文件，里面包含了终端内容。
```bash
# 例如运行一个 node.js 程序
nohup node main.js

# 在当前目录会出现 nohup.out 文件，里面包含了 Hello World
nohup echo "Hello World"
```


## cd
进入指定目录
```bash
# 进入当前 src 目录
cd src

# 回到上一次目录
cd -

# 返回上一级目录
cd ..
cd ../../..   # 返回多级

# 进入家目录
cd ~
cd  # 或者不带任何参数

# 将上一个命令的参数作为cd参数使用
cd !$
```


## echo
输出字符串或者变量

注: 一般情况下字符串不必加双引号, 如果包含转义字符就必须要加
```bash
# 在终端输出 Hello World
echo "Hello World"
echo Hello World    # 也可以不加双引号
echo "Hello\nWorld" # 必须加双引号, 否则无法转义

# 输出变量, 前面加 $ 符号即可, 如果变量不存在输出为空
echo $say

# 也可以将内容输出到指定文件
echo Hello World > 1.txt
```


## time
测试某条命令执行所需花费时间
```bash
# time 后面跟着要测试的命令
# 输出:  0.02s user 0.01s system 0% cpu 6.233 total
time curl https://github.com/cosyer/linux-learning
```


## clear
用于清除当前终端所有信息，本质上只是向后翻了一页，往上滚动还能看到之前的操作信息

注：笔者用得比较多的是 `command + K` 可以完全清除终端所有操作信息。
```bash
clear
```



# rm
删除指定目录或文件

注: 使用此命令需要非常小心, 一但删除无法恢复
```bash
# 删除当前 1.txt 文件
rm 1.txt

# 这条命令比较常用, 强制删除目录或文件
# -r 如果是目录递归删除, -f 强制删除 不发出任何警告
rm -rf ./src
```

## rmdir
删除指定空目录

注：`rmdir` 实际上用得并不多，因为不是很灵活，基本上使用 `rm` 代替
```bash
# 删除当前 temp 空目录, 如果不是空目录会发出警告
rmdir temp

# -p 参数可以删除多层空目录, 发现temp3是空目录删除掉，然后接着往父级找如果还是空目录继续删除...
rmdir -p temp1/temp2/temp3
```

## watch
通常用于监听1个命令的运行结果、定时执行命令

```bash
# 每5秒执行一次 tail 命令, 如果不指定-n 默认为2秒
watch -n 5 "tail README.md"

# -d 高亮显示变化内容
watch -n 5 -d "tail README.md"
```

## ping
测试目标地址是否可连接、延迟度

```bash
# 测试 github.com 连通性, 按 ctrl + C 停止 
ping github.com

# ping 5次后断开
ping -c 5 xiejiahe.com

# 每5秒ping 一次
ping -i 5 xiejiahe.com
```

## cp
拷贝文件或目录

```bash
# 将当前 README.md 文件拷贝到上一层
cp ./README.md ../README.md

# -a 将原文件属性一同拷贝
cp -a ./README.md ../README.md

# -r 拷贝目录
cp -r home ../home

# -i 如果目标文件存在会询问用户是否需要覆盖
cp -i README.md README.md
```

## which
查找某个命令存储在哪个位置, 输出绝对路径, `which` 会在环境变量 `$PATH` 设置的目录里去查找。

注: 可以通过 `echo $PATH` 查看设置的目录. 

```bash
which top  # /usr/bin/top

# 查找pwd发现会找不到，因为 pwd 是bash的内置命令
which pwd

# 打印多个命令
which ls vi
```

## cat
查看指定文件内容

```bash
# 查看 README.md 文件所有内容
cat README.md
cat README.md README2.md  # 或者一次性显示多个文件

# -n 指定显示行号
cat -n README.md
```

## mv
`mv` 有2个用途：
- 将文件或目录移动到另一个位置
- 将文件或目录重命名

注：实际上 `mv` 是用来移动文件或目录，只不过有类似重命名的功能而已。
```bash
# 将 README.md 重命名为 README-2.md, 如果 README-2.md 存在会直接覆盖。
mv README.md README-2.md

# 将 README.md 移动到上一层目录
mv README.md ../README.md

# -i 交互式操作，如果目标文件存在则进行询问是否覆盖
mv -i README.md ../README.md
```



## cal
显示当前日历

```bash
cal
# 输出
     June 2020        
Su Mo Tu We Th Fr Sa  
    1  2  3  4  5  6  
 7  8  9 10 11 12 13  
14 15 16 17 18 19 20  
21 22 23 24 25 26 27  
28 29 30

# 显示临近3个月, 只能是3个月
cal -3
```

## last
显示用户最近登录信息

```bash
last # root     pts/0        Sun Jun 14 00:12   still logged in    192.0.0.0

# 指定显示条目数
last -n 1
```

## shutdown
将系统关机或重启操作

```bash
# 立即重启系统
shutdown -r now

# 关机系统
shutdown -h  关机

# 把前一个关机或重启取消掉
shutdown -c 

# 设定一个时间关机, 加 & 可以继续用终端命令
shutdown -h 05:33 &
shutdown +5 "5分钟后关机" # 5分钟后关机，同时送出警告信息给登入用户：
```

## reboot
用于重新启动系统。

```bash
# 重启系统
reboot

# -f 强制重启
reboot -f

# 用于模拟重新启动系统，不会真实重启，数据会写入 /var/log/wtmp 
reboot -w

# 在重新启动之前关闭所有网络界面
reboot -i
```

## uname
打印系统信息

```bash
# 不带任何参数打印当前操作系统内核名称
uname # Linux  等价于 uname -s

# 打印系统所有信息
uname -a

# -r 打印系统版本 , 如果次版本号都是偶数，说明是一个稳定版
uname -r # 3.10.0-514.26.2.el7.x86_64

# 打印网络节点主机名称
uname -n # Yin.local

# 打印处理器名称
uname -p # i386
```

## ifconfig
配置或显示系统网卡的网络参数

```bash
# 显示所有网络参数信息
ifconfig

# 配置网卡IP地址
ifconfig eth0 192.168.1.111
```

## who
显示当前所有用户登录信息

```bash
# 显示当前登录系统的用户
who
cosyer console  Jun 15 21:38

# 显示登录账号名和总人数
who -q

# 显示上次系统启动时间
who -b  # reboot   ~        Jun 15 21:38
```

## whereis
用来定位指令的二进制程序、源代码文件和man手册页等相关文件的路径。

注意：whereis 是从数据库里查找的，因此特别快，默认情况下一星期更新一次数据，所以有时会查找删除的数据或者刚建立的数据无法找到问题。

```bash
# 查找 nginx
whereis nginx # nginx: /usr/sbin/nginx /usr/lib64/nginx /etc/nginx /usr/share/nginx /usr/share/man/man8/nginx.8.gz /usr/share/man/man3/nginx.3pm.gz

# -b 指定只查找二进制
where -b nginx # nginx: /usr/sbin/nginx /usr/lib64/nginx /etc/nginx /usr/share/nginx

# -m 指定查找说明文件 man
whereis -m nginx # nginx: /usr/share/man/man8/nginx.8.gz /usr/share/man/man3/nginx.3pm.gz
```

## zip
将目录或文件压缩为 .zip 格式

```bash
# 压缩文件
zip README.zip README.md

# 压缩目录需要 -r 递归处理
zip -r temp.zip temp

# 包含系统隐藏文件
zip -r -S temp.zip temp

# 指定压缩效率 1-9
zip -r -9 temp.zip temp 
```

## unzip
解压 .zip

```bash
# 将 demo.zip 解压到当前目录
unzip demo.zip

# 查看 demo.zip 文件，但不解压
unzip -v demo.zip

# -d 指定将文件压缩到 src 目录下
unzip demo.zip -d src
```

## locate
搜索文件，与 `find` 命令很像，但更快，因为是从数据库里查找, 通常每天会进行数据更新。

```bash
# 搜索 README.md 相关文件
locate README.md

# 忽略大小写
locate -i README.md
```

## kill
杀死一个正在运行中的程序。注：程序进程id可通过 top 等命令查看。

```bash
# 杀死 pid 为88 进程
kill 88

# 强制杀死
kill -KILL 88

# 彻底杀死进程
kill -9 88

# 显示信号
kill -l

# 杀死指定用户的所有进程
kill -u nginx
```

## chmod
修改文件或目录权限

chmod [参数选项] [mode, 八进制或符号表示] files...
- u 符号代表当前用户。
- g 符号代表和当前用户在同一个组的用户，以下简称组用户。
- o 符号代表其他用户。
- a 符号代表所有用户。
- r 符号代表读权限以及八进制数4。
- w 符号代表写权限以及八进制数2。
- x 符号代表执行权限以及八进制数1。
- X 符号代表如果目标文件是可执行文件或目录，可给其设置可执行权限。
- s 符号代表设置权限suid和sgid，使用权限组合u+s设定文件的用户的ID位，g+s设置组用户ID位。
- t 符号代表只有目录或文件的所有者才可以删除目录下的文件。
- \+ 符号代表添加目标用户相应的权限。
- \- 符号代表删除目标用户相应的权限。
- = 符号代表添加目标用户相应的权限，删除未提到的权限。

```bash
# README.md 文件设为所有用户可读取
chmod a+r README.md

# -R 递归目录下所有文件
chmod a+r src/

# 也可以用八进制符号表示
# 3个数字分别为 x,y,z 表示User、Group、及Other的权限。
# r=4, w=2, x=1
chmod 777 README.md # 等价于 chmod a=rwx README.md
```

## lsof
列出当前系统打开文件的工具
```bash
## 列表所有打开文件的的列表
lsof

# 查看指定端口被占用情况
lsof -i:8080

# -p 列出指定进程号所打开的文件
lsof -p 6112
```

## ps
查看当前系统进程状态

```bash
# 显示所有进程信息
ps -A

# 显示指定用户进程信息
ps -u root

# 显示所有进程信息包括命令行
ps -ef  # -e 等价于 -A  , 即等价于 ps -Af

# 列出所有正在内存中的进程
ps aux

# 配合 grep 查询指定进程
ps -ef | grep nginx
```

## open
open 命令可在 linux / mac 具有可视化界面下进行文本编辑、打开应用程序等功能。

```bash
# 在mac下用Finder打开当前目录
open .

# 用默认应用程序打开文件
open README.md

# 用默认编辑器打开文件
open -e README.md

# 如果是一个URL用默认浏览器打开页面
open https://github.com/cosyer

# 指定某个应用程序打开某个文件, 如果不指定文件默认直接打开程序
open -a /Applications/Google/Chrome.app README.md
```

## curl
`curl` 是一个非常强大的网络传输工具, 利用URL规则在命令行下工作的文件传输工具。

```bash
# 查看网页内容
curl https://github.com/cosyer/linux-learning

# 下载文件到本地
curl https://github.com/cosyer/linux-learning -O
curl https://github.com/cosyer/linux-learning -O --progress # 显示下载进度条

# -I 或 -head 显示HTTP响应报文
curl https://github.com/cosyer/linux-learning -I

# -H 设置请求头
curl -H 'Content-Type: application/json' -H 'Content-Type: application/json' https://github.com/cosyer/linux-learning

# 通过POST请求发送JSON数据, -X 指明是否哪种HTTP请求, -d 实体内容
curl -H "Content-type: application/json" -X POST -d '{"age":"18"}' https://github.com/cosyer/linux-learning

# 发送时携带 cookie
curl https://github.com/cosyer/linux-learning --cookie "age=18;name=xjh"

# -v 查看整个传输过程
curl https://github.com/cosyer/linux-learning -v

# -F(--form) 利用POST上传文件, file 是字段名, =@ 必须存在
curl https://example.com/upload -F "file=@/home/demo.png"
```

## date
显示或设置系统时间日期

```bash
# 显示当前时间
date

# 格式化当前时间
date +"%Y-%m-%d %H:%M.%S" # 2020-07-01 00:00.00

# 设置系统时间
date -s  # 设置当前时间, 须root
date -s "2020-07-01 00:00:00" # 设置全部时间
```

## netstat
查看网络状态系统信息

参数说明：

- a或--all 显示所有连线中的Socket。
- A<网络类型>或--<网络类型> 列出该网络类型连线中的相关地址。
- c或--continuous 持续列出网络状态。
- C或--cache 显示路由器配置的快取信息。
- e或--extend 显示网络其他相关信息。
- F或--fib 显示FIB。
- g或--groups 显示多重广播功能群组组员名单。
- h或--help 在线帮助。
- i或--interfaces 显示网络界面信息表单。
- l或--listening 显示监控中的服务器的Socket。
- M或--masquerade 显示伪装的网络连线。
- n或--numeric 直接使用IP地址，而不通过域名服务器。
- N或--netlink或--symbolic 显示网络硬件外围设备的符号连接名称。
- o或--timers 显示计时器。
- p或--programs 显示正在使用Socket的程序识别码和程序名称。
- r或--route 显示Routing Table。
- s或--statistics 显示网络工作信息统计表。
- t或--tcp 显示TCP传输协议的连线状况。
- u或--udp 显示UDP传输协议的连线状况。
- v或--verbose 显示指令执行过程。
- V或--version 显示版本信息。
- w或--raw 显示RAW传输协议的连线状况。
- x或--unix 此参数的效果和指定"-A unix"参数相同。
- -ip或--inet 此参数的效果和指定"-A inet"参数相同。

```bash
# 列出所有占用端口
netstat -ntlp

# 显示所有网络状况
netstat -a

# 显示所有tcp网络状况
netstat -at

# 显示所有udp网络状况
netstat -au

# 配合grep命令查看某个端口被占用情况
netstat -ap | grep 8080
```

## w
查看当前登入系统的用户信息, 有哪些用户正在登陆, 以及它们正在执行的程序。

此命令与 who 相似，默认情况下比 who 命令输出内容更详细。

## chown
用来变更文件或目录的拥有者或所属群组

```bash
# 将 README.md 文件拥有者设为 byroot
chown byroot README.md

# 使用-R递归处理文件
chown -R byroot src/

# 改变所属群组, 拥有者设为 byroot 群组设为 byrootgroup
chown byroot:byrootgroup README.md
```

## uptime
查看系统负载信息
```bash
[root@node-1 ~]# uptime
 09:45:09 up 2 days, 20:25,  2 users,  load average: 0.22, 0.37, 0.40
You have new mail in /var/spool/mail/root
```

## chattr
用于修改文件属性
参数:
- a：让文件或目录仅供附加用途

- b：不更新文件或目录的最后存取时间

- c：将文件或目录压缩后存放

- d：将文件或目录排除在倾倒操作之外

- i：不得任意更动文件或目录

- s：保密性删除文件或目录

- S：即时更新文件或目录

- u：预防意外删除

- -R：递归处理，将指令目录下的所有文件及子目录一并处理

- -v<版本编号>：设置文件或目录版本

- -V：显示指令执行过程

- +<属性>：开启文件或目录的该项属性

- -<属性>：关闭文件或目录的该项属性

- =<属性>：指定文件或目录的该项属性

```bash
# 锁定该文件, 防止文件被修改或删除
chattr +i README.md  # chattr -i README.md  解锁

# 可以使用 lsattr 查看赋予的属性
lsattr README.md
```

## gzip
用来压缩文件, 也可以用来解压文件, 格式为 .gz, 压缩后原文件将被删除
> 注意：gzip 不能用于压缩整个目录, 只能用于压缩文件, 如果需要压缩整个目录可以考虑使用 [zip](#zip) 命令。

```bash
# 压缩 README.md 文件, 压缩完成后 README.md 文件会被删除
gzip README.md # README.md.gz

# 递归压缩目录下的所有文件
gzip -r ./logs

# 加 -v 显示压缩执行过程
gzip -rv ./logs

# 压缩 .tar 后缀文件
gzip -r src.tar  # 压缩后为 src.tar.gz

# -d 解压之前gzip压缩后的文件
gzip -d README.md
gzip -dr ./logs # 或者递归解压目录下的所有文件
```

## bzip2
将文件压缩成 bz2 格式，也可用于解压 .bz2

```bash
# 压缩 README.md 文件
bzip2 README.md     # 不保留源文件 README.md.bz2
bzip2 -k README.md  # -k 保留源文件

# 解压
bzip2 -d README.md.bz2  # 源文件将被删除
bzip2 -dk README.md.bz2  # -k 保留源文件
bzip -dt README.md.bz2 # -t --test 测试解压, 实际不解压，模拟整个解压过程
```

## more
分页查看文件内容, 每次查看一屏, 每屏能显示多少内容取决于终端大小。

快捷键：

- 空格 - 查看下一屏内容
- 回车 - 查看下一行内容
- B - 查看上一屏内容
- Q - 退出

```bash
more README.md

# 从第10行开始显示
more +10 README.md

# 显示查看进度
more -d README.md # --More--(17%)[Press space to continue, 'q' to quit.]
```

## crontab
周期性执行任务, 通常用于定时备份
* * * * * 分别含义：
```bash
*    *    *    *    *
┬    ┬    ┬    ┬    ┬
│    │    │    │    │
│    │    │    │    │
│    │    │    │    └───── 一周中的某一天 (0 - 7)  0或7代表是星期日
│    │    │    └────────── 月份 (1 - 12)
│    │    └─────────────── 一个月的某一天 (1 - 31)
│    └──────────────────── 小时 (0 - 23)
└───────────────────────── 分钟 (0 - 59)
```

```bash
# 列出该用户设置
crontab -l

# 编辑该用户设置
crontab -e

# 删除该用户设置
crontab -r
```

```bash
# 每天18点18分执行 echo `date` > README.md
18 18 * * * echo `date` > README.md

# 每一分钟执行
* * * * */1 echo `date` > README.md
```

### man
查看指令帮助手册

```bash
# 查看 ls 指令帮助手册
man ls

# -a 在所有手册中查找
man -a ls
```

### sleep
将目前动作延迟一段时间, 通常用于脚本当中
时间参数：
- s 秒
- m 分钟
- h 小时
- d 天

```bash
# 5秒后输出 Hello
sleep 5s; echo Hello
```

### source
在当前Shell环境中从指定文件读取和执行命令， 通常用于重新执行环境(别名 . 点符号)

```bash
source ~/.bash_profile  # 等价 . ~/.bash_profile
```

### paste
合并N个文件的列，相当于追加文件内容

```bash
# 1.txt 和 2.txt 合并输出
paste 1.txt 2.txt

# 1.txt 2.txt 合并后保存为 3.txt
paste 1.txt 2.txt > 3.txt
```

### stat
用于显示文件或目录的状态信息

```bash
stat logs
# File: ‘logs/’
# Size: 16384           Blocks: 32         IO Block: 4096   directory
# Device: fd01h/64769d    Inode: 669067      Links: 5
# Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
# Access: 2020-07-07 17:24:23.941816812 +0800
# Modify: 2020-07-12 11:46:55.567707577 +0800
# Change: 2020-07-12 11:46:55.567707577 +0800
# Birth: -
```

### tree
生成目录树结构, 通常用于描述项目结构

```bash
# 递归当前目录下所有文件并生成目录树
tree
# .
# ├── LICENSE
# ├── README.md
# ├── b.md
# └── media
#     └── poster.jpg


# -I 忽略某些目录
tree -I "node_modules|.git|.svn"

# 只显示目录
tree -d

# 指定要递归的目录层级
tree -L 3
```

### yum
基于RPM的软件包管理器, 特点安装快捷，命令简洁好记

```bash
# 安装nginx
yum install nginx

# 指定 -y 安装时自动全部 yes
yum -y install nginx

# 查找包
yum search nginx

# 显示所有已安装的包
yum list

# 升级包
yum -y update nginx

# 移除包
yum -y remove nginx

# 清除缓存
yum clean all

# 显示安装包信息
yum info nginx

# 检查可更新的包程序
yum check-update
```

### history
列出当前系统使用过的命令，默认保存1000条

```bash
# 列出当前使用过的命令,
history

# 指定要显示的条数
history 50

# 清空历史命令
history -c

# 过滤
history | grep java
```

### md5sum
计算和校验文件报文摘要

```bash
# 计算文件md5
mmd5sum README.md # d41d8cd98f00b204e9800998ecf8427e  README.md

# 校验文件, 查看文件是否被篡改过
md5sum README.md > README.md5 # 计算文件md5并保存在 README.md5 , 保存的文件名和后缀可以随意命名
md5sum -c README.md5 # -c 从指定的文件读取md5并校验, 会从当前目录寻找 README.md
```

### su
切换当前用户到其他用户

```bash
# 切换到 admin 身份
su admin

# 退出
exit

# -c 执行完指令后切换回原身份
su -c ls admin

# 可以通过以下查找当前系统用户列表
cat /etc/passwd
```

### xargs
给命令传递参数的一个过滤器，也是组合多个命令的一个工具, `将左侧的标准输出放进右侧标准输入`。

此命令可以将多次操作简便为一次操作。

```bash
# 统计代码
find -name "*.js" | xargs wc -l # 等价于 wc -l a.js b.js c.js ...

# 批量下载文件
cat download.txt | xargs wget
```

### scp
加密的方式在本地主机和远程主机之间复制文件
注：需要有读写权限，否则会无法操作。

```bash
# 从远程主机下载文件到本地
scp root@192.168.0.100:/root/file.zip /home/file.zip

# 从远程主机下载目录到本地，需要 -r 递归
scp -r root@192.168.0.100:/root/dir  /home/dir

# 从本地主机上传文件到远程主机
scp /home/file.zip root@192.168.0.100:/root/file.zip

# # 从本地主机上传目录到远程主机，需要 -r 递归
scp -r /home/dir root@192.168.0.100:/root/dir
```

### grep
强大的文本搜索工具，被称为Linux命令三剑客

```bash
# 从 README.md 文件中搜索 linux 关键字
grep "linux" README.md
grep "linux" README.md README2.md # 多个文件搜索

# 输出时高亮显示
grep "linux" README.md --color

# -o 只输出匹配部分
grep -o "linux" README.md --color

# -n 输出到匹配的行数
grep -n "linux" README.md

# -c 输出到匹配次数
grep -c "linux" README.md

# -r 递归目录文件搜索
grep -r "linux" ./src

# 使用正则表达式搜索, 正则表达式语法与大部分编程语言基本上一致
egrep "[0-9]" # 等价于 grep -E "[0-9]" README.md
```

### systemctl
系统服务管理器指令, 通常用来设置某个服务器默认开机启动或关闭。

```bash
# 立即启动服务
systemctl start nginx.service

# 立即停止服务
systemctl stop nginx.service

# 重启服务，stop 后 start
systemctl restart nginx.service

# 重新载入服务, 一般情况下重新载入新的配置
systemctl reload nginx.service

# 下次开机时默认启动服务
systemctl enable nginx.service

# 下次开机时不会启动服务
systemctl disable nginx.service

# 查看某个服务状态信息
systemctl status nginx.service

# 当前服务是否正在运行中
systemctl is-active nginx.service

# 查看服务开机有没有默认启动
systemctl is-enable nginx.service
```

## tar
```bash
tar -zcvf 1.tar.gz xxx
tar -zxvf 1.tar.gz
```

## base64
base64 编码/解码文件或标准输入输出
```bash
# 编码字符串
printf "hello world"|base64 # aGVsbG8gd29ybGQ=

# 解码字符串
printf aGVsbG8gd29ybGQ=|base64 -d # hello world

# 编码文件, 将结果保存在 decode.txt
base64 README.md > decode.txt

# 从标准输入中读取已经进行base64编码的内容进行解码
base64 -d decode.txt
```

## ln
将某一个文件在另外一个位置建立并产生同步的链接。 当不同的2个目录需要同时引用某一个文件时此命令就派上用场了。

软链接：

- 软链接，以路径的形式存在。类似于Windows操作系统中的快捷方式
- 软链接可以 跨文件系统 ，硬链接不可以
- 软链接可以对一个不存在的文件名进行链接
- 软链接可以对目录进行链接

硬链接：

- 硬链接，以文件副本的形式存在。但不占用实际空间。
- 不允许给目录创建硬链接
- 硬链接只有在同一个文件系统中才能创建

```bash
# 默认创建硬链接，修改 README.md 内容， a.md 也会同步修改, 修改a.md  README.md 也会同步修改
ln README.md a.md

# -s 创建软链接
ln -s README.md a.md # 如果删除了 README.md  a.md 将失效

# -f 强制执行
ln -f README.md ./src/a.md
```

## service
管理操作系统服务的命令, 是Redhat Linux兼容的发行版中用来控制系统服务的实用工具，它以启动、停止、重新启动和关闭系统服务，还可以显示所有
系统服务的当前状态。

```bash
# 启动 docker 服务
service docker start

# 查看 docker 状态
service docker status

# 停止 docker 服务
service docker stop

# 重新启动 docker 服务
service docker restart

# 查看所有服务状态
service --status-all
```

## free
显示内存使用情况
选项
- b 字节单位显示
- k KB单位显示
- m MB单位显示
- g GB单位显示
- s<秒> 每S秒监控内存使用情况

解释
- total 内存总数
- used 已使用内存
- free 空闲内存
- shared 当前已废弃内存
- buff/cache 缓存内存数
- 1204660 可用内存数

```bash
free
# 输出以下, 默认以字节为单位
              total        used        free      shared  buff/cache   available
Mem:        1882192      485312      448424         704      948456     1204660
Swap:             0           0           0

# MB单位显示
free - m

# 10秒执行一次查询
free -s 10
```

## apt-get
apt-get命令 是Debian Linux发行版中的APT软件包管理工具。所有基于Debian的发行都使用这个包管理系统。

```bash
# 安装一个docker软件
apt-get install docker

# 卸载软件，保留配置文件
apt-get remove docker

# 卸载软件并删除配置文件
apt-get –purge remove docker

# 更新所有已安装的软件包
apt-get upgrade

# 删除软件备份，主要用来释放空间
apt-get clean
```

## file
查看文件类型，比如文件、目录、二进制、符号链接等

```bash
# 输出 README.md: ASCII text
file README.md

# index.html: HTML document, UTF-8 Unicode text, with very long lines, with no line terminators
file index.html
```

## jobs
显示当前运行在后台模式中的所有用户的进程（作业）

```bash
# 先来启一个后台进程, 比如启一个sleep命令进程， & 符号表示后台运行
sleep 3 &
# 查看后台进程
jobs # 输出：[1]+  Running       sleep 3 &
```

## type
type 命令有2个作用：
- 用来查找命令的位置，类似 which 命令
- 检测某个命令是内建命令还是外部命令

内建命令和外部命令的区别：内建命令不会衍生出子进程，而外部命令会衍生出一个子进程然后执行命令, 所以内建命令执行效率要高。

```bash
# cd is a shell builtin  表示这是shell内建命令
type cd

# ps is hashed (/usr/bin/ps)  表示这是一个外部命令
type ps
```

## printenv
列出全局环境变量, 有个 env 命令很像，但 printenv 可以打印变量的值。所有系统环境变量都是大写字母，用于区分普通用户的环境变量。

```bash
# 列出所有全局环境变量
printenv

# 也可以显示指定全局环境变量的值, 等价于 echo $HOME
printenv HOME # /root
```

## set
列出所有全局变量、局部变量和普通用户定义的变量，按照字母顺序对结果进行排序。注意：所有系统全局变量都是大写，用户定义的环境变量全部采用小
写，这是标准规范。

```bash
set
# OPTIND=1
# OSTYPE=linux-gnu
# PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
# PIPESTATUS=([0]="0")
# ...
```

## export
导出环境变量, 可以把一个局部变量导出成全局环境变量。注意：export 只有在当前Shell有效，退出后将失效。

```bash
# 先声明一个局部环境变量
my_var='Hello'
# 然后将其导出全局环境变量
export my_var
```

## unset
删除环境变量

注意：unset 只在当前shell删除环境变量，假如环境变量设置在 ~/.bash_profile 等文件中用户重新启动依然生效。如果是在子进程删除全局环境变
量只在子进程有效，不会影响父进程。

```bash
# 删除 HOME 环境变量，前面不需要带 $ 符号
unset HOME
```

[回目录](#目录)
