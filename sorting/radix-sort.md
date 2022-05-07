# Radix sort

#### Radix sort

| Radix sort                     | n = input size                     |
| ------------------------------ | ---------------------------------- |
| Time complexity (Worst case)   | $$\mathcal{O}(n^2)$$               |
| Time complexity (Average case) | $$\mathcal{O}(n+\frac{n^2}{k}+k)$$ |
| Space complexity               | $$\mathcal{O}(nk)$$                |

**Key points**

1. Good on multi-threaded machines.

**Code**

```
#include <iostream>
#include <cmath>
#include <list>

int abs(int a) {
    return a >= 0 ? a : -a;
}

void radixSort(int * array, int length) {
    int maxNumber = 0;
    for (int i = 0; i < length; i++) {
        if (abs(array[i]) > maxNumber) {
            maxNumber = abs(array[i]);
        }
    }

    int maxDigits = log10(maxNumber) + 1;

    std::list<int> pocket[10];

    for(int i = 0; i < maxDigits; i++) {
        int m = pow(10, i + 1);
        int p = pow(10, i);

        for(int j = 0; j < length; j++) {
            int temp = array[j] % m;
            int index = temp / p;
            pocket[index].push_back(array[j]);
        }

        int count = 0;
        for(int j = 0; j<10; j++) {
            while(!pocket[j].empty()) {
                array[count] = *(pocket[j].begin());
                pocket[j].erase(pocket[j].begin());
                count++;
            }
        }
    }
}
```
