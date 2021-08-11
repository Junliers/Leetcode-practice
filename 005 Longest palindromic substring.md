[[+Leetcode practice reporter]]
[[004 Media of two Sorted Arrays]]
# Longest palindromic substring

Given a string `s`, return _the longest palindromic substring_ in `s`.

链接：[5. 最长回文子串 - 力扣（LeetCode）](https://leetcode-cn.com/problems/longest-palindromic-substring/)

-----
```
char * longestPalindrome(char * s){

  你的代码将被镶嵌在这

}
```

----

### 代码：
```
int length= strlen(s);
if( length ==0) return 0; 
int max=1,head,tail;
int i,track=0;
for(i=0;i<length-1;i++)
{
	if(s[i]==s[i+1])
	{
		head=i;
		tail=i+1;
		while(head>=0&&tail<length)
		{
			if(s[head]!=s[tail])
			break;
			if(tail-head+1>max)
			{
				max=tail-head+1;
				track=head;
			}
			head--;
			tail++;
		}
	}
}
for(i=0;i<length;i++)
{
	head=i;
	tail=i;
	while(head>=0&&tail<length)
		{
			if(s[head]!=s[tail])
				break;
			if(tail-head+1>max)
			{
				max=tail-head+1;
				track=head;
			}
			head--;
			tail++;
		}
	
}


char *a;
a=malloc(sizeof(char)*max+1);
strncpy(a,s+track,max);
a[max]='\0';
return a;

char *a=s+track;
a[max]='\0';
return a;

-----
ps.以上两种提交方式ok,但是以下这种不行，似乎字符串还是不太等同于数组？

char a[max+1];
for(i=0;i<max;i++)
{
	a[i]=s[i+track];
}
a[max]='\0';
return a;
```

----

#### 题解：
暴力破解，基本思路是从中心结点开始往前后扫描，需要注意的是中心结点有两种情况，单个字符和两个相同字符这两种情况。
此外，该两种情况的代码重复率很高，应该有更好的解法。