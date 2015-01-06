title: git学习总结
date: 2014-12-29 17:15:37
categories: Tool
---
## 基本命令

* __安装git__
  * 下载安装git
  * 配置username 和 emai
    * git config --global user.name "Your Name"
    * git config --global user.email "email@example.com"
    * 注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

* __创建和初始化版本库__
  * mkdir learngit
  * git init

* __添加文件到仓库__
  * git add readme.txt   [添加到暂存区]

* __提交文件到仓库__
  * git commit -m "wrote a readme file"

* __查看仓库当前状态__
  * git status

* __查看本地文件修改内容__
  * git diff readme.txt   [比对工作区和缓存去的不同]
  * git diff HEAD -- readme.txt   [查看工作区和版本库里面最新版本的区别]

* __查看提交日志__
  * git log
  * git log --pretty=oneline  [精简日志信息]

* __回退到版本__
  * git reset --hard HEAD^   [回退到上一版本]
  * git reset --hard HEAD^^   [回退到上二版本]
  * git reset --hard HEAD~10   [回退到上10个版本]

* __回到未来的某个版本__
  * git reset --hard 3628164 [只要知道未来的commit id就行]

* __查看历史命令__
  * git reflog  [可以用来找回未来的某个commit id, 用来回退]、

* __撤销工作去的修改[或恢复到最新版本]__
  * git checkout -- readme.txt

* __删除文件__
  * git rm test.txt  [从版本库中删除]
  * git commit test.txt

## 远程仓库(已githup为例)

* __创建SSH Key__
  * ssh-keygen -t rsa -C "youremail@example.com"
    * 在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥。

  * 在Github上添加SSH Key
    * 登陆GitHub，打开“Account settings”，“SSH Keys”页面
    * 然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容


* __添加远程仓库__
  * git remote add origin git@github.com:zq210wl/learngit.git [添加远程仓库origin]

* __把本地库的内容推送到远程库上__
  * git push -u origin master  [第一次提交分支时]
    * 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送到远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
  * git push origin master  [把当前本地库内容推动到远程origin库下的master分支]
  * git push  [推送当前所在分支到远程库，如果当前是在dev分支，那么会提交到dev上]

* __克隆远程分支到本地__
  * git clone git@github.com:zq210wl/learngit.git destinationDir  [目标文件夹可选]
    * 默认从远程clone的仓库，在本地只有主分支，如果要用其他分支就必须自己创建，然后建立对应联系
    * 当你从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且，远程仓库的默认名称是origin。

* __创建分支__
  * git branch dev  [在当前分支上创建dev分支]

* __切换分支__
  * git checkout dev

* __创建并切换到分支__
  * git checkout -b dev  [加上-b参数表示创建并切换]

* __查看分支__
  * git branch

* __查看远程仓库信息__
  * git remote
  * git remote -v  [显示更详细的信息]

* __合并分支__
  * git merge dev  [合并某分支到当前分支，如果要合并到master分支，就必须切换到master分支下]   [Fast forward模式]
  * git merge --no-ff -m "merge with no-ff" dev  [--no-ff]
    * 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

* __删除分支__
  * git branch -d dev
  * git branch -D dev  [强行删除还没有合并的分支]
  * git push origin :dev  [删除远程dev分支]

* __解决冲突__
  * Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容
  * 需要手动解决冲突

* __查看分支合并图__
  * git log --graph --pretty=oneline --abbrev-commit
  * git log --graph

* __设置本地分支和远程分支的联系__
  * git branch --set-upstream dev origin/dev
    * 如果远程已经有一个dev分支，而你又在本地创建了自己的dev分支，如果要从远程dev分支上更新文件就需要建立联系


* __从远程抓取分支__
  * git pull
    * 如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建


* __注意：__
  * 一个仓库只能关联一个远程库，所以get remote 只会有一个库
  * 一个库可以有多个分支
  * 本地分支和远程分支的区别？
    * 在本地创建的分支就是本地分支;   git branch
    * 如果把本地创建的分支push到远程仓库，那么在远程仓库上就存在了这个分支，也就叫做远程分支;  git remote
    * 开发两种有一些分支是不需要提交到远程仓库，只需要在本地合并到主分支，然后再push到远程主分支

  * 什么时候用分支？
    * 一般是在开发一个新feature时，先创建一个分支, 在这个分支完成此feature然后再merge到master分支，合并完后，如果此feature已经完成，可以删除此分支，如果有另一个feature的话，可以再重新常见分支，以此类推

* __分支策略：__
  * ![](/imgs/git_branch.png)

## 高级使用

* __创建标签__
* __忽略某些文件__
  * 在库的根目录下创建 .gitignore 文件，并提交次文件
  * 格式
    * \# 注释符号
    * 每行写一个要忽略的文件或目录
    * 示例：
      * build.xml
      * *.class
      * *.log
      * bin/
* __配置别名__
* __搭建Git服务器__

## 参考网址

  * Git cheat sheet
    * http://www.git-tower.com/blog/assets/2013-05-22-git-cheat-sheet/cheat-sheet-large01.png

  * Git official website
    * http://git-scm.com/

  * Git 中文教程
    * http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000





