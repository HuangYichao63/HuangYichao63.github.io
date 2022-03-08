---
title: "个人博客搭建指南"
author:
  name: HuangYichao
  link: https://github.com/HuangYichao63
date: 2022-03-7 21:16:00 +0800
categories: [tech]
tags: [GitHub Pages, Jekyll]
---


# 前言
---
搭建一个自己的博客系统已经成为我年度 TODO List 里的常客了，接触过一点网页知识的自己总想着得搞一个完全由自己编程的网页，搜罗了一圈的技术路线后不得不败下阵来，本着效率即是一切的原则，主要参考了 [如何搭建个人独立博客?](https://www.zhihu.com/question/20463581)，利用 GitHub Pages 和 Jekyll 搭建了属于自己的博客。

虽然他人的教程已经很详尽了，但是在搭建过程中还是遇到了很多了问题，所以在此进行一些步骤和问题的记录。

> 可以在 [Jekyll Theme](http://jekyllthemes.org/) 中选择喜欢的主题，我选用的是 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/)，所以下述指南是基于搭建Chirpy的步骤。
{: .prompt-tip }


# 环境
---
* Win10
* 科学上网

> 推荐 [v2ray](https://v2sx.com/)；若访问github慢/不稳定，手动设置 v2ray PAC，亲测有效。
{: .prompt-tip }
![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/v2ray%20PAC%20settings.png){:  style="max-width: 70%".normal}
<br>

* [NodeJS](https://nodejs.org/zh-cn/download/)
* [Ruby 3.0.2](https://rubyinstaller.org/downloads/)

> 官网下载可能会很慢，资源自取 [ruby-devkit-3.0.2-1-x64](https://pan.baidu.com/s/1zInLVf4v8qPmdVrMKLJy7w)，提取码：5n6d
{: .prompt-tip }

* [RubyGems 3.2.22](https://rubygems.org/pages/download)
* Jekyll 4.2.2
```shell
$ gem install jekyll # 使用RubyGems安装jekyll
```

* Bundler 2.3.8
```shell
$ gem install bundler
```

* [Git 2.29.2](https://git-scm.com/download/win)
* GitHub 图床 + [PicGo](https://picgo.github.io/PicGo-Doc/zh/guide/)
* 使用 SSH 连接到 GitHub
```shell
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/ssh.png){:  style="max-width: 70%".normal}
<br>

* Personal access token

![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/tokens.png){:  style="max-width: 70%".normal}
<br>
![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/credential.png){:  style="max-width: 70%".normal}
<br>

# 域名
---
* 购买

> 推荐 [GoDaddy](https://sg.godaddy.com/offers/domains/godaddy-b)
{: .prompt-tip }

* 解析

> 推荐 [DNSPOD](https://www.dnspod.cn/?source=DNSPod&page=console&from=nav)
{: .prompt-tip }
![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/dnspod.png){:  style="max-width: 70%".normal}
<br>

# 流程
---
![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/flowchart%20of%20building%20a%20blog.png){:  style="max-width: 70%".normal}
<br>

## 1. 创建新仓库并重命名
推荐使用 [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/generate) 创建新仓库，命名为 `username.github.io`。

## 2. 克隆仓库到本地
```shell
# Git Bash
$ git clone git@github.com:[仓库地址]
# 比如 git clone git@github.com:username/username.github.io
```

## 3. 安装依赖文件
```shell
$ bundle  # 本地仓库目录下打开cmd(windows)
```

## 4. 运行本地服务器
```shell
$ bundle exec jekyll serve # 运行成功后即可在 http://localhost:4000 查看博客内容
```

## 5. 自定义内容
- _config.yml
  - url（域名）
  - avatar（头像 url）
  - timezone（Asia/Shanghai）
  - lang（zh-CN）

- favicons
  - 新建文件夹 `assets/img/favicons/`{: .filepath}
  - 使用在线工具 [Real Favicon Generator](https://realfavicongenerator.net/) 生成自己的网站图标
  ![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/select%20image.png){:  style="max-width: 70%".normal}
  <br>
  ![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/generate%20favicons.png){:  style="max-width: 70%".normal}
  <br>

  - 下载生成的文件，解压后删除下面两个文件后将剩下的复制到新建的文件夹中
    - browserconfig.xml
    - site.webmanifest

## 6.  使用 Github Actions 部署到远程仓库
- 确保本地仓库有以下两个文件
  - `.github/workflows/pages-deploy.yml`{: .filepath}
  - `tools/deploy.sh`{: .filepath}

- 若非Linux系统，需更新锁定文件中的平台列表
```shell
$ bundle lock --add-platform x86_64-linux
```
- 用命令行或 GitHub Desktop 将修改内容 push 到远程仓库
- 设置 GitHub Pages 的 Source 以及填入域名
 ![](https://raw.githubusercontent.com/HuangYichao63/blog-img/main/gh-pages-sources.png){: style="max-width: 70%".normal}
  <br>





