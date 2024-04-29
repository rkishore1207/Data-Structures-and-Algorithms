
# Palindromic Linked List
## C Sharp

### Problem
- Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

### Sample Test Cases

`Example 1:`<br>
`Input`: head = [1,2,2,1] <br>
`Output`: true<br>
`Example 2:`<br>
`Input`: head = [1,2]<br>
`Output`: false
 

```C#
public class Solution {
    public bool IsPalindrome(ListNode head) {
        int length = 0, count = 0;
        for(ListNode node = head;node != null; node = node.next)
            length++;
        ListNode prev = null, current = head, next = current.next, pointer1 = null, pointer2 = null;
        if(length <= 0)
            return false;
        if(length == 1)
            return true;
        if(length % 2 != 0)
        {
            while(true)
            {
                current.next = prev;
                prev = current;
                current = next;
                next = current.next;
                count++;
                if(count == length/2)
                {
                    pointer1 = prev;
                    pointer2 = next;
                    break;
                }
            }
            while(pointer1 != null && pointer2 != null)
            {
                if(pointer1.val != pointer2.val)
                    return false;
                pointer1 = pointer1.next;
                pointer2 = pointer2.next;
            }
            if(pointer1 == null && pointer2 == null)
                return true;
            return false;
        }
        else
        {
            while (true)
            {
                current.next = prev;
                prev = current;
                current = next;
                next = current.next;
                count++;
                if (count == length / 2)
                {
                    pointer1 = prev;
                    pointer2 = current;
                    break;
                }
            }
            while (pointer1 != null && pointer2 != null)
            {
                if (pointer1.val != pointer2.val)
                    return false;
                pointer1 = pointer1.next;
                pointer2 = pointer2.next;
            }
            if (pointer1 == null && pointer2 == null)
                return true;
            return false;
        }
    }
}

```