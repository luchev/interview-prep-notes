# Stack



### Stack (LIFO)

A stack is a **restricted** data structure - allows access only to the element at the top of the stack.

Add elements to the top, take from the top.

LIFO = Last In First Out

#### Problems that can occur with stacks

Overflow - Adding too many elements and the stack cannot contain them

Underflow - Try to access the top element when the stack is empty

| Stack with   | Dynamic Array                        | Linked list        |
| ------------ | ------------------------------------ | ------------------ |
| push()       | Amortized $$\mathcal{O}(1)$$         | $$\mathcal{O}(1)$$ |
| pop()        | Amortized $$\mathcal{O}(1)$$         | $$\mathcal{O}(1)$$ |
| peek()/top() | $$\mathcal{O}(1)$$                   | $$\mathcal{O}(1)$$ |
| clear()      | $$\mathcal{O}(p)$$ - delete memory   | $$\mathcal{O}(n)$$ |
| isEmpty()    | $$\mathcal{O}(1)$$                   | $$\mathcal{O}(1)$$ |
| initialize   | $$\mathcal{O}(p)$$ - allocate memory | $$\mathcal{O}(1)$$ |
| merge        | $$\mathcal{O}(n)$$                   | $$\mathcal{O}(1)$$ |

#### Application of stacks

1. Undo/Redo in programs
2. Reverse word/array
3. Programming languages are usually compiled down and work as a pushdown automaton
4. Syntax parsing - used by compilers
5. Switching between infix and prefix notation
6. Backtracking
