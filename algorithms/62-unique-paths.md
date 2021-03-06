# [62. 不同路径](https://leetcode-cn.com/problems/unique-paths/) - medium

<p>一个机器人位于一个 <code>m x n</code><em> </em>网格的左上角 （起始点在下图中标记为 “Start” ）。</p>

<p>机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。</p>

<p>问总共有多少条不同的路径？</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png" />
<pre>
<strong>输入：</strong>m = 3, n = 7
<strong>输出：</strong>28</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>m = 3, n = 2
<strong>输出：</strong>3
<strong>解释：</strong>
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右
3. 向下 -> 向右 -> 向下
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>m = 7, n = 3
<strong>输出：</strong>28
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>m = 3, n = 3
<strong>输出：</strong>6</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= m, n <= 100</code></li>
	<li>题目数据保证答案小于等于 <code>2 * 10<sup>9</sup></code></li>
</ul>


## Solutions

### 1. 排列组合

总共需要走 `(m - 1) + (n - 1)` 步，看成排列组合问题，从 `(m + n - 2)` 中选择 `min(m, n) - 1` 步出来。

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        c = (m + n) - 2
        d = min(m, n) - 1

        v1, v2 = c, d
        for i in range(1, d):
            c *= v1 - i
            d *= v2 - i
        
        return (c // d) if d > 0 else 1 
```

### 2. 动态规划

用 dp[i][j] 表示到 i 行 j 列的走法。则有 `dp[i][j] = dp[i - 1][j] + dp[i][j - 1]`

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [[1] * n for _ in range(m)]

        for i in range(1, m):
            for j in range(1, n):
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        
        return dp[-1][-1]
```
