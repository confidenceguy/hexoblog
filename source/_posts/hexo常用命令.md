---
title: hexo常用命令
date: 2021-01-06 20:12:59
tags:
    - Tools 
    - 常用命令
categories: Hexo
keywords: 
    - Hexo 
    - 常用命令
cover: https://s3.ax1x.com/2021/01/06/sVoP1S.jpg
---

## 1.简写指令:

 `hexo n` "我的文章" 新建文章    
 `hexo p` 等价于 `hexo publish`
 `hexo g` 等价于 `hexo generate`  
 `hexo s`等价于 `hexo server`     
 `hexo d` 等价于 `hexo deploy`
 `hexo deploy -g`  等价于 `hexo deploy --generate`
 `hexo generate -d`等价于`hexo generate --deploy


**注: hexo  clean 没有 简写,  git --version 没有简写**

## 2.指令说明:

 `hexo server`    #Hexo 会监视文件变动并自动更新，除修改**站点配置文件**外,无须重启服务器,直接刷新网页即可生效。
 `hexo server -s` #以静态模式启动
 `hexo server -p 5000` #更改访问端口   (默认端口为4000，'ctrl + c'关闭server)
 `hexo server -i IP地址` #自定义 IP
 `hexo clean` #清除缓存  ,网页正常情况下可以忽略此条命令,执行该指令后,会删掉站点根目录下的public文件夹
 `hexo g` #生成静态网页  (执行 `$ hexo g`后会在站点根目录下生成public文件夹, hexo会将"/blog/source/"   下面的.md后缀的文件编译为.html后缀的文件,存放在"/blog/public/ "   路径下)
 `hexo d` #将本地数据部署到远端服务器(如github)
 `hexo init 文件夹名称` #初始化XX文件夹名称
 `npm update hexo -g`#升级
 `npm install hexo -g`#安装
 `node-v`          #查看node.js版本号
 `npm -v`        #查看npm版本号
 `git --version`  #查看git版本号
 `hexo -v`      #查看hexo版本号

`hexo publish [layout] <title>`   #通过 `publish` 命令将草稿移动到 `source/_posts` 文件夹,如:`$ hexo publish [layout] <title>`,草稿默认是不会显示在页面中的，可在执行时加上 `--draft` 参数，或是把 `render_drafts` 参数设为 `true`来预览草稿。

`hexo new aaa "bbb"`  # 新建一篇文章,文章名称和标题分别为bbb.md 和 bbb.   文章采用aaa布局,  此时会在站点根目录下的---->source----->_post文件夹下生成bbb.md文件,  bbb.md文件的顶部(-----分割线上方区域,也称作Front matter区),生成

```
layout : aaa`
 `title:`
 `date:
```