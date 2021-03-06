# [263. 丑数](https://leetcode-cn.com/problems/ugly-number/) - easy

<p>给你一个整数 <code>n</code> ，请你判断 <code>n</code> 是否为 <strong>丑数</strong> 。如果是，返回 <code>true</code> ；否则，返回 <code>false</code> 。</p>

<p><strong>丑数 </strong>就是只包含质因数 <code>2</code>、<code>3</code> 和/或 <code>5</code> 的正整数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 6
<strong>输出：</strong>true
<strong>解释：</strong>6 = 2 × 3</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 8
<strong>输出：</strong>true
<strong>解释：</strong>8 = 2 × 2 × 2
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 14
<strong>输出：</strong>false
<strong>解释：</strong>14 不是丑数，因为它包含了另外一个质因数 <code>7 </code>。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>true
<strong>解释：</strong>1 通常被视为丑数。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-2<sup>31</sup> <= n <= 2<sup>31</sup> - 1</code></li>
</ul>


## Solutions

### 1. 依次判断

小于等于 0 一定不是。

```py
class Solution:
    def isUgly(self, n: int) -> bool:
        if n <= 0:
            return False

        v = n
        while n not in [-1, 1]:
            if n % 2 == 0:
                n = n // 2
            elif n % 3 == 0:
                n = n // 3
            elif n % 5 == 0:
                n = n // 5
            else:
                return False
        
        return True
```

可以在单次迭代中把所有某一个因素除尽

```py
class Solution:
    def isUgly(self, n: int) -> bool:
        if n <= 0:
            return False

        fastors = [2, 3, 5]
        for f in fastors:
            while n % f == 0:
                n //= f
        
        return n == 1
```
