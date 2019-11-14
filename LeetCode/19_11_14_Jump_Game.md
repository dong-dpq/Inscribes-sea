# 原题：

```
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

Example 1:

Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public boolean canJump(int[] nums) {
        int n = nums.length;
        if( 0 == n){
            return true;
        }else{
            int maxJump = 0;
            for(int i =0;i<n;i++){
                if(i>maxJump){
                    return false;
                }else{
                    maxJump = Math.max(i+nums[i],maxJump);
                }
            }
            return true;
        }  
    }
}
```
最终结果：1 ms	41 MB

时间复杂度O(n)，用maxJump记录可以跳的最远距离，通过遍历来不断更新maxJump值。


### 第二次提交 动态规划
```

```
最终结果：

## Python
```

```
最终结果：
