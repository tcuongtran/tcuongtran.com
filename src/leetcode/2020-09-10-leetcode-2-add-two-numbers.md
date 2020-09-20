---
title: "Leetcode #2. Add Two Numbers"
type: posts
published: 2020-09-19
tag: leetcode
---
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number `0` itself.
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    const dummyHead = new ListNode(null);
    let current = dummyHead;
    let carry = 0;

    while (l1 || l2 || carry) {
        const val1 = l1 ? l1.val : 0; // first value
        const val2 = l2 ? l2.val : 0; // second value
        const value = val1 + val2 + carry; // add 2 numbers plus carry

        current.next = new ListNode(value % 10); // add number to linked-list
        current = current.next;
        carry = value >= 10 ? 1 : 0; // find carry number
        l1 = l1 && l1.next;
        l2 = l2 && l2.next;
    }

    return dummyHead.next;
};
```

<!-- more -->