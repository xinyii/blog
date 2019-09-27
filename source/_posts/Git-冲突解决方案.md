---
title: Git 冲突解决方案
date: 2017-12-31 19:40:58
categories:
  - Git
tags:
  - Git
---

# 说明

在团队协作使用Git时，遇到的冲突通常为两种，分别为：

- `git pull` 拉取冲突，本地修改的文件与远程仓库待拉取的文件内容冲突。
- `git push` 推送冲突，本地仓库提交的版本基于远程仓库的旧版本。

<!-- more -->

# 拉取冲突

```sh
$ git pull
error: Your local changes to 'xxx/xxx' would be overwritten by merge.  Aborting.
Please, commit your changes or stash them before you can merge.
```

遇到这种情况，你可以：

## Checkout 丢弃

丢弃本地中发生冲突的修改，然后再拉取。

```sh
$ git reset HEAD <file> # 如果文件未add到暂存区，可以不执行该操作
$ git checkout <file> # 丢弃修改
$ git pull
```

## Stash 贮藏

贮藏修改，然后拉取，接着恢复贮藏，解决冲突。

```sh
$ git stash # 开始贮藏修改
$ git stash list # 查看贮藏列表
$ git pull
$ git stash pop # 恢复贮藏修改，然后会产生如下日志，根据日志提示解决冲突
Auto-merging xxx/xxx
CONFLICT (content): Merge conflict in xxx/xxx
```

编辑冲突文件，会看到如下内容：

```
<<<<<<< Updated upstream
  var a = 1
=======
  var a = 2
>>>>>>> Stashed changes
```

在`<<<<<<< Updated upstream`和`=======`之间的是拉取下来的内容；
在`=======`和`>>>>>>> Stashed changes`之间的是本地修改的内容。
根据需要丢弃无用内容，保留有用的内容。

# 推送冲突

同一个分支上有多个人维护时，建议在`commit`前进行`pull`操作。
如果未`pull`就进行`commit、push`操作，很有可能造成版本冲突，从而产生不必要的合并提交。

```sh
$ git push
To git@github.com:xxx/xxx.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:xxx/xxx.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

这种情况是因为远程仓库的分支比本地的新，有以下方法解决这种情况：

## Merge 合并

在推送前进行pull操作：

**无内容冲突**

```sh
$ git pull # 在push前执行pull，如果没有冲突，git会自动merge
$ git push
```

**有内容冲突**

```sh
$ git pull # pull后发生冲突
Auto-merging xxx/xxx
CONFLICT (content): Merge conflict in xxx/xxx
$ git add <file> # 在手动解决冲突内容后添加该修改到暂存区
$ git commit # 提交冲突修改
$ git push
```

## Rebase 变基

变基操作可以省掉一次合并提交，使项目历史变得更加简洁：

**无内容冲突**

```sh
$ git fetch # 同步仓库
$ git rebase origin/master # 或 git pull --rebase
$ git push
```

**有内容冲突**

```sh
$ git fetch # 同步仓库
$ git rebase origin/master # 或 git pull --rebase
$ git add <file> # 在手动解决冲突内容后添加该修改到暂存区
$ git rebase --continue # 无需commit，继续变基
$ git push
```

# 参考

[代码合并：Merge、Rebase 的选择](https://github.com/geeeeeeeeek/git-recipes/wiki/5.1-%E4%BB%A3%E7%A0%81%E5%90%88%E5%B9%B6%EF%BC%9AMerge%E3%80%81Rebase-%E7%9A%84%E9%80%89%E6%8B%A9)