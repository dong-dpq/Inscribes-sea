# 原题：

```
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order 
and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

# 提交
## Python
### 第一次提交
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        flag = 0
        result = ListNode(0)
        index = result
        while(True): 
            if l1 != None:
                a = l1.val
                l1 = l1.next
            else:
                a = 0   
            if l2 != None:
                b = l2.val
                l2 = l2.next
            else:
                b = 0
            if a + b + flag >= 10:
                left = a + b + flag - 10
                flag = 1
            else:
                left = a + b + flag
                flag = 0
                
            result.next = ListNode(left)
            result = result.next 
            if l1 == None and l2 == None:
                break

        if flag == 1:            
            result.next = ListNode(1)
            result = result.next
        return index.next
```
最终结果：48 ms	11.7 MB

还不太熟悉链表的操作，出了两次bug

## Java
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0);
        ListNode result = head;
        int a,b,left,up = 0;
        while(true){
            if(l1 != null){
                a = l1.val;
                l1 = l1.next;
            }else{
                a = 0;
            }
            if(l2 != null){
                b = l2.val;
                l2 = l2.next;
            }else{
                b = 0;
            } 
            if(a+b+up >= 10){
                left = a+b+up - 10;
                up = 1;
            }else{
                left = a+b+up;
                up = 0;
            }
            head.next = new ListNode(left);
            head = head.next;
            if ((l1 == null) && (l2 == null)){
                break;
            }
        }
        if(up == 1){
            head.next = new ListNode(1);
            head = head.next;
        }
        return result.next;
    }
}
```
最终结果：2 ms	45.2 MB
