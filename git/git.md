### git
```
echo "# a" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:yt-theme/a.git
git push -u origin master
```
### git使用
    git init 将          本地文件夹变成git仓库
    git add               将某些文件添加到git的缓存区 .代表所有的修改
    git add index.html    让git跟踪修改
    git commit -m "版本信息" 将本次的修改做成一个版本,并提交版本信息,第一次使用git commit会弹出提示信息
    git status            查看当前仓库状态
    git push              没有推送目标 第一次推送提示没有目标
    ssh-keygen            钥匙
    git-pull              拉取远程的更新到本地
#### git分支
	gh-pages              分支
    git branch            查看当前仓库分支
    git branch 分支名     创建新的分支
    git branch gh-pages   特殊分支
    git checkout 分支名   切换到分支
   > 当创建新的分支时，分支里面的内容默认和master一样 <br/>
   > 如果仓库有gh-pages分支 可用 用户名.github.io/仓库名访问 gh-pages分支下的页面 

#### 合并分支
	merge                 合并分支