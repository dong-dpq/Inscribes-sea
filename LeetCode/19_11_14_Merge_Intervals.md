# 原题：

```
Given a collection of intervals, merge all overlapping intervals.

Example 1:

Input: [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
Example 2:

Input: [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
NOTE: input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public int[][] merge(int[][] intervals) {
        int n = intervals.length;
        if(0 == n){
            return new int[0][0];
        }else{
            ArrayList<Integer> list = new ArrayList<Integer>();
            //sort
            for(int i =0;i < n-1;i++){
                for(int j=i+1;j<n;j++){
                    if(intervals[i][0]>intervals[j][0]){
                        int[] temp = new int[2];
                        temp = intervals[j];
                        intervals[j] = intervals[i];
                        intervals[i] = temp;
                    }
                }
            }
            int left =intervals[0][0],right=intervals[0][1];
            for(int i = 0,j=1;i<n-1&&j<n;){
                if(right < intervals[j][0]){
                    list.add(left);
                    list.add(right);
                    i=j;
                    j++;
                    left = intervals[i][0];
                    right = intervals[i][1];
                }else if(right > intervals[j][1]){
                    j++;
                }else{
                    right = intervals[j][1];
                    j++;
                }
            }
            list.add(left);
            list.add(right);
            System.out.println(list);
            int[][] result = new int[list.size()/2][2];
            for(int i = 0;i<list.size();i++){
                if(i%2==0){
                    result[(int)(i/2)][0] = list.get(i);
                }else{
                    result[(int)(i/2)][1] = list.get(i);
                }
            }
            return result;
        }
    }
}
```
最终结果：  85 ms	47.6 MB

好繁琐，勉强还是写出来了...


### 第二次提交
```

```
最终结果：
## Python
```

```
最终结果：
