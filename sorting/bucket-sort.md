# Bucket sort

### Properties

| Bucket sort                    | n = input size, k = number of buckets |
| ------------------------------ | ------------------------------------- |
| Time complexity (Worst case)   | $$\mathcal{O}(n^2)$$                  |
| Time complexity (Average case) | $$\mathcal{O}(n)$$                    |
| Space complexity               | $$\mathcal{O}(n+k)$$                  |
| Adaptive                       | No                                    |
| Stable                         | Depends on the underlying sort        |
| Local                          | No                                    |
| Online                         | No                                    |
| In-place                       | No                                    |
| Parallel                       | Yes                                   |
| External                       | Yes                                   |

### **Implementation**

```python
# This implementation works for floats in the range [0;1]
def bucketSort(arr):
  buckets = []
  
  for i in range(len(arr)):
    buckets.append([])
  
  for x in arr:
    bucketIndex = int(10 * x)
    buckets[bucketIndex].append(x)
  
  for i in range(len(buckets)):
    buckets[i] = sorted(buckets[i])
  
  k = 0
  for bucket in buckets:
    for x in bucket:
      arr[k] = x
      k += 1
```

### **Key points**

1. It’s a distribution sort, not a comparison sort
2. Very a situational sort
