## 《Pro Git》读书笔记4 -- 服务器上的Git

### 4.1 协议

* **本地协议**（local protocol）

	* 优点
	
		简单，并且直接使用了现有的文件权限和网络访问权限。
	
	* 缺点
	
		共享文件配置比较难，并且外网访问速度特慢


* **HTTP协议**

	* 优点
		
		快速、高效，利用Https协议比较安全
		
	* 缺点
		
		Https协议架构比较麻烦，密钥认证也比较麻烦

* SSH

	* 优点
	
		传输高效，压缩再传输；
	
	* 缺点
	
		不能通过他实现匿名访问

* Git协议

	* 优点 
	
		Git 协议是 Git 使用的网络传输协议里最快的
	
	* 缺点
		
		Git 协议缺点是缺乏授权机制。

### 4.2 在服务器上搭建Git

* 把裸仓库放到服务器上

* 架设 Git 服务最复杂的地方在于用户管理。 

* 利用SSH链接

### 4.3 生成SSH公钥

*  默认情况下，用户的 SSH 密钥存储在其 ~/.ssh 目录下。

*  在Linux/Mac系统中，密钥生成工具 `ssh-keygen`

*  [Git密钥指南](https://help.github.com/articles/generating-ssh-keys/)

### 4.4 配置服务器

* 使用 `authorized_keys` 方法来对用户进行认证。

* `git-shell`

* `git help shell`

### 4.5 Git守护进程

* 通过 “Git” 协议建立一个基于守护进程的仓库。 

### 4.6 Smart HTTP

* 我们一般通过 SSH 进行授权访问，通过 git:// 进行无授权访问，但是还有一种协议可以同时实现以上两种方式的访问。 设置 Smart HTTP 一般只需要在服务器上启用一个 Git 自带的名为 git-http-backend 的 CGI 脚本。

### 4.7 GitWeb 

* 如果你对项目有读写权限或只读权限，你可能需要建立起一个基于网页的简易查看器。 Git 提供了一个叫做 GitWeb 的 CGI 脚本来做这项工作。

### 4.8 GitLab 

* Gitlab是一个用Ruby on Rails开发的开源项目管理程序,可以通过WEB界面进行访问公开的或者私人项目。

### 4.9 第三方托管的选择

*  Git 维基的 GitHosting 页面 [https://git.wiki.kernel.org/index.php/GitHosting](https://git.wiki.kernel.org/index.php/GitHosting)

* GitHub 作为目前最大的 Git 托管平台.