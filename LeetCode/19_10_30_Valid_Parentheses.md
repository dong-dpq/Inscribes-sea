# 原题：

```
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:

Input: "()"
Output: true
Example 2:

Input: "()[]{}"
Output: true
Example 3:

Input: "(]"
Output: false
Example 4:

Input: "([)]"
Output: false
Example 5:

Input: "{[]}"
Output: true
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public boolean isValid(String s) {
        List<Character> list = new ArrayList<Character>();
        for(int i = 0; i < s.length(); i++){
            char c = s.charAt(i);
            if(c == '(' || c == '[' || c == '{'){
                list.add(0,c);
            }else if(list.size() == 0){
                return false;
            }else if(c == ')') {
                if(list.remove(0) != '('){
                    return false;
                }
            }else if(c == ']') {
                if(list.remove(0) != '['){
                    return false;
                }
            }else if(c == '}') {
                if(list.remove(0) != '{'){
                    return false;
                }
            }
        }
        if(list.size() > 0){
            return false;
        }else{
            return true;
        }
    }
}
```
最终结果：2 ms	34.3 MB	

简单地用栈来解决。看评论里有人说：其实可以增加一个判断：如果栈的深度大于字符串长度的1/2，
就返回false。因为当出现这种情况的时候，即使后面的全部匹配，栈也不会为空。

## Python
```

```
最终结果：
