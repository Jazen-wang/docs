## git 特殊操作

### 合并两个不相关的git仓库并保留commit记录
以下操作均在两个git仓库的master分支下执行

```shell
# 1、将repo1作为远程仓库，添加到repo2中，设置别名为other
git remote add repo1Name repo1Git

# 2、从repo1仓库中抓取数据到本仓库
git fetch other

# 3、将repo1仓库抓去的master分支作为新分支checkout到本地，新分支名设定为repo1
git checkout -b 'repo1' repo1Name/master

# 4、切换回repo2的master分支
git checkout master

# 5、将repo1合并入master分支
git merge repo1 --allow-unrelated-histories

```

