# Dynamic array

### Dynamic arrays

A dynamic array is an array which grows in size when it’s full. Each time it increases its size 2 times. e.g the size at the start is 1, then 2, 4, 8, 16....

The good points are we have amortized $$\mathcal{O}(1)$$ Add and $$\mathcal{O}(1)$$ access like in regular arrays.

The downsides are If we have added 32 items and have reserverd 64 items, but don’t add any more items we are wasting memory needlessly. Also, when adding, if the array is full we will need to resize so occasionally our Add will be with $$\mathcal{O}(n)$$ complexity.

#### Amortized complexity

Amortized complexity is the total expense per operation, evaluated over a sequence of operations.

In other words if we add 1 item it could be very expensive $$\mathcal{O}(n)$$ but if we add `n` items it is going be $$\mathcal{O}(n)$$ to add all n-items.

Explained with example:

Let’s take a dynamic array (in C++ that would be std::vector).

At the start we have 1 empty slot. In constant time we add 1 item at the end.

When we want to add 1 more item, our array is full, so we expand it 2x in size to 2 items, we copy the old 1 item at the start and in constant time we add the new item at the end. The copy operation takes $$\mathcal{O}(n)$$ steps.

We want to add a 3rd item, but we have capacity of 2, we expand the array to 4 in $$\mathcal{O}(n)$$ steps and add the new item to the end in constant time.

We want to add a 4th item, and we have capacity of 4 so we can add it to the end in constant time.

In conclusion, every time we want to add an item in position $$2^k$$ we ahve to expand with complexity $$\mathcal{O}(2^k)$$. All other additions are with $$\mathcal{O}(1)$$ comlexity.

So in the end we have $$1 + 2^0 + 1 + 2^1 + 1 + 1 + 2^2 + 1 + 1 +... + 2^k$$ where $$k = log(n)$$. If we sum these numbers we will get n from the 1s and 2n from the powers of 2. In conclusion adding n items costs us $$\mathcal{O}(n)$$ time. In other words amortized $$\mathcal{O}(1)$$ per item.
