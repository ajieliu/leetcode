# [456. 132 模式](https://leetcode-cn.com/problems/132-pattern/) - medium

<p>给你一个整数数组 <code>nums</code> ，数组中共有 <code>n</code> 个整数。<strong>132 模式的子序列</strong> 由三个整数 <code>nums[i]</code>、<code>nums[j]</code> 和 <code>nums[k]</code> 组成，并同时满足：<code>i < j < k</code> 和 <code>nums[i] < nums[k] < nums[j]</code> 。</p>

<p>如果 <code>nums</code> 中存在 <strong>132 模式的子序列</strong> ，返回 <code>true</code> ；否则，返回 <code>false</code> 。</p>

<p> </p>

<p><strong>进阶：</strong>很容易想到时间复杂度为 <code>O(n^2)</code> 的解决方案，你可以设计一个时间复杂度为 <code>O(n logn)</code> 或 <code>O(n)</code> 的解决方案吗？</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3,4]
<strong>输出：</strong>false
<strong>解释：</strong>序列中不存在 132 模式的子序列。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [3,1,4,2]
<strong>输出：</strong>true
<strong>解释：</strong>序列中有 1 个 132 模式的子序列： [1, 4, 2] 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [-1,3,2,0]
<strong>输出：</strong>true
<strong>解释：</strong>序列中有 3 个 132 模式的的子序列：[-1, 3, 2]、[-1, 3, 0] 和 [-1, 2, 0] 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 <= n <= 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup></code></li>
</ul>


## Solutions

枚举 `i`, 从右往左，如果小于 k 则表示存在 `i < k < j`。因为 k 来自 q，q 里面记录了所有可能的 j。所以，当 k 从 `-inf` 被更新时候，说明 q 中也已经存在 j。

```python
class Solution:
    def find132pattern(self, nums: List[int]) -> bool:
        q = []
        k = float("-inf")
     
        for i in range(len(nums) - 1, -1, -1):
            if nums[i] < k:
                return True
            while q and q[-1] < nums[i]:
                k = q.pop()
            if nums[i] > k:
                q.append(nums[i])
        return False

```