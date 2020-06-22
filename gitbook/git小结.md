## git工作流

![image-20200610141456147](/Users/liguopei/Library/Application Support/typora-user-images/image-20200610141456147.png)

## 一、新建代码库

```
// 在当前目录新建一个Git代码库
$ git init

// 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

// 下载一个项目和它的整个代码历史
$ git clone [url]
```

## 二、配置

Git的设置文件为`.gitconfig`，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

```
// 显示当前的Git配置
$ git config --list

// 编辑Git配置文件
$ git config -e [--global]

// 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

## 三、提交代码流程

1、git add 

2、git commit

3、git push 

4、git push origin 分支名

## 四、分支

### 查看分支

本地分支：git branch 

远程分支：git branch -r

本地分支和远程分支：git branch -a

### 新建分支

git branch 分支名称；不切换分支

git checkout -b 分支名称；切换到新建的分支

### 切换分支

git checkout 分支名称

git checkout -b 分支名城 ；新建分支并切换到该分支

### 删除分支

删除本地分支：

git branch -d 分支名称

删除远程分支：

git push origin --delete 分支名称

### 合并分支

待完善

## 五、查看信息

```
#显示变更的文件

git status

#查看当前分支的历史版本信息

git log

#显示某个文件的版本历史，包括文件改名

git log --follow file

#显示工作区与当前分支最新commit之间的差异

git diff HEAD

#查看某次提交元数据和内容的变化

git show [commit]

#查看某次提交某个文件的内容

git show [commit]:[filename]
```

## 六、版本回退

### 1、本地分支版本回退

查看回退的版本commit id

```
git reflog
```

回退版本

```
git reset --hard xxxx
```

其中，xxxx为所要回退版本的commit id的前面几位。

注意：本地分支会滚后，版本将落后于远程分支，必须使用强制推送覆盖远程分支，否则无法推送到远程分支。

git rm --f filename

git checkout -- filename  //撤销文件的改动

git reset HEAD file  //撤销add操作

git reset --soft HEAD^ //撤销commit操作，回到上一个版本

### 二、公共远程分支版本回退

 **git revert  **

```
git revert 命令意思是撤销某次提交。它会产生一个新的提交，虽然代码回退了，但是版本依然是向前的，所以，当你用revert回退之后，所有人pull之后，他们的代码也自动的回退了.

revert 是撤销一次提交，所以后面的commit id是你需要回滚到的版本的前一次提交

使用revert HEAD是撤销最近的一次提交，如果你最近一次提交是用revert命令产生的，那么你再执行一次，就相当于撤销了上次的撤销操作，换句话说，你连续执行两次revert HEAD命令，就跟没执行是一样的

使用revert HEAD~1 表示撤销最近2次提交，这个数字是从0开始的，如果你之前撤销过产生了commi id，那么也会计算在内的。

如果使用 revert 撤销的不是最近一次提交，那么一定会有代码冲突，需要你合并代码，合并代码只需要把当前的代码全部去掉，保留之前版本的代码就可以了.
```