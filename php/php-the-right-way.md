## 《PHP之道》学习笔记

### 欢迎

* 《PHP之道》[官网](http://www.phptherightway.com/)

*  简体中文版 

	[连接1](http://laravel-china.github.io/php-the-right-way/)
	
	[连接2](https://github.com/laravel-china/php-the-right-way/)
	
	[连接3](http://wulijun.github.io/php-the-right-way/)

### 入门指南

#### 使用当前稳定版本(5.6)

虽然 5.2 和 5.6 之间增加的版本号似乎很小，但却做了很多优化和改进。

#### 内置的web服务器

* 版本要求 > 5.4

* 这个内置的Web服务器主要用于本地开发使用，不可用于线上产品环境。

* [了解更多内置的命令行服务器](http://php.net/manual/zh/features.commandline.webserver.php)

#### PHP安装

* **Mac 安装**
	
	* 包管理器 : [php-osx by Liip](http://php-osx.liip.ch/)
	
	* 自己编译 : [官方教程](http://php.net/manual/en/install.macosx.php)
	
	* 集成环境 : [MAMP](https://www.mamp.info/en/) 、[XAMPP](https://www.apachefriends.org/index.html)

* **Windows 安装** 

	* 集成环境 : [WAMP](http://www.wampserver.com/) 、 [XAMPP](https://www.apachefriends.org/index.html)
	
	* 如果你需要把产品部署在Windows上，那么IIS7将给你最稳定和性能最佳的环境。
	
	* 参考网址 [php.iis.net](http://php.iis.net/) 、 [phpmanager](http://phpmanager.codeplex.com/)
	
* **Linux 安装**

	* 集成环境  [LNMP](http://lnmp.org/)
		
* **Vagrant**

	* [官网](https://www.vagrantup.com/)
	
	* [puphpet](https://puphpet.com/)
	
### 代码风格指南

* [框架互操作组](http://www.php-fig.org/)(即PHP标准组)发布了一系列推荐风格

* [英文版](http://www.php-fig.org/psr/)

* [中文版](https://github.com/hfcorriez/fig-standards)

* 其他规范
	* [Pear](http://pear.php.net/manual/en/standards.php)
	* [Zend]()
	* [Syfony](http://symfony.com/doc/current/contributing/code/standards.html)