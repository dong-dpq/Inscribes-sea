# 原题：Two Sum

```
Given an array of integers, return indices of the two numbers 
such that they add up to a specific target.
You may assume that each input would have exactly one solution,
and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)):
            rest = target - nums[i]
            for j in range(len(nums)):
                if rest == nums[j] and i != j:
                    return [min(i,j),max(i,j)]
```
最终结果：  5220 ms	12.7 MB	
这个算法最坏的情况需要比较n方次，时间复杂度太高。

### 第二次提交
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        dic = {}
        for i in range(len(nums)):
            rest = target - nums[i]
            if rest not in dic:
                dic[nums[i]] = i
            else:
                return [dic[rest],i]
```
最终结果：  32 ms	13.4 MB
用字典存储已遍历过的列表元素和索引，牺牲了一点存储空间，但是最坏的情况只需要比较n方/2次，速度大幅提升。

## Java
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
		int[] list = {0,0};
        for(int i = 0;i < nums.length ;i++){
            int rest = target - nums[i];
            if(!map.containsKey(rest)) {
            	map.put(nums[i],i);
            }else {
            	list[0] = map.get(rest);
            	list[1] = i;
            	return list;
            }
        }
        return list;
    }
}
```
最终结果：  2 ms	38.2 MB
