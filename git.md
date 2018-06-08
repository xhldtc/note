```git merge dev```    将dev分支上的修改合并到当前的工作分支上

```git clone http://git.51.nb/service/data-ecommerce.git```    从远程仓库克隆，会进入设置的默认分支，假设为dev

```git branch```    查看所有分支

```git branch -d xhl```    删除本地xhl分支

```git branch -D xhl```    强制删除本地xhl分支，忽略merge状态

```git push origin --delete release```    删除远程release分支

```git checkout -b xhl```    从当前工作分支复制创建分支xhl，并切换到该分支上

```git checkout -b xhl origin/xhl```    从远程xhl分支复制创建本地分支xhl，并切换到该分支上

```git checkout dev```    切换工作分支回dev

```git push origin xhl```    把本地仓库所有修改推送到远程仓库的同名分支

```git pull origin xhl```    把远程xhl分支的改动合并到本地xhl分支

```git stash```    暂存当前工作现场

```git stash list```    查看保存的工作现场列表，给到时候恢复的时候使用

```git stash pop stash@{0}```    恢复保存的工作现场，stash@{0}是从list命令里查到的那次暂存
