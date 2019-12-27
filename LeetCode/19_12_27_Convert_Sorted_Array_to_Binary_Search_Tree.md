# 原题：

```
Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

Example:

Given the sorted array: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
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
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums.length == 0){
            return null;
        }
        return fun(nums, 0, nums.length-1);
    }
    public TreeNode fun(int[] nums, int beg, int end){
        if(beg > end){
            return null;
        }
        int rootNum = (beg + end)/2;
        TreeNode root = new TreeNode(nums[rootNum]);
        root.left = fun(nums, beg, rootNum-1);
        root.right = fun(nums, rootNum+1, end);
        return root;
    }
}
```
最终结果：0 ms	37 MB

注意是二叉搜索树..用递归解..


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
