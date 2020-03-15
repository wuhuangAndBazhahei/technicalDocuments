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
