[[+Leetcode practice reporter]]

[[008 String to Integer(atoi)]]

# Panlindrome number

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

链接：https://leetcode-cn.com/problems/palindrome-number

-------
```
bool isPalindrome(int x){

 你的代码将被镶嵌在这 

}
```

-----
#### 代码
```
if(x<0)return false;
int num=0;
int a=x;
int lastnum=0;
while(a!=0||lastnum!=0)
{
	if(num>INT_MAX/10||num==INT_MAX&&lastnum>8)
	return false;
	num=num*10+lastnum;
	lastnum=a%10;
	a=a/10;
}
if (num==x)return true;
return false;
```
-----

#### 题解：
直接套用了[[007 Reverse Integer]]整数反转的思想，在一开始就把全部错误的负数排除。

进阶算法可能要判断一个字符串是不是回文字符串，可以直接参考[[005 Longest palindromic substring]]找最长回文字符串的算法。
