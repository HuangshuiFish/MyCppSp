## LeetCode94二叉树的中序遍历

[94二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

代码：

```c++
/*
 * @lc app=leetcode.cn id=94 lang=cpp
 *
 * [94] 二叉树的中序遍历
 */

// @lc code=start
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
    public:
    vector<int> ans;
    vector<int> inorderTraversal(TreeNode* root)
    {
        //vector<int> ans;  不能把这个放在这，因为每次都会调用递归函数，会重新建立一个ans
        if (root) {
            inorderTraversal(root->left);  //递归，再次调用inorderTraversal函数
            ans.push_back(root->val);
            inorderTraversal(root->right);
        }
        return ans;
    }
};
/*
Accepted
68/68 cases passed (8 ms)
Your runtime beats 34.56 % of cpp submissions
Your memory usage beats 5.26 % of cpp submissions (11.1 MB)
*/
```



收获：

1. 二叉树的中序遍历（左-根-右）。
2. 递归函数中不要有存储输出数据的结构，因为每一次都会调用递归函数。
3. 递归函数的写法：[数据结构与算法之美递归篇](https://time.geekbang.org/column/article/41440)  找到递推公式和终止条件，不要试图分解递归的每个步骤。



