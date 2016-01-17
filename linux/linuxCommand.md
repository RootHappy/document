### 软件包管理器
- 安装库中的软件包（自动安装依赖的包）
	- Debian
		- apt-get update
		- apt-get install package_name
	- Red Hat
		- yum install package_name

- 安装软件包文件(不会自动安装依赖)
	- Debian
		- dpkg --install package_file
	- Red Hat
		- rpm -i package_file

- 删除软件包
	- Debian
		- apt-get remove package_name
	- Red Hat
		- yum erase package_name

- 更新库中的软件包
	- Debian
		- apt-get update
		- apt-get upgrade
	- Red Hat
		- yum update

- 更新本地软件包文件
	- Debian
		- dpkg --install package_file
	- Red Hat
		- rpm -U package_file

- 列出已经安装的软件包列表
	- dpkg --list
	- rpm -qa



### 网络

- ping: 向网络主机发送ICMP ECHO_REQUEST数据包,用来验证网络是否连通
	- ping baidu.com
- traceroute: 显示数据包到网络主机的路由路径(Ubuntu用tracepath)
	- traceroute/tracepath baidu.com
- netstat:检查网络设置和相关统计数据
	- netstat -ie ：查看系统中的网络接口信息
	- netstat -r : 显示内核的网络路由表
- ftp:采用文件传输协议（FTP）传输文件，与FTP服务器进行通信
- lftp:更好的ftp
- wget:非交互式网络下载工具
	- wget http://baidu.com
- ssh:安全登录远程计算机
	- ssh wangyunlong@127.0.0.1
- scp:远程复制命令
	- scp document/LinuxCommandLine.md wangyunlong@127.0.0.1:/home/wangyunlong
	- scp wangyunlong@127.0.0.1:/home/wangyunlong/document/LinuxCommandLine.md .
- sftp:

### 文件搜索

- locate:通过文件名查找文件
	- locate name ----(通过快速搜索数据库，以寻找路径名与给定子字符串相匹配的文件)
- find: 在文件系统目录框架中查找文件
	- find dir_name -type file_type
    | 文件类型 | 描述 |
    |:----:|:----|
    | d | 目录 |
    | f | 普通文件 |
    | l | 符号链接 |
    | c | 字符设备 |
    | b | 块设备  |
	- find dir_name -name file_name
	-  find fir_name -size n（+ 大于给定n, -小于给定n 默认等于给定n）

	| 字母 | 描述 |
    |:----:|:----|
	| b | 512字节的块（默认值） |
    | c | 字节 |
    | w | 两个字节的字 |
    | k | KB |
    | M | MB |
    | G | GB |

	- 预定义动作

	| 动作 | 描述 |
    |:---:|:----|
    | -delete 	| 删除匹配的文件 |
    | -ls  		| 对匹配文件执行ls操作|
    | -print 	| 将匹配的文件的全路径以标准的形式输出。默认 |
    | -quit 	| 一旦匹配成功就退出 |


- xargs:从标准输入中建立，执行命令行
- touch:更改文件的日期时间
- stat:显示文件或文件系统的状态

### 归档和备份

- 文件压缩程序
	- gzip: 压缩文件工具 （源文件会被压缩文件替换）
		- gzip file_name   压缩文件
		- gzip -d file_name_gz		解压缩文件
		- gzip -l file_name_gz		列出压缩文件内容
		- gzip -r file_name			递归压缩
		- gzip -tv file_name_gz		压缩文件的完整性
	- gunzip:解压缩文件工具（将压缩文件还原成源文件）
		- gunzip file_name_gz
		- gunzip -c file_name_gz 	查看压缩文件的内容
	- bzip2:块排序文件压缩工具,与gzip用法类似
	- bunzip2:解压缩工具
- 文件归档程序
	- tar: 磁带归档工具
		- tar cf file.tar pathname/
		- tar xf file.tar
		- tar tf file.tar
		- tar tvf file.tar
		- tar czf file.tar.gz pathname
		- tar xzf file.tra.gz
		- tar cjf file.tar.bz pathname
		- tar xjf file.tar.bz

        | 模式 | 描述 |
        |:----:|:----|
        | c | 创建文件或目录列表的归档文件 |
        | x | 从归档文件中提取文件 |
        | t | 列出归档文件中的内容 |
        | r | 列出归档文件的内容 |
        | f | 制定归档文件名 |
        | v | 列出详细的归档文件内容 |
        | z | 代表使用gzip压缩和解压缩 |
        | j | 代表使用bzip2压缩和解压缩 |

	- zip: 打包和压缩文件
	- unzip:
- 文件同步程序
	- rsync: 远程文件和目录的同步
		- rsync -av source destionation


### 存储介质

- 在/var/log/messages中可以查看到设备名，来手动挂载（ubuntu目录是：/var/log/syslog）

- mount: 挂载文件系统
	- mount 查看已挂载的文件系统列表
	- mount /dev/xxx /mnt/xxx
	- mount -t iso9660 -o loop image.iso /mnt/xxx
- unmount:卸载文件系统
	- umount /dex/xxx
- fdisk: 硬盘分区命令
- fsck:检查修复文件系统
- mkf: 创建文件系统
- dd:向设备直接写入面向块数据