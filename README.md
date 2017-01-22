Title         : How to use Git
Author        : suntengfei
Logo          : True

#### 本教程为速成教程,如需要更深入的学习,请出门左拐
在浏览教程之前我们先看一下git版本管理的流程示意"图"<br><br>
本地文件--->暂存区--->本地版本库(某分支)--->远程版本库(某分支)<br><br>
以下所有版本库地址都以git@aaa.bbb:ccc.git为例<br><br>
# 初级教程<br><br>
## 我有一个现成的版本库地址我可以进行读写,我该如何将代码拉取远程代码到本地?<br>
答:
```java
  git clone git@aaa.bbb:ccc.git //将在本地新建一个ccc的文件夹,可以理解为于仓库,其实为本地文件
```
<br>
## 我已经获取到了远程的代码,经过修改,我想把我的代码改动提交的远程的版本库,我应该怎么操作呢?
答:
```java
  git diff //对比一下我的"本地文件"和"暂存区"的文件
  git add . //提交"本地文件"到暂存区
  git diff -cached //对比暂存区和本地版本库的区别
  git commit -m commit_info //提交暂存区文件到本地版本库
  git push origin master //提交本地版本库到远程版本库
```
<br>
# 中级教程<br><br>
## master分支是什么?我如何创建以及切换一个分支?<br><br>
答:<br>
一个仓库可以有多个分支,无论是本地还是远程

```java
  git branch newbranch //在本地创建一个新分支
  git checkout newbranch //将本地指向新分支
```
简而言之
```java
  git checkout -b newbranch //创建并切换到新分支newbranch
```
创建并切换到新分支之后
```java
  git commit -am commit_info //简写了add & commit
  git push origin newbranch //从本地版本库推送到远程版本库 
```
# 高级教程
## 我已经新建了一个空文件夹,我如何"绑定"远程仓库?
答:
```java
  git init //创建一个本地版本库
  git remote add origin git@git.yhouse.com:test.git //将远程版本库与本地"关联"
  git pull origin master //将远程版本库的内容拉下来(注意这里是同时fetch到了本地版本库和merge到了本地文件)
```
## 我本地有一些代码没及时关联远程版本库,我又不想clone了复制过去,一定有更简洁的方法吧?
答:<br>
我们直接按照上面的方式不就行了?但是,如果本地文件和远程文件有文件冲突了那该怎么办?问题是我不知道如何应对啊?<br>
下面就是应对方法
```java
  git init //在本地创建一个版本库
  git remote add origin git@git.yhouse.com:test.git //将远程版本库与本地"关联"
  git fetch origin master:temp //将远程版本库内容拉到新本地分支temp里面
  git diff temp 将本地文件与本地仓库新分支temp做比较
  //处理冲突或者完全没有冲突
  git merge temp //合并内容到本地
```
## 我想看一下我的提交历史?
答:
```java
  git log //查看全部提交历史commit_info信息
  git log -n //查看最近n次提交历史commit_info信息
  git log -p //查看提交历史commit_info信息以及文件更改详情
  git log --stat //-p是详情,这个没有详情,只有更改的行数git log //查看全部提交历史commit_info信息
```

## 我这次修改的错误了,我应该如何回退到上一个版本?
答:
```java
  git reset --hard HEAD^ //退回到上一个版本
```
## 学会了退回上一个版本,那么其他任意版本呢?
```java
  git reset --hard commit_id //退回到任意版本
```
## 还有什么其他有用的命令?
答:
```java
  git remote -v //查看远程版本库地址
  git branch -a //查看所有分支
```