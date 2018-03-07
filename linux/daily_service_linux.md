### 设置默认内核
```
	cat /boot/grub2/grub.cfg
	#比如菜单项有menuentry 'openSUSE Tumbleweed，Linux 4.4.104-39-default'则
	grub2-set-default "openSUSE Tumbleweed，Linux 4.4.104-39-default"
	grub2-mkconfig -o /boot/grub2/grub.cfg 
```

### 开热点
需要安装hostap等依赖

	安装create_ap
```
sudo create_ap wlx000aeb141d6b wlp2s0 MyAccessPoint 121212121
# wlx000... 为用于开热点的无线网卡, wlp... 为提供网络的网卡
# 如果需要密码则如代码所示
# 如果不加密则直接写ssid
```
### 开源驱动造成不能正常开机问题
安装前引导安装程序前也可用
```
# 在grub2启动时按e进入引导参数编辑器,在有linux字样的行追加如下
# 禁用所有显卡驱动模块intel显卡驱动
acpi_osi=linux nomodeset
# 按f10或看下面提示一般可正常启动,但是本代码不会保存
# 如需要保存则将代码加入，同编辑grub2参数时位置一样
sudo nano /boot/grub/grub.cfg 
# 有些发行版是grub2
```
### ubuntu16.4 npm不可正常安装gitbook-cli
```
sudo rm -r /usr/local/lib/node_modules/
sudo npm install gitbook-cli -g
```
### MongoDB数据库
```
sudo apt-get install mongodb
service mongodb start # 开启服务
service mongodb stop # 关闭服务
pgrep mongo -l # 查看是否启动
sudo apt-get --purge remove mongodb mongodb-clients mongodb-server # 卸载
```

使用
```
$mongo

# 显示数据库列表
show dbs

# 显示当前数据库中集合(table)
show collections

# 显示所有用户
show users

# 切换当前数据库至yourDB
use yourDB

# 显示数据库操作命令
db.help()

# 显示集合操作命令(yourcollection集合名)
db.yourCollection.help()
```
MongoDB无建立数据库命令<br/>
建立数据库方法
```
use myDB
db.createCollection('myDBcontent') # 创建集合
```
插入数据二个方法<br/>
1.insert -> 如果_id存在则不操作<br/>
2.save -> 如果_id存在则更新操作<br/>
如果以上两者不加_id则插入数据操作

```
db.myDBcontent.insert({_id:1,name:'laowang',age:20}) # _id可选
db.student.save({_id:1,name:'laowang',age:21}) # _id可选
```
查找数据
```
db.yourCollection.find(criteria,filterDisplay) 
# criteria可选的查询条件
# filterDisplay筛选显示部分数据,如指定列数据
```
```
db.myDB.find() # 查询所有记录 同 select * from myDB
db.myDB.find({name:'laowang'}) # 查询name='laowang'的数据 同select * from myDB where name='laowang'
db.myDB.find({},{name:1,age:1}) # 查询指定列name,age数据 同select name,age from myDB
								# name:1表示返回name列
db.myDB.find({name:'laowang',age:21}) # select * from myDB where name='laowang' and age=21
db.myDB.find({$or:[{age:21},{age:20}]}) # select * from myDB where age=21 or age=20
```
修改数据
```
db.myDB.update(criteria,objNew,upsert,multi)
# criteria : 必选update查询条件 类似sql update查询内where后面的
# objNew : 必选update的对象和一些更新的操作符(如$set),同sql update查询内set后面的
# upsert : 可选如果不存在update记录,是否插入objNew,true为插入 默认false
# multi : 可选mongodb默认false 只更新找到的第一条记录,如果这个参数为true,就把按条件查出来多条记录全部更新 ，默认false只修改匹配到的第一条数据
```
```
db.myDB.update({name:'laowang'},{$set:{age:30}},false,true) # update myDB set age=30 where name='laowang'
```
删除数据
```
db.student.remove({name:'laowang'}) # delete from myDB where name='laowang'
```
退出
```
exit 或 ^+C
```
#### mongodb shell
```
# 查看数据库
showdbs

# 查看当前所在数据库
db

# 临时创建数据库
use openfire

# 在当前数据库删除当前数据库
db.dropDatabase()

# 查看当前库的所有用户
show users

# 查看表
sgiw cikkectuibs

# 创建表
db.createCollection("mycollection")


```
### postman
```
sudo tar -xzf postman.tar.gz -C /yourpath
cd yourpath
./Postman # 运行
sudo ln -s /yourpath/Postman/Postman /usr/bin/postman # 可使用命令
vim /usr/share/applications/postman.desktop # 图标
#===加内容=
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=postman
Icon=/yourpath/Postman/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
```
### vim设置
```
# 显示行号
set number

# 自动缩进
set autoindent

# 设置tab宽度
set tabstop=4
```
改配置文件
```
vim ~/.vimrc
```

### MySQL
```
apt-get install mysql-server
apt-get install mysql-client libmysqlclient-dev

# 登录
mysql -u root -p
# -u 用户名
# -p 密码提示输入
```
```
# 显示数据库
show databases ;

# 启动/停止
service mysqld start
service mysqld stop
```
MySQL图形管理工具
```
sudo apt-get install mysql-workbench-community
```
### debian fcitx
```

apt-get install fcitx-table-wubi

#/etc/X11/Xsession.d/95input
export LANG=en_US.UTF-8
export LC_CTYPE=en_US.UTF-8
export XMODIFIERS=@im=fcitx
fcitx &

```
### debian nodejs&npm
```
sudo apt-get install curl
sudo curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install nodejs npm
```
### debian 163 mirr
```
deb http://mirrors.163.com/debian/ stretch main
deb http://mirrors.163.com/debian/ stretch-updates main non-free contrib
deb-src http://mirrors.163.com/debian/ stretch-updates main non-free contrib
deb http://mirrors.163.com/debian-security/ stretch/updates main non-free contrib
deb http://httpredir.debian.org/debian stretch-backports main contrib non-free
deb http://download.virtualbox.org/virtualbox/debian stretch contrib
```
###时间同步/时区更改/本地化
```
# apt-get install ntpdate -y    # 安装时间同步软件
# ntpdate time.windows.com      # 同步时间

# dpkg-reconfigure tzdata       # 更改时区

# apt-get install locales
# dpkg-reconfigure locales      # 本地化设置
```
### i3 mount wrong
```
su

cd /etc/polkit-1/localauthority/50-local.d/

vim 50-filesystem-mount-system-internal.pkla

#file
[Mount a system-internal device]
Identity=*
Action=org.freedesktop.udisks2.filesystem-mount-system
ResultActive=yes
```

### i3配置
```
#自动启动
exec --no-startup-id pnmixer
exec --no-startup-id nm-applet
```
