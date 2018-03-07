从用户到内核

USER -> shell -> kernel
shell

1. CLI bash等
2. GUI i3等

#### 系统启动
BIOS -> MBR:Boot Code -> 执行引导程序-GRUB -> 加载kernel -> 执行init -> runlevel<br/>
initranfs 驱动模块存在内存的文件系统
```
dmesg # 查看启动时内核输出信息
	  # 日志在/var/log/dmsg
```
运行级别
```
init [0-6]
0 # 关机
1 # 单用户模式
2 # 不带网络的多用户模式
3 # 无图形界面的多用户模式
4 # 未使用
5 # X图形模式
6 # 重启
```
```
runlevel # 当前运行级别
```
<br/>
<br/>
<br/>
#### 在后台运行程序 ``` mousepad & ```
#### 命令 ``` !! 重复前一个命令

!字符              重复前一个以字符开头的命令

!num               第num个命令

!?a                前面包含a的命令

!-n                几个命令之前的命令

^+R                可以搜索历史命令

按esc后再按.输入上一个命令

date               # 查看日期时间或格式化时间
				   # 格式化时间+%Y--%m--%d


<br/>
#### 通配符

?

[0-9]

[abc]

[^abc] # 除了a或b或c


<br/>
#### su - 与 su 

su - # 创建新用户环境 su # 切换用户

#### 磁盘知识
	cylinder 柱面
    sector   扇区
    head     磁头
    
    fdisk只用于mbr如需要gpt格式下就可使用parted替代
    
    raw设备  没有文件系统 裸设备
#### 用户&组
	每个进程必须以用户身份运行
	1.  每个用户有一个UserID 系统以UID识别用户
	2.  每个用户属于一个主组,属于一个或多个附属组
	3.  每个组拥有一个GroupID
	4.  每个进程以一个用户身份运行,并受该用户可访问的资源限制
	5.  每个可登录用户拥有一个指定shell

	用户ID是32位,从0开始,往往限制60000以下 Linux uid最大为4294967294
    
> 三种用户
> 1. root用户   ID 0 注超级用户不一定非得为root 只有超级用户限制ID 0
> 2. 系统用户   ID 1-499 可创建服务 为限制资源 作为进程创建使用 不需要登录
> 3. 普通用户   ID >500

