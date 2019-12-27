# 原题：

```
Given preorder and inorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree.

For example, given

preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
Return the following binary tree:

    3
   / \
  9  20
    /  \
   15   7
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

//根据树前序遍历和中序遍历构建二叉树
//根据树后序遍历和中序遍历构建二叉树
//根据树前序遍历和后序遍历不能构建唯一的二叉树
class Solution {
    
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length == 0){
            return null;
        }else{
            /*
            TreeNode root = new TreeNode(preorder[0]);
            int flag = 0;
            for(int i = 0;i < inorder.length;i++){
                if(inorder[i] == preorder[0]){
                    flag = i;
                }
            }
            fun(root.left,preorder,inorder,0,flag-1,1,flag);*/
            TreeNode root = new TreeNode(-1);
            root = fun(preorder,inorder,0,inorder.length-1,0,preorder.length-1);
            return root;
        }
    }
    
    public TreeNode fun(int[] preorder,int[] inorder,int beg,int end,int index1,int index2){
        if(beg <= end){
            TreeNode root = new TreeNode(preorder[index1]);
            int flag = beg;
            for(int i = beg;i <= end;i++){
                if(inorder[i] == preorder[index1]){
                    flag = i;
                    break;
                }
            }
            root.left = fun(preorder,inorder,beg,flag-1,1+index1,index1+flag-beg);
            root.right = fun(preorder,inorder,flag+1,end,index1+flag-beg+1,index2);
            return root;
        }else{
            return null;
        }
    }
}
```
最终结果：10 ms	39.4 MB


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
