# 原题：

```
Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Example 1:

Input: haystack = "hello", needle = "ll"
Output: 2
Example 2:

Input: haystack = "aaaaa", needle = "bba"
Output: -1
Clarification:

What should we return when needle is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length() == 0){
            return 0;
        }else if(needle.length() > haystack.length()){
            return -1;
        }else{
            for(int i = 0; i < haystack.length() - needle.length() + 1; i++){
                int flag = 1,j;
                for(j = 0; j < needle.length(); j++){
                    // System.out.println(haystack.charAt(i+j)+"------"+needle.charAt(j));
                    if(haystack.charAt(i+j) != needle.charAt(j)){
                        flag = -1;
                        break;
                    }
                }
                if(flag > 0){
                    return i;
                }
            }
            return -1;
        }
    }
}
```
最终结果：2 ms	37.9 MB

最笨的双指针法。

### 第二次提交
```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length() == 0){
            return 0;
        }else if(needle.length() > haystack.length()){
            return -1;
        }else{
            int n=needle.length();
            int[] dp = new int[n];
            dp[0] = 0;
            for(int i = 1,j = 0; i < n; i++){
                while(j > 0 && needle.charAt(j) != needle.charAt(i)){
                    j = dp[j - 1];
                }
                if(needle.charAt(i) == needle.charAt(j)){
                    j++;
                }
                dp[i] = j;
            }
            for(int k = 0; k < haystack.length()- needle.length() + 1;){
                for(int m = 0; m < n;){
                    if(haystack.charAt(k+m) == needle.charAt(m)){
                        m++;
                    }else if(m == 0){
                        k++;
                        break;
                    }else{
                        k = k + m - dp[m-1];
                        m = dp[m-1];
                        break; 
                    }
                    if(m >= n){
                        return k;
                    }
                }
            }
            return -1;
        }
    }
}
```
最终结果：3 ms	37.2 MB

学了一下KMP算法，好难懂qaq...

## Python
```

```
最终结果：
