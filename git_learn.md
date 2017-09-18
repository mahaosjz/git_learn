# 时光机穿梭
---
## 版本回退
1. `git log --pretty=oneline` 日志单行显示（当前版本保留的操作记录）
2. `git reflog`记录每一次命令（建库对版本的所有操作）
3. 版本修改并提交到版本库中（commit之后），HEAD表示当前版本，HEAD^为上一版本，网上100个版本则为HEAD~100
4. `git reset --hard HEAD^` 版本回退到上一版本
## 工作区和暂存区
1. `git diff` 是工作区和暂存区的比较
2. `git diff --cached` 暂存区和分支的比较
3. `git add`命令后，工作区的第一次修改放入暂存区，准备提交
4. `git commit`负责把暂存区的修改提交到版本库
## 管理修改
#### git跟踪管理的是修改，并不是文件
commit后，`git diff HEAD -- file`查看工作区和版本库最新版本的区别
## 撤销修改
1. `git checkout -- file` 丢弃工作区的修改，回到最近一次git commit或 git add的状态
+ file自修改后还没有放到暂存区，即没有git add 则回到版本库一模一样的状态
+ file已经添加到暂存区，又做了修改，则撤销修改就回到添加到暂存区的状态
#### 小结
1. 当改乱了工作区某个文件的内容，直接丢弃工作区的修改使用`git checkout -- file`
2. 修改了工作区并git add之后，则分两步，第一步：`git reset head file`,回到场景1，第二步根据场景一操作
3. 提交了不合适的修改到版本库，撤销本次提交，则参考‘版本回退’一节，前提是没有推送到远程库
## 删除文件
1. `rm file`删除无用的文件
2. 若确实要从版本库删除该文件则 `git rm file`删掉并且`git commit`
3. 若删除错误，则`git checkout -- file` 轻松地把误删的文件恢复到最新版本, (该命令是用版本库里的版本替换工作区的版本，无论工作区修改或者删除，则一键还原)
---
# 远程仓库
1. 查看当前所有的远程仓库`git remote -v`
2. 解除其中一个远程仓库`git remote rm <远程库名>`
## 添加远程库
1. `git remote add origin mahaosjz@gmail.com:git@github.com:mahaosjz/git_learn.git`,下载后可以把本地库的内容推送到远程库上
2. `git push -u origin master`把当前分支推送到远程，-u参数 第一次推送时把本地的master分支推送到远程新的master分支，并与之关联。
## 远程克隆
1. 要克隆一个仓库，首先知道仓库的地址，然后`git clone 远程地址`
## 分支管理
### 创建与合并分支
1. 查看分支：`git branch`
2. 创建分支：`git branch <name>`
3. 切换分支：`git checkout <name>`
4. 创建+切换分支：`git checkout -b <name>`
5. 合并某分支到当前分支：`git merge <name>`
6. 删除分支：`git branch -d <name>`
