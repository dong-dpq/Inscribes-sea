# 原题：

```
Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in-place.

Example 1:

Input: 
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
Output: 
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]
Example 2:

Input: 
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
Output: 
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
Follow up:

A straight forward solution using O(mn) space is probably a bad idea.
A simple improvement uses O(m + n) space, but still not the best solution.
Could you devise a constant space solution?
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public void setZeroes(int[][] matrix) {
        
        if(matrix.length == 0 || matrix[0].length==0){
            return ;
        }else{
            int m = matrix.length;
            int n = matrix[0].length;
            int[] flagRow = new int[m];
            int[] flagCol = new int[n];
            for(int i = 0;i< m;i++){
                for(int j= 0;j<n;j++){
                    if(matrix[i][j] == 0){
                        flagRow[i] = 1;
                        flagCol[j] = 1;
                    }
                }
            }
            for(int i = 0;i< m;i++){
                for(int j= 0;j<n;j++){
                    if(flagRow[i] == 1 || flagCol[j] == 1){
                        matrix[i][j] = 0;
                    }
                }
            }
        }
    }
}
```
最终结果：1 ms	43.7 MB

这个是O(m + n) space的解法，O(1)的不知道该怎么写。。


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
