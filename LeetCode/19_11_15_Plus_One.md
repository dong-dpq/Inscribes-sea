# 原题：

```
Given a non-empty array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

Example 1:

Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
Example 2:

Input: [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int[] plusOne(int[] digits) {
        int n = digits.length,sign=0;
        //non-empty
        List<Integer> list = new ArrayList<Integer>();
        for(int i = n-1;i>=0;i--){
            int addNum = 0;
            if(i == n-1){
                addNum = digits[i]+1+sign;
            }else{
                addNum = digits[i]+sign;
            }
            if(addNum >= 10){
                list.add(0, addNum%10);
                sign = 1;
            }else{
                list.add(0, addNum);
                sign = 0;
            }
        }
        if(sign == 1){
            list.add(0, 1);
        }
        int[] result = new int[list.size()];
        for(int i=0;i< list.size();i++){
            result[i] = list.get(i);
        }
        return result;
    }
}
```
最终结果：1 ms	35.4 MB

没啥意思的一个题..可以通过找末位的9的个数来做（XXX999）更快.


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
