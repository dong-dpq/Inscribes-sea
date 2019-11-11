# 原题：

```
Given a collection of distinct integers, return all possible permutations.

Example:

Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public static List<List<Integer>> permute(int[] nums) {
        //队列
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        int n = nums.length;
        for(int i =0; i < n;i++){
            int lenList = result.size();
            if(lenList == 0){
                for(int j= 0;j < n;j++){
                    ArrayList<Integer> first = new ArrayList<Integer>();
                    first.add(nums[j]);
                    result.add(first);
                }
            }else{
                for(int k =0;k<lenList;k++){
                    List<Integer> head = result.remove(0);
                    for(int j= 0;j < n;j++){
                        if(!head.contains(nums[j])){
                        	List<Integer> temp =new ArrayList<Integer>();
                        	for(int m = 0;m<i;m++) {
                        		temp.add(head.get(m));
                        	}
                        	temp.add(nums[j]);
                            result.add(temp);
                        }
                    }
                }
            }
        }
        return result;
    }
}
```
最终结果：3 ms	37.9 MB	

用队列的思想，初始只有[[1], [2], [3]]，弹出一个队首元素[1]，然后新加入[1, 2], [1, 3]。
不断循环直至n个位置都被填满。

### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
