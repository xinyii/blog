---
title: Git 常用命令
date: 2016-10-26 10:47:51
categories:
  - Git
tags: 
  - Git
---

#### 开始工作

- 初始化仓库 `git init`
- 克隆远程仓库 `git clone <repository>`
- 添加远程仓库 `git remote add origin <repository>`

<!-- more -->

---

#### 文件操作

- 暂存文件 `git add [<pathspec>…​]`
- 取消暂存文件 `git rm --cached <file>…​`
- 移动暂存文件 `git mv <file1> <file2>`
- 回滚文件 `git reset <version> <file>`

---

#### 版本信息

- 查看状态 `git status [<pathspec>…​]`
- 查看最近指定次数版本日志 `git log -<limit>`
- 查看指定文件日志 `git log [<file>...]`
- 查看指定分支日志 `git log <branch>`
- 查看详情 `git show <object>…​`

---

#### 仓库操作

- 提交更新 `git commit -m <message>`
- 修正提交 `git commit --amend`
- 合并提交 `git merge`
- 查看本地分支 `git branch`
- 查看远程分支 `git branch -a`
- 创建分支 `git branch <branch>`
- 删除分支 `git branch -d <branch>`
- 强制删除分支 `git branch -D <branch>`
- 删除远程分支 `git push origin :<branch>`
- 切换分支 `git checkout <branch>`
- 版本比较 `git diff`

---

#### 多人合作

- 拉取 `git pull`
- 推送 `git push`
- 下载 `git fetch`