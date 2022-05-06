# Queue

### Queue (FIFO)

Add elements to the back, take from the front.

FIFO = First In First Out

| Stack with       | Dynamic Array                        | Linked list        |
| ---------------- | ------------------------------------ | ------------------ |
| push()/enqueue() | Amortized $$\mathcal{O}(1)$$         | $$\mathcal{O}(1)$$ |
| pop()/dequeue()  | Amortized $$\mathcal{O}(1)$$         | $$\mathcal{O}(1)$$ |
| peek()/top()     | $$\mathcal{O}(1)$$                   | $$\mathcal{O}(1)$$ |
| clear()          | $$\mathcal{O}(p)$$ - delete memory   | $$\mathcal{O}(n)$$ |
| isEmpty()        | $$\mathcal{O}(1)$$                   | $$\mathcal{O}(1)$$ |
| initialize       | $$\mathcal{O}(p)$$ - allocate memory | $$\mathcal{O}(1)$$ |

#### Application of queues

1. System processes
2. Interactive processes
3. Background processes
4. Batch process
5. CPU scheduling
6. Synchronize data transfer
7. Print spooler
8. First-come-first-serve (servers for example)

![](https://www.tutorialspoint.com/operating\_system/images/queuing\_diagram.jpg)

#### Ring buffer

Ring buffers are queues where the new data can overwrite the old data when needed. It’s like a queue implemented with an array, providing limited space. Problem that can occur if the pointer for adding new data reaches the pointer for fetching data, in other words the front pointer and the back pointer must never overlap.

![](https://i.imgur.com/kVoguMh.png)

**Application of ring buffers**

1. Chats
2. Real-time processing

#### Okasaki Queue

A queue implemented with 2 linked lists.

https://ucsd-progsys.github.io/liquidhaskell-tutorial/09-case-study-lazy-queues.html

Other interesting topic to research https://en.wikipedia.org/wiki/Persistent\_data\_structure
