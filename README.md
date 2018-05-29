# Shell-Script-Master
Some useful code for shell script

### Compare
```sh
#!/bin/bash

a=2462620
b=2462620

if [ "$a" -eq "$b" ];then
  echo "They're equal";
fi

-eq # equal
-ne # not equal
-lt # less than
-le # less than or equal
-gt # greater than
-ge # greater than or equal
```
### RAM used monitor
```sh
#!/bin/bash
freemem=$(free | grep Mem | awk '{print $4/$2 * 100}')
lamtron=${freemem//.*}
echo "$lamtron"
if [ $lamtron -le 30 ]; then
  #clear cache if RAM used greater than 70%
	sync; echo 3 > /proc/sys/vm/drop_caches
	#More info: https://geeksterminal.com/clear-cache-memory-cronjob-linux/698/
else
	echo "Working well"
fi
```
### Run script in background
```sh
sh your-script.sh &>/dev/null &
```
### Kill script is running in background
```sh
#insert this row at top of script after #!bin/bash, it will export PID in tmp folder
echo $$ > /tmp/nameofscript.pid
#kill script with PID
kill -9 PID
```
