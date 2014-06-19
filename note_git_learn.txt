- 初始化一个版本库，使用git init 命令
- 添加文件到git仓库，分两步 
	1. 用git add命令，可以反复多次添加到暂存区 
	2. 用git commit 命令完成提交
- 要随时掌握工作区的状态，使用git status 命令
- 如果git status 告诉你文件被修改过，可以使用git diff 查看修改内容
- 修正提交，如果你提交时候注释写错了，可以用git commit --amend -m“新的注释“来进行修正

- HEAD 指向的版本就是当前版本，因此git允许我们在版本的历史之间穿梭，使用命令 git reset --hard commit_id
- 穿梭前，可以用git Log 查看提交历史，以确定需要退回哪个版本
- 要重返未来，用git reflog查看命令历史，以确定要回到未来的那个版本

- 当你想丢弃工作区的修改时，可以用 git checkout -- file_name 
- 当时不小心把错误文件添加到暂存区时，分两步，先用git reset HEAD file退回到工作区，然后再按上一条的方法操作
- 已经提交了不合适的修改到版本库时，想要撤销本次提交，用版本回退的方法，前提是还没推送到远程的仓库
- 命令git rm 用于删除一个文件，如果一个文件已经被提交到版本库，那么永远不用担心误删，但是只能恢复到最近一次提交后你修改的内容

- 要关联一个远程库，使用命令 git remote add origin git@server-name:path/repo-name.git,命令格式是：git remote add [shortname] [url]
- 关联后，使用命令git push origin master 第一次推送 master 分支的所有内容
- 此后每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改，实际格式是git push [remote-name] [branch-name]
- origin 为这个分支的名字，如果要修改某个远程仓库的名字，可以用git remote rename oldname newname这个命令
- 要删除对应的远程仓库，可以运行git remote rm repo_name这个命令

- 从远程库克隆，首先需要知道仓库的地址，然后使用git clone 命令克隆
- git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快

- git 鼓励大量使用分支
- 查看分支:git branch
- 创建分支:git branch branch_name
- 切换分支:git checkout branch_name
- 创建+切换分支:git chockout -b branch_name
- 合并某分支到当前分支:git merge branch_name
- 删除分支:git branch -d branch_name

- 当git无法自动合并分支时，就必须先解决冲突。然后再提交合并。
- 用git log --graph 命令可以看到分支合并图(用q退出）

- 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出曾经做过的合并，而fast foward模式合并就看不出曾经做过合并

- 修复bug时，会通过创建新的bug分支进行修复，然后合并，最后删除
- 当手头工作没有完成时，先把工作现场git stash 保存，修复后在 git stash pop 回到工作现场
- 可以多次git stash，后用git stash list 来查看，然后恢复指定的stash 用命令 git stash apply stash@{0}

- 开发一个新的feature时最好新建一个分支
- 如果要丢弃一个没有合并过得分支，可以通过git branch -D name 强行删除

- 查看远程库的信息，使用git remote -v
- 本地新建的分支如果不推送到远程，对其他人是不可见的
- 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull 抓取远程的新提交
- 在本地创建和远程分支对应的分支，使用git branch -b branch-name origin/branch-name ，本地和远程名称最好一致
- 建立本地分支和远程分支的关联，使用git branch --set-upstreambranch-name origin/branch-name
- 从远程抓取分支，使用git pull，如果有冲突，要先处理冲突

- 命令git tag name 用于新建一个标签，默然为HEAD，也可以指定一个commit id
- -a tagname -m“balabala”可以指定标签信息
- -s tagname -m“balabala”可以用PGP签名标签
- 命令git tag可以查看所有标签
- git show tagname可以查看标签详细信息

- git push origin tagname 可以推送一个本地标签
- git push origin --tag可以推送本地所有未推送的标签
- git tag -d tagname可以删除一个本地标签
- git push origin ：refs/tags/tagname 可以删除一个远程标签

- 在github上可以任意fork开源仓库
- 自己拥有fork后仓库的读写权限
- 可以推送pull request给官方仓库来贡献代码

- 忽略特殊文件，需要编写.gitignore
- .gitignore要放到版本库里，并且可以对.gitignore做版本管理

- 给git 配置好别名，就可以在输入命令时候偷个懒。命令是 git config --  global alias.你要的别名 原来的名称
- 在你的$HOME目录下可以找到一个叫做.gitconfig的文件，可以修改已经配置的别名