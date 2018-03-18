---
title: git学习笔记
date: 2015-05-03 10:19:50
tags:
- 阅读
- 技术
---

开始阅读git权威指南

  

第一章：

1、diff和patch的联合使用

2、cvs -> svn -> git

  

第二章和第三章：

废话太多，过

<!--more-->
  

第四章：

命令：

git --version

git config 和 git config--global 和 git config --system 三种命令

git init 初始化当前目录，生成 .git目录，即版本库（此目录只在根目录下有）

git add 和 git commit （这两个命令常用，可以设置别名）

  

第五章：

概念：

git 暂存区（stage）

  

[![](http://s7.sinaimg.cn/mw690/001hbb8fgy6Gc5Cvs6ab6&690)](http://blog.photo.sina.com.cn/showpic.html#url=http://album.sina.com.cn/pic/001hbb8fgy6Gc5Cvs6ab6)  
  

注：左侧是工作区，右侧是.git目录下的所有东西，其中index就是所谓的暂存区，objects是实体对象库，HEAD是master所在分支

注：add 命令之后会把工作区的内容存到暂存区，commit命令之后才会把暂存区的内容存到master分支中

  

命令：

git diff（工作区和暂存区比较） 和 git diff --cached（暂存区和HEAD比较）和 git diff HEAD（工作区和HEAD比较）

git status 的输出（加 -s 选择可以得到简略的输出，记住其中第一个M和第二个M的意义）

  

  

第六章、第七章和第八章：

概念：

对象ID（40位十六进制的SHA1哈希值）

[![](http://s12.sinaimg.cn/mw690/001hbb8fgy6Gc6fCnH5cb&690)](http://blog.photo.sina.com.cn/showpic.html#url=http://album.sina.com.cn/pic/001hbb8fgy6Gc6fCnH5cb)  
  

  

[![](http://s1.sinaimg.cn/mw690/001hbb8fgy6Gc6sLKxi50&690)](http://blog.photo.sina.com.cn/showpic.html#url=http://album.sina.com.cn/pic/001hbb8fgy6Gc6sLKxi50)  
  

  

  

命令：

git branch 查看当前所在的分支

git log 可以查看提交的记录（常用的选项包括 --graph 和 --oneline）

git log -l HEAD/master 可以查看HEAD或者master指向的commit结构

git rev-parse HEAD/master 可以得到他们的对象ID

linux 命令中的 sha1sum

git reset 可以重新设置master分支到任意一个commit（如 HEAD^，即HEAD的上一个commit）

reflog可以用来记录改变的分支操作，以防止误操作导致指针指向无法找回

git checkout可以重置 HEAD指针

git merge + 对象ID 可以把某个commit 合并到master分支中

（git reset 和 git checkout 两个命令的详细用法见原书第七和第八章）
