### 2016-01-07
- cd: [ Change Directory ]

	| Command | Description |
	|:-------:|:------------|
	| cd / cd ~ | 回到用户目录 |
	| cd . | 回到当前工作目录 |
	| cd .. | 回到当前目录的上级目录 |
	| cd - | 回到上次工作目录 |
	| cd path | 回到指定路径(绝对/相对) |

- pwd: [ Print the full filename of the current working directory ]
	- [ -P ] : 符号连接显示指向的目录
	- [ -L ] : 符号连接显示当前符号目录

- which comman:[ locate a command ]
	- [ -a ]:print all matching pathnames of each argument

- ls: [ List Directory Contents]
	- 语法: ls [ option ] [ File ]（默认列出当前目录文件列表）
	- option :
		- [ -a ]:列出所有文件,包含以.开头的隐藏文件
		- [ -A ]:列出所有文件,包含以.开头的隐藏文件,不包含．和 ..
		- [ -1 ]：每行列出一个文件
		- [ -l ]:列出文件/目录的所有信息
		- [ -t ]:修改时间排序,最新的排在前面
		- [ -S ]:大小排序
		- [ -r ]:反转排序
		- [ -h ]:with -l, print sizes in human readable format (e.g., 1K 234M 2G)
		- [ -d ]:with -l,查看当前目录的信息R
		- [ -R ]:	list subdirectories recursively
		- [ -F ]:在目录后追加 @ – link file. / – directory. * – Executable file
		- [ -i ]:显示节点
		- [ -n ]:打印文件的UID,GID

### 01-08

- Manipulating Files Commnads
	- cp [ copy files and directories ]
		- copy files in current directory: cp source_name dest_name
		- copy files to dest dirextory: cp source_name... dest_path
		- copy directory: cp -r source_dir dest_dir
	- mv [move (rename) files ]
		- rename files : mv source_name dest_name
		- move files : mv source_name dest
	- rm [ remove files or directory ]
		- [ -d ]: remove empty directories
		- [ -r ]: remove directories and their contents recursively
		- [ -f ]: ignore nonexistent files and arguments,never prompt
		- [ -i ]: prompt before every removal
	- mkdir [ Make directories ]
		- [ -p ]: 如果目录存在不报错,可创建层次目录
		- [ -m ]: -m=rwx 设置目录模式







- 目录栈
	- pushd .
	- popd .






- Unix LS Command: 15 Practical Examples:
	- http://www.thegeekstuff.com/2009/07/linux-ls-command-examples/