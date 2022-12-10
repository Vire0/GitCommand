# git的基本使用技巧

### 本地代码版本管理

1.初始化用户名和邮箱账户

`git config --global user.name "zhongdao.li"`

`git config --global user.email "vire0@outlook.com"`

2.初始化版本管理工作目录

`git init`

3.查看当前工作目录状态

`git status`

4.忽略不更新的文件

新建`.gitignore`文件，在文件中写入忽略上传的文件

> Test/
>
> *bin

5.添加当前目录下待管理的文件

`git add .`      /      `git add *`

6.查看当前工作目录状态

`git status`

7.提交到本地进行git版本管理

`git commit -m "first commit"`

8.查看提交的日志

`git log`

`git log --pretty=oneline`

`git log --oneline`

`git reflog` 表示回退需要的步数

9.回退到任意版本

`git reset --hard <commit_id>`

- --hard: 本地库的指针移动的同时，重置暂存区，重置工作区

`git reset --mixed <commit_id>`

- --mixed: 本地库的指针移动的同时，重置暂存区，但是工作区不动

`git reset --soft <commit_id>`

- --soft: 本地库的指针移动，暂存区和工作区都不动

10.将提交回退到上一个版本

`git reset --soft HEAD^`  或 `git reset --soft HEAD~1`

### 远程代码版本管理

1.申请远端仓库链接

- Https链接 ：`https://github.com/Vire0/GitCommand.git`

2.本地仓库和远端仓库进行关联

`git remote add origin https://github.com/Vire0/GitCommand.git`

3.将本地仓库分支推送到远端

`git push origin master`

`git push -u origin master`

在第一次push中，要求输入用户名和密码，密码无回显

4.创建分支/删除分支/查看分支/切换分支

- 创建分支

`git checkout -b dev`

`dev`是分支名，常用的还有`feature`

- 删除分支

`git branch -d dev`

`git push origin --delete dev` 删除远端分支

- 查看分支

`git branch` 查看分支

`git branch -a` 查看所有分支

`git branch -v` 查看分支信息，带提交信息

- 切换分支

`git checkout dev`

5.回退远端的代码版本(替换本地改动)

`git fetch origin`

`git reset --hard origin/master`

### 打标签与发布

1.标签

为软件发布创建标签

指定版本打标签：`git tag V0.0.9 -m "bate version 0.0.9" <ID %10d>`

当前版本打标签：`git tag -a V1.0.0 -m "release version 1.0.0"`

将标签推送到远端仓库，直接推送即可，无需提交

`git push origin master --tags`

2.删除标签

- 删除本地标签

`git tag -d V1.0.0`

- 删除远端标签

`git push origin :refs/tags/V1.0.0`



# Github常用工作流程

1.从远端仓库拉取项目工程

`git clone https://github.com/Vire0/GitCommand.git`

2.建立个人 branch

`git checkout -b my-branch`

3.查看硬盘和git暂存区之间的变化

`git diff` 或 `git stauts`

4.将硬盘中的改动增加到暂存区

`git add <changed_file>` 

5.将暂存区中的修改提交到本地git仓库

`git commit`

6.将本地git仓库的提交push到远端仓库

`git push origin my-branch`

7.切换本地到master branch下

`git checkout master`

8.同步远端master更新

`git pull origin master`

9.再回到个人branch

`git checkout my-branch`

10.同步master的改变

`git rebase master`

11.同步改变后提交到远端个人分支

`git push -f origin my-branch`



# Gerrit常用工作流

1.从远端仓库拉取项目工程

`git clone https://github.com/Vire0/GitCommand.git`

2.查看所有项目分支

`git branch -a`

3.切换到自己负责项目的分支

`git checkout <branch_name>`

4.查看当前分支的提交记录

`git log`

5.产看当前分支的所有变化或状态

`git diff` 或 `git stauts`

6.更新远端项目工程

- `git stash`  -暂存当前状态
- `git pull --rebase`  -把远端的更新同步到本地改变
- `git stash pop` -把暂存当前状态合并到最新远端代码的本地git中

7.将硬盘中的改动增加到暂存区

`git add <changed_file>` 

8.将暂存区中的修改提交到本地git仓库

`git commit`

9.提交到Gerrit后审核合并

`git push origin :refs/<branch_name>`



# git撤销修改技巧

1.撤销掉本地磁盘的修改

`git checkout <changed_file>` 或 `git restore <changed_file>`

2.修改从暂存区移除，但是保留本地磁盘的修改

`git reset <changed_file>` 或 `git restore --staged <changed_file>`

3.撤销暂存区和本地磁盘的修改

`git checkout HEAD <changed_file>`

4.撤销本地git中的提交回退到暂存区

`git reset --soft HEAD^` = `git reset --soft HEAD~1`

5.同时撤销本地git中的提交和暂存区状态的add回退到本地磁盘修改状态

`git reset HEAD~1` = `git reset --mixed HEAD~1`

6.完整恢复到初始状态，本地磁盘的修改也删除

`git reset --hard HEAD~1`  > 不建议使用

7.通过增加一次提交来回退到上一次的状态 - 好处是公有分支回退的时候较好

`git revert HEAD`

