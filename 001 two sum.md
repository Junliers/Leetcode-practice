# 001 两数之和
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

链接：https://leetcode-cn.com/problems/two-sum

------------
## 代码：
```
/**

 * Note: The returned array must be malloced, assume caller calls free().

 */

int* twoSum(int* nums, int numsSize, int target, int* returnSize){

int i,j;
for(i=0;i<numsSize;i++)
{
	for(j=i+1;j<numsSize;j++)
	{
		if(nums[i]+nums[j]==target)
		{
			int *a=(int*)malloc(2*sizeof(int));
			a[0]=i;
			a[1]=j;
			*returnSize=2;
			return a;
		}
	}
}
return 0;  

}
```

-----
## 题解：
>本题遇到的困难主要是将*returnSize*误认为是返回数组，事实上是返回数组的大小

用暴力法ac了本题，但应该还有更好的解法