`gid   主ID

	/etc/passwd   用户信息
    /etc/shadow   用户密码 只有管理员查看
    /etc/group    组信息
    
    
	/etc/skel     用户建立时的初始文件 可放一些文件方便创建用户时在用户主目录建立文件
    
useradd

	useradd -d home目录 -s shell -u userId -g 主组 -G 附组(最多31附组用","分隔) 用户名
 
> useradd执行创建用户后的一系列操作
> 1. 在/etc/passwd中添加用户信息
> 2. 如使用passwd创建密码则密码加密保存在/etc/shadow中
> 3. 建立一个新的home目录
> 4. 将/etc/skel中的文件复制到用户home
> 5. 建立一个与用户名相同组 用户则默认属于这个组

usermod 修改用户信息

	usermod
	-l   新用户名
    -u   新Id
    -d   用户home位置
    -g   主组
    -G   附加组
    -L   锁定用户使其能登录
    -U   解除锁定用户登录
    
    
 userdel 删除用户
 
 	userdel -r name # 删除用户与用户Home
    
 组
 
 > 每个组有一Id
 > 每个用户有一个主组 每个用户有最多31附组

	groupadd test
    useradd -G test user1 # 将user1加到test里
    
 #### 权限
 
 > 1. r   读<br/>
 > 2. w   写<br/>
 > 3. x   执行<br/>


   > 进程继承用户权限

r -- 可读取文件内容 -- 可列出目录内容<br/>
w -- 可修改文件内容 -- 可在目录创建删除文件<br/>
x -- 可作为命令执行 -- 可访问目录内容
> 对于目录必须同具备rx


文件权限<br/>
U <i>(user)</i> - G <i>(group)</i> - O <i>(others)</i>
<br/>
<br/>
<br/>



第一位表示文件类型 后面三个一组分别是U - G - O

	-rwx-r-xr--
    
    
chown 改变文件所属用户&组

chwon user1 file # 修改所属用户 chown -R user1 ./text # 以递归修改文件以及其中所有文件 chown -R user1 dir


chmod 修改文件权限

	chmod a+x
    chmod u+rw
    chmod a-r
    # 数字方式
    # r = 4 否为0
    # w = 2 否为0
    # x = 1 否为0
    # rwxrwxrwx -> 777
    # rwx------ -> 700
    # rw-rwxrwx -> 677
    chmod 777 file
    
chgrp 改变所在组

	chgrp groupname user1
    
默认权限与umask

$touch a $ls -l -rw-rw-r--... $mkdir aa $ls -l drwxrwxr-x...
受umask属性影响

目录默认权限<br/>
777-umask(777减umask)<br/>

如果umask等于022则权限为777-022

文件默认权限<br/>
666-umask<br/>
> 普通用户默认umask:002<br/>
> 超级用户默认umask:022

five@five-msi:$ umask 0002 user1@user1:$ su 密码： root@five-msi:/home/five# umask 0022
为什么权限打印结果4位
因为第一位需要给特殊权限留位置
特殊权限有 suid sgid sticky
suid 以文件所属用户身份执行而非执行文件的用户-rwsr-xr-x
sgid 以文件所属组身份执行
sticky 对目录有影响,对目录拥有写入权限的用户仅可删除其拥有的文件,无法删除其它用户文件

修改umask

$umask 022

修改特殊权限

suid

chmod u+s document
sgid

chmod g+s document
sticky

chmod o+t document
也可通过数字权限
suid 4
sgid 2
sticky 1

chmod 4755 document # set suid


#### 网络原理
网络编址<br/>
IP编址是其中一种方式<br/>
一个IP一个主机<br/>
IPv4 32位长<br/>
IPv6 128位

##### IPv4
点分十进制
1. 网络部分
2. 主机部分

IPv4常见形式之一

192.168.1.1
其二进制是

11000000.10101000.00000001.00000001

##### 子网掩码
来确定IPv4网络部分位置<br/>

255.255.255.0

子网掩码长度与IPv4同 每一位与IP中的每一位一一对应<br/>
IPv4相对应子网掩码中为1的部分是网络部分

192.168 .1 .1 11000000.10101000.00000001.00000001 255.255.255.0 11111111.11111111.11111111.00000000
192.168.1就是网络部分

##### 同一个网络主机之间通信
使用MAC<br/>
例子:<br/>
1. 192.168.1.1发送ARP(地址解析协议只在同网段发)至192...2获取192...2MAC<br/>
2. 目标设备响应<br/>

192.168.1 MAC:dd:dd:dd:dd 192.168.2 MAC:dd:dd:dd:dc 192.168.3 MAC:dd:dd:dd:db

##### 不同网络主机之间通信
1. 需要路由器/网关数据转发<br/>
2. 路由器之间转发

> 路由表

##### 网关
跨区域通信
##### 域名
每个域名对应一个或多个IP<br/>

www.baidu.com
www 主机
baidu 域名
com 类型

> 主机名随便起

ftp.126.com mail.126.com

##### DNS
最后还是通过IP进行通信<br/>
域名服务<br/>
DNS域名服务器运营商运营

DNS请求->DNS服务器->返回解析后地址->访问

##### 网络主机配置项目
1.局域网通信

IP地址
子网掩码


2.跨网段通信

IP地址
子网掩码
网关

3.可上网computer

IP地址
子网掩码
网关
DNS



#### 网络配置
以太网命名规则 eth0 eth1<br/>

pci信息查看方法

lspci
如usb网卡

lsusb

查看接口信息

ifconfig ifconfig -a # 查看所有接口

lo环回网卡系统用
> RX packets  接收包
> 
> TX packets  发送包
> 
> RX bytes    接收流量
> 
> TX bytes    发送流量

启用禁用网卡

启用eth0 出现地址

ifup eth0
禁用eth0 地址消失

ifdown eth0


> 服务器不启用DHCP

配置网卡

vim /etc/network/interfaces
input sim

auto eth0 iface eth0 inet static address 192.168.1.100 netmask 255.255.255.0 gateway 192.168.1.1


配置DNS

vim /etc/resolv.conf


配置临时主机名

hostname host.www.net

配置静态主机名

vim /etc/hosts



##### 测试网络

网络连通性

ping [IP] | [域名]

DNS解析

host www.baidu.com dig www.baidu.com



##### 查看路由表

ip route

##### 追踪到达目标地址的网络路径
经过的路由器

traceroute www.baidu.com

##### 网络质量测试

mtr www.baidu.com

##### 网络排查
从底层到高层 从自身到外部
1. 看网络配置
2. 看网卡
3. 看网关
4. 看DNS解析
5. traceroute追踪

##### date
```
date --help # 帮助
date # 查看时间
date +%Y--%m--%d # 显示指定时间
date -s "20:20:20" # 修改时间
```

##### hwclock/clock 查看硬件时间

##### uptime 系统运行时间/登录用户/负载

##### cal 日历

##### echo 输入的内容返回
```
echo "this"
```
##### cat 查看文档

##### more/less 以翻页显示内容/上下翻页
```
more # 无向前翻页功能
less # 可上下翻页
q    # 退出
```

##### head/tail 显示文件前几行/后几行-追踪文件更新
默认是10行
```
head -n 1000 xx.conf # -n指定显示几行
tail -n 1000 xx.conf # 同上
tail -f xx.conf # 追踪文件更新 可用于显示日志
```
##### lspci 查看pci设备
```
lspci -v # 详细信息
```

##### lsusb 查看usb设备
```
lsusb -v
```

##### lsmod 查看内核加载模块
```
lsmod
```

##### shutdown 关机/重启
```
shutdown -h # 关机
shutdown -h now # 现在关机
shutdown -h +10 # 等十分钟关机
shutdown -h 23:01 # 23:01关机
shutdown -r # 重启
shutdown -r now # 现在重启
```

##### zip/unzip 压缩/解压
```
zip xxx.zip myfile # 压缩成xxx.zip
unzip xxx.zip
```

##### gzip gzip算法压缩

##### tar 归档
```
tar -cvf xxx.tar myfile # 创建归档
tar -xvf xxx.tar # 释放归档
tar -cvzf xxx.tar.gz myfile # 先归档再压缩成gzip格式
```

##### locate 快速查找文件
查找时查找数据库,但新文件可能不在数据库
```
updatedb # 创建数据库
locate a # 查找
```

##### find 查找可定义规则
```
find . -name *a*
find / -name *.cfg
find / -perm 777
find / -type d
find / -type l
find . -name "*.cfg" -exec ls -l {}\;
```
> 基于查找条件
> -name<br/>
> -perm<br/>
> -user<br/>
> -group<br/>
> -ctime<br/>
> -type<br/>
> -size<br/>


### 管道重定向
管道与重定向控制数据流<br/>
为方便管理,shell数据流定义<br/>
1.STDIN标准输入 编号0 默认键盘<br/>
2.STDOUT标准输出 编号1 默认终端<br/>
3.STDERR标准错误 编号2 默认终端<br/>

```
# > 覆盖
echo "aaa" > xx.txt

