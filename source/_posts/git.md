---
title: git
date: 2018-02-03 23:19:34
description: git的用法
categories: git
tags: git
comments: true
---
# Git用法

## 1 建立仓库
+ 远程
`git remote add origin git@github.com:ghxdghxd/$NAME.git`
+ 本地
`git init`

## 2 常用操作

+ 拉取  `git pull origin master`
+ 提交
```shell
git add *.py
git commit -m "message"
git push origin master/dev/develop
```

## 2 分支类型

|主支|修补|发布|开发|功能|
|:-:|:-:|:-:|:-:|:-:|
|master|hotfix|release|develop|feature|

### 查看本地/全部/远程分支

    git branch  /-a/r

### 建立分支

    git branch [name]

### 删除分支

    git branch -d [name]

### 建立并切换开发分支

    git checkout -b [name] origin/develop

### 切换分支

    git checkout [name]

### 合并分支

    git merge --no-ff [name]

### 本地分支提交到远程

    git push origin dev:develop

### 重命名

    git mv

## 删除

    git rm

#### push命令用于将本地分支的更新，推送到远程主机。
它的格式与git pull命令相仿。

    git push <远程主机名> <本地分支名>:<远程分支名>

注意，分支推送顺序的写法是<来源地>:<目的地>，
所以git pull是<远程分支>:<本地分支>，而git push是<本地分支>:<远程分支>。
如果省略远程分支名，则表示将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建。

    git push origin master

上面命令表示，将本地的master分支推送到origin主机的master分支。如果后者不存在，则会被新建。

**如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。**

    git push origin :master

等同于

    git push origin --delete master

上面命令表示删除origin主机的master分支。

如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。

    git push origin
上面命令表示，将当前分支推送到origin主机的对应分支。

如果当前分支只有一个追踪分支，那么主机名都可以省略。

    git push
如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。

    git push -u origin master
上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。

不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用git config命令。

    git config --global push.default matching

或者

    git config --global push.default simple

还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用–all选项。

    git push --all origin
上面命令表示，将所有本地分支都推送到origin主机。

如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用–force选项。

    git push --force origin
上面命令使用–force选项，结果导致在远程主机产生一个”非直进式”的合并(non-fast-forward merge)。除非你很确定要这样做，否则应该尽量避免使用–force选项。

最后，git push不会推送标签(tag)，除非使用–tags选项。

    git push origin --tags

## 中文乱码
    git config --global core.quotepath false
core.quotepath设为false的话，就不会对0x80以上的字符进行quote。中文显示正常。

## gitignore忽略文件

```
1、配置语法：

　　以斜杠“/”开头表示目录；

　　以星号“*”通配多个字符；

　　以问号“?”通配单个字符

　　以方括号“[]”包含单个字符的匹配列表；

　　以叹号“!”表示不忽略(跟踪)匹配到的文件或目录；

　　

　　此外，git 对于 .ignore 配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效；

2、示例：

　　（1）规则：fd1/*
　　　　  说明：忽略目录 fd1 下的全部内容；注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略；

　　（2）规则：/fd1/*
　　　　  说明：忽略根目录下的 /fd1/ 目录的全部内容；

　　（3）规则：

/*
!.gitignore
!/fw/bin/
!/fw/sf/

说明：忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录；
```
## git 子模块
> 仓库包括别的仓库

```
git submodule add <仓库地址> <本地路径>
```