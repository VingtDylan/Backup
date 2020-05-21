---
title: LeetCode 25
mathjax: true
copyright: true
tags:
  - LeetCode
  - 链表
categories: LeetCode
abbrlink: '9828'
date: 2020-05-16 13:25:28
---

#### [25. K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

难度: hard

给你一个链表，每 *k* 个节点一组进行翻转，请你返回翻转后的链表。

*k* 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 *k* 的整数倍，那么请将最后剩余的节点保持原有顺序。

**示例：**

给你这个链表：`1->2->3->4->5`

当 *k* = 2 时，应当返回: `2->1->4->3->5`

当 *k* = 3 时，应当返回: `3->2->1->4->5`

**说明：**

- 你的算法只能使用常数的额外空间。
- **你不能只是单纯的改变节点内部的值**，而是需要实际进行节点交换。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/reverse-nodes-in-k-group
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### 思路

递归不递归都随便吧，按照题意实现而已

##### 1.非递归

```c++
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
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(!head || k == 1)return head;
        ListNode* dummy = new ListNode(-1);
        dummy->next = head;
        ListNode* pre = dummy;
        ListNode* cur = head;
        for(int i = 1; cur; i++){
            if(i % k == 0){
                pre = reverse(pre, cur->next);
                cur = pre->next;
            }else{
                cur = cur->next;
            }
        }
        return dummy->next;    
    }

    ListNode* reverse(ListNode* pre, ListNode* last){
        ListNode* dummy = pre->next;
        ListNode* cur = dummy->next;
        while(cur != last){
            dummy->next = cur->next;
            cur->next = pre->next;
            pre->next = cur;
            cur = dummy->next;
        }
        return dummy;
    }
};
```

##### 2.递归

```c++
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
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(!head || k == 1)return head;
        ListNode* cur = head;
        for(int i = 0; i < k; i++){
            if(!cur)return head;
            cur = cur->next;
        }
        ListNode* dummy = reverse(head, cur);
        head->next = reverseKGroup(cur, k);
        return dummy;
    }

    ListNode* reverse(ListNode* head, ListNode* tail){
        ListNode* pre = tail;
        while(head != tail){
            ListNode* temp = head->next;
            head->next = pre;
            pre = head;
            head = temp;
        }
        return pre;
    }
};
```



