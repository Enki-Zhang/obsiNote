两遍《[代码随想录](https://zhida.zhihu.com/search?content_id=653555737&content_type=Answer&match_order=1&q=%E4%BB%A3%E7%A0%81%E9%9A%8F%E6%83%B3%E5%BD%95&zhida_source=entity)》的回溯、贪心、动态规划、二分、双指针 +[《算法图解》](https://zhida.zhihu.com/search?content_id=653555737&content_type=Answer&match_order=1&q=%E3%80%8A%E7%AE%97%E6%B3%95%E5%9B%BE%E8%A7%A3%E3%80%8B&zhida_source=entity)的动态规划 +两遍[《剑指offer》](https://zhida.zhihu.com/search?content_id=653555737&content_type=Answer&match_order=1&q=%E3%80%8A%E5%89%91%E6%8C%87offer%E3%80%8B&zhida_source=entity)，耗时68小时。
## 时间复杂度



### 最长回文子串 

思路：

使用双指针 两重循环 头指针指向头节点 内层循环中尾指针都从数组最后一个元素开始
因为是要找到最长的回文 尾指针从后向前更容易找到符合要求的最长回文串
同时更新最长的回文子串长度 因为头指针会移动
直到找到最长子串

## 前缀和

**前缀和（Prefix Sum）** 是一种常用的算法技巧，主要用于快速计算数组或序列中某个区间的和。它的核心思想是通过预处理，==**将数组中的每个位置存储为从起始位置到当前位置的累加和**==，从而在查询时能够以 **O(1)** 的时间复杂度快速计算出任意区间的和。


## 区间和

题目要求「区间和」的时候，那么就可以考虑使用「前缀和」