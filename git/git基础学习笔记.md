学习视频地址(优才网 Git视频教程): [git视频链接](http://www.ucai.cn/course/show/241)

## 笔记内容

### 一、git的介绍与安装及add commit操作

1. **相关网址**

	. [git-scm](http://git-scm.com/)
	
	. [github](https://github.com/)
				
2. **安装**

	[安装说明](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
	
	版本查看 
	
	`git --version`
	
	命令帮助文档查看  
	
	`XX命令 --help`
	
3. **初始化**

	`git init`
	
4. **添加**

	`git add `

5. **提交**
	
	`git commit `


### 二、git状态与对比status diff

* `git status`

* `git diff`


### 三、git版本回退

* `git log`

* `git log --pretty=oneline`
	
* HEAD 当前版本
	
* HEAD^ 上一个版本
	
* `git reset --hard HEAD^`回退到上一个版本
	
* `git reflog`

### 四、git工作区和版本库

* 工作区

* 缓存区

* 版本库 : master(HEAD)
	
* `git add <name> ` ==>缓存区

* `git commit <name>` ===>从缓存区到master(HEAD)

### 五、git管理修改

* `git status`

* `git diff HEAD -- <name>`

### 六、git注册github和本地配置

* 注册github账号

* 本地配置

	* ssh
	
	* ssh-keygen -t rsa -C "github邮件名"
	
	* 在github设置添加ssh-key

### 七、git添加远程库

* 创建版本库:https/ssh

* 远程到本地

	* `git pull`
	
* 本地到远程

	* `git push`

### 八、git标签

* 查看分支

	* `git branch`
	
* 添加标签
		
	* `git tag <tagName>`
	
* 查看标签

	* `git tag`
		
	* `git tag -m "注释"`
	
	* `git show <tagName>`
	
* 补添加标签
	* `git log --pretty=oneline --abbrev-commit`
	
	* `git tag <tagName>版本号`
	
* 删除标签

	* `git tag -d <tagName>`

### 九、git远程库克隆

* `git clone`

### 十、git创建与合并分支

* 创建分支

	* `git branch <branchName>`
	
	* `git checkout -b <branchName>`
	
* 切换分支
	
	* `git checkout <branchName>`
	
* 合并分支

	* `git merge`
	
* 删除分支

	* `git branch -d <branchName>`

### 十一、git冲突解决

* **冲突**:两个分支上修改同一行数据
	
* **解决**:手动修改,然后git add ,git commit, git merge

### 十二、git别名

* 创建

	* `git config --global alias.st "git status"`

* 使用

	* `git st `
	
* 查看

	* `vi .gitconfig`

