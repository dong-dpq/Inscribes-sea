# 原题：

```
Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
return its zigzag level order traversal as:
[
  [3],
  [20,9],
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
    private List<List<Integer>> result = new ArrayList<List<Integer>>();
    
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        if(root == null){
            return result;
        }else{
            result.add(new ArrayList<Integer>());
            fun(root, 0);
            return result;
        }
    }
    public void fun(TreeNode root,int depth){
        if(depth %2 ==1){
            result.get(depth).add(0, root.val);
        }else{
            result.get(depth).add(root.val);
        }
        if(root.left != null || root.right != null){
            if(result.size() == depth + 1 ){
                result.add(new ArrayList<Integer>()); 
            }
            if(root.left != null){
                fun(root.left, depth+1);
            }
            if(root.right != null){
                fun(root.right, depth+1);
            }
        }
    }
}
```
最终结果：0 ms	36.4 MB

递归...在插入链表的时候进行判别..


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
