## Shell Script

- Shell 脚本是一个包含一系列命令的文件，Shell既是一个强大的命令行接口，也是一个脚本语言解释器
- 如何编写Shell
	- 编写脚本文件
	- 使脚本文件可执行
	- 将脚本文件放置在Shell能够发现的位置

- 脚本文件的格式

    ```Bash
    #！/bin/bash

    #This is our first script.

    echo 'Hello World.'
    ```

- 行连接符 （反斜杠+回车符序列）

### Shell 基础语法

- 创建变量和常量
	- variable=value
	- 在赋值时，变量名、等号和值之间不能含有空格
	- 通常用大写字母表示常量，使用小写字母表示变量
	- 变量的命名规则
		- 变量名称应由字母、数字和下划线组成
		- 变量名称的第一个字符必须是字母或者下划线
		- 变量名称中不允许空格和标点
	- 变量引用方式 （$variable || ${variable}）
	- 局部变量：仅仅在定义的函数中有效 （local variable=value）

- Shell 函数

```
function name {
	commands
    return
}

name(){
	commands
    return
}
```

- IF分支语句
	- 退出状态（0-255）
		- 数值0表示命令执行成功，其他数值表示执行失败
		- $? :检测退出状态的参数
	- test 命令
		- test expression
		- [ expression ]

测试文件表达式

| 表达式 | 描述 |
|:---:|:---|
| -b file | file存在并且是一个块（设备）文件|
| -c file | file存在并且是一个字符（设备）文件|
| -d file | file存在并且是一个目录|
| -f file | file存在并且是一个普通文件|
| -e file | file存在 |
| -L file | file存在并且是一个符号|
| -r file | file存在并且可读 |
| -w file | file存在并且可写 |
| -x file | file存在并且可执行 |
| -s file | file存在并且长度大于0 |

测试字符串表达式

| 表达式 | 描述 |
|:---:|:----|
| string 	| string 不为空 |
| -n string | string的长度大于0 |
| -z string | string的长度等于0 |
| string1 == string2 | string1 等于string2 |
| string1 != string2 | string1 不等于string2 |
| string1 > string2 | 在排序时，string1在string2之后 |
| string1 < string2 | 在排序时，string1在string2之前 |

整数判断操作

| 表达式 | 描述 |
|:-----:|:----|
| integer1 -eq integer2 | 等于 |
| integer1 -nq integer2 | 不等于 |
| integer1 -le integer2 | 小于等于 |
| integer1 -lt integer2 | 小于 |
| integer1 -ge integer2 | 大于等于 |
| integer1 -gt integer2 | 大于 |

```
if commands; then
	commands
[elif commands; then
	commands...]
[else
	commands]
fi
```

- 读取键盘输入
	- read 从标准输入读取输入值
	- read [-option] [variable...] 如果没有变量名，则存储在REPLY

| 选项 | 描述 |
|:----:|:----|
| -p prompt | 使用prompt字符串提示用户进行输入 |
| -s | 保密模式，不在屏幕显示输入的字符。|
| -u fd | 从文件说明符fd读取输入，而不是从标准输入中读取 |
| -t seconds | 超时 |
| -d delimiter | 用字符串delimiter作为字符结束的标志 |
| -a array | 将输入值从索引为0的位置开始赋给array |

- 流控制 While 和 until 循环
	- while非0退出循环
		- while commands; do commands; done
	- break
	- continue
	- until与while类似，0退出循环

- case分支

```
case word in
	[pattern][|pattern]...) commands;;....
esac

a)				若关键字为a则吻合
[[:alpha:]])	若关键字为单个字母则吻合
???)			若关键字为三个字符则吻合
*.txt)			若关键字以.txt结尾则吻合
*)				与任何关键字吻合

可组合多个模式

```


- for循环
	- for:传统Shell形式
	- for:C语言形式

```
for variable [ in words];do
	commands
done

for i in A B C D; do echo $i; done		序列
for i in {A..D}; do echo $i; done		花括弧扩展
for i in distros*.txt; do echo $i; done		路径扩展

for (( expression1; expression2; expression3 )); do
	commands
done

```

- 位置参数
	- $0 $1...$9 ${11}..${123}
	- $# : 命令行参数个数，不包含$0
	- shift 参数移位操作
	- $* / $@: 获取所有位置参数，空格分割，引号内也会按照空格分割
	- "$*" ：双引号引用的全部位置参数构成的字符串
	- "$@" : 常用，符合期望，将每个位置扩展为双引号引用

- 参数扩展
	- $variable
	- ${variable}
	- ${variable:-"default value"}
	- ${variable:="default value"} 默认值会赋值给variable
	- ${variable:?word} ：如果variable未设定或为空，出错而退出，如果非空则扩张variable
	- ${variable:+word}
	- 返回变量名
		- ${!prefix*} :返回当前以prefix开头的变量名。
		- ${!prefix@} :返回当前以prefix开头的变量名。

- 字符串操作
	- ${#parameter} :parameter包含的字符串的长度
	- ${parameter:offset} 子串，如果offset为负，从末尾开始，切前面必须有空格
	- ${parameter:offset:length} length不能小于0
	- ${parameter#pattern}:去除parmater开头中匹配pattern的部分（最短）
	- ${parameter##pattern}去除parmater开头中匹配pattern的部分（最长）
	- ${parameter%pattern}：去除parmater末尾中匹配pattern的部分（最短）
	- ${parameter%%pattern}:去除parmater末尾中匹配pattern的部分（最长）
	- ${parameter/pattern/string} :替换第一个出现与pattern匹配的值为string
	- ${parameter//pattern/string}:替换所有与pattern匹配的值为string
	- ${parameter/#pattern/string}:替换开头与pattern匹配的值为string
	- ${parameter/%pattern/string}:替换末尾与pattern匹配的值为string

- 算术操作
	- $(())
	- 运算符
		- \+ : 加法
		- \- : 减法
		- \* : 乘法
		- /  : 除法
		- \**: 求幂
		- %  : 取模

- 数组
	- 创建数组 declare -a array_name	// a[1]=value
	- 数组赋值
		- 单个：name[subscript]=value
		- 多值：name=(value1,value2...)
	- 访问数组
	- 输出数组中所有元素：
		- for i in ${array[*/@]};do echo $i; done
		- for i in "${array[*/@]}";do echo $i; done
	- 数组元素的数目 ${#array[@]}
	- 数组结尾增加元素 array+=(vaule1 value2 value3)
	- 数组删除 ： unset array //// unset 'array[1]'






