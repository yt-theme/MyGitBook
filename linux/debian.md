清除软件残留文件
```
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P
```
