## Ubuntu 14.04 install Application

### Sogou Input method
- sudo apt-get update
- sudo apt-get install fcitx
- download sogou deb package {http://pinyin.sogou.com/linux/}
- open fcitx-configuration to add sogou

### Haroopad(A markdown editor)
- download Haroopad {http://pad.haroopress.com/user.html}
- install deb package

### Install chrome Browser
- Search Chrome in Ubuntu Software Center
- install it

### Install Git and Configuration
- sudo apt-get install git
- git config --global user.name xxx
- git config --global user.email xxx
- ssh-keygen -t rsa -C "your email"

### Install SSH-Server
- sudo apt-get install openssh-server

### Install Mysql
- http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/
- Adding the MySQL APT Repository
	- download the MySQL APT repository
		- http://dev.mysql.com/downloads/repo/apt/
	- Install the downloaded release package
		- sudo dpkg -i mysql-apt-config_w.x.y-z_all.deb
	- Update package information from the MySQL APT repository
		- sudo apt-get update

- Installing MySQL with APT
	- sudo apt-get install mysql-server
		- This installs the package for the MySQL server, as well as the packages for the client and for the database common files.
	- Supply a password for the root user for your MySQL installation.

- Starting and Stoping the Mysql Server
	- sudo service mysql status
	- sudo service mysql stop
	- sudo service mysql start
