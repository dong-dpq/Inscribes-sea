# 原题：

```
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Note:

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

Example 1:

Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
Example 2:

Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public void rotate(int[][] matrix) {
        int n=matrix.length,temp=0;
        float center=(float)(n-1)/2;
        for(int i = 0;i < n;i++){
            for(int j=0;j < n;j++){
                //(i,j)->(k,m)
                int k=0,m=0;
                if(i < center && j <= center){
                    temp = matrix[i][n-j-1];
                    matrix[i][n-j-1] = matrix[j][i];
                    matrix[j][i] = temp;
                    
                    temp = matrix[n-j-1][n-i-1];
                    matrix[n-j-1][n-i-1] =matrix[j][i];
                    matrix[j][i] = temp;
                    
                    temp = matrix[n-i-1][j];
                    matrix[n-i-1][j] = matrix[j][i];
                    matrix[j][i] = temp;
                }
            }
        }
    }
}
```
最终结果：  0 ms	36.3 MB

先寻找矩阵的中心，然后将左上角区域的每个元素，旋转交换3次。笨方法，但是速度和内存使用都还可以...神奇

### 第二次提交
```

```
最终结果：
## Python
```

```
最终结果：
