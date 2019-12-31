[LeetCode8](https://leetcode-cn.com/problems/string-to-integer-atoi/)

自己写的：

```c++
/*
 * @lc app=leetcode.cn id=8 lang=cpp
 *
 * [8] 字符串转换整数 (atoi)
 */

// @lc code=start
class Solution {
    public:
    int myAtoi(string str)
    {
        int flag = 0;  //存储符号位
        long ans = 0;		//需要改进，不要用long来存储
        int index = 0;  //str的下标
        if (str.length() == 0) {
            return 0;
        }
        while (str[index] == ' ') {
            index++;
        }
        if (str[index] == '+') {
            flag = 1;
            index++;
        }
        else if (str[index] == '-') {
            flag = 2;
            index++;
        }
        while (str[index] >= '0' && str[index] <= '9') {
            if (ans == 0) {
                ans = str[index] - '0';
                index++;
            }
            else if (ans > INT_MAX || ans < INT_MIN) {
                return flag == 2 ? INT_MIN : INT_MAX;
            }
            else {
                ans = (str[index] - '0') + ans * 10;
                index++;
            }
        }
        if (ans > INT_MAX || ans < INT_MIN) {
            return flag == 2 ? INT_MIN : INT_MAX;
        }
        return flag == 2 ? -ans : ans;
    }
};
/*
Accepted
1079/1079 cases passed (4 ms)
Your runtime beats 91.78 % of cpp submissions
Your memory usage beats 80.77 % of cpp submissions (8.5 MB)
整体写得很繁琐，不够清晰
*/
```



其他人的程序：

```cpp
/*
 * @lc app=leetcode.cn id=8 lang=cpp
 *
 * [8] 字符串转换整数 (atoi)
 */

// @lc code=start
class Solution {
    public:
    int myAtoi(string str)
    {
        if (str.empty())
            return 0;
        int i = 0, sign = 1;
        while (i + 1 < str.size() && isspace(str[i]))
            ++i;
        long res = 0;
        if (str[i] == '-' || str[i] == '+')
            sign = 44 - str[i++];
        while (i < str.size()) {
            if (isdigit(str[i]))
                res = 10 * res + str[i++] - '0';
            else
                return res * sign;
            if (res > INT_MAX)
                return sign == -1 ? INT_MIN : INT_MAX;
        }
        return res * sign;
    }
};
/*
Accepted
1079/1079 cases passed (8 ms)
Your runtime beats 61.33 % of cpp submissions
Your memory usage beats 84.57 % of cpp submissions (8.4 MB)
*/
```

