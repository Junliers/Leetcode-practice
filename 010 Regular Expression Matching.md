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

#### 代码2（动态规划法|T）
```
int lenth1=strlen(s),lenth2=strlen(p);
char dp[lenth1+1][lenth2+1];
//多开辟一个空间是因为空也要算一种情况，下面要记住dp[i-1][j-1]才对应s[i]和p[j]
int i,j;
dp[0][0]=true;
//s为空，p为空，必true
for(i=1,j=0;i<lenth1+1;i++)
{
	dp[i][j]=false;
}
//当p为空，s不为空时，必然false
for(i=0,j=1;j<lenth2+1;j++)
{
	if(p[j-1]=='*'&&j>=2)dp[i][j]=dp[i][j-2];
	//s为空，p不为空时，只有a*b*c*…这种情况才能true
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
		//‘*’时有两种情况
			if(p[j-2]==s[i-1]||p[j-2]=='.')
			//能匹配上时
				dp[i][j]=dp[i][j-2]||dp[i][j-1]||dp[i-1][j];
				//可能`a*`指代空||指代a||指代两个及以上的a
			else dp[i][j]=dp[i][j-2];
			//没匹配上直接指代为空
		else dp[i][j]=false;
	}
/*
for(i=0;i<lenth1+1;i++)
{
	printf("\n");
	for(j=0;j<lenth2+1;j++)
	{
		printf("%c\t",dp[i][j]);
	}
}
*/
//这段调试代码因为vscode一直跳bug最后没用到
return dp[lenth1][lenth2];
```
-------

#### 题解
哭了，这道用动态规划的题做了我一天，有一说一不就是一个递推吗？？！！！题解写注释上了