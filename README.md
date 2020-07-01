# How-To-Use-System-Shortcut-keys
note: system shortcut keys

前置
1、有github账号
2、本地安装了git

目录
    涉及git命令
    建立仓库
    日常操作
    注意事项

正文
一、涉及git命令
git init --本地初始化建立git仓库
git clone <url> --克隆远程代码仓库
git remote add origin <url> --在url远程建立仓库origin
git remote -v --查看可用远程
git status [-s] --git当前状态/详细状态
git pull <branch> --拉取远程仓库到本地branch分支中
git fetch origin --把远程仓库中origin最新代码取回
git add <file/dir> --添加追踪的文件或文件夹
git commit -m "<text>" --提交所有追踪的文件到本地版本库，准备推送
git push <origin> <master> --将本地master分支推送到远程仓库
git branch --git本地分支目录(结果中带星号为当前选择分支)
git checkout -b <branch> --建立一个新的分支branch并选择
git branch -d <branch> --删除分支branch，branch不能是选择中的分支

二、建立仓库
1、本地生产ssh-keygen，并将ssh秘钥上传至github，具体步骤参考 摆渡 搜索结果
2、在github上创建一个新的repository，记下那个链接，后续有用

三、操作起来
1、首先我们在本地创建两个文件夹，模拟两个小伙伴协作开发，一个叫二狗，一个 叫小胖

2、我们进入小胖文件夹，git init 初始化本地仓库，git remote add origin https://github.com/Annanl/gittest.git 创建远程仓库，起名为origin，git remote -v 查看远程仓库

3、这时小胖创建了一个新的文件xiaopang01.txt，然后git add xiaopang01.txt表示追踪这个文件，以后它有代码更改git都会检测到，git commit -m "xiaopang01.txt" 提交一个本地版本，引号内容表示这个版本提交了什么更新，比如登录，git push origin master 提交此版本到远程仓库，也就是github上
这时我们发现github上已经有了一个新的文件，文件后面写有xiao01.txt就是commit时写的版本信息

4、现在我们让二狗加入开发，进入二狗文件夹，先本地初始化git init，然后pull拉下来代码，这时二狗的文件夹里已经有了远程仓库的所有代码文件

5、这时二狗改了一下这个文件，写了点代码进去，然后add,commit,push的时候发现，不能提交？
是因为只拉了代码没有添加远程仓库，提交成功后发现github上的提交版本已经更新为erdog change1

6、这时小胖也改了一下xiaopang01.txt，然后add，commit，push提交，又失败了，这是因为这时网上的代码与小胖的代码不一样，github并不知道应该保留哪一部分

7、OK我们来解决这个问题，关键操作来了，注意这里不应该是发现提交失败的时候才这样操作，你应该每次提交前都这样操作，git checkout -b dev 建立一个新的分支，我们看到建立成功后自动从默认的master主分支切换到了dev分支上，使用git时要时刻注意自己的当前分支
我们也可以git branch 查看目前分支列表，带星号为当前分支

8、使用git pull origin master 将远程仓库origin的master分支的内容合并到本地当前分支dev里，红框内为有冲突并已经合并的文件，我们需要手动打开去修改
打开发现是这样的，根据自己需要选择留下的代码
好，我们选择都留下

9、这时又是关键一步，同样是add，commit，但是并不push，我们先切换到master主分支上，然后将dev合并到master分支上，删除dev分支，这时进行push就可以了
10、打开github，发现提交成功了

四、注意事项
1、重要提交流程
      （1）开发使用master主分支就行
      （2）提交代码之前创建分支，在新分支上进行合并远程仓库
      （3）将新分支合并到master主分支上，并删除临时分支
      （4）提交
————————————————
