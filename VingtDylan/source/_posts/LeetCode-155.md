---
title: LeetCode 155
mathjax: true
copyright: true
tags:
  - LeetCode
  - 栈
  - 设计
categories: LeetCode
abbrlink: 9a8
date: 2020-05-12 00:18:02
---

#### [155. 最小栈](https://leetcode-cn.com/problems/min-stack/)

难度: medium

设计一个支持 `push` ，`pop` ，`top` 操作，并能在常数时间内检索到最小元素的栈。

- `push(x)` —— 将元素 x 推入栈中。
- `pop()` —— 删除栈顶的元素。
- `top()` —— 获取栈顶元素。
- `getMin()` —— 检索栈中的最小元素。

**示例:**

```
输入：
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

输出：
[null,null,null,null,-3,null,0,-2]

解释：
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.getMin();   --> 返回 -2.
```

**提示：**

- `pop`、`top` 和 `getMin` 操作总是在 **非空栈** 上调用。

<!--more-->

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/min-stack
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

双栈或者记录“曾经”的最小值，注意相同的值

##### 双栈

```c++
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {

    }
    
    void push(int x) {
        stk1.push(x);
        if(stk2.empty() || x <= stk2.top())stk2.push(x);
    }
    
    void pop() {
        if(stk1.top() == stk2.top())stk2.pop();
        stk1.pop();
    }
    
    int top() {
        return stk1.top();
    }
    
    int getMin() {
        return stk2.top();
    }
private:
    stack<int> stk1,stk2;
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```



##### 曾经的最小值

```c++
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {
        minm = INT_MAX;
    }
    
    void push(int x) {
        if(x <= minm){
            stk.push(minm);
            minm = x;
        }
        stk.push(x);
    }
    
    void pop() {
        int t = stk.top();
        stk.pop();
        if(t == minm){
            minm = stk.top();
            stk.pop();
        }
    }
    
    int top() {
        return stk.top();
    }
    
    int getMin() {
        return minm;
    }
private:
    stack<int> stk;
    int minm;
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```

