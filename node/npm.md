### apm/npm
apm/npm相似 包管理器 在线安装包

```

    apm install emmet                   atom编辑器安装插件
    
    npm init                            管理文件
    
    npm i jquery --save                 非工具类
    
    npm i xx --save-dev                 工具类
    
    npm i jquery@版本号 --save          安装某种版本包
    
    npm unistall jquery                 卸载jq
    
    npm i                               安装package.json里的包
    
    npm i zepto -g                      全局包此电脑任何地方都能使用
    
    npm uninstall zepto -g              删除全局包
    
```

### ignore文件
	.gitignore 文件 git上传时写在该文件内的文件被忽略上传 比如node_modules
> 将本地仓库删除 克隆网上的仓库到本地 将node_modules删除再上传 此时网上就没有了node_modules
然后本地 npm i node_modules 就会出现 此时新建.gitignore 再上传 此时本地的node_modules 就会上传不上去了

### Package.json属性说明

```
name            包名
version         包版本号
description     包描述
homepage        包官网url
author          包作者名
contributors    包的其他贡献者姓名
dependencies    依赖包列表
repository      包代码存放的地方的类型 git/svn
main            程序主入口文件,require就加载这个文件 默认根目录下的index.js
keywords        关键字
```

淘宝npm镜像

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install [name]
```