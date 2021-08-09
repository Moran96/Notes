### 【坑点以及注意事项】

#### 1. 提交 `package-lock.json` 冲突

- 从远端 `master` 拉取代码至本地，再`npm install`相关依赖模块后，本地会生成 `package-lock.json`文件
- 建议不要将 `package-lock.json` 提交，因为在手动解决冲突时可能会有上万行冲突(吓人)
- 可以在 `.gitignore` 中设置忽略；或者提交时全部采用线上版本(不推荐)；也可在提交前直接删除该文件

> `package.json`: 主要用来定义项目中需要依赖的包
> `package-lock.json`：在 `npm install`时候生成一份文件，用以记录当前状态下实际安装的各个npm package的具体来源和版本号。
> `'^'` : 放在版本号之前，表示向后兼容依赖，如`'^3.11.0'`, 作用是大版本号不变的情况下，下载最新版的包
> 项目中引入的包版本号之前经常会加 `^` 号，每次在执行 `npm install` 之后，下载的包都会发生变化，为了系统的稳定性考虑，每次执行完 `npm install` 之后会对应生成 `package-lock` 文件，该文件记录了上一次安装的具体的版本号，相当于是提供了一个参考，在出现版本兼容性问题的时候，就可以参考这个文件来修改版本号即可。

### git 提交远程分支

1. 创建新分支
`git checkout -b feature-bindlist`

2. 核对并修改变化代码, 通过 + add
3. commit, 也可使用 vscode 提交，但是commit需要按照公司要求去写，是添加了功能还是debug
4. git push(不会成功，复制终端 push 信息再 push 一下就ok了)

### git 相关操作

1. `git branch` 查看本地已有分支
2. `git branch -a` 查看本地和远端分支

### 合并分支

- 由当前分支跳转至 `dev`
`git checkout dev`
- 进入 `dev` 分支后，合并目标分支
`git merge fix-bug`
- 若无冲突会自动合并
- 若有冲突请手动合并(要小心)，并根据需求选择是否添加 `commit` 信息
- 提交 `git push`

### 删除分支

- 删除远端分支
`git push origin --delete BranchName`
- 删除本地分支
`git branch -d Chapater8`

### 本地分支重命名

`git branch -m oldName newName`

### 版本回退

- https://blog.csdn.net/tsq292978891/article/details/78965693

- `git reset --hard xxxxxx`
- `git push -f origin originBranchName`

### 取消合并

- `git merge --abort`

### 连接远端仓库

- `git init`

- `git remote add origin git@github.com:yourName/repositoryname.git`
or
- `git remote add origin https://github.com/yourName/repositoryname.git`


