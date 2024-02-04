---
title: "[C++ / Algorithm] 소수 판별 #13"
date: 2024-02-04 23:02:00 +/-TTTT
categories: [algorithm, cpp]
tags: [algorithm, cpp]   # TAG names should always be lowercase
---

## 1. 소수를 판별하는 가장 빠른 방법

소수를 판별하는 가장 빠른 방법은 시간 복잡도가 **`O(log N)`** 입니다.
판별하려는 수의 제곱근까지만 반복하여 소수를 반별하는 방법으로,
모든 수의 약수는 제곱근을 기준으로 짝지어진다는 특징을 이용한 알고리즘입니다.

## 2. 구현

```cpp
#include <iostream>
#include <cmath>

using namespace std;

bool isPrime(int x) {
    if (x == 1) return false;
    
    for (int i = 2; i <= sqrt(x); i++) {
        if (x % i == 0) return false;
    }
    
    return true;
}

int main() {
    cout << isPrime(3) << endl;
    cout << isPrime(4) << endl;
    cout << isPrime(7) << endl;
    cout << isPrime(193) << endl;
    cout << isPrime(1295) << endl;
    
    return 0;
}
```
{: file="main.cpp" }
```
1
0
1
1
0

```
{: file="output.cpp" }