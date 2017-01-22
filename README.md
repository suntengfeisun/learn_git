#初级知识

###一.客户端(本地电脑)安装git
1.windows 安装git.exe 和TortoiseGit(图形化GUI界面)<br>
2.linux安装git<br>
###二.使用git

1.克隆远程(git版本库都有一个默认为master的分支,如下全部是对master分支的操作,关于分支的操作将在中级知识中介绍)<br>
a.项目开始时已知仓库地址<br>
git clone git@xxxx:hello_world.git   //将hello_world版本库中名为master分支的数据"克隆"到本地仓库<br>
b.项目开始时未知仓库地址<br>
git init //初始化一个本地仓库<br>
git remote add origin git@xxxx:hello_world.git  // 将远程仓库地址"关联"到本地仓库(origin 为远程仓库名,不建议修改)<br>
2.提交文件/修改到远程仓库<br>
当我们完成代码,或者任何想保存代码的时候,我们将代码提交到远程仓库,步骤如下<br>
git add . //将所有文件添加到本地缓存区<br><br>
git commit //这时将启动一个vim,将文件wq保存后的内容为commit的说明(小技巧:使用git commit -m "comment_introduction")<br><br>
git push origin master //只有一个分支时,可省略为"git push"<br><br>
注意:在多人协作是一定要通过git pull 先拉取远程代码到本地,再做修改,防止冲突的发生.如何解决已经发生的冲突,另开一篇.<br><br>


#中级知识
###一.git分支相关操作:
1.克隆时不想克隆master默认分支:想克隆名为one的分支<br><br>
git clone -b one git@xxxx:hello_world.git //将hello_world版本库中名为one分支的数据"克隆"到本地<br><br>
2.已经克隆了master分支,远程已知存在one分支,想切换到one分支<br><br>
git checkout one //切换到one分支.一定注意本地原分支代码安全<br><br>
3.想把现有分支推送到远程新分支two:<br><br>
git push origin master : two //本地分支名:远程新分支名<br><br>
4.想在远程版本库新增一个为空的新分支two:<br><br>
git branch "two" //创建一个名为two的本地分支<br><br>
git checkout "two"  //将本地代码切换到本地名为two的分支(切换分支一定注意,本地原分		支代码将被删除)<br><br>
以上两句可以使用一句git checkout -b two代替<br><br>
git push origin two //推送到为two分支(省略:two,建议本地和远程分支名相同)<br><br>

#高级知识
###一.其他常用知识:
1.查看文件的不同<br><br>
git status //总览文件变化<br><br>
git diff //查看本地文件的对比<br><br>
git diff --cached //查看缓存区和本地仓库的对比,貌似与--staged意义相同<br><br>
2.查看提交历史相关操作<br><br>
git log //查看全部提交历史comment_introduction信息<br><br>
git log -n //查看最近n次提交历史comment_introduction信息<br><br>
git log -p //查看提交历史comment_introduction信息以及文件更改详情<br><br>
git log --stat //-p是详情,这个没有详情,只有更改的行数<br><br>
3.版本回退<br><br>
一言难尽详<br><br>见:http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000
强烈安利廖雪峰的git教程
4.其他:
git remote -v //查看远程版本库地址
git branch -a //查看所有分支





