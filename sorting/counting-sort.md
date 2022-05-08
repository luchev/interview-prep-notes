# Counting sort

### Properties

| Counting sort                | n = input size, k = max number |
| ---------------------------- | ------------------------------ |
| Time complexity (Worst case) | $$\mathcal{O}(n + k)$$         |
| Time complexity (Best case)  | $$\mathcal{O}(n)$$             |
| Space complexity             | $$\mathcal{O}(k)$$             |
| Adaptive                     | No                             |
| Stable                       | Yes                            |
| Local                        | No                             |
| Online                       | No                             |
| In-place                     | No                             |
| Parallel                     | Yes                            |
| External                     | Yes                            |

### **Implementation**

```python
def countingSort(arr):
    counts = [0] * (max(arr) + 1)
    for x in arr:
        counts[x] += 1
        
    resultIndex = 0
    for x in range(len(counts)):
        while counts[x] > 0:
            counts[x] -= 1
            arr[resultIndex] = x
            resultIndex += 1
```

### **Key points**

1. Not a comparison sort
2. Very efficient for an array of integers with many repeating integers with a small difference between the biggest and smallest integer
3. Can be applied to an array with negative numbers by finding the smallest number, adding that number to the whole array (the smallest number becomes 0), and after the sort - subtracting the same number from the whole array
