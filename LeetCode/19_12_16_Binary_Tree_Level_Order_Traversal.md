# 原题：

```
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
return its level order traversal as:
[
  [3],
  [9,20],
  [15,7]
]
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        List<Integer> list = new ArrayList<Integer>();
        if(root == null){
            return result;
        }else{
            result.add(list);
            fun(root, result, 0);
            return result;
        }
    }
    
    public void fun(TreeNode root, List<List<Integer>> result,int depth){
        result.get(depth).add(root.val);
        if(root.left != null || root.right != null){
            if(result.size() == depth + 1 ){
               List<Integer> list = new ArrayList<Integer>();
                result.add(list); 
            }
            if(root.left != null){
                fun(root.left, result, depth+1);
            }
            if(root.right != null){
                fun(root.right, result, depth+1);
            }
        }
    }
}
```
最终结果：0 ms	36.1 MB

递归...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
