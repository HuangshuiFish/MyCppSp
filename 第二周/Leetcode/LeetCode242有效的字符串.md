## LeetCode242有效的字符串

[242有效的字符串](https://leetcode-cn.com/problems/valid-anagram/)



自己思考：

1. 暴力法求解（将s字符串中的字符一个个分离出来，在t字符串中查找有没有相同的字符。需要写双重循环）
2. 栈的思想（把s字符串压入栈，每次出栈的时候找t字符串有没有相对应的字符）
3. s建立HashMap，t中寻找是否有对应的key值。



老师解答：

1. 暴力法：先sort，之后比较两个sorted_array是否相等（O(nlogn))
2. hash,map   统计每个字母出现的频次



题解

1. 暴力法

   ```c++
   /*
    * @lc app=leetcode.cn id=242 lang=cpp
    *
    * [242] 有效的字母异位词
    */
   
   // @lc code=start
   class Solution {
       public:
       bool isAnagram(string s, string t)
       {
           sort(s.begin(), s.end());
           sort(t.begin(), t.end());
           return (s == t);
       }
   };
   /*
   Accepted
   34/34 cases passed (36 ms)
   Your runtime beats 27.52 % of cpp submissions
   Your memory usage beats 7.84 % of cpp submissions (9.5 MB)
   */
   ```

   

2. hash

   ```c++
   /*
    * @lc app=leetcode.cn id=242 lang=cpp
    *
    * [242] 有效的字母异位词
    */
   
   // @lc code=start
   class Solution {
       public:
       bool isAnagram(string s, string t)
       {
           if (s.length() != t.length()) {
               return false;
           }
           int n = s.length();
           unordered_map<char, int> count; //定义map
           for (int i = 0; i < n; ++i) {
               count[s[i]]++;  //s[i]是key，s[i]对应的value++
               count[t[i]]--;  //t[i]是key，t[i]对应的value++
           }
           for (auto j : count) {  //迭代器遍历
               if (j.second) { //访问map中的第二个对象（int)，检查所有的char对应的int是否为0
                   return false;
               }
           }
           return true;
       }
   };
   /*
   Accepted
   34/34 cases passed (16 ms)
   Your runtime beats 66.75 % of cpp submissions
   Your memory usage beats 5.14 % of cpp submissions (9.6 MB)
   */
   ```

   [C++unoedered_map](https://zh.cppreference.com/w/cpp/container/unordered_map)





