### 介绍
	https://github.com/vuejs/vue-cli


### 安装环境
	npm i -g vue-cli
 
### 基本环境代码
	# 创建脚手架程序
	vue-init webpack vue-project-1
    
    #
    第一项问是否要把 vuex-hello-v2 作为项目名称，直接回车，表示同意。
    第二项询问项目描述，回车，保留默认值。
    第三项，询问作者，回车，使用默认值
    第四项，编译工具。直接回车，选择 runtime 也就是运行时，和 compiler 也就是编译器。
    第五项，vue-router ，也就是路由器，回答 n ，回车，先不安装
    第六项，是否使用 ESLint 进行代码检查，选择 n ，避免新手看到过多的报错信息
    第七项，单元测试，回答 n 。
    第八项，e2e 测试，回答 n 。
    第九项，直接回车，选择 npm 作为装包工具。

### 运行项目
	npm run dev
    # 访问 localhost:8080 ，可以看到一个页面运行起来了
    
### 注意
``//methds不使用箭头函数
  methods: {
    Hidden: function () {  //不能使用箭头函数()=>
      this.hide = !this.hide'
      console.log(this.hide)
    },
    Vis: function () {
      this.hide = !this.hide
    }
  //使用生命周期时使用箭头函数
  created () {
    eventBus.$on(
      'sidepopopen', a =>{
          this.close = a
      }
    )
  }
```

v-bind绑定

```

```