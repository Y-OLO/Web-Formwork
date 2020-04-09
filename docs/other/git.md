# Git 版本管理

---

## # Git 下载

[传送门](/base/install-tool)

## # 版本策略

![策略图](_media/git.png)

- `master`：主分支，存储已发布版本的源码，不能在此分支上进行开发，只能合并releace和hotfix分支
- `hotfix`：热修复分支，用来修复线上的紧急Bug，以线上版本对应的主分支为基础新建。
- `release`：预发布分支（提测分支），可以在此分支上修复Bug，以develop分支为基础新建或者合并develop分支。
- `develop`：开发分支，用于汇总各feature分支，只能合并，不能再此分支上进行开发。
- `current feature`：当前版本迭代功能的分支，业务开发人员均在feature分支上进行开发。
- `future feature`：未来版本迭代功能分支，如果某个非常重要的功能要在几个版本后开放，并且开发耗时较长，所以需要提前投入开发。

## # 注意事项
- 负责修复线上紧急Bug的hotfix分支在开发完成之后必须合并到当前正在开发的develop分支，否则会造成下次法本版本丢失hotfix的修复代码。
- release分支在测试阶段可能会有频繁的修复Bug的行为，如果在此工程中同时进行下一个版本的迭代，必须在修复Bug之后将release分支合并到develop分支，否则会引起新版本发布后老版本的既有功能出现问题。

## # Git 命令

![Git命令](_media/l-git.png)