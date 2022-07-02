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

解除三方验签`git config --global http.sslVerify false`

`git push origin master`

其中`origin`为远端仓库名，`master`为分支名，推送其他分支则修改分支名

在第一次push中，要求输入用户名和密码，密码无回显

4.创建分支/删除分支/查看分支/切换分支

- 创建分支

法一

`git checkout -b dev`

`dev`是分支名，常用的还有`feature`

法二

`git branch dev`

- 删除分支

`git branch -d dev`

- 查看分支

`git branch -a` 查看所有分支

- 切换分支

`git checkout dev`

5.更新与合并

- 拉取远端分支的更新

`git pull origin master`

> git pull 的含义就是获取（git fetch）并 合并(merge)远端的改动

- 合并改动

`git merge dev`