# >> 追加
echo "aaa" >> xx.txt

# 2> 标准错误覆盖到
ls -l xxx 2> xx.txt

# 2>&1 结合标准输出与标准错误

# < 重定向标准输入,代替键盘输入
grep aaa < /etc/xx.cfg

# | 管道,将一个命令标准输出作为另一个命令标准输入
ls -l | grep aaa
find / -user aaa 2> /dev/null | grep video
```


##### grep
```
grep 'aaa' /etc/passwd
find / -user user1 | grep s
find / -user user1 2 > /dev/null | grep s
-i  # 搜索时忽略大小写
-n  # 显示结果所在行数
-v  # 输出不带关键字的行
-Ax # 在输出时包含结果所在行之后的指定行数
-Rx # 在输出时包含结果所在行之前的指定行数
```

##### cut
基于列处理文本
```
cut -d: -f1 /etc/passwd
cut -c2-6 /etc/passwd # 只显示第2-6字符
grep a /etc/passwd | cut -d: -f3
-d # 指定分割字符 默认TAB
-f # 指定输出的列号
-c # 基于字符进行切割
```
##### wc 文本统计
```
-l # 只统计行数
-w # 只统计单词
-c # 统计文件字节数
-m # 统计字符数
```

##### sort 排序不支持中文
```
-r # 进行倒序排序
-n # 基于数字进行排序
-f # 忽略大小写
-u # 删除重复行
-t c # 使用c作为分割符侵害为列进行排序
-k x # 当进行基于指定字符分割为列的排序时,指定基于那个列排序

