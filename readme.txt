这是git_test_git的说明文件
增加一行，测试git status
增加开源版本协议GPL

下面研究暂存区（stage）是怎么工作的，how stage work

文件修改后，        存在工作区
git add之后，       存到暂存区
git commit之后， 会提交给当前分支
=======================================

当file.txt文件修改保存后，发现保存错了，还没有git add。这时可以：
git checkout -- file.txt  //这个命令可以将工作区的修改撤回到最开始状态

当file.txt文件修改保存后，并且通过git add添加到暂存区后，发现保存错误。这时可以：
git reset HEAD file.txt    //通过这个命令撤销git add的操作，回退到上一个情况
git checkout -- file.txt   //将工作区的修改撤回到最开始状态
=======================================

git切换到之前的某一个修改状态
1.通过git log --pretty=oneline查看本分支现有修改保存情况
$ git log --pretty=oneline
8cc1787e148a5dd93877064685c8ace98568e893 (HEAD -> master) 增加LIENCE.txt 内部执行结果的说明
81b58e74c5fcfe8e138bd1a9828a4a6576179863 测试git暂存区(stage)是怎么工作的
ae29894e087a550c321a361d7c84c949955449f5 readme.txt增加版本信息
556b00d56e541ba8d8fef1cea60d7dbadae7691b readme.txt 增加一行用来测试git status
068fdeda5f8f8336d9a69f23a248d85fce57051b 增加readme文件
2.通过git reset --hard  ae29回退到“readme.txt增加版本信息”这次修改
或者通过git reset --hard HEAD^回退到上一个版本的修改

========================================
git切换到后面的某个状态，由于068fdeda5f8f8336d9a69f23a248d85fce57051b这个状态已经找不到，可以通过：
git reflog来查找提交的历史，查找结点。然后回退
*********************************************
git删除文件
在工作区删除某个文件后，git status
会提示文件已删除。
如果这个文件之前提交过，可以通过:
git checkout -- test.txt恢复这个文件。
如果确实要提交这个修改到暂存区
git rm test.txt //删除暂存区的文件，删除后暂存区也没有这个文件了，所以此时该文件已经无法回退了，但可以通过之前的版本回退恢复这个文件


******************************************
1.关联远程服务器
git remote add origin git@github.com.....
2.提交代码
git push -u origin master
============================
后面将代码提交到服务器，可以：
1.修改工作区文件
2.git add .
3.git commit -m "修改说明"
4.git push origin master
==============================
git创建分支dev
git branch -b dev
修改工作区...
git add .
git commit -m "注释"

































