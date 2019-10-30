# 原题：

```
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<String>();
        if(n == 0){return list;}
        fun(list,"(",1,0,n);
        return list;
    }
    
    public void fun(List<String> list, String ans, int left,int right, int n){
        if(left == n && right == n-1){
            list.add(ans+')');
        }
        if(left > n || right > n-1 || left < right){
            return ;
        }else{
            fun(list,ans+'(',left+1,right,n);
            fun(list,ans+')',left,right+1,n);
        }
    }
}
```
最终结果：1 ms	36.3 MB

有思路但是不会写...学习了一下递归，总算写出来了...

## Python
```

```
最终结果：
