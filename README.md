# gitdemo
练习git

# 分支提交练习
一般开发别人的仓库和开发自己的仓库流程都可以参考这个

1. 首先默认我们的**master**分支是不能主动提交的，这是规范，比如你github action会基于master分支的变动触发更新上线。

2. 那既然不能动master如何开发呢？答案是大家每次开发都先基于master pull一下，然后创建新分支进行开发

```
git branch  :先查看自己在哪个分支，一般都是默认在master
git pull  :拉取远程仓库的master，及时更新
git branch feature/xxxx  ：创建新分支，xxx命名这次打算做什么新功能
git checkout feature/xxxx :本地切换到这个分支上
```

3. 然后进行开发

4. 开发完你可以本地切换到master观察下本地文件，发现改动没了，切换回feature/xxxx改动又来了，这样feature出bug可以直接删了，回到master，比直接在master上面开发容易多啦。

5. 然后是回到feature/xxxx 添加提交改动上传git
```
git checkout feature/xxxx
git add .
git commit -m "feat: xxx"
git push --set-upstream origin feature/xxxx   这个后缀你不写，命令行也会提示你添加，意思是仓库上游也添加这个分支，因为一开始没有嘛
```

6. 这时候本地开发完成，合并分支不是在本地进行的。是由仓库管理员或者其它同学进行，这里有个名词叫提交`PR `和 `code review`

7. 首先开发者回到主仓库看到自己提交的分支到仓库了，上面有个 PR按钮，提交一下，就是表示我申请合并

8. 这时候在tab栏第三格 Pull request这里可以看到刚刚的合并申请，为什么要在仓库申请合并呢？是因为这时候一般是仓库管理员或者你的mentor leader  同事，对你代码进行审核。当然你也可以直接给自己审核

9. 先要对比看下代码的改动，对改动提交评论是叫code review，一般不code review是不能接受PR的


10. 评论后选择接受PR，开发完毕，分支会自动被删除

11. 开发人员手动删除feature/xxx 回到master，注意此时master还是旧的，所以git pull，好啦，本地同步也完成，一个git 合作开发过程就这样啦

12. 那合作体现在哪？就是大家都是提交自己的分支，然后合并到master，这就是合作，当然也会出现冲突，A同学基于10点钟master仓库将money = 100 改成了money = 150，B统计也基于10点钟的master仓库将money = 100 改成 money = 50；

此时A同学的PR先被管理员接受，B同学提交的时候就冲突了，他的git 改动是100 -> 50,但仓库里面居然是150，这时候PR就显示冲突，管理员页面会有冲突解决模板，管理员看到A同学+50，b同学-50，此时money应该是100，选择既不接受money = 150，也不接受money=50，手动修改冲突为 money = 100. 提交code review，同意PR，结束

```

//等会演示的时候补充

```
