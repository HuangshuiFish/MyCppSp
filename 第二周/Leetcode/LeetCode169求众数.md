##LeetCode169求众数

[169求众数](https://leetcode-cn.com/problems/majority-element/description/)

代码：

```C++
/*
 * @lc app=leetcode.cn id=169 lang=cpp
 *
 * [169] 求众数
 */

// @lc code=start
class Solution {
    public:
    int majorityElement(vector<int>& nums)
    {
        int half_falg = nums.size() / 2;  //判断是否出现的次数超过一半
        for (int i : nums) {              //遍历数组
            int count = 0;
            for (int j : nums) {  //遍历数组，找到元素i在数组中出现的次数
                if (j == i) {
                    count++;
                }
            }
            if (count > half_falg) {  //如果次数大于一半，则将该数返回，结束程序
                return i;
            }
        }
        return -1;
    }
};
/*
Time Limit Exceeded
42/44 cases passed (N/A)
暴力循环，时间复杂度较高O(n^2)
*/
```



```C++
/*
 * @lc app=leetcode.cn id=169 lang=cpp
 *
 * [169] 求众数
 */

// @lc code=start
class Solution {
    public:
    int majorityElement(vector<int>& nums)
    {
        int n = nums.size() / 2;
        sort(nums.begin(), nums.end());	//先对数组进行排序，返回数组中间的数即可
        return nums[n];
    }
};
/*
Accepted
44/44 cases passed (20 ms)
Your runtime beats 89.33 % of cpp submissions
Your memory usage beats 95.96 % of cpp submissions (10.8 MB)
*/
```

```C++
/*
 * @lc app=leetcode.cn id=169 lang=cpp
 *
 * [169] 求众数
 */

// @lc code=start
class Solution {
    public:
    int majorityElement(vector<int>& nums)
    {
        int half_flag = nums.size() / 2;
        map<int, int> hash_map;
        for (int i = 0; i < nums.size(); ++i)
            hash_map[nums[i]] = 0;  //给哈希表赋初值
        for (int i = 0; i < nums.size(); ++i) {
            hash_map[nums[i]]++;    //遍历数组，找到和哈希表的key(nums[i])相同的元素时相应的value+1
            if (hash_map[nums[i]] > half_flag) {
                return nums[i];
            }
        }
        return -1;
    }
};
/*
Accepted
44/44 cases passed (24 ms)
Your runtime beats 74.83 % of cpp submissions
Your memory usage beats 71.12 % of cpp submissions (11.1 MB)
使用哈希表解决问题，不再需要双重循环，
*/
```



收获：

1. ```C++
   for (auto i : nums)
   for (int i = 0; i < nums.size(); ++i)
   ```

   这两个不同，第一个中i代表的是nums中的每一个元素，第二个中i代表的是0,1,2,3,4。在编程时要注意自己要用的是哪一个，不要用错了。