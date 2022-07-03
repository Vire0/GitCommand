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

9.回退到任意版本

`git reset --hard commit_id`

10.回退到上一个版本

`git reset --hard HEAD^`

### 远程代码版本管理

1.申请远端仓库链接

- Https链接 ：`https://github.com/Vire0/GitCommand.git`

2.本地仓库和远端仓库进行关联

`git remote add origin https://github.com/Vire0/GitCommand.git`

3.将本地仓库分支推送到远端

`git push origin master`

在第一次push中，要求输入用户名和密码，密码无回显

4.创建分支/删除分支/查看分支/切换分支

- 创建分支

`git checkout -b dev`

`dev`是分支名，常用的还有`feature`

- 删除分支

`git branch -d dev`

`git push origin --delete dev` 删除远端分支

- 查看分支

`git branch -a` 查看所有分支

- 切换分支

`git checkout dev`

5.回退远端的代码版本(替换本地改动)

`git fetch origin`

`git reset --hard origin/master`

### 打标签与发布

1.标签

为软件发布创建标签

`git tag 1.0.0 <ID %10d>`

将标签推送到远端仓库，直接推送即可，无需提交

`git push origin master --tags`
