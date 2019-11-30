# 原题：

```
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

    1
   / \
  2   2
 / \ / \
3  4 4  3
 

But the following [1,2,2,null,3,null,3] is not:

    1
   / \
  2   2
   \   \
   3    3
 
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
    public boolean isSymmetric(TreeNode root) {
        if(root == null){
            return true;
        }
        return fun(root, root);
    }
    public boolean fun(TreeNode node1, TreeNode node2){
        if(node1==null && node2 == null) {
            return true;
        }else if((node1!=null && node2 != null)&&(node1.val == node2.val)){
            return  fun(node1.left, node2.right) && fun(node1.right, node2.left);
        }else{
            return false;
        }
    }
}
```
最终结果：0 ms	37.6 MB

递归...再试试迭代...

### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