sort -u # 删除所有重复行,不同于uniq
```


##### uniq 删除重复相邻行
```
cat myfile | uniq
```

##### diff 比较文件
```
diff file1 file3
-i # 忽略大小写
-b # 忽略空格数量的改变
-u # 统一显示比较信息,一般以以生成patch文件
diff -u file1 file3 > cheg.patch
```
##### asepll 检查英文拼写
```
aspell check file1
aspell list < file1
```

##### tr 处理文本内容
tr不接收文件,要用重定向
```
# 删除内容
tr -d 'TMD' < file1

#大小写转换
tr 'a-z' 'A-Z < file1 # a-z -> A-Z
```

##### sed 搜索替换文本
用正则表达式处理文件<br/>
s 搜索的字符串<br/>
g 如果一行当中出现多个匹配项则都去进行匹配<br/>
-e 指定多个匹配项<br/>
-f 将sed指令写到文件后,使用-f参数调用文件里的sed指令
```
sed 's/linux/unix/g' file1 # 将linux替换成unix
sed '1,5s/linux/unix/g' file1 # 替换1-5行
sed -e 's/linux/unix/g' -e 's/ss/sss/g file1
sed -f sedfile file1
```

##### vim/vi
命令模式 (默认) <br/>
插入模式<br/>
ex模式 : <br/>
```
:w # 保存
:q # 退出
:q! # 强制退出
:x # 保存并退出
:set number 显示行号
:!系统命令 # 执行一个系统命令并显示结果
:sh # 切换到命令行 ^+D 返回编辑器
```
```
i          # 光标前插入文本

o          # 当前行下面插入新行

dd         # 删除整行

yy         # 将当前行的内容放入缓冲区 复制

n+yy       # 将n行的内容放入缓冲区 复制多行

p          # 粘贴

u          # 撤销

r          # 替换当前字符

/          # 搜索 按n在查找出的关键字之间切换
```
#### LVM
逻辑卷管理
> 通过将底层物理硬盘抽象封闭,以逻辑卷形式表现给上次系统<br/>
> 可动态调整不丢失数据<br/>
> 新加入硬盘不改变现有上层逻辑卷<br/>
> 提高磁盘管理灵活性

概念<br/>
1.PE 物理拓展<br/>
2.PV 物理卷<br/>
3.VG 卷组<br/>
4.LV 逻辑卷<br/>

> LV受VG大小限制<br/>
> 可跨硬盘

创建

	1.磁盘先格式化为物理卷,整个磁盘空间划分为最小单位的PE,默认一个PE大小4M
	2.创建VG,可理解为空间池,用来装PE,可把一个或多个PE加入VG
	3.基于VG创建LV才可使用磁盘空间,可格式化当作分区用
	4.创建后/dev出现lv开头的逻辑卷

改变容量

	加PE
    加硬盘
    拉伸
    
基本操作

创建LVM
> 创建时逻辑卷是PE整数倍

1.将物理磁盘初始化为物理卷
```
pvcreate /dev/sdb /dev/sdc
```
2.创建卷组将PV加入卷组
```
vgcreate yourvgname /dev/sdb /dev/sdc
```
3.基于卷组创建逻辑卷
```
lvcreate -n mylv -L 100G yourvgname
```
4.为创建的逻辑卷创建文件系统
```
mkfs.ext4 /dev/yourvgname/mylv
```
5.将格式化好的逻辑卷挂载使用
```
mount /dev/yourvgname/mylv /mnt
```
```
# 查看逻辑卷信息
pvs
pvdisplay
vgs
vgdisplay
lvs
lvdisplay
```
> lv实际在/dev/mapper

<br/>
删除卷步骤<br/>
<br/>
1.删除lv<br/>
2.删除vg<br/>
3.删除pv<br/>
```
# 先umount目标lv
lvremove /dev/yourvgname/mylv
# 下同
```
逻辑卷拉伸
> 拉伸在线执行<br/>
> 保证vg有足够空闲空间<br/>
> 扩充逻辑卷<br/>
> 更新文件系统

```
vgdisplay

