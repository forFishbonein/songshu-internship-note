### git拉取制定分支代码的方法

> 方法一：直接拉取远程分支，并形成本地与远程的关联关系，手动签入

1.直接拉取指定分支代码

```bash
git pull origin feature #远程分支名为feature
```

注意：`git pull origin <name>` 命令在拉取远程分支时，如果本地没有同名的分支，会自动创建一个新的本地分支并关联到远程分支。如果本地已经存在同名的分支，则将远程分支的更新合并到已存在的本地分支。

所以这里会自动创建feature，但是并不会自动切过去，需要手动checkout

2.切换到指定分支

```bash
git checkout feature #本地分支名为feature
```

> 方法二：先新建本地仓库并签入，再拉取远程分支合并到已有分支

1.首先新建并切换到分支

```bash
git checkout -b feature #新建本地分支名为feature
```

注意：加不加-b的区别就是会不会新建一个分支，如果分支不存在的话会报错！

git branch查看当前所处分支

2.拉取指定分支代码

```bash
git pull origin feature #远程分支名为feature，origin为固定写法
```



> 方法二：直接拉取远程分支，并形成本地与远程的关联关系，自动签入

相当于是切换到一个远程已经存在的仓库，并在本地建立一个新仓库与之关联

```bash
git checkout -b 本地新分支名 远程分支名
```

对比：切换到本地已经存在的仓库：

```bash
git checkout 本地分支名
```

注意：形成关联关系之后，git push命令就会自动将代码推送到对应的分支



> 如果没有在checkout的时候进行关联呢，推送的时候怎么办？

如果你想将代码推送到名为 `feature` 的分支，可以使用：

```bash
git push origin feature
```

- 还有一种策略：

**首次**推送到远程仓库的分支时，使用 `-u` 参数来将本地分支与远程分支关联起来

```bash
git push -u origin feature
```

这样做后，将来的 `git push` 命令就会自动将代码推送到正确的分支，无需再指定远程仓库和分支名称。

后面的话就是：

```bash
git push #直接git push即可
```

在推送代码之前，请确保你已经完成了代码的提交和所有必要的更改。另外，你需要具有推送到远程仓库的权限。

