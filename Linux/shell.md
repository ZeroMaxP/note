### shell script

![1531995889245](shell.assets/1531995889245.png)

```shell
1
echo "Hellow World"
exit 0

2
 read -p "Please input your score:" score
if [ $score -ge 90 ];then
        echo "A"
elif [ $score -ge 70 ];then
        echo "B"
elif [ $score -ge 60 ];then
        echo "C"
else
        echo "D"
fi


3
i=1
sum=1
while [ $i -ne 6 ]
do
        sum=$(($sum*$i))
        i=$(($i+1))
done
echo "5!=$sum"


```

###top & kill 命令

![1531995668278](shell.assets/1531995668278.png)

![1531995683290](shell.assets/1531995683290.png)





