	
```java
public static int kmp(String s, String p) {  
	int sLen = s.length();  
	int pLen = p.length();  
	s = " " + s;  
	p = " " + p;  
	char[] ss = s.toCharArray();  
	char[] pp = p.toCharArray();  
	int[] next = new int[pLen + 1];  
	//创建前缀数组  
	//next[i]的含义:先判断第i个字母与前面的字母(要连续)能否凑成从第一个字符开始的前缀  
	//如果可以,则next[i]就是该字符所在前缀的位置  
	//如果不可以,跳到上一个前缀匹配位置,匹配上一个前缀其它可能  
	for (int i = 2, j = 0; i < next.length; i++) {  
		//i是用于更新每个位置它是否为前缀的一部分,如果是,那么它在哪个位置  
		//j是维护前缀长度,用于判断i所在字母的前缀位置  
		while (j > 0 && pp[j + 1] != pp[i]){  
			j = next[j];  
		}  
		if (pp[j + 1] == pp[i]){  
			j++;  
		}  
		next[i] = j;  
	}  
 
	//从s的第一个字母开始  
	for (int i = 1, j = 0; i < ss.length; i++) {  
		//如果已经匹配的位置的下一个位置与原串不匹配,那么就跳到这个匹配前缀的上一个  
		//可以理解为匹配串往前移动  
		while (j > 0 && ss[i] != pp[j + 1]){  
			j = next[j];  
		}  
		//j指向的是 已经 匹配的匹配串位置  
		if (ss[i] == pp[j + 1]){  
			j++;  
		}  
		//匹配串已经完全匹配完毕  
		if (j == pLen){  
			return i - pLen;  
		}  
	} 
	return -1;  
}

```