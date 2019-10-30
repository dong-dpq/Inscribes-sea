# 原题：

```
Given a linked list, remove the n-th node from the end of list and return its head.

Example:

Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
Note:

Given n will always be valid.

Follow up:

Could you do this in one pass?
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode beg = head;
        int count = 1;
        while(beg.next != null){
            count++;
            beg = beg.next;
        }
        if (count == 1){return null;}
        ListNode newhead = new ListNode(0);
        newhead.next = head;
        ListNode usebeg = newhead;
        int usecount = 0;
        while(usebeg != null ){
            if(usecount == count - n){
                ListNode temp = usebeg.next.next;
                usebeg.next.next = null;
                usebeg.next = temp;
                break;
            }
            usecount++;
            usebeg = usebeg.next;
        }
        return newhead.next;
    }
}
```
最终结果：0 ms	34.7 MB

第一次遍历计算链表的长度N，第二次遍历删除目标节点。


### 大佬解法
```
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    ListNode first = dummy;
    ListNode second = dummy;
    // Advances first pointer so that the gap between first and second is n nodes apart
    for (int i = 1; i <= n + 1; i++) {
        first = first.next;
    }
    // Move first to the end, maintaining the gap
    while (first != null) {
        first = first.next;
        second = second.next;
    }
    second.next = second.next.next;
    return dummy.next;
}
```
最终结果：

用两个指针而不是一个指针。第一个指针从列表的开头向前移动 n+1n+1 步，而第二个指针将从列表的开头出发。

## Python
```

```
最终结果：
