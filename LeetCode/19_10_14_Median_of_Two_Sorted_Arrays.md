# 原题：

```
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

Example 1:

nums1 = [1, 3]
nums2 = [2]

The median is 2.0
Example 2:

nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

# 提交
## Python
### 第一次提交
```
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        
        a1 = 0
        a2 = len(nums1)-1
        b1 = 0
        b2 = len(nums2)-1
        
        while(a2+b2-a1-b1 > 0):
            if a1 > a2:
                if (b1+b2)%2 == 0:
                    return nums2[(b1+b2)/2]
                else:
                    return (nums2[(b1+b2-1)/2]+nums2[(b1+b2+1)/2])/2
            if b1 > b2:
                if (a1+a2)%2 == 0:
                    return nums1[(a1+a2)/2]
                else:
                    return (nums1[(a1+a2-1)/2]+nums1[(a1+a2+1)/2])/2
                
            if nums1[a1] < nums2[b1]:
                a1 += 1
            else:
                b1 += 1
            if nums1[a2] > nums2[b2]:
                a2 -= 1
            else:
                b2 -= 1
        return (nums1[a1]+nums2[b1])/2
```
最终结果：Wrong Answer

题中说的是cannot be both empty，结果我以为是两个都不会为空。。

### 第二次提交
```
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        a1 = 0
        a2 = len(nums1)-1
        b1 = 0
        b2 = len(nums2)-1
        while(True):
            if a1 > a2:
                if (b1+b2)%2 == 0:
                    return float(nums2[(b1+b2)/2])
                else:
                    return float(nums2[(b1+b2-1)/2]+nums2[(b1+b2+1)/2])/2
            if b1 > b2:
                if (a1+a2)%2 == 0:
                    return float(nums1[(a1+a2)/2])
                else:
                    return float(nums1[(a1+a2-1)/2]+nums1[(a1+a2+1)/2])/2
            if a2+b2-a1-b1 <= 0:
                break 
            if nums1[a1] < nums2[b1]:
                a1 += 1
            else:
                b1 += 1
            if nums1[a2] > nums2[b2]:
                a2 -= 1
            else:
                b2 -= 1
        return float(nums1[a1]+nums2[b1])/2
```
最终结果：76 ms	12 MB

感觉就是用了四个指针，不断的去掉一个最高分和最低分...但是时间复杂度好像有点问题

## Java
```

```
最终结果：