# 扩充逻辑卷
lvextend -L +1G /dev/yourvgname/mylv # 拉伸后不更新文件系统

# 更新文件系统
resize2fs /dev/yourvgname/mylv
```

如果卷组不够用,向卷组增加新pv<br/>
例如添加/dev/sdd
```
pvcreate /dev/sdd
vgextend yourvgname /dev/sdd
vgdisplay
```
缩小逻辑卷<br/>
> 离线操作

```
# 卸载已挂截逻辑卷
umount /dev/yourvgname/mylv

# 缩小文件系统
e2fsck -f /dev/yourvgname/mylv
resize2fs /dev/yourvgname/mylv 30G

# 缩小LV 可能损坏数据(例如resize2fs与lvreduce不同) 最好有阀值
lvreduce -L -30G /dev/yourvgname/mylv

lvdisplay

mount /dev/yourvgname/mylv /mnt
```
缩小卷组
```
# 将一个PV从卷组移除
vgreduce yourvgname /dev/sdd

vgdisplay
```

#### 高级权限机制ACL
> 传统UGO权限模型无法应对复杂权限设置需求<br/>
> ACL允许对不同用户,不同组对一个目标文件进行权限设置,不受UGO模型限制<br/>
> 默认根分区打开ACL

```
# 查看一个文件ACL设置
getfacl yourfile

# 针对一个用户进行ACL设置
setfacl -m u:usrname:rwx yourfile

# 针对一个组对文件进行ACL设置
setfacl -m g:usrgroup:rw yourfile

# 删除ACL设置
setfacl -X u:usrname yourfile

# 修改则重写一遍
setfacl -m u:usrname:rx yourfile
```

#### RAID
廉价磁盘冗余阵列技术<br/>
通过多磁盘并行运行提高存储IO性能<br/>

```
RAID共七类 RAKD 0 - 6 常用四种
RAID 0 读写性能 最少使用2块磁盘 数据分布每块磁盘 磁盘型号容量要相同 无冗余性
RAID 1 读取性能 冗余性 每块磁盘数据相同 读性能强 写性能弱 利用率是所有磁盘中最小那块 需要稳定性极强情况使用
RAID 5 读写性能 冗余性 允许故障1块磁盘 最少3块硬盘 数据分布读写在所有磁盘 有奇偶校验同时保存校验信息在磁盘上 校验信息用于数据恢复 空间利用率1-1/n
RAID 6 读写性能 冗余性 允许故障2块磁盘 最少使用4块硬盘 读性能接近RAID5 写性能比RAID5弱 
```
RAID实现
> 1.软件RAID 使用操作系统实现需占一定资源 受系统稳定性影响 受cpu或硬盘接口速度影响<br/>
> 2.硬件RAID 用独立RAID硬件卡实现 有的评析集成RAID硬件 不受系统影响

软件实现RAID
> linux中通过mdadm软件<br/>
> mdadm支持RAID0 RAID1 RAID4 RAID5 RAID6<br/>
> mdadm可基于多个块硬盘、分区或逻辑卷创建软件RAID<br/>
> 创建好的软件RAID对应/dev/mdn(n为第几个RAID)<br/>
> RAID信息保存在/proc/mdstat文件中 也可通过mdadm命令查看

```
# 创建软件RAID0
mdadam -C /dev/md0 -a yes -l 0 -n 2 /dev/sdb /dev/sdc
# -C 创建一个新的RAID
# -a 自动创建对应设备
# -l 指定要创建的RAID级别 READ 0 - 6
# -n 指定硬盘的数量
# 创建之后对/dev/sdb /dev/sdc操作会损坏RAID

