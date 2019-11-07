# 原题：

```
Given an unsorted integer array, find the smallest missing positive integer.

Example 1:

Input: [1,2,0]
Output: 3
Example 2:

Input: [3,4,-1,1]
Output: 2
Example 3:

Input: [7,8,9,11,12]
Output: 1
Note:

Your algorithm should run in O(n) time and uses constant extra space.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        if(n == 0){
            return 1;
        }else{
            for(int i = 0; i < n; i++){
                // while(nums[i]<=n && nums[i] >0 && nums[i]>i+1){
                while(nums[i]<=n && nums[i] >0 && nums[i]!=nums[nums[i]-1]){
                    int temp = nums[nums[i]-1];
                    nums[nums[i]-1] = nums[i];
                    nums[i] = temp;
                }
            }
            for(int j = 0; j < n;j++){
                if(j+1 != nums[j]){
                    return j+1;
                }
            }
            return n+1;
        }
    }
}
```
最终结果：0 ms	35 MB

想了老久，感觉就差一点就自创桶排序了...但是最开始while的终止条件想不明白...看了大佬的才写出来。


## Python
```

```
最终结果：
