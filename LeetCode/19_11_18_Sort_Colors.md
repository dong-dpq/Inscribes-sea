# 原题：

```
Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Note: You are not suppose to use the library's sort function for this problem.

Example:

Input: [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
Follow up:

A rather straight forward solution is a two-pass algorithm using counting sort.
First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.
Could you come up with a one-pass algorithm using only constant space?
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public void sortColors(int[] nums) {
        int n = nums.length;
        if(0 == n){
            return ;
        }else{
            int beg =0,end=n-1,i=0;
            while(i<=end){
                if(0 == nums[i]){
                    nums[i] = nums[beg];
                    nums[beg] = 0;
                    beg++;
                    i++;
                }else if(2 == nums[i]){
                    nums[i] = nums[end];
                    nums[end] = 2;
                    end--;
                }else{
                    i++;
                }
            }
        }
    }
}
```
最终结果：0 ms	35.1 MB

知道用多指针来写...但是用了三个，写的有点蒙..不知道双指针是不是就够了...


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
