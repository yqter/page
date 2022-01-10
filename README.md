# Git教程

## 撤销

撤销修改`git checkout -- file`有两种情况

* 修改这个文件之后，还没有提交到缓存区（`git add .`），
  这个文件就可以回退到你修改之前的样子。
  
* 这个文件的修改已经添加到了缓存区，你又对这个文件本身进行了修改，
  这时，回退就会变成你提交到缓存区里的样子

`git reset --soft`：撤销上一次commit，回到git add.的状态

`git reset --mixed`：撤销上一次commit和add，回到本地编辑的状态

`git reset --hard`：撤销上一次对文件的所有修改

## 关联远端数据库

要关联一个远程库，使用命令

`git remote add origin URL`；

关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

关联后，使用命令`git push origin master`推送

