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

#### 代码2 (T)：
```
int length=strlen(s);
int i,k,j=0,max=0;
for(i=0;i<length;i++)
{
	for(k=j;k<i;k++)
	{
		if(s[i]==s[k])
		{
			j=k+1;
			break;
		}
	}
	if(i-j+1>max)
	max=i-j+1;
}
return max;
```

-----
#### 题解：
本题最开始的思路是用哈希做，很复杂，一个字母一个字母的要从头扫过去，还需要用哈希函数储存对应字母的个数，需要归零调整等一系列操作，而且最后可能是没理解字符串的相关操作，盲目的用了指针，导致一直error，暂时没有查出原因。之后需要再对应一下指针对字符串的操作。

正确题解用的是窗口滑动，运用了队列的思想，进来一个新字母就比一比有没有相同的，由于需要一直往后滑，所以看到相同的会直接舍弃掉前面的，中途要记录好最大字符串长度。