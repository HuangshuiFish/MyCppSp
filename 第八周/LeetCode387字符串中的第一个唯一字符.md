## LeetCode387字符串中的第一个唯一字符

[LeetCode387字符串中的第一个唯一字符](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

方法一：

```cpp
/*
 * @lc app=leetcode.cn id=387 lang=cpp
 *
 * [387] 字符串中的第一个唯一字符
 */

// @lc code=start
class Solution {
    public:
    int firstUniqChar(string s)
    {
        unordered_map<char, int> m;
        for (auto& c : s) {
            m[c]++;
        }
        for (int i = 0; i < s.size(); i++) {
            if (m[s[i]] == 1) {
                return i;
            }
        }
        return -1;
    }
};
/*
Accepted
104/104 cases passed (76 ms)
Your runtime beats 36.71 % of cpp submissions
Your memory usage beats 79.96 % of cpp submissions (13 MB)
*/
```

方法二：

```cpp
/*
 * @lc app=leetcode.cn id=387 lang=cpp
 *
 * [387] 字符串中的第一个唯一字符
 */

// @lc code=start
class Solution {
    public:
    int firstUniqChar(string s)
    {
        unordered_map<char, pair<int, int>> m;
        int idx = s.size();
        for (int i = 0; i < s.size(); i++) {
            m[s[i]].first++;
            m[s[i]].second = i;
        }
        for (auto& p : m) {
            if (p.second.first == 1) {
                idx = min(idx, p.second.second);
            }
        }
        return idx == s.size() ? -1 : idx;
    }
};
/*
Accepted
104/104 cases passed (80 ms)
Your runtime beats 33.63 % of cpp submissions
Your memory usage beats 82.77 % of cpp submissions (12.9 MB)
*/
```

自己写的：

```C++
/*
 * @lc app=leetcode.cn id=387 lang=cpp
 *
 * [387] 字符串中的第一个唯一字符
 */

// @lc code=start
class Solution {
    public:
    int firstUniqChar(string s)
    {
        unordered_map<char, int> hashmap;
        for (char c : s) {
            hashmap[c]++;
        }
        for (int i = 0; i < s.length(); i++) {
            if (hashmap[s[i]] == 1)
                return i;
        }
        return -1;
    }
};
/*
Accepted
104/104 cases passed (92 ms)
Your runtime beats 21.45 % of cpp submissions
Your memory usage beats 75.52 % of cpp submissions (13.1 MB)
使用map，第一遍存储数据，第二遍进行循环
*/
```

