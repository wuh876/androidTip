# git常用命令

## 1、查看本地分支
```
git branch
```
## 2、查看远程分支
```
git branch -r
```
## 3、查看所有分支
```
git branch -a
```
## 4、切换远程分支
```
git checkout -b myRelease origin/Release
Branch myRelease set up to track remote branch Release from origin.
Switched to a new branch 'myRelease'

checkout远程的Release分支，在本地起名为myRelease分支，并切换到本地的myRelase分支
```
## 5、合并分支

合并前要先切回要并入的分支
```
把cloud分支合并入master分支
  git checkout master
  git merge cloud
```
## 5、合并分支

合并前要先切回要并入的分支
```
把cloud分支合并入master分支
  git checkout master
  git merge cloud
```
## 6、撤消上一次commit的内容(该操作会彻底回退到某个版本，本地的源码也会变为上一个版本的内容)

```
  git log
  git reset --hard <commit-id>
```
## 7、注释换行
```
  git commit -m '
    >1、.....
    >2、.....
  '
  git commit --amend 可以查看到刚刚commit的log信息
```
