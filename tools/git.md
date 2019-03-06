## 笔记整理自：廖雪峰的官方网站
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
## Git是什么
* 分布式版本控制系统（对比集中式的版本控制系统，集中式需要联网，而分布式每台电脑都是服务器）
* 作者是Linus
* Git跟踪并管理的是修改，而非文件
* 下载地址：https://git-scm.com/downloads
* 下载地址：https://pan.baidu.com/s/1kU5OCOB?errno=0&errmsg=Auth%20Login%20Sucess&&bduss=&ssnerror=0&traceid=#list/path=%2Fpub%2Fgit

### 常见命令

#### 初始化配置
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

##### 创建目录

$ mkdir learngit
$ cd learngit
$ pwd

pwd命令用于显示当前目录
Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。

##### 变为仓库
$ git init

不要使用Windows自带的记事本编辑任何文本文件

##### 添加文件到Git仓库

git add <file>：添加文件
git commit -m <message>：提交

##### 查看状态

git status：掌握工作区的状态
git diff <file>：查看修改内容

##### 版本切换

HEAD指向的是当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
git reset --hard commit_id：切到某版本（本地分支的版本，如果已经推送到远程库就不适用了）
git log：查看提交历史（以便确定要回退到哪个版本）
git log --pretty=oneline：查看简要提交历史
git reflog：查看命令历史

### 工作区和暂存区

#### 工作区
本地的目录

#### 版本库
.git就是Git的版本库

版本库中存在
* 称为stage（或者叫index）的暂存区
* 我们的主分支master，以及指向master的指针HEAD
* 其他

git add的效果就是将文件修改添加到暂存区

git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支

每次修改，如果不用git add到暂存区，那就不会加入到commit中。

git checkout -- <file>：撤销工作区的修改，使文件恢复到上一次git add或git commit时的状态

git reset HEAD <file>：将暂存区的修改撤销掉（工作区不变）

git rm <file>：将删除操作提交到暂存区（跟git add对应）

### 远程仓库

#### 本地仓库跟GitHub仓库关联
* ssh-keygen -t rsa -C "youremail@example.com"：创建SSH Key，如果用户主目录下已经有了.ssh目录，则不需要此操作
* 登录GitHub，打开“Account settings” - “SSH Keys” 页面 - 点击“Add SSH Key”，填写任意Title，在Key文本框粘贴 用户主目录/.ssh/id_rsa.pub文件的内容 - 点击“Add Key”
* 在本地仓库目录下，执行“git remote add origin git@github.com:账户名/项目名.git”
* git push -u origin master：把本地库的所有内容推送到远程库上

以后每次可以执行“git push origin master”来推送远程库

一个Key对应一个本地仓库

#### 从远程库克隆到本地库
git clone git@github.com:michaelliao/gitskills.git：会在当前目录下自动克隆项目的根目录，所以在工作目录执行此命令即可