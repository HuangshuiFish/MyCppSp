##LeetCode22括号生成

[22括号生成](https://leetcode-cn.com/problems/generate-parentheses/)

代码：

```c++
/*
 * @lc app=leetcode.cn id=22 lang=cpp
 *
 * [22] 括号生成
 */

// @lc code=start
class Solution {
    public:
    vector<string> ans;
    vector<string> generateParenthesis(int n)
    {
        generate(0, 0, n, "");
        return ans;
    }

    void generate(int left, int right, int n, string s)	//left左括号的个数，right右括号的个数，n单个括号的最大个数，s生成的括号组
    {
        if (left == n && right == n) {	//判断递归是否结束
            ans.push_back(s);
            return;
        }
        if (left < n) {	//左括号还可以再增加
            generate(left + 1, right, n, s + "(");
        }
        if (right < left) {//必须保证右括号<左括号，右括号才可以增加，此时的括号组才是合法的括号组
            generate(left, right + 1, n, s + ")");
        }
    }
};
/*
Accepted
8/8 cases passed (20 ms)
Your runtime beats 18.3 % of cpp submissions
Your memory usage beats 35.53 % of cpp submissions (17.4 MB)
*/
```



收获：

1. 递归的写法（四步）。![递归模板](C:\Users\17820\AppData\Roaming\Typora\typora-user-images\1571887167069.png)
2. 自顶向下的编程方法。