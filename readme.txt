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