###linux命令

- who ：show who is logged on
- wc : print newline,word,and byte counts for each file
- wf
- pwd
- cd
- ls
- ll
- echo
- cat
- tr
- stty
- echo
- printf
- read
- grep : print lines matching a pattern(匹配文本)
- locale
- sed(Stream Editor)流编辑器
- find
- cut
- join
- awk
- sort
- uniq
- od -a -b
- fmt
- head
- tail
- dd
- strings
- file
- man 5 passwd
- umask 077
- cal
- top
- ps aux
- kill PID
- killall process-name
- export
- id
- chmod
- chgrp
- chown
- passwd
- su
- ps
- top
- jobs
- bg
- fg
- kill
- killall
- shutdown
- pstree

---------------------------
- 获取文件开头结尾指定行数
	- 开头n行
		- head -n 5 fileName
		- head -5 fileName
		- sed -e 5q fileName
		- sed 5q fileName
		- awk 'FNR <= 5' fileName
	- 结尾n行
		- tail -n 5 fileName
		- tail -5 fileName
---------------------------
- 重定向
	- "<" 改变标准输入
	- ">" 改变标准输出
	- ">>" 重定向追加数据
---------------------------





command & ->>>>后台执行，Shell不用等该命令执行完成，就可执行下一条命令
Ctrul+D 文件结尾