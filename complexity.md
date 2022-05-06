# Complexity

## Complexity (Big O)

The most commonly used notation for complexity is Big O (pronounced "Big Oh"). Big O evaluates the complexity in the worst case.

Complexity is measured in terms of the input size (usually for the input size we use the letter $$n$$).

When calculating complexity we

* discard multiplication of constants: $$n^2$$ and $$1000 \times n^2$$ are treated identically
* discard insignificant addends: $$n^2 + n + 1042$$ and $$n^2$$ are treated identically

#### Examples

* $$\mathcal{O}(34n^4+5) = \mathcal{O}(n^4)$$
* $$\mathcal{O}(2^n+n^{1024}+log(n)) = \mathcal{O}(2^n)$$
* $$\mathcal{O}(5N + \frac{1}{2} M) = \mathcal{O}(N + M)$$

### Time complexity

Time Complexity evaluates how many steps an algorithm takes to complete. The number of steps can be translated to CPU cycles or time (seconds/minutes). This conversion depends on the CPU used so it's not very reliable.

For simplicity 1 step is usually assumed to be 1 CPU cycle although different operations take different numbers of cycles (e.g. Division takes 80ish cycles, while Comparison takes 1 cycle [Check page 10](https://www.agner.org/optimize/instruction\_tables.pdf))

#### Examples

$$\mathcal{O}(n^2)$$ means that if our algorithm takes an input of 10 elements it will need 100 steps to finish in the worst case. If the input is of 100 elements it will need 10000 steps to finish in the worst case.

The following algorithm requires $$\mathcal{O}(1)$$ time, because regardless of the input, it will always take a constant number of steps to complete.

```python
def foo(arr):
    return 5 + 2
```

The following algorithm requires $$\mathcal{O}(n)$$ time, because as the size of the input `arr` grows, the algorithm will take more and more time to complete. That time is proportional to the size of `arr`, which is $$n$$.

```python
def foo(arr):
    y = []
    for x in arr:
        y.append(x)
```

### Memory complexity

Memory complexity evaluates how much memory an algorithm requires. This is the maximum memory allocated at a single point in time. This memory usually disregards the size of the variables (i.e. 32-bit int is considered the same as an 8-bit char).

#### Examples

$$\mathcal{O}(n^2)$$ means that if our algorithm takes an input of 10 elements it will allocate 100 memory in the worst case. If the input is of 100 elements it will allocate 10000 memory in the worst case.

The following algorithm requires $$\mathcal{O}(1)$$ memory, because as soon as `y` is allocated it's freed.

```python
def foo(arr):
    for x in arr:
        y = x
```

The following algorithm requires $$\mathcal{O}(n)$$ memory, because as soon as `y` constantly grows in size and at the end `y` has the same size as the input `arr`, and `arr` has size $$n$$.

```python
def foo(arr):
    y = []
    for x in arr:
        y.append(x)
```

## Comparison of orders of common functions

$$
\mathcal{O}(1) < \mathcal{O}(loglog(n)) < \mathcal{O}(log(n)) < \mathcal{O}(log^2(n)) < \mathcal{O}(\sqrt{n}) < \mathcal{O}(n) < \mathcal{O}(nlog(n)) < \mathcal{O}(n^2) < \\ < \mathcal{O}(n^3) < \mathcal{O}(2^n) < \mathcal{O}(3^n) < \mathcal{O}(n!) < \mathcal{O}(n^n) < \mathcal{O}(3^{n^2}) < \mathcal{O}(2^{n^3})
$$

## Big O cheat sheet

\[https://www.bigocheatsheet.com/]\(https://www.bigocheatsheet.com/)

## Constants and Big O

Usually, we discard constants when using Big O, but in some cases, the constant can be meaningful for small input sizes. The following example $$\mathcal{O}(n^2)$$ is faster than $$\mathcal{O}(n)$$ because our complexities are $$n^2$$ and $$9n$$ so for $$n < 9$$ the $$n^2$$ algorithm is faster than the $$9n$$ one.

![](https://i.imgur.com/qv7rO70.png)

## Worst, Best, and Average case

We can analyze algorithms in the Best, Average, and Worst cases:

e.g. for a naive search function defined as:

```python
def search(haystack, needle):
    for x in haystack:
        if x == needle:
            return True
    return False
```

* Best case: `search([1,2,3,4,5], 1)` --> $$\mathcal{O}(1)$$​ because we find the `needle` on the first iteration.
* Worst case: `search([1,2,3,4,5], 5)` --> $$\mathcal{O}(n)$$​ because we find the `needle` on the last iteration. $$n$$​ is the length of the input array.
* Average case: `search([1,2,3,4,5], x)` --> $$\mathcal{O}(n/2) = \mathcal{O}(n)$$. We calculate this by taking all possible values of x: 1,2,3,4,5, evaluating the algorithm complexity for each of them and dividing by the number of executions ($$n$$). i.e. $$\mathcal{O}((1 + 2 + ... + n-1 + n)/n) = \mathcal{O}(n/2)$$

## Amortized complexity

Amortized complexity is the total expense per operation, evaluated over a sequence of operations.

The idea is to guarantee the total expense of the entire sequence while permitting individual operations to be much more expensive than the amortized cost.

e.g. Appending to a dynamic array is $$\mathcal{O}(1)$$​ but in reality, it can be $$\mathcal{O}(1)$$​ or $$\mathcal{O}(n)$$.​ Every time the array is resized the cost is $$\mathcal{O}(n)$$​, but this happens only when adding every $$2^k$$element so it happens for the 1st, 2nd, 4th, 8th, 16th, etc. elements. In all other cases, the array has a buffer​ at the end so the append costs $$\mathcal{O}(1)$$​. If you take the average of many $$\mathcal{O}(1)$$s and the occasional $$\mathcal{O}(n)$$​ you'll get amortized $$\mathcal{O}(1)$$​.

## Names of common complexities

* Constant $$\mathcal{O}(1)$$​
* Logarithmic $$\mathcal{O}(log(n))$$​
* Linear $$\mathcal{O}(n)$$​
* Linearithmic $$\mathcal{O}(n \times log(n))$$​
* Quadratic $$\mathcal{O}(n^2)$$​
* Cubic $$\mathcal{O}(n^3)$$
* Exponential $$\mathcal{O}(2^n)$$​
* Factorial $$\mathcal{O}(n!)$$​



## Definitions of all notations

1. Big O: $$\mathcal{O}(n^2)$$ - the algorithm takes **at most** $$n^2$$ steps to finish in the **WORST CASE**.
2. Big Omega: $$\Omega(n^2)$$ - the algorithm takes **at least** $$n^2$$ steps to finish in the **BEST CASE**.
3. Big Theta: $$\Theta(n^2)$$ - the combination of $$\mathcal{O}(n^2)$$ and $$\Omega(n^2)$$. Meaning the algorithm takes at least $$n^2$$ steps to finish and takes at most $$n^2$$ steps to finish, i.e. it always takes $$n^2$$ steps.
4. Little o: $$\mathcal{o}(n^2)$$ - the algorithm takes **less than** $$n^2$$ steps to finish in the **WORST CASE**.
5. Little Omega: $$\omega(n^2)$$ - the algorithm takes **more than** $$n^2$$ steps to finish in the **BEST CASE**.

## Mathematical definitions

$$
\mathcal{O}(f(n))=\{g(n): \exist c > 0, \exists n_0 > 0 \mid 0 \le g(n) \le cf(n) \space \forall n \ge n_0 \}
$$

$$
\Theta(f(n))=\{g(n): \exist c_1 > 0, \exist c_2 > 0, \exists n_0 > 0 \mid 0 \le c_1f(n) \le g(n) \le c_2 f(n) \space \forall n \ge n_0 \}
$$

$$
\Omega(f(n))=\{g(n): \exist c > 0, \exists n_0 > 0 \mid 0 \le cf(n) \le g(n) \space \forall n \ge n_0 \}
$$

$$
\mathcal{o}(f(n))=\{g(n): \forall c > 0 \space \exists n_0 > 0 \mid 0 \le g(n) < cf(n) \space \forall n \ge n_0 \}
$$

$$
\omega(f(n))=\{g(n): \forall c > 0 \space \exists n_0 > 0 \mid 0 \le cf(n) < g(n) \space \forall n \ge n_0 \}
$$

## Further readings

* Calculating the complexity of a recursive function using the [Master Theorem](https://en.wikipedia.org/wiki/Master\_theorem\_\(analysis\_of\_algorithms\))
