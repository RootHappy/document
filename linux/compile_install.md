### 编译源代码-安装

- 需要工具 gcc make等程序
- 获取源代码

```
$ ftp ftp.gnu.org
Connected to ftp.gnu.org.
220 GNU FTP server ready.
Name (ftp.gnu.org:wangyunlong): anonymous
ftp > cd gnu/diction
ftp > ls
ftp > get diction-1.11.tar.gz
ftp> bye

```
- 解压下载的文件 （tar zxf diction-1.11.tar.gz）
- 进入目录执行 ./configure
- 键入： make
- 键入: sudo make