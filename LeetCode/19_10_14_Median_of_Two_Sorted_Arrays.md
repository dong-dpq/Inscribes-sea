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

感觉就是用了四个指针，不断的去掉一个最高分和最低分...但是时间复杂度是O(m+n)，不符合要求....

### 第三次提交
```
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        if (len(nums1)>len(nums2)):
            nums1,nums2 = nums2,nums1
        a1 = 0
        a2 = len(nums1)
        hf = (len(nums1) + len(nums2) + 1)/2
        
        if len(nums1) == 0:
            return float(nums2[hf - 1]) if len(nums2)%2 == 1 else (nums2[hf]+nums2[hf-1])/2.0
        
        while(a1 <= a2):
            rightA = (a1 + a2+1)/2
            leftA = rightA -1        
            rightB = hf - rightA
            leftB = rightB -1

            if (rightA > 0  and nums1[leftA] > nums2[rightB]):
                a2 -= 1
            elif ( rightA < len(nums1) and nums1[rightA] < nums2[leftB]):
                a1 += 1
            else:
                if(rightA == 0):
                    maxLeft = nums2[leftB]
                elif(leftB < 0):
                    maxLeft = nums1[leftA]
                else:
                    maxLeft = max(nums2[leftB], nums1[leftA])
                    
                if(rightA == len(nums1)):
                    minRight = nums2[rightB]
                elif(rightB >= len(nums2)):
                    minRight = nums1[rightA]
                else:
                    minRight = min(nums2[rightB], nums1[rightA])

                if (len(nums1)+len(nums2))%2 == 1:
                    return float(maxLeft)
                else:
                    return float((maxLeft+minRight))/2
```
最终结果：72 ms	11.9 MB

核心思想是，找到两个列表的前(m+n+1)/2个最小的元素，最开始取第一个列表的前一半元素和第二个列表的前面部分元素，并且这两个部分的元素数量和要恒定为
(m+n+1)/2；然后不断调整这部分中的元素，如果这个集合中存在某个元素大于剩余部分的最小值，就进行交换；直至这个集合中的元素比剩余集合的元素都要小。
两个集合的边界就可以计算出所需要的中位数。

## Java
```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m = nums1.length;
        int n = nums2.length;
        
        if(m > n){
            return this.findMedianSortedArrays(nums2,nums1);
        }
        
        int hf = (m+n+1)/2;
        int a1 = 0;
        int a2 = m;
        int maxLeft = 0,minRight = 0;
        
        // if(m == 0){
        //     return n%2==1? nums2[hf - 1] :(nums2[hf]+nums2[hf-1])/2.0;
        // }
        
        while(a1 <= a2){
            int rightA = (a1+a2+1)/2;
            int leftA = rightA - 1;
            
            int rightB = hf - rightA;
            int leftB = rightB - 1;
            
            if (rightA < m && nums2[leftB] > nums1[rightA]){
                a1 += 1;
            }else if (leftA >= 0 && nums1[leftA] > nums2[rightB] ){
                a2 -= 1;
            }else{
                
                if(leftA < 0){
                    maxLeft = nums2[leftB];
                }else if(leftB < 0){
                    maxLeft = nums1[leftA];
                }else{
                    maxLeft = nums1[leftA] > nums2[leftB]? nums1[leftA]: nums2[leftB];
                }
                if((m+n)%2 == 1){
                    return maxLeft;
                }
                if(rightA >= m){
                    minRight = nums2[rightB];
                }else if(rightB >= n){
                    minRight = nums1[rightA];
                }else{
                    minRight = nums1[rightA] < nums2[rightB]? nums1[rightA]: nums2[rightB];
                }

                return (maxLeft + minRight)/2.0;
            }
        }
        return 0.0;
    }
}
```
最终结果：18 ms	47 MB

这个算法太复杂了...特别是判断游标和0、m的大小关系，时不时的就会数组越界...特别是对于用例[ [],[1] ]，需要将数组分奇偶拆开来处理，或者跟上面的python一样，加一个空数组判断。
