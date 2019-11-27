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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<Integer>();
        if(root == null){
            return list;
        }
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode useRoot = root;
        stack.push(useRoot);
        while(!stack.empty() ){
            while(useRoot.left != null){
                stack.push(useRoot.left);
                useRoot = useRoot.left;
            }
            
            if(stack.peek() != null){
                TreeNode temp = stack.pop();
                list.add(temp.val);
                if(temp.right != null){
                    stack.push(temp.right);
                    useRoot = temp.right;
                }
            }
        }
        return list;
    }
}
```
最终结果：	1 ms	34.7 MB

学了一手非递归的中序遍历...好难...

## Python
```

```
最终结果：
