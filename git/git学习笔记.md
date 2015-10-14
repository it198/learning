## git学习笔记

### 简介与安装

1. **相关网址**

	. [git-scm](http://git-scm.com/)
	
	. [github](https://github.com/)
				
2. **安装**

	[安装说明](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
	
	版本查看 
	
	`git --version`
	
	获取帮助  
	
	`git help <verb>`
	
	`git <verb> --hlep`
	
	`man git-<verb>`
	
### 创建新仓库

创建新文件夹，打开，然后执行下面命令
	
`git init`（初始化）
	
以创建新的git仓库

### 检出仓库(克隆版本)

* 克隆本地仓库版本

	`git clone /path/to/repository` 
	
* 克隆远程仓库版本
	
	`git clone username@host:/path/to/repository`

### 工作流

* 本地仓库由git维护的三棵"树"组成。第一个是你的 **工作目录** ，它持有实际文件；第二个是 **暂存区(Index)** , 它像个缓存区域，临时保存你的改动；最后是 **HEAD**，它指向你最后一次提交的结果。

* working dir `add` ==> Index(Stage) `commit` ==> HEAD(master)

### 添加和提交

* 添加

	`git add <filenme>`
	
	`git add *`
	
	提出更改只是把他们添加到缓存区，这是git基本工作流程的第一步

* 提交
	
	`git commit -m "代码提交信息"`
	
	提交改动，就是把改动提交到了HEAD,但是还没推送到你的远程仓库


### 推送改动

* 推动改动到远程仓库

	`git push origin master` 
	
	master 可以换成你想要推送的任何分支
	
* 推送到所添加的服务器

	`git remote add origin <server>`

	如果还克隆现有仓库，并想将你的仓库连接到远程服务器，可以使用上面的命令

### 分支

* 分支是用来将特性开发绝缘开来的。创建仓库的时候，*master* 是“默认”的分支。在其他分支上进行开发，完成后台再将他们合并到主分支上。

* 创建并切换分支

	`git checkout -b feature_x`

* 切换回主分支

	`git chekcout master`

* 查看分支

	`git branch`
	
* 删掉新建的分支

	`git branch -d feature_x`
	
* 推送分支到远程仓库，不然该分支就不为人所见

	`git push origin <branch>` 
	
### 更新与合并

* 更新本地仓库到最新改动

	`git pull`

* 合并分支

	`git mergen <branch>`
	
* 解决冲突
	
	若有冲突，需手动解决，然后再 `git add <filename>`

* 版本差异预览

	`git diff <source_branch> <target_branch>` 

### 标签

* 查看标签

	`git tag`
	
	`git show <tagName>`

* 添加标签

	`git tag <tagName>`

	`git tag <tagName> <版本ID前10位>`

* 删除标签

	`git tag -d <tagName>`

* 查看版本日志

	`git log`
	
	`git log --pretty=oneline`

### 替换本地改动

* 替换本地改动

	`git checkout -- <filename>`
	
	此命令会使用HEAD中最新内容替换掉你的工作目录中的文件。已添加到缓存区的改动以及新文件都不会受到影响。

* 获取服务器最新的版本历史，并将你本地主分支指向它

	`git fetch origin`
	
	`git reset --hard origin/master`
	
### 别名

* 创建

	* `git config --global alias.st stauts`

* 使用

	* `git st `
	
* 查看

	* `vi .gitconfig`


### 实用技巧

* 显示历史记录时，每个提交的信息只显示一行

	`git config format.pretty oneline`
	
	相当于
	
	`git log --pretty=oneline`

### 链接与资源

* 学习教程

	+ [优才网Git基础学习视频](http://www.ucai.cn/course/show/241)
	
	+ [优才网Git使用教程](http://www.ucai.cn/course/show/53)
	
	+ [廖雪峰Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
	
	+ [Git-简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)
	
* 指南与手册

	+ [Git社区参考书](http://git-scm.com/book/zh/v2)
	
	+ [GitbookIO](https://github.com/GitbookIO/git/blob/master/zh/SUMMARY.md)
	
	+ [像git那样思考](http://think-like-a-git.net/)
	
	+ [GitHub帮助](https://help.github.com/)
	
	+ [图解Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)