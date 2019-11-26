# 原题：

```
A message containing letters from A-Z is being encoded to numbers using the following mapping:

'A' -> 1
'B' -> 2
...
'Z' -> 26
Given a non-empty string containing only digits, determine the total number of ways to decode it.

Example 1:

Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).
Example 2:

Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

# 提交
## Java
### 第一次提交
```
class Solution {

    public int fun(String s,int index){
        if(index == s.length()){
            return 1;
        }else if(index == s.length()-1 && s.charAt(index) != '0'){
            return 1;
        }else if(s.charAt(index) != '0'){
            String str = "";
            str+=s.charAt(index);
            str+=s.charAt(index+1);
            int temp = Integer.valueOf(str);
            if(temp <=26){
                return fun(s,index+1)+fun(s,index+2);
            }else{
                return fun(s,index+1);
            }
        }else{
            return 0;
        }
    }
    public int numDecodings(String s) {
        int n = s.length();
        if(0 == n){
            return 0;
        }
        return fun(s,0);
    }
}
```
最终结果：Time Limit Exceeded

超时了...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
