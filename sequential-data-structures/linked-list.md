# Linked List

### Linked lists

![](https://i.imgur.com/u8jPKdM.png)

Linked list stores its data in separate Nodes. Each node points the next node in the list. The last node points NULL.

The most primitive linked list’s node contains 2 fields - Data and Next pointer

```
struct Node {
	int data;
	Node* next;
};
```

**Complexity comparison**

| Operation / Data structure | Array              | Singly linked list without tail | Singly linked list with tail | Doubly linked list without tail | Doubly linked list with tail |
| -------------------------- | ------------------ | ------------------------------- | ---------------------------- | ------------------------------- | ---------------------------- |
| push\_front                | $$\mathcal{O}(n)$$ | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |
| pop\_front                 | $$\mathcal{O}(n)$$ | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |
| get\_front                 | $$\mathcal{O}(1)$$ | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |
| push\_back                 | $$\mathcal{O}(1)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(1)$$           |
| pop\_back                  | $$\mathcal{O}(1)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(1)$$           |
| get\_back                  | $$\mathcal{O}(1)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(1)$$           |
| get\_at                    | $$\mathcal{O}(1)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           |
| find\_key                  | $$\mathcal{O}(n)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           |
| erase\_key                 | $$\mathcal{O}(n)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           |
| is\_empty                  | $$\mathcal{O}(1)$$ | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |
| add\_before                | $$\mathcal{O}(n)$$ | $$\mathcal{O}(n)$$              | $$\mathcal{O}(n)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |
| add\_after                 | $$\mathcal{O}(n)$$ | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           | $$\mathcal{O}(1)$$              | $$\mathcal{O}(1)$$           |

**Memory allocation**

****

**Array**

![](https://i.imgur.com/YrXJ0RG.png)

**Linked list**

![](https://i.imgur.com/s6NIOOy.png)

**Use**

Linked lists are useful if we don’t know the input size (when getting data from streams).

Also if we want constant time for adding/removing element from the front/back and not amortized constant.

**Inserting a node**

![](https://i.imgur.com/myKqfvr.png)

**Removing a node**

![](https://i.imgur.com/TwspHEo.png)

#### Singly linked list

Singly linked lists have only one pointer to the next Node.

```
struct Node {
	int data;
	Node* next;
};
```

#### Doubly linked list

Doubly linked lists have two pointers, one to the previous item, one to the next.

```
struct Node {
	int data;
	Node* previous;
	Node* next;
};
```

#### Circular linked list

Circular linked lists can be implemented as singly or doubly linked list but the start and end nodes are connected. i.e the end node’s next pointer is not NULL but points the first node instead.

#### XOR linked list

Doubly linked list using memory for singly linked list. The idea is to XOR the address of the previous element and the next element and save that XOR value in one pointer. When we need to access the next element, we XOR the pointer we have saved with the address of the previous element and the result will be the pointer to the next element.

#### Unrolled linked list

Linked list of arrays. Usually the size of the array is the size of the CPU cache. This way we can quickly iterate through the arrays in the cache and we also have the benefits of a linked list.

#### Skip list

A skip list is a linked list-like data structure which allows $$\mathcal{O}(logn)$$ search and $$\mathcal{O}(logn)$$ insertion in an ordered sequence of elements. It builds $$\mathcal{O}(logn)$$ lanes up with links more and more sparse. The chance to build the next lane of links up is 1/2. The higher lanes are “express lanes” for the lanes bellow. The idea is to quickly get to the approximate location we need to get to on the higher lanes and then go down on the lower lanes to the exact location we need.

![](https://i.imgur.com/XW8f8Y0.png)
