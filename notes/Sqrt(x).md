# 原题
求一个数的平方根。

注意点：

  - 结果返回整数，舍去小数，不是四舍五入

例子：

输入: x = 5

输出: 2

# 解题思路
这道题很巧妙的运用了二分查找法的特性，有序，查找pos（在这道题中pos=value），找到返回pos，找不到返回邻近值。

因为是求数x（x>=0) 的平方根， 因此，结果一定是小于等于x且大于等于0，所以用二分查找法肯定能搜到结果。

以每一次的mid的平方来与target即数x相比：

如果mid*mid == x，返回mid；

如果mid*mid < x，那么说明mid过小，应让low = mid+1，在右边继续查找

如果mid*mid > x，那么说明mid过大，应让high = mid-1，在左边继续查找

若x无法开整数根号（在上述查找中没有找到），那么我们仍然可以利用之前对二分查找法总结的技巧，
当target值不在数组中，low指向大于target的那个值，high指向小于target的那个值，
由于我们需要向下取整的结果，所以我们返回high指向的值（这里high指向的值和high的值是同一个值），
这个值就是所求得最接近起开根号结果的整数值。

因为leetcode的test case x=2147395599，在算mid*mid的时候造成溢出，
所以mid不能使用int型来接，要使用long型防止溢出（Java中Integer型的范围：-2^31 到2^31-1即(-2147483648~2147483647)）
