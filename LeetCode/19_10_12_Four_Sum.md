# 原题：4Sum

```
Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums 
such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note:

The solution set must not contain duplicate quadruplets.

Example:

Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        if len(nums) < 4:
            return []
        nums.sort()
        result = set()
        
        for i in range(len(nums)-2):
            left3 = target - nums[i]
            for j in range(i+1, len(nums) - 1):
                left2 = left3 - nums[j]
                dic = {}
                for k in range(j+1, len(nums)):
                    left = left2 - nums[k]
                    if left in dic:
                        result.add(tuple(sorted([nums[i], nums[j], nums[k], left])))
                    else:
                        dic[nums[k]] = k
        return list(result)
            
```
最终结果：868 ms	11.7 MB

思路跟3sum一样，只是多了一层循环。一遍过~

## Java
```
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Set<List<Integer>> set = new HashSet<List<Integer>>();
        Map<Integer,Integer> map ;
        List<Integer> childList ;
        Arrays.sort(nums);
        for(int i = 0; i < nums.length - 2; i++){
            int left3 = target - nums[i];
            for (int j = i+1; j < nums.length - 1; j++){
                int left2 = left3 - nums[j];
                map = new HashMap<Integer,Integer>();
                for(int k = j+1; k < nums.length; k++){
                    int left = left2 - nums[k];
                    if (map.containsKey(left)){
                        childList = new ArrayList<Integer>();
                        childList.add(nums[i]);
                        childList.add(nums[j]);
                        childList.add(left);
                        childList.add(nums[k]);
                        set.add(childList);
                    }else{
                        map.put(nums[k], k);
                    }
                }
            }
        }
        return new ArrayList<List<Integer>>(set);
    }
}
```
最终结果：258 ms	58.5 MB

add、append和put给我搞糊涂了。
