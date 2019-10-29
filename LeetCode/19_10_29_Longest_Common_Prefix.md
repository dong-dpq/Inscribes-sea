# 原题：

```
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0 || Arrays.asList(strs).contains("")){
            return "";
        }else if(strs.length == 1){
            return strs[0];
        }else{
            String result = "";
            int commonIndex = 0;
            boolean flag = true;
            while(flag && commonIndex < strs[0].length()){
                char c = strs[0].charAt(commonIndex);
                for(int i = 1; i < strs.length; i++){
                    if(commonIndex >= strs[i].length() || strs[i].charAt(commonIndex) != c ){
                        flag = false;
                        break;
                    }
                }
                if (flag){
                    result += c;
                }
                commonIndex++;
            }
            return result;
        }
    }
}
```
最终结果：1 ms	37.7 MB

思维有点打结。


### 大佬的方法
```
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";
    for (int i = 0; i < strs[0].length() ; i++){
        char c = strs[0].charAt(i);
        for (int j = 1; j < strs.length; j ++) {
            if (i == strs[j].length() || strs[j].charAt(i) != c)
                return strs[0].substring(0, i);             
        }
    }
    return strs[0];
}
```

## Python
```
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if("" in strs or len(strs) == 0):
            return "";
        elif(len(strs) == 1):
            return strs[0];
        else:
            result = "";
            for i in range(len(strs[0])):
                c = strs[0][i];
                for item in strs[1:]:
                    if i >= len(item) or item[i] != c:
                        return result;
                result += c;
            return result;
```
最终结果：24 ms	11.8 MB
