# 原题
机器人从起点到终点有多少条不同的路径，只能向右或者向下走。

注意点：

  - 格子大小最大为100*100

例子：

输入: m = 3, n = 7

输出: 28

# 解题思路
### 动态规划。 

到达右下角的方法只有两个，从上往下，和从左往右。

利用到达终点的唯一性，就可以写出递推公式（dp[i][j]表示到坐标（i,j）的走法数量）：

dp[i][j] = dp[i-1][j] + dp[i][j-1]

初始条件的话，当整个格子只有一行，那么到每个格子走法只有1种；只有一列的情况同理。

所以，理解了这些，代码就非常好写了。

通常来讲，我们会初始dp数组为dp[m+1][n+1]。但是这里的话，因为dp[i][j]是表示坐标点，所以这里声明dp[m][n]更容易理解。
