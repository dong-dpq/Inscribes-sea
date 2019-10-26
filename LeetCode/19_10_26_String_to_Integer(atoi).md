# 原题：

```
Implement atoi which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

Note:

Only the space character ' ' is considered as whitespace character.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. If the numerical value is out of the range of representable values, INT_MAX (231 − 1) or INT_MIN (−231) is returned.
Example 1:

Input: "42"
Output: 42
Example 2:

Input: "   -42"
Output: -42
Explanation: The first non-whitespace character is '-', which is the minus sign.
             Then take as many numerical digits as possible, which gets 42.
Example 3:

Input: "4193 with words"
Output: 4193
Explanation: Conversion stops at digit '3' as the next character is not a numerical digit.
Example 4:

Input: "words and 987"
Output: 0
Explanation: The first non-whitespace character is 'w', which is not a numerical 
             digit or a +/- sign. Therefore no valid conversion could be performed.
Example 5:

Input: "-91283472332"
Output: -2147483648
Explanation: The number "-91283472332" is out of the range of a 32-bit signed integer.
             Thefore INT_MIN (−231) is returned.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int myAtoi(String str) {
        if(str == "" ){
            return 0;
        }
        String result = "";
        int indexOfFirst = -1;
        for(int i = 0; i < str.length(); i++){
            char c = str.charAt(i);
            if( c >= '0' && c <= '9'){
                if(result == ""){
                    indexOfFirst = i;
                }
                result += c;
            }else if(c == ' ' && indexOfFirst == -1){
                continue;
            }else if( (c == '-' || c == '+') && indexOfFirst == -1){
                if (i + 1 <= str.length() - 1 && (str.charAt(i+1) < '0' || str.charAt(i+1) > '9')){
                    return 0;
                }else{
                    continue;
                }
            }else{
                break;
            }
        }
        if(result == ""){
            return 0;
        }
        if(indexOfFirst > 0 && (str.charAt(indexOfFirst - 1) == '-') ){
            result = "-" + result;
            try{
                return Integer.parseInt(result);
            }catch(Exception e){
                return Integer.MIN_VALUE;
            }
        }else{
            try{
                return Integer.parseInt(result);
            }catch(Exception e){
                return Integer.MAX_VALUE;
            }
        }
}
```
最终结果：3 ms	36.3 MB

题目本身没有什么难处，但是各种边界条件太繁琐了。

### 第二次提交
```
class Solution {
    public int myAtoi(String str) {
        str = str.trim();
        if (str == "") return 0;
        int result = 0;
        int sign = 0;
        for(int i = 0; i < str.length(); i++){
            char c = str.charAt(i);
            if(c >= '0' && c <= '9'){
                int temp = c - '0';
                
                if((Integer.MAX_VALUE - temp)/10 < result){
                    return sign>=0? Integer.MAX_VALUE : Integer.MIN_VALUE;
                }
                result = result * 10 + temp;
            }else if(c=='-' && sign == 0 && i==0){
                sign = -1;
            }else if(c=='+' && sign == 0 && i==0){
                sign = 1;
            }else{
                break;
            }
        }
        return sign>=0?result:-result;
    }
}
```
最终结果：1 ms	36.1 MB

参考大佬的写法，优化了整个流程和数字溢出的判别。判别数字溢出的方法除了上面之外，还可以通过将result存成long型直接进行判别。

## Python
```
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        for i in range(len(str)):
            if str[i] == ' ':
                continue
            else:
                str = str[i:]
                break
        result = 0
        sign = 0
        for j in range(len(str)):
            c = str[j]
            if c >= '0' and c <= '9':
                num = int(c)
                result = result * 10 + num
                if result >= pow(2,31) and sign != -1:
                    return pow(2,31)-1
                elif result >  pow(2,31) and sign == -1:
                    return -pow(2,31)
                else:
                    continue
            elif c == '-' and sign ==0 and j == 0:
                sign = -1
            elif c == '+' and sign ==0 and j == 0:
                sign = 1
            else:
                break
        return -result if sign == -1 else result
```
最终结果：16 ms	11.7 MB

同样的思路，只不过用Python实现了一下trim()函数。
