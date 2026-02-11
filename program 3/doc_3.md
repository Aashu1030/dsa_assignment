# Reverse Traversal of Singly Linked List

This program demonstrates the implementation of a singly linked list and performs reverse traversal using recursion to print the elements in reverse order.

## Data Structures

The program uses a structure to represent nodes in a singly linked list:

### `struct Node`
- **data**: An integer field that stores the value of the node.
- **next**: A pointer to the next node in the linked list. For the last node, this pointer is set to NULL.

The linked list is accessed through a head pointer that points to the first node. If the list is empty, the head pointer is NULL.

## Functions Implemented

### 1. `struct Node* createNode(int value)`
**Purpose**: Creates and initializes a new node with the given value.

This function dynamically allocates memory for a new node using `malloc()`. It sets the data field to the provided value and initializes the next pointer to NULL, indicating that the node doesn't point to any other node yet. The function returns a pointer to the newly created node.

### 2. `void insertEnd(struct Node** head, int value)`
**Purpose**: Inserts a new node at the end of the linked list.

This function takes a double pointer to the head of the list and a value to insert. It first creates a new node using the `createNode()` function. If the list is empty (head is NULL), the new node becomes the head. Otherwise, the function traverses the entire list using a temporary pointer until it reaches the last node (where next is NULL), then links the new node at the end.

### 3. `void reverseTraversal(struct Node* head)`
**Purpose**: Prints the linked list elements in reverse order using recursion.

This is a recursive function that traverses the list in reverse without modifying the list structure. The base case occurs when the head pointer is NULL, meaning we've reached beyond the last node. For the recursive case, the function first calls itself with the next node, effectively going to the end of the list. As the recursion unwinds, each node's data is printed, resulting in reverse order output. This approach uses the call stack to temporarily store node references.

## Organization of main() Method

The main function demonstrates the usage of the linked list with the following steps:

1. **Initialization**: A head pointer is declared and initialized to NULL, representing an empty linked list.

2. **List Construction**: Four nodes with values 10, 20, 30, and 40 are inserted at the end of the list using the `insertEnd()` function. This creates a list: 10 -> 20 -> 30 -> 40.

3. **Display Message**: A message is printed to indicate that reverse traversal is being performed.

4. **Reverse Traversal**: The `reverseTraversal()` function is called with the head pointer, which recursively prints all elements in reverse order.

5. **Program Termination**: Returns 0 to indicate successful execution.

Note: The program doesn't explicitly free the allocated memory, which in a production environment should be done to prevent memory leaks.

## Sample Output

### Complete Run
```
Reverse traversal of linked list:
40 30 20 10 
```

### Explanation
The linked list contains elements in the order: 10 -> 20 -> 30 -> 40

When reverse traversal is performed, the recursive function goes to the end of the list first, then prints values as it returns from each recursive call, resulting in the output: 40, 30, 20, 10.

### Additional Test Cases

If we modify the main function to insert different values:
```
// Insert: 5, 15, 25
Reverse traversal of linked list:
25 15 5 
```
```
// Insert: single element 100
Reverse traversal of linked list:
100 
```
```
// Empty list (no insertions)
Reverse traversal of linked list:
```
