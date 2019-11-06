# 原题：

```
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

Example 1:

Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
Example 2:

Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int search(int[] nums, int target) {
        int n = nums.length;
        if(n == 0){
            return -1;
        }else if(n == 1){
            return nums[0] == target?0:-1;
        }else{
            int ptr = 0;
            int sign = target>nums[0]?1:-1;
            while(true){
                if(nums[ptr] == target){
                    return ptr;
                }
                if((sign > 0 && nums[(ptr+n+1)%n]<nums[ptr])||
                   (sign < 0 && nums[(ptr+n-1)%n]>nums[ptr])){
                    return -1;
                }
                ptr = (ptr+n+sign)%n;
            }
        }
    }
}
```
最终结果：0 ms	39.9 MB

思路是想办法优化逐个比较的暴力法。上面的方法优化后，利用大小关系，不需要将所有元素进行遍历，但是时间复杂度是O(n)。

### 第二次提交
```
class Solution {
    public int search(int[] nums, int target) {
        int n = nums.length;
        if(n == 0){
            return -1;
        }else if(n == 1){
            return nums[0] == target?0:-1;
        }else{
            //二分找边界
            int beg =0, end = n-1,border = -1;
            if( nums[beg] < nums[end] ){
                border = n-1;
            }else{
                while(true){
                    int mid = (int) (end + beg)/2;
                    if(end - beg <= 1){
                        border = beg;
                        break;
                    }else if(nums[mid] > nums[beg]){
                        beg = mid;
                    }else{
                        //nums[mid] < nums[end]
                        end = mid;
                    }
                }
            }
            //二分找target
            int s_beg = 0,s_end=n-1;
            if(target > nums[0]){
                s_end = border; 
            }else if(target < nums[0]){
                s_beg = border + 1;
            }else{
                return 0;
            }
            while(s_beg <= s_end){
                int s_mid = (int)(s_beg+s_end)/2;
                if(nums[s_mid] == target){
                    return s_mid;
                }else if(target > nums[s_mid]){
                    s_beg = s_mid +1;
                }else{
                    s_end = s_mid -1;
                }
            }
            return -1;
        }
    }
}
```
最终结果：0 ms	40.9 MB

参考了大佬的方法。采用两次二分法，第一次寻找旋转的边界，第二次查找目标值。

## Python
```

```
最终结果：
