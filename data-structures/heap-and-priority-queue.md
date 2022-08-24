# Heap

1. Heaps are complete binary trees.
2. There are two types of heaps, min heaps and max heaps.
3. Max heap is a heap where the parent node has a value bigger than or equal to both child nodes.
4. Min heap is a heap where the parent node value is always smaller than or equal to its child nodes.
5. Insertion: The new node is added to the bottom of the tree and travels up until it's the right position.
6. Deletion: The deletion of a node is done via the pop() operation, which is always popping the root node of the tree. Then the last node is moved to the root and moves down until it is at the right position.

# Priority Queue

1. A priority queue is an abstract data type where the pop() gives you the data with the highest priority.
2. It can be easily implemented with heaps.
3. Alternatively, you can also implement it with either a linked list or an array. If you use a linked list, the deletion would be O(1) but insertion would be O(n).
4. If you use an array, the insertion would be O(n) but the deletion would be O(1) (pop last index of the array).
5. If you use a heap, both insertion and deletion are O(log n).
