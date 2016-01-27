# The Linux Command

[TOC]

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
		- zip -r filename.zip pathname
	- unzip:
		- unzip filename.zip -d dest
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

### 正则表达式
- grep 文本搜索（Global Regular Expression Print）
	- grep [options] regex [file...]

    | 选项 | 描述 |
    |:---:|:---|
    | -i | 忽略大小写 |
    | -v | 输出不包含匹配的行 |
    | -c | 输出匹配的多少行|
    | -n | 输出匹配的行在文件中的行号 |
    | -l | 不输出匹配的行，输出匹配的文件名 |
    | -L | 输出的是没匹配到的文件 |

- 正则表达式元字符^ $ . [ ] { } - ? * + ( ) | \
	- 匹配任意字符 .
	- 匹配行开头和末尾 ^ $ -----------------(^$匹配空行)

- POSIX字符类
| 字符类 | 描述 |
|:-----:|:----|
| [:digit:] | 数字0-9 |
| [:alpha:] | 字母字符 |
| [:lower:] | 小写字母 |
| [:upper:] | 大写字母 |
| [:alnum:] | 字母字符和数字字符 |
| [:word:] | 与[:alnum:]类似，只多一个下划线(_) |
| [:blank:] | 空格和制表符 |
| [:space:] | 空白字符 |

- 扩展的正则表达式
	- | 或选项
	- ？ 匹配某个元素0次或1次
	- \* 匹配某个元素多次或0次
	- \+ 匹配某个元素一个或多次
	- {} 指定匹配某个元素的次数 {n},{n,m},{n,}{,m}

### 文本处理
- 文本命令总览：
    - cat: 连接文件并打印到标准输出
    - sort: 对文本行排序
    - uniq: 通知或者省略重复的行
    - cut : 删除文本行中的部分内容
    - paste: 合并文本行中的每列元素
    - join: 连接两个文件中具有相同字段的行
    - comm: 逐行比较两个已排序文件
    - diff: 逐行比较文件
    - patch: 对原文件打补丁
    - tr: 替换或者删除字符
    - sed: 用于文本过滤和转换的流编辑器
    - aspel:

- cat 详解
	- cat file1 file2		连接file1和file2，输出到标准输出
	- cat > file_name		标准输入，存入文件file_name中
	- cat -A file_name		打印file_name到标准输出，可显示文本中的非打印字符
	- cat -n file_name		打印带行号的输出
	- cat -s file_name 		禁止输出多个空白行

