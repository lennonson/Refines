[[CODE]]
1. 使用git init初始化当前仓库

   ```bash
   git init
   ```

2. 使用git add命令将文件添加到本地仓库的提交缓存

   ```bash
   # add one file
   git add test.c
   # add all file in directory
   git add .
   git add --all
   ```

3. 使用git commit命令为其添加修改的描述信息

   ```bash
   git commit -m "something annotation"
   ```

4. 重写上一次的提交信息

   ```bash
   git commit --amend
   ```

5. 查看历史提交日志

   ```bash
   git log
   ```

6. 回滚代码仓库：

   ```bash
   git reset --hard [要回滚id]
   ```

7. 查看当前仓库状态

   ```bash
   git status
   ```

8. 将文件撤销回到最近一次修改的状态：

   ```bash
   git checkout -- file
   ```

9. git基本组成框架：Workspace、Index / Stage、Repository、Remote

   > - Workspace：开发者工作区
   > - Index / Stage：暂存区/缓存区
   > - Repository：仓库区（或本地仓库）
   > - Remote：远程仓库

10. git创建分支

    1. 使用git checkout -b参数来创建一个分支，创建完成分支后会自动切换过去

       ```bash
       git checkout -b dev
       ```

    2. 然后我们在使用branch来查看当前属于哪个分支，也就是查看HEAD的指向

       ```bash
       git branch
       ```

11. git切换分支

    ```bash
    git checkout master
    ```

12. git合并分支

    ```bash
    git merge
    ```

13. git查看分支

    ```bash
    git branch -a
    ```

14. git删除分支

    1. 删除前切换到其他分支

       ```bash
       # 1. 创建并切换到 main 分支
       git checkout -b main
       ```


```bash
git branch -D master
```

15. github将本地仓库关联到远程仓库

    ```bash
    git remote add origin
    ```

16. git推送

    1. 推送前先拉去`pull`

       ```bash
       git pull origin main --rebase
       
       # 强制push
       git push -u origin main --force
       ```


```bash
# example
git push -u origin master
```









