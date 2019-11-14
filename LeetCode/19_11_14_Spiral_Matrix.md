# 原题：

```
Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

Example 1:

Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
Example 2:

Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<Integer>();
        if(matrix.length == 0 || matrix[0].length == 0){
            return result;
        }else{
            getBorder(result, matrix, "right",new int[]{0,0,matrix.length-1,matrix[0].length-1});
            return result;
        }
    }
    public void getBorder(List<Integer> result, int[][] matrix,String sign,int[] border){
        if(border[0] > border[2] || border[1] > border[3]){
            return ;
        }
        if(sign.equals("right")){
            for(int i = border[1];i<=border[3];i++){
                result.add(matrix[border[0]][i]);
            }
            getBorder(result, matrix, "down",new int[]{border[0]+1,border[1],border[2],border[3]});
        }else if(sign.equals("down")){
            for(int i = border[0]; i <= border[2];i++){
                result.add(matrix[i][border[3]]); 
            }
            getBorder(result, matrix, "left",new int[]{border[0],border[1],border[2],border[3]-1});
        }else if(sign.equals("left")){
            for(int i = border[3]; i >=border[1];i--){
                result.add(matrix[border[2]][i]); 
            }
            getBorder(result, matrix, "up",new int[]{border[0],border[1],border[2]-1,border[3]});
        }else{
            for(int i = border[2]; i >=border[0];i--){
                result.add(matrix[i][border[1]]);
            }
            getBorder(result, matrix, "right",new int[]{border[0],border[1]+1,border[2],border[3]});
        }
    }
}
```
最终结果：0 ms	34.7 MB

无话可说，就是不断的取某行或某列。

## Python
```

```
最终结果：
