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

- Test/

- *bin

5.添加当前目录下待管理的文件

`git add .`

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
