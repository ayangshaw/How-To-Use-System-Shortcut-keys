1-  關於linux的使用技巧和命令行的使用記錄檔案;
第一次提交項目, 创建分支master  
win + R   ==>  Git bash 
1、git init 在当前文件建立一个git仓库(可以直接拖项目文件夹)
2、git add 项目名称 ，或者可以直接git add . //(这样是所有的项目)
3、git commit -m "fist commit"  如果不是第一次，以上三步可以省略；走下面两步就可以了
4、git remote add origin <仓库地址>
5、git push -u origin master
----------------------------------------------------------------------------
如果顺利，一路不会报错。如果不顺利的话
解决办法：
git pull  //同步数据
git push --force origin master  //强制提交数据到master
----------------------------------------------------------------------------

第二次提交项目，创建分支
git add .  //点号和add中间必须有空格、否则会报错
git commit -m "备注“
git branch 新的分支名  //创建分支
git status 查看分支  
git push origin 新的分支名  //提交