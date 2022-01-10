# Git - 学习小笔记

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



## 推

**git push** 命用于从将本地的分支版本上传到远程并合并。

命令格式如下：

```
git push <远程主机名> <本地分支名>:<远程分支名>
```

如果本地分支名与远程分支名相同，则可以省略冒号：

```
git push <远程主机名> <本地分支名>
```

## 打tag

**默认标签是打在最新提交的commit上的。**

1. 在控制台打印出当前仓库的所有标签：`git tag`
2. 搜索符合模式的标签：`git tag -l 'v0.0.*'`

3. 创建附注标签：`git tag -a v0.0.1 -m "v0.0.1发布"`

4. 删除标签：`git tag -d v0.0.1`

5. 查看标签的版本信息：`git show v0.0.1`

6. 指向打v0.0.2标签时的代码状态：`git checkout v0.0.2`

7. 将v0.0.1标签提交到git服务器：`git push origin v0.0.1`

8. 将本地所有标签一次性提交到git服务器：`git push origin –tags`

-- 以上都是在当前的版本打的tag --

如果忘记了在之前版本打的tag，可以`get tag v0.9 commitid`

再用 `git tag` 可以查看标签

 **注意**，标签不是按时间顺序列出，而是按字母排序的。可以用`git show <tagname>`查看标签信息



## Git分支操作

- **Git删除远程分支**
  `git push origin --delete [branch_name]`

- **删除本地分支区:**
  `git branch -d` 会在删除前检查merge状态（其与上游分支或者与head）。
  `git branch -D` 是 `git branch --delete --force` 的简写，它会直接删除。
- **git查看分支：**
  查看本地分支 `git branch`
  查看远程分支 `git branch -r`
  查看本地和远程分支 `git branch -a`
- **git删除分支：**
  删除本地分支 `git branch -d 本地分支名`
  删除远程分支 `git push origin --delete 远程分支名`
  推送空分支到远程（删除远程分支另一种实现）`git push origin:远程分支`

当我们删除远程分支后执行`git branch -a`，本地却依然能看到远程分支

这个时候我们只需要执行 `git remote prune 自定义名Git库`

清理一下就可以了，然后再次执行 `git branch -a`，就看不到啦