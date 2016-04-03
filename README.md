#### psredhatentlinuxshscrfunda
#####script execu
######sourcing script
example:
in terminal:
```
> var="var"
```
test.sh
```
echo var
```
we must run
```
. ./test.sh
```
to get var.  

Or:  
test.sh
```
read -p "please type"
echo $REPLY
```
in shell
```
echo $REPLY  //empty
```
we must run
```
. ./test.sh
```
to make $REPLY available in shell




######referencing var
using double quotes for string. If using single quote, vars like $var will print literally

######more on position parameter
```
shift
```
this just shift left parameters
```
$# total number of args
$@ all args as a list
$* all args in a single value
```

#####getting user input
######intro to read command
```
read -p "please input" var1
echo "$var1"
```
######more options
limit max char
```
read -n1 p "only allow 1 char"
```
slient mode, do not print on screen
```
read -sn1 p "only allow 1 char"
```
######REPLY
if we donot assign value in read command, it will save in $REPLY

###### multiple values
```
read -p "enter" var1 var2 var3
```
#####conditional
######
```
#!/bin/bash
if[[$# -eq 0]]; then
```
same as
```
if[[$# -eq 0]]    //Or  if["$#" -eq 0]
then
```

######check arg
basename command
```
(basename $0)
```
######check file exists
```
filename = "$1"
if [ -e "$filename"];then
else
fi
```
######case
```
check = $(file $1 |cut -d " " -f 2)
case $check in
"ASCII")
echo "xx"
;;
esac
```

#####loops
######
```
for i in 1 2 "done";do
echo $i
done
```
######enhancing
```
for i; do
check = $(file $1 |cut -d " " -f 2)
case $check in
"ASCII")
echo "xx"
break
;;
*)
echo 'wrong'
;;
esac
shift
done
```
call
```
./test.sh a.txt b.txt
```
each time the leftest one will be removed.  
######while /until
```
while [$count -gt 0 ];do
let count = $count-1
done
```
#####menus
######first simple
```
var = "a b c"
select x in $x; do

done
```

$REPLY is digit. x is always actual value in var list.

######cron
```
vim /etc/cron.d/weekly-bins
```
#####troubleshooting
######exit
exit status=2 not root  
exit status=3 no args
exit status= out of disk space
######xtrace
```
bash +x ./xxx.sh
```
```
set +x   (xtrace on)
set -x    (xtrace off)
```
