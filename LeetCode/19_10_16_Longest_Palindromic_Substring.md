# 原题：

```
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:

Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
Example 2:

Input: "cbbd"
Output: "bb"
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        n = len(s)
        if n == 0:
            return ""
        while(n > 0):
            for i in range(len(s) - n + 1):
                start = i
                end = i + n - 1
                while(True):
                    if end <= start:
                        return s[i:i + n]
                    if s[start] != s[end]:
                        break
                    else:
                        start += 1
                        end -= 1
            n -= 1
```
最终结果：Time Limit Exceeded

暴力求解，遍历所有的子串，从长到短判断它们是不是回文，如果是就直接返回，直到子串的长度为1。但是对于长度1000，回文子串长度499的用例没通过。


### 第二次提交
```
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        n = len(s)
        if n == 0:
            return ""
        while(n > 0):
            for i in range(len(s) - n + 1):
                if s[i:i + n] == s[i:i + n][::-1]:
                    return s[i:i + n]
            n -= 1
```
最终结果：5052 ms	11.7 MB

同学跟我说，判断是否回文不用一个个字符遍历判断，直接用s和s[::-1]比较就行。emmm虽然通过了，但是速度还是好慢。

### 第三次提交
```
class Solution(object):
    def longestPalindrome(self, s): 
        """
        :type s: str
        :rtype: str
        """
        sta = 0
        end = 0
        for i in range(len(s)):
            left, right = i, i
            while(left >= 0 and right <= len(s) -1 and s[left] == s[right]):
                left -= 1
                right += 1
            len1 = right - left - 1
            left, right = i, i+1
            while(left >= 0 and right <= len(s) -1 and s[left] == s[right]):
                left -= 1
                right += 1
            len2 = right - left - 1
            maxL = max(len1,len2)
            if maxL > end-sta:
                sta = i - (maxL-1)/2
                end = sta + maxL - 1
        return s[sta:end+1]
```
最终结果：888 ms	11.9 MB

参考大佬的扩展中心解法，每次循环选择一个中心，进行左右扩展，判断左右字符是否相等。


## Java
```

```
最终结果：
