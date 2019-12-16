# 原题：

```
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Note: A leaf is a node with no children.

Example:

Given binary tree [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
return its depth = 3.
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
    public int fun(TreeNode root, int depth) {
        if(root == null){
            return depth-1;
        }else{
            return Math.max(fun(root.left,depth+1), fun(root.right,depth+1));
        }
    }
    
    public int maxDepth(TreeNode root) {
        if(root == null){
            return 0;
        }else{
            return fun(root,1);
        }
    }
}
```
最终结果：0 ms	38.5 MB

递归...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
