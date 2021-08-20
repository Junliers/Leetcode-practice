[[+Leetcode practice reporter]]
[[006 Zigzag conversion]]

# 007 Reverse Interger

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

链接：https://leetcode-cn.com/problems/reverse-integer

------
```
int reverse(int x){

  你的代码将被镶嵌在这

}
```

-----
#### 代码：
```
int tem=x;
int answer=0;
while(tem!=0)
{
	if(answer>INT_MAX/10||answer<INT_MIN/10)
	{
		return 0;
	}
	answer=answer*10+tem%10;
	tem=tem/10;
}
return answer;
```

-----
#### 题解：
真没想到居然会败在这么一道简单题手上，最开始的时候只想到了递归，但这个根本不是递归而是递推。只需要每次把一个数位上的数字提取出来就可以了。

嗯，顺序是先提取个位数，然后提取百位数，同时将之前提取的个位数乘以十，如此反复，直到tem=0。有一个小陷阱是这里的answer 不能溢出，所以要在answer溢出之前进行预判而不能等到已经溢出了再进行判断。