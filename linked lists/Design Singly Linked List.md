# Design a Singly Linked List class.

Your LinkedList class should support the following operations:

* LinkedList() will initialize an empty linked list.
* int get(int i) will return the value of the ith node (0-indexed). If the index is out of bounds, return -1.
* void insertHead(int val) will insert a node with val at the head of the list.
* void insertTail(int val) will insert a node with val at the tail of the list.
* bool remove(int i) will remove the ith node (0-indexed). If the index is out of bounds, return false, otherwise return true.
* int[] getValues() return an array of all the values in the linked list, ordered from head to tail.

### Example 1:

### Input: 
`["insertHead", 1, "insertTail", 2, "insertHead", 0, "remove", 1, "getValues"]`

### Output:
`[null, null, null, true, [0, 2]]`
### Example 2:

### Input:
`["insertHead", 1, "insertHead", 2, "get", 5]`

### Output:
`[null, null, -1]`
### Note:
The index int i provided to get(int i) and remove(int i) is guaranteed to be greater than or equal to 0.

# Solution
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None


class LinkedList:
    def __init__(self):
        self.head: Node | None = None
        self.tail: Node | None = None

    def get(self, index: int) -> int:
        curr = self.head
        i = 0

        while curr:
            if i == index:
                return curr.val
            curr = curr.next
            i += 1
            
        return -1 

    def insertHead(self, val: int) -> None:
        node = Node(val)

        if not self.head:
            self.head = self.tail = node
        else:
            node.next = self.head
            self.head = node
        
    def insertTail(self, val: int) -> None:
        node = Node(val)

        if not self.tail:
            self.head = self.tail = node
        else:
            self.tail.next = node
            self.tail = node

    def remove(self, index: int) -> bool:
        if not self.head:
            return False

        if index == 0:
            self.head = self.head.next
            if self.head is None:
                self.tail = None
            return True

        curr = self.head
        i = 0

        while curr and curr.next:
            if i + 1 == index:
                if curr.next == self.tail:
                    self.tail = curr
                curr.next = curr.next.next
                return True
            
            curr = curr.next
            i += 1   

        return False

    def getValues(self) -> list[int]:  
        vals = []
        curr = self.head
        while curr:
            vals.append(curr.val)
            curr = curr.next
        return vals
```
