# 原题：

```
Given a string, find the length of the longest substring without repeating characters.

Example 1:

Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        subLen = len(s)
        if subLen == 0:
            return 0
        while(subLen > 0):
            for i in range(len(s) - subLen + 1):
                dic = {}
                for j in s[i:i+subLen]:
                    if j in dic:
                        break
                    else:
                        dic[j] = 1
                if len(dic) == subLen:
                    return subLen
            subLen -= 1
```
最终结果：Time Limit Exceeded

查看了一下没通过的用例，是一个超长字符串，所以超时肯定是由于字符串长度太大了。
思考方向是如何减小搜索的子串长度，首先想字符的数量是有限的，在网上查了一个有ASCII码的字符是128个，
将min(128, len(s))作为初始值，比直接将len(s)作为初始值肯定要快很多很多。

### 第二次提交
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        subLen = min(128,len(s))
        while(True):
            for i in range(len(s) - subLen + 1):
                dic = {}
                for j in s[i:i+subLen]:
                    if j in dic:
                        break
                    else:
                        dic[j] = 1
                if len(dic) == subLen:
                    return subLen
            subLen -= 1
```
最终结果：Time Limit Exceeded

没通过的是同一个用例，也就是说还是初始值太大，导致了很多无用的搜索。
考虑到返回子串的长度应该有一个上界，上界值是原始字符串的不重复的字符数，还可以改进。

### 第三次提交
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        letter = set()
        for i in s:
            letter.add(i)
        subLen = len(letter)
        while(True):
            for i in range(len(s) - subLen + 1):
                dic = {}
                for j in s[i:i+subLen]:
                    if j in dic:
                        break
                    else:
                        dic[j] = 1
                if len(dic) == subLen:
                    return subLen
            subLen -= 1
```
最终结果：316 ms	13 MB

用元组获取子串长度上界，作为初始值再进行搜索。

### 大佬的解法
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        string = ""
        result = 0
        for i in s:
            if i in string:
                string = string[string.index(i)+1:]+i
            else:
                string += i
            result = max(result, len(string))
        return result
```
最终结果：48 ms	12.1 MB

这也太精妙了，怎么想出来的啊...

## Java
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        String str = "";
        int result = 0;
        for(int i = 0; i < s.length(); i++){
        	char c = s.charAt(i);
            if (str.contains(c+"")){
                str = str.substring(str.indexOf(c)+1,str.length())+c;
            }else {
            	str += c;
            }
            result = result > str.length() ? result : str.length();
        }
        return result;
    }
}
```
最终结果：13 ms	37.6 MB