- sort 详解
	- 对标准输入或命令行中指定的一个或多个文件排序结果送到标准输出
	- du -s /usr/share/* | sort -nr | head
	- ls -l /usr/bin | sort -nr -k 5 | head
	- ls -l ~ | sort -k 5,5nr -k 9
	- sort -k 3.7nbr -k 3.1nbr -k 3.4nbr file_name
	- sort -t ':' -k 7 /etc/passwd | head

    | 选项 | 描述 |
    |:---:|:---|
    | -b | 忽略行开头空格，从第一个非空白字符开始排序 |
    | -f | 不区分字母大小写 |
    | -n | 按照数值顺序排序 |
    | -k | 选择排序的列 |
    | -r | 逆序 |
    | -o | 输出排序结果到文件而不是标准输出 |
    | -m | 多个排序好的文件合并为一个 |
    | -t | 定义字段分割符 |

- uniq 通知或省略重复的行
	- 只对排序好的文件，去除重复的行
	- sort foo.txt | uniq
	- sort foo.txt | uniq -c

    | 选项 | 描述 |
    |:---:|:---:|
    | -c | 去除重复行，在行首增加重复次数 |
    | -d | 只输出重复行 |
    | -i | 行与行之间比较时忽略大小写 |
    | -u | 仅输出不重复的行 |
    | -s n | 跳过每行的前n个字符 |
    | -f n | 跳过每行前n个字段，字段之间空格分割 |

- cut 删除文本行中的部分内容
	- cut命令用于从文本行中提取一段文字并将其输出至标准输出。（单个tab分割的列）
	- cut -d ':' -f 1 /etc/passwd | head
	- cut -f 3 file_name
	- cut -c 3-5 file_name

    | 选项 | 描述 |
    |:---:|:---|
    | -f field_list | 文本行中提取列 |
    | -d delim_char | 指定-f选项后，用来指定分解符，默认是单个tab|
    | -c | 从文本行中提取char_list指定的部分内容 |

- join 连接两个文件中具有相同字段的行
	- 基于共享关键字段将多个文件的数据拼接在一起的操作
	- 默认已空格分割，必须已共享字段进行排序后的文档
	- 共享列在第一个位置

- comm 逐行比较两个已排序的文件
	- 比较的文件已经排序
	- 输出三列内容，分别是：第一个文件中的独有行，第二个文件中独有行，两个文件的共同行
	- comm file1 file2
	- comm -12 file1 file2 省略第一二列

- diff 逐行比较文件
	- 默认格式 （范围 执行操作 范围）
	- 上下文格式 diff -c file1 file2
	- 统一格式 diff -u file1 file2

```
#默认格式
1d0
< a
4a4
> e

#上下文格式
*** file1.txt	2016-01-21 14:49:02.112095455 +0800
--- file2.txt	2016-01-21 14:49:21.284094888 +0800
***************
*** 1,4 ****
- a
  b
  c
  d
--- 1,4 ----
  b
  c
  d
+ e

#上下文格式
--- file1.txt	2016-01-21 14:49:02.112095455 +0800
+++ file2.txt	2016-01-21 14:49:21.284094888 +0800
@@ -1,4 +1,4 @@
-a
 b
 c
 d
+e
```

- patch 对原文文件进行diff操作
	- 用于更新文本文件，利用diff命令的输出结果将旧版本的文件升级成新版本
	- 生成补丁文件：diff -Naur ole_file new_file > diff_file
	- patch < diff_file

- tr 替换或者删除字符
	- 基于字符的查找和替换操作
	- echo "wang" | tr a-z A-Z
		- 枚举列表 ABCDEFGHIJ.....
		- 字符范围 A-Z
		- POSTX字符类 [:upper:]
	- echo "wang" | tr -d w   删除字符
	- tr -d '\r' < dos_file > linux_file
	- echo "aaabbbcc" | tr -s ab		去除重复的字符

- sed 用于文本编辑和转换的流编辑器
	- sed中的命令总是以单个字母开头
		- s : 替换
		- p : 打印
		- d : 删除当前行
		- i : 在当前行前输入文本
		- a : 在当前行后附加文本
		- = : 输出当前行号
		- q :退出sed不在处理其他行
		- y/set1/ser2 ： 将字符集set1转换成set2
		- s/regexp/replacement/ 替换regexp匹配的文本替换成replacement
	- echo "front" | sed 's/front/back/'		替换front->back
	- sed -n '1,5p' foo.txt			打印前五行
	- sed -n '/a/p' foo.txt 		打印匹配正则表达式的行
	- sed 's/\([0-9]\{2\}\)\/\([0-9]\{2\}\)\/\([0-9]\{4\}\)$/\3-\1-\2/' date.txt		MM/dd/yyy 转换成yyyy-MM-dd
	- echo "aaabbbcc" | sed 's/b/B/g'
    - 地址表示法:
        - N :正整数表示行号
        - $	:最后一行
        - n1,n2 : n1-n2的所有行
        - addr,+n : addr和后面的n行
        - addr! : 排除addr后的n行
        - addr~step : 从first开始，step为间隔的行
        - /regexp/ :匹配正则表达式的行


### 格式化输出

- nl:对行进行编号
- fold: 将文本中的行长度设定为指定长度
	- fold -w n file
	- fole -w n -s file
- fmt:简单的文本格式化工具
- pr: 格式化打印文本
- printf:
- grof:






