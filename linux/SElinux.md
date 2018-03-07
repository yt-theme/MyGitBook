#### SElinux
安全增强linux<br/>
NSA开发<br/>
允许管理员更加灵活定义安全策略
> SElinux是一个内核级安全机制 从linux2.6某些发行版集成<br/>
> 修改可能需要重新启动

##### 基本概念
1.所有安全机制都是对两样东西限制:进程与系统资源(文件,网络套接字,系统调用)<br/>
2.两个基本概念:域和上下文

> 域对进程进行限制<br/>
> 上下文针对系统资源

```
# 查看进程域
ps -Z

# 查看文件上下文 
ls -Z
```

##### 策略
1.通过定义策略控制哪些域可以访问哪些上下文<br/>
2.有很多预置策略 通常不需要自定义策略

> target策略 只有目标进程受SElinux限制 其他进行运行在非限制模式下 目标策略只影响网络应用

##### 三种工作模式
1.强制(enforcing) -> 违反策略的行动都被禁止并作为内核信息记录
2.允许(permissive) -> 违反策略的行动都不被禁止但会产生警告
3.禁用(disable) -> 禁用SElinux 与不带SElinux的系统一样

```
# 配置文件
/etc/systemconfig/selinux

# 设置工作模式
vim /etc/systemconfig/selinux
# 内容
SElinux=permissive
# 或
SElinux=disable
# 或
SElinux=enforcing
```
```
# 查看工作状态
getenforce
```
```
# 临时 设置工作状态
setenforce 0
setenforce 1
```

##### 策略 域 上下文 
```
system_u : object_r : httpd_exec-t : s0
```

##### 恢复上下文
对文件操作可能会改变上下文导致一些进程无法访问某些文件
```
restorecon -R -v /var/www
```

##### 改变上下文
```
chcon --reference=/etc/named.conf.orig /etc/named.conf
# --reference=/etc/named.conf.orig 参照文件
```