# Markdown的正确打开方式

* [Header](#1)
* [referance](#2)
* [Emphasize](#3)
* [Import](#4)
* [Others](#5)

<h2 id = "1"> 1. Header </h2>

This is an h1
=============
	This is an h1
	=============
	or
	# //space + This is an h1

This is an h2
-------------
	This is an h2
	-------------

<h2 id = "2" >2. reference </h2>

>This is referance

	>This is referance
	//one space line for next text

<h2 id = "3" >3. Emphasize</h2>

### (1) Bold

**I am important**

	**I am important**
	//also a space line

### (2) Italic

*I am Italic*

	*I am Italic*

### (3) Underline

<u>emmm important</u>

	<u>emmm important<\u>

### (4) Delete

~I am sorry I am wrong~

	~I am sorry I am wrong~
<h2 id = "4">4. Import</h2>

### (1) link

[Where did I learn a about this damn thing ?](https://www.jianshu.com/p/e4a544741fe0)

	[Where did I learn a about this damn thing ?](https://www.jianshu.com/p/e4a544741fe0)

### (2) pictures

![baidu search](https://www.baidu.com/img/bd_logo1.png))

	![baidu search](https://www.baidu.com/img/bd_logo1.png))

### addjusted picture

<div align="center"><img width="65" height="75" src="https://raw.githubusercontent.com/mzlogin/mzlogin.github.io/master/images/posts/markdown/demo.png"/></div>

	<div align="center"><img width="65" height="75" src="https://raw.githubusercontent.com/mzlogin/mzlogin.github.io/master/images/posts/markdown/demo.png"/></div>

## 4. List

### (1) ordered list
1. insertion
2. merge
3. buble

-----
	1. insertion
	2. merge
	3. buble

### (2) unordered list

- int
- double
- char

-------
	- int
	- double
	- char
<h2 id ="5">5. Others</h2>

### (1) Segamentation

paragraph1

paragraph2

	paragraph1
	//space line
	paragraph2
	
###  (2) Divid line

***
___

	***
	___
### (3) Block

	dffasdfd
	asdfasdfs
	//tab + dffasdfd
	//tab + asdfasdfs

### (4) inline-block

Use the recursive `merge()` function

	Use the recursive `merge()` function

### (5) Table

| Header1 | Header2                          |
|---------|----------------------------------|
| item 1  | 1. one<br/>2. two<br/>3. three |

	| Header1 | Header2                          |
	|---------|----------------------------------|
	| item 1  | 1. one<br />2. two<br />3. three |
### (6) emoji
:smile:

	:smile:

### (7) 行首缩进

&emsp;&emsp;fuck

	&emsp;&emsp;fuck
### (8) Math formula

[在 Github.Page渲染数学公式](http://wanguolin.github.io/mathmatics_rending/)

[贴图]( https://www.codecogs.com/latex/eqneditor.php) 网页上部的输入框里输入 LaTeX 公式，比如 `$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$`
![效果](https://raw.githubusercontent.com/mzlogin/mzlogin.github.io/master/images/posts/markdown/latex-img.png)
![](https://latex.codecogs.com/png.latex?%24%24x%3D%5Cfrac%7B-b%5Cpm%5Csqrt%7Bb%5E2-4ac%7D%7D%7B2a%7D%24%24)

	![](https://latex.codecogs.com/png.latex?%24%24x%3D%5Cfrac%7B-b%5Cpm%5Csqrt%7Bb%5E2-4ac%7D%7D%7B2a%7D%24%24)
### (9) Task list

**list**

- [ ] 一次性水杯
- [x] 西瓜
- [ ] 豆浆
- [x] 可口可乐
- [ ] 小茗同学

	```**list**
	```- [ ] 一次性水杯
	```- [x] 西瓜
	```- [ ] 豆浆
	```- [x] 可口可乐
	```- [ ] 小茗同学