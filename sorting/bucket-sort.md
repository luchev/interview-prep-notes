# Bucket sort

#### Bucket sort

| Bucket sort                    | n = input size, k = number of buckets |
| ------------------------------ | ------------------------------------- |
| Time complexity (Worst case)   | $$\mathcal{O}(n^2)$$                  |
| Time complexity (Average case) | $$\mathcal{O}(n+\frac{n^2}{k}+k)$$    |
| Space complexity               | $$\mathcal{O}(nk)$$                   |

**Key points**

1. It’s a distribution sort, not a comparison sort.
2. Very situational sort.
3. The bellow code is a sample implementation for floats between 0 and 1.

**Code**

```
#include <iostream>
#include <vector>
#include <algorithm>
void bucketSort(double *array, int length) {
    std::vector<double> buckets[length];

    for(int i = 0; i < length; i++) {
        buckets[int(length * array[i])].push_back(array[i]);
    }

    for(int i = 0; i < length; i++) {
        sort(buckets[i].begin(), buckets[i].end());
    }

    int index = 0;
    for(int i = 0; i < length; i++) {
        while(!buckets[i].empty()) {
            array[index] = buckets[i][0];
            index++;
            buckets[i].erase(buckets[i].begin());
        }
    }
}
```