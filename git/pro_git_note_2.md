## 《Pro Git》读书笔记2 -- Git基础

### 2.1 获取Git仓库

* **在现有目录中初始化仓库**

	`git init`

* **克隆现有的仓库**

	`git clone [path]`
	
### 2.2 记录每次更新到仓库

* **检查当前文件状态**

	`git status`
	
	*状态简览*
	
	`git status -s` / `git status --short`  
	
* **跟踪新文件**

	`git add <filename/directory>`

* **忽略文件**

	一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。
	
	`.gitignore`
	
	GitHub 有一个十分详细的针对数十种项目及语言的 `.gitignore` 文件列表，你可以在 [https://github.com/github/gitignore](https://github.com/github/gitignore) 找到它.
	
* **查看已暂存和未暂存的修改**

	`git diff`
	
	`git diff --cached` / `git diff --staged`
	
	`git difftool`

* **提交更新**

	`git commit`
	
	`git commit -m <msg>`	
	
* **跳过使用暂存区域**

	`git commit -a -m <msg>`
	
* **移除文件**

	`git rm <filename>`
	
* **移动文件**

	`git mv <filename>`
	
	相当于
	
	`mv A B`
	
	`git rm A`
	
	`git add B`
	
### 2.3 查看提交历史

* 查看提交历史的工具是 `git log`

* 但它很多格式化的参数，能更美观的显示日志数据

	`git log --pretty=onelie`
	
	`git log --pretty=format:XXX`  很多选项
	
	`git log -P`
	
	`git log -p -<n>` n表示显示n条数据

### 2.4 撤销操作

* 注意，有些撤消操作是不可逆的。
 
	`git commit --amend`
	
	`git reset HEAD <file>`  // 取消暂存的文件
	
	`git checkout -- [file]` 是一个危险的命令；你对那个文件做的任何修改都会消失 - 你只是拷贝了另一个文件来覆盖它。 除非你确实清楚不想要那个文件了，否则不要使用这个命令。
	
### 2.5 远程仓库的使用

* **查看远程仓库**
	
	`git remote`
	
	`git remote -v`
	
	`git remote show [remote-name]`
	
* **添加远程仓库**

	`git remote add <shortname> <url>`
	
* **从远程仓库中抓取与拉取**

	`git fetch [remote-name]`
	
* **推送到远程仓库**

	`git push [remote-name] [branch-name]`

* **远程仓库的移除与重命名**

	`git remote rename `
	
	`git remote rm`

### 2.6 打标签

* **列出标签**

	`git tag`
	
	`git show [tagName]`  //查看某个标签
	
* **创建标签**

	 Git 使用两种主要类型的标签：轻量标签（lightweight）与注释标签（annotated）。
	 
	 创建轻量标签，不需要使用 -a、-s 或 -m 选项，只需要提供标签名字
	 
	 `git tag [tagName]`
	 
	 `git tag -a [tagName] -m <msg>`
	 
* **后期打标签**

	对过去的提交打标签
	
	`git tag [tagName] [版本ID]`
	 
* **共享标签**
	
	默认情况下，`git push` 命令并不会传送标签到远程仓库服务器上。 在创建完标签后你必须显式地推送标签到共享服务器上。	 
	
	`git push [remote-name] [branch-name] [tag-name]`
	

### 2.7 Git别名

* Git 只是简单地将别名替换为对应的命令。

	`git config --global alias.XX [verb]`
	
	eg
	
	`git config --global alias.co checkout` // 使用  `git co`
	
	