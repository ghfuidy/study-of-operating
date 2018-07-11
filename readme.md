-----------
the use of git(first try)
-----------

在网络上搜索教程将本地git仓库与github仓库关联
.git文件中可以看见远程仓库

----------
文件上传过程
git add xxx
git commit -m""
git push #推送到github上
（第一次推送过程
git push -u origin master    失败  报错：
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

-->修改用户名
git config --global user.email github推荐文件名
-->修改
git commit --amend --reset-author

git push    失败：
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use
git push --set-upstream origin master

~~~~~~~~~~~~
然后考虑采用强制措施git push -u origin master -f（不考虑云端与本地的冲突）
成功
~~~~~~~~~~~~
）

思考题：云端与本地文件完全不同，且属于第一次上传，如何将本地文件加入云端
（采用先下载在上传的方式
push前先将远程repository修改pull下来

$ git pull origin master

$ git push -u origin master

失败
）


若不想merge远程和本地修改，可以先创建新的分支：

$ git branch [first-practice]

然后push

$ git push -u origin [first-practice]

失败    原因:
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (9/9), 694 bytes | 347.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0)
remote: error: GH007: Your push would publish a private email address.
remote: You can make your email public or disable this protection by visiting:
remote: http://github.com/settings/emails
To https://github.com/ghfuidy/study-of-operating.git
 ! [remote rejected] first-practice -> first-practice (push declined due to email privacy restrictions)
error: failed to push some refs to 'https://github.com/ghfuidy/study-of-operating.git'