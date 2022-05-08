# Radix sort

### Properties

| Radix sort                     | n = input size, k = number of digits |
| ------------------------------ | ------------------------------------ |
| Time complexity (Worst case)   | $$\mathcal{O}(n^2)$$                 |
| Time complexity (Average case) | $$\mathcal{O}(n*k)$$                 |
| Space complexity               | $$\mathcal{O}(n+k)$$                 |
| Adaptive                       | No                                   |
| Stable                         | Depends on the underlying sort       |
| Local                          | No                                   |
| Online                         | No                                   |
| In-place                       | No                                   |
| Parallel                       | Yes                                  |
| External                       | No                                   |

### Implementation

```python
def radixSort(arr):
  maxElement = max(arr)
  place = 1
  while maxElement // place > 0:
    countingSort(arr, place)
    place *= 10
    
def sortByPlce(arr, place):
  size = len(arr)
  output = [0] * size
  count = [0] * 10

  for x in arr:
    index = x // place
    count[index % 10] += 1
  
  for i in range(1, 10):
    count[i] += count[i - 1]

  i = size - 1
  while i >= 0:
    index = arr[i] // place
    output[count[index % 10] - 1] = arr[i]
    count[index % 10] -= 1
    i -= 1

  for i in range(0, size):
    arr[i] = output[i]
```
