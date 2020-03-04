---
title: shell
date: 2020-03-04 21:06:27
tags:
	- shell
	- sh
	- 脚本
---
# for循环
### for1.sh
```shell script
#!/bin/bash 
for ((i=1;i<=5;i++))
do   
  echo $i >> test.txt
done
```
### for2.sh
```shell script
#!/bin/bash
for i in {a..z} {A..Z} {0..9}  # 可任意组合
do   
  echo $i >> test.txt
done
```
### for3.sh
```shell script
#!/bin/bash 
for i in `ls`
do   
  echo $i >> test.txt
done