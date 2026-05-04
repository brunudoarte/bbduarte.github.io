---
layout: post
title: Computing Fibonacci Numbers with Dynamic Programming in C++
date: 2026-05-03 16:00:00
description: An efficient approach to compute Fibonacci numbers using dynamic programming in C++.
tags: algorithms dynamic-programming c++
categories: tutorial
featured: true
---

The Fibonacci sequence is a classic problem in computer science. The sequence is defined as follows:

$$F(0) = 0, F(1) = 1$$
$$F(n) = F(n-1) + F(n-2) \text{ for } n > 1$$

A naive recursive implementation has exponential time complexity $O(2^n)$. Dynamic programming allows us to solve this in linear time $O(n)$.

### Iterative Approach (Bottom-Up)

The most efficient way to compute Fibonacci numbers is using an iterative approach that saves space by only keeping track of the last two values.

```c++
#include <iostream>
#include <vector>

long long fibonacci(int n) {
    if (n <= 1) return n;
    
    long long prev = 0;
    long long curr = 1;
    
    for (int i = 2; i <= n; ++i) {
        long long next = prev + curr;
        prev = curr;
        curr = next;
    }
    
    return curr;
}

int main() {
    int n = 50;
    std::cout << "Fibonacci of " << n << " is " << fibonacci(n) << std::endl;
    return 0;
}
```

### Memoization (Top-Down)

Alternatively, we can use recursion with memoization to store previously computed results.

```c++
#include <iostream>
#include <vector>

std::vector<long long> memo;

long long fib_memo(int n) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n];
    
    memo[n] = fib_memo(n - 1) + fib_memo(n - 2);
    return memo[n];
}

int main() {
    int n = 50;
    memo.assign(n + 1, -1);
    std::cout << "Fibonacci (Memoized) of " << n << " is " << fib_memo(n) << std::endl;
    return 0;
}
```

Dynamic programming is a powerful technique that transforms exponential problems into linear ones by avoiding redundant computations.
