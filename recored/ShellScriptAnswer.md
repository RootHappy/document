### Answer to Variable sections exercise

- Q.1.How to Define variable x with value 10 and print it on screen.
```
$ x=10
$ echo $x
```
- Q.2.How to Define variable xn with value Rani and print it on screen
```
$ xn=Rani
$ echo $xn
```
- Q.3.How to print sum of two numbers, let's say 6 and 3
```
$ echo 6 + 3
This will print 6 + 3, not the sum 9, To do sum or math operations in shell use expr, syntax is as follows:
Syntax: expr   op1   operator   op2
Where, op1 and op2 are any Integer Number (Number without decimal point) and operator can be(+ Addition,- Subtraction , * Multiplication , / Division, % Modular)
$ expr 6 + 3
Now It will print sum as 9 , But
$ expr 6+3
will not work because space is required between number and operator (See Shell Arithmetic)
```
- Q.4.How to define two variable x=20,y=5 and then to print division of x and y
```
$ x=20
$ y=5
$ expr $x / $y
```
- Q.5.Modify above and store division of x and y to variable called z
```
$ x=20
$ y=5
$ z=`expr $x / $y`
$ echo $z
```
- Q.6.Point out error if any in following script
```
$ vi   variscript
#
#
# Script to test MY knolwdge about variables!
#
myname=Vivek
myos   =  TroubleOS    -----> ERROR 1
myno=5
echo "My name is $myname"
echo "My os is $myos"
echo "My number is   myno,   can you see this number"  ----> ERROR 2
```
Following script should work now, after bug fix!
```
$ vi   variscript
#
#
# Script to test MY knolwdge about variables!
#
myname=Vivek
myos=TroubleOS
myno=5
echo "My name is $myname"
echo "My os is $myos"
echo "My number is   $myno,   can you see this number"
```

### Shell Built in Variables

| Shell Built in Variable  | Meaning |
|:-------:|:---:|
| $#  | Number of command line arguments.Useful to test no. of command line args in shell script |
| $* | All arguments to shell  |
| $@ | 	Same as Above   |
| $-  | Option supplied to shell |
| $$  | PID of Shell  |
| $!  | PID of last started background process |
| $? | Exit Status|

### System Variables in Shell

| System Variable | Meaning |
|:-------:|:---:|
| BASH | Our shell name |
| BASH_VERSION | Our shell version name |
| COLUMNS | No. of columns for our screen |
| LINES | No. of lines for our screen |
| HOME | Our home directory |
| LOGNAME | Our logging name |
| OSTYPE | Our Os type |
| PWD | Our current working directory |
| PS1 | Our prompt settings |
| SHELL | Our shell name|
| USERNAME | User name who is currently login to this PC |

