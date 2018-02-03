---
title: git submodule
subtitle: git 子模块
description: 抄袭于: http://www.cnblogs.com/nicksheng/p/6201711.html，仅支持于自己查找方便
categories: git
tags: git
comments: true
date: 2018-02-03 22:29:21
---

使用场景
当项目越来越庞大之后，不可避免的要拆分成多个子模块，我们希望各个子模块有独立的版本管理，并且由专门的人去维护，这时候我们就要用到git的submodule功能。
常用命令
git clone <repository> --recursive 递归的方式克隆整个项目git submodule add <repository><path> 添加子模块git submodule init 初始化子模块git submodule update 更新子模块git submodule foreach git pull 拉取所有子模块
如何使用
1. 创建带子模块的版本库
例如我们要创建如下结构的项目
project  |--moduleA  |--readme.txt
创建project版本库，并提交readme.txt文件
git init --bare project.gitgit clone project.git project1cd project1echo"This is a project." > readme.txtgit add .git commit -m "add readme.txt"git push origin mastercd ..
创建moduleA版本库，并提交a.txt文件
git init --bare moduleA.gitgit clone moduleA.git moduleA1cd moduleA1echo"This is a submodule." > a.txtgit add .git commit -m "add a.txt"git push origin mastercd ..
在project项目中引入子模块moduleA，并提交子模块信息
cd project1git submodule add ../moduleA.git moduleAgit statusgit diffgit add .git commit -m"add submodule"git push origin mastercd ..
使用git status可以看到多了两个需要提交的文件，其中.gitmodules指定submodule的主要信息，包括子模块的路径和地址信息，moduleA指定了子模块的commit id，使用git diff可以看到这两项的内容。这里需要指出父项目的git并不会记录submodule的文件变动，它是按照commit id指定submodule的git header，所以.gitmodules和moduleA这两项是需要提交到父项目的远程仓库的。
On branch masterYour branch is up-to-datewith'origin/master'.Changes to be committed:  (use "git reset HEAD ..."to unstage)    new file:   .gitmodules    new file:   moduleA
2. 克隆带子模块的版本库
方法一，先clone父项目，再初始化submodule，最后更新submodule，初始化只需要做一次，之后每次只需要直接update就可以了，需要注意submodule默认是不在任何分支上的，它指向父项目存储的submodule commit id。
git clone project.git project2cd project2git submodule initgit submodule updatecd ..
方法二，采用递归参数--recursive，需要注意同样submodule默认是不在任何分支上的，它指向父项目存储的submodule commit id。
git clone project.git project3 --recursive
3. 修改子模块
修改子模块之后只对子模块的版本库产生影响，对父项目的版本库不会产生任何影响，如果父项目需要用到最新的子模块代码，我们需要更新父项目中submodule commit id，默认的我们使用git status就可以看到父项目中submodule commit id已经改变了，我们只需要再次提交就可以了。
cd project1/moduleAgit branchecho"This is a submodule." > b.txtgit add .git commit -m "add b.txt"git push origin mastercd ..git statusgit diffgit add .git commit -m "update submodule add b.txt"git push origin mastercd ..
4. 更新子模块
更新子模块的时候要注意子模块的分支默认不是master。
方法一，先pull父项目，然后执行git submodule update，注意moduleA的分支始终不是master。
cd project2git pullgit submodule updatecd ..
方法二，先进入子模块，然后切换到需要的分支，这里是master分支，然后对子模块pull，这种方法会改变子模块的分支。
cd project3/moduleAgit checkout mastercd ..git submodule foreach git pullcd ..
5. 删除子模块
网上有好多用的是下面这种方法
git rm --cached moduleArm -rf moduleArm .gitmodulesvim .git/config
删除submodule相关的内容，例如下面的内容
[submodule "moduleA"]      url = /Users/nick/dev/nick-doc/testGitSubmodule/moduleA.git
然后提交到远程服务器
git add .git commit -m"remove submodule"
但是我自己本地实验的时候，发现用下面的方式也可以，服务器记录的是.gitmodules和moduleA，本地只要用git的删除命令删除moduleA，再用git status查看状态就会发现.gitmodules和moduleA这两项都已经改变了，至于.git/config，仍会记录submodule信息，但是本地使用也没发现有什么影响，如果重新从服务器克隆则.git/config中不会有submodule信息。
git rm moduleAgit statusgit commit -m"remove submodule"git push origin master