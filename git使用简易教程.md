#### 工作流
本地仓库由git维护。
1.工作目录，持有实际文件
2.缓存区(Index)， 临时保存改动
3.HEAD，指向最近一次提交后的结果
#### 添加与提交
1.计划改动，相当于把文件添加到缓存区，命令如下
```
git add git使用简易教程.md
git add *
```
这是git基本工作流程的第一步。

2.使用如下命令以实际提交改动：
```
git commit -m '代码提交信息'
```
现在，改动已经提交到了 HEAD，**但是还没有到远端仓库**
#### 推送改动
改动已经在本地仓库的HEAD了。之后就可以将改动提交到远端仓库。
```
git push origin master
```
可以把master换成你想要推送的分支

如果还没有克隆现有仓库，并欲将你的仓库链接到某个远程服务器，你可以使用如下命令添加：
```
git remote add origin <server> //这一步只是把origin和远端仓库建立联系
git push origin master
```
如此能够将你的改动推送到所添加的服务器上去了。
#### 分支
创建分支
```
git branch feature_x
```
切换分支
```
git checkout feature_x
```
上面两条可以合并为
```
git checkout -b feature_x
```
切换回主分支
```
git checkout master
```
再把新建的分支删掉
```
git branch -d feature_x
```
除非将分支推送到远端仓库，不然该分支就是不为他人所见的：
```
git push origin <branch>
```
#### 更新与合并
```
git pull
git merge <branch>
git add <filename>
git diff <source_branch> <target_branch>
```
#### 标签
```
git tag 1.0.0 1b2e1d63
```
其中1b2e1d63是想要标记的提交ID的前几位字符，使用如下命令可以获得提交ID
```
git log
```
#### 替换本地改动
可以使用如下命令替换掉本地改动
```
git checkout -- <filename>
```
此命令会使用HEAD中的最新内容替换掉你的工作目录中的文件。已经添加到缓存区的改动，以及新文件，都不受影响。
加入要丢弃所有的本地改动与提交，可以到服务器上获取最新的版本，并将本地主分支指向到它
```
git fetch origin
git reset --hard origin/master
```
#### 有用的贴士
内建的图形化git,gitk]
```
gitk
```
彩色的git输出
```
git config color.ui true)
```
显示历史记录时，只显示一行注释信息
```
git config format.pretty oneline
```
交互地添加文件至缓存区
git add -i