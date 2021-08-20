[[+Leetcode practice reporter]]

[[009 Panlindrome number]]

# Regular Expression Matching
给你一个字符串 s 和一个字符规律 p，请你来实现一个支持 '.' 和 '*' 的正则表达式匹配。

'.' 匹配任意单个字符
'*' 匹配零个或多个前面的那一个元素
所谓匹配，是要涵盖 整个 字符串 s的，而不是部分字符串。

链接：https://leetcode-cn.com/problems/regular-expression-matching

-----
```
bool isMatch(char * s, char * p){

  你的代码将被镶嵌在这

}
```

-----

#### 代码
```
int i,j;
int lenth1=strlen(s),lenth2=strlen(p);
while(i<lenth1)
{
	if(j>=lenth2)return false;
	if(s[j]=='*')
	{
		j=j-1;
	}
	if(s[i]==s[j]||s[j]=='.')
	{
		i++;
		j++;
	}
	else
	{
		if(s[j+1]=='*') j=j+2;
		else return false;
	}
	
}
return true;
```

-----
