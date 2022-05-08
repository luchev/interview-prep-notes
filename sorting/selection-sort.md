# Selection sort

### Properties

| Selection sort        | n = input size       |
| --------------------- | -------------------- |
| Time complexity       | $$\mathcal{O}(n^2)$$ |
| Space complexity      | $$\mathcal{O}(1)$$   |
| Number of comparisons | $$\mathcal{O}(n^2)$$ |
| Number of swaps       | $$\mathcal{O}(n)$$   |
| Adaptive              | No                   |
| Stable                | No                   |
| Local                 | No                   |
| Online                | No                   |
| In-place              | Yes                  |
| Parallel              | No                   |
| External              | No                   |

### Implementation

```python
def selectionSort(arr):
  for i in range(len(arr)):
    minIndex = i
    for k in range(i+1, len(arr)):
      if arr[minIndex] > arr[k]:
            minIndex = k       
    arr[i], arr[minIndex] = arr[minIndex], arr[i]
```

### **Key points**

* It’s better than bubble sort in cases we need to sort items that are very large in size because it has $$\mathcal{O}(n)$$ swaps
