# Bubble sort

### Properties

| Bubble sort           | n = input size       |
| --------------------- | -------------------- |
| Time complexity       | $$\mathcal{O}(n^2)$$ |
| Space complexity      | $$\mathcal{O}(1)$$   |
| Number of comparisons | $$\mathcal{O}(n^2)$$ |
| Number of swaps       | $$\mathcal{O}(n^2)$$ |
| Adaptive              | Yes                  |
| Stable                | Yes                  |
| Local                 | Yes                  |
| Online                | No                   |
| In-place              | Yes                  |
| Parallel              | No                   |
| External              | No                   |

### Implementation

```python
def bubbleSort(arr):
  for end in range(len(arr)):
    for i in range(0, len(arr) - end - 1):
      if arr[i] > arr[i + 1]:
        arr[i], arr[i+1] = arr[i+1], arr[i]
```

### **Optimizations**

* Bubble sort can be made adaptive if each time we execute the inner loop we check if any swaps occur. If no swaps occur - we can stop the outer loop.

### Further readings

* [Cocktail shaker sort](https://en.wikipedia.org/wiki/Cocktail\_shaker\_sort) - based on bubble sort, but the bubble moves in both directions
