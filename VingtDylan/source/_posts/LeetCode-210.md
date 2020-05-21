---
title: LeetCode 210
mathjax: true
copyright: true
tags:
  - LeetCode
  - 深度优先搜索
  - 广度优先搜索
  - 图
  - 拓扑排序
  - mark
categories: LeetCode
abbrlink: ca9a
date: 2020-05-17 00:30:05
---

#### [210. 课程表 II](https://leetcode-cn.com/problems/course-schedule-ii/)

难度: medium

现在你总共有 *n* 门课需要选，记为 `0` 到 `n-1`。

在选修某些课程之前需要一些先修课程。 例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们: `[0,1]`

给定课程总量以及它们的先决条件，返回你为了学完所有课程所安排的学习顺序。

可能会有多个正确的顺序，你只要返回一种就可以了。如果不可能完成所有课程，返回一个空数组。

**示例 1:**

```
输入: 2, [[1,0]] 
输出: [0,1]
解释: 总共有 2 门课程。要学习课程 1，你需要先完成课程 0。因此，正确的课程顺序为 [0,1] 。
```

<!--more-->

**示例 2:**

```
输入: 4, [[1,0],[2,0],[3,1],[3,2]]
输出: [0,1,2,3] or [0,2,1,3]
解释: 总共有 4 门课程。要学习课程 3，你应该先完成课程 1 和课程 2。并且课程 1 和课程 2 都应该排在课程 0 之后。
     因此，一个正确的课程顺序是 [0,1,2,3] 。另一个正确的排序是 [0,2,1,3] 。
```

**说明:**

1. 输入的先决条件是由**边缘列表**表示的图形，而不是邻接矩阵。详情请参见[图的表示法](http://blog.csdn.net/woaidapaopao/article/details/51732947)。
2. 你可以假定输入的先决条件中没有重复的边。

**提示:**

1. 这个问题相当于查找一个循环是否存在于有向图中。如果存在循环，则不存在拓扑排序，因此不可能选取所有课程进行学习。
2. [通过 DFS 进行拓扑排序](https://www.coursera.org/specializations/algorithms) - 一个关于Coursera的精彩视频教程（21分钟），介绍拓扑排序的基本概念。
3. 拓扑排序也可以通过 [BFS](https://baike.baidu.com/item/宽度优先搜索/5224802?fr=aladdin&fromid=2148012&fromtitle=广度优先搜索) 完成。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/course-schedule-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### 分析

1.很明显的拓扑排序问题

有向无环图结点的线性排序

2.BFS算法
step1:统计图中每个节点的入度，生成入度表 indegrees。
step2:借助一个队列 queue，将所有入度为0的节点入队。
step3:当queue非空时，依次将队首节点出队，依次将队首节点的所有邻接节点cur的入度-1，即 indegrees[cur] -= 1;
当入度-1后邻接节点cur的入度为0，说明cur所有的前驱节点已经被 “删除”，此时将cur入队

3.DFS算法略了，懒得打，网上有很多解析

#### AC代码

##### BFS

```c++
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<int> res;
        vector<vector<int>> graph(numCourses,vector<int>(0));
        vector<int> indegrees(numCourses,0);
        for(auto & pre : prerequisites){
            graph[pre[1]].push_back(pre[0]);
            indegrees[pre[0]]++;
        }
        queue<int> q;
        for(int i = 0; i < numCourses; i++){
            if(indegrees[i] == 0)q.push(i);
        }
        while(!q.empty()){
            int t = q.front();
            res.push_back(t);
            q.pop();
            for(auto &a: graph[t]){
                indegrees[a]--;
                if(indegrees[a] == 0)
                    q.push(a);
            }
        }
        if(res.size() != numCourses)return {};
        return res;
    }
};
```

##### DFS

```c++
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<int> res;
        vector<vector<int>> graph(numCourses,vector<int>(0));
        vector<int> visited(numCourses);
        bool circle = false;
        for(auto & pre : prerequisites){
            graph[pre[1]].push_back(pre[0]);
        }
        for(int i = 0; i < numCourses && !circle; i++){
            if(!visited[i]){
                dfs(i,res,graph,visited,circle);
            }
        }
        if(circle)return {};
        reverse(res.begin(),res.end());
        return res;
    }

    void dfs(int x, vector<int>& res, vector<vector<int>>& graph, vector<int>& visited, bool& circle){
        visited[x] = 1;
        for(int v: graph[x]){
            if(visited[v] == 0){
                dfs(v,res,graph,visited,circle);
                if(circle){
                    return;
                }
            }else if(visited[v] == 1){
                circle = true;
                return;
            }
        }
        visited[x]= 2;
        res.push_back(x);
    }
};
```
