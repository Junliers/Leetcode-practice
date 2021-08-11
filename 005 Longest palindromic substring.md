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
			if(tail-head+1>max)
			{
				max=tail-head+1;
				track=head;
			}
			if(s[head]!=s[tail])
				break;
			head--;
			tail++;
		}
	}
}
char a[max]；
for(i=0;i<max;i++)
{
 a[i]=s[track+i];
}
return a;
```