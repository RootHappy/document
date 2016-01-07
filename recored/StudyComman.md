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
		- ［－１］：每行列出一个文件







- 目录栈
	- pushd .
	- popd .