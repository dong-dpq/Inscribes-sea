# 原题：

```
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:

The number of elements initialized in nums1 and nums2 are m and n respectively.
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.
Example:

Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        if(m==0){
            int end2=n-1;
            while(end2>=0){
                nums1[end2] = nums2[end2];
                end2--;
            }
        }else{
            int end1=m-1,end2=n-1;
            while(end1>=0 && end2>=0){
                if(nums1[end1] > nums2[end2]){
                    nums1[end1+end2+1] = nums1[end1];
                    end1--;
                }else{
                    nums1[end1+end2+1] = nums2[end2];
                    end2--;
                }
            }
            while(end1>=0){
                nums1[end1+end2+1] = nums1[end1];
                end1--;
            }
            while(end2>=0){
                nums1[end1+end2+1] = nums2[end2];
                end2--;
            }
        }
    }
}
```
最终结果：0 ms	36.3 MB

从后往前添加...

### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
