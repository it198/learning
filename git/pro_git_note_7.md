## 《Pro Git》读书笔记7 -- Git工具

### 7.1 选择修订版本

* **Git版本号的表示**

	使用`SHA-1`来表示，一般只要提供不少于4个字符就可以区别一个版本
	
* **版本查看**

	`git log`
	
	`git show`
	
* **引用日志**

	* 每当你的 HEAD 所指向的位置发生了变化，Git 就会将这个信息存储到引用日志这个历史记录里。

	`git reflog`   
	
	`git show HEAD@ {n}`
	
* **祖先引用**

	* 如果你在引用的尾部加上一个 ^， Git 会将其解析为该引用的上一个提交。
	
	`git show HEAD^`  `git show HEAD^^`
	
	`git show HEAD~`   `git show HEAD~3`
	
* **提交区间**

	`git log master..experiment`

### 7.2 交互式暂存

* 如果运行 `git add` 时使用 `-i` 或者 `--interactive` 选项，Git 将会进入一个交互式终端模式

* 通过命令，可以使用交互式添加模式来轻松地处理暂存区。

* **暂存补丁**

	`git add -i`  然后选择`5`或`p`（补丁）
	
	其他高级命令
	
	`reset --patch` 
	
	`checkout --patch`
	
	`stash save --patch`

### 7.3 储藏与清理

* 储藏会处理工作目录的脏的状态 - 即，修改的跟踪文件与暂存改动 - 然后将未完成的修改保存到一个栈上，而你可以在任何时候重新应用这些改动。

* **储藏工作**

 	* `git stash`
 	
 	* `git stash save`
 	
 	* `git stash list`
 	
 	* `git stash apply`  `git stash apply stash@{n}`
 	
 	* `git stash pop`
 	
 * **创造性的储藏**
 
 	* `git status -s`
 	
 * **从储藏创建一个分支**
 
 	* `git stash branch [branch-name]`
 	
 * **清理工作目录**
 
 	* `git clean`
 	
 	* `git clean -f -n`
 
### 7.4 签署工作

* **GPG 介绍**

	配置 GPG 并安装个人密钥
	
	`gpg --list-keys`
	
	`gpg --gen-key`
	
	`git config --global user.signingkey [密钥]`
	
* **签署标签**

	`git tag -s [tag-name] -m [msg]`
	
* **验证标签**

	`git tag -v [tag-name]`

* **签署提交**

	`git commit -a -S -m [msg]`
	
	签署标签与提交很棒，但是如果决定在正常的工作流程中使用它，你必须确保团队中的每一个人都理解如何这样做。 如果没有，你将会花费大量时间帮助其他人找出并用签名的版本重写提交。 在采用签署成为标准工作流程的一部分前，确保你完全理解 GPG 及签署带来的好处。

### 7.5 搜索

* **Git Grep**

	`git grep -n [查找的内容]`
	
	`git grep --count [查找的内容]`

* **Git 日志搜索**

	`git log` 很强悍，参数很多，需要时查看帮助文档


### 7.6 重写历史

* **修改最后一次提交**

	`git commit --amend`
	
* **修改多个提交信息**

	`git rebase -i HEAD-3`
	
* **重新排序提交**

* **压缩提交**

* **拆分提交**

* **核武器级选项：filter-branch**

### 7.7 重置揭密

* **三棵树**

	* HEAD ： 上一次提交的快照，下一次提交的父结点
	
		HEAD 是当前分支引用的指针，它总是指向该分支上的最后一次提交。
		
		*查看快照*：
		
		`git cat-file -p HEAD`
			
		`git ls-tree -r HEAD`
	
	* Index ： 预期的下一次提交的快照
	
		`git ls-files -s`
	
	* Working Directory ： 沙盒

* **重置**  `reset`

	* 第 1 步：移动 HEAD
	
	* 第 2 步：更新索引（--mixed）
	
	* 第 3 步：更新工作目录（--hard）


### 7.8 高级合并

* Git 的哲学是聪明地决定无歧义的合并方案，但是如果有冲突，它不会尝试智能地自动解决它。

* 所有有冲突就需要手动解决


### 7.9 Rerere

* `git rerere` 功能是一个隐藏的功能。

### 7.10 使用 Git 调试

* Git 也提供了两个工具来辅助你调试项目中的问题。

* **文件标注**

	`git blame`
	
* **二分查找**
	
	`git bisect`

### 7.11 子模块

* 子模块允许你将一个 Git 仓库作为另一个 Git 仓库的子目录。 它能让你将另一个仓库克隆到自己的项目中，同时还保持提交的独立。

### 7.12 打包

* Git 可以将它的数据 “打包” 到一个文件中。  `git bundle`

### 7.13 替换

* `replace` 命令可以让你在 Git 中指定一个对象并可以声称“每次你遇到这个 Git 对象时，假装它是其他的东西”。 在你用一个不同的提交替换历史中的一个提交时，这会非常有用。

### 7.14 凭证存储

* Git 拥有一个凭证系统来处理这个事情。

* Git 凭证辅助工具系统的命令是 `git credential`


