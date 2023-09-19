# GIT

- 分布式版本控制工具

## GIT工作原理![img](C:/Users/%E8%89%AF%E5%B0%8F%E8%BE%B0/Documents/Typora/GITHUB.assets/1352126739_7909.jpg)

- "HEAD" 实际是指向 master 分支的一个"游标"
- 执行 **git add** 命令时，暂存区的目录树被更新
- 提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
- **git reset HEAD** 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响
- **git rm --cached <file>** 命令时，会直接从暂存区删除文件，工作区则不做出改变。
- 执行 **git checkout .** 或者 **git checkout -- <file>** 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动,加到暂存区的改动以及新文件都不会受到影响
- 当执行 **git checkout HEAD .** 或者 **git checkout HEAD <file>** 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

## Sourcetree

一般用法

- 暂存，提交，推送
- 双击分支切换工作区
- 新建分支，合并分支
  - ![image-20221018121149893](C:/Users/%E8%89%AF%E5%B0%8F%E8%BE%B0/Documents/Typora/GITHUB.assets/image-20221018121149893.png)
- 拉取单独拉分支
- 获取拉整个

## 常用命令

- 简明教程[git 简明指南 (runoob.com)](https://www.runoob.com/manual/git-guide/)

![img](C:/Users/%E8%89%AF%E5%B0%8F%E8%BE%B0/Documents/Typora/GITHUB.assets/git-command.jpg)

- git init - 初始化仓库。

- git clone [url] - 克隆仓库

- git add . - 添加文件到暂存区。

- git commit - 将暂存区内容添加到仓库中。

  - git commit -m [message]
    - message可以是备注信息
  - git commit -am [message]
    - 同时执行add和commit

- git reset

  - ```
    $ git reset HEAD^            # 回退所有内容到上一个版本  
    $ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
    $ git  reset  052e           # 回退到指定版本
    
    ```

- git status -s  简短说明

- | `git add`    | 添加文件到暂存区                         |
  | ------------ | ---------------------------------------- |
  | `git status` | 查看仓库当前的状态，显示有变更的文件。   |
  | `git diff`   | 比较文件的不同，即暂存区和工作区的差异。 |
  | `git commit` | 提交暂存区到本地仓库。                   |
  | `git reset`  | 回退版本。                               |
  | `git rm`     | 将文件从暂存区和工作区中删除。           |
  | `git mv`     | 移动或重命名工作区文件。                 |

### git remote

- git remote -v  显示所有远程仓库

- 显示某个远程仓库的信息：

  ```
  git remote show [remote]
  ```

- 添加远程版本库：

  ```
  git remote add [shortname] [url]
  ```

  shortname 为本地的版本库，例如：

  ```
  # 提交到 Github
  $ git remote add origin git@github.com:tianqixin/runoob-git-test.git
  $ git push -u origin master
  ```

- ```
  git remote rm name  # 删除远程仓库
  git remote rename old_name new_name  # 修改仓库名
  ```

### git branch

创建分支命令：

```
git branch (branchname)
```

切换分支命令:

```
git checkout (branchname)
```

当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。

合并分支命令:

```
git merge 
```

删除分支命令：

```
git branch -d (branchname)
```

Git标签

```
$ git tag -a v1.0
```

## 常用工作流

### git clone

![image-20221016161408680](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016161408680.png)

### git checkout -b my-feature

![image-20221016161541298](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016161541298.png)

### git diff

![image-20221016161754330](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016161754330.png)

### git add < >

![image-20221016161853959](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016161853959.png)

### git commit

![image-20221016161943182](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016161943182.png)

### git push origin my-feature

![image-20221016162057980](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162057980.png)

### git checkout main

![image-20221016162232348](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162232348.png)

 以防init有更新

### git pull origin master

![image-20221016162346172](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162346172.png)

### git checkout my-feature

![image-20221016162441205](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162441205.png)

### git rebase main

![image-20221016162530808](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162530808.png)

### git push -f origin my-feature

- -f强制提交
- ![image-20221016162739795](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162739795.png)
- ![image-20221016162955803](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016162955803.png)
- 先squash所有更改再merge

删除分支

- 远端delete branch
- 本地git checkout main切换到main
- git brach -D my-feature删掉本地的分支
- git pull origin master再次更新main
- ![image-20221016163556070](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20221016163556070.png)