# Middle of the Linked List

## https://leetcode.com/problems/middle-of-the-linked-list

Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.
```
Example 1:

Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.

Example 2:

Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
``` 

![Middle of the Linked List](middle-of-the-linked-list.PNG?raw=true "Middle of the linked list")

**Note:**

The number of nodes in the given list will be between 1 and 100

## Implementation 1 : First calculate size of list

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        if(head == null)
            return null;
        int size = 0;
        ListNode current = head;
        while(current != null) {
            size++;
            current = current.next;
        }
        current = head;
        for(int i = 1; i <= size / 2; i++){
            current = current.next;
        }
        return current;
    }
}
```

## Implementation 2 : Fast and Slow Pointer

When traversing the list with a pointer slow, make another pointer fast that traverses twice as fast. 
When fast reaches the end of the list, slow must be in the middle.


```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        if(head == null)
            return head;
        ListNode slow = head;
        ListNode fast = head;
        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```

**Complexity Analysis : **

```
Time Complexity: O(N), where NN is the number of nodes in the given list.

Space Complexity: O(1), the space used by slow and fast.
```
