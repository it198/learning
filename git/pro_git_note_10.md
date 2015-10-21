## 《Pro Git》读书笔记10 -- Git内部原理

### 10.1 底层命令和高层命令

* **关于底层命令**

	* 底层命令得以让你窥探 Git 内部的工作机制，也有助于说明 Git 是如何完成工作的，以及它为何如此运作。 多数底层命令并不面向最终用户：它们更适合作为新命令和自定义脚本的组成部分。
	
* **git init 初始化**

	* `git init` 初始化 `.git`目录结构：
		* `HEAD` 指示目前被检出的分支
		* `branches/`
		* `config` 包含项目特有的配置选项
		* `description` 仅供 GitWeb 程序使用，我们无需关心
		* `hooks/` 包含客户端或服务端的钩子脚本（hook scripts）
		* `info/` 包含一个全局性排除（global exclude）文件，用以放置那些不希望被记录在 `.gitignore` 文件中的忽略模式（ignored patterns）
		* `objects/` 存储所有数据内容
		* `refs/` 存储指向数据（分支）的提交对象的指针
	* Git的核心组成部分: `HEAD` 、 `index`(尚未创建的) 、`objects` 、`refs`

### 10.2 Git对象

* **Git 对象**
	* Git 是一个内容寻址文件系统。
	
	* Git 的核心部分是一个简单的键值对数据库（key-value data store）。 你可以向该数据库插入任意类型的内容，它会返回一个键值，通过该键值可以在任意时刻再次检索（retrieve）该内容。 
	
	* Git 存储内容的方式——一个文件对应一条内容，以该内容加上特定头部信息一起的 SHA-1 校验和为文件命名。 校验和的前两个字符用于命名子目录，余下的 38 个字符则用作文件名。
	
	* 存储数据  `git hash-object -w [file]`
	
	* 读取数据 `git cat-file -p [file-name]`
	
	* 读取数据类型  `git cat-file -t [file-name]`
	
* **树对象**

	* Git 以一种类似于 UNIX 文件系统的方式存储内容，但作了些许简化。 所有内容均以树对象和数据对象的形式存储，其中树对象对应了 UNIX 中的目录项，数据对象则大致上对应了 inodes 或文件内容。 
	
	* 一个树对象包含了一条或多条树对象记录（tree entry），每条记录含有一个指向数据对象或者子树对象的 SHA-1 指针，以及相应的模式、类型、文件名信息。
	
	* `git write-tree` 命令将暂存区内容写入一个树对象。 此处无需指定 `-w` 选项——如果某个树对象此前并不存在的话，当调用 `write-tree` 命令时，它会根据当前暂存区状态自动创建一个新的树对象 

	* `git read-tree`   `git update-index`
	
* **提交对象**

	* 可以通过调用 `commit-tree` 命令创建一个提交对象
		
			$ echo 'first commit' | git commit-tree d8329f
			
			fdf4fc3344e67ab068f836878b6c4951e3b15f3d
	* Git 所做的实质工作——将被改写的文件保存为数据对象，更新暂存区，记录树对象，最后创建一个指明了顶层树对象和父提交的提交对象。 这三种主要的 Git 对象——数据对象、树对象、提交对象——最初均以单独文件的形式保存在 `.git/objects` 目录下。 
	
* **对象存储**

	* 在存储内容时，会有个头部信息一并被保存。


### 10.3 Git引用

* **Git 引用**

	* Git 引用文件放在 在 `.git/refs` 目录下
	
	* 当运行类似于 `git branch (branchname)` 这样的命令时，Git 实际上会运行 `update-ref` 命令，取得当前所在分支最新提交对应的 SHA-1 值，并将其加入你想要创建的任何新引用中。

* **HEAD 引用**

	* 执行 git branch (branchname) 时，Git 如何知道最新提交的 SHA-1 值呢？ 答案是 HEAD 文件。
	
	* HEAD 文件是一个符号引用（symbolic reference），指向目前所在的分支。 所谓符号引用，意味着它并不像普通引用那样包含一个 SHA-1 值——它是一个指向其他引用的指针。
	
	* `symbolic-ref` 命令可以查看HEAD引用的值，也可以设置该值
	
		`git symbolic-ref HEAD`
		
		`git symbolic-ref HEAD refs/heads/test`
		
* **标签引用**

	* 标签对象（tag object）非常类似于一个提交对象——它包含一个标签创建者信息、一个日期、一段注释信息，以及一个指针。 主要的区别在于，标签对象通常指向一个提交对象，而不是一个树对象。 它像是一个永不移动的分支引用——永远指向同一个提交对象，只不过给这个提交对象加上一个更友好的名字罢了。

* **远程引用**

### 10.4 包文件

* Git 使用 zlib 压缩文件的内容。

* Git 最初向磁盘中存储对象时所使用的格式被称为“松散（loose）”对象格式。 但是，Git 会时不时地将多个这些对象打包成一个称为“包文件（packfile）”的二进制文件，以节省空间和提高效率。 当版本库中有太多的松散对象，或者你手动执行 `git gc` 命令，或者你向远程服务器执行推送时，Git 都会这样做。 要看到打包过程，你可以手动执行 `git gc` 命令让 Git 对对象进行打包

* `git verify-pack` 这个底层命令可以让你查看已打包的内容

### 10.5 引用规格

* 默认情况下，引用规格由 git remote add 命令自动生成， Git 获取服务器中 refs/heads/ 下面的所有引用，并将它写入到本地的 refs/remotes/origin/ 中。

* **引用规格推送**

	* `git push origin master:refs/heads/qa/master`
	
	* 如果他们希望 Git 每次运行 git push origin 时都像上面这样推送，可以在他们的配置文件中添加一条 push 值：
	
			[remote "origin"]
				url = https://github.com/schacon/simplegit-progit
				fetch = +refs/heads/*:refs/remotes/origin/*
				push = refs/heads/master:refs/heads/qa/master
* **删除引用**

	`git push origin :topic`
	
	因为引用规格（的格式）是 <src>:<dst>，所以上述命令把 <src> 留空，意味着把远程版本库的 topic 分支定义为空值，也就是删除它。


### 10.6 传输协议

* Git 可以通过两种主要的方式在版本库之间传输数据：“哑（dumb）”协议和“智能（smart）”协议。 

* 如果你正在架设一个基于 HTTP 协议的只读版本库，一般而言这种情况下使用的就是哑协议。现在已经很少使用哑协议了。 使用哑协议的版本库很难保证安全性和私有化。

* **智能协议** ： SSH 、 HTTP(S)

### 10.7 维护与数据恢复

* 有的时候，你需要对仓库进行清理 - 使它的结构变得更紧凑，或是对导入的仓库进行清理，或是恢复丢失的内容

* **维护**

	`git gc --auto`
	
* **数据恢复**

	`git reset`  `git reflog`
	
* **移除对象**

### 10.8 环境变量

* Git 总是在一个 bash shell 中运行，并借助一些 shell 环境变量来决定它的运行方式。

* 像通常的程序一样，Git 的常规行为依赖于环境变量。


