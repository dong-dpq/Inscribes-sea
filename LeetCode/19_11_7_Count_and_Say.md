# 原题：

```
The count-and-say sequence is the sequence of integers with the first five terms as following:

1.     1
2.     11
3.     21
4.     1211
5.     111221
1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.

Given an integer n where 1 ≤ n ≤ 30, generate the nth term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string.

 

Example 1:

Input: 1
Output: "1"
Example 2:

Input: 4
Output: "1211"
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public String countAndSay(int n) {
        String s = "1";
        if(n == 0){
            return s;
        }else{
            for(int i = 1;i < n;i++){
                s = nextStr(s);
            }
            return s;
        }
    }
    public String nextStr(String s){
        String result = "";
        for(int i = 0; i < s.length(); ){
            char c = s.charAt(i);
            int count =1;
            while(true){
                if(i+1<s.length() && c==s.charAt(i+1)){
                    count += 1;
                    i += 1;
                }else{
                    result += ""+ count + c;
                    i += 1;
                    break;
                }
            }
        }
        return result;
    }
}
```
最终结果：7 ms	36 MB

没啥可说的，就是用count记录重复次数。


## Python
```

```
最终结果：
