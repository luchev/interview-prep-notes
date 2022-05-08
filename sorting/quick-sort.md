# Quicksort

### Properties

| Quicksort                      | n = input size                           |
| ------------------------------ | ---------------------------------------- |
| Time complexity (Worst case)   | $$\mathcal{O}(n^2)$$                     |
| Time complexity (Average case) | $$\mathcal{O}(n*log(n))$$                |
| Space complexity               | $$\mathcal{O}(log(n))$$                  |
| Number of comparisons          | $$\mathcal{O}(n*log(n))$$                |
| Number of swaps                | $$\mathcal{O}(n*log(n))$$                |
| Adaptive                       | Anti-Adaptive (more randomness = better) |
| Stable                         | No                                       |
| Local                          | Yes                                      |
| Online                         | No                                       |
| In-place                       | Yes                                      |
| Parallel                       | Yes                                      |
| External                       | No                                       |

### **Implementation**

```python
def quickSort(arr):
  _quickSort(arr, 0, len(arr) - 1)

def _quickSort(arr, left, right):
  if len(arr) <= 1:
    return
  if left < right:
    mid = partitionLomuto(arr, left, right)
    _quickSort(arr, left, mid - 1)
    _quickSort(arr, mid + 1, right)

def partitionLomuto(arr, left, right):
  mid = left - 1
  pivot = arr[right]
  for k in range(left, right):
    if arr[k] <= pivot:
      mid = mid + 1
      arr[mid], arr[i] = arr[i], arr[mid]
  
  arr[mid + 1], arr[right] = arr[right], arr[mid + 1]
  return mid + 1
  
def partitionHoare(arr, left, right):
  pivot = arr[(left + right) // 2]

  while True:
    while array[left] < pivot:
      left += 1
    while array[right] > pivot:
      right -= 1
    if left >= right:
      return right
    array[left], array[right] = array[right], array[left]
```

### **Key points**

* C++ STL sorting algorithm is Introsort, which is a hybrid between quicksort and heapsort

### Optimizations

* To avoid the worst-case a common strategy is to shuffle the array before sorting it, because of the anti-adaptive property
* For arrays with many equal numbers, we can use the three-way partitioning, aka. Dutch national flag
* To avoid a worst-case complexity we can pick 2 pivots instead of 1, aka. multi-pivot quicksort

### **Why is quicksort usually faster than merge sort and other fast algorithms?**

The table below is an approximation of the time required to access data from the disk/RAM/CPU cache. It gives us an idea of why Quicksort is indeed quick. Being in-place means that a lot of the operations are performed in the CPU cache, which is very fast. Merge sort on the other hand uses additional memory (it uses 2 arrays). Often these 2 arrays cannot simultaneously be in the cache so they have to be read from RAM, which is slow.

| Memory hierarchy | CPU cycles | size   |
| ---------------- | ---------- | ------ |
| HDD              | 500, 000   | 1 TB   |
| RAM              | 100        | 4 GB   |
| L2 cache         | 10         | 512 kb |
| L1 cache         | 1          | 32 kb  |

### **Further readings**

* [Quickselect](https://en.wikipedia.org/wiki/Quickselect) - uses the partitioning from Quicksort to find k-th biggest/smallest element
