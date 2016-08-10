# 如何squash已经提交的commits

1. 指定commits来squash  

1.1 选择最近的5个commit

```
git rebase -i origin/master~5 master
```

1.2 选择从指定的commit开始来squash

```
git rebase -i 917748e master
```

2\. 合并commit  

2.1 这时我们可以看到：
```
pick e073fc7 fix bug
pick 517ae07 fix bug
pick 6a6dc0e fix bug
pick d17340b fix bug
pick e04de92 fix bug
```

2.2 批量将pick改成squash

```
:2,$s/^pick /squash /g
```

注意： 第一条commit是一定要pick，否则执行时会看到这样一条错误：`Cannot 'squash' without a previous commit`

2.3 这时可以看到：

```
pick e073fc7 fix bug
squash 517ae07 fix bug
squash 6a6dc0e fix bug
squash d17340b fix bug
squash e04de92 fix bug
```

3\. 提交  

```
git push origin +master
```