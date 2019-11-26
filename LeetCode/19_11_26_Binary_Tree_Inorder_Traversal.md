# 原题：

```
Given a binary tree, return the inorder traversal of its nodes' values.

Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
Follow up: Recursive solution is trivial, could you do it iteratively?
```

# 提交
## Java
### 第一次提交
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    
    public void fun(List<Integer> list, TreeNode root){
        if(root == null){
            return ;
        }
        fun(list, root.left);
        list.add(root.val);
        fun(list, root.right);
    }
    
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<Integer>();
        fun(list, root);
        return list;
    }
}
```
最终结果：0 ms	35.1 MB

直接递归解决...下一步想想用迭代算法...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
