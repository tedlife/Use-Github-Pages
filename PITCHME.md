# Github Pages 的 N 种用法

---

Github Pages 是什么？

如果你没使用过 Git 版本控制系统以及 Github 代码托管平台，可能就会有点陌生。如果用过的话，那就好办了。

---

用官方的话说，Github Pages 就是：

> 为你或你的项目提供的网站。直接从你的 Github 仓库代码托管。仅仅需要编辑，推送，然后任何改变都是在线实时的。

相关链接：[Github Pages 官网](https://pages.github.com/)，[Github Pages 帮助](https://help.github.com/categories/github-pages-basics/)

---

## 使用 Github Pages 作为项目页面

---

### 安装 Git

如果没有使用过 Git 和 Github 的，让我们先从安装 Git 以及配置 Github 开始。会使用到命令行工具 MAC 或 Linux 系统都自带了 Shell 命令行软件，Windows 建议使用 [Cmder](http://cmder.net/)，体验更好。

---

MAC OS 下，如果你安装了 Homebrew，直接：

```
brew install git
```

Windows 也非常简单，下载安装 cmder full 版本的，包含了 Git for Windows 的安装了。

---

### 生成 SSH Keys

SSH Keys 是什么？SSH Keys 指的是在电脑上生成的一对密钥，包含公钥 Public Key 与密钥 Private Key。它可以用来验证你的身份。

---

SSH Keys 有什么常用用途？

* 像 Github, Coding.net, gitlab 等等这样的代码托管平台都需要你的 SSH Keys 来验证身份
* 如果你有一台服务器，在服务器添加你本地电脑的 SSH Keys，可以让你免密码通过 SSH 登陆服务器

---

首先打开命令行工具，在生成之前先看下之前是不是已经有了

```
ls ~/.ssh
```

---

如果在这个目录的下面列出了 id_rsa 与 id_rsa.pub，说明已经有了，就不用再生成一次。如果没有，就需要使用下面的命令生成新的 SSH Keys:

```
ssh-keygen
```

一路回车，就可以生成一对 SSH Keys。

---

### 在 Github 中使用 SSH Key

到这里其实就很简单了，把生成的 id_rsa.pub 文件里的密钥复制粘贴到你的 Github 账户里就可以了。

---

首先，使用命令查看 id_rsa.pub 文件内容：

```
cat ~/.ssh/id_rsa.pub
```

然后复制

---

最后，在你的 Github 账户 -> settings -> SSH and GPG keys 中新增一个 SSH Keys 以及粘贴刚才复制的密钥。

---

那么怎么验证你已经有权访问你在 Github 托管的仓库了呢，打开命令行输入：

```
ssh -T git@github.com
```

---

如果显示下面的信息，说明已经大功告成，你的本地电脑就可以顺利和你的 Github 账户联系在一起了：

```
Hi Udacity! You've successfully authenticated, but GitHub does not provide shell access.
```

---

### 新建你的第一个 Github 仓库

下面就开始新建你的第一个 Github 仓库，名称随意，并且为该仓库配置开启 Github Pages

---

## 使用 Github Pages 托管个人博客

---

### Hexo 和 Jekyll 对比

为什么要使用 [Hexo](https://hexo.io/) 和 [Jekyll](https://jekyllrb.com/) 这类静态博客框架，其实就是写博客，管理博客方便，比如说支持 Markdown，支持命令行一键部署，支持插件等等。

---

然后，Jekyll 基于 Ruby 实现，安装 Jekyll 需要搭建 Ruby 环境，在 Windows 搭建 Ruby 环境并不是被推荐的，而 Hexo 基于 NodeJS 实现，在 Windows 上安装 NodeJS 开发环境简单，而且作为前端，使用 NodeJS 更加亲近。

---

### 如何使用 Hexo 静态博客框架

准备工作就是安装好 NodeJS 环境，直接去 NodeJS 官网选择对应系统版本安装就可以。但是其实最佳的方式是通过 [nvm](https://github.com/creationix/nvm) 安装，然后使用 [nrm](https://github.com/Pana/nrm) 切换成淘宝的源。

---

```
# 安装 nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
# 安装最新版本 NodeJS
nvm install node
# 安装稳定版本 NodeJS
nvm install stable
# 切换 node 的版本
nvm use xxx
# 查看当前 node 版本
node -v
# 安装 nrm
npm install -g nrm
# 列出所有可供选择的 NPM registry
nrm ls
# 国内用户建议切换成淘宝的源
nrm use taobao
```

---

然后就可以安装 Hexo 以及使用 Hexo 搭建你的第一个博客

```
# 安装 hexo-cli
npm install hexo-cli -g
# 初始化你的博客文件夹
hexo init yourBlogName
# 进入你的博客目录
cd yourBlogName
# 启动本地 server
hexo server
```

---

### 发布第一篇文章

```
# 新建文章
hexo new postName
# 清理 public 目录 
hexo clean
# 生成静态页面至 public 目录
hexo generate
# 开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo server
```

---

当然你也可以通过其他命令新建页面，新建标签页，配置 RSS 等等，这些可以之后去[Hexo文档](https://hexo.io/docs/)或网上搜索怎么搞。

---

### 配置站点信息

所有配置均可以在 `_config.yaml` 中设置：

* `title` -> 网站标题
* `subtitle` -> 网站副标题
* `description` -> 网站描述
* `author` -> 你的名字
* `language` -> 网站使用的语言
 
️注意：在配置时，需要加上冒号:,冒号后面要加一个英文的空格

---

### 更换主题

[Hexo官网主题](https://hexo.io/themes/)，有很多选择，选择一个，然后下载到，或 git clone 到 themes 文件夹下

```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

---

### 配置主题信息

在站点配置文件，也就是 `_config.yaml` 中，配置 theme

```
theme: next
```

---

### 部署到 Github Pages

---

#### 新建 Github 仓库

创建一个 xxx.github.io 的仓库，这里的 xxx 表示你的 Github 账户名，设置开启下 Github Pages

然后通过 Git 克隆到本地。将上面的 yourBlogName 文件夹中的文件

---

#### 开始部署

安装 hexo-deployer-git：

```
npm install hexo-deployer-git --save
```

---

然后配置：

```
deploy:
	type: git
	repo: <repository url>
	branch: [branch]
```

---

最后部署：

```
# 直接部署
hexo deploy
# 在部署之前先 generate
hexo deploy -g
```
---

## 给 Github Pages 绑定个性域名

---

### 域名是什么

域名其实我们经常看到，比如说 “www.baidu.com”，“cn.udacity.com”，这两个是属于二级域名，一级域名是什么，就是 “baidu.com”，“udacity.com”，每个域名，不管一级域名还是二级域名都对应唯一一个 IP 地址，不知道 IP 地址是什么？只要把它想象成服务器的门牌号就行了。

---

### 如何绑定注册的域名

域名注册是需要付费的，每年大概60元左右，很低的成本，国内的可以去[阿里云万网](https://wanwang.aliyun.com/)注册，国外的知名的有 [Godaddy](https://www.godaddy.com)

---

如何将注册的域名绑定到你刚创建的 Github Pages 呢？

---

在你的 Github 仓库中新增 CNAME 文件，加上你要绑定的域名

然后，去注册域名的服务商网站后台配置你的域名解析


