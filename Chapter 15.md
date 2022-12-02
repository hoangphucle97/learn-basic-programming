# Chapter 15: LINKED LIST.
## Types of list organization.
### The relationship between the elements is implicit.
- The elements must be next to each other in memory.
- Fixed number of elements. There are no add and remove operations, only shift operations.
- Random access to each element is fast.
- Memory consuming due to unknown size.
### The relationship between the elements is clear.
- Each element, in addition to its own information, has a link (address) to the next element.
- The elements do not need to be aligned side by side in memory.
- Access to one element requires passing through another.
- Depending on the needs, the elements will be linked in different ways to form a single, double, and circular linked list.
## Linked list.
### Note.
- The number of nodes is not fixed, changes depending on demand, so this is a dynamic structure.
- Suitable for performing insertions and cancel because there is no need to move the node, but just edit the links accordingly. The execution time does not depend on the number of list nodes.
- Consumes memory containing pNext link pointer.
- Sequential access should take time.
## Types of linked lists.
### Single linked list.
```sh
typedef struct tagNode
{
Data Info;
struct tagNode *pNext;
} NODE;
typedef struct tagList
{
NODE *pHead;
NODE *pTail;
} LIST;
```
### Doubly Linked List.
```sh
typedef struct tagDNode
{
Data Info;
struct tagDNode *pNext, *pPrev;
} DNODE;
typedef struct tagDList
{
NODE *pHead;
NODE *pTail;
} DLIST;
```
### Circular Linked List (single round).
```sh
typedef struct tagCNode
{
Data Info;
struct tagCNode *pNext;
} CNODE;
typedef struct tagCList
{
NODE *pHead;
NODE *pTail;
} CLIST;
```
### Circular Linked List (double round).
```sh
typedef struct tagCNode
{
Data Info;
struct tagCNode *pNext, *pPrev;
} CNODE;
typedef struct tagCList
{
NODE *pHead;
NODE *pTail;
} CLIST;
```
## Single linked list.
### Remove a node from the end of the list.
- Find the last node p (with p->pNext == NULL).
- Find the q node before the p node (if any).
- Cancel button after q button.
### Remove a node with key k (Info = k).
- Find node p with key k and destroy previous node q.
- Cancel the button after the q button (if any).
### Browse the list.
- Count/Find the elements of the list that satisfy the condition.
- Remove the entire list.
## Application of single DSLK.
### Stack.
- Working under LIFO (Last In First Out) mechanism.
### Queue.
- Working under FIFO (First In First Out) mechanism.