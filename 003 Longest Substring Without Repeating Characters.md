[[+Leetcode practice reporter]]

[[002 Add Two Numbers]]

# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the **longest substring** without repeating characters.

链接：[Longest Substring Without Repeating Characters - LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

------
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
      
	  你的代码将被镶嵌在这
    }
};
```

-----
#### 代码1（F）:
```
char *p=s;
int max=0;
while(p)
{
	int count=0;
	int a[26]={0};
	int tem=*p-97;
	a[tem]++;
	while(a[tem]<2)
	{
		p++;
		tem=*p-97;
		a[tem]++;
		count++;
	}
	if(count>max)
	max=count;
	p=p-count+1;
}
return max;
```

#### 代码2：
```
int length=strlen(s);
int i,k,j=0,max=0;
for(i=1;i<length;i++)
{
	for(k=j;k<i;k++)
	{
		if(s[i]==s[k])
		{
			j=k+1;
		}
	}
	if(i-j+1>max)
	max=i-j+1;
}
return max;
```