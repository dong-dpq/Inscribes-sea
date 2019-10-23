# 原题：

```
Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123
Output: 321
Example 2:

Input: -123
Output: -321
Example 3:

Input: 120
Output: 21
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int reverse(int x) {
        if(x < 10 && x > -10){
            return x;
        }else{
            int num = x<0?-x:x;
            int flag = x/num;
            String s = num+"";
            int beg=0,end = s.length()-1;
            String result = "";
            while(end >= 0){
                if(s.charAt(end) != '0' || beg > 0){
                    result += s.charAt(end);
                }
                beg+=1;
                end-=1;
            }
            return Integer.parseInt(result)*flag;
        }
        
    }
}
```
最终结果：Wrong Answer 

思路是把数字转化成字符串，然后逐个加入到新字符串中，再吧新字符串转化成数字。但是没有考虑越界的情况。


### 第二次提交
```
class Solution {
    public int reverse(int x) {
        if(x < 10 && x > -10){
            return x;
        }else{
            int num = x<0?-x:x;
            int flag = x/num;
            String s = num+"";
            int beg=0,end = s.length()-1;
            String result = "";
            while(end >= 0){
                if(s.charAt(end) != '0' || beg > 0){
                    result += s.charAt(end);
                }
                beg+=1;
                end-=1;
            }
            try{
                return Integer.parseInt(result)*flag;
            }catch(Exception e){
                return 0;
            }
        }
        
    }
}
```
最终结果：3 ms	34.2 MB	

加了一个try catch来处理溢出情况.

### 大佬的方法
```
class Solution {
    public int reverse(int x) {
        int a = 0;
        while(x!=0){
            int temp = x%10;
            if (a > Integer.MAX_VALUE/10 || (a == Integer.MAX_VALUE / 10 && temp > 7)) return 0;
            if (a < Integer.MIN_VALUE/10 || (a == Integer.MIN_VALUE / 10 && temp < -8)) return 0;
            a = a*10 + temp;
            x = (x - temp)/10;
        }
        return a;

    }
}
```
最终结果：1 ms	33.6 MB

没有涉及到字符串，纯数字的方法。用%10来获取末位数字，用*10+来把末位数字加到新数字后面。

## Python
### 第一次提交
```
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        if (x < 10 and x > -10):
            return x
        else:
            flag = x/abs(x)
            s = str(abs(x))
            result = ""
            beg = 0
            end = len(s) - 1
            while(end >= 0):
                if(s[end] != '0' or beg != 0):
                    result += s[end]
                beg += 1
                end -= 1
            num = int(result)*flag
            if num >= -pow(2,31) and num <pow(2,31):
                return num
            else:
                return 0 
```
最终结果：16 ms	11.7 MB	
