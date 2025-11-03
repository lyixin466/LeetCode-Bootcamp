#### Reorder List

class Solution {

  public void reorderList(ListNode head) {

​    if (head == null || head.next == null) return;

​    ListNode slow = head, fast = head;

​    while (fast != null && fast.next != null) {

​      slow = slow.next;

​      fast = fast.next.next;

​    }

​    ListNode secondHalf = reverse(slow.next);

​    slow.next = null;

​    ListNode firstHalf = head;

​    while (secondHalf != null) {

​      ListNode temp1 = firstHalf.next;

​      ListNode temp2 = secondHalf.next;

​      firstHalf.next = secondHalf;

​      secondHalf.next = temp1;

​      firstHalf = temp1;

​      secondHalf = temp2;

​    }

  }

  private ListNode reverse(ListNode head) {

​    ListNode prev = null;

​    while (head != null) {

​      ListNode next = head.next;

​      head.next = prev;

​      prev = head;

​      head = next;

​    }

​    return prev;

  }

}