git add .    (git add -A)  //添加    （add . 不会把删掉的内容从仓库删掉）
git commit -m "2020-06-16-01"  //保存添加
git log 查看commit
q 退出log

git add .    (git add -A)  //添加    （add . 不会把删掉的内容从仓库删掉）
git commit -m "2020-06-16-01"  //保存添加
git log 查看commit
q 退出log
回退命令：
$ git reset --hard HEAD^         回退到上个版本
$ git reset --hard HEAD~3        回退到前3次提交之前，以此类推，回退到n次提交之前
$ git reset --hard commit_id     退到/进到 指定commit的sha码


强推到远程：
git commit 到旧的后  新commit消失问题
git commit到旧的版本后 git log不出来最新的commit id  
可以 git show <commit id> 显示提交的具体信息
git reflog #可以看到丢失的commit id
git help
git status
git reset HEAD
git show 查看现在在哪
https://www.jianshu.com/p/8b4c95677ee0
git reset  --hard 哈希值的前半部分 //回退 强制回退 会删掉内容

git push origin master  //上传

git pull origin master  //下载
强行覆盖
git fetch --all 
git reset --hard origin/master


新文件关联到仓库
打开文件 Git bash
git init
git add .
git commit -m "sss"
关联仓库
git remote add origin https://gitee.com/muzappar_murat/hezuoxiedexiaochengxu.git
git push -u origin master
成功了


git tag xxxxx
git checkout  xxxxx就可以回到那个 tag
git checkout master  又可以回去

git tag　　//查看tag
git tag test_tag c809ddbf83939a89659e51dc2a5fe183af384233　　　//在某个commit 上打tag
git tag
git push origin test_tag　　//!!!本地tag推送到线上
git tag -d test_tag　　　　//本地删除tag
git push origin :refs/tags/test_tag　　//本地tag删除了，再执行该句，删除线上tag

首先说一下作用：Git 中的tag指向一次commit的id，通常用来给开发分支做一个标记，如标记一个版本号。

下面就说一下具体的用法：
1.添加标签： git tag -a version -m "note"
注解：git tag 是打标签的命令，-a 是添加标签，其后要跟新标签号，-m 及后面的字符串是对该标签的注释。
2.提交标签到远程仓库
：git push origin -tags注解：就像git push origin master 把本地修改提交到远程仓库一样，-tags可以把本地的打的标签全部提交到远程仓库。3.删除标签：git tag -d

version注解：-d 表示删除，后面跟要删除的tag名字4.删除远程标签：git push origin :refs/tags/version注解：就像git push origin :branch_1 可以删除远程仓库的分支branch_1一样， 冒号前为空表示删除远程仓库的tag。5.查看标签：git tag或者git
 tag -l


)带有说明的标签，用-a指定标签名，-m指定说明文字：
$ git tag -a v0.1 -m "version 1.0" 88d434eb9992fa7502ec246ecfb89aef19f16873
5)删除标签
MacBook-Pro:API_TestCase$ git tag -d testtag
Deleted tag 'testtag' (was 88d434e)
6) 推送某个标签到远程，使用命令git push origin <tagname>：
$ git push origin testtag

7) 一次性推送全部尚未推送到远程的本地标签
$ git push origin --tags
注意，标签不是按时间顺序列出，而是按字母排序的。可以用git show <tagname>查看标签信息：



分支
git checkout master //先切换到主干上
git merge bugfix    //再合并修改bug的分支
