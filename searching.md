# Searching

### Searching

#### Linear search

| Linear search    | n = input size     |
| ---------------- | ------------------ |
| Time complexity  | $$\mathcal{O}(n)$$ |
| Space complexity | $$\mathcal{O}(1)$$ |

**Algorithm idea**

Iterate every element in order and check if it is the element we are looking for.

**Code**

```
int linearSearch(int *array, int length, int target) {
    for (int i = 0; i < length; i++) {
        if (array[i] == target) {
            return i;
        }
    }
    return -1;
}
```

**Uses**

Searching in unordered data, when we have very few queries. If we have many queries it’s better to sort the array and use faster searching for the queries.

#### Binary search

| Binary search    | n = input size          |
| ---------------- | ----------------------- |
| Time complexity  | $$\mathcal{O}(log(n))$$ |
| Space complexity | $$\mathcal{O}(1)$$      |

Works only on sorted array-like structures, which support $$\mathcal{O}(1)$$ access to elements.

The algorithm uses $$\mathcal{O}(log(n))$$ space if written recursively, but can be written iteratively to have $$\mathcal{O}(1)$$ space as well.

**Algorithm idea**

1. Check the middle element, if it’s the element we are looking for - we are done
2. If the element is bigger than the one we are looking for - recurse into the left sub-array (the sub-array with smaller elements).
3. If the element is smaller than the one we are looking for - recurse into the right sub-array (the sub-array with bigger elements).

**Code**

```
int binarySearch(int *array, int length, int target) {
    int left = 0;
    int right = length - 1;

    while(left <= right) {
        int mid = (left + right) / 2;

        if (array[mid] == target) {
            return mid;
        }
        if (array[mid] > target) {
            right = mid - 1;
        }
        if (array[mid] < target) {
            left = mid + 1;
        }
    }

    return -1;
}
```

**Uses**

Fast searching in ordered data.

Guess and check algorithms.

#### Ternary search

| Ternary search   | n = input size          |
| ---------------- | ----------------------- |
| Time complexity  | $$\mathcal{O}(log(n))$$ |
| Space complexity | $$\mathcal{O}(1)$$      |

**Algorithm idea**

The same idea as binary search but we split the array in 3 parts. On each step we decide which one part to discard and recurse into the other 2.

**Code**

```
int ternarySearch(int *array, int length, int target) {
    int left = 0;
    int right = length - 1;

    while (left <= right) {
        int leftThird = left + (right - left) / 3;
        int rightThird = right - (right - left) / 3;

        if (array[leftThird] == target) {
            return leftThird;
        }
        if (array[rightThird] == target) {
            return rightThird;
        }

        if (target < array[leftThird]) {
            right = leftThird - 1;
        } else if (target > array[rightThird]) {
            left = rightThird + 1;
        } else  {
            left = leftThird + 1;
            right = rightThird - 1;
        }
    }

    return -1;
}
```

**Uses**

Finding min/max in a sorted array.

#### Exponential search

| Exponential search | n = input size          |
| ------------------ | ----------------------- |
| Time complexity    | $$\mathcal{O}(log(n))$$ |
| Space complexity   | $$\mathcal{O}(1)$$      |

**Algorithm idea**

This is the binary search algorithm applied for ordered data of unknown size. We don’t have a mid point so we start from the beginning and double our guessed index each time. e.g for guessed index: 1, 2, 4, 8, 16, 32... If we overshoot the end of the data we go back using binary search because we now have an end index. e.g for array with 27 elements we do a jump to element 32 which doesn’t exist and then use binary search on elements 16 - 32.

**Code**

```
int exponentialSearch(int *array, int length, int target) {
   if (length == 0) {
      return false;
   }

   int right = 1;
   while (right < length && array[right] < target) {
      right *= 2;
   }

   int binaryIndex = binarySearch(array + right/2, min(right + 1, length) - right/2, target);
   if (binaryIndex != -1) {
      return binaryIndex + right/2;
   } else {
      return -1;
   }
}
```

**Uses**

Binary search on streams, which are ordered and other ordered data of unknown size.

#### Jump search

| Jump search      | n = input size          |
| ---------------- | ----------------------- |
| Time complexity  | $$\mathcal{O}(log(n))$$ |
| Space complexity | $$\mathcal{O}(1)$$      |

**Algorithm idea**

We decide on a jump step and check elements on each step. e.g for step 32 we will check elements 0, 32, 64, etc.

Optimal jump step is $$\sqrt{n}$$.

**Code**

```
int jumpSearch(int *array, int length, int target) {
   int left = 0;
   int step = sqrt(length);
   int right = step;

   while(right < length && array[right] <= target) {
      left += step;
      right += step;
      if(right > length - 1)
         right = length;
   }

   for(int i = left; i < right; i++) {
      if(array[i] == target)
         return i;
   }

   return -1;
}
```

**Uses**

Because it’s worse than Binary search, it’s useful when the data structure we are searching in has very slow jump back, aka it’s slow to go back to index $$i - 10$$ from $$i$$.

#### Interpolation search

| Interpolation search                        | n = input size               |
| ------------------------------------------- | ---------------------------- |
| Time complexity for evenly distributed data | $$\mathcal{O}(log(log(n)))$$ |
| Time complexity for badly distributed data  | $$\mathcal{O}(n)$$           |
| Space complexity                            | $$\mathcal{O}(1)$$           |

**Algorithm idea**

If we have well distributed data we can approximate where we will find the element with the following formula

$$
jumpToIndex=startIndex+(\frac{endIndex-startIndex}{array[endIndex]-array[startIndex]})\times (target-array[startIndex])
$$

Example for well distributed data: 1, 2, 3, 4, 5, 6 .... 99, 100

Example for badly distributed data: 1, 1, 1, 1.... 1, 1, 100

**Code**

```
int interpolationSearch(int *array, int length, int target) {
    int left = 0;
    int right = length - 1;

    while (array[right] != array[left] && target >= array[left] && target <= array[right]) {
        int mid = left + ((target - array[left]) * (right - left) / (array[right] - array[left]));

        if (array[mid] < target)
            left = mid + 1;
        else if (target < array[mid])
            right = mid - 1;
        else
            return mid;
    }

    if (target == array[left])
        return left;
    else
        return -1;
}
```

**Uses**

Very situational, when we have data which is evenly distributed.
