### Palindrome Linked List

class Solution {

  public boolean isPalindrome(ListNode head) {

​    if (head == null || head.next == null) return true;

​    ListNode slow = head, fast = head;

​    while (fast != null && fast.next != null) {

​      slow = slow.next;

​      fast = fast.next.next;

​    }

​    ListNode secondHalf = reverseList(slow);

​    ListNode firstHalf = head;

​    ListNode p1 = firstHalf;

​    ListNode p2 = secondHalf;

​    boolean isPalindrome = true;

​    while (p2 != null) {

​      if (p1.val != p2.val) {

​        isPalindrome = false;

​        break;

​      }

​      p1 = p1.next;

​      p2 = p2.next;

​    }

​    reverseList(secondHalf);

​    return isPalindrome;

  }

  private ListNode reverseList(ListNode head) {

​    ListNode prev = null;

​    while (head != null) {

​      ListNode nextNode = head.next;

​      head.next = prev;

​      prev = head;

​      head = nextNode;

​    }

​    return prev;

  }

}