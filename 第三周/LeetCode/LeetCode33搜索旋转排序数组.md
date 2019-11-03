##LeetCode33搜索旋转排序数组

[LeetCode33](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)

代码：

```cpp
class Solution {
    public:
    int search(vector<int>& nums, int target)
    {
        int left = 0;
        int right = nums.size() - 1;
        while (left < right) {
            int mid = (left + right) / 2;
            if (nums[0] <= nums[mid] && (target > nums[mid] || target < nums[0])) {
                left = mid + 1;
            }
            else if (nums[0] > nums[mid] && (target < nums[0] && target > nums[mid])) {
                left = mid + 1;
            }
            else if (nums[mid] == target) {
                return mid;
            }
            else {
                if (mid > 0) {  //防止right越界
                    right = mid - 1;
                }
                else {
                    right = mid;
                }
            }
        }
        return left == right && nums[left] == target ? left : -1;
    }
};
/*
Accepted
196/196 cases passed (4 ms)
Your runtime beats 90.73 % of cpp submissions
Your memory usage beats 76.05 % of cpp submissions (8.8 MB)
*/
```



学习总结;

1. 二分查找：有序，单调，可以用下标访问。
2. 在写程序时注意极端情况下程序能否跑通。