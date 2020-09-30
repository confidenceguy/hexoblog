---
title: git学习记录
date: 2020-09-07 10:13:35
tags: 
    - git 
categories: git
keywords: git
cover: https://s1.ax1x.com/2020/09/30/0uDgcF.jpg
---

## 1.git简介

分布式版本控制系统  

## 2.在  Git环境搭建（windows）  

安装完成后配置自己的信息

``` bash
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com " 
```

### （1）创建版本库

``` bash
$ mkdir learngit
$ cd learngit
$ pwd  
```

通过 git init 命令把这个目录变成 Git 可以管理的仓库：  

``` bash
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/  
```

注意编译软件的选择

### （2）把文件添加到版本库  

第一步，用命令 git add 告诉 Git，把文件添加到仓库：

``` bash
$ git add readme.txt  
```

第二步，用命令 git commit 告诉 Git，把文件提交到仓库：  

``` bash
$ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
1 file changed, 2 insertions(+)
create mode 100644 readme.txt  
```

## 3.版本控制

### （1）仓库状态

 git status查看当前仓库里的文件状态:

``` bash
$ git status
\# On branch master
\# Changes not staged for commit:
\# (use "git add <file>..." to update what will be committed)
\# (use "git checkout -- <file>..." to discard changes in working directory)
\#
\# modified: readme.txt
\#
no changes added to commit (use "git add" and/or "git commit -a")  
```

查看修改了哪些内容

``` bash
$ git diff 文件名
```

查看git日志

``` bash
$ git log  
```

### （2）版本回退

在 Git 中，用 HEAD 表示当前版本，也就是最新的提交 3628164...882e1e0 （注意我的提交 ID 和你的肯定不一样），上一个版本就是 HEAD^ ，上上一个版本就是 HEAD^^ ，当然往上 100 个版本写 100 个 ^ 比较容易数不过来，所以写成 HEAD~100 。

``` bash
$ git reset --hard HEAD^
HEAD is now at ea34578 add distributed  
```

Git 提供了一个命令 git reflog 用来记录你的每一次命令：  

``` bash
$ git reflog
ea34578 HEAD@{0}: reset: moving to HEAD^
3628164 HEAD@{1}: commit: append GPL
ea34578 HEAD@{2}: commit: add distributed
cb926e7 HEAD@{3}: commit (initial): wrote a readme file  
```

###  （3）工作区和暂存区


我们把文件往 Git 版本库里添加的时候，是分两步执行的：  

第一步是用 git add 把文件添加进去，实际上就是把文件修改添加到暂存区；
第二步是用 git commit 提交更改，实际上就是把暂存区的所有内容提交到当前分支。  

![avatar](/img/article/git_workspace_image.png)

git checkout -- file 可以丢弃工作区的修改：  

``` bash
$ git checkout -- readme.txt  
```

git checkout -- file 命令中的--很重要，没有--，就变成了“创建一个新分支”的命令 。 

git reset HEAD file 可以把暂存区的修改撤销掉（unstage），重新放回工作区：  

``` bash
$ git reset HEAD readme.txt  
```

### （4）删除文件


确实要从版本库中删除该文件，那就用命令 git rm 删掉，并且 git commit ：  

``` bash
$ git rm test.txt
rm 'test.txt'
$ git commit -m "remove test.txt"
[master d17efd8] remove test.txt
1 file changed, 1 deletion(-)
delete mode 100644 test.txt  
```

如果删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本 ：


``` bash
$ git checkout -- test.txt  
```

## 4.分支管理

### （1）创建与合并分支


创建 dev 分支，然后切换到 dev 分支：  

``` bash
$ git checkout -b dev
Switched to a new branch 'dev'  
```

git checkout 命令加上 -b 参数表示创建并切换，相当于以下两条命令：  

``` bash
$ git branch dev
$ git checkout dev
Switched to branch 'dev'  
```

然后，用 git branch 命令查看当前分支： 

``` bash
 $ git branch
\* dev
master  
```

把 dev 分支的工作成果合并到 master 分支上：  

``` bash
$ git merge dev
Updating d17efd8..fec145a
Fast-forward
readme.txt | 1 +
1 file changed, 1 insertion(+)  
```

合并完成后，就可以放心地删除 dev 分支了：  

``` bash
$ git branch -d dev
Deleted branch dev (was fec145a).  
```

### （2）小结

{% note primary no-icon %}
Git 鼓励大量使用分支：
查看分支：git branch
创建分支：git branch 分支名
切换分支：git checkout 分支名
创建+切换分支：git checkout -b
合并某分支到当前分支：git merge
删除分支：git branch -d  
当 Git 无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。用 git log --graph 命令可以看到分支合并图。  
{% endnote %}