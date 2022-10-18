# GITHUB

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