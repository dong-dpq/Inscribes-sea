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

思路很简单，难点在于如何随着迭代动态更新list中的字符串数组（删除旧的，添加新的）；例如迭代前是{a, b}，按键代表c，d.则需要添加ac，ad和bc，bd，
然后删除a，b。得到{ac,ad,bc,bd}。上面的思路是，先加d变成{a，b，bc，bd}，然后修改a，b为{ac,ad,bc,bd}。


### 大佬的解法
```
public List<String> letterCombinations(String digits) {
		LinkedList<String> ans = new LinkedList<String>();
		if(digits.isEmpty()) return ans;
		String[] mapping = new String[] {"0", "1", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
		ans.add("");
		for(int i =0; i<digits.length();i++){
			int x = Character.getNumericValue(digits.charAt(i));
			while(ans.peek().length()==i){
				String t = ans.remove();
				for(char s : mapping[x].toCharArray())
					ans.add(t+s);
			}
		}
		return ans;
}

```
用队列来解决问题，每弹出一个旧的，会添加若干个新的。

## Python
```

```
最终结果：
