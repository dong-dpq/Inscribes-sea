# 原题：

```
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.



Example:

Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
Note:

Although the above answer is in lexicographical order, your answer could be in any order you want.
```

# 提交
## Java
### 第一次提交
```
class Solution {
    public List<String> letterCombinations(String digits) {
        List<String> list = new ArrayList<String>();
        if(digits.length() == 0){
            return list;
        }
        Map<Character, String> map = new HashMap<Character, String>();
        map.put('2',"abc");
        map.put('3',"def");
        map.put('4',"ghi");
        map.put('5',"jkl");
        map.put('6',"mno");
        map.put('7',"pqrs");
        map.put('8',"tuv");
        map.put('9',"wxyz");
        
        String temp = "";
        list.add(temp);
        for(int i = 0; i < digits.length(); i++){
            char c = digits.charAt(i);
            String res = map.get(c);
            int listLen =  list.size();
            for(int j = 1;j < res.length(); j++){
                for(int k = 0;k < listLen; k++){
                    list.add(list.get(k)+res.charAt(j));
                }
            }
            for(int m =0; m < listLen;m++){
                list.set(m, list.get(m)+res.charAt(0)); 
            }
        }
        return list;
    }
}
```
最终结果：1 ms	36.2 MB




### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
