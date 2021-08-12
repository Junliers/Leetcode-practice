[[+Leetcode practice reporter]]
[[006 Zigzag conversion]]

# 007 Reverse Interger

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

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
if(x==0)return 0;
int count =1;
int tem = x;
while(tem/10!=0)
{
	count++;
	tem=tem/10;
}
int answer=0;
tem=0;
for(int i=0;i<count;i++)
{
	answer+=(x/(10^(count-i-1))-tem*10)*10^(i);
	tem=x/(10^(count-i-1));
}
return answer;