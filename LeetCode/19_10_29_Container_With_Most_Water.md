# 原题：

```
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

 



The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

 

Example:

Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int maxArea(int[] height) {
        int maxWater = 0;
        for(int i = 0; i < height.length; i++){
            for(int j = i+1; j < height.length;j++){
                int temp = (j-i)*Math.min(height[i],height[j]);
                maxWater = temp>maxWater?temp:maxWater;
            }
        }
        return maxWater;
    }
}
```
最终结果：196 ms	40.1 MB

暴力求解。Java能过，但是Python无法通过。


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
