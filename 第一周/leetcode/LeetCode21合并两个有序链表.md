## LeetCode21合并两个有序链表

[21合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)



代码：

```C++
/*
 * @lc app=leetcode.cn id=21 lang=cpp
 *
 * [21] 合并两个有序链表
 */

// @lc code=start
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
    public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2)
    {
        ListNode dummy(INT_MIN);    //INT_MIN是结构体初始化的值（ListNode(int x) : val(x), next(NULL) {}）
        ListNode* tail = &dummy;
        while (l1 && l2) {
            if (l1->val < l2->val) {
                tail->next = l1;
                l1 = l1->next;
            }
            else {
                tail->next = l2;
                l2 = l2->next;
            }
            tail = tail->next;
        }
        tail->next = l1 ? l1 : l2;  //判断l1是不是一个空指针，若l1是一个空指针，则为false，next指向l2
        return dummy.next;
    }
};
```



Note:

​	自己还没看懂，多次调用该函数完成链表合并

​	递归     迭代     不是很明白