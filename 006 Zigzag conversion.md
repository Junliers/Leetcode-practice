[[+Leetcode practice reporter]]
[[005 Longest palindromic substring]]
# 006 Zigzag conversion

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

链接：https://leetcode-cn.com/problems/zigzag-conversion

------
```
char * convert(char * s, int numRows){

  你的代码将被镶嵌在这

}
```

-----
#### 代码：
```
int lenth=strlen(s);
if(numRows==1)return s;
char *a=(char *)malloc(sizeof(char)*(lenth+1));
int i,j,k=0;
for(i=0;i<numRows;i++)
{
	for(j=0;j<lenth;j++)
	{
		if(j%(2*numRows-2)==i||j%(2*numRows-2)==2*numRows-2-i)
		{
			a[k++]=s[j];
		}
	}
}
a[k]='\0';
return a;
```

-----
#### 题解：
这道题主要是一道找规律的题目，面对这种逻辑上重复的题，可以将数字分组，然后自然而然会想到可以利用‘%’来进行区分。

需要注意的是当numRows=1是下方除数会是0，所以需要单独处理。