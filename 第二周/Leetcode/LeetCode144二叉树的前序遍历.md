## LeetCode144二叉树的前序遍历

[144二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)

代码：

```c++
/*
 * @lc app=leetcode.cn id=144 lang=cpp
 *
 * [144] 二叉树的前序遍历
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
    vector<int> preorderTraversal(TreeNode* root)
    {
        if (root) {
            ans.push_back(root->val);
            preorderTraversal(root->left);
            preorderTraversal(root->right);
        }
        return ans;
    }
};
/*
Accepted
68/68 cases passed (4 ms)
Your runtime beats 81.89 % of cpp submissions
Your memory usage beats 5.1 % of cpp submissions (11.2 MB)
*/
```

