[[+Leetcode practice reporter]]

# String ti Integer(atoi)

请你来实现一个 myAtoi(string s) 函数，使其能将字符串转换成一个 32 位有符号整数（类似 C/C++ 中的 atoi 函数）。

函数 myAtoi(string s) 的算法如下：

读入字符串并丢弃无用的前导空格
检查下一个字符（假设还未到字符末尾）为正还是负号，读取该字符（如果有）。 确定最终结果是负数还是正数。 如果两者都不存在，则假定结果为正。
读入下一个字符，直到到达下一个非数字字符或到达输入的结尾。字符串的其余部分将被忽略。
将前面步骤读入的这些数字转换为整数（即，"123" -> 123， "0032" -> 32）。如果没有读入数字，则整数为 0 。必要时更改符号（从步骤 2 开始）。
如果整数数超过 32 位有符号整数范围 [−231,  231 − 1] ，需要截断这个整数，使其保持在这个范围内。具体来说，小于 −231 的整数应该被固定为 −231 ，大于 231 − 1 的整数应该被固定为 231 − 1 。
返回整数作为最终结果。
注意：

本题中的空白字符只包括空格字符 ' ' 。
除前导空格或数字后的其余字符串外，请勿忽略 任何其他字符。

链接：https://leetcode-cn.com/problems/string-to-integer-atoi

------
```
int myAtoi(char * s){

  	你的代码将被镶嵌在这

}
```
----
#### 代码1(F)：
```
int a[200]={0};
int count=0;
int nums=1;
char *p=s;
while(p)
{
	if(*p==' ')
	{
		p++;
		continue;
	}
	if(*p=='-')
	{
		nums=-1;
		p++;
		continue;
	}
	if(*p<123&&*p>96||*p<91&&*p>64||*p=='.')
	{
		break;
	}
	if(*p<10&&*p>(-1))
	{
		count++;
		a[count]=*p;
		p++;
	}
}
int answer=0;
for(int i=1;i<=count;i++)
{
	if(a[i]==0)
	{
		continue;
	}
	answer+=a[i]*10^(count-i);
}
answer=answer*nums;
if(answer>INT_MAX)
return INT_MAX;

if(answer<INT_MIN)
return INT_MIN;

return answer;

```
>真没想到居然还会超出时间限制，那不按描述的算法来了

-----
#### 代码2
```
int lenth=strlen(s);
int nums=1;
int answer=0;
int i=0;
int nextnum=0;
while(s[i]==' ')i++;
if(s[i]=='-')
{
	nums=-1;
	i++;
}
else
{
if(s[i]=='+')i++;
}
while(s[i]>='0'&&s[i]<='9'&&i<lenth)
{
	nextnum=s[i]-'0';
	if(answer>INT_MAX/10||answer==INT_MAX/10&&nextnum>7)
	{
		if(nums==-1)
		return INT_MIN;
		return INT_MAX;
	}
	answer=answer*10+nextnum;
	i++;
}
answer=answer*nums;
return answer;

```