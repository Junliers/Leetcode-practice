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