# Merge sort

### Properties

| Merge sort            | n = input size            |
| --------------------- | ------------------------- |
| Time complexity       | $$\mathcal{O}(n*log(n))$$ |
| Space complexity      | $$\mathcal{O}(n)$$        |
| Number of comparisons | $$\mathcal{O}(n*log(n))$$ |
| Number of swaps       | $$\mathcal{O}(n*log(n))$$ |
| Adaptive              | No                        |
| Stable                | Yes                       |
| Local                 | No                        |
| Online                | No                        |
| In-place              | No                        |
| Parallel              | Yes                       |
| External              | Yes                       |

### **Implementation**

```python
def mergeSort(arr):
  _mergeSort(arr, 0, len(arr) - 1)

def _mergeSort(arr, left, right):
  if left < right:
    mid = left + (right - left) // 2
    _mergeSort(arr, left, mid)
    _mergeSort(arr, mid + 1, right)
    merge(arr, left, mid, right)
 
def merge(arr, left, mid, right):
  leftArr = [0] * (mid - left + 1)
  rightArr = [0] * (right - mid)

  for i in range(len(leftArr)):
    leftArr[i] = arr[left + i]
    
  for i in range(len(rightArr)):
    rightArr[i] = arr[mid + 1 + i]
    
  left = 0
  right = 0
  merged = left
  
  while left < len(leftArr) and right < len(rightArr):
    if leftArr[left] <= rightArr[right]:
      arr[merged] = leftArr[left]
      left += 1
    else:
      arr[merged] = rightArr[right]
      right += 1
    merged += 1
    
  while left < len(leftArr):
    arr[merged] = leftArr[left]
    left += 1
    merged += 1
  
  while right < len(rightArr):
    arr[merged] = rightArr[right]
    right += 1
    merged += 1
```

### **Key points**

1. Every array with 0 or 1 element is sorted.
2. Merging requires additional memory.
3. Splitting the array in 2 every time gives us $$log(n)$$ levels.
4. On each level, we have $$\mathcal{O}(n)$$ for the merging operation.



![](https://i.imgur.com/obZrU8h.png)

### Further readings

* [Ford–Johnson aka. Merge-insertion sort](https://en.wikipedia.org/wiki/Merge-insertion\_sort) - algorithm with very few comparisons, but not practical
* [Timsort](https://en.wikipedia.org/wiki/Timsort) - based on merge sort + insertion sort with $$\mathcal{O}(nlogn)$$ worst case and $$\mathcal{O}(n)$$ best case. [Implementation](https://github.com/tvanslyke/timsort-cpp)
* An important application is using merge sort to count [inversions](https://en.wikiversity.org/wiki/Inversion\_\(discrete\_mathematics\))
