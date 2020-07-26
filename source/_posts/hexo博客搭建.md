---
title: hexo博客搭建
date: 2020-07-16 13:41:32
tags: 
- Hexo
keywords: "Hexo, 搭建， 部署"
categories: 
  - Hexo
  - 教程
toc_number: false
cover: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1594984602256&di=2bdb6d228c3100b76eb182ffb892fa59&imgtype=0&src=http%3A%2F%2Fimg4.imgtn.bdimg.com%2Fit%2Fu%3D1402406314%2C3856743612%26fm%3D214%26gp%3D0.jpg
top_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1594984559166&di=41fbd4b4704fcb05d7d9513c47ecc3c9&imgtype=0&src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201702%2F28%2F20170228124358_WFiy3.jpeg
top: false
---

# 一、本地部署

## 1、安装Git

windows：到git官网上下载，[Download git](https://gitforwindows.org/)，下载后会有一个Git Bash的命令行工具，以后就用这个工具来使用git，不用自带的cmd，因为它有点难用。

## 2、安装Node.js

windows：[nodejs](https://nodejs.org/en/download/) 选择LTS版本就行了。

## 3、安装Hexo

右键Git Bash Here，输入命令

```
npm install -g hexo -cli//若出错请看下文踩坑部分
```

安装完毕后文件路径在你安装的node.js文件下的node_global\node_modules\hexo

## 4、初始化Hexo

在你想创建Blog文件夹的磁盘下面右键Git Bash Here，输入命令

```
hexo init Blog
cd Blog //进入这个myblog文件夹，也可以直接右键创建好的Blog文件夹点击Git Bash Here
npm install
```

新建完成后，指定文件夹目录下有：

- node_modules: 依赖包
- public：存放生成的页面
- scaffolds：生成文章的一些模板
- source：用来存放你的文章
- themes：主题
- _config.yml: 博客的配置文件

继续输入命令行

```
hexo g//或者 hexo generate
hexo s//或者hexo server
```

启动hexo的服务，在浏览器输入localhost:4000就可以看到你生成的博客了，使用ctrl+c可以把服务关掉。

*tip：所有的操作都基于Blog文件夹，如若出错大不了直接删除Blog重新来，不要畏手畏脚*

# 二、远端部署

## 1、登录或注册GitHub账户

登录后或注册完（tip:注册一个你觉得好听的名字，关系到后面的域名），在GitHub.com中看到一个New repository，新建仓库

必须创建一个和你用户名xxx相同的仓库，后面加.github.io（xxx.github.io //这就是名字取好听点的原因）

## 2、将hexo部署到GitHub

打开Blog文件夹下面的配置文件 `_config.yml`，翻到最后，修改为

```
deploy:
  type: git
  repo: https://github.com/YourgithubName/xxx.github.io.git
  branch: master
```

这个时候需要先安装deploy-git ，也就是部署的命令，这样你才能用命令部署到GitHub

```
npm install hexo-deployer-git --save
```

然后

```
hexo cl //或hexo clean       清除了你之前生成的东西，网页没什么错误基本不用
hexo g //或hexo generate     或生成静态文章
hexo d //或hexo deploy       部署文章
```

*注意：远端部署一定要先 `hexo g`，然后 `hexo d`*

当然如果觉得这个网址逼格不太够，你可以自己花点小钱购买个域名，具体操作请百度

# 三、写博客

## 1、布局

Hexo 有三种默认布局：`post`、`page` 和 `draft`，它们分别对应不同的路径，而您自定义的其他布局和 `post` 相同，都将储存到 `source/_posts` 文件夹。

| 布局  |      路径      |
| :---: | :------------: |
| post  | source/_posts  |
| page  |     source     |
| draft | source/_drafts |

```
hexo n "xxx" //或者hexo new "xxx"、 hexo new post "xxx" (有引号)
```

它其实默认使用的是`post`这个布局，也就是在`source`文件夹下的`_post`里面。

```
hexo new draft "xxx"  (有引号)
```

这样会在source/_draft中新建一个xxx.md文件，如果你的草稿文件写的过程中，想要预览一下，那么可以使用 `hexo server --draft` 在本地端口中开启服务预览。如果你的草稿文件写完了，想要发表到post中，可以使用`hexo publish draft xxx` ，就会自动把xxx.md发送到post中。

```
hexo new page xxx  (无引号)
```

另起一页，系统会自动给你在source文件夹下创建一个xxx文件夹，以及xxx文件夹中的index.md，这样你访问的xxx对应的链接就是`http://localhost:4000/xxx 或者 域名/xxx`

## 2、内容

如果不会MarkDown语法写文章，推荐下载[Typora](https://www.typora.io/)，轻松写博客。

# 四、更换主题

到这一步，如果你觉得默认的`landscape`主题不好看，那么可以在官网的主题中，选择你喜欢的一个主题进行修改就可以啦。[点这里](https://hexo.io/themes/)

兄弟们也可以参考我使用的主题，个人感觉还是挺漂亮的，步骤如下：

## 1、下载主题

右键Blog文件夹，点击Git Bash Here，输入命令

```
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

下载好的主题在`Blog\themes\butterfly`可以查看到

##  2、应用主题

修改站点配置文件`_config.yml`，把主題改为`butterfly`

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: butterfly
```

# 五、Hexo踩坑之路

## 1、`npm install -g hexo -cli` 命令错误

安装hexo中出现报错`npm WARN deprecated hexo-bunyan@2.0.0: Please see https://github.com/hexojs/hexo-bunyan/issues/17`

解决办法：将`npm install -g hexo -cli`改成`npm install -g hexo -log`

问题分析：根据报错给出的网站 `https://github.com/hexojs/hexo-bunyan/issues/17`来看，hexo-log v2.0.0发布后就不再推荐使用hexo-bunyan，猜想hexo官方文档给出的npm install -g hexo-cli命令默认安装hexo-bunyan，尝试改成hexo-log之后就可以继续下一步了。

## 2、Typora写博客时网页图片加载失败

解决办法：

- 首先把主页配置文件`_config.yml` 里的`post_asset_folder:`这个选项设置为`true`

- 其次下载安装一个可以上传本地图片的插件`hexo-asset-image`

```
npm install hexo-asset-image --save  //下载插件
hexo n "xxx"  /在下载完插件后，使用hexo命令新建文章时，posts目录下会生成同名文件夹；
#远端部署
hexo g  //在文件夹里可以存放相应的图片，然后在hexo g编译文件的时候，图片会自动生成到public中
hexo d
```

- 然后设置Typora--文件--偏好设置


![1594900826(1)](hexo博客搭建/Typora设置.png)

- 最后把图片拖动到Typora中，点击`复制图片到`同名文件夹中，最后图片成功在网页中显示


![1594901055(1)](hexo博客搭建/图片路径.png)