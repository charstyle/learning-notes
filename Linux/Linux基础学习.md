# Linux基础学习

## Linux安装

* USTC Open Source Software Mirror：https://mirrors.ustc.edu.cn/
* Deppin国产操作系统：https://www.deepin.org/zh/download/

## 操作系统区别

```bash
# windows

C：D：E： // 盘符命名
// 可能也只有一个物理磁盘，只是虚拟成了不同的逻辑磁盘


# Linux

 /       // 以目录命名
 // 在Linux中只有一个物理盘，如果要添加其他物理盘，那就需要挂载
 
 linux 文件系统以“/”开始
 
 这个“/”称之为“根”
```

* Linux文件目录

  在普通查看文档管理器中，我没有任何区别的

  * CMD（Windows）

  * Terminal（Linux）

    ```bash
    ctrl+alt+t // 呼出终端
    
    // 终端，就算Linux输入指令的一种接口形式
    // 与图形化相似，只不过使用更少的资源
    ```

  * 文件目录的含义

    ```bash
    ls /		列举“/”目录下的文件或目录
    ls -al /	列举“/”目录下的文件或目录的详细信息（包含隐藏文件、目录）
    
    
    drwxr-xr-x	22 root	root	4096 10月 28 00:18 .
    drwxr-xr-x	22 root	root	4096 10月 28 00: 18 ..
    drwx------	6 root	root	4096 10月 28 00：18 boot
    drwxr-xr-x	7 root root		4096 7月 31 00: 13 data
    drwxr-xr-x	2 root root		4096 8月 20 23: 31 Desktop
    drwxr-xr-x	20 root root	4520 12月 18 21:57 dev
    drwxr-xr-x	139 root root	12288 11月 6 20:28 etc
    drwxr-xr-x	3 root root		4096 7月 30 16: 21 home
    drwx------	2root root		16384 7月 31 00：12 lost+found
    drwxr-xr-x	5 rootroot		4096 7月 30 16: 22  media
    drwxr-xr-x	2 root root		4096 10月 28 00: 12 mnt
    drwxr-xr-x	8 root root		4096 10月 28 00: 12 opt
    dr-xr-xr-x	332 root root	0 1月1 2217 proc
    drwxr-xr-x	4 root root		4096 7月 30 16: 21 recovery
    drwx------	5 root root		4096 8月 20 23: 21 root
    drwxr-xr-x	35 root root	920 12月 18 21: 57 run
    drwxr-xr-x	2 root root		4096 4月 17 2023 srv
    dr-xr-xr-x	13 root root	0 1月 1 2217 sys
    drwxr-xr-x	2 root root		4096 8月 20 23: 31 .Templates
    drwxrwxrwt	22 root root	12288 12月 18 23:37 tmp
    drwxr-xr-x	16 root root	4096 12月 26 2021 usr
    drwxr-xr-x	12 root root	4096 7月 30 16:25 var
    ```
    
    > 带有箭头的表示什么？？
    >
    > "—>"软链接=快捷方式
    
    像`bin —> usr/bin`的意思是`bin`代表`/usr/bin`，这仅仅是一个软链接而已，或快捷方式而已

## Linux目录的含义

```bash
.					# 当前目录
..					 # 返回上层目录
/boot			        # 存放操作系统的启动文件、加载内核的目录
/data			        # 正统的Linux是没有这个目录的，他在这里是存放一些数据内容的，比如：下载的软件
/Desktop			# 正统的Linux是没有这个目录的，（ubuntu，CentOS），桌面目录
/dev			       # 驱动类的目录
/etc				# 配置文件目录
/home			     # 家目录，隔离其他用户的数据，防止窥探
/lost+found			 # 垃圾回收站
/media			       # 多媒体光盘目录
/mnt			       # 挂载U盘的目录，约定俗成
/opt				# 下载的第三方软件存放地址（安装包、ISO文件）
/proc				# 系统信息目录
/recovery			# 正统的Linux是没有这个目录的，恢复目录
/root				# root 用户的家目录，最高权限
/run				# 存放一些pid进程，程序执行时，有一个进程号，如果要对进程进行停止或热加载，就可以使用该pid文件
/srv				# 不怎么用，基本废弃
/sys				# 用的不多，硬件上的
/.Templates			# 正统的Linux是没有这个目录的
/tmp				# 临时目录，这里的文件会在一定时间后删除，如果不去操作的话，他的权限很高，容易出问题
/usr				# 关键目录，这里存放了各种依赖项
/var				# 基本都是日志文件，目录
```

## 文件管理

> 以点开头的文件或者目录，都为隐藏文件/目录

```
ls 		# 列举目录下的文件或目录

ls -al 	# 列举目录下的所有文件或目录的详细信息（包含隐藏文件、目录）
```

