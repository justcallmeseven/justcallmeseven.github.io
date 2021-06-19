# 简的博客
基于HEXO搭建---https://justcallmeseven.github.io

##  HEXO设置

- 安装 Hexo 需要先安装下列应用程序

  1. Node.js（Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本）
  2. Git

- 淘宝镜像（即cnpm），它把npm官方的“包”全部搬到国内(卸载 npm uninstall cnpm -g)

  ```yaml
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  ```

- Git命令(卸载 npm uninstall hexo-cli -g)
  下面选择一个执行（建议cnpm）:

  ```yaml
  npm install -g hexo-cli
  cnpm install -g hexo-cli
  ```

- 在空文件下执行初始化

  ```yaml
  hexo init
  ```

  或者

  ```yaml
  hexo init myblog   //myblog名字自己取
  cd myblog          //进入myblog文件夹
  npm install
  ```

  init 执行到 Install dependencies 的时候可能会卡住 Ctrl C 退出

  以上方法要是不能完成博客的初始化，尝试下面方法：

  ```yaml
  git clone https://e.coding.net/hellosummer/myhexoblog/myhexoblog.git
  ```

  把克隆下来的复制到myblog，在myblog执行cnpm install

- hexo g      //生成/public文件夹，里面是网站/生成静态文件
  hexo s      //若报错，执行下一步,没有报错忽略

  *Hexo 3.0 把服务器独立成了个别模块，必须先安装 hexo-server 才能使用*

  ```yaml
  npm install hexo-server --save
  ```

  有时可能报：

  ```yaml
  npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.3.2(node_modules\fsevents):
  npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.3.2: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"}
  ```

  这不是什么大问题，只是你的某些包依赖fsevents包，而fsevents包是MacOS系统下，在Windows/Linux下会提示警告，但不会安装

  ```yaml
  $ hexo s
  INFO  Start processing
  INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
  ```
  
  出现这样的信息即可访问
  
  ***
  
  ####  部署GIT
  
  1. 在博客根目录下打开git bash，分别执行下面的命令：
  
  ```yaml
  git config --global user.name "yourname"
  git config --global user.email "youremail"
  ```
  
  2. 创建一个git秘钥
     打开git bash（哪里打开无所谓），执行
  
     ```yaml
     ssh-keygen -t rsa -C "youremail"   //一路回车
     ```
  
     再执行
  
     ```yaml
     cat ~/.ssh/id_rsa.pub              //面板查看输出的密匙，复制
     ```
  
  3. Github网页>>>Settings>>>Deploy keys
  
     然后打开git bash
  
     ```yaml
     ssh -T git@github.com
     ```
  
     提示下面这个，输入yes回车
     Are you sure you want to continue connecting (yes/no/[fingerprint])? 
  
  4. 打开项目，选 SSH 复制git开头的地址
  
     打开站点配置文件，修改deploy信息
  
     ```yaml
     deploy:
       type: git
       repository: git@github.com:yourname/yourname.github.io.git  （repo:也可以）
       branch: main
     ```
  
     如果网站在服务器上，则可以用 rsync
  
     ```yaml
     deploy:
       type: rsync
       host: 服务器名
       user: 用户名
       root: 放网站的文件夹
       port: 22
     ```
     
  5. 然后安装上传插件
  
     ```yaml
     cnpm install hexo-deployer-git --save
     ```
  
  6. 在博客根目录下打开git bash，执行下面的命令上传
  
     ```yaml
     hexo clean
     hexo generate
     hexo deploy
     ```
  
  ***
  
  ####  升级HEXO
  
  1. ```yaml
     npm install -g cnpm --registry=https://registry.npm.taobao.org（安装过忽略）
     ```
  
  2. ```yaml
     cnpm install -g cnpm    //升级 npm
     cnpm cache clean -f     //清除 npm 缓存
     ```
  
  3. 更新 hexo: 进入 blog 目录，执行如下命令(以上实际没执行，直接来这步了)
  
     ```yaml
     cnpm install -g npm-check     //检查之前安装的插件，都有哪些是可以升级的 
     cnpm install -g npm-upgrade   //升级系统中的插件
     npm-check
     npm-upgrade                   //一路回车即可
     ```
  
  4. 更新 hexo 及所有插件
  
     ```yaml
     cnpm update
     
     hexo -v    //更新完查看版本信息
     
     若启动报错（没报错忽略）
     extends includes/layout.pug block content #recent-posts.recent-posts include includes/recent-posts.pug include includes/pagination.pug 
     
     git bash输入命令
     npm install --save hexo-renderer-jade hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive
     ```



##  简介

怎么描写才能惊艳到在座的各位呢（托腮.jpg）
