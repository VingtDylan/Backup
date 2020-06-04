---
title: LeetCode 994
mathjax: true
copyright: true
tags:
  - LeetCode
  - 广度优先搜索
categories: LeetCode
abbrlink: bed
date: 2020-06-04 13:56:12
---

#### [994. 腐烂的橘子](https://leetcode-cn.com/problems/rotting-oranges/)

难度: medium

在给定的网格中，每个单元格可以有以下三个值之一：

- 值 `0` 代表空单元格；
- 值 `1` 代表新鲜橘子；
- 值 `2` 代表腐烂的橘子。

每分钟，任何与腐烂的橘子（在 4 个正方向上）相邻的新鲜橘子都会腐烂。

返回直到单元格中没有新鲜橘子为止所必须经过的最小分钟数。如果不可能，返回 `-1`。

**示例 1：**

**![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/16/oranges.png)**

```
输入：[[2,1,1],[1,1,0],[0,1,1]]
输出：4
```

<!--more-->

**示例 2：**

```
输入：[[2,1,1],[0,1,1],[1,0,1]]
输出：-1
解释：左下角的橘子（第 2 行， 第 0 列）永远不会腐烂，因为腐烂只会发生在 4 个正向上。
```

**示例 3：**

```
输入：[[0,2]]
输出：0
解释：因为 0 分钟时已经没有新鲜橘子了，所以答案就是 0 。
```

**提示：**

1. `1 <= grid.length <= 10`
2. `1 <= grid[0].length <= 10`
3. `grid[i][j]` 仅为 `0`、`1` 或 `2`

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/rotting-oranges
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

#### AC代码

广搜，可以扩展时+1

```c++
class Solution {
public:
    int m, n;
    int dx[4] = {0, 1, 0, -1};
    int dy[4] = {1, 0, -1, 0};
    int orangesRotting(vector<vector<int>>& grid) {
        int count = 0;
        m = grid.size();
        n = grid[0].size();
        int step = 0;
        queue<pair<int,int>> q;
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(grid[i][j] == 2){
                    q.push(make_pair(i,j));
                }else if(grid[i][j] == 1)
                    count++;
            }
        }
        while(!q.empty()){
            int len = q.size();
            bool flag = false;
            while(len--){
                pair<int,int> t = q.front();q.pop();
                for(int i = 0; i < 4; i++){
                    int tx = t.first + dx[i];
                    int ty = t.second + dy[i];
                    if(tx < 0 || tx >= m || ty < 0 || ty >= n || grid[tx][ty] != 1)continue;
                    grid[tx][ty] = 2;
                    q.push(make_pair(tx,ty));
                    flag = true;
                    count--;
                }
            }
            if(flag)step++;
        }
        return count == 0 ? step : -1;
    }
};
```



