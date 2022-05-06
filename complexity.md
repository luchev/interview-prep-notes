---
description: Pronounced "Big Oh"
---

# Complexity

## Complexity (Big O)

Algorithm complexity refers to how many resources (time, memory, etc.) an algorithm consumes.

We measure these values in terms of the input size (usually for the input size we use the letter $$n$$)

We can analyze algorithms in the Best, Average, and Worst cases:

e.g. for a naive search function defined as:

```python
def search(haystack, needle):
    for x in haystack:
        if x == needle:
            return True
    return False
```

* Best case: `search([1,2,3,4,5], 1)` --> $$O(1)$$​ because we find the `needle` on the first iteration.
* Worst case: `search([1,2,3,4,5], 5)` --> $$O(n)$$​ because we find the `needle` on the last iteration. $$n$$​ is the length of the input array.
* Average case: `search([1,2,3,4,5], x)` --> $$O(n/2)  = O(n)$$. We calculate this by taking all possible values of x: 1,2,3,4,5&#x20;

#### Definitions

1. Big O: $$\mathcal{O}(n^2)$$ - the algorithm takes **at most** $$n^2$$ steps to finish in the **WORST CASE**.
2. Little o: $$\mathcal{o}(n^2)$$ - the algorithm takes **less than** $$n^2$$ steps to finish in the **WORST CASE**.
3. Big Omega: $$\Omega(n^2)$$ - the algorithm takes **at least** $$n^2$$ steps to finish in the **BEST CASE**.
4. Little Omega: $$\omega(n^2)$$ - the algorithm takes **more than** $$n^2$$ steps to finish in the **BEST CASE**.
5. Big Theta: $$\Theta(n^2)$$ - the combination of $$\mathcal{O}(n^2)$$ and $$\Omega(n^2)$$. Meaning the algorithm takes at least $$n^2$$ steps to finish and takes at most $$n^2$$ steps to finish, i.e. it always takes $$n^2$$ steps.

#### Comparison of orders of common functions

$$
\mathcal{O}(1) < \mathcal{O}(loglog(n)) < \mathcal{O}(log(n)) < \mathcal{O}(log^2(n)) < \mathcal{O}(\sqrt{n}) < \mathcal{O}(n) < \mathcal{O}(nlog(n)) < \mathcal{O}(n^2) < \\ < \mathcal{O}(n^3) < \mathcal{O}(2^n) < \mathcal{O}(3^n) < \mathcal{O}(n!) < \mathcal{O}(n^n) < \mathcal{O}(3^{n^2}) < \mathcal{O}(2^{n^3})
$$

#### Big O cheat sheet

https://www.bigocheatsheet.com/

#### Formal definitions

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

#### Examples

$$\mathcal{O}(34n^4+5) = n^4$$

$$\mathcal{O}(2^n+n^{1024}+log(n)) = 2^n$$

$$\mathcal{O}(5N + \frac{1}{2} M) = N + M$$

$$\mathcal{O}(n^2)$$ means that if our algorithm takes an input of 10 elements it will need 100 steps to finish in the worst case. If the input is of 100 elements it will need 10000 steps to finish in the worst case.

#### Constants and Big O

Usually, we discard constants when using Big O, but in some cases, the constant can be meaningful for small input sizes. The following example $$\mathcal{O}(n^2)$$ is faster than $$\mathcal{O}(n)$$ because our complexities are $$n^2$$ and $$9n$$ so for $$n < 9$$ the $$n^2$$ algorithm is faster than the $$9n$$ one.

![](https://i.imgur.com/qv7rO70.png)
