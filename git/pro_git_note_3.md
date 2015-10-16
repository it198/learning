## 《Pro Git》读书笔记3 -- Git分支

### 3.1 分支简介

* Git 的分支实质上仅是包含所指对象校验和（长度为 40 的 SHA-1 值字符串）的文件，所以它的创建和销毁都异常高效。

	`git branch [branch-name]`  //创建分支
	
	`git checkout [branch-name]`  //切换分支

### 3.2 分支的新建与合并

* **新建分支**

	`git checkout -b [branch-name]`
	
	相当于
	
	`git branch [branch-name]`
	
	`git checkout [branch-name]`

* *请牢记*：当你切换分支的时候，Git 会重置你的工作目录，使其看起来像回到了你在那个分支上最后一次提交的样子。


* **分支的合并** 

	`git merge [branch-name]`
	
	`git checkout -d [branch-name]` // 删除分支
	
* **遇到冲突时的分支合并**

	* 如果你在两个不同的分支中，对同一个文件的同一个部分进行了不同的修改，Git 就没法干净的合并它们。
	
	* 有冲突需手动修改再做合并
	
	* 图形化合并工具 `git mergetool`


### 分支管理

* `git branch` 命令不只是可以创建与删除分支。

	`git branch`  // 获取分支列表
	
	`git branch -v` // 查看分支的最后一次提交
	
	`git branch --merged` // 已经合并的分支
	
	`git branch --no-merged`  // 未合并工作的分支
	
	`git branch -d [branch-name]`  // 删除分支
	
	`git branch -D [branch-name]` // 强制删除分支

### 分支开发工作流

* 长期分支
	
	你可以用这种方法维护不同层次的稳定性。

* 特性分支

	特性分支对任何规模的项目都适用。 特性分支是一种短期分支，它被用来实现单一特性或其相关工作。

### 远程分支

* 推送  `git push [remote] [branch]`

* 拉取  `git fetch`

* 删除远程分支  `git push [remote] --delete [branch]`

### 变基

* 不要对在你的仓库外有副本的分支执行变基。

* 变基命令 `git rebase` ,变基也是一种分支合并

* **变基VS合并**

	总的原则是，只对尚未推送或分享给别人的本地修改执行变基操作清理历史，从不对已推送至别处的提交执行变基操作，这样，你才能享受到两种方式带来的便利。
	
	



