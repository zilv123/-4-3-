# git与NPM

#### 一、GIT

- GIT基础管理：下载安装、基础介绍、集中式，公布式、工作流程、基础命令(这个第一阶段基础应用)
- GIT-HUB的应用：网站的常规操作，与GIT操作结合管理
- NODE模块管理工具：npm的基础应用
- ...
- 官网:[https//git-scm.com/](https//git-scm.com/)
- 1.git的发展历史

##### GIT版本控制系统：

1.记录历史版本信息(记录每一次修改的记录)

2.方便团队相互之间协作开发

......

##### 常用的版本控制系统

- cvs/svn:集中式版本控制系统
- git:分布式版本控制系统

##### GIT工作原理

- 工作区
- 缓存区
- 历史区

工作区>缓存区>历史区

##### 1.git全局配置

第一次安装完成git后,我们在全局环境下配置基本信息:我是谁？

```shell
$ git config -l 查看配置信息
$ git config --global -l 查看全局配置信息

配置全局信息:用户名和邮箱
$ git config --global user.name 'xxx'
$ git config --global user.email 'xxx@xx.xx'
```

##### 2.创建仓库完成版本控制

>创建本地git仓库

```shell
$ git init 
//=>会生成一个隐藏文件夹".git"(这个文件夹前往不要删，因为暂存区和历史区还有一些其他信息都在这，删了就不是一个完整的git仓库)
```

>在本地编写完成代码后(在工作区)，把一些文件提交到暂存区

```shell
$ git add xxx 把某一个问价或者文件夹提交到暂存区
$ git add . 把仓库中所有最新修改的文件都是提交到暂存区
$ git add -A 把当前仓库所有最新修改的文件都提交到暂存区

$ git status 查看当前文件的状态(红色代表在工作区，绿色代表在暂存区，看不见东西证明所有修改的信息都已经提交到历史区)
```

`提交到历史区`

```shell
$ git commit -m '注释' 将暂存区的文件提交到历史区，并生成版本号 6e2ba15ad04f0cf8a3f92f8f5fc6ea2cbe5689bb

$ git log 查看提交记录
```

##### 3.版本控制回滚

> 从暂存区回滚

```shell
$ git reset --hard HEAD^ 回滚到上一个版本
版本号或版本号前7位 回滚到前2个版本
$ git reset --hard xxx (版本号或版本号前7位)，回滚到指定版本号，如果式版本号前几位，git会自动寻找匹配的版本号
$ git reset --hard xxx (版本号或版本号前7位)，filename,回滚某个文件到指定版本号
$ git reflog 若想回滚到未来的版本，输出用户之前的所有命令，找到用户以前的commit操作的版本id
```

##### GIT和GIT-HUB

>GIT-HUB:https/www.github.com
>
>一个网站(一个开源的源代码管理平台),用户注册后，可以在自己账户下创建仓库，用来管理项目的源代码(源代码是基于git传到仓库中)
>
>我们所熟知的插件、类库、框架等都是在这个平台上有托管，我们可以下在观看和研究源码等

##### 1.settings用户设置

- Account 可以修改用户名
- Security 可以修改自己密码
- Emails 邮箱(必须进行邮箱校验)
- ......git

##### 2.创建仓库

new repository -> 填写信息 ->Create repository

- pubilc 公共仓库为开源项目

- private 私有仓库作为内部团队协作管理项目

- Settings ->删除仓库 Delete this repository

  ​		->Collaborators 设置协作开放的人员

  Code 可以查看历史版本信息和分支信息

##### 3.把本地仓库信息提交到远程仓库

```shell
//=>建立本地仓库和远程仓库的链接
查看本地仓库和那些远程仓库保持链接
$ git remote -v
让本地仓库和远程仓库新建一个链接 origin 是随便起的一个链接名(可以改变自己想要的，只不过一般用这个名字)
$ git remote add origin [GIT远程仓库地址]
删除关联信息
$ git remote rm origin
```

```shell
提交之前最好先拉取
$ git pull origin main 
把本地提交到远程仓库(需要输入GITHUB的用户名和密码)
$ git push origin main
```

```shell
$ git clone [远程仓库git地址] [别名：可以不设置，默认是仓库名]
/*
 *真实项目开发流程
 *  1.组长或者负责人创建中央仓库(增加协作者)
 *  2.小组成员基于 $ git clone 把远程仓库及默认的内容克隆到本地一份(解决了三个事情：初始化一个本地仓库"git init"、和对应的远程仓库也保持了关联"git remote add"、把远程仓库默认内容拉取到本地"git pull")
 *  3.每个组员写完自己的程序后，基于"git add/git commit"、把自己修改的内容放到历史区，然后通过"git pull/git push"、把本地信息和远程仓库信息保持同步即可(可能涉及冲突的处理)
```

#### 二、NPM

>node package manger :NODE模块管理工具，根据npm我们可以快速安装、卸载所需要的资源文件(例如：jQuery、vue、vue-router...)
>
>
>
>区NODE官网：https://nodejs.org/zh-cn/下载NODE(长期支持版)，安装NODE后，npm也就跟着安装
>
>$ node -v
>
>$ npm -v 出现版本号证明安装成功 

##### 基于npm进行模块管理

>https://www.npmjs.com/ 基于npm是从npmjs.com平台上下载安装

```shell
$ npm install xxx 把模块安装当前项目中(node_modules)
$ npm install xxx -g 把模块安装在全局环境中
$ npm xxx@1.0.0 安装指定版本号的模块
$ npm view xxx versions > xx.version.json 产看某个版本号信息(输出到指定JSON文件中)
$ npm install xxx -g 把模块安装在全局环境中
$ npm uninstall xxx 把当前项目中的模块卸载
$ npm uninstall xxx -g 把全局环境中的模块卸载
$ npm root -g 查看模块全局安装路径

/*
 *什么情况下会把模块安装在全局？
 *       ->可以使用"命令"对任何的项目进行操作
 *		 ->$ npm root -g 查看全局安装的目录
 *  	 ->因为在安装目录下生成xxx.cmd的文件，所以我们能够使用xxx的命令进行操作
 */
 /*安装在本地项目中的模块
  *  	->可以在项目导入进来使用
  *  	->但是默认不能基于命令来操作(因为没有.cmd文件)
  *  	->但是可以基于package.json中script，配置一些npm可以执行命令，配置后通过 $ npm run xxx执行
  */
  
  $ npm init -y 初始化当前项目的配值依赖清单(项目文件夹的名字中不能出现中文，大写字母和特殊符号)
  =>创建成功后在当前项目中生成 package.json 的清单文件
  dependencies ：生产以来模块(开发和项目部署的时候都需要)
  devDependencies ：开发以来模块(只有开发的时候需要)
  script ：配置本地可执行命令
  
  $ npm i xxx --save 把模块保存在清单生产依赖中
  $ npm i xxx --save-dev 把模块保存在清单开发依赖中
  $ npm install 跑环境，按照清单安装所需的模块              
```

##### 一个新的项目的开始：

1.创建项目文件夹

2.把他作为一个新的仓库进行代码管理(可以基于$git clone 把远程仓库克隆下来即可)

3.初始化模块配置清单package.json : $npm init -y

4.安装所需要的模块：$npm i jquery bootstrap@3 less ...

5.正常开发

6.开发中：可能需要在本地配置命令去完成一些功能(例如LESS文件编译，此时需要配置npm可执行命令)

7.开发中我们需要基于git把文件进行管理：生成对应的历史版本提交到暂存区、历史区、远程仓库的时候，项目中很多文件无需处理和提交的，例如：node_modules、.idea...,不需要提交的，我们生成一个.gitgnore忽略文件

```
# dependencies
node_modules
...
```

8.由于每次git提交的时候，我们都不去提交node_modules,所以团队协作开发中，我们每次拉下来程序后，都需要"跑环境"：执行$ npm install,按照项目中的package.json中的依赖项信息，把缺失的模块都安装一遍

基于yarn进行第三方模块管理

$ npm install yarn -g  使用npm安装yarn

$ yarn init/yarn install 初始化package.json文件

$yarn add xxx@xx.xx -dev 安装需要的包模块

$yarn remove xxx 移出相应包模块

...

yarn不能安装全局模块

基于nrm切源(镜像源)提高npm的速度

$ npm install nrm -g 全局安装nrm

$ nrm 查看可用的国内镜像源

$ nrm use xxx 切换到你想用的镜像源

接下来正常使用npm命令即可,他会自动从你选择的镜像源去获取资源