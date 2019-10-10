# 原题：3 Sum

```
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note:

The solution set must not contain duplicate triplets.

Example:

Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        result = []
        for i in range(2,len(nums)):
            for j in range(0,i-1):
                for k in range(j+1,i):
                    if 0 == nums[i]+nums[j]+nums[k]:
                        a = min(nums[i],nums[j],nums[k])
                        b = max(nums[i],nums[j],nums[k])
                        temp = [a,0-a-b,b]
                        if temp not in result:
                            result.append(temp)
        return result
```
最终结果：Time Limit Exceeded


### 第二次提交
```

```
最终结果：

## Java
```

```
最终结果：
