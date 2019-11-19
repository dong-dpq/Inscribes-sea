# 原题：

```
Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public void fun(List<List<Integer>> result, int[] nums,int flag){
        if(flag == 0){
            for(int i : nums){
                List<Integer> temp = new ArrayList<Integer>();
                temp.add(i);
                result.add(0,temp);
            }
            fun(result,nums,1);
        }else if(flag>nums.length){
            return ;
        }else{
            for(int j=0;j<result.size();j++){
                List<Integer> temp = result.get(j);
                if(temp.size() == flag){
                    for(int i : nums){
                        if(i>temp.get(flag-1)){
                            //优化List<Integer> newSub = new ArrayList<Integer>(res.get(j));
                            List<Integer> item = new ArrayList<Integer>();
                            for(int k=0;k<flag;k++){
                                item.add(temp.get(k));
                            }
                            item.add(i);
                            result.add(item);
                        }
                    } 
                }
            }
            fun(result,nums,flag+1);
        }
    }

    public List<List<Integer>> subsets(int[] nums) {
        int n = nums.length;
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        if(0 == n){
            return result;
        }else{
            List<Integer> temp = new ArrayList<Integer>();
            result.add(temp);
            //sort
            for(int i=0;i<n-1;i++){
                for(int j =i+1;j<n;j++){
                    if(nums[i]>nums[j]){
                        int ex = nums[i];
                        nums[i] = nums[j];
                        nums[j] = ex;
                    }
                }
            }
            fun(result,nums,0);
            return result;
        }
    }
}
```
最终结果： ms	37.1 MB	

头晕脑胀的写了一道题...递归


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
