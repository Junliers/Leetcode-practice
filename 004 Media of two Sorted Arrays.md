[[+Leetcode practice reporter]]
[[003 Longest Substring Without Repeating Characters]]

# 004 Media of Two Sorted Arreys

Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

链接：https://leetcode-cn.com/problems/median-of-two-sorted-arrays

----
```
double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size){

 **你的代码会被镶嵌在这** 

}
```

----
#### 代码：
```
int numssize=nums1Size+nums2Size;
int a[numssize];
int i=0,j=0;
while(i<nums1Size&&j<nums2Size)
{
	if(nums1[i]<nums2[j])
	{
		a[i+j]=nums1[i];
		i++;
	}
	else
	{
		a[i+j]=nums2[j];
		j++;
	}
}
	while(j<nums2Size)
	{
		a[i+j]=nums2[j];
		j++;
	}

	while(i<nums1Size)
	{
		a[i+j]=nums1[i];
		i++;
	}
int b=numssize%2;
double c;
if(b==1)
c=a[numssize/2];
else
c=(a[(numssize/2-1)]+a[numssize/2])/2.0;
return c;

```
----
#### 题解：
本题的基本解法是进行数组合并，然后输出中位数（注意进行数据类型转换)。
本题的原理是查找两个有序数组的中位数，查找的方法有很多种，之后可以考虑其它查找方法进行改进。

-----
#### 进阶版本题猜想：
如何查找两个无序数组的中位数