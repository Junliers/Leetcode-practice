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

#### 代码1(F)
```
int i=0,j=0;
int lenth1=strlen(s),lenth2=strlen(p);
while(i<lenth1)
{
	if(j>=lenth2)return false;
	if(p[j]=='*')
	{
		j=j-1;
	}
	if(s[i]==p[j]||p[j]=='.')
	{
		i++;
		j++;
	}
	else
	{
		if(p[j+1]=='*')
		{
			j=j+2;
			continue;
		}
		
		return false;
	}
	
}

if(p[j]=='*'&&j==lenth2-1||j==lenth2)return true;
return false;

```

>本代码最后仍然false，有一种情况无法处理，即当`*`并不取代所有重复字符的时候，类似`s=”aaaa",p="a*a"`

#### 代码2（动态规划法）
```
int lenth1=strlen(s),lenth2=strlen(p);
char dp[lenth1+1][lenth2+1];
int i,j;
dp[0][0]=true;
for(i=1,j=0;i<lenth1+1;i++)
{
	dp[i][j]=false;
}
//当p为空，s不为空时，必然false
for(i=0,j=1;j<lenth2+1;j++)
{
	if(p[j-1]=='*'&&j%2==0)dp[i][j]=true;
	//s为空，p不为空时，只有a*b*c*…这种情况才满足
	else dp[i][j]=false;
}
for(i=1;i<lenth1+1;i++)
	for(j=1;j<lenth2+1;j++)
	{
		if(s[i-1]==p[j-1]||p[j-1]=='.')
		{
			dp[i][j]=dp[i-1][j-1];
			continue;
		}
		if(p[j-1]=='*')
			if(p[j-2]==s[i-1]||p[j-2]=='.')
				dp[i][j]=dp[i][j-2]||dp[i][j-1]||dp[i-1][j];
			else dp[i][j]=dp[i][j];
		else dp[i][j]=false;
	}
return dp[lenth1+1][lenth2+1];
```

