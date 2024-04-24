# Add Two Numbers

The "Add Two Numbers" problem typically involves adding two numbers represented by linked lists, where each node contains a single digit, and the digits are stored in reverse order. Here's a JavaScript solution to solve this problem:

```javascript
// Definition for singly-linked list node
function ListNode(val, next = null) {
  this.val = val;
  this.next = next;
}

function addTwoNumbers(l1, l2) {
  let dummyHead = new ListNode(0); // Dummy head node to start the result linked list
  let current = dummyHead; // Pointer to traverse the result linked list
  let carry = 0; // Variable to hold the carry value

  // Traverse both input linked lists until reaching the end of both
  while (l1 !== null || l2 !== null) {
    // Get the values of the current nodes (or 0 if the node is null)
    let val1 = l1 !== null ? l1.val : 0;
    let val2 = l2 !== null ? l2.val : 0;

    // Calculate the sum of the current digits and the carry
    let sum = val1 + val2 + carry;
    carry = Math.floor(sum / 10); // Update the carry for the next iteration
    current.next = new ListNode(sum % 10); // Create a new node with the digit sum % 10
    current = current.next; // Move the pointer to the next node

    // Move to the next nodes in the input linked lists (if not null)
    if (l1 !== null) l1 = l1.next;
    if (l2 !== null) l2 = l2.next;
  }

  // Handle the case where there is a carry at the end of the addition
  if (carry > 0) {
    current.next = new ListNode(carry);
  }

  return dummyHead.next; // Return the next node after the dummy head, which is the start of the result linked list
}

// Example usage:
const l1 = new ListNode(2, new ListNode(4, new ListNode(3))); // Represents the number 342
const l2 = new ListNode(5, new ListNode(6, new ListNode(4))); // Represents the number 465
console.log(addTwoNumbers(l1, l2)); // Output: ListNode { val: 7, next: ListNode { val: 0, next: ListNode { val: 8, next: null } } } (represents the number 807)
```

In this solution, we traverse both input linked lists simultaneously, adding corresponding digits and the carry from the previous step. We create a new linked list to store the result digits, and finally return the head of this new linked list.
