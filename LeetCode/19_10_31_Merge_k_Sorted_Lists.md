# 原题：

```
Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

Example:

Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
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
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists.length == 0){return null;}
        ListNode head = new ListNode(-1);
        ListNode usehead = head;
        while(true){
            ListNode minNode = new ListNode(Integer.MAX_VALUE);
            int minIndex = -1;
            for(int i = 0; i < lists.length;i++){
                if(lists[i] != null && lists[i].val < minNode.val){
                    minIndex = i;
                    minNode = lists[minIndex];
                }
            }
            if(minIndex < 0){
                break;
            }else{
                usehead.next = minNode;
                usehead = usehead.next;
                lists[minIndex] = lists[minIndex].next;
            }
        }
        return head.next;
    }
}
```
最终结果：343 ms	58.3 MB

有一点k指针的意思。时间复杂度应该是O（K*N）吧，空间复杂度是O（1）。看了一下大佬的方法，可以用队列来优化比较的过程。


## Python
```

```
最终结果：
