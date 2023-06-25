# Learn
----------------------------
此文件夹中的内容仅作为学习使用。

----------------------------
2023/4/13



# Git使用

1.git clone // 到本地
2.git checkout -b xxx 切换至新分支xxx
（相当于复制了remote的仓库到本地的xxx分支上
3.修改或者添加本地代码（部署在硬盘的源文件上）
4.git diff 查看自己对代码做出的改变
5.git add 上传更新后的代码至暂存区
6.git commit 可以将暂存区里更新后的代码更新到本地git
7.git push origin xxx 将本地的xxxgit分支上传至github上的git
\-----------------------------------------------------------
（如果在写自己的代码过程中发现远端GitHub上代码出现改变）
1.git checkout main 切换回main分支
2.git pull origin master(main) 将远端修改过的代码再更新到本地
3.git checkout xxx 回到xxx分支
4.git rebase main 我在xxx分支上，先把main移过来，然后根据我的commit来修改成新的内容
（中途可能会出现，rebase conflict -----》手动选择保留哪段代码）
5.git push -f origin xxx 把rebase后并且更新过的代码再push到远端github上
（-f ---》强行）
6.原项目主人采用pull request 中的 squash and merge 合并所有不同的commit
\----------------------------------------------------------------------------------------------
远端完成更新后
1.git branch -d xxx 删除本地的git分支
2.git pull origin master 再把远端的最新代码拉至本地





# Git连接失败处理方法

**解决git下载报错**：fatal: unable to access ‘https://github.com/…/.git/’:…

1、在git中执行git config --global --unset http.proxy和git config --global --unset https.proxy

```git
git config --global --unset http.proxy
git config --global --unset https.proxy
```


2、在cmd下执行ipconfig/flushdns 清理DNS缓存

```
ipconfig/flushdns
```


3、重新执行git clone https://github.com/…/.git/’ 即可

```
git clone 链接
```

—————————————————————————————————————————

分割线



2023/6/25 使用ssh克隆库，连接有效

# git everything up-to-date解决方法

### 现象

明明已经更改了本地代码，但是git push的时候一直提示everything up-to-date，创建了新分支，依然push了origin master的版本。

### 解决

方法特别简单，实际就是在push之前必须要写commit。

```
git commit -m "msg"
git push
```



### update

前面的做法还是不能用
还是需要用大家说的方法，创建分支，提交代码，在与maser分支合并，最后删除分支
=======
