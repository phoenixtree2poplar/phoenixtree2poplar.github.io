---
title: linxu服务器硬件信息
date: 2017-05-23 11:53:18
tags: 
	- linux-cpuinfo
	- cpu信息
	- linux硬件配置
---
```bash
cat /proc/cpuinfo  | grep name | cut -f2 -d: | uniq  #查看cpu名称
cat /proc/cpuinfo| grep "physical id"| sort| uniq| wc -l  # 查看物理CPU个数
cat /proc/cpuinfo| grep "cpu cores"| uniq  # 查看每个物理CPU中core的个数(即核数)
cat /proc/cpuinfo| grep "processor"| wc -l  # 查看逻辑CPU的个
free -m  #数查看内存
```
### 总核数 = 物理CPU个数 X 每颗物理CPU的核数 
### 总逻辑CPU数 = 物理CPU个数 X 每颗物理CPU的核数 X 超线程数