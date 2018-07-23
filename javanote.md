# Java Note

<h2 id ="9">week 9</h2>

### Recite(word list)

* Point: 
	
	* file io
	* string manipulate
	* collection
	* Thread Timer
	
### File

* File class
	
	File f = new File(String(filename));

	File f = new File(String(filepath),String(filename));

	File f = new File(File(new File(pathname)),String(filename));
	
	String[] list = dir.list(); //get the list of a path(File dir)

	> paths are treated as file
	

### Regular expression(匹配验证，分割，查找，替换 字符串)

	字符{数量}位置

	[0-9]{2,4}\b	//0 to 9 character exists 2 to 4 times at board

* import 

| character | meaning |
|---------|----------------------------------|
| . | characters besides enter|
|---------|----------------------------------|
| [] | type of characters |
|---------|----------------------------------|
| [^] | inverse of [] |
|---------|----------------------------------|
| ^ | start position |
|---------|----------------------------------|
| $ | end position |
|---------|----------------------------------|
| \b | words' boader |
|---------|----------------------------------|
| \B | not words' boader |
|---------|----------------------------------|
| () | group(cluster by the expression) |
|---------|----------------------------------|
| \| | or |
|---------|----------------------------------|
| \\ | 转义 |
|---------|----------------------------------|
| \* | 0 or more times |
|---------|----------------------------------|
| \+ | 1 or more |
|---------|----------------------------------|
| ? | 0 or 1 |
|---------|----------------------------------|
| n | repeat |
|---------|----------------------------------|


* tool: QRe








