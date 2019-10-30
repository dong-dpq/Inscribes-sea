# 原题：

```
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

# 提交
## Java
### 第一次提交
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode newBeg = new ListNode(-1);
        ListNode head = newBeg;
        while(true){
            if(l1 == null){
                newBeg.next = l2;
                break;
            }
            if(l2 == null){
                newBeg.next = l1;
                break;
            }
            int a = l1.val;
            int b = l2.val;
            ListNode temp = new ListNode(0);
            if(a < b){
                temp.val = a;
                l1 = l1.next;
            }else{
                temp.val = b;
                l2 = l2.next;
            }
            newBeg.next = temp;
            newBeg = newBeg.next;
        }
        return head.next;
    }
}
```
最终结果：1 ms	39.5 MB

双指针进行判别。不足之处在于，是new的新节点进行添加，内存占用会多一点，如果直接对原链表进行操作会好很多。


### 第二次提交
```

```
最终结果：

## Python
```

```
最终结果：
