Git使用教程

一.创建版本仓库

	1.打开git bash窗口
	2.在你本地选择一个位置，然后cd到位置 cd F:\
	3.创建空文件： mkdir 命令   mkdir gitFile  mkdir document 
	4.用pwd命令查看当前位置  pwd命令用于显示当前目录。
	5.通过git init 命令 初始化一个空的版本库，创建好后，就会有一个.git文件 这个目录是Git来跟踪管理版本库的。如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -ah命令就可以看见
	6.通过git add 命令将文件添加到git仓库	git add readme.txt
	7.通过git commit -m "提交记录" 提交到仓库		文件要一个一个add，最后一起commit
二.操作历史及版本
	1.本地文件修改之后，可以通过 git status 查看状态
	2.可以通过 git diff 查看文件具体修改了那些地方
	3.提交修改和提交新文件是一样的两步，git add 和 git commit
	4.本模块未完待续。。。。。。。。。。。。。。。。。。。。。。。

三.远程仓库
	1. 关联github远程仓库
		1.1 创建github账号
		1.2 创建ssh key	因为你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的
			1.2.1 （windows）打开git bash 的shell窗口，输入 ssh-keygen -t rsa -C "youremail@example.com" 
			1.2.2 你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。如果一切顺利的话，可以在用户主目录（C:\Users\zlj）里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。 
		1.3 登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容。当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。
		1.4 创建远程仓库
			1.4.1 首先，登陆GitHub
			1.4.2 然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库，填写仓库名和描述
			1.4.3 切记不要勾选创建readme文件，否则提交的时候冲突！！！
		1.5 创建好新库后，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。现在，我们根据GitHub的提示，在本地的仓库下运行命令：
			1.5.1 git remote add origin git@github.com:wuhuangAndBazhahei/technicalDocuments.git
			1.5.2 添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。
		1.6 把本地库的所有内容推送到远程库上
			1.6.1 git push -u origin master
			1.6.2 把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
			1.6.3 推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样。
		1.7 从现在起，只要本地作了提交，就可以通过命令： git push origin master
		1.8 SSH警告
			1.8.1 当你第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告，这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。Git会输出一个警告，告诉你已经把GitHub的Key添加到本机的一个信任列表里了。这个警告只会出现一次，后面的操作就不会有任何警告了。如果你实在担心有人冒充GitHub服务器，输入yes前可以对照GitHub的RSA Key的指纹信息是否与SSH连接给出的一致。
