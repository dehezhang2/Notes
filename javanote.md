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

| [] | type of characters |

| [^] | inverse of [] |

| ^ | start position |

| $ | end position |

| \b | words' boader |

| \w | word |

| \B | not words' boader |

| () | group(cluster by the expression) |

| \| | or |

| \\ | 转义 |

| \* | 0 or more times |

| \+ | 1 or more |

| ? | 0 or 1 |

| n | repeat |

* tool: QRe

### Regular expression in java

* package : java.util.regex

	* Pattern class, Matcher class

* Pattern class

	* spliter: use ',' '/' ' ' as seperator

	Pattern p = Pattern.compile("[,\\s]+"); // ',' || '\' || '\s'  1 or more

	String[] result = p. spilt("one,two,three,four,five");

	for(int i=0;i<result.length;i++)
		
		System.out.println(result[i]);

	* match(whether a string satifiies the format):
	> email: 

	String pattern = "^[^@]+@[\\w]+(\\.[\\w]+)*$" ; 

* Matcher class

get by the macher() method in Pattern object

	* method: find() //find next | appendReplacement() //replace 

	* group: () in the regular expression

		> group() or group(0) represent the whole cluster, group(1) group(2)... means every small () in ()

		> when replacing $0 is the whole cluster, $1 $2...means small () in ()