```bash
# ls -al 

drwxr-x-- 25 hades hades 4096 12月 19 22:45 .
drwxr-xr-x 3 root root 4096 7月 30 16:21 ..
-rw--- 1 hades hades 3645 12月 19 07:05 .bash_history
-rw-r--r-- 1 hades hades 220 8月 4 2020 .bash_logout
-rw-r--r-- 1 hades hades 3890 8月 6 20:56 .bashrc
drwx--- 21 hades hades 4096 12月 19 22:53 .cache
drwx--- 33 hades hades 4096 12月 19 22:45 .config
drwx--- 3 hades hades 4096 7月 30 16:21 .dbus
drwxr-xr-x 2 hades hades 4096 7月 30 17:33 .deepin-calculator
drwxr-xr-x 8 hades hades 4096 10月 28 00:19 .deepinvine
drwxr-xr-x 2 hades hades 4096 11月 6 12:22 Desktop
-rw-r--r-- 1 hades hades 25 7月 30 16:21 .dmrc
drwxr-xr-x 4 hades hades 4096 11月 1 11:05 Documents
drwxr-xr-x 2 hades hades 4096 12月 19 01:43 Downloads
drwx--- 3 hades hades 4096 7月 30 16:21 .gnupg
-rw-r--r-- 1 hades hades 90 7月 30 17:39 .gtkrc-2.0
drwxr-xr-x 3 hades hades 4096 4月 17 2023 .icons
-rw-r--r-- 1 hades hades 345 7月 30 16:22 .imwheelrc
-rwxr-xr-x 1 hades hades 78973328 11月 7 16:43 kk
-rw-r--r-- 1 hades hades 35796470 12月 19 01:15 kubekey-v3.0.13-linux-amd64.tar.gz
drwxr-xr-x 3 hades hades 4096 4月 17 2023 .local
drwxr-xr-x 2 hades hades 4096 4月 17 2023 Music
drwxr-xr-x 4 hades hades 4096 10月 28 00:09 Pictures
drwx--- 3 hades hades 4096 7月 30 16:31 .pki
drwxr-xr-x 3 hades hades 4096 12月 18 22:39 Postman
-rw-r--r-- 1 hades hades 807 8月 4 2020 .profile
drwxr-xr-x 2 hades hades 4096 4月 17 2023 .Public
drwx--- 2 hades hades 4096 11月 1 11:08 .ssh
drwx--- 2 hades hades 4096 12月 19 00:23 .sunpinyin
drwxr-xr-x 2 hades hades 4096 8月 20 23:32 .Templates
drwxr-xr-x 2 hades hades 4096 7月 30 16:22 .themes
drwxr-xr-x 4 hades hades 4096 12月 19 01:42 Videos
-rw--- 1 hades hades 1678 10月 28 00:17 .viminfo
drwxr-xr-x 4 hades hades 4096 12月 18 23:02 'VirtualBox VMs'
drwxr-xr-x 3 hades hades 4096 12月 18 22:09 .vscode
-rw-r--r-- 1 hades hades 175 8月 6 20:50 .wget-hsts
-rw--- 1 hades hades 53 12月 19 07:06 .Xauthority
-rw--- 1 hades hades 48432 12月 19 23:04 .xsession-errors
-rw--- 1 hades hades 175069 12月 19 07:05 .xsession-errors.old
```

## 目录、文件的属性

```bash
d		rwx			r-x			---	25	hades	hades
目录	     读写执行	     读-执行



-		rw-		 r--	r--		1	   hades	  hades		kk
文件	     读写-	读--	   读--			用户		用户组		文件名


kk 这个文件，他的权限是：
对于 hades 用户而言，是可读、可写、可执行的
对于 hades 用户组里的成员来说，是只读的
对于其他用户（除了 hades 用户和 hades 用户组内的成员），是只读的


# 切换目录
cd 带上目录名称

# 判定文件是什么文件
file 带上文件名称

# 查看文本中的内容
cat 带上文本文件

# 编辑器查看文本呢内容
vim 带上文本文件

more 查看文本内容
less 查看文本内容
# 使用  `q` 退出查看状态
```

## 用户管理

```bash
# 查看用户

cat /etc/passwd

# root 用户？
类似win中的 administrator # 管理员账户

认定，linux passwd中可以登录的用户没几个，基本都是属于系统用户，无法登录系统
/bin/bash 的用户才能登录，/sbin/nologin 无法登录

能登录的：

root # administrator
hades # 普通用户，hades是普通用户，并不一定是这个名字，也可能是其他的，这是由自己定义的


# 创建用户

# 提升用户的权限  `sudo`
当处于普通用户下时，无法执行 root 用户才能执行的操作，需要使用 sudo 来提升权限执行操作

#sudo 有什么好处
防止手贱，执行删除操作的一道防线

sudo adduser admin # 提升执行权限，此时使用的是 root 用户来执行创建用户的操作


# 删除用户


# 切换用户

su - admin # 实现用户切换

linux系统从 `hades@hades-PC` -> `admin@hades-PC`

# 查看当前目录的位置（绝对路径）
pwd

# 如何设置密码

```

