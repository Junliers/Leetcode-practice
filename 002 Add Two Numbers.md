[[+Leetcode practice reporter]]

# Add Two Numbers

给你两个 非空 的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储 一位 数字。

请你将两个数相加，并以相同形式返回一个表示和的链表。

你可以假设除了数字 0 之外，这两个数都不会以 0 开头。

链接：https://leetcode-cn.com/problems/add-two-numbers

-----

```
/**

 * Definition for singly-linked list.

 * struct ListNode {

 *     int val;

 *     struct ListNode *next;

 * };

 */

  
  

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2){

  **你的代码会被镶嵌在这**

}
```

----
#### 代码：
```
struct ListNode *sum=NULL,*p=NULL;
int tem,a=0;
while(l1->next||l2->next)
{
	tem=l1->val+l2->val;
	if(!p)
	{
		sum=malloc(sizeof(struct ListNode));
		p=sum;
		sum->val=tem%10;
		sum->next=NULL;
	}
	else
	{
		sum->next=malloc(sizeof(struct ListNode));
		sum->next->val=tem%10+a;
		sum->next->next=NULL;
		sum=sum->next;
	}
	if(tem>10)
		{
			a=1;
		}
		else
		{
			a=0;
		}
	l1=l1->next;
	l2=l2->next;
}
if(a=0)
{
	if(l1)
	{
	sum=l1;
	}
	if(l2)sum=l2;
}
else
{
	if(l1)
	{
		sum=malloc(sizeof(struct ListNode));
		sum->val=l1->val+1;
		l1=l1->next;
		sum->next=l1;
	}
	if(l2)
	{
		sum=malloc(sizeof(struct ListNode));
		sum->val=l2->val+1;
		l2=l2->next;
		sum->next=l2;
	}
}
return p;
```

