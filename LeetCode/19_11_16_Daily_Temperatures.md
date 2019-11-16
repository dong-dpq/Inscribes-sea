# 原题：

```
Given a list of daily temperatures T, return a list such that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.

For example, given the list of temperatures T = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0].

Note: The length of temperatures will be in the range [1, 30000]. Each temperature will be an integer in the range [30, 100].
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int[] dailyTemperatures(int[] T) {
        int n = T.length;
        if(n == 0){
            return new int[0];
        }else{
            int[] result = new int[n];
            result[n-1] = 0;
            for(int i = n-2;i>=0;i--){
                int dis = 1;
                while(true){
                    if(T[i] >= T[i+dis] && result[i+dis] == 0){
                        result[i] = 0;
                        break;
                    }else if(T[i] < T[i+dis] || result[i+dis] == 0){
                        result[i] = dis;
                        break;
                    }else{
                        dis += result[i+dis];
                    }
                }
            }
            return result;
        }
    }
}
```
最终结果：4 ms	42.9 MB

有点动态规划的感觉,倒序逐一进行判别...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
