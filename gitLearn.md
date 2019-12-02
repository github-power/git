# Git 

## Learn

### tips



- 初始化 git init 
- 添加文件到缓存区 git add 
- 提交到本地仓库 git commit -m "版本编号" 

- 查看仓库中文件和本地文件的区别 git diﬀ head -- "文件路径" 
- 撤销对某个文件的修改 git checkout -- "文件路径" 
- 如果修改后还没有被添加到缓存区，撤销修改就回到和仓库一模一样的状态 如果已经添加了，撤回到缓存区的状态 撤销添加到的缓存区，即git add错了 git reset head "文件路径" 
- 从仓库中删除文件（也会在本地删除） git rm "文件路径" 
- 退回到版本库的某个版本（git log     查询 提交的id） git reset --hard commit_id 
- 添加远程仓库 git remote add origin 
- 将本地仓库推送至远程仓库 git push origin master
- 第一次推送 git push -u origin master 
- 从远程仓库拉下来 git pull origin master
- 创建分支  git branch "分支名" 
- 切换分支 git checkout "分支名" 
- 查看当前分支  git branch
- 合并其他分支到当前分支  git merge  "分支名" 
- 删除分支  git banch -d "分支名" 
- 解决冲突

`git reflog`用来记录你的每一次命令

提交到缓存区

``` git
git add 文件名带扩展名
```

从缓存区添加到本地仓库

``` git
git commit -m"版本号随便写"
```

```
 git status -sb
```

```cmd



```



* `git dif`f //看暂存前后的变化
* 已暂存的将要添加到下次提交里的内容，可以用 `git diff --cached`	  Git 1.6.1 及更高版本还允许使用 `git diff --staged`，效果是相同的，但更好记些。
* 给 `git commit` 加上 `-a` 选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 `git add` 步骤
* 

查看历史纪录

```cmd
$ git log
$ git log --pretty=oneline//一行展示
$ git log --graph --pretty=oneline --abbrev-commit//查看分支合并情况
```







 版本回退

```cmd
$ git reset --hard HEAD^//回退到上一个版本
$ git reset --hard commit_id//回退到指定版本
$ git reset HEAD <file> //把暂存区的文件文件，从暂存区删除，工作区不改变
$ git checkout -- readme.txt//在文件提交到暂存区后，回退指定文件到与仓库同版本

```

``` cmd
$ git rm test.txt// 从版本库删除文件//小提示：先手动删除文件，然后使用git rm <file>和git add<file>效果是一样的。

注意：从来没有被添加到版本库就被删除的文件，是无法恢复的！
```

克隆

```cmd
$ git clone git@github.com:michaelliao/gitskills.git
```



```cmd
$ git rebase//把本地未push的分叉提交历史整理成直线；//存疑
```



### 远程

[<https://www.liaoxuefeng.com/wiki/896043488029600/896954117292416>](<https://www.liaoxuefeng.com/wiki/896043488029600/896954117292416>)

```cmd
-- 第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
$ ssh-keygen -t rsa -C "youremail@example.com"
--登陆GitHub，打开“Account settings”，“SSH Keys”页面：见上文链接

$ git remote//查看本地远程仓库信息
$ git remote -v//查看详细信息
$ git remote show origin
$ git remote rename pre filal
$ git remote rm paul
$ git push origin master// 把本地的master分支推到origin远程仓库

```

<https://www.liaoxuefeng.com/wiki/896043488029600/900375748016320>

现在，你的小伙伴要在`dev`分支上开发，就必须创建远程`origin`的`dev`分支到本地，于是他用这个命令创建本地`dev`分支：

```
$ git checkout -b dev origin/dev
```

现在，他就可以在`dev`上继续修改，然后，时不时地把`dev`分支`push`到远程：

### 分支

```cmd
$  git branch//查看分支
$ git checkout -b develop//创建并切换到develop分支
$ git checkout master //切换到主分支
$ git merge develop//将develop分支，合并到master分支//这里有时需要手动出路冲突
$ git branch -d develop//删除develop分支//一般我们不删除看法分支

--no-ff参数，表示禁用Fast forward
$ git merge --no-ff -m "merge with no-ff" develop


$ git branch -D <name> //强行删除一个没有被提交过的分支(设计关键信息)

```

切换分支这个动作，用`switch`更科学。

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`或者`git switch <name>`

创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`

如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除。

```cmd
git config --global alias.st status


git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
//设置别名
```

## Use

```cmd
$ git init //初始化本地仓库
$ git status //查看仓库(工作区，暂存区，仓库)状态
$ git add index.html//添加index.html文件到暂存区
$ git commit -m "添加index.html"//将暂存区的文件提交到仓库，并添加提交信息(注释)
已经配置过不会有一下提示，及设置→→→→→→→→→↓
-- Please tell me who you are.
$ git config --global user.name "Your Name"//全局配置用户名
$ git config --global user.email "email@example.com"//全局配置用户邮箱
→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→↑
$ git commit -m "配置用户名，邮箱后提交"
$ git log //查看提交日志(提交历史纪录)



//前提GitHub 配置 ssh(见上文)，且创建项目仓库
$ git remote add origin git@github.com:michaelliao/learngit.git//添加远程仓库
$ git push -u origin master//第一次提交到远程仓库
$ git push origin master//第一次以后提交到远程仓库

ssh警告→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→↓
当你第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告：
-- The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
-- RSA key fingerprint is xx.xx.xx.xx.xx.
-- Are you sure you want to continue connecting (yes/no)?

这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。
Git会输出一个警告，告诉你已经把GitHub的Key添加到本机的一个信任列表里了：
-- Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→→↑
```



```cmd
$ git clone git@github.com:michaelliao/gitskills.git//克隆远程仓库
$ git checkout -b develop //切换到develop分支//没有就创建

```



