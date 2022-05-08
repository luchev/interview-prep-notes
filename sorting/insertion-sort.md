# Insertion sort

### Properties

| Insertion sort        | n = input size       |
| --------------------- | -------------------- |
| Time complexity       | $$\mathcal{O}(n^2)$$ |
| Space complexity      | $$\mathcal{O}(1)$$   |
| Number of comparisons | $$\mathcal{O}(n^2)$$ |
| Number of swaps       | $$\mathcal{O}(n^2)$$ |
| Adaptive              | Yes                  |
| Stable                | Yes                  |
| Local                 | Yes                  |
| Online                | Yes                  |
| In-place              | Yes                  |
| Parallel              | No                   |
| External              | No                   |

### **Implementation**

```python
def insertionSort(arr):
  for i in range(1, len(arr)):
    k = i-1
    while k >=0 and arr[k] > value:
      arr[k], arr[k+1] = arr[k+1], arr[k]
      k -= 1
```

### **Key points**

1. The best algorithm for sorting small arrays
2. Often combined with other algorithms for optimal runtime
