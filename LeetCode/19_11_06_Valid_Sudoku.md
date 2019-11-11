# 原题：

```
Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the 9 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition.

A partially filled sudoku which is valid.

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

Example 1:

Input:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: true
Example 2:

Input:
[
  ["8","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being 
    modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
The given board contain only digits 1-9 and the character '.'.
The given board size is always 9x9.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        Map<Character,Integer>[] col = new HashMap[9];
        Map<Character,Integer>[] row = new HashMap[9];
        Map<Character,Integer>[] part = new HashMap[9];
        
        for(int i = 0; i < 9;i++){
            col[i] = new HashMap<Character,Integer>();
            row[i] = new HashMap<Character,Integer>();
            part[i] = new HashMap<Character,Integer>();
        }
        
        
        for(int i = 0; i < 9;i++){
            for(int j = 0; j < 9;j++){
                char c = board[i][j];
                if( c != '.'){
                    if(row[i].containsKey(c)){
                        return false;
                    }else{
                        row[i].put(c, 1);
                    }
                    if(col[j].containsKey(c)){
                        return false;
                    }else{
                        col[j].put(c, 1);
                    }
                    int temp = (int)(i/3)*3+(int)(j/3);
                    if(part[temp].containsKey(c)){
                        return false;
                    }else{
                        part[temp].put(c, 1);
                    }
                }
            }
        }
        return true;
    }
}
```
最终结果：3 ms	44 MB

最开始的想法是，逐一判断每一行每一列和每一块，但是这样得遍历3*n*n。
看大佬解法之后，可以维护27个map（9个行，9个列，9个块），遍历一次做到。


## Python

```

```
最终结果：  


