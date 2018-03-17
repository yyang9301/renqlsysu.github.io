---
layout: post
title: ncl文件的输入与输出
categories: ncl
tags: ncl 整理
author: renql
---

* content
{:toc}

# 输出数据到ASCII文件
1. write_matrix 输出二维数据   
```
	opt 		= True
	opt@fout 	= "文件路径"
	opt@title 	= "输出内容的标题"
	opt@tspace  = "标题左边的空格数"
	opt@row 	= True 			;表示会打印行数，若为False则不打印行数
write_matrix(data,fmtf,opt)		;data只能是二维的，fmtf是打印的格式如"9f12.6"
```




2. write_table 输出规则列表
```
	write_table(filename,option,alist,fmtf)
	;option有两种，"w"指重新写，如之前有内容，会覆盖；"a"是接着之前的内容往下写
	;alist是要写的数据，若有a = (/"ab","bc","cd"/),b = (/1,2,3/),alist = [/a,b/],会输出三行两列的数据
	;fmtf必须对输出的每一列数据进行格式规定，不能用"7f12.6"这样的方式重复，且表述方式也与上述不同，如"%d%16.2f%s%d%ld"表示输出整数、小数、字母、整数、整数
```

# 输出数据到二进制文件，可用Fortran读取
1.  直接写入二进制文件，类似于fortran中的"form=unformatted,access=direct"
```
fbindirwrite(path,var)  ;var可以是任意维度,若写入的数据文件之前就存在，新写入的数据将写在后面，而不是覆盖
```