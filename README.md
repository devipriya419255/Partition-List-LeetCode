# LeetCode #86: Partition List (C Solution)

## 📌 Description
This repository contains a concise C implementation to rearrange a singly linked list so all nodes with a value less than `x` precede nodes with values greater than or equal to `x`, while preserving original relative order.

## 🚀 Key Features
*   **Optimal Approach:** Uses two dummy head pointers to manage "before" and "after" chains.
*   **Time Complexity:** $O(n)$ - Single pass through the list.
*   **Space Complexity:** $O(1)$ - In-place reordering.

## 🛠️ Implementation
```c
// Assumes ListNode structure is defined as:
// struct ListNode { int val; struct ListNode *next; };

struct ListNode* partition(struct ListNode* head, int x) {
    struct ListNode before_head, after_head;
    struct ListNode *before = &before_head, *after = &after_head;

    while (head) {
        if (head->val < x) before = (before->next = head);
        else after = (after->next = head);
        head = head->next;
    }
    after->next = NULL;
    before->next = after_head.next;
    return before_head.next;
}
