## 第五章、首次登陆与在线求助 man page

### 1、首次登陆系统

#### 1.1 首次登陆系统注意

* 离开系统(注销Linux)应该使用`exit`命令

* 注销，并不等于关机

### 2. 文本模式下命令的下达

#### 2.1 命令格式与语系支持 

* ` command [-options] parameter1 parameter2 ... `

* 查看当前语系  `echo $LANG` ,修改语系 `LANG=en_US`

#### 2.2 基础命令的操作

* 显示日期与时间的命令： `date`

* 显示日历的命令： `cal`

* 简单好用的计算器： `bc` , `quict`退出；bc默认仅输出整数，如果要输出小数点下位数，那么就必须要运行 scale=number ，那个number就是小数点位数

#### 重要的几个热键[Tab], [ctrl]-c, [ctrl]-d

* [Tab] : 命令补全、文件补齐

* [Ctrl]-c : 中断目前程序

* [Ctrl]-d : 直接离开了(相当于输入exit啊！)

#### 错误信息的察看

* 不怕错，学会看错误提示

### 3. Linux系统的在线求助man page与info page

* 在文本模式下，你可以直接按下`两个[Tab]按键`，看看总共有多少命令.

* man `命令`

* info `命令`

* `命令`  --help


### 4. 正确的关机方法: sync, shutdown, reboot, halt, poweroff, init

* 观察系统的使用状态：

	如果要看目前有谁在在线，可以下达『who』这个命令，而如果要看网络的联机状态，可以下达 『 netstat -a 』这个命令，而要看背景运行的程序可以运行『 ps -aux 』这个命令。使用这些命令可以让你稍微了解主机目前的使用状态！当然啰，就可以让你判断是否可以关机了 （这些命令在后面Linux常用命令中会提及喔！）

* 通知在线使用者关机的时刻：

	要关机前总得给在线的使用者一些时间来结束他们的工作，所以，这个时候你可以使用 shutdown 的特别命令来达到此一功能。

* 正确的关机命令使用：

	例如 shutdown 与 reboot 两个命令！

* 将数据同步写入硬盘中的命令： sync

* 惯用的关机命令： shutdown

* 重新启动，关机： reboot, halt, poweroff

* 切换运行等级： init

	run level 0：关机
	
	run level 3：纯文本模式
	
	run level 5：含有图形接口模式
	
	run level 6：重新启动





