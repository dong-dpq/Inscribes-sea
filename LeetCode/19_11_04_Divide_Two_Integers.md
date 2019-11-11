# 原题：

```
Given two integers dividend and divisor, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing dividend by divisor.

The integer division should truncate toward zero.

Example 1:

Input: dividend = 10, divisor = 3
Output: 3
Example 2:

Input: dividend = 7, divisor = -3
Output: -2
Note:

Both dividend and divisor will be 32-bit signed integers.
The divisor will never be 0.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 231 − 1 when the division result overflows.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int divide(int dividend, int divisor) {
        if(dividend == 0){
            return 0;
        }else if(dividend == -2147483648 && Math.abs(divisor)== 1){
            return divisor<0?2147483647:-2147483648;
        }else{
            int count = 0,flag = 0;
            if((dividend > 0 && divisor > 0) ||(dividend < 0 && divisor < 0)){
                flag = 1;
                count = dividend > 0? fun(-dividend,-divisor):fun(dividend,divisor);  
            }else{
                flag = -1;
                count = dividend > 0? fun(-dividend,divisor):fun(dividend,-divisor); 
            }
            return flag<0?-count:count;
        }
    }
    
    public int fun(int dividend, int divisor){
        if(divisor<dividend){
            return 0;
        }else{
            int temp = 1;
            int b =divisor;
            while(true){
                if(b < dividend - b){
                    break;
                }else{
                    temp+=temp;
                    b+=b;
                }
            }
            return temp+fun(dividend-b,divisor);
        }
        
    }
}
```
最终结果：1 ms	33.8 MB


### 第二次提交
```

```
最终结果：

## Python
```
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        #^ 表示bitwise XOR，在二进制下，0^1 = 1, 0^0=0, 1^1=0
        if dividend == 0:
            return 0
        
        MIN = -2147483648
        MAX = 2147483647
        
        if(dividend == MIN and divisor==-1):
            return MAX
        
        flag = (dividend>0) ^ (divisor>0)
        dividend = abs(dividend)
        divisor = abs(divisor)
        
        def fun(dividend,divisor):
            if(divisor>dividend):
                return 0
            else:
                temp =1
                b = divisor
                while(True):
                    # 这个地方改了的话在Java里面就溢出了
                    # 但是在python里面就没啥事，哈哈哈
                    if(b>dividend-b):
                        break
                    else:
                        temp +=temp
                        b += b
                
                # 当前的 divisor^(temp+1) >= dividend
                return temp+fun(dividend-b,divisor)
        m = fun(dividend,divisor)
        if  flag:
            m = -m
        if m > MAX:
            return MAX
        if m < MIN:
            return MAX
        return m
```
最终结果：
