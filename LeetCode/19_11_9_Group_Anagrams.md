# 原题：

```
Given an array of strings, group anagrams together.

Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
Note:

All inputs will be in lowercase.
The order of your output does not matter.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        int n = strs.length;
        if(n == 0){
            return new ArrayList<List<String>>();
        }else{
            Map<String,List<String>> map = new HashMap<String,List<String>>();
            for(String s: strs){
                int lenS = s.length();
                //字符串转数组
                char[] temp = new char[lenS];
                for(int i = 0; i < lenS;i++){
                    temp[i] = s.charAt(i);
                }
                //字符数组排序
                for(int k =0;k < lenS-1;k++){
                    for(int m=k+1;m < lenS;m++){
                        if(temp[k]>temp[m]){
                            char c = temp[m];
                            temp[m] = temp[k];
                            temp[k] = c;
                        }
                    }
                }
                //数组转回字符串
                String newS = "";
                for(char c:temp){
                    newS += c;
                }
                //加入map
                if(map.containsKey(newS)){
                    map.get(newS).add(s);
                }else{
                    List<String> list = new ArrayList<String>();
                    list.add(s);
                    map.put(newS,list);
                }
            }
            return new ArrayList(map.values());
        }
    }
}
```
最终结果：  15 ms	42.4 MB

1/最初想用HashMap存储一个字符串中各个字符出现的次数，例如对于"eat"，就是{'e':1,'a':1,'t':1}，出现新的字符串"ate"后，就比较它们的HashMap是否一致，
这样就需要用List<HashMap<Character,Integer>>来存储...感觉好麻烦...

看大佬说可以把HashMap简化成字符串，例如abbccc 将表示为 (1,2,3,0,0，...，0)，其中总共有 26 个条目...高手...

还有一种思路是直接把字符串排序，比较他两是否一样...更简单...都是高手...

2/在判断排序后字符串是否出现过时，本来是用的两个list，一个ArrayList<List<String>>存储结果 [["nat","tan"],["bat"]]，另一个ArrayList<String>
同步存储排序后的字符串["ant","abt"]...看大佬的方法直接用一个map来存{"ant"：["nat","tan"]，"abt"：["bat"]}，最后直接返回ArrayList(ans.values())...
好的我是猪...


## Python
```

```
最终结果：
