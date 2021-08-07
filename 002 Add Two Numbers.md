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
while(l1||l2)
{
	int n1=l1?l1->val:0;
	int n2=l2?l2->val:0;
	tem=n1+n2+a;
	if(!p)
	{
		sum=malloc(sizeof(struct ListNode));
		p=sum;
		sum->val=tem%10+a;
		sum->next=NULL;
	}
	else
	{
		sum->next=malloc(sizeof(struct ListNode));
		sum->next->val=tem%10;
		sum->next->next=NULL;
		sum=sum->next;
	}
	if(tem>=10)
		{
			a=1;
		}
		else
		{
			a=0;
		}
	if(l1)l1=l1->next;
	if(l2)l2=l2->next;
}

if(a==1)
{
	sum->next=malloc(sizeof(struct ListNode));
	sum->next->val=1;
	sum->next->next=NULL;
	sum=sum->next;
}

return p;

```

-----
#### 题解：
>又是一道思路很简单，但是相当考细节的题

这道题的关键在于要不要进位，所以需要一个额外的辅助变量。

细节方面，考虑要保留头指针，同时sum作为尾指针保留。最后还要考虑l1和l2都加完了还有可能会进位。

在简化方面，把短指针前面补零可以有效减少代码长度。