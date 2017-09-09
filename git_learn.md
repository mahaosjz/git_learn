# 时光机穿梭
---
## 版本回退
1. git log --pretty=oneline 日志单行显示（当前版本保留的操作记录）
2. git reflog记录每一次命令（建库对版本的所有操作）
3. 版本修改并提交到版本库中（commit之后），HEAD表示当前版本，HEAD^为上一版本，网上100个版本则为HEAD~100
4. git reset --hard HEAD^ 版本回退到上一版本
