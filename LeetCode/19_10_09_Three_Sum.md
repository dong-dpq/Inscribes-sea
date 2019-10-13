# 原题：3 Sum

```
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? 
Find all unique triplets in the array which gives the sum of zero.

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

暴力求解，大部分用例都通过了，但是代码运行速度太慢。看评论区的大佬代码，可以用元组来储存结果，可以自动去重；
还可以用字典来进行元素的储存和查找，速度比列表更快。

### 第二次提交
```
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        
        result = set()
        nums.sort()
        
        for i in range(len(nums) - 1):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            if nums[i] > 0:
                break
            dic = {}
            for j in range(i+1, len(nums)):
                left = -(nums[i] + nums[j])
                if left in dic.keys():
                    result.add(tuple([nums[i],left,nums[j]]))
                else:
                    dic[nums[j]] = j
        return list(result)         
```
最终结果：Time Limit Exceeded

琢磨了很久，发现dic.keys()返回的仍然是一个列表，也就是还是在用列表进行查询，速度依旧很慢。  

### 第三次提交
```
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        
        result = set()
        nums.sort()
        
        for i in range(len(nums) - 1):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            if nums[i] > 0:
                break
            dic = {}
            for j in range(i+1, len(nums)):
                left = -(nums[i] + nums[j])
                if left in dic:
                    result.add(tuple([nums[i],left,nums[j]]))
                else:
                    dic[nums[j]] = j
        return list(result)              
```
最终结果：680 ms	15.2 MB

把dic.keys()改成dic，速度大幅提升。ps没记错的话字典是用hashmap存储，列表是用链表存储。

## Java
### 第一次提交
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> list = new ArrayList<List<Integer>>();
        List<Integer> childList;
        HashMap<Integer,Integer> map;
        Arrays.sort(nums);
        for(int i = 0; i < nums.length-1; i++){
            if(nums[i] > 0){
                break;
            }
            map = new HashMap<Integer,Integer>();
            for(int j = i+1; j < nums.length; j++){
                int left = -nums[i] - nums[j];
                if (map.containsKey(left)){
                    childList = new ArrayList<Integer>();
                    childList.add(nums[i]);
                    childList.add(left);
                    childList.add(nums[j]);
                    childList.sort(null);
                    if (!list.contains(childList)){
                        list.add(childList);
                    }
                }else{
                    map.put(nums[j], j);
                }
            }
        }
        return list;  
    } 
}
```
最终结果：Time Limit Exceeded

在判断list是否包含childList的时候，是链表查询，仍然太慢了。

### 第二次提交
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        // List<List<Integer>> list = new ArrayList<List<Integer>>();
        List<Integer> childList;
        Map<Integer,Integer> map;
        Set<List<Integer>> set = new  HashSet<List<Integer>>();
        Arrays.sort(nums);
        for(int i = 0; i < nums.length-1; i++){
            if(nums[i] > 0){
                break;
            }
            map = new HashMap<Integer,Integer>();
            for(int j = i+1; j < nums.length; j++){
                int left = -nums[i] - nums[j];
                if (map.containsKey(left)){
                    childList = new ArrayList<Integer>();
                    childList.add(nums[i]);
                    childList.add(left);
                    childList.add(nums[j]);
                    childList.sort(null);
                    set.add(childList);
                }else{
                    map.put(nums[j], j);
                }
            }
        }
        return new ArrayList<List<Integer>>(set);
    }  
}

```
最终结果：579 ms	50.9 MB

发现java和python中，set是共通的，map对应dic。