# 添加备份磁盘 通常最后一块磁盘不工作 如果前三块磁盘其中一块故障则自动将最后一块加入RAID
mdadm -C /dev/md0 -a yes -l 5 -n 3 -x 1 /dev/sdb /dev/sdc /dev/sdd /dev/sde

# 创建配置文件
mdadm -D --scan > /dev/mdadm.conf

# 格式化/挂载
mkfs.ext4 /dev/md0
mount /dev/md0 /mnt
```
```
# 关闭RAID
umount /dev/md0
mdadm -S /dev/md0
```
```
# 启用RAID
reboot
# or mdadm -R /dev/md0
```
```
# 删除 数据删 如不删则再用/dev/sdb /dev/sdc报错
madam --zero-superblock /dev/md0
```
```
# 模拟故障 实验或者替换其中某些硬盘情况将使用
mdadm /dev/md0 -f /dev/sdb

# 故障移除
mdadm /dev/md0 -r /dev/sdb

# 换上新硬盘后将新硬盘添加到RAID
mdadm /dev/md0 -a /dev/sdb
```

#### 网卡
```
# 网卡信息
mii-tool eth0

# 网卡底层信息
ethtool eth0

# 网卡底层驱动
ethtool -i eth0

# 网卡状态
ethtool -S eth0
```

IP别名<br/>
软件实现 -> 在一个物理网卡配置多个IP,实现类似接口之类功能

```
# 停图形网卡软件
service NetworkManager stop
chkconfig NetworkManager off
```
临时创建一个IP别名
```
ip addr add 10.1.1.1/24 dev eth0 label eth0:0
# eth0:0第二个0是别名
```
保存配置
```
cd /etc/sysconfig/network-scripts
vim ifcfg-eth0:0
# 内容
DEVICE=eth0:0
IPADDR=10.1.1.1
PREFIX=24
ONPARENT=yes
```
##### 多网卡绑定
多块网卡绑定为一个逻辑网卡以均衡负载<br/>
提带宽/高稳定性<br/>
绑定后物理网卡不再直接使用 IP地址配置在绑定后的逻辑网卡上<br/>
<br/>
<br/>
<br/>
网卡绑定模式:<br/>
1.模式0:平衡轮训<br/>
2.模式1:主动备份<br/>
3.模式3:广播 (每个网卡发一样的数据)

```
ifdown eth0

# 创建配置文件
vim /etc/sysconfig/network-scripts/ifcfg-bond0
# 内容
DEVICE=bond0
IPADDR=192.169.1.200
PREFIX=24
ONBOOT=yes
BOOTPROT=none
USEACTL=no
BONDING_OPTS="mode=1 millmon=50"

# 修改每个属于该逻辑网卡的物理网卡的配置文件
vim /etc/sysconfig/network-scripts/ifcfg-eth0
# 内容
DEVICE=eth0
BOOTPROTO=none
ONBOOT=yes
MASTER=bond0
SLAVE=yes
USEACTL=no

# 给bond网卡添加驱动支持
vim /etc/modprobe.d/bonding.conf
# 内容
alias bond0 bonding

# 网卡激活
ifup bond0
```

#### 网络访问控制
比如控制 可访问服务器的IP 使用协议 接口 是否需要对数据包进行修改<br/>

通过内核netfilter模块实现<br/>
通过iptables程序对netfilter进行控制管理
> 可对数据进行 允许 丢弃 修改操作

```
# netfilter支持通过以下方式对数据包分类
# 源IP地址
# 目标IP地址
# 使用接口
# 使用协议(TCP/UDP/ICMP)
# 端口号
# 连接状态(new/ESTABLISHED/RELATED/INVALID)
```

netfilter用以对数据进行过滤

```

```